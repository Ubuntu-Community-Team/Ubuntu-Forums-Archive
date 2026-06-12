---
title: "Selecting the chosen OS from the Live USB doesn't load and PC reboots"
date: 2015-08-12
forum: Hardware
---

### Post by TomAmey on 2015-08-12
First time posting, I hope this is in the right place...

So, I created a Live USB of Ubuntu 14.04 (I also tried Mint 17.2, with the same results), and planned to install it on the completely new and blank SSD in my Dell Dimension E520. I insert the USB, choose to boot from the USB and get the choice to boot Ubuntu. After I hit enter, some text appears, then the computer just restarts, beginning the process again. I've tried all the options (compatibility mode etc.) and all of them cause a reboot. 

I know the USBs work as they boot up fine on mine and my dad's laptops, just not this tower. I've tried front and rear USB sockets, removing the graphics card, using integrated graphics, and without any peripherals except the memory stick and a keyboard. The odd thing is is that I've got Ubuntu running fine on the same model of machine, but that tower has since died of a fried motherboard, so I cannot do any tests with it. This is really stumping me!

Specs:

Dell Dimension E520
Intel Core 2 Quad Q6600
6GB RAM (2 x 1GB, 2 x 2GB)
AMD Radeon 6670 Graphics

---

### Post by tgalati4 on 2015-08-13
It's possible that your Tower has also developed a problem with the motherboard or PSU.  Around that time, Dell had capacitor quality issues.  Check the motherboard for leaking or bulging capacitors.  The power supplies were also failing in large numbers.  Perhaps swap the power supply with another computer.

Try 12.04.  If you get the same behavior, then that would be consistent with a hardware problem.

---

### Post by mörgæs on 2015-08-13
Trying another release is a good idea, but I recommend 15.04 and not 12.04. Radeon drivers have improved a lot.

---

### Post by weatherman2 on 2015-08-13
Run Memtest on your Dell - you should get an option for Memtest from the boot menu.  Let Memtest run for at least five minutes.  If you get no failures, the RAM is probably good.

If that's a PCI-E graphics card but you also have an internal graphics card(?), try removing it temporarily.

Try removing the SSD and anything else connected to the motherboard - everything but RAM and keyboard or whatever is required to interact with the computer at all - and try again.

Your problem doesn't sound like a bad power supply or motherboard failure to me.

FYI, you can try installing Ubuntu to your SSD on some other hardware first, then connecting it to the Dell and trying to boot it then.  Maybe the issue is only with the live USB boot.  Ubuntu is pretty good about moving one installation from one computer to another, though you may have issues with the graphics card upon boot.

---

### Post by Bucky Ball on 2015-08-13
I recommend 14.04 LTS as it is a long term support release, but whatever you use ...

Boot from the USB install media, when you get to the purple screen with the icon at the bottom, hit any key. That should take you to 'Try Ubuntu' 'Install Ubuntu' etc. Hit F6 and a pop-up options will appear. Choose 'nomodeset'. Proceed. Any luck?

---

### Post by TomAmey on 2015-08-13
Wow, so many replies! I'm away from home for a couple of days, but will test your suggestions ASAP!

@tgalati4: I can test with another PSU, and with another Ubuntu release, but I'd prefer the LTS if possible.

@Morgaes: Have they? That's reassuring, I had heard that Linux's support of Radeon (and other brands) graphics was a bit sketchy. Good to hear!

@weatherman2: I'll try that. Good to hear that it's not a PSU or mobo problem. And does Linux not tie itself to the mobo like Windows does? Is it as simple as installing it on one pc and sticking the drive in another? That's interesting...

@BuckyBall: I was going to go for the LTS release. I will try your suggestion.



As I said, I'm away for a few days, but will try all of your suggestions and report back ASAP on Sunday. Thanks!

---

### Post by weatherman2 on 2015-08-13
> **TomAmey said:**
> 
@weatherman2: I'll try that. Good to hear that it's not a PSU or mobo problem. And does Linux not tie itself to the mobo like Windows does? Is it as simple as installing it on one pc and sticking the drive in another? That's interesting...

I said it doesn't SOUND like a PSU or motherboard problem.  It is still a possibility, though, just sounds unlikely to me.

No, Ubuntu/Linux doesn't "tie itself to the mobo."  It is often very easy to move an installation to completely new hardware without changing a thing. I do it all the time.  I have one "work drive" I have booted in probably ten different machines now - a SATA drive that is sometimes connected internally, sometimes via USB.  Occasionally you have issues with a graphics card driver or some other driver issue, though I never have myself.

There is one little issue moving a server edition build of Ubuntu to new hardware: the network connection device name will change with each new network device detected.  So if you install on one motherboard and your ethernet card is identified as eth0, then move to another, it will be called eth1.  (If you move back to the old motherboard, it will detect it as eth0 again.)  But a server build typically tries to connect to a network before it finishes booting, and it may look for a connection on eth0 even though you have moved to new hardware and now the network card is on eth1.

The solution to this is simple, though:  tell Ubuntu to forget the name of the network card, so that it will assign eth0 to the new hardware upon reboot.  All you have to do is erase the file "/etc/udev/rules.d/70-persistent-net.rules" and reboot - and it will be re-created for the new hardware. If you are doing a desktop build (not server edition) of Ubuntu, you won't have this problem, but it will still assign eth1, eth2, etc. to each new network device, and you can still delete the rules file if you prefer to reset it back to eth0.

---

### Post by tgalati4 on 2015-08-13
The reason for using 12.04 (an older LTS version) is that was around when the Quad-Core processor was popular.  Newer kernels have support for newer processors and motherboard architectures, but that may lead to regressions with older hardware.  You want to make sure your machine can boot into something.  If it can't boot with 15.04 then is it because of the later kernel or a hardware issue?  You won't know.  If you can boot with 12.04 but not 14.04 then that points to a kernel or configuration issue--and we know that you can't boot with 14.04.

---

### Post by TomAmey on 2015-08-14
@weatherman2: Yeah sorry, I meant to type 'Glad to hear it's *probably* not a PSU or mobo problem' .I understand that it still could be. That's interesting about the drives though, you could just take a single drive aand pop it into whichever computer you use, therefore completely negating the need for memory sticks to take around or cloud storage. If all else fails, I'll just install Ubuntu onto the drive from another PC.

@tgalati4: That definitely makes some sense, if an older release works, at least I can install SOME version of Ubuntu. If I did install 12.04, would updating to 14.04 cause the same sorts of problems?

---

### Post by mörgæs on 2015-08-15
Don't upgrade. Regardless of which version you pick install the one you want and use it as long as it's supported. 
After that a new install.

---

### Post by TomAmey on 2015-08-15
> **mörgæs said:**
> Don't upgrade. Regardless of which version you pick install the one you want and use it as long as it's supported. 
After that a new install.You're right, I've done an upgrade before and it breaks more than it updates!

---

### Post by TomAmey on 2015-08-15
Right, I'm back. I installed Ubuntu to the ssd, booted, get the grub menu, select Ubuntu 14.04, then it reboots. It seems Linux is the problem since I tried it without the graphics card and also with Mint 17.2, getting the same results. I'm going to try both 12.04 and 15.04 tomorrow.

---

### Post by weatherman2 on 2015-08-15
Did you run Memtest like I suggested?

Did you try removing all other hardware (e.g. graphics card) that you could possibly remove temporarily and try booting again?  Unplug any USB drives, etc. that don't need to be there.

---

### Post by TomAmey on 2015-08-16
Yes, I still got the same results. I'm downloading 12.04 now.

---

### Post by mörgæs on 2015-08-16
Please note that 12.04 is but a collection of bugs. You could be lucky that it works but chances are bigger in the later releases.

Security bugs found in 12.04 are fixed here but non-security bugs found in 12.04 are fixed in the development release. They may or may not (most often not) be backported to an old release.

*If* they are backported at all then 14.04 receives more attention than 12.04.

---

### Post by TomAmey on 2015-08-16
> **mörgæs said:**
> Please note that 12.04 is but a collection of bugs. You could be lucky that it works but chances are bigger in the later releases.

Security bugs found in 12.04 are fixed here but non-security bugs found in 12.04 are fixed in the development release. They may or may not (most often not) be backported to an old release.

*If* they are backported at all then 14.04 receives more attention than 12.04.Well it *did* work, the i386 (32bit) worked, but the amd64 (64bit) didn't, however I'm going to try 14.04. I know for a fact the processor works with 64bit, but I guess 32bit with PAE is OK, better than 64bit not working. One problem though, I do get random restarts every so often, is this a PSU problem, or the processor pulling too much for thee 305W PSU?

---

### Post by Bucky Ball on 2015-08-16
Is the PSU a generic <70% efficient silver box? If so, possibly the PSU. :)

This is off-topic, so probably better posting a new thread, but if you have half a dozen hard drives, a grunting graphics card, and an i7 hanging off 307W you might be struggling, yes.

---

### Post by TomAmey on 2015-08-16
> **Bucky Ball said:**
> Is the PSU a generic <70% efficient silver box? If so, possibly the PSU. :)

This is off-topic, so probably better posting a new thread, but if you have half a dozen hard drives, a grunting graphics card, and an i7 hanging off 307W you might be struggling, yes. Swapped it out for a spare, and everything seems to be running fine (apart from my USB Wi-Fi dongle, but that won't work under Linux anyway). Thanks for the help, this is a great site, I'll be back! ;)

---

### Post by astralnysledz on 2015-08-16
Though I did not help with resolving your issue, I'm still happy it worked! :)

If you're interested in sorting out your Wi-Fi dongle issue, feel free to start a new thread on that. I might be able to make some reasonable suggestions.

Also, once you're sure that your rebooting problems are over, please mark thread as solved.

---

### Post by TomAmey on 2015-08-17
> **astralnysledz said:**
> Though I did not help with resolving your issue, I'm still happy it worked! :)

If you're interested in sorting out your Wi-Fi dongle issue, feel free to start a new thread on that. I might be able to make some reasonable suggestions.

Also, once you're sure that your rebooting problems are over, please mark thread as solved. Ok, the dongle isn't natively supported, but I do have a disk with drivers, I'm not sure how to use. I'll start a new thread.

---

### Post by Bucky Ball on 2015-08-17
In the new thread in ***Network and Wireless***, include the info from:

```
sudo lshw -C network
```

... to start with or use the wireless script in my signature. Good luck.

---

### Post by TomAmey on 2015-08-17
I just thought I should say, it wasn't a faulty PSU that caused the reboots, it was a dodgy RAM module, memtest didn't seem to report any errors though...

---

### Post by Bucky Ball on 2015-08-17
Ah, ha. ;)

---

