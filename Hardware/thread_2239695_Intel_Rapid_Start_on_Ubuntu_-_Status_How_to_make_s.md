---
title: "Intel Rapid Start on Ubuntu - Status? How to make sure it's working?"
date: 2014-08-15
forum: Hardware
---

### Post by Axx83 on 2014-08-15
I recently bought a Lenovo ideapad u430 touch with a beautiful 256gb SSD drive. I installed Ubuntu in dual boot with windows and everything works smoothly, even the intel wireless that used to have problems.

I read on this article about Intel Rapid Start Technology [http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html) that there was work on implementing it in Linux for Kernel the 3.11 and here [http://summit.ubuntu.com/uds-1308/meeting/21883/foundations-irst-support/](http://summit.ubuntu.com/uds-1308/meeting/21883/foundations-irst-support/) that it was discussed for Ubuntu. Now we're on the 14.04 and Kernel 3.13.

Is Rapid Start functioning in Ubuntu? How do I know if it's working for my system?

---

### Post by oldfred on 2014-08-15
If you just have one SSD, you probably do not have SRT. That is in the systems with a hard drive and a small 16 or 32GB mSATA or SSD on a hybrid hard drive. 

And as with any cache you could not share with Windows. If you have both Windows and Ubuntu on an SSD, you only gain a little as Ubuntu boots very fast, not sure about Windows with fast boot off.

Many with the larger 32GB mSATA SSD drives found SRT was only using a small part, 8GB for the 8GB RAM, so they installed / (root) into mSATA drive so Ubuntu was fully on SSD. Makes Ubuntu faster than Windows which was using SSD only for faster booting.

I see this with gdisk list of available partition types, so gdisk can show if you have a SRT partition.
8400 Intel Rapid Start 

       sudo apt-get install gdisk
sudo gdisk -l /dev/sda

---

### Post by Axx83 on 2014-08-15
I definitely have IRST on this laptop because it works on windows, the option is present in the power settings and if I turn it off the laptop just goes in suspend, slowly depleting all my battery as expected.

It should be working on Ubuntu as well according to this patch in october 2013 [https://gist.github.com/hadess/6968197](https://gist.github.com/hadess/6968197) the problem is I really can't find much on internet regarding this.

And yes Ubuntu boots fast but the value of RST is that it's a very quick hybernate, after x minutes that the laptop suspends it turns the computer off, when I come back and open the lid it turns the computer back on with all my windows and tabs there.

---

### Post by oldfred on 2014-08-15
But there is only one hibernation partition? 
So if you hibernate Windows then hibernate Ubuntu it would overwrite the Windows data? 

Not sure if there is any way to create two partitions and keep them separate. The implementation for Linux, I would think would be for those who only have Linux or only want to hibernate Linux.

---

### Post by Axx83 on 2014-08-17
There's a Windows hibernation partition for sure and then a linux swap, which is used by Ubuntu. I believe that would be used by the hibernate command.

---

### Post by oldfred on 2014-08-17
Linux uses swap for Hibernation, but that is different than the Intel SRT hibernation. Unless Intel also rewrites its software for dual booting & using two partitions, I am not sure it would work.

Not sure if I understand the difference in hibernation anyway. The Intel SRT was mostly for faster booting on hard drives with its boot cache on a small SSD. If everything is on a SSD what advantage is a Intel SRT over just standard hibernation as then both Windows hiberfile & Ubuntu's swap partition would be on SSD. 
But even a full startup on a SSD is very fast.

---

### Post by Axx83 on 2014-08-18
On my computer suspend works pefectly while suspend_bybrid (first suspend then hibernate after 15 minutes of suspend) goes into suspend, apparently saves the image in the swap partition but actually never hibernate even after the 15 minutes of the timeout. I've used this script [http://askubuntu.com/a/145676](http://askubuntu.com/a/145676) in /etc/pm/config.d/.

What I wanna know is: how do I make suspend_hybrid to actually work and how do I check if the system is using intel RST or software hybernate?

Supend_hybrid seems exactly like what windows 8 does with RST.

---

### Post by oldfred on 2014-08-18
That is a different question than your title.
I do not use hibernate, so cannot help on that. I have seen a few threads with that in the title.
You might try a new thread on hibernation with Linux.
But it looks like the askubuntu post covers most of the issues.

---

### Post by WinEunuchs2Unix on 2014-09-10
I've just got a new old DELL 17R 7720 SE with a 500gb SATA II and 32gb mSATA (SSD nand drive).  Setting it up the night before last it used 19gb for Caching C: drive and 11gb "System Reserved".  The 11gb is for system hibernation which I would like to use in Ubuntu's bcache program.  I'd like google and nautilus to run a little faster.

I assume the 19gb cache must be left untouched because it is accelerated disk blocks from Windows C: Drive.  I plan to repartition it (defrag is running on it now) such that there's 250GB for Win7 and 250GB for LINUX.  The laptop has a second HDD bay (in addition to the tray caddy) and I plan to put a 1TB SSHD there.  I already added one to this old Toshiba Satellite 300 and it feels 10 times faster than the old one.

Under Windows the 19 gb partition of the SSD cache I assume is saving program images and their working files from the HDD between suspend/resumes and reboot cycles because everything I used so far like control panel and google are insanely fast.

Under Linux's bcache what I've read so far leaves just as many questions as answers.  For example it says sequential reads are not cached but I want some user space programs cached.  No need to cache kernel modules since boot time is only 10 seconds and they stay in ram unless manually removed.

bcache says it's best to install on fresh disks so that "super  blocks" or something like that can be created on ext4 partitions for both HDD and SSD.  I've read on posts that if they setup stuff on the 32gb mSATA's hibernation / rapid start system reserved space of 11 GB and Window's is used to decelerate / recelerate the HDD to the 19GB SSD cache then their 11 GB partition gets nuked.

I guess it's as confusing as it sounds until you actually try it.  First I have to research some more and learn the config / installation parameters a little better.

Oh one myth about some people having backlit keyboards and some not having them on this SE (Special Edition) model I can clear up-- some people know how to press <Fn>+F6 to turn it on and some do not.  The previous owner thought none existed but the BIOS clearly showed it did and a quick google found the controls for it.

Another myth about loosing the HDD by turning on cache and forced to reinstall windows might have been true for BIOS version A01 through A15 but the version I downloaded 2 nights ago A16 was able to turn on caching with no HDD data loss.

It pays to buy an old laptop not only saving a thousand dollars but also saving pains from bleeding edge technology after mfg's and developers get all the bugs worked out.

Anyone still awake with advise on bcache would be welcomed.

As far as Intel RST or Intel SRT support within Linux that the OP is looking for I haven't come across any such things in my research so far.  Intel did release a white paper about Linux caching in 2011 or something like that.

---

### Post by WinEunuchs2Unix on 2014-09-12
This is the answer to my last post.  I've read 20 or more misleading links until I found this one: [https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows](https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows)

The gentleman has two 128 GB SSD's for caching + OS permanent installation.  He has two 1 TB HDD's for Data.  He dual boots with Windows 8 and Debian (sort of Ubuntu's Sister if you will).  He's using bcache under Linux (like I want to do) and Intel SRT under Windows (like I am now).  The difference is his SSD has an extra device for 8 times the size and he has an extra HDD for 4 times the data size.

He has written the meat & potatoes of using Linux bcache which includes other people's questions and answers in a debate style at the bottom of the web page.

(Sorry much of this post is copy & paste from another post I just made.  It might violate forum etiquette but I wanted to leave a path for others with the same question to follow)

---

