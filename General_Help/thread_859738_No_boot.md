---
title: "No boot"
date: 2008-07-14
forum: General Help
---

### Post by oldguardjon on 2008-07-14
Loaded ubuntu using Wubi onto Windows Pro on old 400mHz computer with 256K memory. On boot, get the logo and then Busybox message 'Enter help' and cursor (initramfs). Windows runs OK.

---

### Post by Jim! on 2008-07-14
I recommend you do a search, quite often people find that the answer to there question was just a search away.

---

### Post by coolaj86 on 2008-07-14
Try reinstalling.

Does the LiveCD work?

It seems as though Jim! is hinting that it's really easy to find the answer to your problem on Google. Try searching for that error message that you get.

@Jim!
Do you know some search terms that would work particularly well for this problem?

---

### Post by ago on 2008-07-15
Please post the output of:

cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions

---

### Post by plastichero on 2008-07-15
Do you stuck at some point with this prompt?

[COLOR="DarkOrange"]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs)[/COLOR]

I also got the same thing and was astonished. The solution is simple: From windows, after running the WUBI installer, replce "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works. (Here G: was the drive that is selected for Ubuntu installation, it may be different for you)

also, is your drive FAT32 formatted? make it NTFS.
__________________

---

### Post by oldguardjon on 2008-07-17
Made the changes suggested by Plastichero and now the program appears to be loading and finally stalls at 'ubuntu@ubuntu:~$'

Ago, how do I find the three cat\proc\    messages?
John

---

### Post by ago on 2008-07-17
cat is a command, /proc/cmdline is an argument, you need to type exactly as above with spaces and correct slash.

---

### Post by oldguardjon on 2008-07-17
Sorry, I'm not ubuntu savvy....at what prompt to issue?

---

### Post by oldguardjon on 2008-07-17
I haven't tried an install from the disk, but another problem might be a memory restriction....this is old machine, 400mHz with 256kB memory. what do you think?

---

### Post by minhmeoke on 2008-07-17
Once you have logged in to ubuntu, you should see the prompt, which looks like 'username'@'computer', for example, ubuntu@ubuntu:~$ . You should be able to type on your keyboard, and see your inputs. Now type in the first command, so the screen looks like this, and hit enter
```
ubuntu@ubuntu:~$ cat /proc/cmdline
```
You should get a line of output, for example:
```
root=UUID=173130dd-21ff-4682-9172-d399a9399fec ro all_generic_ide
```
Repeat those steps for the other two commands, and post the results here.

By the way, if you have not done so, I would highly recommend following plastichero's advice, it usually fixes these problems.

Also, since your computer is low on RAM, you might want to choose xubuntu instead of standard ubuntu, since it runs faster.

---

### Post by ex.hav0k on 2008-07-19
Hello, I am running into a problem simliar to this.  I have had ubuntu installed for a few weeks now, and everything was working fine.  I was playing a video game, talking to a friend on jabber (pidgin) and all of a sudden, the game freezes and things start to mess up.  i tried opening the system manager, but got an error, so i tried to log out, but it wasn't working so I CTRL+ALT+BKSPACEd and then my computer completely froze.  now when I try to boot up I get the same thing as the OP.

So, i tried to boot in safe mode or whatever it is on the options under kernels and there are some lines about not being able to mount various things.  a few of the lines:

```
mount: Mounting /dev/disk/by-uuid/7f6aaeb3-1ca7-4ada-aac8-f4e40d3020f5 on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or direcotry
Target filesystem doesn't have /sbin/init
```

no part of that sounds particularly good to me.  So I ran the lines suggested by ago.

```
cat /proc/cmdline
root=uuid=7f6aaeb3-1ca7-4ada-aac8-f4e40d3020f5 ro single
```
```
cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid.nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusect1 /sys/fs/fuse/connections fusect1 rw,relatime 0 0
```
```
cat /proc/parititions
major minor  #blocks  name

   8     0   58605120 sda
   8     1   56163208 sda1
   8     2          1 sda2
   8     5    2441848 sda5
```

i hope you guys can help me :downs:

---

### Post by ex.hav0k on 2008-07-19
ah, i feel kinda stupid after i searched the forums and saw a lot of threads where ago gave the answers.  apparently i have to run chdisk, which isnt something one can do from busybox as my harddrive isn't even mounted and the command isn't avaliable either.  im downloading a knoppix disk on my sis's computer and going to see if i can use knoppix to fix the filesystem (which im guessing is the problem).

i'll post again on how that goes.

---

### Post by ago on 2008-07-21
Yes if you hard reboot you have to run chkdsk /r from windows.
PS You might have run out of disk space originally, check with df once you manage to boot.

---

