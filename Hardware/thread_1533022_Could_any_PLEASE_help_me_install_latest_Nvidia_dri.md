---
title: "Could any PLEASE help me install latest Nvidia drivers on my Dell Vostro 1700?"
date: 2010-07-17
forum: Hardware
---

### Post by Godspell on 2010-07-17
Hello all,

I've downloaded the latest Nvidia drivers (256.35) for Linux 32bit from their website.

My laptop is Dell Vostro 1700 and it has Geforce 8600M GT. It's not the best card, I know, but I really want to use the latest drivers.

So, can anybody please give me (simple) instructions on how to do this?
The laptop I'm using currently has ATI drivers 10.6 installed. They were easier to do so...just needed to drop into roots and do "./ATI...".

Unfortunately, I can't pull that on Nividia drivers because they kept saying X server is still running, regardless of what I've tried to kill that X.
I looked up on the Internet on how to kill X and there wasn't ANY straight answer that actually works.

I pressed Ctrl+Atl+F1 and typed ```
sudo killall gdm
``` but it said ```
No process found
``` so I assumed X had been killed and proceeded installing the drivers the following ways.

```
./NVIDIA-Linux-x86-256.35.run
``````
Permission denied
```Although, I was in the bloody root.

So, I did the following and guess what, it didn't work.
```
sudo sh NVIDIA-Linux-x86-256.35.run -k $(uname -r)
```It tried to unpack the package and stuff but ended up saying X is still running.

I tried ```
sudo /etc/init.d/gdm stop
``` and it did NOT work.

Seriously, this is very annoying. All I want to do is remove whatever drivers there and install the latest Nvidia drivers and move on.
But I can't...I've searched on the Internet for simple instructions and solution and found nothing! I don't understand why simple thing like this has to be complicated.

So, please....if any of know how to do this, let me know.
Thank you very much.

Regards,
GS

---

### Post by efflandt on 2010-07-17
Are you trying to do this from an X terminal or the console?  You cannot do it from a terminal in X.  You have to go to a text console (Ctrl-Alt-Fn, where Fn is one of F1-F6).  Once X is running again Alt-F7 takes you back to X.

But do you really need to go to all that trouble?  What do the new drivers do that you cannot do with a recommended nvidia driver installed from System > Administration > Hardware Drivers?  That would keep things more coordinated for kernel and other system updates.  Otherwise kernel updates might break your system and you would have to do something again with the video drivers to fix it.

I am running a newer Gforce GT220 and I simply used Hardware Drivers to install nvidia(195) drivers.  That is noticeably much faster than my old PC with default ATI drivers for a legacy Radeon X1300.

---

### Post by CoolJohnB on 2010-07-17
I also have a Dell Vostro 1700 and did the same as efflandt suggests, just go to System>Administration>Hardware Drivers, when you run it you get a choice of different drivers I had 2 for Nvidia tried them both, the recommended one gave me problems so I use the other one, which works fine.
Hope that helps.

---

### Post by Godspell on 2010-07-17
First of all, thanks to both of you for replying me. I was annoyed a bit earlier cause some of the threads I made had no reply whatsoever. At the end of the day, not having any reply means living with the problem. So, I was pretty bummed.

Fair points you both have made. I just thought it would be nice to use "latest" drivers. No particular reason.
It's interesting **efflandt** said it might "break" the system if I install latest drivers myself and when there's kernal update, because that's exactly what happened with my current laptop (acer aspired 5542).
ATI drivers 10.06 just dropped like that I had to re-install it couple of times.

About killing X, I tried it both ways, mate. From X terminal (by pressing Ctrl+Atl+F1) and Terminal,...X just would not die lol.
Well, it still would be nice to know how to correctly install the drivers, you know.

Anyway, thank you very much for your replies.

Best regards,
GS

---

### Post by Yellow Pasque on 2010-07-17
Ctrl+Alt+F1
```
sudo service gdm stop
cd <wherever you saved the NVIDIA file>
chmod +x NVIDIA-Linux-x86-256.35.run
sudo ./NVIDIA-Linux-x86-256.35.run
```

If you get an error about the kernel module, it's because nouveau is being used.
```
gksu gedit /etc/modprobe.d/blacklist-nouveau.conf
```
This will create a new text file. Copy/Paste this:
```
blacklist nouveau
```
Save. QUit. Reboot. Run the first section of code again.

---

### Post by Godspell on 2010-07-17
**Temüjin**, thanks man. I'll try it first thing tomorrow morning and let you know the result :)

Regards,
GS

---

### Post by Godspell on 2010-07-18
> **Temüjin said:**
> Ctrl+Alt+F1
```
sudo service gdm stop
cd <wherever you saved the NVIDIA file>
chmod +x NVIDIA-Linux-x86-256.35.run
sudo ./NVIDIA-Linux-x86-256.35.run
```If you get an error about the kernel module, it's because nouveau is being used.
```
gksu gedit /etc/modprobe.d/blacklist-nouveau.conf
```This will create a new text file. Copy/Paste this:
```
blacklist nouveau
```Save. QUit. Reboot. Run the first section of code again.

Hey, I did Ctrl+Atl+F1 and then tried to install the drivers but it returned with error.
So, I restarted my laptop and went into terminal and created "blacklist-noveau.conf".
From then on, the bootup screen is in low-res but I figured it's because nouveau isn't running.

The problem is, I can't do Ctrl+Atl+F1 anymore. Everytime I press these buttons, the desktop freezes (although Num lock is working) instead of taking me to black screen. 

I went into root and tried to install drivers from there but the installer returned with warning saying something like 'I shouldn't do this in runlevel-3 but 1'

So, I'm stuck. Please reply me asap.

Many thanks and regards,
GS

---

### Post by wojox on 2010-07-18
Here's what I used to manually install mine [Install NVIDIA drivers manually on Lynx]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

---

### Post by Godspell on 2010-07-18
**Wojox** thank you very much for your guide.
It didn't work exactly as according to your steps so I played around a bit and it worked at the end :D

I was reading your thread and found out there was another person who was having the same problem as me. The bloody nouveau wouldn't get disabled.

So, I had to go on to Synaptic Package Manager and completely remove 
xserver-xorg-video-nouveau. Then I did Ctrl+Alt+F1 and stopped the GDM and installed the Nvidia drivers. It worked like a charm xD

I have no idea why who-knows-what was making to difficult for me to install the drivers and was absolutely annoyed BUT your solutions worked out great.

So, thank you so much.
Thanks to all others who also contributed my thread :) Cheers.

Regards,
GS

---

### Post by Godspell on 2010-08-01
Right, as I've said above, I managed to install latest Nvidia drivers after many attempts.

Two days later, I installed updates via Update Manager and those drivers dropped.
I tried to re-install them just like the first time but didn't work.
So, I thought I'd use the drivers available from "Hardware Drivers" but when I checked, it was empty!

At the end, since the OS was newly installed, I got fed up and re-installed Ubuntu 10.04.

This time, I didn't try to be smart and just installed the ones available from "Hardware Drivers". Version 173 didn't work for me, it kept lagging. So, I installed 175 and it's been fine.

The small problem I'm having is, sometimes it acts slow with Compiz effects.
For example cube effect slows down a little bit when I started spinning it the first time but later on, it works fine. The same for the focus effect "Dodge".

I really don't like this. It didn't happen on latest drivers but as I mentioned above, I had to remove them cause every bloody time kernel gets updated, they dropped!

With these drivers (version 175), I feel that they're holding back the GPU from giving out what's necessary. Possibly, the stupid "powermiser". I've not played around with it yet. Just thought I'd ask here first for any solution.

So, let me know, folks. Graphics related issues are annoying because I face them everytime I use computer.

For those who suggested me to not to update the Nvidia drivers manually, y'all were right. It did screw me up big time lol

Cheers and regards,
GS

---

### Post by Godspell on 2010-08-02
BUMP

Nobody knows the answer to the above post?

---

