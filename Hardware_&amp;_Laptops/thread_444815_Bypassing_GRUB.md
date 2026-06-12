---
title: "Bypassing GRUB"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by AbtZ on 2007-05-15
Hello all,

I'm thinking about switching from using Windows XP to Ubuntu. Ubuntu seems like a very nice distro, and I would like to learn more about how linux works in general. My biggest problem with this is that it seems that GRUB seems to have issues with my desktop computer.

Here's the deal:
I boot from the Ubuntu CD and install it on an empty 120GB Seagate drive, using the "guided, use entire disk" option (I would prefer to specify the partitons myself, but GRUB has given me problems with it in the past, too). The installation proceeds without any issue, and then I reboot the computer. However, during boot when GRUB tries to load I get something called  "error 22", and a blinking cursor, but am unable to do anything. I've found that this error message means "no such partition", and I've read in forums of other people getting it -- but this is *after* manually deleting Ubuntu (or whatever Linux distro they've been using). I get it after a *fresh* install... and it's happened several times before, though I was able to boot windows again by fixing the mbr with a WinXP CDROM -- but this doesn't help me if I want to run Ubuntu.

Now to my question:
Is there anyway I can just ditch GRUB altogether? I don't need it, I don't like it, and configuring it is not user-friendly or easy at all. My BIOS let's me choose which hard drive I want to boot from, and since I have my XP installation on a different drive than Ubuntu, just specifying which drive I wish to boot from should let me load my preferred OS. I was fooling around with SuSE  a while ago, using this method, and it worked fine for me.

If this is not possible, is there any other way for me to solve the problem?

Here are the relevant system specs:
Mobo:[ Asus A8V Deluxe ]("http://www.asus.com/products.aspx?l1=3&l2=15&l3=68&l4=0&model=238&modelmenu=1")
Hard drives: 1 Seagate 320 GB SATA drive
1 Seagate 400 GB SATA drive
1 Seagate 250 GB IDE drive (set to cable select, connected to master socket on cable 1, nothing on slave socket)
1 Seagate 120 GB IDE drive (set to cable select, connected to slave socket on cable 2, where DVD-drive is on master)

Thanks,
eddie

---

### Post by nereid on 2007-05-15
You will need a bootloader, whether you use GRUB or Lilo is your choice. Linux can't boot itself without a bootloader. Windows also uses one but you don't see it ;)

Maybe you would like to take a look at Lilo.

Have you tried to reinstall GRUB into the mbr?

---

### Post by AbtZ on 2007-05-15
Hi, nereid

No, I haven't, since I figured that since it didn't work after being installed initially, it wouldn't work after being reinstalled either. Also, I have no idea how to do it.

Neither do I know how to install Ubuntu with LiLo...

I've been thinking about installing Ubuntu with all other harddrives disconnected. That way GRUB will have to install itself on my "Linux drive" and so would not interfere if I decide to boot from my "Windows drive" instead -- or so I hope.

---

### Post by nereid on 2007-05-17
There are ways to use the Windows bootloader instead of GRUB or Lilo. This means that you have to install GRUB or Lilo on another mbr and the Windows bootloader will refer to either GRUB or Lilo. I'm sorry but I can't really help you here, because I haven't done anything with the various bootloaders.

---

### Post by Ken_Lewis81 on 2007-05-17
GRUB may think it should get its booting information from a partition it believes to be on your hard disk with Windows on it.  If it's been installed to look at "(hd0)" -- GRUB's terminology for your first hard disk-- then it will be searching your SATA disk for its next-stage booting files.

You will probably need to reinstall GRUB to your 120GB disk, telling it exactly which disk it should be loading for.  Perhaps putting [GRUB4DOS](http://grub4dos.sourceforge.net/) in your Windows Partition will enable Ubuntu to work okay.

take care.
Ken.

---

### Post by AbtZ on 2007-05-23
Hey,

Thanks for the responses. I managed to solve my problem, and the short of it is this: 
 
I tried to do as I stated before -- reinstalling Ubuntu with only the 120 GB disk connected. This ensured that  GRUB was installed on that same disk, and not someplace else. After reboot GRUB worked just fine, and I got into Ubuntu, so I tried connecting the other disks. This did not work, and after a lot of rummaging about in both my computers software and hardware I discovered that the guy who had installed the hard disks in my computer when I bought it had set the pins on my Windows drive to Master (as opposed to Cable Select), for some reason. I had later moved this disk and put it on the Slave port -- and this wasn't a problem until I connected my soon to be Linux-drive to the Master port, after which hardware conflicts arose. After a lot of troubleshooting I discovered this, and set the Windows disk to Cable Select as well. 

Finally, I used Super Grub Disk (an excellent guide to the program can be found [here)]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") to update GRUB and now I can choose from the GRUB menu which OS I wish to load, without a problem.

However, I still don't know what spawned the original "no such partition" problem to begin with -- since I didn't start moving around the disks until I read somewhere that GRUB preferred to be on the Master disk for some reason.

Cheers,
//eddie

---

