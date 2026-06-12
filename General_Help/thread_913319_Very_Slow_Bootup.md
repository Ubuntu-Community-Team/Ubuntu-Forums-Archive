---
title: "Very Slow Bootup"
date: 2008-09-07
forum: General Help
---

### Post by solarwind on 2008-09-07
Hey all, I have a Dell Inspiron 6000 laptop with an Intel Pentium M processor at 1.86 GHz. I'm dual booting my 100 GB drive with with windows xp (70 GB) and Linux on 4 logical partitions (7 GB /, 15 /home, some swap and boot space). I have 1 GB RAM.

Here's the problem:

I measured the boot time from the time I press the enter key on the GRUB menu for each operating system:

Windows: 50 seconds to a fully usable desktop.
Ubuntu Linux: 1:40 to a fully usable desktop. During the Ubuntu boot process, the progress bar moves back and forth a few times and freezes in the middle like this for 30 seconds:

```
[           =====            ]
```

and moves a few pixels forward. This takes up around 30 to 40 seconds. After that, the progress bar turns into a *real* progress bar (as in, it moves from start to finish, not back and forth) and boots normally.

Does anyone have any idea why this is happening? This doesn't happen on my desktops and is really slowing down my boot process. By the way, I'm using JFS for all my Linux partitions except for /boot (that one's using ext2).

---

### Post by Pelham123 on 2008-09-07
Have you tried booting without the splash screen. i.e - replacing 'splash' with 'nosplash' at the grub menu? This may tell you where system is hanging.

Also /var/log files may help? dmesg, bootlog etc..

---

### Post by solarwind on 2008-09-07
> **Pelham123 said:**
> Have you tried booting without the splash screen. i.e - replacing 'splash' with 'nosplash' at the grub menu? This may tell you where system is hanging.

Also /var/log files may help? dmesg, bootlog etc..

Thanks for the tip. I totally forgot about that. I'll try it now and post a reply.

---

### Post by OutOfReach on 2008-09-07
Hmm, I too have this problem, with the same exact processor (Intel Pentium M at 1.86GHz) But with a Dell XPS M140.

---

### Post by solarwind on 2008-09-07
Ok, after using the nosplash option, I found that it hangs here:

Starting up...
Loading... Please wait...
---> This is where it freezes for 30 - 40 seconds <---

Note: the first two lines may not be the exact words used, but it went something like that. The two lines were printed and it froze for 30 - 40 seconds then booted up as usual. I got no useful output. How do I get the thing to be more verbose?

---

### Post by edm1 on 2008-09-07
You have to remove 'quiet' from the grub menu.

---

### Post by solarwind on 2008-09-07
> **edm1 said:**
> You have to remove 'quiet' from the grub menu.

Yeah, just did that too. Now I know where it's hanging, but I can't remember the line. Where are the boot logs stored in Ubuntu? I'm used to Arch Linux.

Edit: nevermind, I have to enable bootlogging. Let me do that first.

---

### Post by solarwind on 2008-09-07
I posted my boot logs on the next post.

---

### Post by solarwind on 2008-09-10
Bump. Anyone? I can't figure out the problem.

Link to my logs: [http://www.paste.metafy.org/view.php?file=YrubEjUdUbeq.txt&language=](http://www.paste.metafy.org/view.php?file=YrubEjUdUbeq.txt&language=) (same thing as posted above).

---

### Post by solarwind on 2008-09-11
Bump?

---

### Post by Pelham123 on 2008-09-12
I am curious about this entry in the logs:

audit(1220814764.786:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5015 profile="/usr/sbin/cupsd" namespace="default"

Having tried a google for it, it is posted as a bug, but without any further posts, or problems it may cause...

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/234491](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/234491)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg853447.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg853447.html)

Fairly old posts, but if this helps. Or maybe just confuses the issue :confused:

---

### Post by solarwind on 2008-09-12
> **Pelham123 said:**
> I am curious about this entry in the logs:

audit(1220814764.786:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5015 profile="/usr/sbin/cupsd" namespace="default"

Having tried a google for it, it is posted as a bug, but without any further posts, or problems it may cause...

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/234491](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/234491)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg853447.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg853447.html)

Fairly old posts, but if this helps. Or maybe just confuses the issue :confused:

Hmmm, so should I disable cups?

---

### Post by Pelham123 on 2008-09-13
One last try for me. Could you post your /var/log/dmesg file? The timings may be a little clearer, as previous log file were a bit jumbled.

Honestly dont know about the inode_permission and cupsd, seems like it causes printing problems rather than slow boots. Would be interesting to see your file permissions on /usr/sbin/cupsd tho

Mine:

-rwxr-xr-x 1 root root 382920 2008-04-21 21:18 /usr/sbin/cupsd

Dont know how much I can help :(

---

### Post by solarwind on 2008-09-13
> **Pelham123 said:**
> One last try for me. Could you post your /var/log/dmesg file? The timings may be a little clearer, as previous log file were a bit jumbled.

Honestly dont know about the inode_permission and cupsd, seems like it causes printing problems rather than slow boots. Would be interesting to see your file permissions on /usr/sbin/cupsd tho

Mine:

-rwxr-xr-x 1 root root 382920 2008-04-21 21:18 /usr/sbin/cupsd

Dont know how much I can help :(

Here's my /var/log/dmesg: [http://www.paste.metafy.org/view.php?file=pAdagezyhatA.txt&language=](http://www.paste.metafy.org/view.php?file=pAdagezyhatA.txt&language=)

This is the permission on /usr/sbin/cupsd

-rwxr-xr-x  1 root    root     382920 2008-04-21 16:18 cupsd

---

### Post by Pelham123 on 2008-09-14
Thanks for posting /log...hasnt really helped us much. You could try this utility:

[http://www.bootchart.org/](http://www.bootchart.org/)

Shows a schematic of your bootprocess, havnt used it personally, but worth a look?

Good luck

---

### Post by solarwind on 2008-09-14
> **Pelham123 said:**
> Thanks for posting /log...hasnt really helped us much. You could try this utility:

[http://www.bootchart.org/](http://www.bootchart.org/)

Shows a schematic of your bootprocess, havnt used it personally, but worth a look?

Good luck

Will use that. Reinstalled twice. Same problem. Other distros like Arch Linux have no problems but I want to put Ubuntu on my laptop for simplicity.

---

### Post by solarwind on 2008-09-14
Here's my bootchart:
[[IMG]http://img134.imageshack.us/img134/7206/hardy200809148lu1.th.png[/IMG]](http://img134.imageshack.us/my.php?image=hardy200809148lu1.png)

I don't really know what I'm looking at (don't know how to analyze bootcharts). Can anyone see anything wrong with it?

---

### Post by solarwind on 2008-09-14
I just realized that it says the time is 33 seconds. But I assure you, boot times are well over a minute. Perhaps the lag is happening BEFORE init is getting called - i.e., during the kernel load process. I'll try compiling my own kernel and see how it goes.

---

### Post by solarwind on 2008-09-15
Yes! Yes it works, I knew it!

The problem was happening during the pre-init stage, while the kernel was setting itself up. I compiled a vanilla kernel from kernel.org and installed it. The boot works normally now but for some reason I see a white screen after I login (after GDM). No gnome desktop.

I can see the mouse and move it around but I see a white screen. Hmm...

I am using the ati drivers through envy. Could this be a problem? I reinstalled through envy -t but still same problem.

---

### Post by Pelham123 on 2008-09-16
> **solarwind said:**
> Yes! Yes it works, I knew it!

Nice work :)


Seems like white screen has caused a few problems with ATI. Take a look:

[http://ge.ubuntuforums.com/showthread.php?t=714034](http://ge.ubuntuforums.com/showthread.php?t=714034)

---

### Post by solarwind on 2008-09-16
> **Pelham123 said:**
> Nice work :)


Seems like white screen has caused a few problems with ATI. Take a look:

[http://ge.ubuntuforums.com/showthread.php?t=714034](http://ge.ubuntuforums.com/showthread.php?t=714034)

Solved it by properly generating debian packages for the kernel, installing and reinstalling the binary ATI driver.

---

### Post by Camilia on 2008-10-28
> **Pelham123 said:**
> Have you tried booting without the splash screen. i.e - replacing 'splash' with 'nosplash' at the grub menu? This may tell you where system is hanging.

Also /var/log files may help? dmesg, bootlog etc..

How is this done? Where is the /var/log file?
My splash screen is on for 20 seconds.

---

