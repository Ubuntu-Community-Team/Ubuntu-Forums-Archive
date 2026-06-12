---
title: "Error 18 when booting from HDD"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by frydchkn on 2009-08-30
Greetings to the Ubuntu community.  I have recently installed Ubuntu on a VAIO desktop to recover a bad Buffalo drive in ext3 format.

The problem I'm having is when I try to boot from the installation on the HDD, I get an "Error 18" when GRUB is loading.  Everything runs perfectly fine if I boot from a LiveCD.

I'm using a Samsung 1TB HDD on a Sony PCV-RX550.

Any help will be greatly appreciated, its my first post on my first system.  I'm excited about the Linux switch from Windows and can't wait to tinker with it some more.

Thanks again,
Max

---

### Post by running_rabbit07 on 2009-08-30
You are sure the HDD is working properly?

Did you get any errors during the install?

Have you ran the check disk option on the LiveCD?

---

### Post by frydchkn on 2009-08-30
Haven't tried the checkdisk option, but the drive is new and works just fine if I boot from the LiveCD.  It came out of a Buffalo NAS device whose firmware crashed after a power outtage.  

Could my BIOS have something to do with it?

---

### Post by running_rabbit07 on 2009-08-30
[s]I doubt BIOS is the culprit.[/s] It sounds like grub may need to be reinstalled but first I would recommand testing the disk.

In this [thread]("http://ubuntuforums.org/showthread.php?t=224351") you will find instructions for reinstalling grub from the LiveCD.

---

### Post by frydchkn on 2009-08-30
Just ran checkdisk with 0 errors.  I have reinstalled Ubuntu 3 times so far...isn't that better than just reinstalling GRUB?

---

### Post by running_rabbit07 on 2009-08-30
Sounds like there is a hardware problem then. 

While booted into the LiveCD can you post the output of ```
 fdisk -l
``` That is a lower case L.

---

### Post by frydchkn on 2009-08-30
I'm fairly new to this, where do I run this code?

---

### Post by running_rabbit07 on 2009-08-30
Before trying the above code check out this [thread]("http://ubuntuforums.org/showthread.php?t=11764").

If that thread doesn't fix your system then run the above code by launching the LiveCD and going to Aplications>Accessories>Terminal, then type the code into terminal.

---

### Post by Dangerousdave26 on 2009-08-30
> **frydchkn said:**
> 

Could my BIOS have something to do with it?

I think it could

see my thread on the same subject and a few people who helped fix it.

[http://ubuntuforums.org/showthread.php?t=1252563](http://ubuntuforums.org/showthread.php?t=1252563)

In particular look at his post 

[http://ubuntuforums.org/showpost.php?p=7865354&postcount=6](http://ubuntuforums.org/showpost.php?p=7865354&postcount=6)

Good luck

---

### Post by running_rabbit07 on 2009-08-30
Very well could be. After searching for grub error 18 on google I found the thread I mentioned about that talked about BIOS.

---

### Post by raymondh on 2009-08-30
As dangerousdave26 mentioned (and do check his thread), error 18 usually happens when the BIOS cannot access beyond a certain limit.  The limit depends on the vintage of your BIOS.

For more info, here's [herman's link]("http://members.iinet.net/~herman546/p15.html#18").

---

### Post by frydchkn on 2009-08-30
Thanks all of you guys for all of your support.  I have reinstalled and made a 5gig partition where I installed the OS.  It now boots up but it doesn't seem to see the rest of the 995gigs.

Can I force mount this other partition?

---

