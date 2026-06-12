---
title: "Dell Latitude D531 issues"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by xtlosx on 2007-06-07
Hey guys, work just got me a nice new Latitude D531, and I wanted to get Ubuntu on it.. i can't stand windows :)

When I use the regular Feisty install cd, it freaks out after the ubuntu logo and it tells me X cannot start...

The video card is a ATI RADEON X1270 Integrated Graphics card.  I was thinking about using the alternate install cd, then trying my luck with the binary drivers from ATI, is this the route to go?

When I run my dmesg, it tells me, my video device is unknown... What is going on??


Thanks in advance everyone!

---

### Post by remuskoos on 2007-06-09
I'm in the same boat :-).

I just installed FC6 on my D531. To get the display drivers working was a pain. Download the proprietary driver from the ATI website and build it for your distro (type 'ati-<driver_version>.bin --listpkg' or something like that to see the available distros). Then generate the drivers for your distro and install them.

  Their config utility crashes on FC6. In your xorg.conf in the Driver section replace 'vesa' or 'radeon' with 'fglrx', set your desired resolution then restart x. You should also load the 'fglrx' kernel module. I guess that one gives you some more acceleration.

  Good luck,

    remus

---

### Post by hotani on 2007-06-22
I'm sitting here looking at a D531. X bombed out, and I'm stuck at the command line. Every 10 seconds an error comes up in the middle of what I'm doing stating: 

```
Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
```

So my recommendation is to SKIP this laptop. And SKIP anything with ATI in it. But we all knew that, right?

EDIT: This is what I did to get the window manager to load:

1- install fglrx:
```

sudo aptitude install fglrx-driver

```

2- open xorg.conf and change "vesa" to "fglrx"

3- reboot.

This will not run compositing, and when I tried it my screen turned to mush. ATI cards are bad, bad, bad, baaaaad. Avoid at all costs. This was a work laptop for me so I had no say in the matter.

---

### Post by hotani on 2007-06-24
I'm Xposting from [another thread](http://ubuntuforums.org/showthread.php?t=381019) regarding a separate sound issue with the same device. This is the built-in ATI *shudder* audio device which is reported as an "SB600 Azalia". The problem on my D531 is that there is no sound at all.

This is what alsamixer reports:

```

shell> alsamixer 

alsamixer: function snd_ctl_open failed for default: No such device

```

And from "lspci -v":
```

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: Dell Unknown device 0206
        Flags: slow devsel, IRQ 17
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by RedSalmon on 2007-09-14
Folks,
I am having the very same problems with my D531 with the exception that I installed through WUBI which went great (Vista was unphased  by WUBI).  However I am getting the bcm43XX microcode error and the x server error.

I have prowled all over the ATI site and cannot find any reference to the X1270 or a linux driver for it.  Can someone include a link for the driver?

 Also I need to know how to get to the command line since I can't seem to find nor edit xorg.conf through Windows. A pointer to a good primer on the forums is fine - I don't expect such basic info here for a newbie like moi.

---

### Post by gimbow on 2007-11-01
Same boat here.  Dell D531 with ubuntu 7.1x.  I was able to install without too many problems but I am stuck on 800x600 screen resolution and no sound.  I looked all over the place for Radeon Xpress 1270 drivers and have had no luck yet.  Any help would be awesome.

---

### Post by filcap on 2007-11-04
Hi Hotani!
I've the same laptop and the same problem.
Did anybody get the sound working with Ubuntu 7.10 (it was working perfectly with 7.04) on a Dell Latitude D531???

---

### Post by konungursvia on 2007-11-05
Try installing this and then reboot:

sudo apt-get install linux-backports-modules-generic

For me it got sound going, on the very same macchine

---

### Post by filcap on 2007-11-06
Hi konungursvia!
It didn't work for me....
Apparently the linux-backports-modules-generic was already at the latest version; anyway I tried to remove and reinstall it, but nothing changed...
Have you got the ATI Azalia sound card?
Did you perform any other change in order to get it working? (Maybe something in the alsa-base file?)
Thanks once again!

---

### Post by konungursvia on 2007-11-09
I do have that sound card; after installing the backports, it worked for me. Note I may also have had to go to alsamixer and unmute the pc speakers, master volume, etc. Also, I'm running 64 bit, you may not be, maybe the default packages are different. Make sure you're a member of the audio group too. :)

---

### Post by filcap on 2007-11-09
Hi konungursvia!
Thankyou very much for your "assistance"!
I'm running the 64 bit version of Gutsy Gibbon.
Alsamixer does not work for me.
Just look at this:
[I]filcap@fc-laptop:~$ sudo apt-get install linux-backports-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
filcap@fc-laptop:~$ alsamixer


********************   WARNING   *******************************
Warning! alsamixer uses ALSA emulation instead of the native OSS API
****************************************************************

snd_mixer_set_callback()
No mixer elems found
[/I]

Any idea??

---

### Post by Karlgw on 2007-11-11
sudo apt-get install linux-backports-modules-generic
then re-boot. After that the sound on my Latitude D531 was working fine (found on this thread: [http://ubuntuforums.org/showthread.php?p=3713294](http://ubuntuforums.org/showthread.php?p=3713294))

---

### Post by filcap on 2007-11-12
Hello konungursvia and karlgw!
Since the sound is working on your machines, maybe there is something I've compromised in my configuration while trying to fix the problem....
When you launch alsamixer, do you have that warning message?
*"alsamixer uses ALSA emulation instead of the native OSS API"*
Is this correct? Maybe this is a really basic question, but I know nothing about ALSA...
Can you post your alsa-base configuration file?
Thankyou very much indeed!

---

### Post by Sam Plamondon on 2007-11-18
> **konungursvia said:**
> Try installing this and then reboot:

sudo apt-get install linux-backports-modules-generic

For me it got sound going, on the very same macchine

Hey, thanks!  I have a Dell Inspiron 1521 with the same Azalia sound card as the Latitude D531, and this worked perfectly.

---

### Post by konungursvia on 2008-03-13
Glad I could be of help! But I  wonder how the "thanks" things work, I am still listed as being a thankless monster. :(

---

### Post by hotani on 2008-04-02
As mentioned in [this thread](http://ubuntuforums.org/showthread.php?t=577586), the 8.04 Beta LiveCD looks very promising. Video and sound work on the 531 - but no wireless yet.

---

