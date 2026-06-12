---
title: "Grub doesn't work &lt;Grub rescue&gt;"
date: 2010-08-19
forum: Hardware
---

### Post by mrvly on 2010-08-19
Hi I have a problem. I just installed ubuntu netbook 10.4 once it finished installing i restarted the computer and since then it starts and I only get the following:
 
Error no such device: 5465edc-3f78-4e29-83cc
<Grub rescue>
 
i already lloked for help, but i can't ether start the trial version on my USB nor does the command 'sudo' work
 
please help i can't use my computer at all and there is very important data on it.

---

### Post by varunendra on 2010-08-21
How did you install it? I think it must have been the Live USB stick. Does it work no more?

The capability to boot from USB is almost essential for any further action.


As a quick solution for data access, if you have access to another computer with an Ethernet interface, try booting it off Slax Live CD/USB choosing "Slax as PXE server" from boot menu. Then connect your netbook to it using a cross-cable and boot it choosing 'Boot from Network' (or a similar option in BIOS/ Boot-Menu). It should be able to boot into Slax which you can use to copy your files to the other computer (creating a shared folder on it with read/write access).

But fixing the USB booting should be much easier &, as I said, is almost essential!

---

### Post by mrvly on 2010-08-22
Jeah i installed it with the live usb stick. But when I try to boot from it it doesn't work. I reinstalled it and tried another usb stick it simply doesn't work (I changed the bios setup so it boots from the usb first)
Thanks for the tip with the other computer so at least my data is safe.

---

### Post by varunendra on 2010-08-23
Sounds strange to me. I think we may be missing something here.

Could you please provide following details:

[LIST=1]
[*]Name of the .iso file that you are using to create the Live Usb. (this is to verify that it is 'Desktop', not 'Alternative' - which is bootable but not 'Live')
[*]Method you are trying to create the Live USB.
[*]Is your USB drive listed in BIOS by its name?
[/LIST]
Sometimes there is entry for booting off USB key in the BIOS, but the USB key gets listed under list of Hard Disks (or somewhere else) instead. It depends upon what kind of emulation it (USB key) is using. In such a case you should try to find the key by its exact name- like mine is listed as "Transcend Jet Flash" - under list of hard-disks!!

So if your Live USB is okay (is working perfectly on other computers), then there may be a possibility that you've set BIOS to boot off USB key first, while it is listed as HDD or something else (like USB floppy sometimes), and thus the BIOS switches to the next device in priority which is your regular HDD.

So what you need to verify first is:

[LIST=1]
[*]Your USB key is okay (is able to boot other computers).
[*]You are **able to identify it in BIOS** or Boot Menu and are sure that it gets first priority in boot order.
[/LIST]

---

### Post by camoledge on 2010-09-03
I have the same problem with a Samsung n310. I tried everything and nothing worked. Boot from live CD, samsung recovery **** from usb CD drive, all the processes suggested in threads where users where stuck at grub rescue>.

At some point I get "unknown filename" or some kind of error.

Isn't that crazy that to try a freeware OS I basically made unusable a 400$ netbook?

Isn't there a hardware way to be able to recover it? It is really getting frustrating. I hope someone can help. I can't boot anything on my n310 and it is sad.

---

### Post by varunendra on 2010-09-03
> **camoledge said:**
> Isn't that crazy that to try a freeware OS I basically made unusable a 400$ netbook?
Isn't there a hardware way to be able to recover it? It is really getting frustrating. I hope someone can help. I can't boot anything on my n310 and it is sad.

First of all, please calm down.

It is 12:27 am (just past midnight) here, but I'll try whatever I can before going to bed. :)

Please answer these:

[LIST=1]
[*]What resources you already have (Live CD, USB CD/DVD drive, a working computer, Live USB flash drive, ethernet cross-cable,....)
[*]What all are the options your BIOS has to boot from?
[*]What exactly you are trying now and what exactly is the error message you are getting?
[/LIST]

**EDIT:**
@camoledge,

I just realized that you are already getting good help at [your own thread]("http://ubuntuforums.org/showthread.php?t=1567141"), so I'd take a break now.

However, these may be a consolation for you that your netbook has the capability to run Ubuntu:
[http://ubuntuforums.org/showthread.php?t=1313956](http://ubuntuforums.org/showthread.php?t=1313956)
[http://ubuntuforums.org/showthread.php?t=1474299](http://ubuntuforums.org/showthread.php?t=1474299)

---

### Post by wilee-nilee on 2010-09-03
> **camoledge said:**
> I have the same problem with a Samsung n310. I tried everything and nothing worked. Boot from live CD, samsung recovery **** from usb CD drive, all the processes suggested in threads where users where stuck at grub rescue>.

At some point I get "unknown filename" or some kind of error.

Isn't that crazy that to try a freeware OS I basically made unusable a 400$ netbook?

Isn't there a hardware way to be able to recover it? It is really getting frustrating. I hope someone can help. I can't boot anything on my n310 and it is sad.

**The best thing to do** would be to start your own thread and post the bootscript in my signature in code tags as described.

Boot problems can sometimes be a one page or less communication string, but if mixed with another due to differences in problems and solutions it becomes difficult to follow.

---

### Post by camoledge on 2010-09-03
> **wilee-nilee said:**
> **The best thing to do** would be to start your own thread and post the bootscript in my signature in code tags as described.

Boot problems can sometimes be a one page or less communication string, but if mixed with another due to differences in problems and solutions it becomes difficult to follow.

Here is the thread I opened this morning, I just happened to drop here and so had the need to tell my story, sorry for that you are right, I hope I would be able to follow the rules better and don't panic, but you know I am in a really bad situation. I tried to edit my last post following your instructions.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1567141](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1567141)

---

