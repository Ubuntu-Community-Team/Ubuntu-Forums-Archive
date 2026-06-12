---
title: "Hard drive of disk?"
date: 2014-01-12
forum: Hardware
---

### Post by gordon33 on 2014-01-12
With all the problems (See below Re: UBuntu 10.04 will not boot up. ) I have had with trying to down load Ubuntu 13.10 I am thinking there is a problem with “disk errors”, “ disk access”, and or problem with the drive on my HP G60t-200 lap top.

I hope to save files and photos.  Are there methods to get to the hard drive without an operating system?  If so what do I need to get started?

Presently the computer will not boot up.  Are there ways to check the disk and drive in the computers present condition.
In a previous post: [http://ubuntuforums.org/showthread.php?t=2198806](http://ubuntuforums.org/showthread.php?t=2198806)  tilted “UBuntu 10.04 will not boot up. “  Tgalati4 wrote:

Re: UBuntu 10.04 will not boot up. 
Regardless of how you install 13.10, you didn't address the original problem. What caused your 10.04 system to fail? To me it looks like a disk failure or a power supply failure:

System running fine for several years (10.04)
Then Firefox crashes (typically a bad profile or cache is messed up due to disk errors).
Then Computer freezes (could be disk access problem--not technically frozen, but waiting for data--IOWaits in top go up.)
Then Computer won't boot--again, trouble reading the drive during boot.
Prolems installing new distro--if the drive is bad then installing new distros will be a frustrating experience.

What is the SMART status of the drive? 
Even with the above information more checks of the USB Startup key and download attempts were made.

---

### Post by Dreamer Fithp Apprentice on 2014-01-12
> **gordon33 said:**
>  Are there methods to get to the hard drive without an operating system?Without an operating system AT ALL? No. Computes without operating systems are merely ornamental.

> **gordon33 said:**
> Presently the computer will not boot up.  Are there ways to check the disk and drive in the computers present condition.Certainly. You'll have to boot from some other media. You will need to change the bios settings so it doesn't even try to boot from the problematic drive. 

The most important thing is:

If  you suspect a reasonable possibility that a hard drive with data you  need to recover is failing or the file system on it is corrupt, stop  using it immediately. Until you are ready to attempt recovery it  shouldn't even be powered up. So either put that laptop aside or  take the drive out and put it in a safe place until you are ready. You'll need to prepare some other media to boot from if you want to attempt the recovery on the same machine. If you don't already have something suitable, you'll need to work with another machine to make something or aquire a live disk from someone else, or get another hard drive if you have space for 2 and install an OS and recovery tools on it before you put the other drive back in.  Or you could do it all on some other machine. You'll need a hard drive with enough free space to put the hoped for recovered data on if you recover it.

Then study the subject for a few days. Look up terms like "data recovery". There is lots of software for this and lots of tutorials all over the net. Learn the subject well and make a plan BEFORE you power up that drive again. Good luck.

---

### Post by gordon33 on 2014-01-12
Hello Dreamer Fithp Apprentice

Thank you for your reply.  I did find some good information on data recovery.  
I have removed the hard drive on the HP G60t-200. 
Next, I will purchace a recovery cable.  
Once I get the cable I will check to see if any folders can be copied to my working computer.  
If not I will be looking into recovery soft ware.

I am hopeful I will make some progress now.

---

### Post by hansdown on 2014-01-12
Hi gordon33

The best data recovery tools I've used are on a live ubuntu disc, or usb.

If you can boot from a live disc, or usb, then you can browse and save your files to another usb.

First, boot the live ubuntu.

Next, open a terminal, and type...

> gksudo nautilus

You can now browse your files, and save them to another usb.

You can check the smart rtatus of the drive also.

[http://mikebeach.org/2011/05/21/how-to-check-your-hard-drives-smart-status-using-a-ubuntu-live-cd/](http://mikebeach.org/2011/05/21/how-to-check-your-hard-drives-smart-status-using-a-ubuntu-live-cd/)

---

### Post by gordon33 on 2014-01-13
Hello hansdown

Thank you I will be using recovery tools in a few days with a live CD.

Gordon33

---

### Post by Dreamer Fithp Apprentice on 2014-01-22
> **hansdown said:**
> Hi gordon33

The best data recovery tools I've used are on a live ubuntu disc, or usb.

If you can boot from a live disc, or usb, then you can browse and save your files to another usb.

First, boot the live ubuntu.

Next, open a terminal, and type...



You can now browse your files, and save them to another usb.

You can check the smart rtatus of the drive also.

[http://mikebeach.org/2011/05/21/how-to-check-your-hard-drives-smart-status-using-a-ubuntu-live-cd/](http://mikebeach.org/2011/05/21/how-to-check-your-hard-drives-smart-status-using-a-ubuntu-live-cd/)Certainly, that's usually all that is needed. But calling that approach "best" could be misleading to some poor soul who get's here from a search engine and concludes that if he has already done that and it didn't work, all hope is lost and he might as well junk the drive and the 4 years of work he can't find the backups to and move to darkest Africa because his boss is gonna kill him for this. Hardware DOES occasionally go bad in ways that a file browser can't see through. So for that matter, do filesystems. So while that way is "best" IF IT WORKS simply because it is the easiest and more often than not, is sufficient. But if it doesn't work, there are still plenty of options. An extreme case a couple of years ago was Seagate drives that wouldn't give up their secrets until you returned them to the factory so they could replace a defective chip. There are also programs that will attempt to read the same sectors over and over again, and more often than not, eventually get the data that would be lost to less aggressive techniques. I suspect there is a better chance they'll work if you don't have SMART remapping turned on. The point is there are still a lot of options left that may still work after the simple approach fails, if it does. Options that just cost the time to study them. If someone is talking about really valuable data there are still more options that could be expensive. The most important thing is not to do anything that could write to the drive until you exhaust any techniques that don't and not even to power it up without a definite plan what you are going to try when you do.

---

### Post by gordon33 on 2014-01-25
Hello All


I got the recovery cable and nothing showed up on the working computer that the USB cable was pluged into.  With a quiet room and the recovery cable's power supply on I could hear a ticking coming from the hard drive about as loud as a mechinal wrist watch.  I think It has beed refr=ered to as the tick of death.  This leads me to believe the hard drive is bad.  

Would any Data Recopvery Tools be able to recover data on this Hard Drive?  Or, will the Hard Drive need to be repaired first?

It is a Western Digital Hard drive.  Model WD 1600BEVT-60ZCT1

Gordon33

---

### Post by Mark Phelps on 2014-01-26
> Would any Data Recopvery Tools be able to recover data on this Hard Drive?Probably not.  Software tools can't overcome hardware problems.

> Or, will the Hard Drive need to be repaired first?Hard drive repair is VERY expensive, often running into thousands of dollars -- because you're paying for a drive to be disassembled, dioagnosed, and rebuilt in a clean-room environment.

---

