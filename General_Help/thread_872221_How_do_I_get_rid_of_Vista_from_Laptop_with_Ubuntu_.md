---
title: "How do I get rid of Vista from Laptop with Ubuntu already installed?"
date: 2008-07-27
forum: General Help
---

### Post by cchester on 2008-07-27
Hello,

I have been running a dual boot of Ubuntu and Windows Vista on my laptop since I first got it and now I am wanting to get rid of Vista and the HP Recovery Partition all together so I can have Ubuntu take advantage of the whole hard drive.

How would I go about doing this?

Ubuntu mounts the Windows Vista partition automatically and the HP Recovery partition so I would need to somehow get it to stop doing this.

Then I need to know if it is ok to get rid of the HP Recovery partition. I have made the HP Recovery DVDs through the HP Recovery Dvd Software. So if I do this will I be able to still put the system back to original settings with these disks if I delete the partition? Just in case I find the need to put Vista back on the machine.

Once I know all of the above do I just delete the partitions I don't want and then resize my Ubuntu partition to take advantage of the space? Then do I just erase the Vista option in grub so it only shows Ubuntu? If so how do I do this?

I am able to do what I want in Ubuntu and don't have a need for Windows Vista on my machine and anything like Office 2007 which I have to have for school I am running under Virtual Box with Windows XP. This is why I am wanting to do this.

I have a HP Pavilion dv9700 series laptop that I am running on just so you know. Everything works like the web cam, wireless card, sound, video, etc.

Thanks for any help on this.

---

### Post by Rocket2DMn on 2008-07-27
Hey, have a look at [uhelp]community/HowToRemoveWindows[/uhelp] which explains exactly what you need.
If you have your recovery DVDs, you should be OK to delete your recovery partition.  If you are not comfortable with this, you can keep it have it not automount by adding "noauto" to the entry in /etc/fstab

If you have any problems with that guide, please let me know and I will modify it accordingly.

---

### Post by cchester on 2008-07-27
Thanks for the help and I will check the link out.

---

