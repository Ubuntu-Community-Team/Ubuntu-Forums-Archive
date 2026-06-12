---
title: "Problems Dual Booting Win 7 &amp; Ubuntu"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by mealies on 2009-05-07
Hi Guys

I have searched for answers but have got confused from all the posts i have found.

I cannot boot into win 7 from GRUB.  It states BOOTMGR is missing CTRL-ALT-DEL.

Now my hard disk was already partitioned so i installed Win 7 first.  it has a boot partition 100mb and the normal partition.  I then installed Ubuntu and when at the final screen selected GRUB to be installed on the vista Boot partition.

What do i need to do to fix this?

Thanks

Andrew

---

### Post by Senior_X on 2009-05-07
Hi mealies
I am certainly not a guru, but I have been dual booting Linux and Windows on laptops for years now. You certainly did right in installing windows first. Your problem might be your (lack of??)partitions. The point is: if you have got only one primary partition, it will be impossible - I guess - for GRUB to distinguish between windows and linux, and as you were in the process of installing linux, you cannot really blame GRUB - sorry. My advice: if possible, reinstall. You can make up to four primary partitions, and you are free to install four different operative systems - GRUB will give you the choice to start any of them at boot time. When you install Linux and grub, there will be an option of installing other operative systems, keep an eye on that option and  just choose the right partitions for the operative systems you wish (in yr case it will be win7).It does not matter which tool you use for partitioning- use the one you are most comfortable with.  Maybe someone else can give you a workaround how to boot windows now, but if you are sure that you have got only one primary partition on yr harddsk  (use e.g. a low level tool like fdisk on yr linux system to find out, try 'man fdisk' from a terminal  to learn more if you are new to that), my advice would be to start from scratch and do the right partitioning from the beginning. Please do also wait for "guru answers", there are wiser people like me around.  I helped you along as I was able to. 
Bye

---

### Post by gamblor01 on 2009-05-07
No need to reinstall everything unless you accidentally deleted the partition where Windows was residing and then installed Ubuntu using the entire hard drive.

Boot up into Ubuntu and then run the command

```

sudo fdisk -l

```and paste the output here (please surround it in code tags to make it more readable).  Then open the file /boot/grub/menu.lst and paste its content here as well (preferably in a code or quote tag).

I just want to verify that everything is setup properly with grub in order to boot Windows, though I don't think your problem has anything to do with grub -- I'm pretty sure that grub is properly loading up your Windows partition and *THAT* is where the error is.  I can only assume that Windows 7 is similar to Windows Vista?  I have never used either but a simple google search for "BOOTMGR is missing CTRL-ALT-DEL" returned this result for Vista which looks useful:

[http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php](http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php)


I'm guessing it will probably overwrite grub with the NT bootloader in your MBR so we may have to reinstall grub afterwards, but that's easy.

---

### Post by caljohnsmith on 2009-05-07
> **mealies said:**
> I then installed Ubuntu and when at the final screen selected GRUB to be installed on the vista Boot partition.

Unfortunately, that's a big mistake; if you install Grub to the Vista NTFS/FAT partition, Grub is installed to the boot sector of that partition and the partition will no longer be mountable or readable. If you would like help fixing it, it would help to first get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by gamblor01 on 2009-05-07
> 

Quote:
                                                                      Originally Posted by **mealies**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7230539#post7230539")                 
                 *I then installed Ubuntu and when at the final screen selected GRUB to be installed on the vista Boot partition.*
                                 
Unfortunately, that's a big mistake; if you install Grub to the Vista NTFS/FAT partition, Grub is installed to the boot sector of that partition and the partition will no longer be mountable or readable.
That cannot be true.  My system originally had only one hard drive in it running XP [so it's /dev/sda or hd(0) ].  Over the years I have added a second hard drive and I now quadruple boot XP, Fedora, Ubuntu, and Slackware.  Ubuntu controls my grub and I installed it on hd0, meaning it smashed the MBR -- the NT bootloader is no longer there.  I can guarantee you that I selected the option in the final step of my ubuntu installation to install grub to hd(0).

My system works fine.

---

### Post by caljohnsmith on 2009-05-07
> **gamblor01 said:**
> That cannot be true.  My system originally had only one hard drive in it running XP [so it's /dev/sda or hd(0) ].  Over the years I have added a second hard drive and I now quadruple boot XP, Fedora, Ubuntu, and Slackware.  [COLOR="Red"]Ubuntu controls my grub and I installed it on hd0[/COLOR], meaning it smashed the MBR -- the NT bootloader is no longer there.  [COLOR="Red"]I can guarantee you that I selected the option in the final step of my ubuntu installation to install grub to hd(0)[/COLOR].

My system works fine.
Yes, we would expect your system to work fine if you installed Grub to (hd0), which is the MBR of the HDD. Mealies specifically said that he/she installed Grub to the Vista partition, not (hd0) or the MBR like you did:
[QUOTE=mealies]I then installed Ubuntu and when at the final screen [COLOR="Red"]selected GRUB to be installed on the vista Boot partition[/COLOR].[/QUOTE]
You can do that by selecting Grub to be installed to something like /dev/sda1 instead of (hd0) or /dev/sda. So if mealies truly installed Grub to his Vista partition like he claims to have done so, his Vista partition will not be mountable/readable until he fixes the boot sector.

---

### Post by gamblor01 on 2009-05-08
> 
Yes, we would expect your system to work fine if you installed Grub to (hd0), which is the MBR of the HDD. Mealies specifically said that he/she installed Grub to the Vista partition, not (hd0) or the MBR like you did


Ah I see what you mean.  The default option is to install to (hd0) so yes, I agree -- if it was changed to install on /dev/sda1 (assuming that is the partition where Windows resides) then it would indeed hose the boot sector on the Windows partition.

So which is it mealies?  Do you know if you installed grub to (hd0) or /dev/sda1?

---

