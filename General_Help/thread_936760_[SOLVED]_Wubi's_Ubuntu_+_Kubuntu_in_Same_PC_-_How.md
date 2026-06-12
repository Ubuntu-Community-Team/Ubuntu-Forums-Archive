---
title: "[SOLVED] Wubi's Ubuntu + Kubuntu in Same PC - How?"
date: 2008-10-03
forum: General Help
---

### Post by prabath_fun on 2008-10-03
Hi,
I want to install Kubuntu 8.04 also with Wubi without removing Ubuntu 8.04 installed with wubi. That is, I need both Ubuntu and Kubuntu with seperate Virtual Disks (Dont want to mixup KDE and GNOME applications). Is it possible? Please update me.
With Advanced Thanks,
Prabath

---

### Post by ago on 2008-10-03
no need to have separate virtual disks. Install Ubuntu, then install kubuntu-desktop. Once you login you will be able to select whether to use the gnome or the kde desktop in the Options.

Wubi 8.10 is now recommended.

---

### Post by prabath_fun on 2008-10-03
Hi ago,
   Thanks.
   But, If I do install kde desktop, both gnome and kde applications will be available in any one boot, right? I am not looking such boot up. 
   Wubi 8.10 is now recommanded - means. I should have Kubuntu 8.10 / Ubuntu 8.10 CD, right? I have 8.04 CD's only. Or, Is it possible to install Kubuntu / Ubuntu 8.04 with Wubi 8.10!
Please clear me.
With Thanks,
Prabath

---

### Post by ago on 2008-10-03
Wubi 8.10 requires 8.10 ISOs, it cannot use 8.04 ISOs (and vice versa).
For KDE 4 the version on 8.04 was the very first release, and you will probably have a much better experience with 8.10 (which is now in beta).

And yes if you install Ubuntu and Kubunu in the same setup, you will be able to access the applications of both desktops. This will make the applications menu a bit overcrowded but other than that:

1) you gain the convenience of booting either system at login (as opposed to having to reboot to change the desktop)
2) the fact that you can use apps from the other desktop is not necessarily a bad thing, many users may want to use amarok even if they are on gnome, or gimp in KDE...
3) having two desktop environments in the same installation takes far less space than having 2 dedicated installations
4) setting up wubi to triple boot is not trivial and not supported

---

### Post by prabath_fun on 2008-10-03
Hi ago,
  Thanks for your tips.
  I will install the KDE in Ubuntu itself. Can you help me by providing the list of packages to be installed to get only KDE Desktop. No KDE applications, I want to install. I will install one by one latter.

With Thanks,
Prabath

---

### Post by monkeystuner on 2008-10-03
After you install Ubuntu, just go to Applications > Add/Remove and search for KDE then check the box next to the KDE Desktop, a pop up will tell you about some other files that are required, just hit ok and they will be added then apply and your done

---

### Post by prabath_fun on 2008-10-05
Hi,
  How to add KDE CD to get KDE desktop packages from CD? I tried from software sources. But, While installing, Synaptic is not referring the CD. Please help me.

Is it true that live CD cannot be used for this purpose? how can i extract the packages from live cd. 
With Advanced thanks,
Prabath

---

### Post by prabath_fun on 2008-10-07
Hi,
  I got information that Live CD cannot be used for installation of KDE in Ubuntu, from other thread. 
   Thanks for all your contributions.
 With Thanks,
Prabath

---

### Post by prabath_fun on 2008-10-08
[FONT="Comic Sans MS"]Hi,
   Since I have Live CD only, Please show me the direction to install Kubuntu in another virtual drive with Wubi and have seperate Grub/bootloader (Exact name I dont know for windows) entries. That is WindowsXp, Ubuntu, Kubuntu.
   Please update me.
With Thanks,
Prabath[/FONT]

---

### Post by ago on 2008-10-08
Rename ubuntu to ubuntu-gnome then run wubi again.
Then to boot into ubuntu-gnome you will have to create a section in ubuntu\disks\boot\grub\menu.lst similar to the main one but using loop=ubuntu-gnome and comment out hidemenu.

---

### Post by prabath_fun on 2008-10-08
Hi ago,
   Thanks for your updates.
   Without renaming the ubuntu, If I use Lubi to install Kubuntu in Ubuntu-8.04 (which was installed using wubi), will not create problem, right?
  Is it Linux file system (EXT3 or other one) is required to use Lubi? or even I can run lubi from partition created in windows (NTFS)?
Please update.
With Thanks,
Prabath

---

### Post by prabath_fun on 2008-10-13
Hi ago,
   I installded Kubuntu by renaming Ubuntu folder and with help of Wubi. I have not tried with Lubi. 
    Also, I made menu entry for Kubuntu and can able to boot with both ubuntu and Kubuntu. 
   Thanks for your help.
   Further, I tried to make menu entry in windows menu itself with help of EasyBCD. I could not able to point out virtual disk while making.

[COLOR="Plum"]Prabath[/COLOR]

---

### Post by ago on 2008-10-13
> **prabath_fun said:**
> 
   Further, I tried to make menu entry in windows menu itself with help of EasyBCD. I could not able to point out virtual disk while making.

[COLOR="Plum"]Prabath[/COLOR]

That's more complex as you would need to create 2 wubildr.mbr each with a different embedded menu.lst chainloading to the real menu.lst

---

### Post by Zakhafr on 2008-10-13
You can have as many Wubi'fied systems as you like, because that's taken care of by Wubi's GRUB and specified in menu.lst

If you wish to save space, you can even point them on the same swap pseudo disk.

But from Windows, it launches only one thing: wubildr.mbr (pseudo-MBR ?)

You have no way to "pass parameters" to this wubildr.mbr so that it can guess what Wubi'fied Linux it has to launch.
That's because wubildr.mbr do it by itself (with wubildr)!

To what I can guess, wubildr read
\ubuntu\winboot\menu.lst (hardcoded probably, in the disk from where it has booted)
From there it finds indications of possible locations of the *real *menu.lst (in the meaning on Linux GRUB menu.lst).
Default location is \ubuntu\boot\grub\menu.lst
But you have other fallback locations as well.

So the only way you could do that directly from XP/Vista Bootloader would be to recompile a wubildr/wubildr.mbr of you own, so that it accepts parameters or fetches another location to start.

... maybe you could file a "suggestion" to wubi team for accepting parameters... if that works with windows bootloader (I don't know ?)

So in XP for example, instead of having

[INDENT][boot loader]
timeout=10
default=c:\wubildr.mbr

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"[/INDENT]

you could add the section in bold to make the first file wubildr loads parametric

[INDENT][boot loader]
timeout=10
default=c:\wubildr.mbr

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu" **/start="\ubuntu\winboot\mymenu.lst"**[/INDENT]

Default start location (no parameter) would be the same as today : \ubuntu\winboot\menu.lst


[I][Edited: oops posted at the same time as Ago... or do as Ago said (he is the specialist!) provided you know how to edit a MBR!
Maybe what I suspected to be "hardcoded", is just "hardcoded" in the MBR in fact][/I]

---

