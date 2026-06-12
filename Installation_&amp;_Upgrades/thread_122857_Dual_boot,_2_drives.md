---
title: "Dual boot, 2 drives"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by Daminator on 2006-01-28
My desktop machine has XP installed on a large drive.
I plan on putting Ubuntu on a second drive and choosing which to boot to by changing the boot drive in the bios.
How should I install on this second drive? I don't want 'grub' to do anything to the boot sector on the first drive.
Should I remove the first drive entirely (to ensure nothing gets changed) and then put it back once Ubuntu is installed, or is there a way to install with the drive still there but with no changes happening to it?
Thanks for any help.
Damian

---

### Post by psomas on 2006-01-28
if the second drive is empty(windows and their files are found only in the first drive), i don't think you should have any problem...
however,if windows have "access" to the second drive, i don't know what will happen...probably you'll be asked to partition it...
try to install ubuntu and when it asks you to choose where to install it, you can see if the disk needs to be partitioned...
if it does,then you can exit the installation remove the disk and  try to install it again... ;)

---

### Post by lha on 2006-01-28
I have posted [instructions on another thread]("http://ubuntuforums.org/showthread.php?p=677880#post677880") that might be of interest to you. Once you have installed Ubuntu, do following to edit menu.lst: Open terminal. You'll find it in Applications menu, Applications->Accessories->Terminal. Type these commands:
```
cd /boot/grub
``` This will put you into right folder.
```
sudo cp menu.lst menu.lst_backup
``` Now we want to make a backup of the file we are editing.
```
sudo gedit menu.lst
``` Opens the file in an editor. That sudo part is needed becouse normal users don't have write permission to those files. It will ask for your password when you use it for the first time. Other info should be found from that link.

---

### Post by TecSoft on 2006-01-28
I am dual booting this way. I set my Ubuntu drive to slave and my windows drive to primary. Then I installed GRUB on the MBR. I like it and it works.

---

### Post by Neo40 on 2006-01-31
Actually, I have only Ubuntu installed (hd0). I'm going to install XP on my second hdd (hd1). Does XP will load if it is on my slave drive? If not, what I have to do to be functional?
Thanks

---

### Post by lha on 2006-02-01
[QUOTE=Neo40]Actually, I have only Ubuntu installed (hd0). I'm going to install XP on my second hdd (hd1). Does XP will load if it is on my slave drive? If not, what I have to do to be functional?
Thanks[/QUOTE]

If you are able to install Windows on (hd1), it will overwrite Grub on (hd0). Windows wants to be on your first hd. You'd be best off if you take out your Ubuntu drive and make that second (the one you want to use for Windows) drive (hd0) (or hda/sda). Install Windows on it the usual way. Now, you have to rearrange your drives again. Make Ubuntu drive (hd0) and Windows drive (hd1). Then add
```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
to menu.lst.

---

### Post by Neo40 on 2006-02-01
Thanks lha! I'll try it next week-end :)

---

