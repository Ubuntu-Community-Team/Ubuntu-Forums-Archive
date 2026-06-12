---
title: "GRUB2 doesn't detect Windows 7"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Torquemada28 on 2009-11-01
**_Brief Problem description:_**

I have just installed Ubuntu 9.10 x64 but GRUB2 hasn't added the Windows 7 x64 installation to the boot menu. Now I can't boot into Windows 7.

**_Technical Information_**

I have 5 drives installed, which are divided into a total of 12 partitions. That being the case, I will list the drives/partitions that are relevant to this issue.

_SDA_: is a 320GB drive containing my Ubuntu installation.
      SDA1: is /boot
      SDA5: is /home
      SDA6: is /
      SDA7: is swap

_SDC_: is a 320GB drive containing my Windows 7 installation and a partition containing my music.
      SDC1: is the Windows 7 partition (volume label = Win7)
      SDC5: is a partition containing music files (volume Label = Music)

In addition to these drives, there is also SDB (4 partitions), SDD (1 partition) and SDE (2 partitions) but these have no bearing on this issue.

**_Background Information_**

Previous to installing Ubuntu 9.10 x64, I had a old 200GB IDE drive that had a beta version of Ubuntu 9.10 i386 installed and which dual booted fine with Windows 7. Due to the purchase of a new 1.5TB drive, I had a spare 320GB drive but not enough room in the case for 6 drives. I decided to remove the 200GB IDE that had the 9.10 i386 beta on it and install the new 64 bit Karmic Koala on the newly partitioned 320GB drive (now SDA).

**_Additional Information_**

I have tried to reinstall GRUB2 in the hopes it will find Windows 7 without success. I also added an entry into /etc/grub.d/40_custom for Windows 7.
```
echo "Windows 7" >&2
menuentry "Windows 7" {
insmod ntfs
set root=(hd2,1)
    chainloader +1
```

Still no joy. When I run "sudo update-grub" it still doesn't list the Windows 7 menu entry.

Now here's the weird part; I decided to try to boot directly from the Windows 7 drive (SDC) by changing the hard drive order in the BIOS. I figured that GRUB chainloaded the Windows 7 loader when the beta was installed so the Windows 7 loader should (theoretically) still be there.
What I got was GRUB stage 1.5 loading and then error 17. WTF?
I used the Windows 7 installation disk to repair the MBR  and reinstall the Windows 7 loader but it's just not working. I still get error 17 when I boot directly from SDC.

**_Conclusion_**

Here's what I think is going on.
The 32bit 9.10 beta I had used GRUB legacy (hence stage 1.5) which wrote to the MBR on SDC. When I pulled the 200GB Ubuntu drive out, a non-functional remanant of GRUB legacy was left on SDC and the 64bit 9.10 installed GRUB2 on SDA1 because I designated that as /boot.
GRUB2 can't "see" the Windows 7 installation because the SDC MBR is all screwed up with a broken GRUB legacy install instead of having a Windows 7 loader.


Can anyone help me to fix the MBR and get the Windows loader back on so GRUB2 can locate it and add the entry to the boot menu via os-prober?

If you need more information, please ask.

Thanks in advance.

---

### Post by Torquemada28 on 2009-11-02
The volume of users on this forum is great but also bad. It's great because there's a good chance someone can help but bad because the number of new threads means your thread has about 10 minutes on page 1. This thread took 19 hours to be pushed back around page 20 where only the most diligent forumite delves.

**_Update_**

I used Super Grub disk to try to reinstall the Windows bootloader. Now when I try to boot from SDC1 it says BOOTMGR is missing, even though I looked in /windows/system32/boot and bootmgr is there. I've tried reinstalling the Windows 7 loader (as opposed to the XP loader that Super Grub Disk would've installed) using the Windows 7 disk but everything in the "Repair My Computer" section seems to be pretty useless.
Unfortunately, whatever I did with SGD has resulted in Ubuntu being unbootable. When I try to boot from SDA1, I get a flashing cursor but no GRUB. Not even a GRUB error.
As a result, I partitioned off some space on the end of SDA and installed Windows 7 on it. Strangely, when I added an entry for the Windows 7 installation on SDC to the BCD using EasyBCD, the entry refuses to show up in the bootloader at startup.

I seem to be caught in a knowledge void between the new kids in town; Windows 7 and GRUB2.

I might try loading the LiveCD and seeing if gparted can shed any light on this, since Windows 7's Disk Management utility can't set active and boot flags on drives and is largly useless.

Any help at this point would be much appreciated.

---

### Post by oldfred on 2009-11-02
If Win7 will not boot on its own grub will never be able to chainboot it. It sounds like you someow overwrote the windows partition boot. Win requires both the MBR and the PBR partition boot. You should run both fixMBR and fixboot on the windows drive from the win repair disk.

Karmic beta definitely had grub2, but you may at some time in the past installed legacy grub in the MBR of your windows drive.

There seem to be more problems of grub not seeing drives in the correct order and not installing in the right drive. Old grub sometimes had this problem but it seems worse now or maybe we are just seeing all the problems. One user had a second working drive in windows and ubuntu installed correctly to it but it was not intialized in the BIOS so Grub never saw it. You may want to check your BIOS for drive configuration even if they have worked fine before. Grub seems to require everything just correct.

Did win7 create a 100mb boot partition? It does so on clean installs and that has added confusion as it does not show up correctly all the time.

More info on grub2:
Grub2 info by ranch hand and many links to other grub2 info sites
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

reinstall grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

versions:
grub-install -v
uname -a

---

### Post by ram130 on 2009-11-02
> **oldfred said:**
> If Win7 will not boot on its own grub will never be able to chainboot it. It sounds like you someow overwrote the windows partition boot. Win requires both the MBR and the PBR partition boot. You should run both fixMBR and fixboot on the windows drive from the win repair disk.

Karmic beta definitely had grub2, but you may at some time in the past installed legacy grub in the MBR of your windows drive.

There seem to be more problems of grub not seeing drives in the correct order and not installing in the right drive. Old grub sometimes had this problem but it seems worse now or maybe we are just seeing all the problems. One user had a second working drive in windows and ubuntu installed correctly to it but it was not intialized in the BIOS so Grub never saw it. You may want to check your BIOS for drive configuration even if they have worked fine before. Grub seems to require everything just correct.

Did win7 create a 100mb boot partition? It does so on clean installs and that has added confusion as it does not show up correctly all the time.

More info on grub2:
Grub2 info by ranch hand and many links to other grub2 info sites
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

reinstall grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

versions:
grub-install -v
uname -a

what happen if one deletes dat 100mb(mines 128 )? cause I did :(

---

### Post by F_C on 2009-11-02
[[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22223/)

---

### Post by Torquemada28 on 2009-11-02
> **oldfred said:**
> If Win7 will not boot on its own grub will never be able to chainboot it. It sounds like you someow overwrote the windows partition boot. Win requires both the MBR and the PBR partition boot. You should run both fixMBR and fixboot on the windows drive from the win repair disk.
Thanks, I'll boot the W7 install disk and try those utilities.

> **oldfred said:**
> Karmic beta definitely had grub2, but you may at some time in the past installed legacy grub in the MBR of your windows drive.
Possible but doubtful. That installation of Win7 is not very old and I hadn't installed any linux distros between installing Win7 and installing Karmic beta. Before Karmic beta, the windows bootloader worked fine by itself and it worked fine when it was dual-booting with Karmic beta. My Spidy-Sense is telling me it was the Karmic final installation that hosed the windows MBR.

> **oldfred said:**
> There seem to be more problems of grub not seeing drives in the correct order and not installing in the right drive. Old grub sometimes had this problem but it seems worse now or maybe we are just seeing all the problems. One user had a second working drive in windows and ubuntu installed correctly to it but it was not intialized in the BIOS so Grub never saw it. You may want to check your BIOS for drive configuration even if they have worked fine before. Grub seems to require everything just correct.
I've been spending lots of quality time in my BIOS just lately and I'm 100% sure everything is hunky-dorry in there. All drives detected and configured properly.

> **oldfred said:**
> Did win7 create a 100mb boot partition? It does so on clean installs and that has added confusion as it does not show up correctly all the time.
Funny you say that. The Win7 installation on SDC1 didn't create a special boot partition but the one I installed yesterday on SDA did make a 100mb boot partition. I'm not sure under what conditions Win7 makes the boot partition since one install did and the other didn't. I can't see that the boot partition is mandatory since the Win7 installation without the boot partition worked fine up until recently.

> **oldfred said:**
> More info on grub2:
Grub2 info by ranch hand and many links to other grub2 info sites
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

reinstall grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

versions:
grub-install -v
uname -a

Thanks for the info. My primary goal right now is to get the Win7 bootloader working again and then hopefully a GRUB2 reinstall will detect it and add it to the boot menu.

---

### Post by Torquemada28 on 2009-11-02
I've managed to get back into my original Win7 installation so I'm 50% fixed.

I ran...
```
bootsect /nt60 E: /force /mbr
```
(E: is the Win7 drive)
then
```
bootrec.exe /fixmbr
```
then
```
bootrec.exe /fixboot
```
and finally
```
bootrec.exe /rebuildbcd
```
This last command scanned my drives and allowed me to add any windows installations to my BCD list.

Next will be booting to the Ubuntu 9.10 LiveCD and seeing if I can reinstall GRUB2. With any luck, it will now see the Win7 bootloader and add it to the menu.

I'll post the results.

---

### Post by Torquemada28 on 2009-11-03
No, it's all gone to **** again. No Win7 boot, no Karmic boot and even bootrec /fixmbr and bootrec /fixboot don't seem to help.
I've now installed xp on a spare partition.

If this ******** continues, I'm going to erase 9.10 and install Linux Mint 7 instead, until the dropkicks who developed GRUB2 can learn to extensively test before releasing such a disasterous piece of crap to unsuspecting users. Seriously, how could you be unaware of such a huge bug such as GRUB2 killing the Vista/Win7 bootloader? Judging by the amount of users having this dual-boot issue, it should've happened in any testing environment.

Sorry guys, this is hands down, the worst Ubuntu release ever.
GRUB2 = Fail

---

### Post by sliketymo on 2009-11-03
> **Torquemada28 said:**
> No, it's all gone to **** again. No Win7 boot, no Karmic boot and even bootrec /fixmbr and bootrec /fixboot don't seem to help.
I've now installed xp on a spare partition.

If this ******** continues, I'm going to erase 9.10 and install Linux Mint 7 instead, until the dropkicks who developed GRUB2 can learn to extensively test before releasing such a disasterous piece of crap to unsuspecting users. Seriously, how could you be unaware of such a huge bug such as GRUB2 killing the Vista/Win7 bootloader? Judging by the amount of users having this dual-boot issue, it should've happened in any testing environment.

Sorry guys, this is hands down, the worst Ubuntu release ever.
GRUB2 = Fail
 We are all  sorry that you are having a rough go,but Ubuntu is not made to necessarily accommodate Windows 7,or any other OS for that matter. You have to take into account that they are competing system,not exactly siamese twins.It is but by the grace of developers,testers,hackers,and determined individuals of all stripes that such a thing as dual-booting is even possible,let alone works a large percentage of times.Some things just aren't made for each other.

---

### Post by Mark Phelps on 2009-11-03
Sorry you're having such serious problems, but if it's any consolation, you're not alone.

I run a multi-boot machine, including Windows 7, and did a test of upgrading to GRUB2 to see what would happen -- disaster!!  NOTHING would boot anymore.  Tried all the usual stuff -- in Ubuntu and Seven.  Nothing fixed it.

Fortunately, since I do this kind of experimenting all the time, I was careful to make full image backups before the changes.  So, I restored from backup and all is OK now.

In my case, I only had a single Windows 7 partition, but it still encountered show-stopper kinds of problems!

For what it's worth, I think the combination of a new partitioning sequence in Windows 7, plus a LOT MORE complicated setup with GRUB2 is going to pose a major hurdle for folks not comfortable with messing with script code.

So, yeah, it's going to get a lot worse before it gets any better.

---

### Post by Torquemada28 on 2009-11-03
> **sliketymo said:**
> We are all  sorry that you are having a rough go,but Ubuntu is not made to necessarily accommodate Windows 7,or any other OS for that matter. You have to take into account that they are competing system,not exactly siamese twins.It is but by the grace of developers,testers,hackers,and determined individuals of all stripes that such a thing as dual-booting is even possible,let alone works a large percentage of times.Some things just aren't made for each other.

If they're not made to dual-boot, fine.
That doesn't excuse releasing software you know will cause chaos with a large proportion of your userbase _WITHOUT WARNING THEM_.
I simply don't believe this issue was never encoutered during testing as so many people are affected now, it's apparently quite common. With that in mind, they released a distro complete with a bootloader that will stomp on the Vista/Win7 bootloader. No workarounds, no patches, no warning.
Sorry but that's f**ked.
Ubuntu has lost major brownie points as far as I'm concerned.

---

### Post by shredder12 on 2009-11-03
I had a similar problem too...
Even though right after installation grub2 was able to recognize my windows partition (XP) it didn't have any option to boot into ubunut.
The only options were 2 memory checks and 1 to boot into windows. 
I tried updating the grub which led to loosing the windows booting option too.
Then I finally found out that I couldn't find a vmlinuz file in /boot of the new installation which grub  needs to boot Ubuntu.
I had to do a fresh installation to get rid of the problem.. 
now, things are fine.

---

### Post by oldfred on 2009-11-03
While Ubuntu's new grub has lots of issues do not blame it if you deleted the win7 boot partition. Win7 for a clean install adds a boot partition. If it is an additional windows it will combine its boot into the existing windows so you can choose from the windows boot, but you then cannot directly boot win7 since its boot has been combined. 

It is not that difficult to add a boot stanza to new grub, it is just in a different place.

Grub2 info by ranch hand and many links to other grub2 info sites
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

reinstall grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Torquemada28 on 2009-11-03
> **oldfred said:**
> While Ubuntu's new grub has lots of issues do not blame it if you deleted the win7 boot partition.
Excuse me? Where exactly did I say I deleted any boot partition?
Are you saying that everyone who is now in dual-boot hell thanks to GRUB2, all deleted their boot partitions?
You're talking b0ll0cks.

> **oldfred said:**
> Win7 for a clean install adds a boot partition. If it is an additional windows it will combine its boot into the existing windows so you can choose from the windows boot, but you then cannot directly boot win7 since its boot has been combined.
If this is a known behaviour in Win7, why didn't the GRUB2 developers take this into consideration?
Again, if dual-booting with Win7 was shown to cause issues, regardless or whether it was a GRUB2 issue or a Win7 issue, the GRUB2 developers should've warned Canonical if they were unable to resolve the problem by the time 9.10 was released.
Failure to do so alienates users, as is evident now.

> **oldfred said:**
> It is not that difficult to add a boot stanza to new grub, it is just in a different place.

Over the last 72 hours I've become quite familiar with GRUB2 and can add an entry to /etc/grub.d/40_custom without a problem (if you'd read the whole thread, you'd have seen I've done this already) but complexity of configuration in GRUB2 isn't my complaint.
For all the people in the same boat as me, not one has resolved their issue by editing 40_custom or any other GRUB2 file.
GRUB2 kills the Vista/Win7 bootloader, period.
We can shift blame and responsibility onto Microsoft if you like but the blame game harms Ubuntu's market share far more than it does Microsoft's.

---

