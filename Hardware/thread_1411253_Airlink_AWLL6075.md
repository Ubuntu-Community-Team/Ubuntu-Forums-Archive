---
title: "Airlink AWLL6075"
date: 2010-02-19
forum: Hardware
---

### Post by ve3tru on 2010-02-19
Anyone know how to get the Airlink AWLL6075 golden N wireless usb adapter to work?.
Ubuntu 9.10 won't recognize it at all, XP has no problem duel boot.
Airlink products are some what Linux friendly, but this ones not. I think it has a RTL8191SU chipset whatever that means. It's a really nice product, works great, super small, very cheap too, hate to through it out.
Peter

---

### Post by labinnsw on 2010-02-26
Deleted due to broken link.

---

### Post by intrepid brian on 2010-10-12
> **ve3tru said:**
> Anyone know how to get the Airlink AWLL6075 golden N wireless usb adapter to work?.
Ubuntu 9.10 won't recognize it at all, XP has no problem duel boot.
Airlink products are some what Linux friendly, but this ones not. I think it has a RTL8191SU chipset whatever that means. It's a really nice product, works great, super small, very cheap too, hate to through it out.
Peter
I just got the Airlink AWLL6075 wireless adapter to work with Ubuntu 10.10 on a dell vostro 220s.  This other **_[post]("http://au.ubuntuforums.org/showthread.php?t=1468429&page=2")_** has great instructions on how to get it to work, or follow steps below.  Confirm that you have the RTL8191S chipset by using "lsusb".

1. Download the attached file below. Open Terminal and run what's within quotes.

2. Extract the contents ( "gunzip rtl8192sfw.bin.gz")

3. Use "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192sfw.bin /lib/firmware/`uname -r`/RTL8192SU"

5. Unplug  Wireless USB Adapter and then plug back into same USB port.

---

### Post by mk_kano on 2010-10-28
Thanks a lot. Worked great for me on both Ubuntu and OpenSUSE 11.3

---

### Post by tamavn on 2010-11-05
Work like a charm! Thank you very much.

---

### Post by donsimon on 2010-12-28
Sweet!  It worked for me too!

Thanks a bunch!

---

### Post by rockerZ71 on 2011-02-25
Thanks, worked.

---

### Post by boardinbum on 2011-03-22
Thanks intrepid brian, that worked...

But now it seems every time I update the kernel, I have to go through this process again. 

How do we make it permanent?

---

### Post by Wgimson on 2011-07-22
Noob here. I've downloaded and unzipped the linked file. I tried running the commands in quotes and got ..


mkdir: invalid option -- 'r'

Also, I don't understand the connection between downloading the file and running the commands in the terminal. Is there a step I'm missing *after* downloading the file and *before* running those two sudo commands? I'm running Lynx.

---

### Post by avtolle on 2011-07-22
> **Wgimson said:**
> Noob here. I've downloaded and unzipped the linked file. I tried running the commands in quotes and got ..


mkdir: invalid option -- 'r'

Also, I don't understand the connection between downloading the file and running the commands in the terminal. Is there a step I'm missing *after* downloading the file and *before* running those two sudo commands? I'm running Lynx.
I'd hazard a guess that you used the apostrophe rather than the backtick (found left of the "1" key). Try it with the backtick key.

---

### Post by Wgimson on 2011-07-22
> **avtolle said:**
> I'd hazard a guess that you used the apostrophe rather than the backtick (found left of the "1" key). Try it with the backtick key.

I probably *would* have made that mistake, but I copied and pasted haha. Here's what I'm getting...




I feel like I missed a step between downloading/extracting the linked file, and running the above commands. But I can't for the life of me figure out what it is.


Here's the portion of the instructions that's confusing me...

1. Download the attached file below. [B][I]Open Terminal and run what's within  quotes.

[/I][/B]What's supposed to be in quotes? Is this in reference to the two commands in steps 3 and four?

---

### Post by Wgimson on 2011-07-22
Ah, ok, stupid mistake. I got it to work for me. The problem now is, every time I shut down the system, I have to repeat these steps for the system to see wireless connections....

    1. sudo cp rtl8192sfw.bin /lib/firmware/`uname -r`/RTL8192SU
    2. Unplug and replug airlink USB into same port

......as though the RTL8192sfw.bin file gets erased, or is no longer correct, every time the system is rebooted. Any help would be much appreciated.

P.S. If it makes any difference, immediately after rebooting, the system still sees the wireless connection, but simply won't connect  to it. Then, after a few minutes of failing to connect, it no longer recognizes any wireless networks until I repeat the above steps. Again, any help would be  much appreciated and thanks a lot to the guys who have already posted solutions.

UPDATE - I don't know what the problem was, but it seems to be working fine now. Thanks guys.

---

### Post by jechill on 2011-08-23
ok when i run the command in a terminal window it says sudo then asks for a password but it wont allow me to type anything.
there has to be an easier way to install bloody drivers in ubuntu than this!

---

### Post by ericthelin on 2011-10-22
I found this thread from google and the information seems outdated so I thought I would send an update for the next person who finds it similarly.

This adapter seems to work great with ubuntu 11.04 (natty) right out of the box.  I just plugged it in and it came up and found my access point.  It didn't find any of the neighbors access points though like other cards do.  So the antenna may be lacking.  It also isn't getting 300Mbps, more like 150Mbps even with in 10 feet of the access point with open air between them.  But it does give N 802.11n speeds with no effort required on modern ubuntu and that is all I was really looking for.

Eric

---

### Post by neverstable on 2012-05-01
Its working like a charm. Thank you. Even in Ubuntu 10.04 LTS

---

### Post by carltonbanks787 on 2012-05-27
This worked perfectly! Thanks so much!

---

### Post by jimrooney on 2012-09-11
Eeepc 1005PE running Ubuntu 10.04.4 LTS

Worked like a champ.
Thanks
Jim

---

