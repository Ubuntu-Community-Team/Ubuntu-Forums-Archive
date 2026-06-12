---
title: "Sound card problem (OPL3SA)"
date: 2005-03-03
forum: Hardware &amp; Laptops
---

### Post by Mister_X on 2005-03-03
Hello all,
I can't make my soundcard working on my Toshiba Tecra 8000.
It's a Yamaha OPL3SA.
I tried lots of thing and searched a lot but nothing works
I tried [http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html) but it didn't work.
I tried alsaconf but my card isn't found.
I always get "Device not found or busy"

Does someone have a solution?

edit: 
I found the problem. There was in '/etc/modules' a '-' instead of a '_'. Silly thing.
I'm preparing a guide for people who have problems installing this sound card

---

### Post by buellman on 2005-03-09
hi!

i wrote the "guide" at [http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html) and i wonder why it didn't worked for you? do you use warty or hoary?
i ask because i upgraded my working warty-install to hoary and now my card doesnt't work anymore... funny thing...

greets. buellman

---

### Post by scotty on 2005-04-15
I used the above posted guide from the mailing list archive and it worked like a champ.  I modified modules, and modules.conf (even though it said not to in the file), rebooted, and the Ubuntu drums greeted me at startup.  A quic apt-get xmms and I am in fat city.

Thanks,
Scott Strungis

Toshiba Satellite 4005CDS P2, 96 Megs of RAM, less than 2 GB for /
ION2, XFce, KDE, Fluxbox, xmms, firefox, dillo, gftp, Pan, gedit
What else do you need?
The minimal install rocks!

---

### Post by marxamuel on 2005-05-02
I saw the fix listed on the page
[http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html)
I could not find the file mentioned /etc/modules.conf in my Hoary Installation

Where do I need to go and what do I need to do?  Please break it down becuase I am new to Linux an the command line interface. Thank you.

---

### Post by buellman on 2005-05-02
[QUOTE=marxamuel]I saw the fix listed on the page
[http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html)
I could not find the file mentioned /etc/modules.conf in my Hoary Installation

Where do I need to go and what do I need to do?  Please break it down becuase I am new to Linux an the command line interface. Thank you.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=26990&highlight=tecra+8000](http://ubuntuforums.org/showthread.php?t=26990&highlight=tecra+8000)

thats the way i did it on hoary. there is sound now (alsa), but apps like skype dont work... dont know why, but at least i can listen to my music :-)

hth. buellman

ps: with hoay there is no file like modules.conf. you have to look at /etc/modprobe.d
just follow the instructions in the link above.

---

### Post by marxamuel on 2005-05-03
I went through the procedures laid out in the link [http://ubuntuforums.org/showthread....ight=tecra+8000](http://ubuntuforums.org/showthread....ight=tecra+8000) (editing the files that you listed with the entries that you gave me and now I have an icon with a speaker and I don't get an error message when I start up my sound services. I went into my bios and found that IRQ5 is devoted to the sound. Still no sound. 

In the interest of clarity I will summarize.  
1. I installed esounds/clients

2. edited the etc/modutil/alsa-base with the alias lines 
alias char-major-14 snd-pcm-oss
alias sound-slot-0 snd-card-0
(remming out the old lines)

2. edited the etc/modprobed./alsa-base with 
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530 && /lib/alsa/modprobe-post-install snd-opl3sa2
(remming out the old lines)

3. edited the etc/modules with the lines
snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530
(remming out the old lines)

4.checked the bios and verified that IRQ5 is assigned to the sound. 

Still no sound - any more suggestions greatly appreciated.  Thank you.  _Please break it down a little because I am definately a newbie. _

---

