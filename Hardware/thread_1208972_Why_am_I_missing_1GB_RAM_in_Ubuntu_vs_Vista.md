---
title: "Why am I missing 1GB RAM in Ubuntu vs Vista?"
date: 2009-07-09
forum: Hardware
---

### Post by cknight on 2009-07-09
I've got a 2 month old Dell Studio 17, and just noticed that the System Monitor reports 2.9 GiB of Memory.  I ordered 4GB and this is what shows in Vista.  Why does Ubuntu use 1GB less and where is my missing GB of RAM?

---

### Post by Kalderama on 2009-07-10
Hello!

I guess that you have running Ubuntu 32 bit version, right?
The 32bit address scheme is not sufficient to address 4GB. You can check wether this is your problem simply by trying a 64bit live CD session!

HTH!

---

### Post by ad_267 on 2009-07-10
You probably have 64 bit Vista but only 32 bit Ubuntu. Download the 64 bit version from [here]("http://www.ubuntu.com/GetUbuntu/download") by selecting where it says:
>  64bit version: May provide additional capabilities to computers that are able to use 64bit software

---

### Post by cknight on 2009-07-10
> **Kalderama said:**
> Hello!

I guess that you have running Ubuntu 32 bit version, right?
The 32bit address scheme is not sufficient to address 4GB. You can check wether this is your problem simply by trying a 64bit live CD session!

HTH!

Thanks to you both.  Yes, I am using 32 bit version of Ubuntu.  As it turns out I'm using 32 bit version of Vista too.  A bit more digging (and a bit more sense) and I realized that Vista's 4GB was simply what it found installed on my machine.  Looking at the task manager, it showed approximately 3GB total memory, or roughly what Ubuntu was showing.

Out of curiosity, is this a hard limit?  E.g. there's no way for a 32 bit operating system to take advantage of that 4th GB?  If so, shame on computer manufacturers for selling me (and countless others) a useless GB of RAM (without upgrading the operating system).

---

### Post by Elliot44 on 2009-07-11
All of your memory is never available to the operating system, because the hardware reserves a chunck or chuncks for itself. How much memory depends on many things - video (built-in and/or add-in), motherboard, bios and other add-in cards and devices, etc. 

I've been running XP for seven years now. All of that time it ran on of two old machines - one with 384MB or memory and the other with 256MB. Once in a blue moon I got a message that I was running low on resources. (Linux used to run fine on these machines - but the newer distros won't or won't be very pretty.)

I still running the exact two copies of XP (never reinstalled, just cloned the hard drives) on my two new modern 4GB fast and overclocked Intel machines. The nice ubuntu people sent me a disk in the mail and after trying it out, I was hooked. I still need to dual-boot because of a large collection of software going back to '88 that I sometimes use, and my DVD copying software.  

As for memory I find 4GB way more than I need. Both XP and ubuntu see about 3.5GB available. Systems checks show all 4GB working fine. I've never seen XP use more than 1GB in actual use. 

**Running a 32 bit operating system (as least with Windows XP) you CAN make use of over 4GB of memory** by using certain "ram or virtual" disk programs that act like a superfast solid state drive. I have not checked for a Linux like program as I'm just re-entering the water and really these programs are no longer needed - in my opinion. 

Elliot

---

### Post by cb951303 on 2009-07-11
there are ways to use 4GB ram in 32 bit linux, such as using the server kernel

---

