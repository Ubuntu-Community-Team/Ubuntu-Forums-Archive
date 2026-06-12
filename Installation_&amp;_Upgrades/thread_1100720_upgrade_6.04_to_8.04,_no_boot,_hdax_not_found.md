---
title: "upgrade 6.04 to 8.04, no boot, hdax not found"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Earl54 on 2009-03-19
This computer was my sons.  He put several partitions on it, and it has Win98, SUSE (was unstable, now broken), and Ubuntu.  I upgraded from 6.04 to 8.04 using the online update.  When I tried to re-boot, it won't boot.  The last lines are:

[32.337608] build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core,c: v2.6:USB HID core driver
Done
   Check root= bootarg cat /proc/cmdline
   or missing modules, devices: cat /proc/modules ls /dev
   Reading all physical volumes.  This may take a while...
  ALERT! /dev/hda8 does not exist.  Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.[/COLOR]

I have tried changing the bootloader, which is from SUSE, to try other partitions, and the line ALERT! /dev/hdax always says that device x does not exist.  From the alert, it looks to me like the drivers in the kernel did not build properly and it won't access the hard drive.  I have no idea what to do.

I would do a fresh install and eliminate partitions, but there are files my kids want that I forgot to move to a /data partition (I know, backup, I preach it to my kids).  I can boot from the live CD, but can't read the files to move them because of permissions.

So, two options:
1.  Somehow work around permissions to move files and do a fresh install.
2.  Fix the upgrade.

If I need to do command line, I will need exact instructions, as I haven't done much there.

Sorry for the long post, but I was trying to fill in as much info as I could.

Thanks

---

### Post by meierfra. on 2009-03-20
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Therion on 2009-03-20
You can't upgrade from straight from 6.04 to 8.04 using the online Dist Upgrade option.

Do you have an USB thumb drive you could copy your data to?  Or an external USB hard drive (an iPod would work) you could use for the same purpose ?

Then, if you just want to copy the data off the drive so you can do a fresh install, you could boot with a LiveCD, open the Terminal and type in:```
sudo nautilus
```
Then browse to your data and copy it to the external drive.  

Once the copy is done, do a fresh install from the LiveCD using the entire drive for the installation.

---

### Post by Earl54 on 2009-03-27
Thank you both.  Sorry for the delay, I've been away and been ill.

I figured out how to start as root using sudo, with help from my son.  I got all the data moved, and burned to CD using the live disk, so the data is safe.  There is now a fresh install of Kubuntu that behaves very well.  I scrapped the extra partitions and the boot loader cleaned itself up so it only shows Kubuntu and that other OS that is hanging around still ;)

Back up and running.  And the wireless print server I was installing, which started the whole mess, was much easier to install on Kubuntu, for which it is not supported, than XP, for which it is.  Go figure.

---

