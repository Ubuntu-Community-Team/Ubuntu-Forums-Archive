---
title: "NVIDIA GeForce GTX 560M on Ubunty 11.10 (Alienware M17xR3)"
date: 2012-03-08
forum: Hardware
---

### Post by whitmcrae on 2012-03-08
Hello all.  Recently I purchased an Alienware M17xR3 which I have set up as a dual boot between Windows 7 and Ubuntu 11.10.  Both boot up (GRUB2) and run fine in a generic sense, however I have been unable to get the NVIDIA card working in Ubuntu 11.10 to allow things such as Compiz effects and increased screen resolution.

_I am running in a BIOS RAID0 configuration (fakeRAID) with the following hardware:_
[FONT=&quot][IMG]https://mail.google.com/mail/u/0/?ui=2&ik=b567296f31&view=att&th=135e433e115a9997&attid=0.1&disp=emb&zw[/IMG][/FONT]
[I][FONT=&quot]Intel® Core™ i7 2860QM (2.5GHz,3.6GHz with Turbo Boost, 8MB Cache)[/FONT]
[FONT=&quot]16GB Dual Channel DDR3 at 1600MHz (4DIMMS)[/FONT]
[FONT=&quot]**1.5GB GDDR5 NVIDIA GeForce GTX 560M**
[/FONT][FONT=&quot]1TB Raid 0 (2x 500GB Hybrid Solid State Drives)[/FONT][/I]

I've read just about everything Google and Bing could find on the topic and spent hours doing so, and although I've learned quite a bit in the process every attempt has done nothing but break my GUI boot in one way or another.

If any of you have gotten an NVIDIA driver working with the GTX 560M I would greatly appreciate any knowledge you could impart as to how you did it.  As it is a fresh install I'm willing to try anything and have no problem fixing whatever breaks along the way.

Any other help from you Ubuntu gurus out there would also be appreciated, as I would really like to get this setup working such that I can have Compiz functional and eventually run my Windows 7 installation within Ubuntu though VirtualBox (for development purposes)!

Thanks in advance!

---

### Post by The Bright Side on 2012-03-26
Hey whitmcrae, I wish I could help, but all I really have is an additional question: I see that you posted about this problem about 2 weeks ago. I am considering getting a laptop with the same graphics card (well, the 3GB version), but it's an "optimus" card and reading about the troubles people have had with it makes me apprehensive.

Did you manage to fix your issues in the meantime? How are you getting on? How does the card behave by default? As I understand, it does display the Ubuntu desktop, but won't allow any effects or higher/correct resolutions?

---

### Post by whitmcrae on 2012-03-28
Hello Bright Side, I did not manage to fix the issue because I really did not want to spend any more time debugging it without a good lead, and figured with official Ubuntu 12.04 on the horizon I would wait for that before doing any more.  Hopefully it will have better compatibility with what will then be a little older (and more common) hardware.

To answer your second question, Ubuntu is perfectly usable and loads the Unity desktop fine.  As you correctly stated what it does not do are the support higher resolution and fancy GPU transitions that the graphics card is clearly capable of.  It also runs quite well in Windows 7 (with the provided Windows driver - which is NOT build into the Windows install library).

Hope this helps,
Whitaker

---

### Post by The Bright Side on 2012-03-29
Thanks so much for your response! I plan to get an ASUS PC with the same kind of card some time this year, and when I do, I'll be sure to remember this thread and share what I find.

Have you experimented with Bumblebee?
[http://bumblebee-project.org/](http://bumblebee-project.org/)

It still sounds a tad cumbersome, but quite manageable and from what I understand, it will allow you to use Ubuntu properly.

---

### Post by limestrael on 2012-03-30
Hi, I guess my experience would help you:
I too just bought a M17x R3 with the same hardware than you except for the processor, I have a i7-2670 QM.
So I too have to cope with Nvidia Optimus.
Because of the hardware changes that come with Optimus, you can't use nvidia drivers alone (either from the nvidia-current package or from nvidia's website), they (still) don't handle Optimus on Linux.

I installed Ubuntu 11.10 64 bits.

I installed as The Bright Side suggested bumblebee from its PPA [1] (together with nvidia-current package), it solved some problems: screen resolution is fine, and I have 3d acceleration, however even when I lauch a program through 'optirun' (that switches to the 560M but only for one program, as it is the principle of Optimus) I have poor performances.
But that's maybe just something which has to do with Bumblebee configuration (I think about VirtualGL, that's something used apparently internally by Bumblebee and that limits the framerate even when using the graphics card to save battery life).

[1] See [http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html)

I also have some sound issues: the speakers won't work, however the earphones outlet does. It's not as bad as graphics not working, but if you happend to find a solution I'd be interested in knowing it.

*EDIT:* I just found a post of a guy that deactivated the Intel chipset through BIOS flashing: [http://forum.notebookreview.com/alienware-m17x/585515-howto-disable-optimus-m17xr3.html](http://forum.notebookreview.com/alienware-m17x/585515-howto-disable-optimus-m17xr3.html). Maybe dangerous...

---

### Post by The Bright Side on 2012-03-30
Thanks for taking the time and chipping in, limestrael!

I wonder how we can determine whcih programs will make use of the Nvidia card to begin with. Games are the obvious candidates, but do you happen to know if e.g. Darktable (photo editing software for RAW files) or Gimp heavily employ the graphics card, or whether they use the CPU solely for their operations?

Please do keep us posted about your experiences.

EDIT: I got the impression from some of the installation instructions I found online for bumblebee that it pulls the Nvidia driver automatically while installing. Is that right, or is the user instead required to just install both at the same time?

---

### Post by The Bright Side on 2012-03-30
For the speakers - I assume you went through the "Hardware" tab in the Sound Settings? It may be as easy as finding the correct profile in the dropdown menu at the bottom.

---

### Post by The Bright Side on 2012-03-30
I also found this:
[http://www.computerandyou.net/2011/06/how-to-solve-no-sound-through-laptop-integrated-speakers-in-ubuntu-11-04/](http://www.computerandyou.net/2011/06/how-to-solve-no-sound-through-laptop-integrated-speakers-in-ubuntu-11-04/)

And this bug, including a fix in the original bug description:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)

Hope this helps!

---

### Post by limestrael on 2012-03-30
It worked!
options snd-hda-intel model=alienware
added at the end of the file/etc/modprobe.d/alsa-base.conf

and the speakers work ^^

---

### Post by limestrael on 2012-03-30
It worked!
options snd-hda-intel model=alienware
added at the end of the file /etc/modprobe.d/alsa-base.conf

and the speakers work ^^. However I've got only one earphones outlet that works (M17x R3 have two), that might require some more tweaking.
This will certainly be useful for you, whitmcrae.

---

### Post by The Bright Side on 2012-03-31
Cool! Glad to know it worked.

---

### Post by limestrael on 2012-04-03
@whitmcrae: I still have my graphics issues: acceleration works thanks to Bumblebee, but I have (with the game Trine for instance) really worse performances (settings maxed) than with Windows.

Plus (and I'd like to know if you have the same issue), 720p videos decoding with VLC and mplayer *when on battery* is laggy. I expected a CPU downclock issue due to power saving, but "cat /proc/cpuinfo" showed me my cores could reach the 2.2GHz... Does it work fine for you?

---

### Post by The Bright Side on 2012-04-06
Hey guys,

I found this really useful post on the Ubuntu magazine webupd8 today. It's about running Bumblebee correctly on the upcoming Ubuntu 12.04, and at the end, it contains a way to test whether Bumblebee works as intended.

[http://www.webupd8.org/2012/04/bumblebee-ubuntu-1204-workaround-cannot.html](http://www.webupd8.org/2012/04/bumblebee-ubuntu-1204-workaround-cannot.html)

Limestrael, this may help you with your attempts to get framerates up to realistic levels.

---

### Post by Yellow Pasque on 2012-04-06
> **limestrael said:**
> However I've got only one earphones outlet that works (M17x R3 have two)

This might help: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

### Post by whitmcrae on 2012-04-12
Hey guys, sorry I have been very busy and had not checked this in a while to see all the replies!  I did manage to install Bumblebee, and verify it is working (to some extent) by running glxspheres

optirun glxspears
~70 frames/sec - ~90 Mpixels/sec

glxspears
~5 frames/sec - ~8 Mpixels/sec

I do note that even with optirum the framerate seems rather slow.  I would expect more like 120 frames/sec!

Even with Bumblebee technically installed I still do not have any GUI related GFX functions.  My display settings still only allows the same resolution as before, and compiz still does not show wobbly windows even when it is selected.  Do either of you know what I need to do here to get these 2 things working with Bumblebee?  Sorry I'm not an expert at this, so thank you for experimenting with me so we can discover all of this together!

**EDIT**
Also, when I try to run compiz with optirun (sudo optirun compiz) it gives me the following error:
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager"
Well, when I do try using --replace the screen looks kind of funky (but still visible) and I have to reboot from terminal.  I'm not really sure if optirun compiz would even give the desired effects I'm just looking for some GFX acceleration in the basic Unity GUI if possible!

Whitaker

---

### Post by whitmcrae on 2012-05-09
An update for anyone interested or looking to solve the same problem.  Rather than use Bumblebee for particular applications I have opted to flash a modded BIOS (A10, the current rev) with all of the options unlocked.  After doing this I turned off the Optimus portion of the graphics, now available in the BIOS, and then the NVIDIA-current driver worked great in Ubuntu.  

Windows can be run alongside (installing NVIDIA driver for optimum resolution), however when doing this I did personally encounter BSOD at times.  Instead I have it running as a virtual machine within Ubuntu using VirtualBox, and everything works great.

Below is the link to the modded BIOS for any of you wanting to do this.  It is installed the same way an official BIOS from Dell is installed, by simply running the executable.
[http://forum.techinferno.com/alienware-m17x/1641-%5Btested-working%5D-m17x-r3-*unlocked*-bios-a10-3.html#post21127](http://forum.techinferno.com/alienware-m17x/1641-%5Btested-working%5D-m17x-r3-*unlocked*-bios-a10-3.html#post21127)

Enjoy, and good luck all with M17x-R3 trying to gracefully run Ubuntu 12.04 with all bells and whistles!

---

