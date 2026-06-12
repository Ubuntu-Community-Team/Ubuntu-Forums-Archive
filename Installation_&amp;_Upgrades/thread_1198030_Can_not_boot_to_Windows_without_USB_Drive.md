---
title: "Can not boot to Windows without USB Drive"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by shakahi on 2009-06-26
Hey, everyone.

I just installed the latest desktop version of Ubuntu on my Dell laptop. Ubuntu was installed on a 8 G removable USB drive and now I can't boot to Windows on my internal HD without the USB drive. What can I do to move the boot partition to my internal HD so that I can boot up in Windows without the USB drive?

Thank you.

---

### Post by lindsay7 on 2009-06-26
Which version of windows are you running. I think you just need to reinstall the mbr to your hard drive.  Do you have your windows install disk with you?

Here is the info for xp,

[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)


Here is the info for vista,

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Herman on 2009-06-27
The problem is you allowed the Ubuntu installer to install the pointer for GRUB to the MBR in your first hard disk. When the USB disk is plugged in, you have no problems, because the pointer (IPL or 'stage1' file), can point to GRUB and find it, (in your USB). From there, GRUB can boot either Ubuntu or your other OS, in your computer.
When the USB is not plugged in, your MBR tries to point to GRUB in the USB, but of course it can't find it because it isn't there.

One solution, as the poster above is suggesting, would be to re-install the pointer for your boot loader in whatever operating system you have in your Laptop to MBR.
Then you would need to also install Ubuntu's GRUB to MBR in your USB.
You would then be able to boot your laptop as normal.
To boot your USB, you would need to do a BIOS boot, [How I boot from my BIOS]("http://members.iinet.net.au/%7Eherman546/p1.html#How_I_boot_from_my_BIOS_with_my_F12_key"). That will be slightly less convenient than just booting it right up from a boot loader menu though. You will be swapping one problem for another. Your other operating system will be easy to boot, but then Ubuntu will be harder to boot.

Another idea would be to make a 'dedicated GRUB partition', which is a very small partition anywhere in your laptop's hard drive. [How to make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_"). With a 'dedicated GRUB partition' you'll be able to boot anything, anytime, easily. 
WARNING: You might learn things if you keep playing with Linux and GRUB.

Regards, Herman :)

---

### Post by shakahi on 2009-06-27
Thanks for the responses. I did recreate the MBR using one of the articles quoted above and I'm back to "normal". 

I did back up everything before installing Ubuntu, but should have reigned in my enthusiasm and done a little more research.

I'll install Ubuntu again -- but this time I will take my time and do lot more reading. Thank you both.

---

