---
title: "Need Help Installing Laserjet Printer"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by jimalan on 2007-01-10
I've tried to use the Wizard for installing printers, but Ubuntu can't seem to "see" my HP Laserjet 4m Plus printer.  Why won't it detect my printer?  It works and is powered on at boot.    If I can't get it to detect the printer, is there a set of instructions I can follow to get my printer up and running?  I'm willing to use the terminal and type in the code if I have the info for doing it.  Can someone point me in the right direction?  I've been searching the forums for an hour but haven't run into what I need.  (It's all about other kinds of printers and networks and such.)  Thanks for any help you can give.

---

### Post by adewale on 2007-01-10
sorry is it that it doesn't even recognise it as an hardware at all ? cause i have a modem on board even though it can't use it, it still detects it

---

### Post by jimalan on 2007-01-11
Here's what happens:

I go to Administration/Printing and select Add Printer.  The next screen shows that I have a Local printer with the words "Use another printer by specifying a port: hp_no_device_found."  When I click Forward, I get to select my brand (HP) and the kind of printer I have.  Since Laserjet 4m Plus isn't listed, I've tried the following without success:

Laserjet 4000 Series Postscript (recommended)
Laserjet 4M Postscript (recommended) (suggested)
Laserjet 4 Plus v2013.111 Postscript (recommended)

When I'm finished, I get to give it a name and then click OK to be done.  I tell it to print a test page and nothing happens.  The printer says it's got something in the queue and just sits there forever.

Am I doing something wrong?  Do I need another driver?  If so, where do I get it?  Linuxprinting.org says this printer works perfectly.  They don't tell me where to get the driver, though.  HP drivers say they're only for Mac and Windows.  Is there a place on the Internet for Linxu printer drivers?

I feel pretty stupid when I can't do something this easy.  Can somebody point me in the right direction?

---

### Post by adewale on 2007-01-11
sorry am a newbie like you but why don't you download the windows driver and use ndsiwrapper to install it in linux i wish someone could help you out

---

### Post by jimalan on 2007-01-11
Thanks for the tip.  It looks like NdisWrapper is just for wifi cards, not printers, unless I'm missing something.

---

### Post by adewale on 2007-01-11
u're probably right. i'll do some search whatever i gather i'll let u know

---

### Post by OMRebel on 2007-01-11
How are you connecting the printer?  Are you using USB or Parallel?

---

### Post by adewale on 2007-01-11
i think this could help [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)

---

### Post by jimalan on 2007-01-11
It's a parallel printer.  Any clue what's wrong?  I found one post that said to change the BIOS to EPP instead of ECP but that didn't work.  The printer still works in Win XP and not in Ubunut.

---

### Post by HAL98 SE on 2007-04-08
Could be a port thing.

When adding the printer, try changing the port to LPT1 instead of the default, so, when adding the printer, on the first screen of print driver configuration you can specify the printer port, try changing this away from the default - to LPT1 - I have a Laserjet 4000 and had the exact same problem, i checked bios etc... this worked for me.

---

### Post by 11hjpphty76lkjj on 2007-04-09
Please run:
```

lsmod | grep ppdev
```

if ppdev is not loaded run:

```
modprobe ppdev
```

then 

```
sudo /etc/init.d/hplip restart
```

```
sudo /etc/init.d/cupsys restart
```

and finally:

```
sudo hp-setup
```

A

---

