---
title: "eeePC multiboot problem"
date: 2008-05-02
forum: Hardware
---

### Post by gnumd on 2008-05-02
Hello,

I was successfully using my eeePC 8G as follows:

1) WINXP on an 8gig SDHC 
   - start eeePC press <esc> and select boot off SDHC

2) Ubuntu 7.10 on an 8gig SDHC
  - start eeePC press <esc> and select boot off SDHC

Of note the ubuntu was installed onto the SDHC with the /HOME partition on the internal SSD

I also had a partition set with a boot flag on the SSD

Things were going well.

Then... I tried GnewSense 2.0 DeltaH the other night, placing it's install onto an external 250GB USB HDD.  GnewSense 2.0 boots fine, no internet access but it boots and works well off the SDHC.

Naturally I want to boot into my working Ubuntu Install and try to figure out how to get my GnewSense to work.  However, when I follow the above and choose to boot off the SDHC by pressing the <esc> key which worked before, it now gives me a black screen and I have no way to boot into the Ubuntu 7.10 that was previously working.

My /HOME and all the files on the SDHC are still present.

I think somehow the SSD's boot partition became altered during the gnewsense install.

What do I do to get back my ability to recognize the Ubuntu install on the SDHC and preserve it's use of the internal SSD for the /HOME?

I haven't tried it yet, but I wonder if the WINXP boot is damaged as well.  I would like to get that back if possible (presuming it is damaged).  My first priority is to get back to my Ubuntu it has all my working files and data that I need, the WINXP was an experiment and I could lose that.

thanks!

---

### Post by gnumd on 2008-05-02
> Then... I tried GnewSense 2.0 DeltaH the other night, placing it's install onto an external 250GB USB HDD. GnewSense 2.0 boots fine, no internet access but it boots and works well off the SDHC.
Correction works well off the USB HDD... wonder why I get a migraine dealing with all these abbreviations and keeping things straight!


> WINXP boot is damaged as well. I would like to get that back if possible (presuming it is damaged). My first priority is to get back to my Ubuntu it has all my working files and data that I need, the WINXP was an experiment and I could lose that.

Surprisingly, the WINXP on an SDHC still boots.  I really don't use it, because it runs slowly for me.  Ubuntu runs really well off the SDHC (back when it was working).

So my question is:
QUESTION A:
HOW TO:  Reinstall just the boot portion of the SSD to enable recovery of the /HOME (on the SSD) and access to the previously installed applicatons and everything else stored separately on the SDHC?

My other question is:
QUESTION B:
With the eeePC is there a FREE/LIBRE way to use the wifi and LAN to get internet access?  I would love to move to GnewSense which is based on the 8.04 Ubuntu distribution and try to only use non-proprietary software.  Any ideas or suggestions?

Lastly a general question:
QUESTION C:
I read a 557 post about backing up a GNU/LINUX install... far to long to work through and trust the information in my opinion.
IS there a guide online that WORKS to perform a back-up of a GNU/LINUX install that spans multiple partions that can put all of the needed files and installed software on an external HDD or DVD?

Thank you.
I do think solving these issues would be generalizable to other users, particularly those daring noobs such as myself who would like to use GNU/LINUX and perhaps pioneer through these tough spots in order to share what we learn with others less daring.

~gnumd~

---

### Post by starcannon on 2008-05-02
I'd probably try booting from ubuntu livecd and running grub from command line, perhaps you can restore you boot sequence that way, it does sound like perhaps that other install scrubbed ubuntu outta grub, also note that you can use the livecd to birt from first hard disk (just be sure not to have the external hdd plugged in perhaps to save confusion, and maybe even pull the mmc card out)

Just to make sure you have more options, you can also press 'esc' at the boot post screen and get a boot device order list that way and choose the device you'd like it to attempt to boot first.

GL

---

### Post by gnumd on 2008-05-02
> I'd probably try booting from ubuntu livecd and running grub from command line, perhaps you can restore you boot sequence that way, it does sound like perhaps that other install scrubbed ubuntu outta grub, 

I think I'll need the command line to install just the boot sequence and have it direct itself to the SDHC card where my Ubuntu is installed and to use the internal SSD as the /HOME.  I just don't know how to do that.

> also note that you can use the livecd to birt from first hard disk 
Booting from the first hard disk doesn't work, and it gives a GRUB loading error 17 which I believe is the same error I always got even when things worked booting off the SSD.  I did not install grub to avoid confusion. I use the bios option when I press the <esc> key to choose where to boot from instead of grub.  The first hard disk is only my /HOME directory, the actual install is on the SDHC card.

> (just be sure not to have the external hdd plugged in perhaps to save confusion, and maybe even pull the mmc card out)
Agree, and that was one of the first things I did to ensure the machine didn't try to boot from there.

> Just to make sure you have more options, you can also press 'esc' at the boot post screen and get a boot device order list that way and choose the device you'd like it to attempt to boot first.

I am not sure I know what you mean by the "boot post screen."  I think I am doing this successfully the way I described.

So recap:  When I boot off the SDHC I get a black screen with a flashing cursor and nothing happens.  So I think the boot partition on the SSD is broken.

I'd really appreciate a link or instructions on how to only reinstall or "fix" the boot partition and leave my other partions alone (but direct the boot to the data installed there already).

Thank you.
~gnumd~

---

### Post by gnumd on 2008-05-02
I'm moving this post to installation/upgrades.

Please reply there.

Thank you.

[http://ubuntuforums.org/showthread.php?p=4867272#post4867272](http://ubuntuforums.org/showthread.php?p=4867272#post4867272)

~gnumd~

---

