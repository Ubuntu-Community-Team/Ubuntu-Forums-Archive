---
title: "Hp Dv6058cl On Feisty Fawn"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by JOAO_JR on 2007-08-13
Pessoal, adquiri um note HP, do modelo especificado no assunto - PARA MAIS DETALHES DO NOTE, ACESSE

[http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN)

e estou penando pra instalar o linux. A minha distro de coração é o ubuntu, mas ainda ñ consegui ter o linux estável nesse note (HP, DV6000, NUNCA +). Já Mandei vários e-mails pra v se consigo alguma solução, mas nada, entaum, como sou brasileiro, ubunteiro e nunca desisto, resolvi mais uma vez, relatar neste fórum o ocorrido. Bem, assim q comprei-o, detonei logo o windows e instalei o ubuntu 7.04 32bits com kernel genérico, lí q pra rodar o live cd tinha q colocar o parâmetro noapic nolapic (isso devido a uma falha de implementação ACPI), entaum segui os passos e deu td certo. Mas aí começaram os problemas. Primeiro, o sistema começou a travar, aí descobri num blog q se eu atualizasse a BIOS resolveria esse problema, ñ pensei duas vezes, formatei o hd e instalei o XP pra poder fazer a atualização da BIOS (de F.18 para F.28), na mesma hora, formatei novamente o hd e instalei o ubuntu 32bits de novo. Bem...d fato os travamentos pararam, mas aí começou aparecer outro problema, os aplicativos fechavam-se inesperadamente, o firefox, a janela do terminal. Se estava fazendo um apt-get update, bummm, fechava a janela no meio da atualização, se estava lendo algum artigo no firefox, bummm, fechava tb, e quando queria abri-lo novamente, até tentava, mas algo, q ñ consegui descobri o q é, ñ deixava, mas enfim, isso me causava muita raiva e transtorno Zangado. A mensagem de erro q estava dando quando era essa:

*Starting powernowd…
/etc/rc2.d/s20powernowd: 156:cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: directory nonexistent
*cpu frequency scaling not supported
*running local boot scripts (/etc/rc.local)

Pessoal, ñ sei exatamente se era por causa dessa mensagem q os aplicativos se fechavam inesperadamente, mas foi isso q apareceu.

Então eu pergunto a todos os usuários desse fórum. Alguém sabe algo sobre isso, vcs já viram essa mensagem, e sabem como solucionar? Hein?

Bom, depois de tantas formataçoes, o único S.O. q consigo instalar e q faz o note ficar estável, é o XP, Alguém sabe qual outro parâmetro q seja diferente de noapic nolapic (pois já tentei instalar o ubuntu 64bits com eles e ñ deu certo)pra instalar o ubuntu 64bits nesse note?

POR FAVOR PESSOAL Chocado SE SOUBEREM DE ALGO, ME RESPONDAM (juniorsalgado@gmail.com ou [email]kidushin@hotmail.com[/email]), JÁ CANSEI DE FORMATAR MEU HD PRA TER Q INSTALR O XP, PRA Ñ FICAR COM O NOTE PARADO. Q COISA HORRÍVEL.

Grande abraço.

João Junior Salgado.

---

