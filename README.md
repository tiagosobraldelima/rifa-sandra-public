# Rifa Sandra — Site Público Estático

Página pública estática para compartilhamento com usuários finais.

## Link público
https://tiagosobraldelima.github.io/rifa-sandra-public/

## O que este repo contém
- `index.html` — página estática autocontida (HTML + CSS + dados + JS embarcados)
- `404.html` — fallback para rotas não encontradas
- `.nojekyll` — desabilita Jekyll para GitHub Pages
- `.github/workflows/pages.yml` — workflow de deploy automático

## Como funciona
A página é gerada a partir do Next.js via `npm run build:static` no repositório principal (`Rifa Sandra`), que:
1. Sobe o servidor Next.js temporariamente
2. Coleta snapshot de rifa ativa + tickets via `/api/public/*`
3. Embarca CSS Tailwind compilado e foto da capa (base64)
4. Gera `index.html` autocontido (sem dependência de backend)

Quando o usuário clica em "Reservar números", ele é redirecionado para o backend admin (URL configurada via `ADMIN_BASE_URL`) onde o sistema completo de reserva + Pix opera.

## Como atualizar
1. Modificar dados no app Next.js (settings, fotos, etc)
2. Rodar `npm run build:static` no app principal
3. Copiar `public-static/*` para este repo
4. Commit + push → deploy automático via GitHub Actions

## Configurar domínio customizado
1. Em **Settings → Pages → Custom domain**, adicione o domínio
2. Crie arquivo `CNAME` na raiz com o domínio
3. Configure DNS no provedor do domínio
