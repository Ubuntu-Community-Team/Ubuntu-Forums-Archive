---
title: "How to install GRUB under windows?"
date: 2008-10-02
forum: General Help
---

### Post by Hello71 on 2008-10-02
How do I install GRUB under Windoze's boot loader? I know how to put GRUB on top, but how do I put GRUB _under_ Windows?

---

### Post by Gannon8 on 2008-10-02
You can only put grub on the MBR as far as I know.

Try Super Grub Disk (google it)

---

### Post by Sef on 2008-10-02
> Try Super Grub Disk (google it)

[Super GRUB Disk]("http://supergrubdisk.org") site.

---

### Post by Hello71 on 2008-10-02
OK, anything OTHER than Super GRUB Disk?

---

### Post by Zimmer on 2008-10-02
> **Gannon8 said:**
> You can only put grub on the MBR as far as I know.

Try Super Grub Disk (google it)

Not quite true...  if you are dual booting Windows and Linux then you can install grub to the partition containing your Linux install instead of the MBR and use easyBCD   from
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
It installs to your Windows installation and you edit it there.
I have recently  set up a Vista dual boot with it ...
using this tutorial
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Hello71 on 2008-10-02
Windows XP. NOT Windoze Vistaslow.

---

### Post by Zimmer on 2008-10-02
OK, sure, but my comment was mainly aimed at Gannon8, however
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Have a good look around this page, scroll back to the top for lots of GRUB info.

I am not quite sure I understand you when you say you want to put grub 'under' Windows though...

---

### Post by Hello71 on 2008-10-02
I want to have this happen:
[COLOR=DarkOrange]
Hello71 boots computer
[/COLOR] [COLOR=DarkOrange]Hello, this is the windows bootloader[/COLOR]
[COLOR=Red]OSes: Microsoft *bla, bla, bla
GRUB / Linux[/COLOR]
[COLOR=DarkOrange]Chooses Windows
Starts Windows[/COLOR]
[COLOR=Blue]
Another Scenario:
[/COLOR] [COLOR=DarkOrange]
Now I want to start Linux
Hello, this is the windows bootloader[/COLOR]
[COLOR=Red]OSes: Microsoft *bla, bla, bla
GRUB / Linux[/COLOR]
[COLOR=DarkOrange]Chooses GRUB / Linux
Windows chain-loads GRUB[/COLOR]
[COLOR=DarkOrange]GRUB opens up[/COLOR]
[COLOR=Red]OSes: Ubuntu *something
Other operating systems:
Windows *something[/COLOR]
[COLOR=DarkOrange]Oops, I wanted to start Windows
Chooses Windows
Goes back to the Windows bootloader
Chooses Windows again
Boots Windows[/COLOR]

[COLOR=Blue]Another Scenario:[/COLOR]

[COLOR=DarkOrange]Now I want to start Linux
Hello, this is the windows bootloader[/COLOR]
[COLOR=Red]OSes: Microsoft *bla, bla, bla
GRUB / Linux[/COLOR]
[COLOR=DarkOrange]Chooses GRUB / Linux
Windows chain-loads GRUB
GRUB opens up[/COLOR]
[COLOR=Red]OSes: Ubuntu *something
Other operating systems:
Windows *something[/COLOR]
[COLOR=DarkOrange]Chooses Ubuntu
Boots Ubuntu

[COLOR=Black]Colour Code:
[COLOR=DarkOrange]Orange = Something happens or something intended
[COLOR=Red]Red = Something on the screen[/COLOR]
[/COLOR][/COLOR][/COLOR]

---

### Post by caljohnsmith on 2008-10-02
Sure, you can add the Grub boot loader to your Windows XP boot menu. Probably the easiest way to go about it is when you install Ubuntu, tell Grub to install to the partition boot sector of Ubuntu instead of the MBR (Master Boot Record); you can do this by hitting the "advanced" button at the final stage of the Ubuntu installer and tell Grub to install to say "/dev/sda2" (assuming sda2 is the Ubuntu partition) instead of /dev/sda, which is the MBR. Once you have Grub installed to the partition boot sector, you can make a copy of it and add it to your Windows XP boot loader.

Or if you all ready have Ubuntu installed, let me know, and we can easily install Grub to your partition boot sector and go from there. To get started though, please post:
```
sudo fdisk -lu
```
I can then lead you through the whole process step-by-step if you would like.

---

### Post by Hello71 on 2008-10-02
So after installing GRUB with the following commands:
```

sudo -i
grub
grub>root (hd0,4)
grub>setup (hd0,4)
grub>quit

```
*Then *what do I do?

---

### Post by Hello71 on 2008-10-02
If you really want to inspect my partitioning (with some stuff stripped out), this is the feedback from "sudo fdisk -lu" :
```

Disk /dev/sda: *, * bytes

GRUB Device   Boot   Start  End   Blocks Id  System
(hd0,0)       *                              HPFS/NTFS #Windows Boot
(hd0,1)                                      HPFS/NTFS #Windows Apps
(hd0,2)                                      W95 Ext'd (LBA) #Extended Partition
(hd0,3)                                      Linux #Ubuntu Boot
(hd0,4)                                      Linux swap / Solaris #Linux Swap
(hd0,5)                                      HPFS/NTFS #Profile / "/home"

```

---

### Post by caljohnsmith on 2008-10-02
First off, while you are in Ubuntu, do:
```
sudo dd if=/dev/sda5 of=~/Desktop/grub_bootloader.bin bs=512 count=1
```
Next mount your Windows partition, and move the Grub boot loader file to your Windows root directory:
```
sudo mount /dev/sda1 /mnt
sudo mv ~/Desktop/grub_bootloader.bin /mnt/.
```
Next you need to modify your Windows boot.ini file, but first back it up:
```
sudo cp /mnt/boot.ini /mnt/boot.ini.backup
gksudo gedit /mnt/boot.ini
```
At the end of your boot.ini file, add the following line:
```
C:\grub_bootloader.bin="Grub Menu"
```
Save, and your done, assuming you still have a Windows XP boot loader in your MBR and not Grub. If you don't have Windows in your MBR, run the following command from your Windows Install CD:
```
fixmbr
```
Next time on start up, you should see the Windows boot loader menu offering you a choice between Windows or the "Grub Menu". Let me know how it goes.

---

### Post by Hello71 on 2008-10-05
I actually just moved, but I will try that when I finish setting the computer and desk up. Happy (Pre-)Thanksgiving! :)

EDIT:
Apparently it doesn't work. The GRUB Menu starts, but stands still at a line that looks like a blank command prompt. I know the GRUB Menu starts because Ctrl-Alt-Del works to restart the computer, and doesn't at the Windoze boot loader. Any help?

EDIT EDIT:
Apparently it doesn't work entirely.

EDIT EDIT EDIT:
Apparently I forgot to install GRUB!

---

### Post by Hello71 on 2008-10-06
If you have a ext2/ext3 FS reader on Windows, can't you have it point to the actual kernel to boot directly? (Just asking if I ever want it)

---

### Post by louieb on 2008-10-06
I guess you mean you want the PC to show windows **ntldr** menu 1st. Then have it load GRUB so it can load Ubuntu. 
Its kind of a pain but heres how: [Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692")

---

### Post by Hello71 on 2008-10-08
Also, can't you do:
```

dd if=/dev/sda5 of=/mnt/grub_bootloader.bin bs=466 count=1

```
instead?

---

### Post by Paryshaan on 2011-08-24
> **caljohnsmith said:**
> First off, while you are in Ubuntu, do:
```
sudo dd if=/dev/sda5 of=~/Desktop/grub_bootloader.bin bs=512 count=1
```
Next mount your Windows partition, and move the Grub boot loader file to your Windows root directory:
```
sudo mount /dev/sda1 /mnt
sudo mv ~/Desktop/grub_bootloader.bin /mnt/.
```
Next you need to modify your Windows boot.ini file, but first back it up:
```
sudo cp /mnt/boot.ini /mnt/boot.ini.backup
gksudo gedit /mnt/boot.ini
```
At the end of your boot.ini file, add the following line:
```
C:\grub_bootloader.bin="Grub Menu"
```
Save, and your done, assuming you still have a Windows XP boot loader in your MBR and not Grub. If you don't have Windows in your MBR, run the following command from your Windows Install CD:
```
fixmbr
```
Next time on start up, you should see the Windows boot loader menu offering you a choice between Windows or the "Grub Menu". Let me know how it goes.


I did these steps for several times and several situations.
it works when Ubuntu is in the same hard disk as windows xp. but when xp is in master hard sda1 and Ubuntu is in slave hard disk sdb1 all the times after choosing the linux from xp boot loader it shows a "GRUB" and nothing happens!
it is when GRUB is installed in sdb1.
when GRUB is installed in sdb it shows a "grub>" prompt to rescue grub.
any helps are appreciated.

---

### Post by Mark Phelps on 2011-08-24
First of all, attempting to use GRUB with Windows is taking that hardest possible path to solving this.  So, I'm not even going to go down that route.

Since you have multiple hard drives, the EASY way to do this is the following:
1) Have GRUB installed ONLY to the Ubuntu drive
2) Boot from the Ubuntu drive -- but have the Windows drive connected as well
3) When in Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB menu and add an entry for Windows.

When you reboot, you will be presented with a menu containing both Linux kernels and MS Windows.

---

### Post by Hello71 on 2011-08-24
> **Paryshaan said:**
> I did these steps for several times and several situations.
it works when Ubuntu is in the same hard disk as windows xp. but when xp is in master hard sda1 and Ubuntu is in slave hard disk sdb1 all the times after choosing the linux from xp boot loader it shows a "GRUB" and nothing happens!
it is when GRUB is installed in sdb1.
when GRUB is installed in sdb it shows a "grub>" prompt to rescue grub.
any helps are appreciated.

2-year-old thread bump much?

---

