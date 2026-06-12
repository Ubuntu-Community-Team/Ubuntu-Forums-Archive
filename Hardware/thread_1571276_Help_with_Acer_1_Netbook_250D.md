---
title: "Help with Acer 1 Netbook 250D"
date: 2010-09-09
forum: Hardware
---

### Post by Mister Fowler on 2010-09-09
Hello. I have recently purchased an Acer One D250 netbook. It had Windows 7 starter on it, which I did not want. Being new to Ubuntu and Linux, I am gung-ho to learn. Problem is, Ubuntu, neither version (desktop or netbook) installs on it and runs after shut down.

Here's the history:

I made a USB start up '****' with the 10.04 version. While the netbook booted from the USB and seemed to install everything nice, even after the restart, once a full shut down happened and I powered it up later, all I got was a blinking cursor after the BIOS screen.

Frustrated, I re-installed, updated, enabled restricted drivers and...same thing. After a cold shut down and turn on, nothing, just a blinking cursor. 

So I went for the netbook version. Made the USB start up stick, installed and things seemed fine. Full shut down and restart and .... blinking cursor forever. Doesn't read the hard drive after an initial read to the cursor.

Frustrated I looked for other OSes that would run, found Jolicloud and it installed and works over and over. Now, I could stay with Jolicloud, but its a cloud version of Ubuntu, apparently, and requires an internet connection just to work at all! What a terrible system!

So I installed Ubuntu again and again and again, but no matter what happens, all I get after a cold restart is a blinking cursor. Help!

---

### Post by Mister Fowler on 2010-09-10
Okay, while installing lately, I noticed before the GUI comes up, it says its missing several firmware files ("xxxxx.fw"). How do I get these files and where do I put them once I do find them?

---

### Post by krimzonstarr on 2010-09-10
If it says missing files after installation, it is possible that your LiveUSB was created with an iso file that wasn't 100% intact. Did you verify the checksum before you created the LiveUSB? What method did you create the LiveUSB?

---

### Post by Mister Fowler on 2010-09-10
I used the download iso from the ubuntu site and their recomended start up disk creator for either windows or ubuntu. I don'tknow how to use the checksum.

---

### Post by krimzonstarr on 2010-09-10
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

Always be sure to check the md5sum of all downloads. Sometimes during download tiny parts of the file may have been ignored or left behind, and this can cause a bad "burn." I have had issues with this in the past, find I have much better luck with torrents.

Follow that guide and see if that is your issue. If not, post back here and let us know!

---

### Post by Mister Fowler on 2010-09-10
Thanks! I will try that when I get home. :)

---

