---
title: "The hard disk power management issue on laptops need to be solved. Ubuntu is unusable"
date: 2010-09-22
forum: Hardware
---

### Post by Repgahroll on 2010-09-22
Hello there.

My family just bought the 3rd laptop.

The first one was an HP dv6000, which suffered from the hard disk "clicking" issue, where the default power governor settings are too aggressive, so it keeps stopping while on battery. I skipped Ubuntu 6.10, 7.04, 7.10, and finally I was able to workaround the problem (using the command hdparm -b 254 on a script) on version 8.04.

After that one we bought an Acer One 150, the same HD problem was happening, and some other crucial features didn't work on 9.04 unr, so I just forget it and used the Windows XP.

This month we bought another laptop (because the first one's battery is lasting only 3 minutes), an ECS U40, and I've installed Ubuntu 10.04, everything was fine, the video card (Sis Mirage 3+) was very hard to install properly, and the sound controls was crashing X (because of massive notification printing) but after some fine tweak, it was working very well.

However, it suffers from the same problem (HD clicking once every 3 secs on battery), so I managed to put a script that runs 'hdparm -b 193' when the laptop is on battery. For my surprise though, after some time, the HD became corrupted, I've tried to fix it running lots of commands, without success.
Therefore, the only solution was to reformat the disk and reinstall the entire system. After reconfiguring everything again, and setting the HD power management settings to disabled (255), the battery lifetime was shortened a lot, no big problem though.

This morning though, I was working on it and plugged it in, the system was suspended (another issue?), and when I woke it up, the HD was clicking again, and I couldn't even launch another program. So I rebooted it and the same HD corruption issue happened.

This laptop has Windows Vista "Starter" installed by default, which is horrible imho, has watermarks, uses only 1GB of RAM, cannot launch more than 1 program (because antivirus and firewall are running), doesn't accept lan connections, so I was counting on Ubuntu.
I am not going to install Ubuntu again if I couldn't fix the HD (i'll try some commands from live cd).

Ubuntu (maybe Linux) isn't ready for laptops yet according to my experience, and even brands that supports the platform (like Dell) doesn't launch updates, and updating the system from the repos sometimes break the compatibility, because the drivers only work on old kernels, (an example is the Conexant softmodem driver provided by Dell), not mentioning the netbook distros, which are just a piece of crap.

I've been using Ubuntu on Desktop since 2005, and I am trying to use it on laptops since 2006 without much success, this HD issue exist since the creation of Ubuntu, and it's still affecting it even after 6 years of development.

This issue should be of vital importance in development imho. But looks like no one cares, even the checkbox "spin down hard disks when possible" on gnome-power-preferences does nothing.

Windows doesn't click the HD and the battery lasts longer (if hdparm is disabled), is it 'that' hard to do something similar on Linux?

I'll need to wait more 3~4 years to have Ubuntu working on a mobile device (Because we are not going to buy another laptop soon) and I'm not betting it will be possible. I'm seriously thinking about changing Desktop to Windows also (because it's a big pain to share files between Windows/Linux), and abandon Linux for real-life tasks, keeping it only on my old server.

If Ubuntu is for Human Beings, then i'm not human... Because actual humans need to do other things in life, they can't just sit in front of a computer and forget the world. They can't spend months just to configure and operating system, they need actual solutions. I'm not talking about GUI, Plug&Play, comfort, or "Just Works", I'm talking about the ability to get the operating system running properly, no matter how, but not requiring computer science AND computer engineering PhD skills. If I had those skills, possibly I wouldn't be so poor and would buy a high-end laptop and pay Ubuntu support.

To me it's crystal clear that the biggest difference between Ubuntu (as the easiest GNU/Linux) and the other OSs, is that Ubuntu doesn't have "classes" of users. To get it working you need to have developer knowledge, or at least a "friend" who has. While other OSs offers ways to help even the mediocre user (the one who can only use the programs) to use it and be productive. The limitation most times is the user, not the system.

An operating system should be almost unnoticeable, it should be just a way to run the programs that you actually use, but on laptops I've been using/configuring the operating system more than the programs, and when I use the programs the operating system simply destroys my work.

Thanks and sorry my english.

PS:

The error message is:
```
mounting /dev on /root/dev failed: No such file or directory
mounting /sys on /root/sys failed: No such file or directory
mounting /proc on /root/proc failed: No such file or directory
Target doesn't have /sbin/init
No init found
```

---

### Post by mastablasta on 2010-09-22
Why not buy an Ubuntu fully compatible notebook? i am sure it will work on it then and out of the box. or better yet one with Ubuntu (or other linux) preloaded. You have Dell & System 76 (ubuntu), HP (open suse), Acer (Linpus), ASUS...
 
or you can also just use Windows.
 
in fact i have one working old notebook at home which i had to equip with ubuntu because winxp was working too slow on it (not enough RAM). i am not sure what kind of click ing you are refering to, but on a notebook i have at home there is no clicking and also it's batery life was extended under Ubuntu.

---

