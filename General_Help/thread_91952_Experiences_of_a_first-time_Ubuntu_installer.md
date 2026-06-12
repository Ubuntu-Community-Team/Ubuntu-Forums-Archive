---
title: "Experiences of a first-time Ubuntu installer"
date: 2005-11-18
forum: General Help
---

### Post by tech_101 on 2005-11-18
A bit of background:  I'm an IT guy that works pretty much exclusively with windows.  I've tried dozens of different Linux distros out over the past 7 years, hoping to find one with all the features I'm looking for, without luck so far.

However, I'd heard a lot of buzz about Ubuntu lately, so I thought I'd try it out.  I downloaded the i386 cd iso of "Breezy" through bittorrent, and burnt it.  My first impressions were very favorable.. until the install died when installing the base packages.  Ok, no big deal.  Googled it, found that people were having the same problem I was when burning the cd at too high of a speed.  Re-burnt it at 4X, the install was flawless.

This was one of my spare computers, a p3-1ghz, 512MB RAM, 20GB hard drive.  A Compaq Deskpro EN, to be exact.  Hardware detection was excellent, every on-board device was detected and the drivers installed (compared to windows 2000, which requires you to navigate compaq's poorly designed support site to find video, lan, and sound drivers).

Booted to the very pretty login screen fairly quickly (not expecting miracles from a p3).  Logged in, and the first thing I wanted to do was install firefox 1.5rc3.  Found a short article on installing 1.5b2, used the new package name, it installed no problem.  Installed a few extensions, added some bookmarks, all good.

Next was playing mp3's.  I had used Linux a bit before, so I knew that I wanted to use XMMS for playback.  Took a look at the ubuntu guide for 5.04 (I guess 5.10 is still too new to have a completed guide?).  Followed the instructions for installing the codecs and XMMS, and there it was.  The only thing that I had to change was XMMS' default output to ALSA.

I'm very impressed with pretty much everything about this distro, my only real problem is that it's REALLY SLOW.  Programs take way longer to load that they do with win2k installed, it takes longer to boot, and when just a couple of programs are running it slows to a crawl.

Maybe I'm doing something wrong?  I'd be happy to try any suggestions people have to offer.

Justin

P.S. Sorry for the long-winded post, I wanted to express my impressions so far.

---

### Post by Efwis on 2005-11-18
hi and welcome to ubuntu.

type uname -r  and see what Kernal you are using. with the p3 it is recommend to use the 686 kernel instead of the 386 kernal.
if you have the 386 kernal, install the 686 kernel from synaptic.

open synaptic, then click on search and enter the following.

**linux-image-2.6.12-9-686**
then mark it for installation. After it has installed you can remove 
**linux-image-2.6.12-9-386** if you want to. 

reboot the computer. and choose the 686 kernal

If you are dual booting and you don't want to remove the 386 kernel, just choose the 686 kernal in Grub at reboot. not sure if this is choice to do if Ubuntu is the only OS on the computer. maybe someone else can answer that one :)
Let us know if that did the trick.

---

### Post by taurus on 2005-11-18
You have a 512MB of RAM!  It shouldn't be slow when you open a program at all!  What programs are you talking about here?  And regarding bootup, turn off stuff that you don't need to run as a daemon and it will speed up the boot process...

---

### Post by pickarooney on 2005-11-18
[QUOTE=Efwis]hi and welcome to ubuntu.

type uname -r  and see what Kernal you are using. with the p3 it is recommend to use the 686 kernel instead of the 386 kernal.
if you have the 386 kernal, install the 686 kernel from synaptic.
[/QUOTE]

Wow, this is the first time I've heard this. I imagine most Ubuntu users will have PCs of at least P3 spec - is this common knowledge, and is the difference very noticeable?
Why is this not used by default once the installer has detected the CPU?

---

### Post by Efwis on 2005-11-18
[QUOTE=pickarooney]Wow, this is the first time I've heard this. I imagine most Ubuntu users will have PCs of at least P3 spec - is this common knowledge, and is the difference very noticeable?
Why is this not used by default once the installer has detected the CPU?[/QUOTE]
actually you would be surprised at how many of us use AMD processors. That is why the 686 isn't default installed.
They are faster, easier to overclock, actually rated best for gamers, and less expensive to replace then intel pentiums.
AS for comon knowledge no. and I can't speazk about performance since I use AMD only.

---

### Post by hw-tph on 2005-11-18
[QUOTE=Efwis]actually you would be surprised at how many of us use AMD processors. That is why the 686 isn't default installed.[/QUOTE]

Not a lot of people use pre-Athlon AMD CPU's, so switching to 686 (the Athlon does everything the 686 (Pentium Pro) does and then some) as default for Ubuntu installs wouldn't be too crazy a decision. Or, better yet, include a selector in the installer or simply grep /proc/cpuinfo for CPU information and select a kernel image based on that.


Håkan

---

### Post by Efwis on 2005-11-18
[QUOTE=hw-tph]Not a lot of people use pre-Athlon AMD CPU's, so switching to 686 (the Athlon does everything the 686 (Pentium Pro) does and then some) as default for Ubuntu installs wouldn't be too crazy a decision. Or, better yet, include a selector in the installer or simply grep /proc/cpuinfo for CPU information and select a kernel image based on that.


H&#229;kan[/QUOTE]
That would probably be a good idea to recommend for dapper developement. or dapper+1.

---

### Post by Chayak on 2005-11-18
Odd thing really, I installed a vanilla kernel (2.6.14.2) for my Athlon and it spit out a named kernel of 386.  I did turn on partial preempting and set the timing to 1000 as this is a workstation and not a server.  I got a dramatic increase in the responsiveness of my desktop.

---

### Post by Zonkle on 2005-11-18
I didn't know that even each Kernel version has different versions for different CPUs !

Is there some rules or guide to which Kernel version to use ?
I thought I just had to look for the latest and whether 64bit or 32bit.

Thanks.

---

### Post by Efwis on 2005-11-18
[QUOTE=Zonkle]I didn't know that even each Kernel version has different versions for different CPUs !

Is there some rules or guide to which Kernel version to use ?
I thought I just had to look for the latest and whether 64bit or 32bit.

Thanks.[/QUOTE]
for most parts, the general rule is as follows.

386 = AMD
686 = Intel
386-smp=dual processor AMD
686-smp=Dual processor Intel

AS for the 64 bit part, that is all new in the last 2 or 3 kernels, when AMD came out with the 64bit tech.

Not all distros follow this basis, and this is actually something new in the last few versions of kernels. don't ask me when, I don't know, but I know thats the case.

---

### Post by sailor420 on 2005-11-18
[QUOTE=Efwis]for most parts, the general rule is as follows.

386 = AMD
686 = Intel
386-smp=dual processor AMD
686-smp=Dual processor Intel

AS for the 64 bit part, that is all new in the last 2 or 3 kernels, when AMD came out with the 64bit tech.

Not all distros follow this basis, and this is actually something new in the last few versions of kernels. don't ask me when, I don't know, but I know thats the case.[/QUOTE]

I'm pretty sure the 686 will run on any Athlon or newer AMD processor...

---

### Post by Efwis on 2005-11-18
[QUOTE=sailor420]I'm pretty sure the 686 will run on any Athlon or newer AMD processor...[/QUOTE]
yes it will, but it' smore optimized for Intel.

File description for the 686 kernel.
> Linux kernel image for version 2.6.12 on PPro/Celeron/PII/PIII/PIV.

This package contains the Linux kernel image for version 2.6.12 on
 Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV,

File description for 386 Kernel
> Linux kernel image for version 2.6.12 on 386.

This package contains the Linux kernel image for version 2.6.12 on
386,
And last but not least
File description for the K7
> Linux kernel image for version 2.6.12 on AMD K7.

This package contains the Linux kernel image for version 2.6.12 on
AMD Duron/Athlon,

technically I should be using the K7 kernal, but it doesn't properly support my AMD Athlon/Duron XP 1800+. Graphics suck, slow response times, pegged out CPU processes with certain apps.
The 686 bogs my CPU down immensly.
 With 386 image, I have full functionality of my CPU, graphics etc. so thats the one I use.

---

### Post by DrBair on 2005-11-18
Might want to check into DMA if its taking a long time to load stuff. Easiest way to do it is in a console type: 

sudo hdparm /dev/hda 

or whatever your drive name may be.  DMA should be on, if not issue the command:

sudo hdparm -d 1 /dev/hda

---

### Post by ofek on 2005-11-18
[QUOTE=pickarooney]Wow, this is the first time I've heard this. I imagine most Ubuntu users will have PCs of at least P3 spec - is this common knowledge, and is the difference very noticeable?
Why is this not used by default once the installer has detected the CPU?[/QUOTE]
Because then ull need 2 kernels on the installer cd (386 and optional 686).
The whole idea of ubuntu if to be 1 cd distro and a normal kernel is 40mb, which is alot.

---

### Post by mcduck on 2005-11-18
Athlon and AthlonXP should run both 686- and K7-kernels with no problems. It's like k7 is also 686, but 686 is not K7 ;)

Athlons do everything that Intel's 686-CPUs do, plus 3DNow. 386 works for everything from 386 to latest CPU's, but doesn't include support for newer CPUs floating point and multimedia instructions.

I have AthlonXP and I've tried them all, most of the time there is no big differences, 686- and K7-kernels perform a bit better than 386, and K7-kernel is a bit faster in some things but difference is not big. Now I'm running K7-kernel.

---

### Post by tech_101 on 2005-11-19
Thanks, everyone.  I've installed the 686 kernel, which did speed everything up a bit, checked DMA, and it is on.. As for turning off stuff that I don't need to run as a daemon, I have no idea how to go about this.. if anyone knows of some directions, I'd be glad to try this out as well.

Mainly, it's Firefox and OpenOffice that are really slow.. Firefox takes forever to switch between tabs, and openoffice opens extremely slowly.

Justin

---

### Post by ed_d on 2005-11-19
I have now installed Badger on 2 PCs and find the performance very good. Firefox and OO open much faster than they did under Core 4 and Core 3.

---

### Post by Denis on 2005-11-19
[QUOTE=tech_101]Mainly, it's Firefox and OpenOffice that are really slow.[/QUOTE]
I've seen this thread on how to improve Openoffice performance. It is actually for OpenOffice2, but maybe it can be a help for you too. 
[http://ubuntuforums.org/showthread.php?t=83308](http://ubuntuforums.org/showthread.php?t=83308)

---

### Post by thecdn on 2005-11-19
[QUOTE=tech_101]Mainly, it's Firefox and OpenOffice that are really slow.. Firefox takes forever to switch between tabs, and openoffice opens extremely slowly.[/QUOTE]

I don't know why you might be having speed issues with these apps but why don't you try the Opera browser and see what happens? I've used firefox for a year and just recently tried Opera and love it. Speed is great.

---

### Post by varunus on 2005-11-19
Firefox tab switching trouble?  Hmm...What video card do you have?  You mentioned your proc and RAM, and this should be enough...You shouldn't have an issue with this...

Also, you may want to try epiphany.  Install epiphany-browser from synaptic; its a GNOME browser that uses Gecko, so all the plugins will still work.  You can also install epiphany-extensions for some extra features.

Its a pretty good browser, and it'll have adblock soon, so I intend to fully give it a whirl once it does.

---

### Post by ferentix on 2005-11-19
Whilst on the topic of kernels and speed issues, is there a particular kernel that might work better than the default one for a Cyrix MII 300MHz processor? My Ubuntu is a bit sluggish...

---

