---
title: "Ubuntu 9.10 not startup before upgrade from 9.04"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by gaiterin on 2009-10-24
Hi!
I upgrade the Ubuntu versions from 3 years ago, I hadn't any problem never.

But now, from Ubuntu 9.04 to 9.10 RC, the grub appears, I select the normal options, appears the Ubuntu logo (older) and then the command line with this message:
> init: sreadahead main process (2563) terminated with status 1
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall mian process (264) termintaed with status 1
General error mounting filesystems.
maintenance shell will now be started.
Control-d will terminate this shell and re-try.

Any idea, please? Thanks very much!

---

### Post by motsteve on 2009-10-24
Do you have copy of SuperGrub?  I would make a copy of it, if you don't have it already and try that first.  It appears that grub is messed up and you aren't looking at the right info so that the machine can find your linux and initrd images.  The fstab looks mangled.  SuperGrub is a good, easy first step.  Besides that, it is one of several "must have" CD's to have for computer maintenance.  Must have:

System Rescue CD
PMagic
SuperGrub

---

### Post by ironpoa on 2009-10-24
Hi Gaiterin, 

I had this same issue.
To fixed it, is necessary to use a live cd to enter into the system.
I changed the lines in my menu.lst, just to point to kernel 2.6.31.14.
After doing that, my system started perfect.

---

### Post by gaiterin on 2009-10-24
Hi!
@motsteve Not works :(
I think the menu.lst point to wrong kernel.

@ironpoa I will try it! 

Thanks very much to you!

---

### Post by gaiterin on 2009-10-24
> **ironpoa said:**
> 
I changed the lines in my menu.lst, just to point to kernel 2.6.31.14.
After doing that, my system started perfect.

True! It works perfect for me! THANKS VERY MUCH!!!

---

### Post by monroetransfer on 2009-10-30
I've also just experienced this very nasty problem. I think it was because I had hand-edited my fstab? I dual boot windows xp (for media production mostly) and I also keep my home directory in a FAT32 partition that both windows and ubuntu can see. 

When the "unable to mount" message came up, I entered my root password and poked around a bit, and indeed my fstab is a f*cking disaster. Lines are half-commented, lines I had added are now removed... I *hate* and *dread* upgrading my ubuntu, because every time I do, all my .conf's just get spammed, rewritten, garbled, and *many* things become unusable. Of course my file system was mounted as read-only, so I couldn't just make the changes right then, even though I was root -_-'.

I'm going to try to use a live cd to make my fstab play fair. I'll probably check out menu.list, as well. I'll report back! (posting from my xp)

Also, this: :popcorn:

I've always seen that little thing on the side bar and ALWAYS wanted to use one.

(ps - why does ubuntu forums not allow "profanity"??? Aren't we mature enough to handle simple words?)

---

### Post by gaiterin on 2009-10-30
I think is more easy edit the Grub (press "e" when you're in Grub) ;) and change the kernel version.
When you boot, change the /boot/grub/grub.cnf file to the correct kernel.

I think is a problem of updater, I check the default answer about update grub: Not update grub, then I have the old entries. I must must be by defect update grub.
Best regards.

---

### Post by monroetransfer on 2009-10-30
Thank you for the advice. The lines in my menu.lst file have been changed to look like:

```

title		Ubuntu 8.04.3 LTS, kernel 2.6.31-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=a2bbf929-a163-4418-9223-05dc93905631 ro quiet splash vga=0x0305
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

```

But I am still unable to boot and receive the same error message as the first post in this thread. I'll try what you suggested (I've got a liveCD going right now, and I don't have any other burn discs, and this one's a DVD-R, so I can't try out "supergrub".)



EDIT: Well, I couldn't get it working. I tried a couple different kernel versions, but they were all borked in some way. I guess I sort of failed it by dist-upgrading such a heavily modded box as mine was. It wasn't really even ubuntu anymore. At any rate, I've just finished wiping my disc (except for my /home partition) and installing Linux Mint 6 Fluxbox CE. I have to say I am liking it way more than ubuntu and recommend anybody who reads this to switch! Ubuntu was GREAT for me once upon a time, but I've become a much better programmer, and I know a lot more about linux than I used to. Ubuntu is important I think as an introduction, or a conversion tool, but by the same stroke, this makes it unwieldy for "power-users".

---

### Post by CRIMPS on 2009-10-31
> **monroetransfer said:**
> 
(ps - why does ubuntu forums not allow "profanity"??? Aren't we mature enough to handle simple words?)

Sorry, we aren't.

---

### Post by CRIMPS on 2009-10-31
This was a problem for me as well.  I was upgrading from Ubuntu 9.04 amd64 to 9.10 amd64 via Update Manager.  When prompted with multiple windows to keep or replace my menu.lst, I chose to keep my current menu.lst as this was the default option.  I assume this is the issue.  It looks like a bug has been filed concerning this.

I guess I will try using a live CD to resolve this.  But this is rather frustrating for many users.  I will keep posted my findings.

---

### Post by wcorey on 2009-10-31
I ran into the exact same problem except I didn't get an option to change or update grub.  I started the update manager update yesterday and it hadn't finished when I left work (this after I successfully updated in place 2 other systems with no problem). I vpn'd in last night as it was finishing up the last of the downloads. I was expecting it to give me the message about obsolete packages, but it instead bumped me off and I couldn't reconnect. Today I went in and found the machine was shut off. When I restarted I got "One of more mounts listing in /etc/fstab cannot yet be mounted.

It listed /, /tmp, and /swap. /tmp it listed as null.

mountall main process terminated with status 1
general error mounting file system.

I got into the recovery shell and didn't see anything largely because / was not mounted. I didn't even realize where it put me was even on my system.

I've booted off the livecd but, in my experience, it's self contained, you don't get to see the hard drive file system. How do you accomplish that?

Walt

---

### Post by AngusM on 2009-10-31
So have we arrived at any kind of solution? I hear a lot of talk about things tried that didn't work, but little in the way of general solutions and the like. I have to go to my sister's place tomorrow and try to fix her recently-upgraded-to-9.10 system, and I'd like to know what I'm doing before hand.
The solution seems to involve a LiveCD, but everytime I follow a link that says I can download a LiveCD, it doesn't tell me where I can download a LiveCD.

---

### Post by AngusM on 2009-11-01
Well, I guess I'll never know

---

### Post by mkngl84 on 2009-11-01
On the two LiveCD issues: 
1) How to access hard drive filesystems while using LiveCD and
2) Where to get LiveCD ...

1) I suggest loading up the live CD and doing this(as root/sudo):
```
mount /dev/sdxx /mnt/
```

Replace sdxx with the device name of your root filesystem. The first x is a letter, second a number. If you don't know the number just run through different letters and numbers starting at the beginning until you find the right one.

Do ```
umount /mnt/
``` to undo.

You could mount it somewhere else but this should get the job done. Also, look into chroot coomand.

2) The LiveCD is the regular install cd. So, go to ubuntu.com and look for download and select your flavor and architecture. Burn it and there it is. Select the first entry in the boot menu and you should get to a running session off the CD where you can open the terminal, etc.

I hope this helps! Good luck.

---

### Post by CCC999 on 2009-11-01
> **gaiterin said:**
> Hi!
I upgrade the Ubuntu versions from 3 years ago, I hadn't any problem never.

But now, from Ubuntu 9.04 to 9.10 RC, the grub appears, I select the normal options, appears the Ubuntu logo (older) and then the command line with this message:


Any idea, please? Thanks very much!
gaiterin - had the exact same experience. Found my answer here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)
Hope this helps (or starts you down a path that works)....

---

### Post by deeem119 on 2009-11-02
Out of interest, which reply solved this?

I'm having the issue on a virtual machine hosted by a cloud hosting service, so can't access it with a live CD. Anyone have any idea if there is something I can do before running the release-upgrade to stop it happening? I've got current backups of the server, so I can try the upgrade happy in the knowledge that if it breaks, I can be back up and running on 9.04 in about 2 minutes. Gotta love cloud hosting.

---

### Post by rooster78383 on 2009-11-02
Same problem here. I elected to keep my current menu.lst. I can see that is refers to:

title     Ubunti 8.04, kernel 2.6.24-16-generic

I'm not a power user, but have been using Ubuntu desktop reliably for several years. This is the first time an upgrade made my computer unusable. Hoping against hope for a solution...

---

### Post by rooster78383 on 2009-11-02
SOLVED

Editing menu.lst to reference kernel 2.6.31-14-generic allowed me to boot into 9.10 properly.

This resolved the problem of:

mountall:/proc/: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted

---

### Post by Mgiacchetti on 2009-11-07
so what if i run this inside colinux, and have upgraded from a 9.04 image... and have no /boot/grub/menu.lst??   How can i fix this problem?

---

### Post by Kjeldgaard on 2009-11-20
I have made a fresh install of karmic, and I have this problem as well. Some of you solved the problem editing the /boot/grub/menu.lst file but I don't have this file. So how do I solve this problem?

---

### Post by marquinos on 2009-11-22
/boot/grub/grub.cfg
Change the permissions before ;)

---

### Post by Avantal on 2010-04-28
Have a little addition to the problem.
Got same messages after accidentally installing mountall as a dependency for some package.
So, I don't have correctly updated 9.10, just old 8.04, so correcting menu.lst to point to .31 kernel is impossible.
Is there any way to get server operational back again without reinstalling?

---

### Post by Avantal on 2010-04-28
Solved by removing mountall and reinstalling ubuntu-minmal, startup-tasks, system-services, upstart(with recomended packages) from hardy CDROM

---

