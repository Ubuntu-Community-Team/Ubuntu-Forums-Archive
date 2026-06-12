---
title: "My Ubuntu crashes on multitasking"
date: 2008-07-14
forum: General Help
---

### Post by Walther -FI- on 2008-07-14
Okay, let's get straight to the point.
I have Ubuntu 8.04 installed on my brand-new computer.
I made the computer from:
MSI P35 Neo-Fi MoBo
Intel Core2Quad Q6600 @ 2.4 GHz
ECS Nvidia GeForce 8800GT
4Gb of DDR2

(and a hd, a PSU from Zalman, a better CPU cooler, case from Antec... but I think that you don't need info from those)

The problem is that whenever I multitask a little- music, firefox, installing Steam games on wine, etc. , the Ubuntu crashes. The CPU usage never goes very high, neither does the memory usage.

With "crash" I mean that I cant do anything, I cant get to console by CTRL-ALT-F1, but sometimes I can CTRL-ALT-BACKSPACE -but when I log in it crashes immediately. The only solution is the raw pressing of power button

This is really weird- I have a powerful computer!

I hope that someone can help with this.

Walther -FI-

---

### Post by neoAnderson on 2008-07-14
It is apparently an issue with the 2.6.24- family of Linux kernels... these forums are flooded with people complaining that Hardy crashes. I used to think I was more at the receiving end because I have an HP laptop, but looks like user-built computers aren't exempt from the problem either. 

Maybe try to manually compile the 2.6.25- kernel and see if that makes a difference.

---

### Post by Walther -FI- on 2008-07-14
Thanks for answering- I think that I'm not ready yet to compile kernel myself, but I'd like to do that when I have the knowledge to do that.

I tried to find same kind of problems from forums- but didn't find any crashing problems from multitasking. But if it's a issue with the kernel...

Thanks!

---

### Post by Jim! on 2008-07-14
Ubuntu seems to suffer heavily from kernel panics. I'm hoping this is an issue they will solve soon, at least by the release of 8.10. Also do you have all updates installed? And are you running the proprietry Nvidia drivers? (I'm guessing you are because it sounds like you do gaming on your computer) It could be an issue with your graphics driver.

(System > Administration > Hardware Drivers)

---

### Post by Casper Hansen on 2008-07-14
My system did also crash when multitasking. I had Amarok running, a flash video in Firefox and Pidgin + som other programs. It crashed because of flash and Amarok wouldn't work together. The way I solved it was to install the nVidia driver with the programe EnvyNG and installed Adobe Flash Player 10.

- How did you install the driver for your nVidia card?

---

### Post by Walther -FI- on 2008-07-14
Well- 
I installed driver that Ubuntu throwed me at, should be good?
And yes, I've installed every update.

This is really disturbing- first I had bad-working computer because of the hardware, then bought better, and didn't get any help from that because of Ubuntu.
I could change to a different distro- but I don't want to, because I had the first touch to Linux with Ubuntu 7.10 and I really loved it.
Then, my cousin installed Gentoo for me because of some gaming problems I had. (Well, it  didn't help, games didn't work!)
But with this new computer...

Should I look for a different  driver?
Or is it really just the kernel?
Or, should I change to some other Ubuntu-based distro, let's say, Xubuntu for example? Or to a completely different distro?
If I can get my computer to work normally by changing distro, it doesn't take long to decide. But I really like Ubuntu more than Gentoo, that's for sure. :D

There is only one thing that I hate in Linux- everything feels to be beta, quite few things/programs work cleanly and perfectly. In Windozes are that plus- when they can hire people to do programs at their job, things usually are working cleanly.

But still I live non-windows life, for many good reasons. But for that one reason I might buy some day a Windows OS to use for playing games etc.

(Sorry for the offtopic)

---

### Post by tuxxy on 2008-07-14
Are you using GNOME?

---

### Post by Walther -FI- on 2008-07-14
Yes, I use Gnome desktop, I like it very much. I'm using out-of-the-box Ubuntu with only modifications are Compiz-fusion, Emerald theme manager, K3b and Wine installed.
This is because I have had my computer so short time.

---

### Post by tuxxy on 2008-07-14
Walther i took this from another 64 bit post stating problems I had from installing KDE apps even in GNOME

> mistakenly thought I should give KDE another try not long ago as it had been a while and thought it deserved atleast a chance and I had at that point not run it on Ubuntu.

After 10 minutes in KDE I realised not much had changed and it seemed even slower than ever, how it cannot run slow on an AMD X2 w/ 6GB RAM is beyond me, anyway I returned to GNOME and thought that would be it but no. The packages I had installed on the system to use KDE seriously messed up my GNOME, I had problems with graphics, apps not functioning correctly and also system lockups!

I think you can guess what I did next, once all KDE apps were removed GNOME functioned excellent again.

---

### Post by Walther -FI- on 2008-07-14
That sounds interesting... But well- i have not installed the whole KDE desktop, only K3b, a burning software. Could that make kernel panics even when I'm not using K3b?

---

### Post by markbuntu on 2008-07-14
Your problem is most likely with flash 9. I recommend getting flash 10b. Do not get flash10b2, it has serious problems.

I had a lot of problems initially but after many many updates, especially from Hardy proposed, and since I took out the 2 512MB ram and left in the 2 1GB ram I had installed, it has been smooth sailing on both 64 bit and 32 bit (I have both installed on identical hard drives).

Years ago, when I was working a lot with computers I knew that mixing ram was a recipe for disaster but I was assured by a number of people that this was no longer the case. Apparently I was misinformed.

I would also suggest getting the latest nvidia driver.

---

### Post by Jim! on 2008-07-14
> **Walther -FI- said:**
> That sounds interesting... But well- i have not installed the whole KDE desktop, only K3b, a burning software. Could thats make kernel panics even when I'm not using K3b? Although it doesn't seem like something that would usually occur, It's possible. I suggest you uninstall k3b and see how the system runs afterwards. If it doesn't crash within 3 - 4 weeks then it probably means you can rule out KDE apps being the cause of your system crashing.

Even though I've suggested you see how it runs without any KDE apps installed It's still strange that your computer is experiencing this problem, KDE apps really shouldn't have such an effect on your computers stability!

Also, If you want to do gaming on your computer why do you use Ubuntu/Linux instead of Windows? Wouldn't it be more desirable to dual-boot a Windows OS instead? (Just curious)

---

### Post by Walther -FI- on 2008-07-16
Okay, here's what I did:

I uninstalled K3b, so far, so good.
Then I found a newer driver for my 8800GT, and started installing it.
It was a VERY LARGE PROCEDURE, I don't recommend it to anyone!
Okay, it was installed (had to do that in no xserver terminal) and I wrote reboot.

Next thing I saw was a some "Ubuntu is running in a low-graphics mode." asking me for selecting my screen and video card. Ok, thought that it would now be perfect, but no. Same thing on every boot. And Ubuntu always said "System restart required" because it installed the old driver or something like that, even when I selected from propierty drivers that it's not in use (the old driver). I installed it again a couple of times, and decided to install Ubuntu again. (I think that it's because of Ubuntu trying to use the old driver and me trying to use newer.)

So, I installed Ubuntu from my live-cd again, and copied my data from an external drive. My computer crashed few times, _ even before installation of anything! _ That was strange, only doing something caused to crash. This time it was the data transferring from my ext. drive I think that it must be a kernel issue or xserver issue. (or both, sometimes I see Caps Lock and Scroll Lock lights flashing, meaning kernel panic, sometimes I only have to restart X.)

Now, when I play Team Fortress 2 on Wine, it just crashes at some time. It's disturbing. (by the way, got Steam games working for the first time in six months!)

And @ Jim!:
I would like to use Win XP and Ubuntu dual booting, and I did, but once I decided to resize partitions, delete one from xp and add it to Ubuntu, the partition table (or what is it?) crashed, nothing booted up, nothing worked. So, I installed Ubuntu to my whole drive. But that was on my older computer. 


EDIT: New kernel coming from update manager, let's see if that fixes crashes

EDIT: Nope, still crashing

---

### Post by Walther -FI- on 2008-08-24
Hello again,

Problem solved, it was a hardware fault (memories were broken) and now everything works fine.

Found out the problem when I installed Windows XP to dual boot- to see if it was a Ubuntu-problem. Got loads of BSOD:s... And i took the computer to store where I bought it, they put new memories in, and yeah.

Thanks to everyone who replied!

---

