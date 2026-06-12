---
title: "Problem: Printer HP Deskjet F2480 with ubuntu 9.10"
date: 2009-12-26
forum: Hardware
---

### Post by giombojb on 2009-12-26
Hi!! I'm new here, and this is my problem:

I installed HP Deskjet F2480 Printer in Ubuntu 9.10 following instructions in this site:

[http://www.icelab.eu/blog/ubuntu-e-linux-12/installare-una-stampante-hp-su-ubuntu-79.htm](http://www.icelab.eu/blog/ubuntu-e-linux-12/installare-una-stampante-hp-su-ubuntu-79.htm)
[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html) (english)

(I'm Italian)

after many attempts I was succesful, now the printer work, (it's slow torecive commands) 

[COLOR=Navy]**EVERY TIME**** I TURN ON THE PRINTER IT AUTOMATICALLY PRINT THE ALLIGNMENT PAGE, AND ALSO WHEN I PRINT ANY OTHER PAGE, AFTER THE JOB, IT DO THE SAME. **[/COLOR]

when i wrote in the terminal [COLOR=Red]dpkg -l hplip[/COLOR]:

[COLOR=Red]Desiderato=Unknown/Install/Remove/Purge/Hold
| Stato=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(nessuno)/Reinst-required (Stato,Err: maiuscolo=grave)
||/ Nome                     Versione                 Descrizione
+++-========================-========================-================================================================
rc  hplip                    3.9.8-1ubuntu2           HP Linux Printing and Imaging System (HPLIP)[/COLOR]

please help!!

nicola

---

### Post by jack.herbert on 2010-01-15
Hi nicola,

I have exactly the same printer, never had that test page printing problem so the following will probably be useless for you. just in case...

I found some instructions [here]("http://forums.linuxmint.com/viewtopic.php?f=49&t=38664&p=224886&hilit=hplip+deskjet") I know it's for Linux Mint 8 but it's based on Ubuntu 9.10.
The interesting bit is when he talks about clashing cups/cups-sys/etc. For it to work I had to remove one of them. Since you are printing already, it's unlikely that's your problem.
At the start of the post, he makes reference to the HP guide for Mint, is which basically a manual install guide I think. Who knows, manually installing hplip might help.

Actually, come to think about it, I also have Ubuntu 9.10 on another partition and I think I followed [those]("http://koroshiyaitchy.wordpress.com/2009/11/23/installing-hplip-3-9-10-in-ubuntu-karmic-koala-in-order-to-obtain-support-for-the-hp-deskjet-f2480-series/") instructions. It prints fine there too.

You probably know that, but this printer is only supported with  hplip 3.9.1+
Did you get any error messages with the automatic installer?
I'm fairly ignorant with linux things but it sounds as if your printer was detected as a new one everytime you send a print job, calibrating (waiting time) and testing it every time.

Sorry if this wasn't helpful and good luck
Arivedechi :)

---

