---
title: "Double ubuntu dual boot"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by andre459 on 2008-12-27
The aim was to have two ubuntu installations on two hard drives. One 64bit and other 32bit. The HDD with 64bit system is removable, ie not always attached.

The 32bit was installed first and was working fine.
When I attached the 2nd HDD and installed 64bit Ubuntu on it, it messed up my 32bit system. Booting from 64b works fine and also when I boot my 32b system from grub on the 64b HDD. But when I detach the 64b HDD and booted my original 32b system, I get an "Error 21" from grub, which means device not found.

I checked /dev on the original 32bit system and a lot of devices were missing, incl hda, hda1, hda2 etc. In 64b installation I have > 700 items in /dev, but in 32 I have < 100 left.

Clearly the 64b installation did something on the original 32b system. Is there a way to fix the 32b system without having to reinstall?

Any advice will be much appreciated.

---

### Post by Knatchwa on 2009-01-03
I know it has been done before, but seeking a full tutorial, on setting up 9.04 on a separate hard drive with 8.10 on the main drive has not come about with much advice. I know it is possible but trying to figure it out, as far as 64 and 32 that is a definite challenge, I would think you could use Virtual Box for that setup.  Well looking forward to any information that could be shared on that point.

---

### Post by DeMus on 2009-01-03
> **andre459 said:**
> The aim was to have two ubuntu installations on two hard drives. One 64bit and other 32bit. The HDD with 64bit system is removable, ie not always attached.

The 32bit was installed first and was working fine.
When I attached the 2nd HDD and installed 64bit Ubuntu on it, it messed up my 32bit system. Booting from 64b works fine and also when I boot my 32b system from grub on the 64b HDD. But when I detach the 64b HDD and booted my original 32b system, I get an "Error 21" from grub, which means device not found.

I checked /dev on the original 32bit system and a lot of devices were missing, incl hda, hda1, hda2 etc. In 64b installation I have > 700 items in /dev, but in 32 I have < 100 left.

Clearly the 64b installation did something on the original 32b system. Is there a way to fix the 32b system without having to reinstall?

Any advice will be much appreciated.


It looks to me you ask a question and give the answer yourself already.

You installed the 32 bit system on drive A, then the 64 bit system on the removable drive B.
With installing the 64 bit system you placed Grub on drive B, the removable one. When this disk is removed there is no Grub so the PC can not boot, ergo an error message.

Install the 32-bit system and place his (her?) Grub on the same disk. (A)
Then install the 64 bit system and also place this Grub on the 32-bit disk. (A)
That way you will always be able to boot the 32-bit system.
To boot the 64-bit system you only need to connect drive B,re-boot and choose that install in Grub.

DeMus

---

### Post by caljohnsmith on 2009-01-03
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

