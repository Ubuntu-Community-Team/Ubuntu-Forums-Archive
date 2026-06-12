---
title: "Need Help deleting GRUB. Tricky situation"
date: 2010-03-19
forum: Hardware
---

### Post by WestsideRiderz15 on 2010-03-19
I have an msi wind. i installed netbook remix and lost interest. I removed the partitions via windows xp and now have a GRUB issue. It boots to grub recovery >

Now, I have tried booting with a windows disk and using the recovery console/fix mbr command with no success.

I think it is because my first partition on my only hard drive is a windows automatic installer and recovery partition. my second partition is the actual OS install. this is what i think makes me different from the rest of the people having this problem.

Any ideas how to remove grub and fix the MBR for windows? Ive tried for a week now with no results.

I can currently run ubuntu live on a flashdrive and i think i can still boot into windows via an emergency flash drive (ntdlr, boot.ini ect).

---

### Post by Goveynetcom on 2010-03-20
Hmmmm.....
Maybe you should load a Hard-Disk backing up tool, backup your recovery partition, and the main OS (if you have important stuff on it, other wise the recovery should be fine, and you could just copy that back and reinstall). Verify your backups were successful, then just reformat the whole drive, restore recovery partition, then reinstall Windows.

It's a nasty way to do it, but you might have too...

I googled, deleting grub (for something like your situation), and the **fixmbr **and various other methods you tried should have worked, but other people posted the same things that it didn't... So it maybe your only answer...

But I would back it up for good measure anyways...

---

### Post by WestsideRiderz15 on 2010-03-23
c:/ fix mbr - No go. It says its writes to partition 0. I know i logon to c:\windows at the beginning of the recovery console so i assume it knows the correct partition to fix
fixboot - No help either
bootcfg /rebuild no help

Ive booted via Ubuntu Live and run some command lines, but i dont have a knowledge on the lingo in "terminal"

I found some #dd lines of code and typed them in as best as i could but no go there.

I heard that if you delete partitions that the Grub loader will remain. Does this also apply for a complete format?

Thanks All.

---

### Post by PRC09 on 2010-03-23
I read somewhere that on a wind with card readers installed the win xp install actually identified the hard drive as E because it saw the card readers as hard drives so maybe try fixboot to another letter...Maybe....Just a guess on my part tho.....

---

### Post by WestsideRiderz15 on 2010-03-23
Ill take a look. In dos, I run DIR on the C drive and it shows the documents and settings folder which commonly is the os install partition.

I can go to a D: drive but it says no disk in the drive so maybe that one is the flash reader.

On a second note:
When my pc boots, it gives an option of F3 to boot to the recovery console normally. Is that a bios feature?

---

### Post by WestsideRiderz15 on 2010-03-24
WOOP. HERE is the solution. (only works if you can still boot to windows via emergency bootloader) I used:
Novicorps Win to Flash: free ware
A downloaded copy of windows xp sp3 home (torrent) (dl the version and service pack you have or need)
MBRFIX.exe: freeware (cnet.com)

first, use win to flash, goto tasks and click create bootable emergency flash drive.
A window will open. I used these options: USB-hdd, fat 16 cha, then point it to the directory of the windows iso you downloaded. then point it to your flash drive.
This creates a bootable flash drive with the 3 common files u need to boot (NTDECT, boot.ini ect)

go into your bios when the pc boots and tell it to load usb harddrive first.

reboot

Windows should now boot.

Start menu, run, cmd.exe
a dos window will open
go back to your desktop, extract mbrfix into its own folder (3 files) (mbrfix64 is for 64 bit versions, check with your provider to see what you have)
go back to your dos window
c:\documents and settings\(your name)>cd desktop
...cd (folder name withmbrfix in it)
if you type DIR, it should show the 3 files (mbrfix, mbrfix64, and an html file)
should look something like this
c:\documents and settings\(your name)\desktop\temp>

Now, MY OS partition is my second partition because my first one was a recovery partition. i have one hard drive
hard drive numbers start at 0, partitions start at 1.

in the dos window type:
mbrfix /drive 0 /partition 2 /fixmbr /yes
this fixes the mbr for 1st hard drive, 2nd partition

rebooted and done!

P.S. Read comments on Cnet on MBRfix and also comments on MBRfix website to learn more.

---

