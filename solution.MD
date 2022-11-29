# SRE avaliação (Migração)

O processo utilizado para migração será baseado no improve-and-move, onde durante migração iremos manter a integridade dos dados mas utilizando recursos nativos da nuvem aprimorando o desempenho e experiência dos usuários na utilização da aplicação.

# Passaremos por 3 etapas:

1 - Etapa Assessement
Onde iremos levantar todos os dados referente a aplicação, arquitetura, linguagem utilizada, dependências da aplicaçao e avaliar desempenho do aplicativo atualmente.

2- Planejamento
Definir estrutura básica, como região, rede, identidade de acesso, alinhamento sobre ondas da migração junto com os times envolvidos.

3- Deploy
Execução de uma carga para homologação e após homologada realizar a virada.


# Recursos utilizados :

Amazon CloudFront - Para melhorar o desempenho, prevenção contra ataque DDOS e diminui a latência na entrega do conteúdo para os usuários. 

AWS WAF — Replicar regras de liberação e bloqueio baseada em ACL, trabalhando junto com o CloudFront.

Load Balancer - ficando responsável por receber o tráfego e aonde aplicamos as re e encaminhar para o ASG.

Vpc -  Com public subnet para EC2  e private subnet para o database. 

Amazon EC2 — Vm virtualizada com s.o distribuição linux, php e apache instalados e restore do último bkp da aplicação.

Aws IMI -  Imagem da VM para o ASG

Auto Scaling Group — Para garantir a escalabilidade e resiliência da aplicação em caso de falhas.

Compute Node Oracle RAC - Nativamente o AWS RDS não tem suporte para Oracle RAC, mas temos a opção no marketplace de adqquirir o Compute Node Oracle RAC que ira criar toda a estrutuar dos clusters da Oracle dentro das EC2. Uma outra opção seria entender com o time de DBA o esforço para fazer "Replataform" para o Amazon RDS for Oracle.

Amazon CloudWatch — Após a definição dos indicadores para monitoramento, podemos criar paineis e alertas para tomadas de decisões e controle do ambiente. Ec2, LB, VPC...

Amazon CloudTrail - Pensando em governança,complience ativaremos esse reecurso para auditar os acessos  onde será armazenado a cada 15 min eventos sobre  "quem" acessa o "que".

Amazon S3 -  Armazenamento dos logs coletados pelo Cloud Trail e armazenamento do conteúdo estático da aplicação.
