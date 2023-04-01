# `Inteliplanta`
# `Plant Grower`

## Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de graduação *EA075 - Sistemas Embarcados*, 
oferecida no segundo semestre de 2022, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

Incluir nome RA e foco de especialização de cada membro do grupo. Os projetos devem ser desenvolvidos em duplas.
|Nome  | RA | Curso|
| --- | --- | --- |
| Rafael Domingos Nascimento Molina Ogallas  | 176121  | Eng. Elétrica |
| Rodrigo Toshio Ogasawara Tahara | 205578  | Eng. Elétrica |


## Descrição do Projeto
> Descrição do objetivo principal do projeto, incluindo contexto gerador, motivação.
> Escreva essa seção imaginando que está tentando convencer alguém a investir financeiramente no seu projeto.
> Qual problema vocês pretendem solucionar?
> Quem são os potenciais usuários?
> É possível estabelecer um valor econômico associado?

Plantas em casa são a sensação de paz e vida no ambiente, mas, para sempre reluzirem verde, precisam do cuidado constante e especifico. Aguamento constante e na proporção, iluminação adequada e suficiente, umidade do local, e mesmo o monitoramente de nutrientes, são fatores que possuem maior ou menor peso para cada diferente espécies, aumentando a dificuldade dos cuidados.
Tantos fatores são determinantes para uma planta constantemente viva, verde e vigorosa, e um ambiente harmonizado.
 * Para algumas espécies, alguns dias ou um fim de semana sem aguamento é suficiente para que a planta resseque ou morra.
 * Muitas plantas adoecem e morrem pela falta de iluminação suficiente e não podem preencher o interior dos ambientes.
 * Quando expostas a um ambiente com constante incidência solar, algumas plantas adoencem pelo estresse e podem ressecar e morrer.
 * Nem sempre se dispõe de um ambiente externo ou solo para o cultivo. Às vezes ornar o ambiente interno é mais desejável.
 * Após algum tempo algumas plantas adoecem pelo esgotamento dos nutrientes do substrato.
Cuidar de plantas ou com elas ornar a casa é um hábito desejável que nem sempre a ausência de tantos fatores permite possuir.
Todos esses fatores podem ser resolvidos com uma solução automatizada.

Em média para se possuir algumas plantas no interior de uma casa, já considerando que se possua um local adequado. Os valores com as ferramentas, o substrato, os vazos e os aparatos de rega de uma única planta estão em torno de R$200 - 300.
Algumas plantas, como orquídeas, custam de R$50~100 nos melhores preços e comumente adoecem e são substituídas por outras novas. Outras, como cactus adoecem pelo excesso de água. A substituição da planta devido à ausência do cuidado é a solução encontrada.
No interior de empresas, para harmonização de ambientes, os gastos para manutenção e reposição de plantas são constantes. A presença de uma ambientação adequada é a diferença entre uma recepção que cause boa impressão ou sensação de abandono, uma ambiente de trabalho que forneça tranquilidade ou descuido.

De forma geral, bons cuidados com plantas no interior de ambientes significam cuidado com zelo constante e hábilidade, às vezes altos gastos com reposição ou presença constante de profissionais especializados.

Tantos fatores benéficos, para casas e empresas, poderiam ser alcançados por uma solução automatizada, que removesse os cuidados inalcançáveis e mantivessem o experiência vitalizadora da presença das plantas.


## Descrição Funcional
> A descrição funcional do projeto é a principal entrega do E1 e pode ser realizada neste próprio arquivo Markdown,
> com links para diagramas ou outros arquivos que estejam no próprio repositório.

### Funcionalidades
> Detalhe todas as tarefas que o sistema será capaz de executar

1. Umidade do substrato:
    - Medir a umidade do substrato e indicar a falta ou o excesso.
        - Medir a umidade do solo para, plantas em geral.
        - Medir a umidade do ar no interior de raízes ou em superfície, para orquídeas
        - Medir nível de água para espécies com alto aguamento.
    - Fornecer aguação adequada e programável:
        - Quantidade de água configurada por planta
        - Modos de aguamento múltiplos:
            - mangueira e bombeamento direto na solo (plantas em geral).
            - borrifamento leve (orquídeas e similares).
            - espalhamento e simulação de chuva (displays fechados)
2. Iluminação:
    - Medir a iluminação incidente e indicar falta ou excesso de luz.
    - Fornecer iluminação artificial que substitua ou suplemente a iluminação presente.
3. Temperatura:
    - Medir temperatura local e indicar necessidade de intervenção
    - Fornecer aquecimento possível.
4. Tempo:
    - Medir o tempo e fornecer iluminação ou aguamento de acordo com cronograma diário ou semanal.
5. Nutrientes:
    - Medir nutrientes principais e ph do solo, indicando ação necessária.
6. Monitoramento e conectividade:
    - Monitorar medições e armazenar dados da planta com relatório e possível indicação de intervenção.
    - Enviar dados da planta por wifi e monitoramento remoto por API ou aplicativo.
7. Captura, envio e tratamento de imagens:
    - Capturar imagens da planta e torná-las acessíveis remotamente (por API ou aplicativo).
    - Fornecer imagens e informaçãoes do momento atual.
    - Produzir animação timelapse de certos períodos.
    <!-- - Possível avaliação da saúde da planta por tratamento de imagem. -->
    <!-- - Possível identificação automática de espécie. -->

### Configurabilidade
> Detalhe, se houver, todas as possíveis configurações do circuito e todos os pontos de alteração da configuração.

Configurações editáveis no aparelho ou remotamente:
- Configuração customizada de aguamento e iluminação.
- Configurações pré-fornecidas de aguamento e iluminação por espécies mais comuns.

### Eventos
> Quais eventos o sistema deve tratar?
> Se aplicável, classifique os eventos que são periódicos (procure especificar a periodicidade) e os que são não-periódicos
> (qual o tempo mínimo entre dois eventos sucessivos)?

- Aguamento: baixo nível de umidade.
    - intervalos entre atuações de 10 ~ 30min, a variar por espécie.
    -  Identificar nível de umidade crítico e aguar o substrato.
- Iluminação: baixo nível de iluminação.
    - Atuação imediata 100 ~ 1000ms.
    - Atuação durante período do dia (janela de iluminação).
- Identificação de nutrientes:  baixo nível de nutrientes.
    - evento com menor intervalo, de 1 ~ 7 dias entre cada aferimento e indicação.
- Temperatura: temperatura excessivamente baixa.
    - Atuação rápida 10 ~ 30s (a avaliar):


### Tratamento de Eventos
> Qual comportamento o sistema deve ter para tratar corretamente cada evento?

## Descrição Estrutural do Sistema
> Junto com a descrição do comportamento do sistema, deve-se especificar, em nível de bloco ou sistema, a estrutura necessária 
> para captar os eventos do mundo externo, para alojar e processar o programa de tratamento de eventos, e para atuar sobre o mundo externo.
>
> Para essa descrição recomenda-se a criação de diagramas de blocos.
> Nesse diagrama, devem ser destacados os blocos funcionais que compõem o sistema, incluindo uma síntese das funcionalidades de cada bloco.
> Além disso, deve-se esclarecer também o relacionamento entre estes blocos, incluindo os principais sinais de comunicação entre
> os blocos de forma a assegurar a execução de todas as tarefas que o sistema deve realizar.
> 
> Você sabia? Ferramentas como o `draw.io` permitem integração com o Github.
> 

## Referências
> Seção obrigatória. Inclua aqui referências utilizadas no projeto.
