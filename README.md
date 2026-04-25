## Sobre esta pesquisa
Investigação técnica sobre o panorama da acessibilidade digital, analisando o impacto jurídico de negligências, os padrões de líderes globais (Microsoft, Apple, Google) e a maturidade de empresas nacionais frente às diretrizes WCAG.

## O que descobrimos (Principais Achados)
* **O custo da negligência é real e alto:** Empresas como a ENEL (Brasil) e Vueling Airlines (Espanha) sofreram multas que variam de €90.000 a R$ 1,2 milhão por falhas graves de acessibilidade em seus portais. *(Fonte: MPCE / Accessible EU Centre)*.
* **Shift-Left como padrão de excelência:** Líderes de mercado como Microsoft e Apple não tratam acessibilidade como um "recurso extra", mas como parte da arquitetura básica do produto (Inclusive Design), o que reduz custos de manutenção e evita processos judiciais. *(Fonte: Microsoft Accessibility)*.
* **Complexidade técnica vs. Semântica:** O aumento da complexidade de frameworks e bibliotecas modernas é uma das principais causas de barreiras digitais, conforme o relatório WebAIM Million, que aponta erros básicos em 96% dos sites. *(Fonte: WebAIM Million )*.
* **Lacunas na acessibilidade nacional:** Empresas brasileiras analisadas apresentam maturidade parcial; enquanto a JBS RI foca em acessibilidade visual e motora, o PicPay prioriza o atendimento humano em Libras, mas carece de recursos de interface assistiva no app/site. *(Fonte: RIJBS PICPAY, Pesquisa Acessibilidade Digital - Pedro)*.

## Ferramentas / Casos / Legislação (Mapa Comparativo)

| Empresa / Entidade | Categoria | Status / Ferramenta | Impacto / Prática |
| :--- | :--- | :--- | :--- |
| **Microsoft** | Líder Tech | Microsoft 365 Copilot / ACRs | Acessibilidade integrada via IA e conformidade com Section 508. |
| **Apple** | Líder Tech | VoiceOver / AssistiveTouch | Acessibilidade nativa no SO ("Accessible by Design"). |
| **W3C** | Padrão | WCAG 2.1 / 2.2 | Definição técnica de critérios de sucesso (A, AA, AAA). |
| **ENEL** | Caso Jurídico | Multa de R$ 1,2 mi (2024) | Inviabilidade de uso do site por PCDs para serviços essenciais. |
| **Vueling Airlines**| Caso Jurídico | Multa de € 90 mil | Impossibilidade de compra autônoma de passagens. |
| **Google** | Ferramenta | Lighthouse / Accessibility Scanner | Automação de testes para identificar falhas de contraste e semântica. |

## Como isso afeta o nosso trabalho como desenvolvedores
A acessibilidade não é um "favor" ao usuário, mas um requisito técnico de qualidade de código. Para o time, as mudanças práticas são:

### 1. Semântica em primeiro lugar
Evitar o uso de `<div>` ou `<span>` para elementos clicáveis. O uso de tags nativas garante que o leitor de tela entenda a função do elemento sem esforço extra.
```html
<div onclick="submitForm()" class="btn">Enviar</div>

<button type="submit">Enviar</button>
```

### 2. Gestão de Foco e Navegação por Teclado
Garantir que todos os elementos interativos sejam acessíveis via `Tab` e que o indicador de foco (`outline`) nunca seja removido via CSS sem uma alternativa visual clara.
```css
/* Jamais fazer isso */
*:focus { outline: none; }

/* Correto: Estilizar o foco para combinar com a marca */
.button:focus {
  outline: 3px solid #0056b3;
  outline-offset: 2px;
}
```

### 3. Textos Alternativos e ARIA Labels
Imagens informativas devem ter `alt` descritivo. Para componentes complexos (como modais ou menus hambúrguer), usar atributos ARIA para comunicar estados (aberto/fechado).
```html
<img src="chart-vendas.png" alt="Gráfico de colunas mostrando crescimento de 20% nas vendas em abril">

<button aria-expanded="false" aria-controls="menu-mobile">
  Menu
</button>
```

## Referências
1.  **W3C.** Web Content Accessibility Guidelines (WCAG) 2.2. 2023. Disponível em: [https://www.w3.org/WAI/standards-guidelines/wcag/](https://www.w3.org/WAI/standards-guidelines/wcag/)
2.  **MINISTÉRIO PÚBLICO DO ESTADO DO CEARÁ (MPCE).** Decon multa ENEL em mais de R$ 1,2 milhão por falta de acessibilidade. 2024. Disponível em: [https://www.mpce.mp.br/](https://www.mpce.mp.br/)
3.  **MICROSOFT.** Microsoft Accessibility: Inclusive Design. 2024. Disponível em: [https://www.microsoft.com/accessibility](https://www.microsoft.com/accessibility)
4.  **WEBAIM.** The WebAIM Million 2024: An accessibility analysis of the top 1,000,000 home pages. 2024. Disponível em: [https://webaim.org/projects/million/](https://webaim.org/projects/million/)
5.  **USERWAY.** The Domino’s Verdict: Robbins v. Domino’s Pizza Case Study. 2022. Disponível em: [https://userway.org/blog/the-dominos-verdict/](https://userway.org/blog/the-dominos-verdict/)