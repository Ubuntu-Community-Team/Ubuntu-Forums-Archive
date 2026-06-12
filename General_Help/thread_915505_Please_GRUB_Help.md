---
title: "Please GRUB Help?"
date: 2008-09-09
forum: General Help
---

### Post by ravindukelum on 2008-09-09
In my notebook I've installed XP and Ubuntu in dual boot mode ans Grub loader was working fine Just now grub loader doesn't come and only boot XP and help me get back grub and dual boot menu again and I don't want reinstall it again.

---

### Post by Washer on 2008-09-10
use your livecd & reinstall grub. Google the command, i forget it.

---

### Post by mihaiv on 2008-09-10
See this forum post (wernst comment):
[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

> 1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

### Post by caljohnsmith on 2008-09-10
Since you want to reinstall Grub to the master boot record (MBR), just boot your Live CD and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let us know how it goes.

---

### Post by Zelbinian on 2008-09-10
I'm having a similar problem and have done those steps several times to no avail.

Here's how I managed to muss it up:
[LIST]
[*]Resized and moved my Ubuntu partition to be the 2nd of 3 (to be next to the swap partition)
[*]Attempted to install Vista Business edition on first partition
[*]Even after deleting and reformatting partition 1, Windows doesn't want to install
[*]Reboot, GRUB is dun broked
[*]Google searched, found above instructions, ran them, still get error code 17.
[/LIST]

Any ideas?

---

### Post by wolfen69 on 2008-09-10
here's an easy way out. download [KiwiLinux]("http://kiwilinux.org/kiwi/en/") and boot the live cd. go to system>administration>restore grub and follow the prompts.

---

### Post by caljohnsmith on 2008-09-10
> **Zelbinian said:**
> I'm having a similar problem and have done those steps several times to no avail.

Here's how I managed to muss it up:
[LIST]
[*]Resized and moved my Ubuntu partition to be the 2nd of 3 (to be next to the swap partition)
[*]Attempted to install Vista Business edition on first partition
[*]Even after deleting and reformatting partition 1, Windows doesn't want to install
[*]Reboot, GRUB is dun broked
[*]Google searched, found above instructions, ran them, still get error code 17.
[/LIST]

Any ideas?
If you follow the instructions from my previous post, does the "find /boot/grub/menu.lst" command in Grub return anything? If it does, do the other commands complete successfully?

---

