---
title: "Dell Latitude D600 suspend support"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by joele on 2005-06-07
I have installed Hoary 5.04 on my Dell D600 and it is mostly working, the only extra step was obviously the video drivers... The only thing that is not working is suspend/resume support...

If I press the suspend button it seems to suspend but when I press resume it simply reboots... 

If I just close the screen (or press the little screen down lever) the screen just goes blank but does not turn off, when I release the screen down lever, I can enter my password and it is working, but I would expect that as it never really suspended...

If I choose hibernate from 'log off' I get the usual hibernation routine, I then click the power button to resume, it seems to resume from hibernation but the screen is all scrambled when it finishes resuming and the whole computer is locked up so I have to restart....

Has anyone got any of these suspension methods working at all??? Is the ati 3d driver conflicting with hibernation?

---

### Post by byen on 2005-06-07
I have been looking for the same solution for a loooooong time..hope someone answers this!

---

### Post by joele on 2005-06-09
so I take it no one has had success with this laptop??

---

### Post by Alexander Kirillov on 2005-06-09
[QUOTE=joele]so I take it no one has had success with this laptop??[/QUOTE]
 I also have Latitude D600, and suspend to RAM works fine -- but I do not use ATI's proprietary drivers. IIRC, I din't really change anything in my ACPI scripts - except enabling suspend to RAM nad having it suspend on lid close.

---

### Post by joele on 2005-06-09
mmm, must be the drivers causing it? will have to give it a try without them...

---

### Post by joele on 2005-06-10
Well I still can't seem to get suspend to RAM working, but switching from ATI's closed source drivers back to the 'ati' driver that ubuntu installed by default does make hibernation work correctly (except it does stuff up vmware a little)....

---

### Post by Miguel on 2005-06-10
Hello everybody

I own a Dell Inspiron 8600 with an ATi card.

There are a few ACPI features disabled by default in Ubuntu. The most obvious is supsend to RAM. To acivate this, you should uncomment a few lines of /etc/default/acpi-support:

# cd /etc/default
# sudo gedit acpi-default

Well, I use vim, but that's personal prefference. After uncommenting the line, you will surely have the "suspend" option in the gnome Log Out screen after a reboot. It is also possible that it is available just after editing that line, but most probably requires restarting a few services. Anybody?

But this has problems with an ATI card. You have to choose between 3D hardware acceleration (crappy 2D) and ACPI features. It's your choice. 


\begin{moaning}
Personally, I am very close to keeping the ACPI and a backup of my xorg.conf file to use 3D acceleration just when gaming. And I am very pissed with ATI. I paid for a card that offered me ACPI and speed, not one of those.
\end{moaning}

---

### Post by Alexander Kirillov on 2005-06-10
[QUOTE=Miguel]Hello everybody

I own a Dell Inspiron 8600 with an ATi card.

There are a few ACPI features disabled by default in Ubuntu. The most obvious is supsend to RAM. To acivate this, you should uncomment a few lines of /etc/default/acpi-support:

# cd /etc/default
# sudo gedit acpi-default

Well, I use vim, but that's personal prefference. After uncommenting the line, you will surely have the "suspend" option in the gnome Log Out screen after a reboot. It is also possible that it is available just after editing that line, but most probably requires restarting a few services. Anybody?
[/QUOTE]
Yes - restart acpid: 
/etc/inid.d/acpid restart

---

### Post by joele on 2005-06-10
[QUOTE=Miguel]\begin{moaning}
...... And I am very pissed with ATI. I paid for a card that offered me ACPI and speed, not one of those.
\end{moaning}[/QUOTE]

Yeah I only have a laptop wih an ATI card as work paid for it and I had no choice in the model.... On my desktop I have used Nvidia for the last 4 years due to ATI's pathetic support of Linux, infact I always recommend people not to buy ATI  ](*,)

---

