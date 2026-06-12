---
title: "Lenovo Ideapad Y710 CD/DVD Drive Missing After Linux Install (Problem With GRUB)"
date: 2008-09-21
forum: Hardware
---

### Post by darrylj9 on 2008-09-21
Recently, I partitioned my hard drive to install Ubuntu on my notebook. I've noticed that after the install my CD/DVD drive disappears in both the Windows and Linux partition. This problem has occurred with every linux OS I've installed.

I'm quite sure that the problem is the GRUB Bootloader. Using the option "acpi=off" in the menu.lst file works (only for Ubuntu), however it makes the operating system very unstable. 

If anyone has any suggestions, I would love*to here them.

Thanks In Advance,

Darryl
 
Lenovo IdeaPad Y710
Optiarc AD-7560A (CD Drive)
Intel Core 2 Duo
2.00 GB RAM

---

### Post by alex.radian on 2009-02-17
Hi,

I bought this model (Lenovo Ideapad Y71O) in April 2008. It comes with Vista but I formatted all HDD & installed Ubuntu 8.04 (don't install ubuntu 8.10: it has a video problem with ideapad).
The only problem is a cd/dvd mount: after installing ubuntu, you have to install the LILO (boot loader) instead of GRUB - lilo is in text mode, but once executed, Ubuntu starts in normal (graphic) mode and you'll have auto recognition of any CD/DVD inserted in drive
Video is fine, ubuntu works in full resolution (1440x900, WXGA+)
As software, I recommend the following:
  - crossover (runs windows applications & games)
  - gimp (image editor, like adobe photoshop)
  - cheese (webcam viewer)
  - sun java 6
  - virtual box (runs virtual machines, like in VMWare)
  - mozilla firefox 3 (installed by default)
  - evolution messenger: email client (installed by default)
  - wine (runs windows applications)
  - monodevelop (visual programming in C#, a clone of visual studio .net)
  - eclipse (visual programming in c# and c++)

---

### Post by andso on 2009-03-29
bonjour,
add acpi=off in  /boot/grub/menu.lst
[http://www.linuxquestions.org/questions/linux-newbie-8/cddvd-rom-not-working-in-ubuntu-8.04-on-lenovo-ideapad-y710-686982/page2.html](http://www.linuxquestions.org/questions/linux-newbie-8/cddvd-rom-not-working-in-ubuntu-8.04-on-lenovo-ideapad-y710-686982/page2.html)

---

### Post by crazylife on 2010-04-26
Has anyone installed Lucid on a Lenovo Y710?  I am interested to know if the CD drive recognition issue with the Y710 after Linux is installed finally goes away with the release of Lucid.  The issue has plagued me in Jaunty and Karmic.  At least in Jaunty I could easily modify grub with the acpi=off solution.  Karmic Grub2 is a whole new can or worms.

I think if Lucid does not support the CD drive on the Y710 I will need to either roll back to Jaunty or buy Windows 7.  I want to watch DVD's again on my laptop.

:confused:  Thanks, Pat

---

### Post by crazylife on 2010-04-26
I just completed the realease candidate upgrade to Lucid per [http://www.ubuntu.com/getubuntu/releasenotes/1004overview](http://www.ubuntu.com/getubuntu/releasenotes/1004overview).  It did not help.  It still gives the error unable to mount cdrom0  mount: special device /dev/scd0 does not exist.

---

