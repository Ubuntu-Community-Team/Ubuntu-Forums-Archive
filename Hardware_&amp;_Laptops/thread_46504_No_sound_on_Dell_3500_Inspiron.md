---
title: "No sound on Dell 3500 Inspiron"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by mrbaz on 2005-07-05
Dell Inspiron 3500
400MHz PII M

I can't get the sound to work.  Everything else works fine, even the Linksys ethernet PC card.

I can't get alsamixer to run.  When I try and run it under command line it comes back saying:
'function snd_ctl_open failed for default: no such device'

---

### Post by andlinux21 on 2005-07-05
Have you tried any of the HOWTOs? if so do you know what type of soundcard you have so we can attempt to help you.

---

### Post by andlinux21 on 2005-07-05
Hey I also found this link it may help you with the sound problem

[http://www.post1.com/home/kal/inspiron3500.html](http://www.post1.com/home/kal/inspiron3500.html)

 :roll:

---

### Post by mrbaz on 2005-07-10
[QUOTE=andlinux21]Hey I also found this link it may help you with the sound problem

[http://www.post1.com/home/kal/inspiron3500.html](http://www.post1.com/home/kal/inspiron3500.html)

 :roll:[/QUOTE]
 I still can't get my sound to work. 
Let me ask you this:
During the boot sequence, it gets to a point where it's loading some sort of package/module and the computer system speaker beeps steadily like if you input a wrong command or something.  It then eventually stops (after about 5seconds) and then boots normally.

---

### Post by andlinux21 on 2005-07-10
is there any way you can capture or type part of that logup message??

---

### Post by mrbaz on 2005-07-11
[QUOTE=andlinux21]is there any way you can capture or type part of that logup message??[/QUOTE]

I'll have to use my digicam, but yes.  It's not really an error message.  It's just some time during the boot sequence it acts like an invalid command was entered.  I'll post a pic later.

---

### Post by mrbaz on 2005-07-13
Sorry about not having a pictures capture yet.  I need to get my digicam.
I did note, however, that when it starts beeping it says something about loading amixer, and then saying: "Invalid card number"
It then gives a list of available commands.

What does that mean?  :-?

---

### Post by Aaron.42 on 2005-07-16
I have and Inspiron 3500 and am having the same problems too.  I would like to get it fixed but in the short term I would settle for no sound if I could get rid of the beeping when starting up and shutting down.

---

### Post by mlord on 2005-07-18
I have not tried Ubuntu on my ancient i3500, but I do still have notes from the very old Redhat  system that used to be on it.  At that time, it was necessary to supply kernel module parameters for the sound system, because it does not have full plug'n'play hardware.

The (old) settings I needed are here (below) -- perhaps a modern reincarnation of these is needed on your machine.  These were from /etc/modules.conf:

alias sound ad1848
pre-install sound insmod sound dmabuf-1
alias midi opl3
options opl3 io=0x388
options ad1848 io=0x530 irq=5 dma=0 dma2=1

The numbers on that last line above are controlled partially by the system BIOS settings, so you will have to customize those to match how the CMOS setup is done on your machine.

Cheers

---

### Post by klyick on 2006-03-07
I have the same issue, bump for no solution.

---

