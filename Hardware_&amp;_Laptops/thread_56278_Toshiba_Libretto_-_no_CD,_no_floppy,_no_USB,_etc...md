---
title: "Toshiba Libretto - no CD, no floppy, no USB, etc..."
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by Chiba on 2005-08-11
I decided to blow away XP on my Libretto and install Ubuntu. The machine has no internal removable media drives, and it refuses to boot from a USB CD drive. I've read a variety of hints and got to the stage where I used rawrite/dd to put a floopy image on an old CF card, then tried booting from a PCMCIA adaptor, but that was a no-go too. I'm getting a little frustrated. I think I've read everything that google can find, so need another approach. Can anyone help me out?

Cheers,


Gavin,
Chiba,
Japan

---

### Post by jasmuz on 2005-08-12
Read these threads, they might give you any new idea on how to solve your issue:

[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

[http://www.ubuntuforums.org/showthread.php?t=29555](http://www.ubuntuforums.org/showthread.php?t=29555)

---

### Post by Chiba on 2005-08-12
This is odd. I can boot from a Windows install CD in my external USB CD drive, but not from the Ubuntu CD. Any ideas why? ](*,)

---

### Post by jasmuz on 2005-08-13
Because the Debian installer that the Ubuntu system uses isnt very fond of USB peripherals.

---

### Post by Chiba on 2005-08-14
[QUOTE=jasmuz]Because the Debian installer that the Ubuntu system uses isnt very fond of USB peripherals.[/QUOTE]

Ooh! Works with a different USB CD.

Second problem - screen turns to white noise after I hit "Enter" at the prompt. So, I tried the "linux vga=711 noapic nolapic" trick, and then my screen turns some very interesting purpley colours and starts flashing. Any ideas what I try next?

---

### Post by wvslkr on 2005-08-14
Try vga=normal or 731.

---

### Post by Chiba on 2005-08-15
[QUOTE=wvslkr]Try vga=normal or 731.[/QUOTE]

eNoWork. Still get white static. Logged a bug report. :neutral:

---

### Post by tktreload on 2005-08-15
[QUOTE=Chiba]eNoWork. Still get white static. Logged a bug report. :neutral:[/QUOTE]
 how about removing the hdd from the computer, and putting it in an other computer (you can get those small converter thingies) installing ubuntu and jamming it back in the laptop again?

(remember to install general components so the kernel will match and so on)
just an idea, it seems that you are having a lot of problems...

---

### Post by Chiba on 2005-08-15
[QUOTE=tktreload]how about removing the hdd from the computer, and putting it in an other computer (you can get those small converter thingies) installing ubuntu and jamming it back in the laptop again?

(remember to install general components so the kernel will match and so on)
just an idea, it seems that you are having a lot of problems...[/QUOTE]

Believe me, I've already considered it. The problem is that it's a non-trivial exercise to dismantle the Libretto, and in my particular model it's a 1.8" hard disk, so all things considered I'd rather avoid this. Anyway, I'm kind of forced to ask "why should I?". Hate to say it, but all I'm trying to do is install the OS - I haven't even got to the "missing drivers" stage yet. Even XP can manage this feat...

---

### Post by tktreload on 2005-09-04
ooh belive me you're going to love missing drivers....
missing drivers is the part of the install where you learn the most.

---

