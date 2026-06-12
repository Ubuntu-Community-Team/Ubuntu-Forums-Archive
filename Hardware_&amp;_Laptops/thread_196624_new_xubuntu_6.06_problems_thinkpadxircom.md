---
title: "new xubuntu 6.06 problems thinkpad/xircom"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by rancam on 2006-06-14
Hi,  a fairly new linux guy here.  I just installed the newest xubuntu 6.06 installation and have a problem.  

I had the last version of xubuntu that I installed by the standard server install and apt-get xubuntu-desktop.  After adding " acpi=no apm=no" to the boot "menu.lst" and editing the aliases to "net-pf-10 ipv6 off" my zircom realport ethernet 10/100.  Sound didn't work but I didn't care about it.

When the new xubuntu came out I formatted my drive and installed it off the xubuntu install cd.  I then redid the menu.lst and aliases as I did before and this time the xircom modem did not work.  The little lights on the card do not blink at all or do anything.

I searched for help and saw someone that added pnpbios=off to the command line, I tried it and it did not work.

Any ideas or help?  Thanks in advance.

rancam

---

### Post by rancam on 2006-06-14
A little more searching and I saw someone else had the same problem.  I tried doing what they did "dl'd pcmcia-cs and installed it.  It then said linux 2.6.13-rc1 requries pcmciautils instead of pcmcia-cs.  So I installed pcmciautils and installed it.  

None of this has turned my card on, any ideas?

Rancam

---

### Post by rancam on 2006-06-15
***update on my problem***

I saw that a comment on the board here that removing and placing the pcmcia card back in seemed to help.  I tried it and nothing was listed when I used the ifconfig command.  

I then tried "ifconfig eth0 up" and it showed that eth0.  I then tried to run dhclient and it looks like it is trying to connect but nothing happens and it says "no dhpoffers received,no workign leases in persisten database - sleeping"

Am I getting closer?

rancam

---

