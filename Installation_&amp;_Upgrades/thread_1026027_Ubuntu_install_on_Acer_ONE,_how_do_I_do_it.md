---
title: "Ubuntu install on Acer ONE, how do I do it?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2008-12-30
I have an Acer One model AOA 150-1249, which came with Limpus Lite OS.  The hardware on the Acer One is a 120 GiB HD and 512 MB of RAM.  I have another 512 MB to install after I get Ubuntu installed.

I have tried to use a Kingston 2GB DataTraveler flash drive, a recently made CD-rom with the latest Ubuntu 8.10 ISO file.  I also prepared the flash drive by using the System>Administration>Create a USB Startup Disk.

The Acer One, when F12 is pressed during startup recognizes the Kingston flash drive, but the Acer One then says there is not a bootable OS on the flash drive, then it boots to the Limpus OS.

OK, what am I doing incorrect?  Maybe someone can provide some help on this.

I use U8.10 on both my desktop and laptop and whould like it on my netbook also.  Especially since I have a hard drive on the Acer One instead of the SSD that is usually on an Acer One.

---

### Post by AlbertoDAU on 2009-01-09
This may help with the installation:
help.ubuntu.com/community/AspireOne
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

it contains a link to the bootable USB creation at:
help.ubuntu.com/community/Installation/FromUSBStick
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

i havent tried it... you also can look at
[http://sourceforge.net/projects/unetbootin/]("http://sourceforge.net/projects/unetbootin/")

im not sure AOA 150-1249 is the model... may be some kind of model code, for this look in here:
[http://en.wikipedia.org/wiki/Aspire_One#Specifications]("http://en.wikipedia.org/wiki/Aspire_One#Specifications")

hope it helps

---

### Post by jlh68 on 2009-01-10
I was finally sucessful in makeing a working USB Flash drive that boots.  I found one site a description that mentioned something about making UNetbootin executable, and I right clicked on UNetbootin and found the check box to do that.  Then I as able to get the UNetbootin GUI on screen. From there it was a "a piece of cake" to complete the process.

I have noticed that a lot of these How-to sites often will not mention one small detail that keeps the reader from having success.  I must have looked at 12+ different web pages on how to make a bootable USB drive, trying each one without success then only _one_ provided enough info to get the job done.

** AlbertoDAU**  Thanks for posting pack it is people like you that make the Linux community great.

---

