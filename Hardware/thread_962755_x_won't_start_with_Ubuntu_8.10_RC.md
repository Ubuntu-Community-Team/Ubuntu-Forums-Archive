---
title: "x won't start with Ubuntu 8.10 RC"
date: 2008-10-29
forum: Hardware
---

### Post by ctsdownloads on 2008-10-29
I have an older Averetec 3200 with VIA Unichrome graghics. In the past, I have never had a problem getting X to start up when going to do an install, however this time, it seems like this new dynamic Xorg setup is really creating a problem.

Trying to boot from the standard LiveCD for 8.10, clearly there is a bug with OpenChrome (Unichrome module I believe) as it streams down the error log explaining why every monitor resolution in the world is unconfigurable. Even more frustrating, I fear that when I try the alt-Cd, I will see the same issues there as well. I would love to post the error log, but I am unsure how to do that without...well, actually I guess I could try using the CLI to mount a USB flash drive and cp the log over the drive...argh...

Either way, dpkg-reconfigure xserver-xorg is gone apparently, while the Xorg.conf appears to be dynamic - great.... :mad:

---

### Post by High Roller on 2008-10-30
I'm having similar problems with my Averatec 3700.  I'm sticking with 8.04 for right now because I fear there's no real way around this problem.

My hope is that 9.04 will possibly bring better OpenChrome.  The crappy part is that Ibex worked on my laptop a few weeks ago and then started to fail close to the release date of the RC.  I filed a bug report.

---

### Post by Spitphire on 2008-11-02
I have an Averatec 3715 (same chipset as you).  I've made some progress, here's where I am at.  I'm sure it will help you. I can start x fine now.

After a clean install of 8.10 the system would load normally until it got to starting x.  Once X started up it would show the mouse in the bottom right hand corner and then it would 'freeze'.  Locking the entire system.  The mouse would turn into the little thinking wheel, turn a couple of times then totally freeze.

Before it freezes what you need to do is hit CTRL-ALT F2 to get to a command line. Login and then follow these steps:

```

sudo nano /etc/X11/xorg.conf

```

Replace the entire thing with this:
```


Section "Device"
	Identifier	"Configured Video Device"
        Option          "DisableIRQ"
	Option		"XaaNoImageWriteRect"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
	
	Subsection "Display"
	Depth 16
	Modes "1024x768"
	EndSubsection

EndSection

```

then:
```

sudo shutdown -r now

```

once everything reloads it should get you into xwindows..

I've had a lot of issues with the openchrome driver with 8.10.  As soon as I get it figured I'll post more.  This however should get you up and running.

Here are some specs about my laptop:

```

am@lp:~$ uname -a
Linux lp 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

```

```

am@lp:~$ lspci |grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

```

```

am@lp:~$ cat /proc/cpuinfo |grep -e vendor_id -e "model name"
vendor_id	: AuthenticAMD
model name	: Mobile AMD Sempron(tm) Processor 3000+

```

---

### Post by Spitphire on 2008-11-02
Forgot to mention:

You have to use the Alternative CD (with no gui) to get everything installed.

---

### Post by timpalpant on 2008-11-02
Same exact system, after doing the fix it said that it was running in "low-graphics mode," then went to a black screen indefinitely.

Any other suggestions?...or drivers? I thought I remembered changing the default driver for this system in 8.04...

---

### Post by Spitphire on 2008-11-03
Hmm.. It worked for me (however not very well).  Apparently this is a known problem with the openchrome driver (which works perfectly in 8.04).

I've since reverted back to 8.04 until they fix the problem with 8.10.

More info here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/274340]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/274340")

---

### Post by High Roller on 2008-11-03
> **Spitphire said:**
> I have an Averatec 3715 (same chipset as you).  I've made some progress, here's where I am at.  I'm sure it will help you. I can start x fine now.

That worked great!  I even managed to get it to work on a Live+persistent USB session (this is the main reason I wanted to use Ibex) with the help of "switchconf".  It's unfortunate that it's slow...  but better than nothing!

Thanks!  :)

---

### Post by Spitphire on 2008-11-03
Glad to help.  If you have any other issues with the Averatec let me know.  I'm fairly familiar with all the hardware for it.

---

