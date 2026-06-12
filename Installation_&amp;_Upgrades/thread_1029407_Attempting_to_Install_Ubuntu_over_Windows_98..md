---
title: "Attempting to Install Ubuntu over Windows 98."
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by ripple.effect on 2009-01-03
Ok, I was offered an old desktop PC to do as I wish with. So I've decided to turn it into somewhat of a pet project. I'll be replacing the current windows 98 o/s with Ubuntu. I would like to completely replace the partition making the computer  Ubuntu based only.  However, of course being somewhat/mostly new to the Linux environment, and the fact that I'll be working with outdated software has naturally caused me to run into a few snags.

Here is the old System’s Properties:
Windows 98 
Second Edition
4.10.2222 A
Intel Pentium II, 266
Custom-Built System
224.0MB RAM

System Resources: 94% free
File System: 32-bit
Virtual Memory: 32-bit
Disk Compression: Not Installed
PC Cards (PCMCIA): Not Installed 

1. There is no internet connection for the old PC whatsoever.
I would like to know if there is a way to perform this installation offline.

2. I do have another newer PC right next to the old PC (with an Internet connection) which I can use to gather necessary software for this project, which is currently being done by burning software to CD-R’s and transferring it to the old PC.
I do have a 4GB SanDisk removable thumb drive, which unfortunately is not being recognized by the old PC at this time.

I’m excited to do this project and as much help that might be offered would be very much appreciated.

---

### Post by abn91c on 2009-01-03
> **ripple.effect said:**
> Ok, I was offered an old desktop PC to do as I wish with. So I've decided to turn it into somewhat of a pet project. I'll be replacing the current windows 98 o/s with Ubuntu. I would like to completely replace the partition making the computer  Ubuntu based only.  However, of course being somewhat/mostly new to the Linux environment, and the fact that I'll be working with outdated software has naturally caused me to run into a few snags.

Here is the old System&#8217;s Properties:
Windows 98 
Second Edition
4.10.2222 A
Intel Pentium II, 266
Custom-Built System
224.0MB RAM

System Resources: 94% free
File System: 32-bit
Virtual Memory: 32-bit
Disk Compression: Not Installed
PC Cards (PCMCIA): Not Installed 

1. There is no internet connection for the old PC whatsoever.
I would like to know if there is a way to perform this installation offline.

2. I do have another newer PC right next to the old PC (with an Internet connection) which I can use to gather necessary software for this project, which is currently being done by burning software to CD-R&#8217;s and transferring it to the old PC.
I do have a 4GB SanDisk removable thumb drive, which unfortunately is not being recognized by the old PC at this time.

I&#8217;m excited to do this project and as much help that might be offered would be very much appreciated.
with that much RAM try xubuntu, you can download the live cd iso's here [http://distrowatch.com/](http://distrowatch.com/)
you can find cheap RAM for older systems here [http://www.geeks.com](http://www.geeks.com)
Just make sure you burn the image as an **ISO** use this program, its a free no limits ISO burner and it takes just two clicks to make a live cd: [http://www.download.com/Active-ISO-Burner/3000-2646_4-10602452.html?tag=rtcol;reldl&cdlPid=10792184](http://www.download.com/Active-ISO-Burner/3000-2646_4-10602452.html?tag=rtcol;reldl&cdlPid=10792184)
when installation starts select"guided use entire disk" option since you getting rid of 98

---

### Post by Kevbert on 2009-01-03
With those system specs you may have a few problems trying to install Ubuntu. Probably the best flavour would be [[COLOR="Red"]Xubuntu[/COLOR]]("http://www.xubuntu.org/"). Even with this the system is likely to run quite slowly due to your memory restrictions.  A better bet would be to try [[COLOR="Red"]Puppy[/COLOR]]("http://www.puppylinux.org/") or [COLOR="Red"][Slax]("http://www.slax.org/")[/COLOR] instead.

---

### Post by ripple.effect on 2009-01-03
I've been looking for the live cd's iso for xUbuntu at distrowatch, allthough i can't seem to understand exactly what i'm looking for. may i possiblt get a little better direction. I did find the link on the left side of the page for xUbuntu, but after that i was somewhat lost.

---

### Post by oldos2er on 2009-01-03
I doubt if any LiveCD would run on such a low spec machine. Try Puppy or DSL.

---

### Post by albinootje on 2009-01-03
> **ripple.effect said:**
> 
Intel Pentium II, 266
Custom-Built System
224.0MB RAM


With a machine like that, Ubuntu and also Xubuntu will be quite slow.
You should play around with light-weight Linux distributions like Puppy Linux, Damn Small Linux.

It's also possible that the cdrom is so slow that Live cdroms are not very usable, so you'll need to do a slow install, and then try the hard disk installation.

[http://crunchbanglinux.org/](http://crunchbanglinux.org/) might be a good choice.

See also here :
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

After installation you can decide to use light-weight applications like mousepad, AbiWord (beware, other people usually cannot read .abw formatted documents).
More lightweight web-browsers like : 
Kazehakase, Midori, Epiphany-browser, Links2 (start with : links -g)

GL! Have fun! :)

---

### Post by ripple.effect on 2009-01-03
Ok, so here's the update. I'm in the process of downloading the xubuntu iso, but in the meantime i did have time to grab that iso burning program. Now originally I had downloaded the ubuntu package with the option of installing either Ubuntu, Kubuntu, Xubuntu or Mythbuntu. So I burnt that using the ISO Burning Program and inserted the disk into the old PC. Now, after selecting the Xubuntu, using Wubi, everything seems to start off fine, only, everything stops at about 1/3 of the set-up process promting me to connect to the internet...which brings me back to my very first problem and question to begin with.

Is there a way to perform this entire installation without having to be connected to the internet. This old PC cannot be connected to the internet right now cause it's still has the old phone line port instead of the DSL port. 

I have also taken the additional advice of installing Damn Small Linux. I'm in the process of downloading that iso right now as well.

---

### Post by ripple.effect on 2009-01-03
Also for the record, I have a feeling that yes, the installation of Xubuntu might be slow, I was told that Ubuntu would work on this system too, I would just have to disable some flashy settings during the installation. I know it's only a 266, but there is a very good chance, i'll be upping it to a 400 in the very near future, which i believe might be the max for this system. As for hard disk space, there's a 28.6GB Capacity 15.2 is being used by god knows what, leaving 13.4GB free.

---

### Post by Kevbert on 2009-01-03
> **ripple.effect said:**
> I've been looking for the live cd's iso for xUbuntu at distrowatch, allthough i can't seem to understand exactly what i'm looking for. may i possiblt get a little better direction. I did find the link on the left side of the page for xUbuntu, but after that i was somewhat lost.

The better version of Xubuntu to go with would be Hardy Heron 8.0.4.1 as it has long term support (unlike 8.10 which will be superseded by 9.04 in April) as well as floppy disk support which looks like it has been dropped (by default). Just select the nearest server to you (eg UK) and then you want the PC (Intel x86) desktop version for your 32 bit PC.

---

### Post by ripple.effect on 2009-01-03
Also for the record, I have a feeling that yes, the installation of Xubuntu might be slow, I was told that Ubuntu would work on this system too, I would just have to disable some flashy settings during the installation. I know it's only a 266, but there is a very good chance, i'll be upping it to a 400 in the very near future, which i believe might be the max for this system. As for hard disk space, there's a 28.6GB Capacity 15.2 is being used by god knows what, leaving 13.4GB free.

---

### Post by ripple.effect on 2009-01-03
Do you have a link where I could find Hardy Heron? Will I be promted to connect to the internet in order to continue that installation. Basically i was wondering earlier if there was a way to collect whatever it was trying to gather from the internet and simply have the material or information ready as it installs over the 98 o/s.

---

### Post by ripple.effect on 2009-01-03
I would also like to know idealy what might be the best insallation size condering the above mentioned specs. After much thought, it looks like i'll be going with the Xubuntu Environment. Please keep in mind that this machine will maxed-up for ram very shortly. It currently sits at 266.

Just so you all know, I do appreciate your help very much. As I had mentioned in the begining, I am quite new to the Linux Environment, but i'm being very patient, I learn extremely fast, and taking everyone's input into consideration throughout this project so as it may have the very best outcome as deemly possible. 

Again, your continued support is very much valued.

---

### Post by ripple.effect on 2009-01-03
What exactly is the installation of Xubuntu requesting a connection to the internet for anyway? Can I gather whatever information for Xubuntu installation off the internet with my regular PC and tranfer it via CD onto the old PC without the internet connection (the old PC with o/s Windows 98 being completely replaced by Xubuntu)?

---

### Post by GerryB on 2009-01-03
Puppy Linux is a very sophisticated OS. Your computer is a perfect match. It doesn't require a connection to the internet. As a matter of fact, you have to establish the connection whether on the live CD or once installed to your hard drive. You can also load Puppy entirely into RAM (266 is excellent), making your CD drive available for other uses if you just want to experiment with the live CD. Also, I have a feeling that if you absolutely want Xubuntu bypassing the internet connection you'll have to go back to 6.06 (code name Dapper). Good luck!

---

### Post by ripple.effect on 2009-01-03
With Puppy, does it have to go overtop of the existing 98os or can i have puppy replace the partiotion all together?

---

### Post by GerryB on 2009-01-03
Just click on "Install" and it will guide you all the way. Try the boot option "Load into RAM" first to get a feel for it.

---

### Post by ripple.effect on 2009-01-03
Alright, I know everything has been a little flip-flop, throughout this thread, but I have made up my mind, after dicussing the topic between others and taking most of the information from all of you here. I'm going to officially start off by installing Dapper Drake on this system. 

So if we recap,

---

### Post by ripple.effect on 2009-01-03
Ok so as I was saying, I'll be installing Xubuntu 6.06 over Windows 98 making it so that Xubuntu will be the only Operating system on the partition.

There is no internet connection for the old PC whatsoever.
I will be transfering the nessasary files by CD's over to the project computer ( the one with Windows 98 ) using this computer.

So starting with xubuntu-6.06-desktop-i386 file which I have downloaded temprarily onto my XP computer, how will I go about burning this to CD so as it might load automatically when i insert it into the old PC. Should I burn it using Active@ ISO Burner?

---

### Post by Kevbert on 2009-01-04
The direct link for Hardy Heron (UK) is on this [COLOR="Red"][page]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04.1/release/")[/COLOR]. Just click on the title PC (Intel x86) desktop CD and save to a file.  Next you need to check the downloaded file is OK with [COLOR="Red"][this]("https://help.ubuntu.com/community/HowToMD5SUM")[/COLOR]. The md5sum (checksums) are [COLOR="Red"][here]("https://help.ubuntu.com/community/UbuntuHashes")[/COLOR]. To burn see [COLOR="Red"][this]("https://help.ubuntu.com/community/BurningIsoHowto")[/COLOR]. These steps should be taken regardless of whether you use 6.06 or 8.04.
If you want to update via files from your computer (with internet connection) you could try [[COLOR="Red"]AptonCd[/COLOR]]("http://aptoncd.sourceforge.net/"). Packages (programs and updates) can be found [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/") for 6.06 and 8.04.

---

### Post by mikjp on 2009-01-05
Try something lighter than Ubuntu or Xubuntu. Slackware or Vector Linux might be lightweight enough...

---

