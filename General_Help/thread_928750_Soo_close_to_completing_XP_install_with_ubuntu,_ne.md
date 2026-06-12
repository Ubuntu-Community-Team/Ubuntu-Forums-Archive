---
title: "Soo close to completing XP install with ubuntu, need help!!"
date: 2008-09-24
forum: General Help
---

### Post by Thyssenkrupp on 2008-09-24
Okay, so ive done everything so i can install xp on a seperate partition to ubuntu, now, when i boot from my xp install disc, it says the whole:

Setup is configuring hardware........blah blah blah..

and then it just goes to a black screen, and does nothing......


im running ubuntu 8.04

help, anyone?

thanks,

Jak

---

### Post by Therion on 2008-09-24
Are you trying to configure a dual-boot system; Ubuntu and WinXP on a single drive?

---

### Post by Thyssenkrupp on 2008-09-24
Yes, i have allocated 30gig of un formatted space for XP to go on, which , in theory should work, any suggestions?

---

### Post by fourthofjuly on 2008-09-24
> **Thyssenkrupp said:**
> Yes, i have allocated 30gig of un formatted space for XP to go on, which , in theory should work, any suggestions?
format the unformatted 30gig partition as ntfs before you load the XP disc for installation

---

### Post by Therion on 2008-09-24
> **Thyssenkrupp said:**
> ... any suggestions?
Well... Yeah.

If it's not totally out of the question at this point in time, it's a lot easier to install Windows FIRST, and then Ubuntu.  Reason being is that Windows does NOT like sharing the Master Boot Record... So you install it first and then let GRUB handle the dual-booting.

I suppose installing XP and then doing the 'buntu install would be a huge PITA??

Edit:  If so, fourthofjuly's suggestion should get you over the hump.  It would not be my preferred way to go about things, but it should work.  Emphasis on should...

---

### Post by Thyssenkrupp on 2008-09-24
Ill try formatting to ntfs,

the only way to wipe ubuntu though is to install xp over it, which i cant do lol

can i?

---

### Post by fourthofjuly on 2008-09-24
> **Therion said:**
> Well... Yeah.

If it's not totally out of the question at this point in time, it's a lot easier to install Windows FIRST, and then Ubuntu.  Reason being is that Windows does NOT like sharing the Master Boot Record... So you install it first and then let GRUB handle the dual-booting.

I suppose installing XP and then doing the 'buntu install would be a huge PITA??

Edit:  If so, fourthofjuly's suggestion should get you over the hump.  It would not be my preferred way to go about things, but it should work.  Emphasis on should...
very true, but maybe it doesn't matter much

you can restore grub boot loader using this link

[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

haven't tried it myself though...

---

### Post by lswest on 2008-09-24
About the GRUB re-install:
> For GRUB restore to MBR:
boot to the LiveCD (this is the easiest way IMHO) and then start a terminal (applications-->accessories-->terminal)and type:

    ```
sudo grub
    find /boot/grub/stage1
    root (hd?,?)
    setup (hd?)
    quit
```


where the (hd?,?) and (hd?) corresponds to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).

This is all off [my blog]("http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html") and I guarantee the method works, because I've done it a number of times.  There's a bit more info on my blog and a link to another bootloader-restore how-to in case you run in to a snag.

---

### Post by Therion on 2008-09-24
> **Thyssenkrupp said:**
> ... the only way to wipe ubuntu though is to install xp over it, which i cant do lol

can i?
You CAN, yes.  You'll completely and totally WIPE the drive in the process however; and I don't know if that's an issue for you at this point in time or not.

It's how I would do it.  But that's me.  I like doing things a certain way and in my opinion the BEST way to set up a dual-boot is to install Windows first and then Ubuntu.  

I'm not saying it's the best way for you to do it though, and it's certainly not the only way to do it.

---

