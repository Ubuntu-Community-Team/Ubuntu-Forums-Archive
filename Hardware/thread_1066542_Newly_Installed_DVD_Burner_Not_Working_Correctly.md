---
title: "Newly Installed DVD Burner Not Working Correctly"
date: 2009-02-11
forum: Hardware
---

### Post by g-t-c on 2009-02-11
[SOLVED.  Since I couldn't figure out anything else that was wrong, I took out the Sony DRUV202A, replaced it with a new Lite-On iHAP322-08.  The Lite-On works great.]

Greetings:

This is a Feisty box that has been running like a champ for 14 months. The LG DVD/CD burner I used to clean install Feisty on the system was in need of retirement, so I just replaced it with a new Sony DRUV202A. System BIOS sees it just fine. The Device Manager in Ubuntu identifes the Sony just fine. 

However, when I mount a DVD data or DVD video disc, it's recognized as a Blank Disc. Same with a previously-written data CD. If I click on the icon an empty file window is shown.  Strangely, when I check the Properties of the mounted disc, it does show the accurate MB/GB used. 

The other odd thing is that NeroLinux 3 can correctly identify what's on either DVD or CD discs. Nero can also burn images and compilations to a blank disc. The newly burned CDs are fine. The DVD videos that Nero completes successfully cannot be read by anything else in the house.  If I mount the newly burned CD disc, Gnome will identify it as a blank disc with nothing on it. 

No other OSes on this system for me to test the burner on -- I built it last year to run Feisty. This is the first piece of hardware I have had to switch out on the system, what do I need to do?  The fstab is below.

Thanks in advance,
George


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc890439-b959-4f56-b65d-c866c29d296c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=13c928e9-c239-434b-8e00-b81243153675 /home           ext3    defaults        0       2
# /dev/sda5
UUID=30e3f4f5-a21d-40df-870e-d75e91d8e90c /usr            ext3    defaults        0       2
# /dev/sda6
UUID=011c539a-b755-45cd-b879-6df559134aa7 /var            ext3    defaults        0       2
# /dev/sda8
UUID=ab768628-b96b-49dc-a078-e9978a709e09 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by g-t-c on 2009-02-11
In case this helps, the firmware version on the DRUV202A is 1.6.  I'd check for a later version, but Sony requires a check utility that's Windows only, and it doesn't work correctly via Crossover.

---

