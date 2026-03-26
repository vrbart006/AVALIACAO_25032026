# Avaliação — Engenharia de Software
## Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante

- Aluno: Vitor Leoncio Bartalini
- RA: 25000095
- Data: 25/03/2026

## 1. Definição do MVP

### O que está dentro do MVP:
- O foco deste MVP é a Operação de Venda e Gestão Básica de Estoque/Clientes. Onde
inclui consulta de produtos, validação e baixa automática de estoque, identificação
e cadastro de clientes, processo de venda e emissão de comprovante.
### O que está fora do MVP:
- Módulos de retaguarda como compras com fornecedores, contas a pagar e relatórios
gerenciais da matriz.
### Por que você fez essas escolhas:
- Para focar na operação de balcão onde garante que a entrada de receita ocorra sem atritos e
que o estoque passe a ser confiável imediatamente após as vendas, resolvendo o problema mais
urgente da farmácia.



## 2. Regras de Negócio (mínimo: 5)
Liste e descreva cada RN de forma clara.

RN01 — Produtos com estoque igual a zero não podem ser vendidos.
RN02 — A venda de medicamentos controlados exige autorização de um Farmacêutico.
RN03 — O saldo do estoque deve ser reduzido automaticamente no momento do pagamento.
RN04 — Vendas a prazo devem gerar lançamento automático em "Contas a Receber" com status "Aberta".
RN05 — O sistema deve disparar um alerta visual ao atingir o estoque mínimo de um item.



## 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

RF01 — Permitir a consulta de produtos por nome, código de barras ou fabricante.
RF02 — Exibir a quantidade em estoque do produto pesquisado.
RF03 — Permitir a identificação de cliente pelo CPF.
RF04 — Permitir o cadastro de novos clientes.
RF05 — Calcular o total da venda e permitir escolha de pagamento.
RF06 — Registrar lançamentos financeiros para compras a prazo.
RF07 — Exigir credenciais de Farmacêutico para validar receitas médicas.
RF08 — Emitir comprovante de venda ao final da compra.



## 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

RNF01 — A consulta de estoque deve responder em até 5 segundos.
RNF02 — O sistema deve ter controle de acesso baseado em perfis.
RNF03 — Vendas de controlados devem registrar o ID do farmacêutico responsável.
RNF04 — O sistema deve garantir disponibilidade no horário comercial.



## 5. Casos de Uso (mínimo: 10)
Inserir diagrama de casos de uso geral, demonstrando claramente:
os 10 casos
relação entre eles e atores
pelo menos 3 includes
pelo menos 3 extends



## 6. Documentação dos Casos de Uso
Para cada caso de uso, utilize o template abaixo:
# UC01 — Realizar venda

Ator(es): atendente.
Descrição: registra produtos no balcão.

Pré-condições: atendente logado.
Pós-condições: venda concluída e atualização de produtos no estoque.

Fluxo Principal
FP01. Inicia venda.
FP02. Adiciona produtos.
FP03. Finaliza itens.
FP04. Sistema atualiza estoque.
FP05. Emite comprovante.

Fluxos Alternativos / Exceções
FA01 — Cancelar antes do pagamento
Relacionamentos
Include: UC05, UC07, UC08
Extend: UC09

============================================================================

# UC02 — Consultar produto

Ator(es): atendente.

Fluxo Principal
FP01. Digita o nome/código do produto.
FP02. Sistema busca no estoque.
FP03. Exibe produto no estoque.

============================================================================

# UC03 — Identificação de clientela

Ator(es): atendente.
1. Solicita CPF. 2. Sistema busca. 3. Confirma nome e vincula à venda.

Fluxo Principal
FP01. Solicita o CPF.
FP02. Sistema começa a buscar.
FP03. Confirma a venda e vincula a venda.

Fluxos Alternativos / Exceções
FA01 — Cliente não encontrado (pede ajuda para o AC04 - extend).

============================================================================

# UC04 — Cadastro de clientes

Ator(es): atendente.

Fluxo Principal
FP01. Insere nome, CPF e telefone.
FP02. Valida e salva.
FP03. Retorna a operação.

============================================================================

# UC05 — Registro de pagamento

Ator(es): atendente.

Fluxo Principal
FP01. Mostra o total.
FP02. Seleciona forma de pagamento.
FP03. Confirma pagamento.

Fluxos Alternativos / Exceções
FA01 — Pagamento a prazo (pede ajuda ao UC06 - extend).

============================================================================

# UC06 — Registro de contas

Ator(es): Sistema.

Fluxo Principal
FP01. Coleta dados.
FP02. Gera lançamento.
FP03. Salva como aberta.

============================================================================

# UC07 — Atualizar estoque

Ator(es): Sistema.

Fluxo Principal
FP01. Identifica itens vendidos.
FP02. Subtrai do saldo.

Fluxos Alternativos / Exceções
FA01 — mínimo do mínimo (pede ajuda ao UC10 - extend).

============================================================================

# UC08 — Comprovante
Ator(es): Sistema.

Fluxo Principal
FP01. Formata itens.
FP02. Manda pra impressora.

============================================================================

# UC09 — Comprovante
Ator(es): Farmacêutico.

Fluxo Principal
FP01. Trava venda.
FP02. Pede credenciais de Farmacêutico.
FP03. Libera produto.

============================================================================

# UC10 — Alerta de estoque mínimo
Ator(es): Sistema.

Fluxo Principal
FP01. Detecta limite.
FP02. Gera alerta para o Gerente.

============================================================================


