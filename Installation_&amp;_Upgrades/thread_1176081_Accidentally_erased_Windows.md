---
title: "Accidentally erased Windows"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by TheHimself on 2009-06-01
I just got an Ideapad s10 and wanted to install ubuntu on it but I accidentally erased everything on HDD including Windows and drivers. Fortunately no data was (there to be) lost. If the computer had an optical drive then I would install Windows again but without an optical drive I don't know how to do this. 

This is my first time with Linux alone on a computer and sounds kind of scary! 

I had an experience during installation which I don't know if it's the case for everybody: when I was installing Ubuntu from a usb drive, I had to connect the device immediately after turning on the computer not before. Otherwise it would be "disconnected".

---

### Post by Steelmourne on 2009-06-01
This might reinstall vista (why would you want to?): [http://kurtsh.spaces.live.com/blog/cns!DA410C7F7E038D!1665.entry](http://kurtsh.spaces.live.com/blog/cns!DA410C7F7E038D!1665.entry)

As for the drive, it would depend on your BIOS settings and the boot order. Maybe you should try out Ubuntu for now. Look through help - its on the top panel with a blue question mark.

---

### Post by raymondh on 2009-06-01
> **TheHimself said:**
> I just got an Ideapad s10 and wanted to install ubuntu on it but I accidentally erased everything on HDD including Windows and drivers. Fortunately no data was (there to be) lost. If the computer had an optical drive then I would install Windows again but without an optical drive I don't know how to do this. 

This is my first time with Linux alone on a computer and sounds kind of scary! 

I had an experience during installation which I don't know if it's the case for everybody: when I was installing Ubuntu from a usb drive, I had to connect the device immediately after turning on the computer not before. Otherwise it would be "disconnected".

No need to be scared ... you have got a working OS right now. So, let's see about your goal of dual booting 'eh?

I am hoping that the restore partition is still there.  Can you boot into ubuntu and in a terminal, type

sudo fdisk -l 

and post it back.

Another dilemna is your lack of an external CD drive.  You can see this link as a reference but ... you will still need a working CD drive and the actual XP install disk as I not sure this method will work with the provided recovery disk.

[http://www.scribd.com/doc/13257/Boot-Windows-XP-From-a-USB-Flash-Drive](http://www.scribd.com/doc/13257/Boot-Windows-XP-From-a-USB-Flash-Drive)

Let's take this on one at a time and see if the recovery partition is still there.  If not, we can consider other alternatives.

Like I said, you have a working OS right now. :)

---

### Post by TheHimself on 2009-06-02
Yes, I have a working OS which looks very cute. Actually now I think having only one OS might be better. It reduces clutter and without the boot menu, booting is faster. My other computer is dual boot XP and Ubuntu and I've used windows when something gets messed up in Ubuntu like Kile in Jaunty. Thanks for the link. I think I won't install Windows until I really need it. And here is the result of fdisk -l  

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66666666

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris

---

### Post by raymondh on 2009-06-02
> **TheHimself said:**
> Yes, I have a working OS which looks very cute. Actually now I think having only one OS might be better. It reduces clutter and without the boot menu, booting is faster. My other computer is dual boot XP and Ubuntu and I've used windows when something gets messed up in Ubuntu like Kile in Jaunty. Thanks for the link. I think I won't install Windows until I really need it. And here is the result of fdisk -l  

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66666666

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris

Hello TheHimself,

Yes, you are now the proud owner of a 1-boot Ubuntu OS.  Just wanted to make sure ... no offense meant :)

Happy Ubuntu-ing.

---

### Post by emeraldgirl08 on 2009-06-02
You will need to buy or borrow an external drive if you want to restore your comp. I don't see no existence of a recovery partition in your fdisk report.

---

### Post by TheHimself on 2009-06-02
I think there is no reason for being proud. Something went seriously bad about the display. I just hibnernated the computer and got an error message about the display and when I turn it on .... it's like old computers with few colors and very low resolution. Restarting doesn't help. Even the Lenovo logo at startup is not displayed as before. 

Do you think I can do something about this myself? If no then I have to send it back to Lenovo and the first thig they do is to erase Linux and reinstall Linux. Help me keep my Linux!

---

### Post by raymondh on 2009-06-02
> **TheHimself said:**
> I think there is no reason for being proud. Something went seriously bad about the display. I just hibnernated the computer and got an error message about the display and when I turn it on .... it's like old computers with few colors and very low resolution. Restarting doesn't help. Even the Lenovo logo at startup is not displayed as before. 

Do you think I can do something about this myself? If no then I have to send it back to Lenovo and the first thig they do is to erase Linux and reinstall Linux. Help me keep my Linux!

What happens when you press FN + up or down to change the screen brightness (upon returning from hibernate)?

---

### Post by TheHimself on 2009-06-03
The screen gets brighter or dimmer. Just that.

---

### Post by raymondh on 2009-06-03
> **TheHimself said:**
> The screen gets brighter or dimmer. Just that.

What is the error message?

---

### Post by TheHimself on 2009-06-05
It appeared only ones while hibernating and said something like "display device failure". I sent it back to Lenovo for repair but I don't know how software can damage hardware. I'll keep you updated.

---

### Post by TheHimself on 2009-06-09
They reinstalled Windows and the display is back to normal. I don't know what exactly happened to it. I'm a bit afraid to install Ubuntu again.

---

### Post by MacFianna on 2009-06-09
Congratulations!!

You've killed Bill!

Do not be afraid of a straight Linux system! There are COUNTLESS Linux masters on these forums. Remember when you first ran a Windows system? A Mac system?

You too can master Linux.

And just think of what you can buy with the money you've funneled to satan every year to operate his overly flawed systems.

Cheers, mate! Time to celebrate your emancipation!

Mac

P.S. Seriously, if you cannot live w/o putting your hard earned money in the devil's filthy pockets, there's always clean re-install of Windows for practice. Probably not a bad idea considering you'll likely be doing it again in a couple of months, right?

---

### Post by raymondh on 2009-06-09
> **TheHimself said:**
> They reinstalled Windows and the display is back to normal. I don't know what exactly happened to it. I'm a bit afraid to install Ubuntu again.


Hello Thehimself,

For as long as you have a working system ... any system ... :)

You know, you can still try and learn Ubuntu/linux.  You can make a persistent live USB and boot into it once in a while to satisfy your curiosity and learnings.  Also, that makes a good back-up plan should anything render your windows inoperative :)

A quich google or forum search should point the way.

Welcome back ... like I say, for as long as you've got a working system, life is good.

Regards,

---

### Post by orangepenguin97 on 2009-06-09
do you still have a recovery partition?

---

