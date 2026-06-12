---
title: "MSI Wind &amp; UMPC - Your Thoughts"
date: 2008-05-15
forum: Hardware
---

### Post by victor9098 on 2008-05-15
Hi All,

I came to Ubuntu about 12 months ago now, dumped win-doh's completely and never looked back. Has been a great experience and love telling everyone about it...BUT...I am still very much a linux novice, I carry out 90% of my tacks via the GUI & usually end up here looking for help for the odd problem.

Now I do a lot of travelling on a motorcycle and I wanted a UMPC, but nothing seemed to fit my requirements, but now I have seen this MSI Wind:

[http://www.expansys.ie/d.aspx?i=168090](http://www.expansys.ie/d.aspx?i=168090)

I am very tempted to order one around next August/September. Yet my initial hesitation is that it does not have a cd-rom so will this mean a complicated install trying to boot from a USB stick or such?

Would love to hear some opinions on this or see if anyone has had similar experiences with other UMPC's

Thanks!

---

### Post by aysiu on 2008-05-15
Well, I believe it comes with an operating system already installed (Suse?), but if you want to install Ubuntu on it, yes, you'd need to do a complicated USB stick installation or get a USB external CD-ROM drive.

---

### Post by victor9098 on 2008-05-15
I would really prefer to stick with Ubuntu, have tried a few flavours of it and 2 other linux distro's, but for me Ubuntu is just so easy to use. Have installed on all my machines.

External usb cd-rom might be the easy option, provided it boots from it ;-)

---

### Post by cendant on 2008-05-16
What is so complicated about USB flash install? I use it only, instead of CD install as the speed of the installation is 3-5 times faster. 

Besides, you can keep LiveCD on the Flash stick in case you want to repair the system and install it to your friend

This works for Hardy and Gutsy:


[http://www.siberian.ws/blog/wp-admin/post.php?action=edit&post=3203](http://www.siberian.ws/blog/wp-admin/post.php?action=edit&post=3203)
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

---

### Post by cendant on 2008-05-16
That MSI Wind looks nice, doesn't it?

---

### Post by cendant on 2008-05-16
Ah, found another link

[http://www.technofreak.co.nz/isotousb.txt](http://www.technofreak.co.nz/isotousb.txt)

---

### Post by aysiu on 2008-05-16
> **cendant said:**
> What is so complicated about USB flash install? This is: ```
[Alternative 2] Prepare the USB stick manually

In short here's what you have to do:

    *

      Make the USB flash drive bootable using SYSLINUX.
    *

      Copy the contents of the Ubuntu CD to your flash drive (make sure you include hidden files/directories).
    *

      Rename the isolinux directory to syslinux and the file isolinux.cfg to syslinux.cfg
    *

      only for old versions of syslinux: Copy some files from sub-directories to the root directory and edit syslinux.cfg a bit.
    *

      Boot the computer from your USB flash drive.
    *

      only for the Alternate installer CD and pre-7.04 versions: Create a fake CD-ROM drive and mount the flash drive to /cdrom during the Ubuntu installation process.

Make your USB stick bootable with SYSLINUX

SYSLINUX is a boot loader that operates off an MS-DOS/Windows FAT filesystem. Most USB flash drives come with a FAT filesystem. Here's how you can add a SYSLINUX bootblock to your USB stick:

   1.

      Make sure that "syslinux" is installed. SYSLINUX is available for both Linux and MS Windows (the executable is in the archive under \win32\syslinux.exe). For more information check the SYSLINUX homepage: [WWW] http://www.syslinux.org/. On Ubuntu Linux, install it with:

    *

       sudo apt-get install syslinux mtools

   1.

      Attach your USB stick to your computer and mount it. This may happen automatically. If you are using Linux and it does not get mounted automatically, you can mount it by using a command such as mount -t vfat /dev/sda1 /mnt . Note the mountpoint (i.e. /mnt in the example. If you are using Windows, it should get mounted automatically. (If it doesn't your version of Windows is probably pretty old, and you'll need to install a driver for the USB stick first. Check the vendor's homepage.) Note the drive letter that Windows assigns to it (for example F:).
   2.

      Make the USB stick bootable. If you're using Linux and your USB stick is mounted as in the above example, use: syslinux -s /dev/sda1. If you are using Windows and the flash drive has the letter F: assigned to it as in the above example, use: syslinux -s -m F:
   3.

      You should see a new file called ldlinux.sys in the root directory of your flash drive. (Note that it is a hidden file, you might not see it in Windows Explorer; try dir /a F: from a command prompt). Now you can boot from your USB stick. Read on once you get a SYSLINUX message and a ""boot:"" prompt.
          *

            Regarding the IDE disk: When in the USB cradle, the disk is sda, whereas when I mount it in the Libretto as the primary IDE disk, it is of course hda. (I shot myself in the foot a couple of times because of this ...)

            The automatic mounting is a bit distracting at times. My recommendation would be to pumount any device you intend to do any low-level operations on, and then mount and unmount as root as necessary. -- [Ubuntu]Era

            Make sure to include the -m option with the Windows version of syslinux, to ensure that it copies a fresh ISOLINUX master boot record (MBR.) Otherwise the preexisting MBR may be used, which therefore may not point to your syslinux.cfg file.

Copy the Ubuntu CD to your USB stick

Copy the contents of the Ubuntu installation CD to your USB stick (i.e. all files and directories that are on the installation CD). Please do not copy an ISO image of the installation CD.

Make sure you also copy hidden files and directories (eg. ones with names beginning with a "."). In Gnome, press ctrl-H to see hidden files. In MS Windows you can use the following command, assuming that D: is your CD-ROM drive and F: is the USB stick:

xcopy /e /h /k d:\*.* f:
``` Compare that to burning an ISO: ```
   1.

      Download and install [WWW] Infra Recorder, a free and open source image burning program.
   2.

      Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog pops up.
   3.

      Open Infra Recorder, and select the 'Actions' menu, then 'Burn image'.
          *

            infrarecorder2.png
   4.

      Select the Ubuntu CD image file you want to use, then click 'Open'.
   5.

      In the dialog, click 'OK'.
```

---

### Post by cendant on 2008-05-16
But it is faster!

What about?

1. Install syslinux
2. Download the script IsoToStick
3. Format the Flash drive as FAT
4. run the script

and then:

you can take the tiny Live Ubuntu stick with you anywhere and install Ubuntu on Friend's computers - make them happy (or not :lolflag:)

---

### Post by victor9098 on 2008-05-16
Yip, I like the look of the MSI Wind too.

Found these links for more info:

[http://www.expansys.ie/d.aspx?i=168086](http://www.expansys.ie/d.aspx?i=168086)
[http://www.tweaktown.com/news/9377/exclusive_msi_wind_notebook_photos_here/index.html](http://www.tweaktown.com/news/9377/exclusive_msi_wind_notebook_photos_here/index.html)
[http://gizmodo.com/365720/msi-wind-laptop-to-make-eee-pc-cry-eeek](http://gizmodo.com/365720/msi-wind-laptop-to-make-eee-pc-cry-eeek)

Seems to tick all the boxes for what I want, as I said my only hesitation comes from having to do an USB install, but hopefully an external CD/DVD drive will do the job.

What is not clear on the expansys website is that most other websites claim the XP version is higher spec the the Linux (more RAM, better battery) but they list no difference. Might send an email ;-)

Have a 1GB USB stick, might practice what cendant was saying...though may lose a few friends :-D

---

### Post by victor9098 on 2008-05-16
Email sent ;-)

---

### Post by kshsj777 on 2008-05-24
I can't wait to get the MSI Wind if it turns out to be as good as it claims to be.  

I still haven't decided if I want to go to all the trouble of doing a USB install of Ubuntu or just getting an external hard drive (I am going to want to play DVDs and maybe install one or two things with a CD, and it would make transferring my music easier I think.)

---

