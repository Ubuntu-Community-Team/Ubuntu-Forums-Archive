---
title: "Help! My system's a complete mess"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by bakaeigo on 2009-01-31
Okay, here's a little background first.

On January 29, I installed updates including a kernel update. When I rebooted, ubuntu would go through the boot sequence, then when the login window was supposed to appear, the screen went blank and into sleep mode. If I pressed Ctrl+Alt+F1, I was able to log in via the terminal and execute commands, but "startx" always failed.

So I rebooted, this time using an earlier kernel. GNOME loaded and my system was functional, but compiz didn't work as the kernel was not accepting the nvidia drivers. I read a guide online that said to un-install and reinstall the drivers, so I did that. After I rebooted into the latest kernel, every system message, even in GRUB, has mis-spelled words (For example "Wbuntw" instead of "Ubuntu" and "ggnerck" instead of "generic"). 

Now whenever I boot with *any* kernel version, the same thing happens: Words are mis-spelled in GRUB and in Ubuntu's boot sequence and the screen is sometimes randomly filled with what look like apostraphes, but the GNOME login window loads. I can log in, but it always freezes when loading my desktop, with no icons on the desktop and about half of the panel loaded. I can't get into the terminal with Ctrl+Alt+F1, the only way to get out of this is to turn the computer off.

I put in my Intrepid LiveCD so that I could back up my files before trying something else, but this doesn't work either. Everything seems to work okay until the desktop starts to load, at which point it acts almost exactly like my HD installation. The icons load and the panel mostly loads (save one or two icons) but it doesn't respond to any mouse clicks or keyboard commands.

I tried the Hardy LiveCD and even a Fedora 10 LiveCD I had, but they both did the same thing, freezing after loading the desktop.

:( First and foremost I need to save my data, but I can't with none of the liveCDs working. After I have my data backed up I guess I'll have to reformat and start fresh.

How can I get my data onto my external HDD?

Thanks for any help.

---

### Post by quirks on 2009-01-31
Try this and let me know if it works (or not):

1. When GRUB counts down from 3, press ESC.
2. Select an entry which has "recovery mode" in it.

Ubuntu then boots into text mode. From there you can work on the system from the command line. If you don't know how to use the command line, that is not much of a problem. There are plenty of people here who can guide you through (including me).

---

### Post by bakaeigo on 2009-01-31
> **quirks said:**
> Try this and let me know if it works (or not):

1. When GRUB counts down from 3, press ESC.
2. Select an entry which has "recovery mode" in it.

Ubuntu then boots into text mode. From there you can work on the system from the command line. If you don't know how to use the command line, that is not much of a problem. There are plenty of people here who can guide you through (including me).

I chose recovery mode, and after pressing Ctrl+Alt+F1 at the login window I can get to the terminal. The only problem is that the text seems to be messed up -- even the text I type. For example, my "aoeu" comes out as "coew". Strangely, this doesn't seem to have any effect on the actual operations -- Even though "iPod" is listed as "kPof", I access it by typing "iPod", even though when I type it it comes out as "krod".

So how can I copy my home folder over to my external HD? It doesn't show up in /mnt or /media.

^_^ Thanks for any help

---

### Post by quirks on 2009-01-31
You must be root to do this (in recovery mode this should automatically be the case):

```
fdisk -l
```

Paste the output of this command here. It lists the detected hard disks and the partitions on them. Once we know them, we can mount them manually.

---

### Post by bakaeigo on 2009-01-31
> **quirks said:**
> You must be root to do this (in recovery mode this should automatically be the case):

```
fdisk -l
```

Paste the output of this command here. It lists the detected hard disks and the partitions on them. Once we know them, we can mount them manually.

Unfortunately I can't paste the output of fdisk -l since there's no way to copy it over (except copying it out on paper :p) but it did show me that my external drive is located at /dev/sdb.

How do I mount /dev/sdb? I've never had to mount anything through the terminal before ...

---

### Post by quirks on 2009-01-31
> Unfortunately I can't paste the output of fdisk -l since there's no way to copy it over

Whoops, sorry, I didn't think of that.

/dev/sdb is the hard disk itself. What you need to know in order to access data on the disk is the name of the partition. This is usually the name of the hard disk and a sequential number (e.g., /dev/sdb1, /dev/sdb2, ...). The names of the partitions are listed in the table at the end of the output.

Here is how you can mount something via the command line:
```
mount /dev/sdb1 /mnt
```

This will mount the partition /dev/sdb1 to /mnt. You can mount it to another location (if there is already something in /mnt), but the directory must exist, before you can mount anything there.

---

### Post by bakaeigo on 2009-01-31
> **quirks said:**
> Whoops, sorry, I didn't think of that.

/dev/sdb is the hard disk itself. What you need to know in order to access data on the disk is the name of the partition. This is usually the name of the hard disk and a sequential number (e.g., /dev/sdb1, /dev/sdb2, ...). The names of the partitions are listed in the table at the end of the output.

Here is how you can mount something via the command line:
```
mount /dev/sdb1 /mnt
```

This will mount the partition /dev/sdb1 to /mnt. You can mount it to another location (if there is already something in /mnt), but the directory must exist, before you can mount anything there.

Thank you, this worked for me. I'm in the process of copying all of my files over now.

One last question, though: After re-installing, should I install my graphics drivers before updating the kernel again, or should I wait with my nvidia drivers until after the kernel is updated? Or should I not update the kernel at all? :) I just want to avoid another situation like this.

---

### Post by quirks on 2009-01-31
> One last question, though: After re-installing, should I install my graphics drivers before updating the kernel again, or should I wait with my nvidia drivers until after the kernel is updated?

1. I doubt that the problem was caused by a malfunctioning driver/kernel. If that had been the case, the problem should have vanished when booting the LiveCD. I suspect that there is malfunctioning hardware (e.g., RAM, hard disk, graphics card, mainboard). I recommend that you check your RAM for defects. You can use the memtest86+ option in GRUB to do that. The other hardware components are harder to test.

2. How are you going to reinstall, when not even the LiveCD works (which you need in order to install)?

3. What driver do you use? Do you use packets from the repositories (e.g., nvidia-glx-*) or do you use a driver downloaded directly from the Nvidia homepage? I recommend using one from the repository, because they have been tested better with Ubuntu. Also, it will be updated automatically, whenever you update your kernel (this is not the case, when you use an installer downloaded directly from the Nvidia homepage).

> Or should I not update the kernel at all? I just want to avoid another situation like this. 

If you're in doubt, I recommend leaving the kernel at the version that runs stable. Personally, I do not use the most current kernel either, because an older version runs more stable on my system.

---

### Post by bakaeigo on 2009-01-31
> **quirks said:**
> 1. I doubt that the problem was caused by a malfunctioning driver/kernel. If that had been the case, the problem should have vanished when booting the LiveCD. I suspect that there is malfunctioning hardware (e.g., RAM, hard disk, graphics card, mainboard). I recommend that you check your RAM for defects. You can use the memtest86+ option in GRUB to do that. The other hardware components are harder to test.

2. How are you going to reinstall, when not even the LiveCD works (which you need in order to install)?

3. What driver do you use? Do you use packets from the repositories (e.g., nvidia-glx-*) or do you use a driver downloaded directly from the Nvidia homepage? I recommend using one from the repository, because they have been tested better with Ubuntu. Also, it will be updated automatically, whenever you update your kernel (this is not the case, when you use an installer downloaded directly from the Nvidia homepage).



If you're in doubt, I recommend leaving the kernel at the version that runs stable. Personally, I do not use the most current kernel either, because an older version runs more stable on my system.

I'll do memtest86+ now. I was actually just about to ask how to get the liveCDs to work. With the "Install" option, I can get it to go as far as "Setting up partitioner" before it freezes, so maybe it's a hard drive problem? There's also a yellow box-like thing that follows the mouse, though, so it couldn't be just that. 

I use the drivers that come from the Ubuntu repository, not from the nvidia website.

..I'll post back with the results of memtest...

---

### Post by mavior on 2009-01-31
> **bakaeigo said:**
> Okay, here's a little background first.

On January 29, I installed updates including a kernel update. When I rebooted, ubuntu would go through the boot sequence, then when the login window was supposed to appear, the screen went blank and into sleep mode. If I pressed Ctrl+Alt+F1, I was able to log in via the terminal and execute commands, but "startx" always failed.


Maybe a different approach: log-in in console mode or after boot get a TTY console...then get this thing [http://mavior.eu/apt-log/](http://mavior.eu/apt-log/) (use wget).
Then query with that your logs on 29th of january and revert back each thing you changed(purging added packages). The --changes and --extra option of the program should quickly help you.

bye

---

### Post by bakaeigo on 2009-01-31
Nothing came up on Memtest... What should I do now? Should I boot Gparted? I still can't re-install with any of the LiveCDs.

Thanks for any help.

---

### Post by bakaeigo on 2009-01-31
*bump* :(

---

### Post by quirks on 2009-02-01
I think a reinstallation does not make sense until we have figured out why your system crashed in the first place.

> With the "Install" option, I can get it to go as far as "Setting up partitioner" before it freezes, so maybe it's a hard drive problem?

You don't happen to have a spare hard disk to replace the built-in one temporarily and see if you get any further?

Here is another thing you can try:

1. Log in to your old installation in recovery mode (the way I explained earlier).

2. Examine the output of dmesg and the content of /var/log/messages. Maybe these logs give you valuable information about the cause of the mess.
This will output the kernel log:
```
dmesg | less
```
This will show you the content of /var/log/messages:
```
less /var/log/messages
```
You can browse through the output with Up and Down and the PageUp and PageDown keys. You can leave "less" by pressing "q" (for "quit").

---

### Post by mavior on 2009-02-02
> **bakaeigo said:**
> Nothing came up on Memtest... What should I do now? Should I boot Gparted? I still can't re-install with any of the LiveCDs.

Thanks for any help.

Assuming that you read my previous post,would you please post the output of ```
apt-log -d 2009-01-29
```

And also of this one:
```
apt-log --changes 2009-01-29
```

---

### Post by quirks on 2009-02-02
I don't know about you, but apt-log is not a valid command on my system. And I couldn't find it in the repositories either.

---

### Post by mavior on 2009-02-02
> **quirks said:**
> I don't know about you, but apt-log is not a valid command on my system. And I couldn't find it in the repositories either.

[http://mavior.eu/apt-log/](http://mavior.eu/apt-log/)

and also read my previous  posts on this thread.

---

