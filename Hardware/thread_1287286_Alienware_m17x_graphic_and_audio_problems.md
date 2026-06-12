---
title: "Alienware m17x graphic and audio problems"
date: 2009-10-10
forum: Hardware
---

### Post by niite on 2009-10-10
Hello There - my first post here.

I'm having problems with Ubuntu 9.04 (64 bit) on my Alienware m17x laptop.  I've been an opensuse user the last few years, and this is my first try with Ubuntu, and I'm pleasantly happy so far with the os.  I am having a few hardware issues though.  Specifically my graphics and audio.  

Graphics..   I've got dual NVIDIA GeForce GTX 260M cards.  Can't get them to work -- right now the generic vga driver is working for me, but that is not ideal at all.  The driver option I get when i launch the Hardware Driver app to install proprietary driver aren't the correct ones, it shows NVIDIA accelerated grphics driver (180)..  when I go to the NVIDIA site it shows the driver support for (180) is the GTX 260, not the GTX 260m (which is version 190).  I have download the 190.32 driver package from nvidia, and installed it to no avail.  When I install the driver and restart I get a black screen.  Not sure if this sli related?  no idea.  I've searched the internet for advice, and came accross a few post (one here) on the problem, but no real solution - lol I even translated an italian forum post with google translater, and the advice was the same.  One thing the post mentioned, was to disable hybrid graphics, which I have done - but that does not work for me.

Audio..  I get no audio..  my audio is IDT 92HD73C1.  I tried upgrading my ALSA to the latest version (21) and no joy.  When I go to my volume, the idt it shows for OSS is 92DH73C1X5, but the IDT it shows for alsa is HDA Nvidia -  so I'm at a loss on how to proceed.  I need my sound.

So those are the pressing questions I have right now, any help would be mucho appreciated.

-john

---

### Post by niite on 2009-10-10
I found a workaround for the sound problem..  it's not perfect, but i'm getting sound.

add this line to alsa-base.conf in /etc/modprobe.d/

options snd-hda-intel model=dell-eq

I don't think I'm getting the 5.1 surround now, the front, back, etc speakers aren't showing up in the mixer...  but i'm getting stereo out of the headphone/output jack.

---

### Post by niite on 2009-10-11
Bumping this... still have issue with graphics card.  any help advice would be appreciated.

---

### Post by brentrubeck on 2009-10-12
The workaround I found for the graphic card issue is to disable the integrated card in the bios.  Not ideal, but that got me working.  Also I had to download the Nvidia driver and to install the Nvidia driver I had to boot up to the rescue screen from the grub boot up menu and kick myself into the root prompt (without networking).  All of that got me up and running.  However I have only 1 Nvidia card, so you might have to do something else.

As an aside I don't know if this helps, but when you get the blank screen, it appears that the laptop is up and running fine.  It just doesn't have a monitor.  If you hit ctrl-alt-F2 or any of the other F buttons I think it kicks you into a text only shell (you just can't see it).  I was able to hit ctrl-alt-del from there to get the laptop to reboot without having to hold down the power button.

---

### Post by niite on 2009-10-13
Yeah, I disabled the integrated card in bios but no luck - I'm just going to wait for the 9.10 release of ubuntu and do a clean install of that with integrated card disabled in bios from the get go -  See if that fixes it.  Hopefully I can get surround sound working then as well.

Which Nividia driver did you install?  

And many thanks for your response!

-j

---

### Post by brentrubeck on 2009-10-13
I used the NVIDIA-Linux-x86-185.18.36-pkg1.run (which is also the 32-bit version).  I noticed you were using 64-bit and that might also be causing some issues.

---

### Post by Tim_H on 2009-11-04
> **brentrubeck said:**
> The workaround I found for the graphic card issue is to disable the integrated card in the bios.  Not ideal, but that got me working.

This worked for me as well on Karmic Koala.  My Alienware m17x has a 64-bit CPU.

I installed the latest NVIDIA driver (v190.42) from the *.run file provided by NVIDIA.  However, the driver still would not work until I disabled the integrated card in the BIOS.

---

### Post by Carnagio on 2011-09-30
> **niite said:**
> I found a workaround for the sound problem..  it's not perfect, but i'm getting sound.

add this line to alsa-base.conf in /etc/modprobe.d/

options snd-hda-intel model=dell-eq

I don't think I'm getting the 5.1 surround now, the front, back, etc speakers aren't showing up in the mixer...  but i'm getting stereo out of the headphone/output jack.

This got my sound working on my Alienware m18x -- Thanks niite! Though it is sort of odd sounding. Maybe not all the speakers are working or something? I'm running Ubuntu 11.04 -- any ideas on why the above fix worked or what can be done to improve it?

---

### Post by mi_di on 2012-11-20
> **niite said:**
> I found a workaround for the sound problem..  it's not perfect, but i'm getting sound.

add this line to alsa-base.conf in /etc/modprobe.d/

options snd-hda-intel model=dell-eq

I don't think I'm getting the 5.1 surround now, the front, back, etc speakers aren't showing up in the mixer...  but i'm getting stereo out of the headphone/output jack.

This also worked for me.

---

