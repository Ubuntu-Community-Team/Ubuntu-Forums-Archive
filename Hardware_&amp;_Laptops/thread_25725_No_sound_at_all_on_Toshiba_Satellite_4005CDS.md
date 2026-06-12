---
title: "No sound at all on Toshiba Satellite 4005CDS"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by scotty on 2005-04-10
Hi forumers...

I am running a custom warty installation with apt-get additions from the hoary repository.  This is an older machine.  A PIIMMX with 96 megs of RAM and a 1.5 gig partition set aside for Ubuntu.  I have Win98 installed on the other partition for when I need a Windows machine around the house.

I am posting this from within an xorg environment running fluxbox and dillo.  It FLIES.  Anyway...xfce4 and KDE are also installed and I still have almost 700 megs free.

Now, sound works great under Win98 and the System contol panel reports that I have an OPLSA-3 based yamaha card.  I have gotten this Toshiba to work under Redhat years ago with RH's sndconfig util and a little futzing with sample rates and IRQs.

I am told that /dev/dsp does not exist by KDE.  A list of the PCI devices does not reflect any sound card at all from the command line.  And...to top things off lsmod | grep snd produces no output whatsoever.  I simply get another prompt.

I am somewhat stumped.  ALSA is installed at this time.  The machine is quite reliable otherwise with all other peripherals working--wireless, usb, etc.  I would love to get xmms running for music.  I also would like to get wine going to run my grading software.

Anyway, any help that you can offer would be great.  I have been using Ubuntu since the early warty days and I cannot recommend it enough to newbies on both PPC and the x86 side of things.

Thanks!
Scott

---

### Post by lucus on 2005-05-01
[QUOTE=scotty]Hi forumers...

I am running a custom warty installation with apt-get additions from the hoary repository.  This is an older machine.  A PIIMMX with 96 megs of RAM and a 1.5 gig partition set aside for Ubuntu.  I have Win98 installed on the other partition for when I need a Windows machine around the house.

I am posting this from within an xorg environment running fluxbox and dillo.  It FLIES.  Anyway...xfce4 and KDE are also installed and I still have almost 700 megs free.

Now, sound works great under Win98 and the System contol panel reports that I have an OPLSA-3 based yamaha card.  I have gotten this Toshiba to work under Redhat years ago with RH's sndconfig util and a little futzing with sample rates and IRQs.

I am told that /dev/dsp does not exist by KDE.  A list of the PCI devices does not reflect any sound card at all from the command line.  And...to top things off lsmod | grep snd produces no output whatsoever.  I simply get another prompt.

I am somewhat stumped.  ALSA is installed at this time.  The machine is quite reliable otherwise with all other peripherals working--wireless, usb, etc.  I would love to get xmms running for music.  I also would like to get wine going to run my grading software.

Anyway, any help that you can offer would be great.  I have been using Ubuntu since the early warty days and I cannot recommend it enough to newbies on both PPC and the x86 side of things.

Thanks!
Scott[/QUOTE]
 oh man....  i have a relatively similar computer but way old... a toshiba tecra
this is how my sound worked out

modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530

---

