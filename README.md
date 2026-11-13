# Simulador de Consórcio com Lance

**Desenvolvido por Roger Caires**

🔗 **Acesse:** https://rogercaires11.github.io/Simulador-consorcio-case/

![Tela do simulador](screenshot.png)

Ferramenta web que calcula, junto com o cliente, **quanto fica a parcela de um consórcio depois da contemplação com lance**. Mostra as opções de reduzir parcela, reduzir prazo ou um prazo personalizado e compara com um financiamento.

---

## O problema

Na venda de consórcio, a primeira pergunta do cliente é: *"se eu der um lance, quanto vou pagar depois?"*. Na prática, o gerente:

- faz a conta na mão ou em planilhas soltas, o que gera erro e retrabalho;
- mostra **um número só**, baseado num mês de contemplação que é um chute;
- compara o consórcio com um financiamento de forma enviesada, sem contar as parcelas pagas antes da contemplação nem o aluguel pago durante a espera;
- não consegue mostrar a diferença real de custo entre **reduzir parcela** e **reduzir prazo**.

## A solução

Uma página única, sem login e sem instalação, que funciona no celular durante a reunião e entrega:

| Funcionalidade | O que resolve |
|---|---|
| **Cota nova × cota existente** | Para quem já está no grupo, usa os dados do extrato (% pago e carta atual). A simulação deixa de depender de premissa. |
| **"E se for contemplado em outro mês?"** | Mostra a parcela para contemplação nos meses 6, 12, 24, 36 e seguintes, em vez de um número só. |
| **Total hoje × total projetado** | Considera o reajuste anual e o seguro, e assim mostra quanto reduzir prazo economiza em relação a reduzir parcela. |
| **Lance livre, embutido e FGTS** | Limite do embutido e base do % do lance (categoria, carta ou saldo devedor) configuráveis conforme o regulamento. |
| **Dados do grupo** | Chance de sorteio em 12 e 24 meses e posição do lance em relação ao histórico de vencedores. |
| **Calculadora reversa** | Dado um % de lance-alvo, quanto precisa de embutido, FGTS e recursos próprios. |
| **Consórcio × financiamento** | SAC ou Price, comparando a jornada inteira: parcelas antes da contemplação, lance, aluguel durante a espera e CET. |
| **Resumo para WhatsApp e PDF** | O cliente leva a simulação, com as premissas explícitas. |

## Decisões de produto

- **Honestidade antes de conversão:** a premissa do mês de contemplação aparece na tela, no resumo e no PDF. A ferramenta mostra quando o financiamento sai mais barato.
- **Privacidade (LGPD):** o nome do cliente **não é salvo** em lugar nenhum. O navegador guarda só os parâmetros numéricos.
- **Zero atrito:** um único arquivo HTML, sem backend, sem login e sem custo de hospedagem.
- **Não vinculante por design:** é uma ferramenta de apoio à conversa comercial. A simulação oficial é sempre a proposta da administradora.

## Como o cálculo funciona (resumo)

O consórcio é controlado em **percentuais do valor do bem**, não em reais.

- **Categoria** = 100% + taxa de administração + fundo de reserva.
- **Parcela integral** = categoria ÷ prazo. Na parcela reduzida, só o fundo comum é reduzido.
- **Saldo após o lance** = saldo devedor − (lance ÷ carta atualizada).
- **Reduzir parcela:** saldo ÷ meses restantes. **Reduzir prazo:** mantém a parcela integral e amortiza de trás para frente.
- **Reajuste:** aplicado a cada 12 meses sobre a carta e o saldo, inclusive depois da contemplação.
- **Custo efetivo:** taxa interna de retorno (TIR) dos fluxos de parcelas, lance e crédito recebido.

### Caso de teste de referência
Carta de R$ 100.000, 100 meses, taxa de administração de 18%, fundo de reserva de 2%, contemplação no mês 12 e lance de R$ 30.000 em recursos próprios:

- Reduzir parcela → **R$ 859,09 × 88 meses**
- Reduzir prazo → **R$ 1.200,00 × 63 meses**
- Com reajuste de 6% a.a., reduzir prazo custa **cerca de R$ 6 mil a menos** no total projetado.

## Como usar

1. Escolha **cota nova** ou **cota existente**.
2. Preencha os dados do plano e o lance.
3. Escolha como abater: reduzir parcela, reduzir prazo ou personalizar.
4. Mostre ao cliente a tabela de outros meses de contemplação e, se fizer sentido, a comparação com o financiamento.
5. Copie o resumo para o WhatsApp ou salve em PDF.

## Tecnologias

HTML, CSS e JavaScript puro, num único arquivo. Gráfico em SVG próprio, sem bibliotecas externas. Hospedado no GitHub Pages.

## Aviso

Simulação de apoio comercial, **não vinculante**. Taxas, limites de lance, base do embutido, regras de rateio e índices de reajuste variam por grupo. Confirme sempre na proposta oficial e no regulamento do grupo.

---

**Roger Caires** · Gerente de Relacionamento · em transição para Produto Digital e IA
