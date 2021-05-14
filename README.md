# pandoc으로 markdown을 docx로 변환하는 환경설정을 모았다. mermaid도 지원한다.

### 부가 확장 (markdown)

    Name: vscode-pandoc
    Id: dougfinke.vscode-pandoc
    Description: Renders markdown through pandoc
    Version: 0.0.8
    Publisher: DougFinke
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=DougFinke.vscode-pandoc

    Name: Markdown Converter
    Id: manuth.markdown-converter
    Description: A markdown-converter for Visual Studio Code
    Version: 3.0.2
    Publisher: manuth
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=manuth.markdown-converter

    Name: Markdown Table Formatter
    Id: fcrespo82.markdown-table-formatter
    Description: A simple markdown plugin to format tables.
    Version: 1.4.3
    Publisher: Fernando Crespo
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=fcrespo82.markdown-table-formatter

    Name: Markdown TOC
    Id: alanwalk.markdown-toc
    Description: Markdown TOC(Table Of Contents) Plugin for Visual Studio Code.
    Version: 1.5.6
    Publisher: AlanWalk
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=AlanWalk.markdown-toc

    Name: markdownlint
    Id: davidanson.vscode-markdownlint
    Description: Markdown linting and style checking for Visual Studio Code
    Version: 0.31.1
    Publisher: David Anson
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint

    Name: markdown-formatter
    Id: mervin.markdown-formatter
    Description:  A Markdown Plugin for code artist
    Version: 0.7.5
    Publisher: mervin
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=mervin.markdown-formatter

    Name: Markdown Preview Mermaid Support
    Id: bierner.markdown-mermaid
    Description: Adds Mermaid diagram and flowchart support to VS Code's builtin markdown preview
    Version: 1.3.0
    Publisher: Matt Bierner
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid

    Name: Mermaid Markdown Syntax Highlighting
    Id: bpruitt-goddard.mermaid-markdown-syntax-highlighting
    Description: Markdown syntax support for the Mermaid charting language
    Version: 1.0.1
    Publisher: Brian Pruitt-Goddard
    VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=bpruitt-goddard.mermaid-markdown-syntax-highlighting


### pandoc 관련 설정

나눔고딕폰트로 변경한 레퍼런스 파일은 ```https://github.com/nullvana/pandoc_ref_docx/raw/master/reference.docx```에서 다운받을 수 있습니다.

```sh
git clone https://github.com/nullvana/pandoc_ref_docx.git ~/.pandoc
```

```json
    // vscode settings.json
    "pandoc.pdfOptString": "-V mainfont='KoPubWorldDotum_Pro' -V sansfont='KoPubWorldBatang_Pro' -V monofont='D2Coding' -V papersize=a4 -V fontsize=11pt -F mermaid-filter --pdf-engine=xelatex --toc",
    "pandoc.docxOptString": "-F pandoc-docx-pagebreakpy --reference-doc ~/.pandoc/reference.docx ",
    "pandoc.htmlOptString": "-F mermaid-filter",
```

```sh
# mermaid 설정을 하려면 작업경로(/doc)에 아래와 같은 파일을 생성한다.
cat > .mermaid-config.json
{
    "startOnLoad": true,
    "flowchart": {
        "useMaxWidth": false,
        "htmlLabels": true
    },
    "sequence": {
        "height": 40,
        "actorMargin": 80,
        "mirrorActors": false,
        "bottomMarginAdj": 1
    },
    "theme": "forest",
    "themeCSS": ".node rect { fill: red; }"
}
```
