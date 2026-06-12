---
title: "GRUB Error 18 (Dual Boot with Win7)"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Vistro on 2009-10-12
Thank god for the liveCD.

Using Windows 7, I set aside 20GB for Ubuntu. I ran the CD, and told it to use the remaining disk space (the 20GB). It installed, and told me to reboot. It said GRUB Loading... then the next line said Error 18. So I went through the CD, blew up the partitions it made, then followed the instructions I printed from their website, made a 4096MB (twice my memory) as swap space, and made the rest of the free space as the root, using ext3, and "/" (without quotes) as the mounting path. Then I had it install.

Same thing on boot. 

So here I am on the liveCD, because it went and raped my HDD. How do I fix GRUB?

Thanks in advance.

PS. Not willing to do anything that involved blowing up my Windows partition.

---

### Post by presence1960 on 2009-10-12
see [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors").

Error 18 is returned when the partition you are booting (in this case Ubuntu) is beyond the boundary that BIOS can read. This is not an Ubuntu problem but a problem with your BIOS.

I would check and see if your BIOS has an update available. If not you need to put Ubuntu within the first 137 GB of your hard disk or when you install Ubuntu create a separate /boot partition for Ubuntu within the 137 GB boundary.

Due to limitations of your BIOS there is no other option.

What are your mobo and BIOS?

---

### Post by Vistro on 2009-10-12
Okay, I am brand new to Ubuntu and Linux. I've been working with Windows all of my life. So, if this is at all possible, please give instructions in fool proof steps, please.

Dell Latitude D610, newest Motherboard revision (firmware upgraded a few months ago, checking weekly for updates). 

140GB Windows, then 4GB for Swap, then the rest belongs to Ubuntu. It is a 160GB HDD in total.

I am running from a LiveCD so nothing is mounted right now. Is it at all possible to 

1) Blow up the swap space (4GB) to give some wiggle room for...
2) Scoot the windows partition 4GB over so I can...
3) Put a 100MB (or as big as I need for the /boot) partition JUST for GRUB and then...
4) Take the 3.9GB left over and make it swap space

And do this all without disturbing Windows? 

2GB memory, 1.8Ghz Intel processor, 160GB HDD, Windows 7 RTM.

---

### Post by Mark Phelps on 2009-10-13
Since you're running Windows 7, first thing you should do (if you haven't already) is use the option for creating a Recovery Disk. If you use Ubuntu or GParted to resize and/or move Windows 7, you're likely to need this disk to recover booting capability.  Better to be safe and have the disk, than have an unbootable system and no way to repair it.

---

### Post by Vistro on 2009-10-13
I can't boot into Windows. I can only boot into the Windows 7 install disk, (which does not see fixmbr as a command), and the Ubuntu LiveCD.  

I tried moving it around with gparted, but first it complained about errors, so I used the install disk to chkdsk c: /f (like gparted said), and then it worked for about a minute. Then I tried to move it, and somewhere along the line (I tried to go to bed each time) it failed. Said it could not read something. So I ran chkdsk (with all kinds of flags), and it fixed some sectors, and made a list of bad sectors. Now gparted won't touch the partition. It does say that it will gladly move it if I use something like ntfsresize --badsectors or something. 

I can't make a backup (the file server is not accessible at the moment), but my most recent system image was made last week. 

I at the very least want to be able to use windows. Then I can worry about a backup. 

What is the worst that can happen if I force gparted to move the partition even though there are bad sectors?

---

### Post by Vistro on 2009-10-13
Okay, I managed to get into Windows, and get rid of GRUB.

Is it at all possible to have Ubuntu on it's own partition, but still use the Windows boot manager?

---

### Post by namok on 2009-10-13
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by presence1960 on 2009-10-13
> **namok said:**
> [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Stay away from EasyBCD for two reasons: 1) it will not fix the GRUB error 18. You need to keep your Ubuntu root partition or a separate /boot partition for Ubuntu within the 137 GB boundary which your BIOS can read. Easy BCD will fix that scenario. 2) IMO Easy BCD is for people who don't want to learn about Linux and GRUB. GRUB can do way more things than EasyBCD and is way more configurable than EasyBCD. But of course it is your choice.

fixmbr is an XP recovery console command that will not work with Vista or Win 7. I believe windows 7 is like Vista in many respects, here are the commands you need from recovery console:

To restore the Windows Vista bootloader, you must first boot off your Windows Vista installation DVD.
If you have one of the many OEM computers that didnt come with a Vista installation disk, you can get the same effect with a Vista recovery disk, which you can download from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr
```

Now close the two windows and click "Restart."

---

### Post by Vistro on 2009-10-14
I was able to get it to boot to windows now, but I still can't make it boot to Ubuntu when redirected from 7's bootloader. 
 
I can't quite understand what you said above. You said eBCD won't fix the problem, then you said it would.
 
All I really want to do is use 7's bootloader, have it default to 7, and be able to select Ubuntu within a 10 second period. There has to be a good way to do that.
 
I can't move the Windows partition; gparted REFUSES because it INSTANTLY detects problem sectors (chkdsk just made a list of them, making gparted quit faster), so moving partitions around just isn't an option. 
 
Any other way to do this?

---

### Post by presence1960 on 2009-10-14
> **Vistro said:**
> I was able to get it to boot to windows now, but I still can't make it boot to Ubuntu when redirected from 7's bootloader. 
 
I can't quite understand what you said above. You said eBCD won't fix the problem, ***_then you said it would_***.
 
All I really want to do is use 7's bootloader, have it default to 7, and be able to select Ubuntu within a 10 second period. There has to be a good way to do that.
 
I can't move the Windows partition; gparted REFUSES because it INSTANTLY detects problem sectors (chkdsk just made a list of them, making gparted quit faster), so moving partitions around just isn't an option. 
 
Any other way to do this?

I never said EasyBCD would fix the problem. GRUB is way more configurable and can boot practically any OS. Why do you want to use the windows bootloader anyway? GRUB is far superior.

If you can't move your windows partition you will never be able to boot Ubuntu no matter which bootloader you use because your Ubuntu files needed to boot Ubuntu are beyond the area that your BIOS can read. It would appear that you need to wipe your hard drive and create the partitions necessary prior to installing windows & Ubuntu.

---

### Post by Vistro on 2009-10-14
Then can we work on that command that forces gparted to move the partition even though there are bad sectors?

Do I put it into the terminal or something?

It mentioned ntfsresize --badsectors or something like that.

EDIT: I thought the BIOS only had to deal with handing control off to the bootloader;

How can I tell if my Motherboard will look 8 or 137GB? If it's 8, will I simply have to choose between Windows or Ubuntu? Because at that point, only one OS can be in that range.

---

### Post by Vistro on 2009-10-14
I just noticed something peculiar...

I shrunk Windows down to 128GB before I started this fiasco. With the 4GB swap space, at least 5GB of the Ubuntu partition was in the 137GB limit. 

I'm shrinking windows to 120GB now, and I'll certainly try

1) Putting swap space last
2) Using GBs 122-136 (14GB) For '/'
3) Using GBs 137-154 (17GB) For personal documents
4) Using the rest for Swap

But I have this strange feeling that my Mobo will force the 8GB limit, in which case, I'm f*cked. 

Or is it like a "The entire partition needs to be in the readable space" thing?

---

### Post by raymondh on 2009-10-14
> **Vistro said:**
> I just noticed something peculiar...

I shrunk Windows down to 128GB before I started this fiasco. With the 4GB swap space, at least 5GB of the Ubuntu partition was in the 137GB limit. 

I'm shrinking windows to 120GB now, and I'll certainly try

1) Putting swap space last
2) Using GBs 122-136 (14GB) For '/'
3) Using GBs 137-154 (17GB) For personal documents
4) Using the rest for Swap

But I have this strange feeling that my Mobo will force the 8GB limit, in which case, I'm f*cked. 

Or is it like a "The entire partition needs to be in the readable space" thing?

Try 137. I remember having success at the 100GB 'area' in a 2002-vintage Dell. The idea is to have the linux kernel within the limit.  Also, in BIOS, see if HD detection is set to AUTO.  

Another trick is to put a [separate /boot]("http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition") (only needs about 200mb) in front of the drive.  

I second presence1960's opinion about easybcd.  I find GRUB more versatile/flexible.  If you choose, you can edit GRUB later to suit your preferences.

Regards,

---

### Post by Vistro on 2009-10-15
The problem wasn't GRUB, it was the motherboard not playing nice.

I decided to just have Ubuntu run inside the Windows partition, but I'll check out that HDD detection thing..

brb.

---

