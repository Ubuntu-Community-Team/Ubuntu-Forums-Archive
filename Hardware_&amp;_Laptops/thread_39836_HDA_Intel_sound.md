---
title: "HDA Intel sound"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by matthew on 2005-06-06
Okay, I've successfully installed Hoary on 4 computers now. This is the newest, and the newest challenge.

I am trying to get the sound working on a computer that has onboard sound in the form of the Intel High Definition Audio as described on this HOWTO page:

[http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto)

All I have done so far with the install is this:

1) install ubuntu from disk -no problems, all installed quickly and properly

2) do all security updates, etc. -just using the default repositories

3) use the install script from [http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646) -worked beautifully with no errors

4) Removed the marilliat repositories and changed the repositories in sources.list to these:

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

5) installed all updates using this repositories list -no errors

6) tried all the steps listed at [http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto)
specifically trying the second method as listed on the bottom of the page.

Everything worked great until the very last step of #6 where the following happened:

myrootprompt # dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

dpkg: error processing alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb


Any ideas of what to do now??

Thanks in advance!

---

### Post by matthew on 2005-06-08
update: I noticed no one had responded so I thought I would walk myself through the process again and noticed an error I had missed last night (I have to quit doing this stuff when I'm tired). Anyway, here is where the error occurred and what it is.

I tried to perform the last step from [http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto) in the wrong directory.

For the previous step I had to be in /usr/src/linux-headers-2.6.10-5-686 however for the final dpkg step I had to return to /usr/src, but this wasn't noticed...it probably should have been obvious to me, but it wasn't.

Well, that was simple, wasn't it? Hopefully this will help someone else. I'm going to go and listen to some music now.

---

### Post by PryGuy on 2005-06-08
[Read this!](http://ubuntuforums.org/showthread.php?t=36870) It appears that I had the same problem

---

### Post by matthew on 2005-06-08
[QUOTE=PryGuy][Read this!](http://ubuntuforums.org/showthread.php?t=36870) It appears that I had the same problem[/QUOTE]

Thanks! I'm glad I'm not the only one. Actually, this has been a lot of fun figuring out how to pay close attention to the little details and learn the inner workings of stuff.

---

### Post by PryGuy on 2005-06-08
Yeah, that's what I thought as well... I'm mostly a Windows guy, dreaming of making a switch to Linux (or MacOS X as they are going to switch to Intel and as a result will be cheaper I hope) and I'm spoiled by the Windows Installer's "Next" buttons let us say. :) 

I don't actually think these are "little details", in fact they appear to be little for us but not for the Linux itself. And this is ANOTHER OS, and it has another very solid philosophy (and I think that Windows' only philosophy is money, nothing else lol) and we of course will have to learn it. It's just like with the foreign languages; beginners studying other languages try to copy the constructions of their own language combining them with the words of the language they study. So think that's about us too! 

Studying Linux is a looong way! Good Luck to all us! :)

---

