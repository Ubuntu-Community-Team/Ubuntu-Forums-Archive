---
title: "boot issue???"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by de_valentin on 2007-12-19
Hi,

Ever since I installed a 2nd OS, I have ctrl-alt-delete during boot to get gutsy to start.

On startup I get the GRUB menu, I make my choice for gutsy and after a second or 2 I get  the screen with the orange bar. the orange bar hangs at about 1/3 after that I get a commandline (or something like it) screen.

It reads:

> 
* File system check failed.
Please repair the filesystem manually.
* A maintenance shell will now be started.
CONTROL_D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash:Command: command not found
bash: The: commmand not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@laptop:~#


after ctrl-alt-delete it takes a few seconds untill  the login manager is started
How can I fix this?

---

### Post by Red Badger on 2007-12-19
Have you tried running fsck?
If you have a SATA drive, you would enter:

fsck /dev/sda1

I have the same problem, and when I run fsck I get an error 'a compression flag is set without compression support'. I still haven't worked out how to fix it, but if you have the same problem, 'two heads are better than one'. :)

---

### Post by de_valentin on 2007-12-19
I just tried it but it warns me that I shouldn't do it while it is still mounted so I have to wait a little, I will run it from a livecd later today

---

### Post by de_valentin on 2007-12-19
I forgot I had a livecd with me.

That didn't really show anything special I think

```
root@Elive[/home/eliveuser]# fsck /dev/hda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda1: clean, 161070/2518208 files, 1704907/5032353 blocks
root@Elive[/home/eliveuser]# 
```

I hope this helps but I doubt it.

---

### Post by Red Badger on 2007-12-19
According to fsck your disk looks okay, so not the same problem that I'm having. I still haven't found the solution to my problem.
There seems to be a lot of people experiencing boot problems on the forum. I've already re-installed Gutsy four times, and the problem re-occurs after a week or so.
Hope you find the answer! If I come across anything of use to you, I'll post it.

Best of Luck. :)

---

### Post by de_valentin on 2007-12-19
Thanks good luck to you to

---

### Post by SonicSteve on 2007-12-19
> **Red Badger said:**
> Have you tried running fsck?
If you have a SATA drive, you would enter:

fsck /dev/sda1

I have the same problem, and when I run fsck I get an error 'a compression flag is set without compression support'. I still haven't worked out how to fix it, but if you have the same problem, 'two heads are better than one'. :)

Make that 3 of us and three heads are better than one.
It started for me after the last update which I downloaded about 40mins ago. It included a new kernel.

---

### Post by SonicSteve on 2007-12-19
It seems as though in that last update the FSTAB file was changed. 
My error message was referencing a drive called /dev/sda1 and the UUID was non-existent in my hardware information database. 
Check your error message and write down the first 9 digits of any UUID listed,
Check your FSTAB files and see if that UUID is listed as one of the mounting options. 
I commented out the line that referenced the UUID pointing to nothing and the message is gone.

In my computer I think /dev/sda1 used to be my root file system, I can't be sure but based on my FSTAB file and what I remember from installing a few months back it makes sense. That last update must have re-written the FSTAB entry after updating my Hardware information database.
Even if I'm wrong about the update re-writing the drive from /dev/sda1 to /dev/hdb1 I know my FSTAB file suddenly had a bogus entry that it didn't have before.

EDIT 
Just an FYI my exact message was this;
Checking file systems...
FSCK 1.40-wip (14 nov 2006)
FSCK. EXT3: unable to resolve UUID "bogus UUID #"
File system check failed
Maintenance Shell will now be started

If that was your message this should help you.

---

### Post by Red Badger on 2007-12-20
Hi  de_valentin & SonicSteve

I managed to fix it!
Fstab had been changed so that the drive was only mounted read only. I booted with a Live-CD, unmounted /dev/sda1 and the re-mounted it to /mnt  Then I was able to open /etc/fstab in gedit and change the entry for /dev/sda1 so that it was read write. Re-booted the machine and I was back in Ubuntu with everything intact.
I don't know if this will fix your problems, but if you think so I'll post full details.

:):):)

---

### Post by SonicSteve on 2007-12-20
So far the common theme has been a changed FSTAB file. No answer as to why so far though. I use Feisty and guys are using Gutsy. Unless Feisty and Gutsy both had a Kernel update in the last few days I don't see a connection. I wonder if a changed FSTAB file could result from a Kernel update.

---

