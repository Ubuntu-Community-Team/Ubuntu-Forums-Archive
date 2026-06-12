---
title: "Problem with VMWare Player Install"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2009-02-28
All,

Using install guide(s) at:

[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)
and
[http://czarism.com/easy-peasy-vmwareplayer-vmplayer-ubuntu-hardy-804](http://czarism.com/easy-peasy-vmwareplayer-vmplayer-ubuntu-hardy-804)

I got error in the first and posted to the thread, but no response so looked up the second and get all through, then insert the Win CD, click "setup" and get this error:

> This CD-ROM is from an older version of Windows than the one you are presently using. Setup functionality from this disk will be disabled.

I am trying to install W2KPro, so something in the distribution on the VMWare side seems to think it has newer Win version.  Does anyone know what version of VMWare player distro I should be using for W2K?

I found and installed:

VMware-player-2.0.5-109488.i386.tar.gz

Thanks All!

OMR

---

### Post by roshanjose on 2009-02-28
Why use VMWare. VirtualBox is better and safe and easy to use.

Download one and use it

---

### Post by OldManRiver on 2009-03-01
> **roshanjose said:**
> Why use VMWare. VirtualBox is better and safe and easy to use.

Download one and use it
Sounds interesting, and OK on non-commercial machines, but commercial machines have requirement to run on 100% of all Win Apps, and Wine and VBox have disclaimer they don't run 100%.

Besides VMWare is setup so you can have Win, install VMWare then run Linux under it on Win or the preferred way of have Linux, install VMWare and run Win under it.  Later is obviously preferred due to OS design, security, lack of memory leaks and OS stability.

Besides you did not give link to VBox.  I'll see if Synaptic Pkg Mgr has it.

OMR

---

### Post by OldManRiver on 2009-03-01
Found it in SPM and installed but have no clue about using it, so off to Google for HOWTO.

OMR

---

### Post by OldManRiver on 2009-03-02
VirtualBox installed OK but would not install the Windows and always errors.

OMR

---

### Post by OldManRiver on 2009-03-03
All,

So back to my Q, what is right version of VMW Player?

OMR

---

### Post by dabl on 2009-03-03
Current release is 2.5.1 :

[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

Runs great on my Kubuntu 8.10 system.

---

### Post by OldManRiver on 2009-03-05
> **roshanjose said:**
> Why use VMWare. VirtualBox is better and safe and easy to use.

Download one and use it
R,

See your install of VirtualBox was not as easy as you make it sound:

[http://ubuntuforums.org/showthread.php?t=1083335&highlight=vmware+server](http://ubuntuforums.org/showthread.php?t=1083335&highlight=vmware+server)

OMR

---

### Post by OldManRiver on 2009-03-05
All,

Since I was following the HOWTO at:

[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

I made the following entry to it on page 34:

Following this procedure I get to:
```
cabextract 'nameofarchive.exe' -d 'our working directory'
```
and it blows up.

Yes I did understand the two strings above were marker which I needed to sub for.  My subs were:
```
'nameofarchive.exe' ==> '/home/iso-extract/Win2KPro.iso'
'our working directory' ==> '/home/iso-extract/files/'
```


Everything else has gone fine up to that line of code.  Is there a work around for this line or alternate method to extracting the file.  I did not get any errors from the install of "cabextract", so why doesn't it work?

What about just loading from the CD?

I got further information, from #vmware on irc.freenode.net that leaves me confused, as they say you can not load or use Windows .iso or image inside player, which conflicts with statements made in the HOWTO I was following.  They said only "server" allows you to load the Win CD.

I did deviate from the HOWTO, when I could not get a response to fix it, I found and used the HOWTO at:

[http://czarism.com/easy-peasy-vmwareplayer-vmplayer-ubuntu-hardy-804](http://czarism.com/easy-peasy-vmwareplayer-vmplayer-ubuntu-hardy-804)

which allowed me to finish a successful install of the player, without being stuck at the "cabextract" point.

Need a response and would like to discuss automation of this install as bash script and maybe inclusion into U-Kernel or Synaptic Pkg Mgr in later Ubuntu releases.  Seems like this is something every advanced user wants/needs, so should be automated.

OMR

---

### Post by cariboo on 2009-03-05
I use Virtualbox. I set it up using the deb from [here.]("http://www.virtualbox.org/wiki/Linux_Downloads") I have XP Pro, Vista 64 and Windows 7 64 running in VM's. 

When you create a vm, it asks you what type of OS you want to setup, You can choose almost anything. I have successfully setup Win95+MS Bob, Win98, WinMe,  Win2K, XP, Vista 64 and Windows 7 64. Plus a lot of Linux variants.

Jim

---

### Post by OldManRiver on 2009-05-16
> **cariboo907 said:**
> I use Virtualbox. I set it up using the deb from [here.]("http://www.virtualbox.org/wiki/Linux_Downloads") I have XP Pro, Vista 64 and Windows 7 64 running in VM's. 

When you create a vm, it asks you what type of OS you want to setup, You can choose almost anything. I have successfully setup Win95+MS Bob, Win98, WinMe,  Win2K, XP, Vista 64 and Windows 7 64. Plus a lot of Linux variants.

Jim

J,

Appreciate the comment, but I stated before I tried it and it did nothing, so not sold.

OMR

---

### Post by OldManRiver on 2009-07-21
All,

I've never got this working and want off Win bad, but since I have customers to support, that only apps in Win run, then have to have this working.

After talking to one of the gurus at our local opensource meetup, I tried again and actually got VB OSE installed.

But when I attempt to run get error:> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

HELP!!

OMR

---

### Post by OldManRiver on 2009-08-11
All,

Still looking for answers here

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #7 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

I have VBox running XP, but still want to master the VMWare install!

OMR

---

