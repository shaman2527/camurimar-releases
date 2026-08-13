# camurimar-releases

Canal público de actualizaciones para las apps desktop de **Portal Camuri Mar**.

## Endpoints del updater

- **CamuriSeguridad:** `https://github.com/shaman2527/camurimar-releases/releases/latest/download/seguridad-latest.json`
- **CamuriAdmin:** `https://github.com/shaman2527/camurimar-releases/releases/latest/download/admin-latest.json`

## Cómo funciona

Cada release (tag `seguridad-vX.Y.Z` / `admin-vX.Y.Z`) lleva:

- El instalador firmado: `CamuriSeguridad_X.Y.Z_x64-setup.exe` (+ `.sig`)
- AMBOS manifests: `seguridad-latest.json` y `admin-latest.json` (para que `releases/latest` siempre resuelva ambos canales)

Los manifests también viven commiteados aquí (copia de seguridad y referencia).

## Publicar

Desde el repo principal (project-residend):

```powershell
.\tools\release\release.ps1 -App seguridad -Version X.Y.Z -Notes "..."
.\tools\release\release.ps1 -App admin     -Version X.Y.Z -Notes "..."
.\tools\release\release.ps1 -App all       -Version X.Y.Z -Notes "..."
```

Requisitos: `gh auth login` + llave privada `~/.tauri/camuri.key` (minisign). Si se pierde la llave, no hay más actualizaciones para los clientes ya instalados.
