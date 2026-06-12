---
title: "Nvidia GeForce  FX 5200"
date: 2011-06-23
forum: Hardware
---

### Post by MG&amp;TL on 2011-06-23
Hi everybody, not sure if this in the right place, graphics cards are under 'hardware' aren't they?

Anyway, after problems with a graphics driver for the aforementioned card, a manual install eventually solved it.* My problem is it appears to be blacklisted, even though it's not on the list here:*

[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

Anyway, as it runs "glxgears" fine, and running "./compiz-check" works fine.

Compiz check see here:

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

However, desktop effects returns "scanning for available drivers", then "Desktop effects could not be enabled."

Note that I'm not just after desktop effects, although they are cool, I was kind of hoping someone has a similar problem and could offer a one-size fits-all solution (I want to eventually try and learn to program 3d things, which probably won't run at the mo), rather than the constant mucking about/crashing/profanity/reinstalling Ubuntu that the web offers.

Can anybody help please? :D Have only being using Ubuntu for about a month, XP convert, not afraid of crashing computer, although would rather not, I don't have too many files and I have a live cd.

EDIT: oh, btw, I dodged the blacklist, but nothing happened. Just realised I should have put that in the post.

[SIZE=1]P.S I don't suppose anyone knows what sort of skills an assistant/apprentice Ubuntu developer needs (?), I'm interested in computers and Linux, and I'm the sort of person that likes giving back. Particularly as it's free. I can use basic C++ if it helps, and a smattering of other programming languages too. Or alternatively, if someone has a link or a site or a helpful person I can follow? :)

[/SIZE]

---

### Post by pqwoerituytrueiwoq on 2011-06-23
you just need to install the driver for it 
that is all it took for my old geforce 5200tv
system->administration->hardware drivers

---

### Post by MG&amp;TL on 2011-06-23
Sorry, hate to sound so smug, but it's not as simple as that for me. :(

Crashed my 'puter several times doing that, and when it finally did work, nothing happened. Following web advice (can't remember where now :frown:), I did a manual install of an Nvidia driver, somewhere inside GRUB, root console, "sudo sh Nvidia....etc " Running a dimension 2400, 256 mb RAM  so that's proboably why it's different for me.

---

### Post by MG&amp;TL on 2011-06-23
Although I appreciate someone so experienced helping me.:)

---

### Post by pqwoerituytrueiwoq on 2011-06-23
if you want to uninstall the nvidia drive installed with nvidia's run file 
[FONT=Courier New]sudo nividia-installer --uninstall[/FONT]

---

### Post by MG&amp;TL on 2011-06-24
Sorry, trueiwoq, I don't see where this is going, I wanted to know why my card was blacklisted, even though it's not meant to be according to the first link I gave. Maybe uninstalling the nvidia driver helps in some way, if it does, please explain?

---

### Post by tacklestar on 2011-06-24
> **pqwoerituytrueiwoq said:**
> if you want to uninstall the nvidia drive installed with nvidia's run file 
[FONT=Courier New]sudo nividia-installer --uninstall[/FONT]
yup, if so  nvidia's run file is necessary.

---

### Post by realzippy on 2011-06-24
Which Ubuntu version do you run?

---

### Post by MG&amp;TL on 2011-06-24
Very confused now...Although thank you for all the replies, it's very nice of you.

I'm running Ubuntu 10.10, (almost) fresh install.
Dell Dimension 2400
Nvidia GeForce FX 5200
256Mb RAM
Pentium 4

No other OS on the system

Because installing NVIDIA drivers automatically from "Harware drivers" a) hadn't worked, and b) caused my 'puter to crash several times, I downloaded the right driver from NVIDIA, popped it on my desktop, then (following web page on subject - I'm not this good :D) ran GRUB bootloader, recovery mode, root console, then the following:

"echo options nouveau modeset = 0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf"

As I understand it, this disables the default driver.

"update-initramfs -u"

Don't have a clue what this does, I broke the cardinal rule and did it because the page told me to. I guess it updates something called initramfs. It didn't ask for a root password so I assumed it wasn't anything harmful. 

Rebooted as instructed. Root console again :

" init 3"

This just seemed to do a system-start-type-thing, "checking power system" etc.

"cd Desktop"

my file was on the desktop

"sudo sh NVIDIA-Linux-x86-173.14.30-pkg1.run"

Ran the Nvidia installer as per usual, hit "yes" to all the options about XORG.conf, then rebooted. No crash, just a new message in that time between BIOS/GRUB and Ubuntu login screen, it's very fast, something about "modeset = 0 does not apply for nouveau"
On the same screen, there's some more messages, again very fast, something about "failed to allocate RT chipset" , although this was there before...:confused:

Any ideas?

And thanks again for the input, there are thousands of computer forums out there, but how many reply to semi-newbies comments? Just this one. Thanks guys, great forum you have here.:D

---

### Post by realzippy on 2011-06-25
*Any ideas?*

Not exactly,but maybe some conflict with nvidia/linux (kernel) AGP driver...
What is your output from

```
lsmod | grep agp
```

?
..and please post your /etc/X11/xorg.conf file.

---

### Post by MG&amp;TL on 2011-06-26
_**"lsmod | grep agp" returns:**_

"intel_agp              26566  1 
agpgart                32011  4 nvidia,ttm,drm,intel_agp"

_**Xorg.conf is:**_

"# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 14 09:22:52 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
End Section
"

Thanks, realzippy, appreciate it. :D

---

### Post by realzippy on 2011-06-27
Would you please check the xorg.conf file again?
Is it the *whole* file you posted?

Missing the most important "device section" where the video driver is specified..

---

### Post by MG&amp;TL on 2011-06-27
oops :oops: Must remember to use 'gedit' rather than 'less'- that way I actually remember to turn the page...:mad:

Anyway, here's the WHOLE file: 
"

[SIZE=1]# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 14 09:22:52 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
"[/SIZE]

Sorry realzippy...still haven't quite got my head around terminal work, haven't used anything text-based...ever. Although now I'm getting used to it, it's much faster. :)

Unless you want "xorg.conf.failsafe" as well?

---

### Post by realzippy on 2011-06-27
No,no .failsafe, just wanted to see if nvidia installation was ok.
You mentioned that forlong's compiz-check was ok?
(your link from post #1  links to cc instead to your cc's output).
Since you are running 10.10 "dodging blacklist" according to your link
(which originally is from 2007)  might not work,since compiz-manager isn't used anymore (according to [http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist))...
read something about HEX editing the compiz binary which includes the blacklist pci-ids...

---

### Post by MG&amp;TL on 2011-06-27
To start with, it said that there may be hardware compatibility problems and would I like to dodge the blacklist, so I said yes, then realized that it was actually asking 'HAD I dodged the blacklist' so then had to do it manually, [-( via terminal, as described in the post from 2007 I linked to. Must be more careful about dates.

 I then re-ran compiz-check and it popped up fine, saying that everything should be ok. Note that I'm not after the effects, I'm just one of those people that gets annoyed if something doesn't work as intended. And I might want to run (or program! :-?) 3-d graphics at some point in the future...

Err...can deal with terminal code, programming languages, or simple Ubuntu concepts, but I'm afraid you've lost me with HEX. Is it a person? Group? Program? And if so, what do I do about it? I installed compiz as a test fairly recently, about two weeks ago if memory serves. Just starting ubuntu then...happy days. :)

---

### Post by MG&amp;TL on 2011-06-27
Hmmm...that's interesting.

It's probably unrelated, but I've just noticed that if I run glxgears, and then close the 'gears' window, it closes, but with a 'fatal error' -well it would be, I've just terminated it, but it probably shouldn't do this, should it?

```
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
12542 frames in 5.0 seconds = 2508.384 FPS
12548 frames in 5.0 seconds = 2509.594 FPS
12550 frames in 5.0 seconds = 2509.968 FPS
12465 frames in 5.0 seconds = 2492.817 FPS
12369 frames in 5.0 seconds = 2473.662 FPS
12117 frames in 5.0 seconds = 2423.215 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 42 requests (42 known processed) with 0 events remaining.

```X server sounds familiar from my excursions from crashing Ubuntu :D
As I said, probably unrelated, but interesting. Thanks for all the help so far, realzippy, learning a lot. And I've had a "bean upgrade"!

---

### Post by realzippy on 2011-06-28
About the hex thingy:
eg. in post #8 of
[http://ubuntuforums.org/showthread.php?t=1467202](http://ubuntuforums.org/showthread.php?t=1467202)
...of course you have to watch out for "your" pci-id.....

---

