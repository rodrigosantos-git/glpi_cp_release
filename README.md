# GLPI Car Park — Releases

Repositório público **só de distribuição** do app GLPI Car Park (código-fonte fica em repositório privado à parte). Contém:

- `version.json` — manifesto lido pelo app pra saber se há uma atualização disponível.
- `releases/*.apk` — os binários baixados quando o usuário toca em "Atualizar Agora".

## Como publicar uma nova versão

1. Gere o APK com a versão nova (`versionCode`/`versionName` incrementados em `app/build.gradle.kts`).
2. Coloque o arquivo em `releases/GLPI-CAR-PARK-<versionName>.apk`.
3. Atualize `version.json`:
   - `versionCode`: precisa ser **maior** que o anterior (é o que o app compara).
   - `versionName`: texto exibido pro usuário (ex: "1.2").
   - `mandatory`: `true` bloqueia o uso do app até atualizar; `false` permite adiar ("Lembrar depois").
   - `changelog`: texto curto do que mudou, mostrado no diálogo.
   - `apkUrl`: link raw do novo APK nesse mesmo repositório.
4. Commit + push. O app verifica esse arquivo toda vez que abre a tela principal.
