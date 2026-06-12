---
title: "Karmic no longer recognises soundcard"
date: 2011-06-19
forum: Hardware
---

### Post by Schaeufele on 2011-06-19
Hi,

I'm running Xubuntu 9.10 on a Toshiba Satellite 3000-514. Suddenly the soundcard is no longer recognised by Xubuntu. I have removed/purged and then reinstalled Alsa and Pulseaudio. Still I only get the Dummy output in Mixer and Pulse Audio Volume Control.

Some info below.  

Kernel: 2.6.31-23-generic #75-Ubuntu SMP Fri Mar 18 18:08:39 UTC 2011 i686 GNU/Linux

lshw -c sound yields:

*-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801CA/CAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
       resources: ioport:1c00(size=256) ioport:18c0(size=64)

File /proc/asound/cards does not exist.

Can anyone help, please.

Edit: I am also running Lubuntu 11.04, there the sound works.

---

### Post by dino99 on 2011-06-19
Lucid is a LTS so why still using Karmic ?

---

### Post by Schaeufele on 2011-06-21
Hi,
 
I am not sure if upgrading to Lucid will fix this problem, especially on my machine. Xubuntu becomes heavier and heavier with every upgrade and problems have been reported with Nvidia graphics cards; I have a GeForce 2Go. I am trying Lubuntu Maverick at the moment, it is much lighter than Xubuntu, but I and am having loads of trouble with my graphics card. Working on it.
 
Therefore, I'd like to get my fine Karmic system back to running perfectly as it was before it suddenly forgot about its soundcard.
 
I have actually searched for quite some time in various sources, but could not find anything that even gave me a hint as to how to make my system recognise the soundcard again.
 
Therefore, any hint how to fix this sound issue given the circumstances would be much appreciated. I will put in the effort, but I don't even know how to start on this one.

---

### Post by mastablasta on 2011-06-21
you could try to upgrade ALSA.
 
Or yeah simply go Lucid or maybe latest Crunchbang (based on debian stable). it is quite friendly to older systems. i too have issues on old notebook with latest *buntus thoguh previous ones worked just fine.

---

### Post by Schaeufele on 2011-06-25
Have tried upgrading ALSA, all very nice but the multimedia adapter was still UNCLAIMED and therefore no sound. This was with kernel  2.6.31-23. After some more research I found that the driver for my soundcard is missing, as revealed by MODINFO SOUNDCORE.

So I tried the previous kernel, 2.6.31-22, and the sound works! 

I am therefore marking this thread as SOLVED. Will try to get the sound driver to work with the -23 kernel now.

---

### Post by Schaeufele on 2011-06-25
For completeness:

To get the driver modules compiled and working with the -23 kernel, I have done the following:

1.) Find the hardware: lshw -class multimedia
2.) Find the most recent ALSA driver: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
3.) Follow instructions on ALSA-Website: compile drivers, utils etc. and modprobe to kernel

Job done, no upgrade needed, system fixed!  \\:D/

---

### Post by mörgæs on 2011-06-25
It is good that you got the system working, but are you aware that 9.10 is out of support, so you will not receive security bug fixes?

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by Schaeufele on 2011-06-28
Yes, I know that 9.10 is no longer supported. But Xubuntu is a lot safer than any Windows, is it not? 
The system works perfectly on my hardware so I do not have any intention to upgrade Xubuntu on this particular laptop.

---

### Post by mörgæs on 2011-06-28
I would not be satisfied with knowing that my system is safer than something else. I am aiming for the best possible (within sensible limits).

Since Lubuntu 11.04 works on your hardware I would recommend this one. Your decision...

---

### Post by kumoshk on 2012-02-22
This is just a post in defense of Karmic over future versions.

It supports backported wireless cards better than every version that follows (at least my wireless cards), among other things, and there are a few nitpicky things I like better about it that I don't remember since it's been so long since I did the comparison. I imagine there are loads of other reasons a person might want to continue using it, too. People have their reasons for using old software.

I just switched to 11.10, however. I'm still having trouble getting my microphone and sound working properly—but I'm determined. Worked fine before. Updating just for software and security updates isn't always ideal (at least, if you know how to and have the patience to do stuff without apt-get). I like to wait until either I have lots of time or until the newest upgrade works with my hardware with minimal effort. Maybe this person was holding out there, too.

Other than the microphone and the wireless, though, I like Xubuntu 11.10 (after configuring) a lot more than Karmic with Gnome (not more than the Unity brand, though—it's kind of slow on my computer). Well, Thurnar and Nautilus are buggy on my machine, too—so I use Dolphin instead (yes, in XFCE). It actually has more configuration options (and without having to use dconf-editor) if you look. Too bad it won't integrate with XFCE's desktop (I just disable that, anyway, though). LXDE's file manager is pretty cool, too. I like its defaults.

I do miss the Gmail chat plugin for Karmic. It worked really well (but you can't download it anymore, unless it's on archive.org or something). The new one gives me a bunch of crackly sounds. Maybe that's just Xubuntu 11.10 and my sound card. I don't know.

---

