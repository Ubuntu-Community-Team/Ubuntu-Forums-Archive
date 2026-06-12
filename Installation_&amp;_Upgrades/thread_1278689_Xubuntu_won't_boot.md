---
title: "Xubuntu won't boot"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by sirloganthestud on 2009-09-29
Hello all!  I am new to the forums and linux in general, but not new to computers.  I have had no previous experience with linux, so bear with me.  I have an old HP pavilion 733n desktop running Windows XP Home Edition with the following specs:

AMD Athlon 2400+ (2.0 GHz)
512MB of Ram
120 GB Western Digital HDD

It runs very slow, so I wanted to install linux so it would run faster.  My family uses it mainly for web browsing.  I downloaded xubuntu and burned the iso image to a CD-R disc.  When the Xubuntu screen came up, i chose "Install Xubuntu".  When I did, the next screen came up with this:

[17.116029] ata1.00: revalidation failed (errno=-5)
[27.280027] ata1.00: revalidation failed (errno=-5)

After a short delay, the xubuntu loading screen came up.  But soon after this screen popped up:


[17.116029] ata1.00: revalidation failed (errno=-5)
[27.280027] ata1.00: revalidation failed (errno=-5)
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands.

(initramfs)


The system just hangs there.  So what should I do to get it to boot?  I'm sure there are a million threads like this, and I'm sorry if there are.  Thanks in advance

Sincerely,

~Logan Thomas Seeley~

---

### Post by danns on 2009-09-29
I'm seeing bug reports about this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635)

---

### Post by sirloganthestud on 2009-10-05
So what should I do?

---

### Post by sirloganthestud on 2009-10-07
I'd assume this is a problem with the hard disk?

---

### Post by orngjce223 on 2009-10-07
> **sirloganthestud said:**
> I'd assume this is a problem with the hard disk?

 Nope, it's a problem with the ISO.  The dude above says it's a known problem - but sorry, I can't help you :(

---

### Post by sirloganthestud on 2009-10-07
I may just burn a new one.  Would that help?

---

### Post by Jose Catre-Vandis on 2009-10-07
Check the iso against the md5, you can use the integrity check on the CD also

---

### Post by sirloganthestud on 2009-10-07
> **Jose Catre-Vandis said:**
> Check the iso against the md5

How?

---

### Post by Dennis N on 2009-10-07
To check the md5sum from Windows XP you need a utility program. There are a number of these you can google to find and there is a list of some here:

[http://en.wikipedia.org/wiki/Md5sum#External_links](http://en.wikipedia.org/wiki/Md5sum#External_links)

You compare the result you get from running the utility to the published md5 sum from the download site (see the file MD5SUMS) for the exact same .iso that you downloaded. Assuming it was the U.S. download site for Xubuntu 9.04 the MD5SUMS file is among the downloadable files here:

[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/)

---

### Post by sirloganthestud on 2009-10-08
The md5sum of the .iso that I downloaded (9.04 desktop i386) matched the one on the xubuntu site.  So what should I do now?

---

### Post by Jose Catre-Vandis on 2009-10-08
Can you run it as live cd, or do you get the same problem?

---

### Post by LaneLester on 2009-10-08
> **Jose Catre-Vandis said:**
> Can you run it as live cd, or do you get the same problem?
I'm having the same problem, and before I found this thread, I tried two different downloads of the i386 and one of the amd64. None of them would boot.

I've had no trouble installing **Ubuntu** Karmics, so this is quite irritating.

Oh, and yes, these were all supposed to be just booting the live CD, not installing. I at least have sense enough to wait and see if the live CD will work before I install. :)

Lane

---

### Post by CannibalAngel on 2009-10-08
I am getting a very similar problem. If you find anything out could you post it here or in my thread? Thanks in advance!

---

### Post by LaneLester on 2009-10-08
Well, it seems to be a **Xubuntu** problem. I just successfully booted an **Ubuntu** amd64 beta live CD.

I don't understand why there is so much **hard drive** activity during a live **CD** boot.

I sure would like to try Xubuntu, but I guess I'll have to wait for the release or some notice that this problem has been fixed.

Lane

---

### Post by sirloganthestud on 2009-10-08
I can't install it or run it as a live cd.  I might try a different version of ubuntu.

---

### Post by LaneLester on 2009-10-08
After my successful boot of the **Ubuntu** live CD, I decided to try **Xubuntu** again. And yes, indeed, this time it booted... and installed!

My joy was short-lived, however. When I tried to boot the new Xubuntu hard drive partition, it didn't make it. The screen started flashing rapidly, and the process stopped at the terminal login, instead of starting X. The flashing was part of some kind of activity that prevented logging in even in the terminal.

So I'm still Xubuntu-less.

Lane

---

### Post by LaneLester on 2009-10-09
I'm very pleased to report that I'm typing this from Xubuntu Karmic Beta 64-bit!

[A new release]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/") was available today, and this time it worked. It took quite a few hours, but it's done.

The choice to install, rather than boot the live CD, didn't work. A bunch of things failed, including the partitioner (ubiquity?). Fortunately, I bailed out before anything bad happened.

So I booted the live CD session and installed from there. It went OK for a while, but then it got hung installing the language packs (why language packs after one has chosen their language at the very beginning?). Anyway, I let it sit on 86% for an hour or so, and then I hit the Skip button. 

That was OK, and the install proceeded to completion.

Lane

---

### Post by sirloganthestud on 2009-10-12
So would you suggest I install Karmic Koala?  Or would you suggest I try Hardy Heron?

---

### Post by LaneLester on 2009-10-12
Go with Karmic Koala! The problems I had were fixed a day or two later, and I now have a fully functional KK system.

However, I'm using Fluxbox for my window manager, because I think the current Xfce menu system is ridiculously user-unfriendly and complex.

Lane

---

### Post by sirloganthestud on 2009-10-12
*Sigh!*

Karmic Koala didn't work either!  It stops before booting saying "Unable to find live disc image" or something similar.  So should I try Hardy Heron, do you think it's a problem with my cd drive, or what?

---

### Post by sirloganthestud on 2009-10-12
Well, I couldn't run the disk check on the computer I am trying to install xubuntu on, so I ran the disk check on another computer.  I tested the Jaunty and the disk came up with 1 error.  Then I tested Karmic, which also came up with 1 error.  What the heck?

---

### Post by LaneLester on 2009-10-12
I'm out of ideas. Maybe someone else will chime in.

Lane

---

### Post by sirloganthestud on 2009-10-12
Hopefully!

---

### Post by sirloganthestud on 2009-10-13
It may be a problem with the CD drive because when I generated the md5 hash of the .iso I downloaded, it matched the hash xubuntu had posted; but when I ran the disk check on the cd it posted one error.  Could it be the drive?

---

### Post by sirloganthestud on 2009-10-13
I'm convinced it's the cd drive.  I was able to install Karmic succesfully on another computer using a cd I burned from a different computer than the original one.  I then tried it on the original computer and it didn't work.

---

