---
title: "Nvidia graphics and monitor not working on Acer 5920g"
date: 2010-10-18
forum: Hardware
---

### Post by toille on 2010-10-18
Hi, just decided to go ahead and install Ubuntu 10.10 but not having much luck.

First of all it doesn't seem to recognise my monitor properly and sets the maximum resolution to 800x600. However if I select recovery mode and then boot normally it works at the correct resolution of 1280x800 automatically.

Secondly I've been trying to install the Nvidia drivers for the card in hope that will help (and for performance) however x.org says unable to load the nvidia driver and to look in the kernel log. The kernel log says the following:

```
Oct 18 18:00:10 laptop kernel: [  110.255739] nvidia: module license 'NVIDIA' taints kernel.
Oct 18 18:00:10 laptop kernel: [  110.255743] Disabling lock debugging due to kernel taint
Oct 18 18:00:11 laptop kernel: [  111.246681] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 18 18:00:11 laptop kernel: [  111.246704] nvidia 0000:01:00.0: setting latency timer to 64
Oct 18 18:00:11 laptop kernel: [  111.246716] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Oct 18 18:00:11 laptop kernel: [  111.246779] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:0407) installed
Oct 18 18:00:11 laptop kernel: [  111.246783] NVRM: in this system is not supported by the 260.19.12 NVIDIA Linux
Oct 18 18:00:11 laptop kernel: [  111.246786] NVRM: graphics driver release.  Please see 'Appendix A -
Oct 18 18:00:11 laptop kernel: [  111.246789] NVRM: Supported NVIDIA GPU Products' in this release's README,
Oct 18 18:00:11 laptop kernel: [  111.246792] NVRM: available on the Linux graphics driver download page at
Oct 18 18:00:11 laptop kernel: [  111.246795] NVRM: www.nvidia.com.
Oct 18 18:00:11 laptop kernel: [  111.246809] nvidia: probe of 0000:01:00.0 failed with error -1
Oct 18 18:00:11 laptop kernel: [  111.246864] NVRM: The NVIDIA probe routine failed for 1 device(s).
Oct 18 18:00:11 laptop kernel: [  111.246879] NVRM: None of the NVIDIA graphics adapters were initialized!
```

However the card in my laptop is an 8600m GT which is listed as supported.

The display and graphics worked fine on 10.04 and also on Mint.

Any help would be appreciated.

Cheers,
Toille

---

### Post by DelusionalX on 2010-10-19
I'm having the same problems with my 5920G although it is not really a 5920G specific problem.

What is happening:
Ubuntu 10.10 screws up the nvidia drivers
You can't install a new driver because it will lock you in a no-GUI tty1-console boot (which is where I'm at)
A fresh install will cause the same problems

All you can do right now is wait for a fix (there doesn't seem to be one right now) and use another OS.

My story is this:
Had 10.04
upgraded to 10.10
error, no fix, no boot
fresh install
install nvidia drivers
error, no fix, tty1 console at boot
fresh install
removed Nouveau (read that would solve it)
error, no fix, tty1 console
...

So now I'm just waiting for a fix or at least a decent description on what I have to do.
I don't want to do another fresh install and end up with still no GUI boot.

---

### Post by zenarcher on 2010-10-19
I'm having the same situation with Nvidia GeForce 8400GS cards in three of my computers.  Install in a 6xxx series worked fine.  I tested Kubuntu 10.10 from Alpha 1 through the RC with no problems at all and in the end, with the Final Release, I'm unable to do anything.  I've tried a dozen different possible fixes, none having worked.  I moved over to Debian Squeeze where everything is working just fine.  My monitor just goes to sleep when booting up.  I see a short splash screen and that's it.  Looking at the hard drive light, the system continues to boot up, but the monitor is sleeping.

There's a real issue between Maverick and 8xxx series Nvidia cards and right now, you just can't use Maverick.

Cheers,
zenarcher

---

### Post by DelusionalX on 2010-10-20
> **zenarcher said:**
> I'm having the same situation with Nvidia GeForce 8400GS cards in three of my computers.  Install in a 6xxx series worked fine.  I tested Kubuntu 10.10 from Alpha 1 through the RC with no problems at all and in the end, with the Final Release, I'm unable to do anything.  I've tried a dozen different possible fixes, none having worked.  I moved over to Debian Squeeze where everything is working just fine.  My monitor just goes to sleep when booting up.  I see a short splash screen and that's it.  Looking at the hard drive light, the system continues to boot up, but the monitor is sleeping.

There's a real issue between Maverick and 8xxx series Nvidia cards and right now, you just can't use Maverick.

Cheers,
zenarcher

I don't think it's only the 8-series. But anyway, I really hope this gets fixed soon. I know they implemented some changes in X in the past few days but it seems they really messed up this time.
Every nvidia mobile card is experiencing unfixable problems.

---

### Post by toille on 2010-10-20
Well its good to know im not alone on this one!
My only guess judging from that log is that the graphics cards arnt been reported back correctly so therefore the driver wont load.

Did other people have the screen res issue? Because it weird that loading up the recovery one would get my res to work fine but the normal boot wouldnt?

---

### Post by DelusionalX on 2010-10-21
> **toille said:**
> Well its good to know im not alone on this one!
My only guess judging from that log is that the graphics cards arnt been reported back correctly so therefore the driver wont load.

Did other people have the screen res issue? Because it weird that loading up the recovery one would get my res to work fine but the normal boot wouldnt?

Loading which recovery? Booting in recovery? Or loading a backup xorg.conf file?

What I've read today is that you can run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
(source: [http://start.ubuntuforums.org/showthread.php?p=9957053](http://start.ubuntuforums.org/showthread.php?p=9957053))
and that that COULD fix it.
I haven't tried it yet because I have to reinstall my 10.10 and I don't have the time to do that now.

But you can always try that command and report back. :)

---

### Post by toille on 2010-10-21
I remember seeing that before but can't remember for sure if i tried it or not.
I shall do it now and report back.

And by recovery mode i meant choosing the recovery option from the grub list then selecting normal boot from the next menu

---

### Post by toille on 2010-10-21
Well I tried that command, and as far as I can tell, it has done nothing.
Still stuck with a max res of 800x600.
Something tells me I may have to wait till the next release of Ubuntu for this laptop.

---

### Post by DelusionalX on 2010-10-21
> **toille said:**
> Something tells me I may have to wait till the next release of Ubuntu for this laptop.

Let's hope that will not happen.

---

### Post by mgiuca on 2010-10-21
I am having a problem which just started in 10.10 with an nVidia 8600M GT (the exact same graphics card), on a Dell laptop. It sounds like a bit of a different problem -- it works fine with the laptop's screen, but when I plug it into an external monitor (Acer H234 HBMID 24"), I get both the external monitor and laptop screen going black (but I can still see the mouse cursor).

I reported it here:
[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/659851](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/659851)

Not sure if this is the same bug, therefore, but it seems related (since they both happened in 10.10 with the same graphics card).

Note that this is only a problem with the nVidia proprietary drivers. It works fine (but without the 3D effects) if I switch to the Nouveau open source drivers (but I'm not sure how you can do that without being able to see the screen -- if you hit Ctrl+Alt+F1 do you see a login prompt? In that case you can probably apt-get install the correct drivers, but I'm not sure exactly what to get.)

---

### Post by br-amm on 2010-10-24
I'm having the same issue after installing the drivers for the GeForce G 310M on my Samsung Q330. I'll use the Intel GMA HD chipset for the time being...

---

### Post by zeromx on 2010-11-17
Ive got the exact same problem, ive got a ACER 5920 and when i installed ubuntu 10.10 all was well until i tried to install the display drivers and thats when it all went down hill.

---

### Post by Dao984 on 2010-12-01
Hi guys, look [here.]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/616023")
However i don't remember very well how i have fix it, but i remember that i have to install 10.10 x64. I believe its work out of the box whit nvidia-current. Only some time Ubuntu start in low-graphics and don't find xorg, then i have to recovery xorg and i solve it run nvidia-xconfig like root.
I hope that u can solve your problem. sry my very bad englis cya

---

