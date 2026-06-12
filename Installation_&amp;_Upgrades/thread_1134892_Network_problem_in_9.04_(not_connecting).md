---
title: "Network problem in 9.04 (not connecting)"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by damyhonn on 2009-04-24
Olá pessoal.
Acabei de instalar o Jaunty mas o danado não consegue achar minha conexão de rede. Fica o tempo inteiro informando que não há conexão na rede com fios (mas tenho um modem a cabo ligado ao pc). Quando entro no windows tudo ocorre perfeitamente, a conexão dhcp é encontrada sem problemas.
Eu sempre encontrava problema semelhantes em todas as versões do Ubuntu que eu instalava aqui. Mas sempre resolvia seguindo esses passos. Inclusive quando instalei essa nova, tbm tive o mesmo problema da antiga versão de incrementar o valor do eth0 a cada boot (eth1, eth2, eth3, etc). Esse problema eu consegui resolver seguindo o tutorial, mas ainda assim ele não encontra rede. É como se ele não soubesse que o cabo tá conectado.
Alguém passou por algo semelhante ou tem alguma solução?

Agradeço muito!

Hi all.
I've just installed Jaunty but it can't find my network connection. 
I have a Motorola SB5101 cable modem configured in dhcp and in Windows it works great but Ubuntu shows me that I'm not connected to anything, like a disconnected cable.
I notice, btw, that in every boot my network card changes its name (eth1, eth2, eth3,...).
I'll apreciate any help.
Thanks!

---

### Post by GJLenon on 2009-04-24
Have you tried using a different networking agent than Nautilus?  I know that in 64-bit, my Nautilus will not recognize many of the computers on my network.

---

### Post by damyhonn on 2009-04-24
Thanks for the answer GJLenon.

But.. how can I change my networking agent?
Sorry if it is an already answered question.
Thanks again.

---

### Post by ManuC on 2009-04-24
Paste into this thread the output of:

ifconfig
cat /etc/network/interfaces

---

### Post by damyhonn on 2009-04-24
Thanks all! I'm getting desperate to use my Jaunty. =/

```
damyhonn@damyhonn-pc:~$ ifconfig -a
eth1      Link encap:Ethernet  Endereço de HW 00:00:6c:97:04:ef  
          endereço inet6: fe80::200:6cff:fe97:4ef/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:13181 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:11 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:848603 (848.6 KB) TX bytes:2222 (2.2 KB)
          IRQ:253 Endereço de E/S:0x8000 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:4 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:4 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  Endereço de HW 9e:b7:9b:c6:a7:a0  
          BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

===================

```
damyhonn@damyhonn-pc:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by willgrant on 2009-04-24
I am in the same boat.  With the same settings as listed above.

---

### Post by rgeddes on 2009-04-24
Hi,

 I had the same problem that you are describing, and found this bug reported and confirmed at 

[https://bugs.launchpad.net/ubuntu/+bug/343898]("https://bugs.launchpad.net/ubuntu/+bug/343898")

at the bottom of the page is a link to a workaround: 

[https://help.ubuntu.com/community/AppArmor#Disable%20one%20profile]("https://help.ubuntu.com/community/AppArmor#Disable%20one%20profile")

after doing the workaround, I ran 
```
sudo dhclient eth0
```
and the dhcp was able to assign a lan address to my card.

The bug was reported on 2009-16-03... I'm surprised they let that one slip by.. maybe it affects a small group of people

Regards,
Richard

---

### Post by rgeddes on 2009-04-24
Apparently that was not enough to clean up my problem after a reboot ... the apparmor code for dhclient still loads... 

to get around this problem I moved the file sbin.dhclient3 into the disable directory:

```
sudo mv /etc/apparmor.d/sbin.dhclient3 /etc/apparmor.d/disable
```

it looks like that symlink to the disable directory doesn't disable it on start up

After I moved the file into the disable directory, I got a good dhcp'd boot

Regards,
Richard

---

### Post by damyhonn on 2009-04-25
Thank you for answers.
I'm currently away from home and I can't test these solutions. But after this weekend I will try it.
Good weekend you all!
:popcorn:

---

### Post by damyhonn on 2009-04-27
Hi all.
Unfortunately I couldn't fix the problem.
=/
I think my problem is simple to fix but I couldn't understand very well the solution proposed by Richard (thanks, btw).
I tried the "DISABLE ONE PROFILE" solution proposed [here]("https://help.ubuntu.com/community/AppArmor#Disable%20one%20profile"), but my ubuntu didn't recognize '-R' option and when I try with '-r' it shows me that "sbin.dhclient3" isn't a folder (or something like that).
That's what I tried:
```
ln -s /etc/apparmor.d/sbin.dhclient3 /etc/apparmor.d/disable/ apparmor_parser -R /etc/apparmor.d/sbin.dhclient3
```

Is it right?
I'm a kind of newbie in linux and I don't understand very well all this solution.
After that I tried the codes Richard told:
```
sudo dhclient eth0
```
and
```
sudo mv /etc/apparmor.d/sbin.dhclient3 /etc/apparmor.d/disable
```
but whitout success.
I'll apreciate if Richard or someone else could tell me exactly how to fix this bug, with all commands to paste in shell (console).
Thank you very much.
I'm so anxious to make use of my new Ubuntu. But, until now, nothing! :(

---

### Post by Gazoo01 on 2009-04-28
```
sudo mv /etc/apparmor.d/sbin.dhclient3 /etc/apparmor.d/disable
```



Thanks, Richard: this solved the connection problem I was having after upgrading.:KS

---

### Post by drelyn86 on 2009-04-30
> **damyhonn said:**
> Hi all.
Unfortunately I couldn't fix the problem.
=/
I think my problem is simple to fix but I couldn't understand very well the solution proposed by Richard (thanks, btw).
I tried the "DISABLE ONE PROFILE" solution proposed [here]("https://help.ubuntu.com/community/AppArmor#Disable%20one%20profile"), but my ubuntu didn't recognize '-R' option and when I try with '-r' it shows me that "sbin.dhclient3" isn't a folder (or something like that).
That's what I tried:
```
ln -s /etc/apparmor.d/sbin.dhclient3 /etc/apparmor.d/disable/ apparmor_parser -R /etc/apparmor.d/sbin.dhclient3
```

Is it right?
I'm a kind of newbie in linux and I don't understand very well all this solution.
After that I tried the codes Richard told:
```
sudo dhclient eth0
```
and
```
sudo mv /etc/apparmor.d/sbin.dhclient3 /etc/apparmor.d/disable
```
but whitout success.
I'll apreciate if Richard or someone else could tell me exactly how to fix this bug, with all commands to paste in shell (console).
Thank you very much.
I'm so anxious to make use of my new Ubuntu. But, until now, nothing! :(

Have you tried getting DHCP _after_ moving the file?

---

