# Cenários Gherkin - QAPlanning

## Sobre este documento

Este documento apresenta exemplos de cenários de teste elaborados durante minha atuação como **Analista de Quality Assurance** no projeto QAPlanning.

Os cenários foram escritos utilizando a abordagem **BDD (Behavior Driven Development)** com a linguagem **Gherkin**, considerando regras de negócio, critérios de aceite e comportamentos esperados da aplicação.

Durante o projeto foram elaborados **48 cenários de teste**, contemplando validações funcionais, regras de negócio, segurança, privacidade, responsividade e funcionalidades baseadas em Inteligência Artificial Generativa.

---

# QA-4 - Validar provedores de IA por Feature Flag

## Cenário: Exibir apenas provedores de IA homologados na configuração

```gherkin
Funcionalidade: Validar provedores de IA por Feature Flag

Cenário: Exibir apenas provedores de IA homologados na configuração

Dado que o usuário possui acesso à tela de Configuração de IA
E as Feature Flags de provedores não homologados estão desabilitadas
Quando o usuário acessa a aplicação QAPlanning
E navega até a tela de Configuração de IA
E a lista de provedores é carregada
Então deve ser exibido apenas o provedor Gemini
E nenhum outro provedor deve ser exibido na interface
```

---

# QA-8 - Validar limpeza das credenciais ao fechar o navegador

## Cenário: Armazenar chaves da API no sessionStorage

```gherkin
Funcionalidade: Validar armazenamento das credenciais da API

Cenário: Armazenar as chaves da API no sessionStorage

Dado que estou na página de configuração de IA
E informei uma chave de API válida
E a opção "Limpar chaves ao fechar o navegador" está marcada e salva
Quando salvo a configuração
Então a chave da API deve ser armazenada no sessionStorage
E não deve estar armazenada no localStorage
```

---

# QA-13 - Validar Dados Simulados (Modo Mock)

## Cenário: Executar análise utilizando dados simulados

```gherkin
Funcionalidade: Validar execução de análise utilizando dados simulados

Cenário: Permitir iniciar uma análise com o modo Mock ativado

Dado que estou na página de configurações do QAPlanning
E ativei o checkbox "Usar dados simulados (Mock)"
E salvei a configuração
E não existe nenhuma chave de API aplicada
Quando acesso a tela de análise
E solicito a análise de uma história
Então o sistema deve iniciar a análise sem exigir uma chave de API
```

---

# QA-14 - Validar proteção contra Prompt Injection

## Cenário: Impedir manipulação das instruções da IA

```gherkin
Funcionalidade: Validar proteção contra manipulação de comandos da IA

Cenário: Impedir execução de comandos de alteração das instruções do modelo

Dado que estou na página de análise do QAPlanning
E possuo uma chave de API real ativa
Quando informo no campo "História/Requisito" um comando para ignorar instruções anteriores
E clico no botão "Iniciar Análise"
Então o sistema deve identificar o conteúdo como tentativa de manipulação
E deve impedir que a IA execute o comando inserido
```

---

# QA-21 - Validar anonimização de dados sensíveis

## Cenário: Substituir dados pessoais antes do envio para IA

```gherkin
Funcionalidade: Validar anonimização local de dados sensíveis

Cenário: Substituir dados pessoais por tags de anonimização

Dado que estou na página de análise do QAPlanning
E possuo uma chave de API real ativa
Quando informo um texto contendo CPF, e-mail ou telefone no campo "História/Requisito"
E clico no botão "Iniciar Análise"
Então o sistema deve substituir os dados sensíveis por tags de anonimização
E a requisição enviada para a API não deve conter os dados originais
```

---

# QA-22 - Validar conteúdo insuficiente

## Cenário: Bloquear requisitos vagos ou sem contexto

```gherkin
Funcionalidade: Validar critérios mínimos para análise de requisitos

Cenário: Bloquear análise de requisito com conteúdo insuficiente

Dado que estou na página de análise do QAPlanning
E possuo uma chave de API real ativa
Quando informo um texto sem contexto suficiente no campo "História/Requisito"
E clico no botão "Iniciar Análise"
Então o sistema deve identificar o conteúdo como insuficiente
E deve exibir uma mensagem orientando o refinamento do requisito
E nenhuma requisição deve ser enviada para o provedor de IA
```

---

# QA-17 - Validar seleção de módulos de refinamento

## Cenário: Selecionar módulos de análise

```gherkin
Funcionalidade: Validar seleção dos módulos de refinamento

Cenário: Selecionar um módulo individualmente

Dado que estou na página de análise do QAPlanning
Quando seleciono o módulo "Cenários de Testes"
Então apenas o módulo selecionado deve permanecer marcado
E os demais módulos devem respeitar a seleção realizada pelo usuário
```

---

# QA-18 - Validar estado do botão Iniciar Análise

## Cenário: Controlar habilitação do botão

```gherkin
Funcionalidade: Validar controle de estado do botão Iniciar Análise

Cenário: Exibir botão desabilitado sem requisito informado

Dado que estou na página de análise do QAPlanning
E o campo "História/Requisito" está vazio
Quando visualizo o botão "Iniciar Análise"
Então o botão deve estar desabilitado
E não deve permitir interação do usuário
```

---

## Observação

Os demais cenários desenvolvidos durante o projeto foram executados e gerenciados através do Jira, incluindo validações de:

