---
title: "I give up: Which dial-up modems WILL work for Hardy 8.04 (64bit)?"
date: 2008-05-02
forum: Hardware
---

### Post by Drakelet on 2008-05-02
I've tried for hours to get my Hardy online.  Nothing.  Asked everywhere, still nothing.

So I give up.  I'm willing to buy a whole new modem so Hardy will work online.

For anyone here on Hardy 64bit with a dial-up internet connection through a modem:
**Which modems will work?**

I suppose if I had to I could go to 32bit, if that will help.  Ideally one that would work with both.

PLEASE!  I'm getting desperate now...

EDIT: Before you say, yes I have looked.  But I want to make sure it works with Hardy 8.04 64bit.  I don't want to buy another which won't work.  Websites like linmodems name loads, but finding one that will definitely work on my desire setup is hard.

---

### Post by Drakelet on 2008-05-03
I hate bumping my threads, but I just want my Hardy working. :(

---

### Post by CREEPING DEATH on 2008-05-03
Too bad you're in the UK, if you were in the US I'd tell you to buy one at Wal-Mart.  Many winmodems will work on Linux, just look on the box.  32-bit might be a better bet though.

CD

---

### Post by cjazz on 2008-05-03
Have you tried this?

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

---

### Post by starcannon on 2008-05-03
Look for an old Zoltrix Rainbow 56k or any old hardware modem.

Linmodems can be a pain for 32bit as well, I'd just go hunt and find a hardware modem, they aren't rare and a search on ebay will likely net you one in a matter of minutes.

Just my 2 cents, good luck and sorry your having modem issues, they can be a real pita.

---

### Post by Drakelet on 2008-05-03
I have an Intel 536EP, but I can't get it working whatever I do.  I've looked through all the websites, all the guides etc, but nothing seems to get it working.  See my other thread on the modem issues.

Does anyone currently have Hardy on modem?  If so, which modem?  If it works, I'll buy it (well, one like it).

EDIT:
If anyone can help, here is my scanModem results:
[http://jgibbins92.googlepages.com/Modem.zip](http://jgibbins92.googlepages.com/Modem.zip)[]("http://jgibbins92.googlepages.com/Modem.zip")
A quote:
> USB modems not recognized
For candidate card in slot 05:00.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 05:00.0    8086:1040    8086:1000    Communication controller: Intel Corporation 536EP Data Fax Modem
And here are my old threads:
[http://ubuntuforums.org/showthread.php?t=777031](http://ubuntuforums.org/showthread.php?t=777031)
[http://ubuntuforums.org/showthread.php?t=774611](http://ubuntuforums.org/showthread.php?t=774611)

I have actually just found a new, updated driver.  Hopefully that will work.  Wish me luck!!!

EDIT2:

Didn't work.  Tried the 2008 driver from here:
[http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/](http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/)
When I did "make 536", it came up with a load of text, then said "Failed to build driver".
This is a screenshot from my previous driver attempt, but I'm pretty sure it's identical, or very similar:
[IMG]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/make536fail1small.gif[/IMG]

I think some of the problems may be to do with as-yet not installed kernel files or whatever.  But I don't know how to install them.

Actually, it would probably be best to keep it to my other thread.
[http://ubuntuforums.org/showthread.php?t=774611](http://ubuntuforums.org/showthread.php?t=774611)

Please help!

EDIT3:
Did some searching on XMODEM.
According to my Hardware ID from Windows Device Manager, it is an E-Tech PCI56AVP
[http://www.e-tech.nu/producten/faxmodems_pci56avp.htm](http://www.e-tech.nu/producten/faxmodems_pci56avp.htm)
An Intel 536EP (as I said)
[http://xmodem.org/chipsets/intel/intel_536ep.html](http://xmodem.org/chipsets/intel/intel_536ep.html)

Don't know if that helps.

---

### Post by Sepero on 2008-07-17
Ever get the 536EP working?

[http://ubuntuforums.org/showthread.php?p=2827908](http://ubuntuforums.org/showthread.php?p=2827908)

---

### Post by Drakelet on 2008-07-17
Ha I wish.  I bought an external serial modem which someone on this forum has, and I STILL can't get it working.  I think it may be the number from my ISP as wvdial says "invalid dial command", and in wvdial.conf I've tried everything in the "dial command =" part (ATDT etc).  And the only other part of the dial command is the phone number.  I've emailed my ISP, but might telephone them soon.

Thanks though. :)

---

### Post by Sepero on 2008-07-17
Unfortunately, I wouldn't give it any hope. If you can't get it working with a hardware modem, the fault has to be with your service provider.

Sounds like you're kinda locked in there with no other choice of provider. You might want to consider just running Ubuntu from inside Windows through some kind of VirtualMachine, like VMware or Qemu.

---

### Post by Drakelet on 2008-07-18
Emailed my ISP and they said they don't support Linux.  Don't know if that means don't supply support for Linux, or the service doesn't work for Linux.  Might still try phoning them, but probably won't work.

Looks like I'll just have to wait until I get broadband (once it comes to where I live, or I move).  Aww.

---

### Post by Henry04 on 2008-07-18
> **Drakelet said:**
> Emailed my ISP and they said they don't support Linux.  Don't know if that means don't supply support for Linux, or the service doesn't work for Linux.  Might still try phoning them, but probably won't work.

Looks like I'll just have to wait until I get broadband (once it comes to where I live, or I move).  Aww.

This is the closest I can find here on this forum, to my question/s regarding installing ubuntu on my system: _*Is there some way to pre-install (i.e., via the live CD) test a modem (& printer), etc. for ubuntu *_(Hardy, though I assume that my system will be 32 bit?)? Or do I just have to install (dual boot, for now, is the plan), & hope for the best?

I have on the motherboard, a Mobile AMD Athlon(tm) 64 XP-M Processor chip; an Agere Systems PCI-SV92PP Soft Modem; & an Apple 360 LaserWriter Select is my present printer. I'm currently running XP sp2 home edition as OS.

& is *not* supporting linux by ISPs, as the quote above indicates, a very common problem? & why is this a problem at all?

Thanks for any help here. If there is another more relevant discussion area for these questions, some direction to go will also be appreciated.

---

### Post by wpshooter on 2008-07-18
> **Drakelet said:**
> Emailed my ISP and they said they don't support Linux.  Don't know if that means don't supply support for Linux, or the service doesn't work for Linux.  Might still try phoning them, but probably won't work.

Looks like I'll just have to wait until I get broadband (once it comes to where I live, or I move).  Aww.

Drakelet:

In case you have not already found this out, the problem you are having is probably NOT related to the type and/or brand of modem that you are using but instead a BUG in the 8.04.1 version of Ubuntu.

I found this out the hard way myself just recently when trying to get a computer cofigured for my sister's use on a dialup basis.

More than likely if you will drop back to Gutsy (until they get the bug fixed in Hardy) instead of Hardy, you will find that the dialup will work fine.  That is what I had to do.  But having said that, in case you are not aware of this, the problem that you are having in Hardy is NOT that you are not connecting to the ISP but that there is a bug in either Firefox 3.0 and/or the Network Manager program that is precluding you from browsing the net even though you ARE actually connected to your ISP.

On the matter of modem choices.  I initially thought that all these problems that I was having with getting connected to the dialup connection was related somehow to either a bad internal PCI modem that I was trying to use or the fact that I was not sure if I had the correct driver for that modem.  I then went out and purchased an external serial port modem because everyone on the forums was saying how that MOST all serial modems would work with Linux with no problems.  In my case that did NOT turn out to be true.  I could get the serial modem to connect to the ISP just fine but the connection would last only a few minutes before being dropped.  Yes, I had the idle timing set to disable.  This problem could have just been that there was a defect in the serial modem that I purchased.  I am sending it back for refund.  But then after I found out about the BUG in Hardy, I went back to the original internal PCI modem that I had attempted to use and when I switched the O/S to Gutsy instead of Hardy, bingo, it worked to perfection.

So, assuming you can find and install a Linux compatible driver for your modem and you use Gutsy, I think you will be fine.  Then just wait and hope that they fix the mess that they have in Hardy someday.

Good luck.

---

### Post by Drakelet on 2008-07-18
> **wpshooter said:**
> Drakelet:

In case you have not already found this out, the problem you are having is probably NOT related to the type and/or brand of modem that you are using but instead a BUG in the 8.04.1 version of Ubuntu.

I found this out the hard way myself just recently when trying to get a computer cofigured for my sister's use on a dialup basis.

More than likely if you will drop back to Gutsy (until they get the bug fixed in Hardy) instead of Hardy, you will find that the dialup will work fine.  That is what I had to do.  But having said that, in case you are not aware of this, the problem that you are having in Hardy is NOT that you are not connecting to the ISP but that there is a bug in either Firefox 3.0 and/or the Network Manager program that is precluding you from browsing the net even though you ARE actually connected to your ISP.

On the matter of modem choices.  I initially thought that all these problems that I was having with getting connected to the dialup connection was related somehow to either a bad internal PCI modem that I was trying to use or the fact that I was not sure if I had the correct driver for that modem.  I then went out and purchased an external serial port modem because everyone on the forums was saying how that MOST all serial modems would work with Linux with no problems.  In my case that did NOT turn out to be true.  I could get the serial modem to connect to the ISP just fine but the connection would last only a few minutes before being dropped.  Yes, I had the idle timing set to disable.  This problem could have just been that there was a defect in the serial modem that I purchased.  I am sending it back for refund.  But then after I found out about the BUG in Hardy, I went back to the original internal PCI modem that I had attempted to use and when I switched the O/S to Gutsy instead of Hardy, bingo, it worked to perfection.

So, assuming you can find and install a Linux compatible driver for your modem and you use Gutsy, I think you will be fine.  Then just wait and hope that they fix the mess that they have in Hardy someday.

Good luck.
Wait, WHAT!?  This isn't a modem/ISP problem!?

This is getting more and more complex! :D

I might try Gutsy then, or I may just stick to Windows for now.  Thanks for the info though!!

---

