# Site do Hydra Animes (GitHub Pages)

Página pública de divulgação e download do APK. **Não contém código-fonte do app** —
apenas o site estático, as imagens e o CSS.

## Publicar

1. Crie um repositório **público** chamado `hydra-animes` no GitHub.
2. Envie **o conteúdo desta pasta** para a raiz do repositório (não a pasta `site/`).
3. Em **Settings → Pages**, escolha *Deploy from a branch* → `main` → `/ (root)`.
4. O site fica em `https://wwlvdev.github.io/hydra-animes/` em alguns minutos.

## Endereço já configurado

O site está apontando para **`wwlvdev` / `hydra-animes`**:

- página: `https://wwlvdev.github.io/hydra-animes/`
- downloads: `https://github.com/wwlvdev/hydra-animes/releases/latest`

Se o usuário ou o nome do repositório mudar, substitua `wwlvdev` e/ou
`hydra-animes` em:

- `index.html`, `en.html` e `es.html` — `canonical`, `hreflang`, Open Graph, Twitter, JSON-LD e os botões de download
- `robots.txt` — linha `Sitemap`
- `sitemap.xml` — `<loc>` e alternates

Com um editor de texto, um "substituir tudo" por arquivo resolve. Não há build.

## APK

O GitHub recusa arquivos acima de 100 MB, e o APK passa disso — então ele **não**
entra no repositório. Publique-o em **Releases**:

- tag `v0.13.0` (mesma `versionName` do app)
- anexo `.apk` (o nome do anexo é livre; os botões usam a URL `/releases/latest`)

A URL `/releases/latest` sempre aponta para a release mais recente — não precisa
editar o HTML a cada versão.

## Atualizar a versão na página

Ao subir uma versão nova, ajuste o texto em quatro lugares:

1. `index.html` — eyebrow do hero, `.version` do bloco final e `"softwareVersion"` no JSON-LD
2. `en.html` — mesmos três pontos
3. `es.html` — mesmos três pontos
4. `sitemap.xml` — `lastmod` das três URLs

## Estrutura

```
index.html          página principal (pt-BR)
en.html             versão em inglês
es.html             versión en español latino (es-419)
robots.txt
sitemap.xml
.nojekyll           impede o Jekyll de processar os arquivos
assets/
  styles.css
  fonts/            Poppins 400/700 (subset do app, ~10 KB cada)
  img/              logo, ícone, capa Open Graph e arte da TV
```

As imagens vieram do próprio app (`res/drawable/logo.png`,
`res/drawable/splashtv.jpg`, `ic_launcher-playstore.png`), então a identidade
visual é a mesma do APK.

## Checklist de SEO já aplicado

- `title` e `description` únicos por idioma, `canonical` próprio
- `hreflang` recíproco (pt-BR, en, es-419, x-default) nas três páginas
- seletor de idioma no header (PT · EN · ES) e no rodapé
- Open Graph + Twitter Card com capa 1200×630 e `og:locale` por idioma
- JSON-LD `SoftwareApplication` + `Organization` + `WebSite`
- `robots.txt` e `sitemap.xml` com alternates das três versões
- imagens com `width`/`height`, `alt` descritivo e fonte pré-carregada
- `rel="noopener noreferrer"` nos links externos e `meta referrer`

Nada de `aggregateRating` inventado — nota falsa em schema é penalizada.
