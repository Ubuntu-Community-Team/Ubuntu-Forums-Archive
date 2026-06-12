---
title: "Numerous Problems"
date: 2008-08-15
forum: General Help
---

### Post by Enigmatus on 2008-08-15
Well, since installing Ubuntu a few days ago, I seem to be suffering nothing but problems with it, I've been working with a member of the forum trying to resolve these, but as yet, no such luck. I shall detail some of the problems below:

- General non-responsiveness (i.e. I will open an application, which will then immediately stop responding, forcing me to forcefully quit it). If anything does open in this state, no text/buttons etc. are shown.

- When attempting to play full-screen games (these problems began occurring before the installation of aforementioned games, so it rules out those being the source of the problem), it will play fine for a while, but then will 'snap out' of fullscreen mode, freeze and the entire computer will become non-repsonsive.

- When typing on forums/Pidgin etc., it will regularly just 'jump' to the middle of the sentence (which it has done multiple times whilst I have been typing this)

If you would like anymore information, let me know :)

Thank you in advance for your assistance

---

### Post by lisati on 2008-08-15
First of all, it might be useful to start with just one problem.

I'll start with my two cents worth of the typing with pidgin stuff: Are you using a laptop? I sometimes get a similar effect when using the laptop's keyboard and my hand wanders too close to the touchpad.

---

### Post by Enigmatus on 2008-08-15
> **lisati said:**
> First of all, it might be useful to start with just one problem.

I'll start with my two cents worth of the typing with pidgin stuff: Are you using a laptop? I sometimes get a similar effect when using the laptop's keyboard and my hand wanders too close to the touchpad.

I am indeed, but I make a conscious effort to keep my thumbs and hands away from the touchpad when typing, so that's unlikely to be the cause.

---

### Post by mb_webguy on 2008-08-15
I'm not sure about the first problem, but I have an idea about the second.  I bet if you timed the fullscreen games, they'll drop out of fullscreen mode after the same amount of time, every time.  I had the same problem until I realized that they were dropping out of fullscreen after the exact amount of time the screensaver was set to kick in.  When the games are fullscreen, Gnome apparently doesn't receive any input, and thinks the computer is idle, and therefore activates the screensaver after the set amount of time, which obviously drops you out of the fullscreen game.  Turn off the screensaver or set it to a longer duration, and you should be fine.

As for your third problem, I'm not sure what you mean by jumping to the middle of the sentence.  Could you explain in a bit more detail?

---

### Post by Inane_Asylum on 2008-08-15
It may help also to post what kind of setup you're using, like vid card, processor, etc.

---

### Post by peakshysteria on 2008-08-15
> **Inane_Asylum said:**
> It may help also to post what kind of setup you're using, like vid card, processor, etc.

Second that. Without it we cannot dissect your problems and give thorough answers and possible solutions. 

For starters try with:
```
cat /etc/lsb-release
```
```
cat /proc/cpuinfo
```
```
lspci
```

---

### Post by Enigmatus on 2008-08-15
> **mb_webguy said:**
> I'm not sure about the first problem, but I have an idea about the second.  I bet if you timed the fullscreen games, they'll drop out of fullscreen mode after the same amount of time, every time.  I had the same problem until I realized that they were dropping out of fullscreen after the exact amount of time the screensaver was set to kick in.  When the games are fullscreen, Gnome apparently doesn't receive any input, and thinks the computer is idle, and therefore activates the screensaver after the set amount of time, which obviously drops you out of the fullscreen game.  Turn off the screensaver or set it to a longer duration, and you should be fine.

As for your third problem, I'm not sure what you mean by jumping to the middle of the sentence.  Could you explain in a bit more detail?

Ahh, that does make sense, thank you very much for your input! :)

---

### Post by Enigmatus on 2008-08-15
> **peakshysteria said:**
> Second that. Without it we cannot dissect your problems and give thorough answers and possible solutions. 

For starters try with:
```
cat /etc/lsb-release
```
```
cat /proc/cpuinfo
```
```
lspci
```

Distribution: Ubuntu 8.04.1 (Hardy Heron)

Regarding your second request, I shall copy and past the results:

> processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz
stepping	: 12
cpu MHz		: 1866.753
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor tm2 xtpr
bogomips	: 3737.73
clflush size	: 64


Regarding your third request, I shall do the same again:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


---

### Post by peakshysteria on 2008-08-15
Thanks. Do you have visual effects/Compiz turned on?

---

### Post by Enigmatus on 2008-08-15
I have the 'Cube' worktop changer on, but again, the problems were there before I did this :(

---

### Post by peakshysteria on 2008-08-15
Have you tried playing games both with visual effects/Compiz on and off? (The visual effects are, as I'm sure you know, more than the cube) I guess you had the effects enabled by default after install. I'm not to good with Intel. But my daughters machine (she's seven) are running Intel an visual effects and I've seen that she experience some of the same problems as you once in a while when playing games. Though I'm not entirely sure this is related to Compiz and your graphics driver. But so far it looks like my best bet. Check out Forlong's [Compiz-switch]("http://forlong.blogage.de/article/pages/Compiz-Switch") for easy Compiz on/off.

Are you having resolution problems of any kind? Or is that like it should be? And/or are you experiencing choppy/sluggish scrolling in your browser(s). And dose things sometimes seem unnecessary slow? 

Could you post the output of:
```
glxinfo
```
And
[Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")

---

### Post by Enigmatus on 2008-08-15
Nope, everything is generally fine apart from the response problems etc. that I detailed

---

### Post by Enigmatus on 2008-08-16
Any more thoughts? This has happened twice more since I established this thread, both times requiring me to shut down the computer via. the power button.

---

### Post by peakshysteria on 2008-08-16
You are not answering all questions man. Are you running your setup with Compiz on or off? And please try running the commands I mentioned in my last post.....now...zzzzz.... back to zzzzz..... sleep.........

---

