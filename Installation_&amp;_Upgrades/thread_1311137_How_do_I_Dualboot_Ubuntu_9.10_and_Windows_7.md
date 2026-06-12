---
title: "How do I Dualboot Ubuntu 9.10 and Windows 7?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by lwordish on 2009-11-02
Been looking all over for a guide how to dualboot Ubuntu 9.10 and Windows 7, with Ubuntu installed first. I've heard that Grub can cause some issues.

I just installed 9.10 and tweaked it just the way I like it, so I don't wannna re-install it.

Anyone know a guide or able to help me in the right direction?

---

### Post by fela on 2009-11-02
Well it's easy with Ubuntu versions that use GRUB 1.x, ie everything up to and including 9.04, as you can restore the GRUB MBR with its own self-recovery thingy from a livecd, after Windows has overwritten it with its own.

However, 9.10 uses GRUB2, and I don't think this has a recovery thingy.

So, the way I would do it is to backup the disk's MBR prior to installing Windows. I'll give you step by step instructions but remember: **doing this is dangerous to the point of losing all your data if you're not careful (although not permanently). Please, please do not blindly run these commands, and know exactly what they do before even opening your terminal!**

So, first I'd backup the first 446 bytes of /dev/sda (where /dev/sda is the harddisk with Ubuntu on it - of course make sure you use the right one). This contains the GRUB bootloader code. This is how you would do this, for example (but remember the disclaimer - **don't blindly run anything.**). Also, **remember to put the output file (of=/path/to/outputfile) somewhere that you know is safe, for example a USB flash drive or better, a different partition on your hard drive. Do NOT put it on the Ubuntu partition for obvious reasons. In my example, there is a USB flash drive mounted at /media/disk and I'm putting the first 446 bytes containing GRUB into a file on that flash drive.**

```
sudo dd if=/dev/sda of=/media/disk/before_windows_backup_446 bs=446 count=1
```

I'm not going to explain all those options and what they do, I'll leave that for you to find out if you don't know them already, as finding out how a program works yourself is essential if you want to run it to its full potential and without breaking things.

OK, now you can install Windows if you've verified you've done all this right. Of course, shrink the Ubuntu partition with Gparted from a LiveCD before installing Windows.

Now, after Windows has installed we need to restore the backup containing GRUB to the MBR from the USB stick (again mounted at /media/disk for the sake of example), but we'll also backup the Windows MBR (well I would anyway). For **example**:

```
sudo dd if=/dev/sda of=/media/disk/after_windows_backup_446 bs=446 count=1
sudo dd if=/media/disk/before_windows_backup_446 of=/dev/sda bs=446 count=1
```

Now reboot, eject the livecd and GRUB *will* come up if you've done it all right.

Oh and by the way, it's not grub that causes the issues, it's Windows. It decides to overwrite GRUB with its own MBR, thereby clobbering GRUB and making your system only able to boot Windows (typical Microsoft strategy).

---

### Post by rip_it on 2009-11-02
Think I'll wait for the thingy to come out.  I tried Windows 7 Pro with 9.10 two seperate harddrives, got that grub loading  grub rescue> error.

---

### Post by fela on 2009-11-02
> **rip_it said:**
> Think I'll wait for the thingy to come out.  I tried Windows 7 Pro with 9.10 two seperate harddrives, got that grub loading  grub rescue> error.

I think there's something catastrophically wrong with Karmic's grub. On my machine it worked, but only after about 30 seconds or so of the 'grub loading' text...should NOT happen and does not happen with grub2 on debian...strange. Anyway it'll probably (hopefully) fix itself in time.

---

### Post by Obazda on 2009-11-07
Hey guys! Im quite new to Ubuntu/ Linux (perh 2 weeks now)
After looking through quite a bunch of forums an wikis, i think i probably found a solution (actually it worked for me)

My native OS had been Win Vista Hp 32-bit,
had no problems dualbooting with 9.04 later 9.10, 
today i installed Win7 Pro (hehe BSOD during first try! ;)), had to restore grub2 through Live- CD, (win7 booted directly)
after that i couldnt boot into Win 7 with grub2, always got an error message.
restoring WIn7 bootloader brought me back where i started- as is guessed.. -.-

Finally i found this:

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

.. and the life saving comment (first one) 

Ryan Phillips                         
             [January 7th, 2009 at 7:40 am]("http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/#comment-5609")              "Instead of step 3, try installing the os-prober package. It should detect your Windows installation automatically:
 # apt-get install os-prober
# update-grub2"


so terminal-> sudo apt-get install os-prober /
sudo update-grub2 /
sudo reboot 



tadaa im dualbooting Win 7 32-bit/ Ubuntu 9.10 32-bit


(pls anyone with 64-bit OS's state your experience using that solution!) 


well i hope this will help some ppl out!

greetz from bavaria ):P

---

### Post by fela on 2009-11-07
rubbish post, delete please

---

### Post by Obazda on 2009-11-08
> **fela said:**
> rubbish post, delete please

I'll do it, but just tell me why it is a rubbish post? not to be offensive, i really want to know it, as one learns from failures?! :-k

---

### Post by conorsulli on 2010-01-10
> **Obazda said:**
> I'll do it, but just tell me why it is a rubbish post? not to be offensive, i really want to know it, as one learns from failures?! :-k

Please DONT delete as I would also like to follow this thread....

Ugh.. some people, just because its not relevant to them, They feel they can judge what others do and dont need to know... how annoying.

---

