---
title: "cirrus logic sound card not found"
date: 2005-02-21
forum: Hardware &amp; Laptops
---

### Post by kelean on 2005-02-21
I have just installed 4.10 warty and updated with apt-get.  My sound card did not get detected during the install.  I have a cirrus logic cs4232 sound card.  I did lspci, here is the output:
kevin@Kelean:~ $ sudo lspci
Password:
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0e.0 Communication controller: Conexant HCF 56k Data/Fax/Voice Modem (Wo rldwide) (rev 08)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (r ev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/ 2X (rev 5c)

I also did  modinfo soundcore with the output:

kevin@Kelean:~ $ sudo modinfo soundcore
Password:
filename:       /lib/modules/2.6.8.1-3-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.8.1-3-386 preempt 386 gcc-3.3

So where do I go from here.  I am not new to linux, I have used slack 10, yoper 2.1,    and a few live CD's.  With those all I needed to do was run alsaconf and i was good to go. I tried to run it here and all I get is command not found.

This is getting frustrating.  Is this a kernel, alsa, unbuntu, or system proublem.  I have not had any problems before with linux.  Please any help will be greatly aprieated

---

### Post by kelean on 2005-02-23
[QUOTE=kelean]I have just installed 4.10 warty and updated with apt-get.  My sound card did not get detected during the install.  I have a cirrus logic cs4232 sound card.  I did lspci, here is the output:
kevin@Kelean:~ $ sudo lspci
Password:
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0e.0 Communication controller: Conexant HCF 56k Data/Fax/Voice Modem (Wo rldwide) (rev 08)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (r ev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/ 2X (rev 5c)

I also did  modinfo soundcore with the output:

kevin@Kelean:~ $ sudo modinfo soundcore
Password:
filename:       /lib/modules/2.6.8.1-3-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.8.1-3-386 preempt 386 gcc-3.3

So where do I go from here.  I am not new to linux, I have used slack 10, yoper 2.1,    and a few live CD's.  With those all I needed to do was run alsaconf and i was good to go. I tried to run it here and all I get is command not found.

This is getting frustrating.  Is this a kernel, alsa, unbuntu, or system proublem.  I have not had any problems before with linux.  Please any help will be greatly aprieated[/QUOTE]
 I just upgraded to Hoary without a hitch.  The only problem is no sound except the beep. I do like ubuntu the best of the debian distros.  I will do a bit more investgating and if no luck I guess I will go back to Slackware or Yoper.  At least there I can get some kind of an answer or a point in the right direction.  I would would very much like to resolve this problem.  There are lots of sound problems in the forums but nothing has helped me to get my sound card detected.

I really do not want to start anything with this post but I am so damed frustrated!!!!!!!!!!!!!

---

### Post by kelean on 2005-02-26
[QUOTE=kelean]I just upgraded to Hoary without a hitch.  The only problem is no sound except the beep. I do like ubuntu the best of the debian distros.  I will do a bit more investgating and if no luck I guess I will go back to Slackware or Yoper.  At least there I can get some kind of an answer or a point in the right direction.  I would would very much like to resolve this problem.  There are lots of sound problems in the forums but nothing has helped me to get my sound card detected.

I really do not want to start anything with this post but I am so damed frustrated!!!!!!!!!!!!![/QUOTE]
 Come on now this is just SAD.  I can't be the only person with this problem.  All I need is a little help with the sound card.  

HELP PLEASE!!!!!!!!!!!!!!!!!!

---

### Post by kelean on 2005-02-27
It is a sad sate of affairs that I am the only person to reply to this post.  Having heard good things about ubuntu's great support base.  All I can say im back to Yoper with sound!!!!!!!!!!!!!!!!!!!!!!

---

### Post by kelean on 2005-03-01
[QUOTE=kelean]It is a sad sate of affairs that I am the only person to reply to this post.  Having heard good things about ubuntu's great support base.  All I can say im back to Yoper with sound!!!!!!!!!!!!!!!!!!!!!![/QUOTE]
 HMMMMMMM...........STILL NOTHING.

---

### Post by kelean on 2005-03-08
[QUOTE=kelean]HMMMMMMM...........STILL NOTHING.[/QUOTE]
 Im back again.  I have not found any help yet!!!  I tried dmesg | grep isa pnp and got CS4236B for a sound card which i knew.  I still cant the modules to load and cant use any alsa componets.  Please help as this is not fun any more.

---

### Post by kelean on 2005-03-13
I cant beleive that not one person other than myself has replyed to this.  No help what so ever This is sad after all of the good things i have read about this forum.

---

### Post by tommie-lie on 2005-03-14
What exactly are your symptoms?
I also have a Cirrus Logic sound card and it worked fine after I added the snd-cs46xx module to /etc/modules. Before doing that, the mixer was complaining about the missing sound device and my sound card did not get an IRQ assigned to.

---

### Post by kelean on 2005-03-19
[QUOTE=tommie-lie]What exactly are your symptoms?
I also have a Cirrus Logic sound card and it worked fine after I added the snd-cs46xx module to /etc/modules. Before doing that, the mixer was complaining about the missing sound device and my sound card did not get an IRQ assigned to.[/QUOTE]
 How did you add the module?  I get the same thing no sound device.

---

### Post by kadissie on 2005-03-27
I'm having the same problem as you, kelean, as described [HTML="http://ubuntuforums.org/showthread.php?p=107504#post107504"]here[/HTML].

As I said, I managed to get it working once under Hoary. That is the most frustrating thing of all! I don't think that tommie-lee's suggestions works - indeed, I think you'll find from a "lsmod | grep snd" that the module he suggests is already loaded.

I think it's almost time for a bugzilla entry.  Related bugs I found are <a href="https://bugzilla.ubuntu.com/show_bug.cgi?id=4787">4787</a> and, well, that's it.  There are plenty of hits on google for this sort of thing (thinkpad 600e cs4232 or something like that) but they just don't work with Ubuntu Hoary.

Robert.


How does markup work in this $%##*ing forum?

---

### Post by kelean on 2005-04-27
I have fixed the problem I now have sound.  

Adding the following line to /etc/modules

      snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

I added it the end of the file saved rebooted and sound works not without doing anything else.  Go figure I found it by chance in another post.

---

