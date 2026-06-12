---
title: "Samsung Series 7 - glitch in suspend/hibernate"
date: 2012-09-10
forum: Hardware
---

### Post by clockworktri on 2012-09-10
I am running 12.04 on Samsung Series 7 17.3" Notebook (NP700Z7C-S01US). I am using the fix for suspend posted [here]("http://ubuntuforums.org/showthread.php?p=11926504"). It seems to work ok except that suspending disables my wireless. I cannot re-enable it, and have to reboot the computer to get it back.
Does anyone have any help for advice for me?

---

### Post by mauricioDorame on 2012-09-14
Hi clockworktri, I have the same laptop but I cant install ubuntu, could you please tell me how you did it?? 
I tried installing from USB and CD version 12.04 and it didnt work. I got to it to work using wubi but after a few restarts it wont load any more. 

PLEASE help me.
Best regards, 
Mauricio

PS. Sorry for the spelling english is not my first language :D

---

### Post by russ2001 on 2012-09-14
I'm having the same problem. Have tried variou suspend fixes but just get more errors.

---

### Post by clockworktri on 2012-09-15
> **mauricioDorame said:**
> Hi clockworktri, I have the same laptop but I cant install ubuntu, could you please tell me how you did it?? 
I tried installing from USB and CD version 12.04 and it didnt work. I got to it to work using wubi but after a few restarts it wont load any more. 

PLEASE help me.
Best regards, 
Mauricio

PS. Sorry for the spelling english is not my first language :D

I installed from CD, so I'm not sure why you couldn't. Only thing I can think to try is re-downloading the iso and burning a different copy. And maybe make sure you're hitting all the right steps? ([http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/))

As for getting the system to work once it's installed, I found this awesome guide:
[http://wiki.colar.net/ubuntu_12_04_on_samsung_series_7_chronos_laptop](http://wiki.colar.net/ubuntu_12_04_on_samsung_series_7_chronos_laptop) 
It has practically everything. For a few other tweaks I referred to these sites: 
[http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/](http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/)
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)
[http://bgrande.de/chronos7.html](http://bgrande.de/chronos7.html)
[http://forum.notebookreview.com/samsung/672233-ubuntu-12-04-working-great-chronos-7-np700z5b.html](http://forum.notebookreview.com/samsung/672233-ubuntu-12-04-working-great-chronos-7-np700z5b.html)

Just remember that the how-to guides (first and second links) are referring to an NP70035B-S01UB and NP700Z5B-S01U, respectively, which are 15.6" Series 7s. If you have the 17.3 inch, like me, you will have Nvidia Optimus instead of the ATI Radeon driver. So skip the steps referring to it, and instead install Bumblebee (follow the directions of the first poster here: [http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work)).

I did have to do a clean install three or four times before I got the whole process right (may have been being over-careful there...) but it works fine now (except for this suspend issue). I'm liking it a lot!

Good Luck!

---

### Post by caliber556 on 2012-12-01
A very simple quide to install 12.10 on the Series 7 17" (NP700Z7C-S01UB  - Best Buy model) since everything works out of the box:

1. Replace the horribly slow HDD with the SSD (a must - they are cheap now).

2.  Unfortunately (not really) the OEM Windows 8 could not be transferred  to the SSD due to some EFI boot issues and the distribution CD/DVD is  not available at this time: brilliant on Microsoft's behalf. Dual boot s  nice, but I doubt anyone would miss Windows 8 "innovations".

2a. If  you are installing Ubuntu on the original HDD (after shrinking the Windows  partition), you will need to fix it, as Grub messes up Windows EFI  initially. 100% automatic repair with Boot Repair tool (choose  "Recommended repair") [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Windows 7 is not EFI-compatible (didn't care to research more) and good luck downloading and installing proprietary Samsung drivers - the joys of non-OEM Windows installation. Not worth it IMO.

2b. In any case disable the Secure Boot in BIOS (so it won't check against the oh so important OEM Windows signature), leave it at UEFI and change the boot sequence, so the CD boots first - doesn't really matter with an empty SSD, as it is not going to find any boot partitions there.

3. SSD: wipe it completely deleting all old partitions.

4. Boot from the Live DVD (in UEFI mode). When the installer asks you about partitioning, do the following ("Something else"):
- sda1: 100M (I suspect size doesn't matter, but better safe than sorry) EFI boot partition
- sda2: standard (Ext4?) partition for "/" - the rest of the SSD
- sdb1 (8G "express cache"): swap partition
Choosing the standard installation (whole disk) works too, but it won' utilize the little internal SSD as swap - a least initially.

5.  Everything works out of the box. Graphics even w/o Bumblebee. However  Bumblebee greatly improves power consumption and lowers the core  temperature 10 or so degrees (Celsius). I installed the minimal version  w/o the Nvidia drivers. Doesn't really matter - Bumblebee is solid and  is not causing any problems. The instructions can be found here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

6.  As far, as the "user experience" is concerned, Suspend/resume works out of the box (minus the ACPI issue - see below). 

7. So is the trackpad - no fixes necessary though you may play with synclient to tweak various settings. The default ones were enough for me - adjusted everything else using the Mouse tool in the standard System Settings. It is not as clever,  as Mac's detection of proper two-finger scroll since people rarely move  their fingers 100% horizontally or vertically. I disabled the horizontal  scroll for that reason - diagonal scrolling. It'd also be nice (to have a setting) to ignore the second finger  unless dragging - the way it works on both Mac and Windows since people  (at east myself) tend to keep it in the lower left corner ready to  press.

8. Samsung-specific support (voria repo) - namely samsung-laptop  package is not available for 12.10 at he moment, so don't install it to  fix the F-keys. It breaks them instead. F2-F8 work anyway out of the box and I am not  missing the adjustable keyboard backlight: the standard automatic one is  enough for me. Here is the repo link:  [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa). You'd need samsung-laptop and  samsung-tools. Play at your own risk.

**9. The only real issue:**  serious, but not enough to make me put back the original HDD and return  the notebook to Best Buy. This is the infamous ACPI/kworker kernel bug  affecting many newer notebooks, not just Samsung series 7. I posted my  observations here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793). Not sure  how to convey it to the Linux kernel team, but it is not an XFS  (filesystem) bug. That wrong assignment is probably preventing it from being fixed for several months over several Ubuntu releases.

There is  no fix (at the moment). Just keep rebooting, waiting for the kworker to  calm down and "helping" it by jerking the power cord in and out. No  other "solution" mentioned in that thread worked for me (pci=noacpi,  etc.). This issue also makes Suspend unusable though it formally works  in 12.10 w/o any fix scripts. The Core 1 utilization goes to 100%  upon Resume and stays there. I noticed that if the kworker misbehaves  for whatever reason: on its own or after resume, it is very hard to get  it back to normal - requires a number of restarts. Typically restarting  with alternating kernel versions (results of updates) helps. Not sure  why, like some kernel flag is being reset. I am not a system programmer,  so can only speculate about it. 

When kworker is calm, the core  temperature stays between 45-50 degrees Celsius (no fan engaged) and the battery  life is about 5 hours - not the best in class, but very respectable.

---

