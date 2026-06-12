---
title: "BIG video and audio problems ......"
date: 2008-04-30
forum: Hardware
---

### Post by ElEdwards on 2008-04-30
My laptop is a Compaq Presario 2170us and Hardy is the first distro I've had problems with, especially when it comes to my display.  There are lines all over the screen anytime I open a window and getting Compiz to work is an unsuccessful chore.

I posted my **xorg.conf** and the output of **lspci** here:
[http://ubuntuforums.org/showthread.php?t=774266&highlight=xorg]("http://ubuntuforums.org/showthread.php?t=774266&highlight=xorg")

Can anyone help?  I've been a cheer-leader for Ubuntu for almost a year..... but I don't like this "auto config" think at all!!  My laptop has an older ATI card (ATI Mobility Radeon).

I'm having an audio problem, too (ton's of skips and crackles in my recordings) and since I do commercial voice-overs, this is a really bad thing!

....but I want to get my video problems fixed first.

I was really hoping for great things from Hardy....but right now, DreamLinux 3.2 works the best for me.

(...and if your response is along the lines of "Stay with DreamLinux", please save your breath/typing.)

Thanks!
El

---

### Post by Miguel on 2008-04-30
Hi El,

First of all, compiz won't work. Some ati laptop cards were crashing when using the free drivers and it varied even between cards with the same PCI ID, so compiz is blacklisted for all ati cards using the free driver.

Secondly, I need more info on your hardware. What's your screen size? What's its resolution? From what I've googled, it's a 15" 1024x768 screen.

Let's try to modify xorg.conf by hand. We'll also set AGP to 1x, just in case:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
 	Option		"AGPMode"	"1"
EndSection

```

Also, if your monitor is indeed 15" 1024x768 you may try changing your monitor and screen sections to
```

Section "Monitor"
	Identifier	"Configured Monitor"
        DisplaySize	305 228
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

```

Remember to make a backup!!! Also, it is possible that this doesn't work. OK, don't panic. Hardy is using xserver-xorg-video-ati version 6.8.0, the latest stable. However, ATi released quite a few specs after that release, and there are a few bugfixes backported by Bryce Harrington (one of Ubuntu X mantainers) to an experimental deb. I'll put a link to both the current hardy driver and this one, and you should download both. In case the experimental doesn't work, you will easily revert to the default one using dpkg.

[http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.8.0-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.8.0-1_i386.deb)
[http://people.ubuntu.com/~bryce/Testing/ati/xserver-xorg-video-ati_6.8.0-1ubuntu1_i386.deb](http://people.ubuntu.com/~bryce/Testing/ati/xserver-xorg-video-ati_6.8.0-1ubuntu1_i386.deb)

**Beware! 32bit intel only!!!**Does this work? In any case, I fear that I won't be able to help you with your audio issue.

*EDIT* Did you keep a previous home partition? If so, you might want to create a new user and see if that user has the same issues (especially the audio ones).

---

### Post by ElEdwards on 2008-04-30
Thanks, Miguel :)

First, no, there is no previous /home partition.  I did a clean installation over the previous installation, using both **/home** and **/**.

Compiz has worked just fine up until 8.04.... so I guess I'll just have to settle in my head that Hardy isn't for me on my laptop. :(
...and I'm really bummed about that.

El

---

### Post by ElEdwards on 2008-05-01
Miguel,

FYI, I tried the settings in **xorg.conf** that you posted above.... and 8.04 wouldn't even start :(

After Grub and the startup progress bar, things went to black and after 5 minutes with no HDD activity, I gave up.

El

---

### Post by Miguel on 2008-05-02
This is really weird. The worst I would expect was that you got kicked out to tty1 or so. But hanging? No way!. Have you been able to restart your laptop again?

---

### Post by ElEdwards on 2008-05-02
Yes, I restarted in Recovery Mode, which took me to a command prompt and I was able to restore xorg.conf from the backup I had made.

El

---

### Post by Miguel on 2008-05-02
What exactly did you try? I'm interested in knowing what exactly happens when you specifically select AGP 1x. By the way, it would be nice if you posted your exact hardware ;-)

---

### Post by ElEdwards on 2008-05-02
Miguel,

I appreciate your help.... but I've decided to stick with DreamLinux 3.0.... it has given me no issues, in much the same way as Ubuntu 7.04 and/or 7.10 worked fine for me, but DL3.0 is smoother and faster.

Thanks :)
El

---

### Post by Miguel on 2008-05-02
Good luck El!

---

