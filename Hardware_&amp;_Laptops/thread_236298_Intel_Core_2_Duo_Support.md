---
title: "Intel Core 2 Duo Support"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by CodeMonkeyX on 2006-08-14
I have been looking around the web about current Linux support for the Core 2 Duo motherboards out there. And it seems that the new motherboards based on the P965 chipsets, and the new Intel south bridge are only supported in the very latest 2.6 linux kernel, and most distros will not work.

This puts me off the Intel chipsets a bit, because even when support comes around it will probably not be mature for several more months.

So my question is, when the new Nvidia NForce 570 and 590 boards come out for Core 2 will they be just as well supported in Linux as the current AMD motherboards? I am hoping that the Nvidia NForce boards will be pretty much identical to the current AMD boards, and will provided much more mature support for Linux.

Or am I mistaken about the P965, and will it be well supported very quickly?

---

### Post by John.Michael.Kane on 2006-08-14
CodeMonkeyX most of the hardware on the boards should be supported with exception of some of the raid controller chips. this where you need to research. when looking at the boards themselves find out the model of the raid controller,and start with your build from there.

---

### Post by KlausU on 2006-08-14
Be careful with the motherboard you chose! The Intel P965 chipset has no more integrated IDE channel, thus the motherboard usually has an additional chip onboard for an IDE channel. In the current Gigabyte (I got one of them) and ASUS (think they have it too) this is a JMicron JMB363. Until very recently the kernel had a bug inside that made it unable to access the IDE/PATA channel ([http://www.uwsg.iu.edu/hypermail/linux/kernel/0607.1/1730.html)](http://www.uwsg.iu.edu/hypermail/linux/kernel/0607.1/1730.html)). So If you have and IDE drive or HDD left you will not be able to use it until your distro has a late kernel inside. Probably 6.10 will have.
The last days I have fought this problem here and it really sucks :/

---

### Post by KlausU on 2006-08-14
Oh and see [http://ubuntuforums.org/showthread.php?t=233540](http://ubuntuforums.org/showthread.php?t=233540)

---

### Post by CodeMonkeyX on 2006-08-14
Thanks for the replies.

Yah that was what I was hearing, the post I was reading on another forum was saying they had to compile a bleeding edge kernel to get the PATA to work on the Gigabyte P965 board.

Then I read a review of an ABit NForce 570 board that said it had great support in Linux, and works great. I just want the NForce 570 board with a Core 2. :) Hopefully by September that will be an option.

Or maybe by then 6.10 will be out and I can run a P965 board just fine. ;)

BTW on a side note how are you liking you Core 2 system in Windows?

---

### Post by KlausU on 2006-08-15
> **CodeMonkeyX said:**
> BTW on a side note how are you liking you Core 2 system in Windows?

Just fine, no Problems (Except maybe installation on a raid... but thats general issue).

---

### Post by SFAOK on 2006-09-02
I've just placed an order for a Core 2 Duo and an Asus P5B motherboard and am now thinking I should've done some research before clicking "buy" :(

I have 2 IDE drives and I dual boot (an up to date) Dapper with Windows. I figured I'd have to reinstall Windows which would overwrite Grub; as I wasn't sure if reinstallation of Ubuntu was necessary after significant hardware changes, I figured I'd might give it a go rather than rescue the existing install. Now I'm thinking I might see how Ubuntu copes with motherboard and cpu (err and graphics card) replacement!

Does any one have any advice on what I should do and what my options are? It's not too late for me to cancel the order... I'm not big on hacking and tinkering with stuff, most of the things described in this thread and the other thread posted by Klaus are beyond me I think and I'd prefer not to have a crash course in fixing Linux as I'm supposed to be looking for work atm ;)

Feedback is most appreciated,
SFA

---

### Post by John.Michael.Kane on 2006-09-02
SFAOK right now i think the only issue you will have is with this chip **JMB363** this jmicron seems to be the one giving some users a rough time.

There was talk that it maybe supported in the next release,however i'm not sure of that.


Note: Update on their web site for this chip they say Ubuntu support with Linux kernel 2.6.16 or above. so you may be ok with the release of edgy.

---

### Post by amonsul on 2006-09-02
Change the order, take Sata-Harddrives and Sata-Dvd-player and all will work fine. The Problem is only the IDE-connection.

---

### Post by CodeMonkeyX on 2006-09-02
Has anyone with this Motherboard tried installing Edgy Knot 2? It would be nice to know if the pre-release of Edgy worked on this mobo.

The first NForce5 for Core 2 is out, but it not running as fast as the P965 boards, and does not seem to overclock as well. So I would rather have a P965 if possible.

---

### Post by fireboxtester on 2006-09-02
I made a wiki page to put all of the information about this issue in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

### Post by lazerradial2003 on 2006-09-11
Anyone know if this has been resolved yet? Just about to buy something with the 965 chipset and really dont want to have to go back to windows.

---

### Post by KlausU on 2006-09-11
> **lazerradial2003 said:**
> Anyone know if this has been resolved yet? Just about to buy something with the 965 chipset and really dont want to have to go back to windows.

The Problem is not the 965 but the JMB363.
I am running Ubuntu fine here on an 965 with Core 2 duo. I just do not have access to my CD Drive (didn't miss that much) and I have been getting new SATA HDDs anyway.

I managed install Ubuntu with Windows / GRUB / Netinstall that was well documented in some wiki/howto post here.

If you buy new hardware and its sata only there is no Problem.

---

### Post by ykpaiha on 2006-09-11
sad sad sadness justn bought a brand new e6300 + p5b and noway to install a linux !!!!
no edgy, no drake, nothing ....
really desapointed and.:confused: :confused: :confused: :confused:

---

### Post by lazerradial2003 on 2006-09-12
Worth having a look at the wiki mentioned earlier, explains some work arounds like installing from a USB key, you can also get adaptors to let you plug IDE devices into the SATA ports, can't tell you how well this works because i only got mine off ebay (£7) yesterday so it hasnt arrived yet.

---

### Post by CodeMonkeyX on 2006-09-13
I recently saw that a fix has been commited to the Edgy Eft development version. So hopefully Edgy Knot 3, or 6.10 which ever comes first should work.

---

### Post by tall-male on 2006-09-14
Well, it's quite sad if you just bought a 965 motherboard, but it's not the end of the world.

- Spend a couple of bucks buying an extra IDE-controler.
- Search forums how to install Linux without CD-rom, therwe's plenty of solutions. As far as I know Ubuntu doesn't supply out of the box networkinstall using 2 boot diskettes but probably someone did. In the past I installed Debian on a computer without CD-rom many times just using 2 diskettes and an internet connection.
- There is another option as well. Using another Linux box you can transfer the CD-image (using dd) to an USB stick. You can boot and start the install from the USB stick.
- Even if your computer doesn't support USB boot this is still an option. You can create a Grub boot diskette which configured to boot from the USB-stick.

However: after installing you still won't have a CD-rom but at least you have a running system. You might try to share a CD-rom on another computer. Is there a new kernel available solving this problem? ([www.kernel.org](www.kernel.org)) Manually compile the new kernel. Compiling a whole new kernel ('make -j3 all') doesn't take much time using a Core 2 duo:p 

Unfortunately, I don't have URL's for these howto's right now (I'm at work....) but I might give them later on this forum.

---

### Post by tall-male on 2006-09-14
Last week I got my Core 2 Duo using Asus P5W DH Deluxe.

Well, the motherboard worked out of the box! Jut be shure not to attach any drive to the Jmicron controllers. Even the Marvell 1GB interface (causing problems in the past) works perfectly. (Don't know about performce of the 1 GB LAN, I only use 100 Mbit 8-[

It save me some problems with the 965 chipset. There's one disadvantage: the P5W DH is quite expensive..... :?

---

