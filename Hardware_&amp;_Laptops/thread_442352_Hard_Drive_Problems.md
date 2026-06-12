---
title: "Hard Drive Problems"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by koulanji on 2007-05-13
So my electricity went out and when I booted up my computer I get a message stating that /dev/sda1 contains file system with errors, check forced. The check is finished and it states that /dev/sda1: Multiply-claimed blocks in inode 3919326: 9214211, indoe: 3919560: 9214202, inode: 18404540

dev/sda1: Unexpected Inconsistency; Run fsck Manually
fsck died with exit status 4. 

It then tells me that the automatic file system of the root filesystem failed, and a manual fsck must be performed.

It then says that the root filesystem is mounted in read only mode and a maintenance shell will be started, and then I get bash errors

bash: no job control in this shell
bash: groups: command not found
bash lesspipe not found
bash: The: command not found

Then I get this weird error

The program apt-get is not installed. You can install it by typing: apt-get install apt
bash: apt-get command not found
bash: dircolors: command not found
bash The: command not found.

So I am not really sure what's going on, and any help would be appreciated.

---

### Post by kidders on 2007-05-14
Hi there,

This is nasty. Sometimes, peoples' power can go and their computers are fine. :-(

My interpretation of what's happened is that Ubuntu detected root filesystem errors, tried to correct them, failed, tried to fall back to an emergency repair console, and didn't quite make it. Basically, Linux tends not to be very eager to automatically perform repairs that are potentially dangerous, which is why you get odd messages that effectively amount to "I've just run fsck... now it's your turn".

[U][B]Step 1
[/B][/U]Boot your PC with any Linux CD and drop to a console. It's important not to use any graphical tools, so you can see every single error message, and have complete control over everything that happens.

Try to force your root filesystem to mount (in read only mode), and poke around in it a little, to see what kind of shape it's in. The "read only" part is extremely important, as it will guarantee that the corruption can't get any worse.
```
sudo mkdir /mnt/broken
sudo mount -o ro /dev/sda1 !$
```[U][B]Step 2
[/B][/U]Make a judgement call. I always ask people who've corrupted things to make backups, so that they can undo any repair attempt that goes pear-shaped and makes things worse. If your root filesystem is big though, making a backup is easier said than done!

[U][B]Step 3
[/B][/U]Dismount your filesystem, and try running **fsck** on it a few times. Read the man page, start with a conservative approach, and try a few more daring things each time, until **fsck** simply refuses to cooperate any more, or gives your filesystem a clean bill of health.

[U][B]Step 4
[/B][/U]If you're successful, do a **sudo shutdown -r now**, eject the boot CD and hold your breath.

Unless the damage is very severe, this should work out well for you. It's all basically quite easy ... just go slow, and don't do anything rash.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by anselm on 2007-05-15
I have this problem also but I am using ide drives same errors but I run fsck manually and it ask me to fix a bunch of problems with inodes??? I just keep hitting enter untill it says reboot, then when I reboot everything works fine????

This has happened to me twice,  not sure what caused this, when it happened this time I was running vmware server and looking thru the add remove programs in ubuntu.

main system is 7.04.

Thanks

---

### Post by kidders on 2007-05-15
Excellent. :-) That's be best case scenario, where **fsck** is able to clean up the mess with no ill effects. Glad to hear your recovery went well.

---

### Post by justmoon on 2007-05-21
My mum has a similar problem.

Since the update to Feisty Fawn Ubuntu will every once in a while have this "fsck failed with exit status 4" then to get into recovery console, not finding apt-get and a few other basic tools, but the console does come up. I told my mum to run a fsck -c /dev/sda1 which comes up with a few million errors, so it takes a while. (A weight on the ENTER key does the trick.) After rebooting everything is fine. Computer works perfectly, not a single file corrupted, ever.

I have a hard time believing that this could really be the filesystem having actual corruptions, thousands of them without anything else breaking at some point.

Doesn't correlate with incorrect shutdown or power outages either. Just every once in a while Fawn decides that it would be nice to fail at fsck with tons of filesystem errors and then recovering perfectly through the manual fsck...

Again, this is only since we installed 7.04, before everything was fine.

---

### Post by justmoon on 2007-05-21
Oh and if after running fsck you run it again right away, it finds the same errors all over again.

---

