---
title: "Lenovo Ideapad Y710 CD/DVD Drive Missing After Linux Install"
date: 2008-09-21
forum: Hardware
---

### Post by darrylj9 on 2008-09-21
Recently, I partitioned my hard drive to install Ubuntu on my notebook. I've noticed that after the install my CD/DVD drive disappears in both the Windows and Linux partition. This problem has occurred with every linux OS I've installed.

I'm quite sure that the problem is the GRUB Bootloader. Using the option "acpi=off" in the menu.lst file works (only for Ubuntu) , however it makes the operating system very unstable. 

If*anyone*has any suggestions, I*would love*to here them.*
*
*
Thanks In Advance,

Darryl
*
Lenovo IdeaPad Y710
Optiarc AD-7560A (CD Drive)
Intel Core 2 Duo
2.00 GB RAM

---

### Post by phidia on 2008-09-21
You can check the laptop testing [page]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM") for reports and ideas on your laptop or a model that's similar-I didn't see your laptop listed.

Perhaps the best approach, though, is to use the Ubuntu wiki on [debugging acpi]("https://wiki.ubuntu.com/DebuggingACPI").

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

### Post by Tankerdog2002 on 2009-08-22
Just an update.

Jaunty broke some of our machine at the office. After we installed Ubuntu 9.04, none of the CD DVD optical drives were found in XP. They are completely gone. They are listed in the BIOS but are not listed in device manager. They will load and run at boot, but only at boot. They worked fine in Jaunty, but Ubuntu even blew the registry entries out of XP. It pissed our CIO off big time.

So we tried LILO. LILO works only for so long.....actually, LILO won't work for Jaunty. The first time you get a kernel update your machine will be toast.

This happened to 3 different machines of ours using Jaunty and LILO.

We posted bug reports. Nothing back from anyone.

Canonical has brushed this issue under the rug.

We had to dump Ubuntu and go back to Windows.

---

### Post by petitlou60 on 2009-10-18
Hello everybody,
 
I have made a lot of tests which show the following
 
1) each time that mbr is changed by any utilitiy DVD disappear  so vista MBR is absolutly needed to see DVD
 
2) on mixed configuration: linux (any) installed on another partition,grub installed in linux partition, linux entry added in bootmgr menu with esaybcd   DVD does not appears
 
So conclusions are
 
1) vista mbr code contains needed instructions to detect DVD
2) grub boot code reset this  and dvd dispappear
3) adding acpi=off in linux kernel line seems solve this issue but it is a very bad solution for battery life


i also tried option acpi=ht  dvd appears,energy handling is active but few seconds after there is a kernel failure but system continue to run apparently without problems 





Best regards

 
 
Best regards

---

