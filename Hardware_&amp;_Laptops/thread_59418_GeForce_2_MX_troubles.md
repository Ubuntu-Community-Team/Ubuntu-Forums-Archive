---
title: "GeForce 2 MX troubles"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by vh1 on 2005-08-23
hey there. I've got this geforce2 card that just doesn't seem to want to work with ubuntu.

I gota a new computer, and first off I just tried running the hoary livecd just because I was bored. but it would hang right before the final boot. the blinking underscore character was all that was shown, only it wasn't blinking. and hitting the numlock key on my keyboard didn't toggle any leds on the keyboard. so the system was completely unresponsive.

I took the card out and just used the integrated chip to install ubuntu, and things are working fine with it. but whenever I put in that card, right before it boots into GDM, the system hangs. I know, I know, "x11 set itself up to use your integrated card (some intel one)." but from past experiences, won't x11 fail and give me an error, as opposed to just hanging?

I would like to try to add the card to my xorg.conf, but I have no way to run a `lspci` command to get the card's slot.

any suggestions?

---

### Post by s_p_a_r_k_y on 2005-08-24
is there a switch in your bios to say which device to use? integrated or AGP/PCI?

---

### Post by vh1 on 2005-08-24
[QUOTE=s_p_a_r_k_y]is there a switch in your bios to say which device to use? integrated or AGP/PCI?[/QUOTE]
 not exactly. you can only choose between AGP and PCI, and this motherboard doesn't even have an AGP slot.

---

### Post by nquinnathome1 on 2005-08-27
I am also having this same problem but with a GeForce 4 card; I have integrated Intel 810 graphics and a PCI-nvidia card, which works during setup but at the point where the system boots the actual welcome screen my screen blanks.

A quick look in xorg.conf shows the system has configured the integrated graphics but there is no sign of it even looking at my PCI card.

Is there anyway I can get Ubuntu to see my nvidia card instead of the integrated one? My bios does not allow me to 'disable' the integrated chip, it simply allows me to switch between the PCI\Integrated chips.

---

### Post by tseliot on 2005-08-27
[QUOTE=nquinnathome1]I am also having this same problem but with a GeForce 4 card; I have integrated Intel 810 graphics and a PCI-nvidia card, which works during setup but at the point where the system boots the actual welcome screen my screen blanks.

A quick look in xorg.conf shows the system has configured the integrated graphics but there is no sign of it even looking at my PCI card.

Is there anyway I can get Ubuntu to see my nvidia card instead of the integrated one? My bios does not allow me to 'disable' the integrated chip, it simply allows me to switch between the PCI\Integrated chips.[/QUOTE]
Try to switch to the PCI graphic card (even if your card is not PCI) and see if it works (the important thing is that your integrated chip is NOT selected).

I had a problem if my PCI (ati integrated chip) (which was selected by default, thanks Compaq :mad: ) was set by the bios. Ubuntu kept on using (in xorg.conf) my other graphic card (Geforce 6200 PCI-E) despite the bios settings. So the system froze randomly. I had to switch to PCI-E in my bios settings. No lock-ups any more.

I hope it helps.

---

### Post by nquinnathome1 on 2005-08-27
I have already switched it over; i've done it again just to make sure, in the bios it definitely displays the Geforce as being selected, and I know this is true as my monitor is plugged into the Geforce. My bios only uses the display that is selected; attempting to use the integrated chip at this time means no screen at all; I can install Ubuntu, I just can't get it to actually boot to the GUI login screen.

I'll have a look at the other bios settings but apart from that I can't see a problem; the machine readily accepts my Geforce when I try installing any Windows OS on it without any such problem.

---

### Post by vh1 on 2005-09-07
I have tried another video card, and using the "pci=routeirq" boot option, and neither have worked.

both cards work in windows, and are set as the primary card in the bios (monitor is plugged into pci card)

but, still nothing

nquinnathome1, you can try what I will try later. boot your system using a live-cd, or just something so you can mount your linux partition (debian boot floppy, for example). mount said partition and edit your /etc/X11/xorg.conf file. maybe it will work

---

### Post by vh1 on 2005-09-08
[QUOTE=vh1]nquinnathome1, you can try what I will try later. boot your system using a live-cd, or just something so you can mount your linux partition (debian boot floppy, for example). mount said partition and edit your /etc/X11/xorg.conf file. maybe it will work[/QUOTE]
confirmed. it works fine now!
and maybe now I can finally get a dual-monitor setup working in linux

---

