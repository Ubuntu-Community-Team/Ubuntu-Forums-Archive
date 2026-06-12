---
title: "dual boot ubuntu 10.04 bootmgr missing"
date: 2012-09-26
forum: Hardware
---

### Post by learning_ on 2012-09-26
So here's a breakdown of what happened:

-Via gparted I deleted my primary ubuntu partition (10.04) as well as 2 other ubuntu partitions. The partitions were set up with pirmary ubuntu first (on left), next windows, then at the end were 2 ubuntu partitions.
-Reinstalled ubuntu 10.04 64bit
-Booted into ubuntu, ran updates and installed a few basic programs.
-Restarted
-Instead of loading grub, printed out the message "BOOTMGR is missing press CTRL+ALT+DEL to restart". That key combo wouldn't work but that's less important.
-Figured I might have installed something wrong so I reinstalled overtop of the previous ubuntu install.
-After 2 restarts, had the same problem. 
found [this link]("https://help.ubuntu.com/community/Boot-Repair") and followed the steps to install and repair. It worked once, then it spit out the same message after another reboot. 

Now everytime I reboot after this fix, I have to run that repair program from the ubuntu livecd in order for it to even load. I received a link detailing every line in the terminal that had taken place each time I ran the repair.
[http://paste.ubuntu.com/1219513]("http://paste.ubuntu.com/1219513")
[http://paste.ubuntu.com/1219748]("http://paste.ubuntu.com/1219748")
[http://paste.ubuntu.com/1219880]("http://paste.ubuntu.com/1219880")
[http://paste.ubuntu.com/1228828]("http://paste.ubuntu.com/1228828")
I've been tearing my hair out trying to get this fixed and after days of searching, I can't find the solution. Any help is appreciated, also I am still a beginner when it comes to terminal commands and more in-depth file editing so please explain in detail.

---

### Post by oldfred on 2012-09-26
Bootmgr missing is  a Windows error as bootmgr is a Windows file.

Normally you boot thru the hidden 100MB boot/repair partition, which on your system is sda2, but you have boot flag on sda3. 

Boot-Repair may have copied bootmgr & BCD from Windows boot partition as a just in case you have issues. It looks like either should boot Windows from grub's menu, except you have grub4dos installed which has to confuse booting. Plus in both you have two copies of grub4dos and Windows cannot have  the same file twice. Delete them both.

From sda2
Boot files:        [COLOR=Red]/grldr[/COLOR] /bootmgr /Boot/BCD [COLOR=Red]/grldr[/COLOR]
From sda3:
    Boot files:        [COLOR=Red]/grldr[/COLOR] /bootmgr /Boot/BCD                         /Windows/System32/winload.exe [COLOR=Red]/grldr[/COLOR]

---

### Post by YannBuntu on 2012-09-27
@learning: please follow Oldfred's advice.

@fred: -i'm surprised it says "bootmgr is missing". 
- do you know where grub4dos comes from? is it installed by default in 'legal' copies of Windows? 
- your intuition was good: we can see "Copied Win boot files from sda2 to sda3" at the bottom of the 1st log.

---

### Post by oldfred on 2012-09-27
I do not follow Windows 7 installs. From the beginning we rarely saw grub4dos. Even early with Boot script meierfra always posted to remove the grub4dos file grldr.
Correction. meierfra has said it should not cause issues. But two will be an issue.
The grub4dos may be from wubi or easyBCD.

---

### Post by YannBuntu on 2012-09-27
@learning_: have you installed grub4dos , or followed a tutorial talking about grub4dos?

---

### Post by learning_ on 2012-09-29
yannbuntu, I hadn't heard of grub4dos at all prior to your responses. 
> in both you have two copies of grub4dos and Windows cannot have the same file twice. Delete them both.

From sda2
Boot files: /grldr /bootmgr /Boot/BCD /grldr
From sda3:
Boot files: /grldr /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr
oldfred, could I get some clarification on this? I understand I have to delete the grub4dos, are the locations you listed what need to be deleted? If that is the case, how exactly would I do this, or rather how would I navigate to these to remove them via terminal? I apologize if this seems like a very obvious question but I just want to be sure I am understanding everything properly before potentially making a fancy new paper weight.

---

### Post by oldfred on 2012-09-29
They are in the root of Windows or c: in Windows. Often in Windows now that is all hidden files that only show if you turn that on.

The NTFS driver from Linux shows all Windows hidden files & folders. From that stand point it can be a bit more dangerous as you can delete or move vital Windows files.  I used to turn on the show hidden files in Windows and often (too often) clicked & moved too fast and moved an entire system folder under another folder. Major repairs or reinstall ensued. 

You should from Ubuntu be able to use Nautilus or the file browser and navigate to the top level of the Windows folder. If concerned copy files to another location and rename. 

Duplicate names are not allowed for files or folders.

Linux is case sensitive so in Linux you can have /boot & /Boot but in Windows that would be the same folder. So the only way to delete that type of error is from a Linux repairCD or LiveCD.

---

### Post by learning_ on 2012-11-20
I couldn't find the files you mentioned but I have been having another big issue which I have been trying to work out. For some reason my x-server won't start after loading up a new boot-splash screen. Posting a new thread regarding this issue now. Thanks, oldfred, for all your help.

EDIT: Forgot to mention... I couldn't find the files, but the issue seems to have self repaired... ?

---

