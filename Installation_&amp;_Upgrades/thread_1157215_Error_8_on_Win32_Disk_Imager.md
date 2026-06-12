---
title: "Error 8 on Win32 Disk Imager"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by fiadys on 2009-05-12
Hi, I'm using:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

So, I've downloaded the image file for the 9.04 netbook edition and I am trying to put onto my 2GB pen/flash drive.
I select the image file, select E:/ as my Device (I have checked - it is right) and select Write.
A message box pops up saying that my physical device can become corrupted and I click OK.
I click Yes and then a message box comes up saying:
"An error occurred when attempting to get a handle on the device.
Error 8:"
How can I fix this so I can install Ubuntu on my Acer?

---

### Post by colinator on 2009-05-22
Hi, I have the same problem, I Fixed it to download Version 1 of the Win32 Disk Imager.
 
You can download it from the LINK Ubuntu has given on their page for installing the IMG file.
 
so select Win32diskimager Release 0.1 instead of 0.2
 
Hope this helps ^^

---

### Post by jaf777 on 2009-07-01
Well neither version works for me.  

Fantastic.  I have a netbook (MSI Wind), and if I desire the actual "Netbook Remix" I seem to be tied to the *.img file, as there seems to be (?) no *.iso of the UNR release.

So there is a nice, slick page about getting UNR for your netbook (linked on the home page), but this is completely dependent upon "win32 disk imager"?  Which is broken?  

Broken for many people.  A bug was filed for the "error 8" on June 10th but its "Importance" rating remains "Undecided".

Fantastic.

Is there any other software I can use to write the *.img file?
Is there an *.iso of UNR anywhere?

I currently only have a netbook with xp; pc is dead.

Thanks for any help.

---

### Post by jaf777 on 2009-07-01
Well I found the *.iso here (NOT linked on the UNR download page):

[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/)

and I'll try using UNetbootin to get it on my USB drive...

---

### Post by jaf777 on 2009-07-02
OK instead I tried with "flashnul", a win32 command-line utility, which wrote the *.img to my usb flash drive.  Instructions from the wiki are as follows: 
> From Windows Command Prompt using flashnul
Download the image to your disk.
Download flashnul from [http://shounen.ru/soft/flashnul/](http://shounen.ru/soft/flashnul/)
At the command prompt run:
flashnul -p 
Note the drive letter for the target USB disk.
At the command prompt run:
flashnul <letter obtained in prior step>: -L \path\to\unr-<version>.img
Answer "yes" after verifying the destination device.
Booting from such a USB key will let you install Ubuntu Netbook Remix on your device.

I really have to reiterate that it's ridiculous to provide such a prominent page promoting Netbook Remix while the only obvious win32 instructions point to a BROKEN utility.  LOTS of people are having this problem.  I'm not the only one out there w/ only a winxp netbook who needs such a utility.  I had to dig to find a (relatively obscure) solution.

Ridiculous.

Update: flashnul did not work.  It wrote the *.img but apparently did not make it bootable/install a bootloader (?)

Trying UNetbootin and UNR *.iso

---

### Post by gentlegear on 2009-07-09
Hello?
There is a simple and nice solution.
JUST COPY THE FILE DOWNLOADED TO C DRIVER (I.E., YOUR MAIN LOCAL DRIVER).
RENAME THE FILE, "UBUNTO.iso"
Try again.
I did and it' was done.

---

### Post by M&amp;C on 2009-07-15
It can be easily solved, I met with the same problem today,just make sure there is no non-English words in the path of your img file.Then write it again,hope it will help:)

---

### Post by bandofmercy on 2009-07-20
renaming the file worked for me!  don't know if it was the length of the name or what, but... well, since one post said it had to be an english word (why?  perhaps english characters only?) i chose... "windows."

---

### Post by raymondh on 2009-07-20
Another option is to install standard Ubuntu 9.04....update 9.04....then use the terminal to install ubunut-netbook-remix ...then reconfigure your panel for the UNR feel and look. This may be a longer route but still possible ;)  Of course, you still have to make a liveUSB if you don't have an external CD drive.

See the [link ]("http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html")for the dell mini 9.  It may be for a dell but the process is still the same as you are still using the same repos of Jaunty ... of which UNR is included.

Good luck.

---

### Post by Nightmate on 2009-08-08
Check you have admin rights when running the prog. In Windows right click & run as administrator. USe Sudo in Ubuntu.

---

### Post by nielschrist on 2009-08-09
I had the same problem. The reason seem to be very simple. Explorer was showing the contents of the usb drive. As soon as I closed the eplorer of my usb drive, I was able to get Win32 writing the image to the usb.

probably a silly situation, but it was the one in my case.

---

### Post by _Vicki_ on 2009-08-13
I had the same issue and finally decided to reformat the SD card, at which point I realised I hadn't formatted to FAT32.

---

### Post by mhooimeijer on 2009-12-14
Hi there. I had the same problem so I looked on the webpage of the win32 Imager. In the answers section I read the USB drive needs to be formatted before using Win32 imager.

I followed the instructions and then it worked for me (using version 0.1. Did not try out 0.2).

[https://answers.launchpad.net/win32-image-writer/+question/72126](https://answers.launchpad.net/win32-image-writer/+question/72126)

Regards,

Martijn

---

### Post by Daniil_xXx on 2010-02-24
Hi everyone!

As someone already mentioned before the **problem** with "**Error:8**" can be **solved** if you rename your *.iso using a DOS standard naming conventions - 8 char, uppercase.

What I also discovered that this is not enough, the path to the *.iso should be also in accordance to the DOS standards, so no space or folder names longer then 8 char.

I just put renamed file to UBUNTU.iso and have put it to the root on my disk.

After all of this steps I was **able to use Win32 Disk Imager** **0.2** :D

---

### Post by nitrooreo on 2010-04-10
For me the problem was caused by my user not having administrator privileges. Running diskimager as administrator solved the problem.

---

### Post by Paul Gibbons on 2011-08-13
> **M&C said:**
> It can be easily solved, I met with the same problem today,just make sure there is no non-English words in the path of your img file.Then write it again,hope it will help:)

I had the same error message when trying to write at image from a shared folder on vmware. The problem was due to the space character in the path to the img file: \\vmware-host\Shared Folders\scratch\iii.img. I had yo copy the file to the local c:\ drive so that I could refer to a path without the space character.

---

