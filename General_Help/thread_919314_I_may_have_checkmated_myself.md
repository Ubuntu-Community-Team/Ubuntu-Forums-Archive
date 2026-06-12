---
title: "I may have checkmated myself"
date: 2008-09-13
forum: General Help
---

### Post by cp1969 on 2008-09-13
In trying to repair an unbootable xp dual installation, I tried a technique in which I installed something called Smart Boot Manager.

The whole idea was to get it so that I could boot from the Windows CD.

Well, it seemed to get in front of Bios somehow.  In bios, my first choice for booting is the CD.  But SBM does not allow the 'press any key to boot from CD' message to come up.  Instead, I get directed to its own menu, of which there are three choices--none of which include the CD.

Now, even ubuntu won't start.  I tried to boot under the ubuntu recovery mode, but that comes up with a prompt:

(initramfs)

if you type 'help' it will give a list of available commands, none of which are familiar to me.

Help!

---

### Post by rraj.be on 2008-09-13
Try a ```
fsck
``` to check the disks and partitions integrity by booting into ubuntu live CD.

---

### Post by red_team316 on 2008-09-13
Try hitting Esc, F1, F2, F12, or DEL when the computer is starting up. I know many BIOS have an alternate boot option that manually lets you specify it at each boot.

It's hard to believe that SMB(a boot loader) has priority over your BIOS, but if thats the case, then thats really scary! Are you absolutely sure there isn't another BIOS option you have changed preventing CD boot since then?

Is there any reason you prefer, SMB? whats wrong with GRUB?

If you just want to repair the bootloader, you can fire up a Live CD, enter the terminal, and type:

grub
root (hd0)
setup (hd0)
quit

Then reboot.

The above commands are assuming you have the dualboot all on one hard drive, if that isn't the case, then you may need to point it to hd1 or something else.

---

### Post by cp1969 on 2008-09-13
That command resulted in a 'not found' response.

At present, I cannot boot with the CD--it will not even attempt it.  If I start the machine with a CD in the drive, Smart Boot Control opens up it's own menu in which there is no choice to boot from the CD.  At no point do I get the message 'press any key to boot from CD'.

---

### Post by cp1969 on 2008-09-13
> **red_team316 said:**
> Try hitting Esc, F1, F2, F12, or DEL when the computer is starting up. I know many BIOS have an alternate boot option that manually lets you specify it at each boot.

It's hard to believe that SMB(a boot loader) has priority over your BIOS, but if thats the case, then thats really scary!

Is there any reason you prefer, SMB? whats wrong with GRUB?

I can get to BIOS and see that the CD is the first boot choice.  But, before I can ever get the prompt to boot from it, SBM opens up it's own menu with no CD choice on it.

I installed SBM because I could not boot from the Windows CD.  It worked--once--then the next time I tried it I got this SBM menu.  Somehow during all this I hosed my ubuntu installation (I think by interrupting a boot up, not sure) and now, without the ability to even boot from the Live CD, I may be totally hosed unless there is a set of commands that I can issue from this 'initramfs' shell to get unbuntu to run again.

---

### Post by cp1969 on 2008-09-13
I can boot up using the Live CD, but only after I unplug my HDD that has ubuntu installed on it.

---

### Post by Gannon8 on 2008-09-13
> **cp1969 said:**
> Now, even ubuntu won't start.  I tried to boot under the ubuntu recovery mode, but that comes up with a prompt:

(initramfs)

if you type 'help' it will give a list of available commands, none of which are familiar to me.

Somehow, that looks like grub. Try entering into the prompt:
```
initrd.img
```

---

### Post by cp1969 on 2008-09-13
> **Gannon8 said:**
> Somehow, that looks like grub. Try entering into the prompt:
```
initrd.img
```

Don't think its Grub. Grub has already ran and offered it's menu choices at that point. It is the equivalent of a c: prompt in dos, it mentions that by typing 'help' it give a whole list of commands that it will apparently accept but I don't recognize any of them.

---

### Post by red_team316 on 2008-09-14
post what it says for the commands, it does sound like it is GRUB. Maybe you borked your bootloader with half GRUb half SMB...

---

### Post by cp1969 on 2008-09-14
> **red_team316 said:**
> post what it says for the commands, it does sound like it is GRUB. Maybe you borked your bootloader with half GRUb half SMB...

OK.  This will involve some typing.

First, the Grub boot options screen comes up normally.  I choose ubuntu, and not the recovery mode, just the regular choice I have always made.  Then, the ubuntu logo comes up as normal, but the progress bar has one little bit of it lit up on the left and it does nothing for about five minutes.  Then, it says:

Busybox v. 1.1.3  (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

So, I enter 'help' and this is what it lists:

Built-in commands:
. : alias break cd chdir command continue echo eval exec exit export false getopts has help let local pwd read readonly return et shift times trap true type ulimit umask unalias unset wait [ [[ ash basename busybox cat chmod chroot chvt clear cmp cp cut deallocvt dumpkmap echo egrep env expr false fbset fdflush fgrep grep hostname ifconvig ip kill ln loadfont loadkmap ls mkdir mkfifo mknod mkswap mktemp more mount mv openvt pidof printf ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort stat sync tail tee test touch tr true tty umount uname uniq wget yes

There may be some typos in there as I had my head cranked about 90 degrees left reading the screen of the dead computer while typing this.

---

### Post by red_team316 on 2008-09-14
Aha, the BusyBox error! This has been plaguing many people for quite some time.

Please post what version of Ubuntu you have installed.

Try
> 
While 7.10 won't install for me either, I had no problem with this "ATA failing cause I don't have sata" issue while installing 7.04 but I had a slow boot and at the end of this post and I'm sure this is the issue with the 7.10 installation. (See the fix I used below).

The fix is great for the installed system but how do we modify a CD? I have no idea how to make it ignore "ata_piix" and use "ide_generic". Boot options? Some busybox commands?

It would be real nice if someone posted the steps to make this work for the the newbie and if it couild be made "sticky" in the forum, even better. This is messing up a lot of people.

************
edit /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

**************

Credit for this 7.40 slow boot fix goes to "Fabio Povoledo". He had it posted in a forum somewhere and I was days finding the solution. I saw a lot of people trying to fix the slow boot issue. I assume none of these people could do a fresh 7.10 install.


See Post #4
[http://ubuntuforums.org/showthread.php?t=581746](http://ubuntuforums.org/showthread.php?t=581746)
See Post #8
[http://ubuntuforums.org/showthread.php?t=582199&highlight=busybox](http://ubuntuforums.org/showthread.php?t=582199&highlight=busybox)

Please let us know if this does the trick.

---

### Post by cp1969 on 2008-09-14
I *had* version 7.10.  Now I have nothing.  It is totally hosed.

---

