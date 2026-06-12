---
title: "Experiencing memory leaks in gam_server? Here's a fix."
date: 2005-12-04
forum: General Help
---

### Post by magnusbb on 2005-12-04
I found my system extremely slow the other day, and went to the system monitor to find out what was going on. I found a process called **gam_server** taking up some 100 MB of my memory. That's much fore a process I've never heard about! The name reminds me of some malicious software lurking in the shadows of Kaaza.

But, it's actually called Gamin, and is an extension to FAM (the File Alteration Monitor) which is pretty essential for seamless file management. The problem is, the version bundled with Breezy is 0.1.5 and it has a couple of serious memory leaks - once you've got them, even killing the process will not help you. It will be leaking again, untill you restart your computer.

Well, but, there is an easy fix to this. Just go download version 0.1.7:

```
http://www.gnome.org/~veillard/gamin/sources/gamin-0.1.7.tar.gz
```

Unzip, open the directory and do a

```
./configure && make
```

I didn't run into any dependency problems - I think this one is pretty independent. As for the final step I always use the nifty tool **checkinstall** to install my compiled code. It creates a .deb, that can be easily installed and of course, uninstalled if it does not work for you. But depending on your wishes, do either a:

```
sudo make install
```

or a:

```
sudo checkinstall
```

The last thing to do is to kill the process "gam_server" using your System Monitor, or whatever you prefer, and to log out and back in.

I hope it works for you. My system is "stable" again. Perhaps some of the people complaining about a slow Breezy installation, is actually experiencing a memory leak from the gam_server?

Give me your thoughts.

---

### Post by dalee on 2005-12-04
Hi,

Thanks for the tip. I wasn't really having any mem leaks that I could see with it. But, forewarned is to be forearmed.

I didn't use checkinstall, but rather ran it through alien, converted and installed fine.

Thanks again!
Dalee

---

### Post by magnusbb on 2005-12-04
Perhaps it was the placebo effect, but, looking at where it is located, it seems that my compiled versions installs somewhere else than the Ubuntu native version of Gamin.

So, looking at the process monitor, it is still running version 0.1.5 and not the new one. How can that be? How do overwrite the old one?

This is a serious problem in Ubuntu Breezy, and it has to be fixed, if it shall remain as a stable system!

I am sorry about this, it may not work.

---

### Post by jjmckay on 2005-12-04
This happens to me as well and the newest version of gamin (0.1.17)does not fix this.  This is a high impact bug that needs to be escalated to (k)ubuntu.  As far as I know, they are not fixing this, but it is affecting a lot of users.

My symptom is this:

Access a mounted NTFS partition (by default in /media), especially a folder with a lot of files, and gam_server will immediately jump up to between %10 and %40 cpu utilizaiton.  The process locks up the computer for about 1/5 of a second on my machine every 3 seconds or so, an annoying symptom.

I've reinstalled kubuntu 3 times and this issue with gam_server still happens.  When I was using Ubuntu (5.10), it did not happen for me.

PLEASE HELP US ubuntu/kubuntu staff!

---

### Post by jjmckay on 2005-12-04
Other aspects to this issue:

* simply killing the process does not fix it for me.  It immediately restarts and is at the same percentage of utilization.

* opening a folder with a lot of files in konqueror (or using command line) has a more dramatic effect than a folder with only a few.  A folder with just a few files may not cause any issue with gam_server cpu utilization.

* I play mp3 files on an ntfs folder using XMMS but this does not cause the symptom.

---

### Post by jjmckay on 2005-12-04
My hardware is as follows (to assist in diagnosing this issue):

AMD64 3200+, 939 socket, i386 build of os, nforce4 motherboard (msi neo 4).  I have four hard drives, one of which is on a SATA bus.  No matter which hard disk I access (all have NTFS volumes), I get the same issue with gam_server eating cpu.

Video card - nvidia 6600GT.   Two DVD drives, one is burner.  Sound card is SB audigy pro.  usb mouse & keyboard.  I also have a usb webcam logitech orbit.

*shrug*

---

### Post by magnusbb on 2005-12-05
[QUOTE=jjmckay]This happens to me as well and the newest version of gamin (0.1.17)does not fix this.  [/QUOTE]

Did you install this using my method? If yes, that method isn't correct. It installs to a different place than 0.1.5 and therefore Ubuntu continues to use 0.1.5 even if 0.1.7 is installed. If we just figure out how to replace 0.1.5 with 0.1.7 the problem would be fixed.

The problem is, that 0.1.5 has some memory leaks in the interaction with inotify - a part of the Linux kernel which monitors changes in the file system (fx. used with Beagle). My current workaround, which I read in an earlier post, is to:

```
sudo nano /boot/grub/menu.list
```

And add the word **noinotify** at the end of this line, so that it reads:

```
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda5 ro quiet splash noinotify
```

This will disable the inotify feature, but it doesn't affect your system unless use Beagle. And it's a temponary fix for the leak. But it's not good enough.

---

### Post by magnusbb on 2005-12-05
Running with this tip for a few hours, gam_server leaks again. This is really a problem. Does somebody know any more?

---

### Post by WorLord on 2005-12-06
I've installed Gamin packages from Dapper... none of them seemed to have dependencies.  I was able to install just Gamin, libgam, and python-gam without incident, restarted Gnome, and appear to be using Dapper's (v. 0.1.7).

Memory consumption on my current system appears to be solid at 2.7mb, no matter where I browse on my filesystem, what filesystem I'm browsing, or anything else.

To do this, download these three files to a directory[1]:

[Gamin]("http://archive.ubuntulinux.org/ubuntu/pool/main/g/gamin/gamin_0.1.7-2ubuntu1_i386.deb")
[LibGamin]("http://archive.ubuntulinux.org/ubuntu/pool/main/g/gamin/libgamin0_0.1.7-2ubuntu1_i386.deb")
[Python-2.4_Gamin]("http://archive.ubuntulinux.org/ubuntu/pool/main/g/gamin/python2.4-gamin_0.1.7-2ubuntu1_i386.deb")

Change into that directory, and use DPKG to install:

```
sudo dpkg -i *.deb
```

Log out of Gnome, and log in again.  You should now be using the new Gamin.

[1] - If you're not using Intel32 based things, don't download these - get the right packages for your system.  They're in the same directory, just with different names.

---

### Post by whiskybar on 2005-12-08
I backported gamin-0.1.7-2 from debian. The memory leak is gone but it still uses about 13% CPU time after one day or so. That is too much for my system I guess (AMD64-3000+ Kubuntu Breezy AMD64). Restarting the process does not solve the problem.

What is your CPU usage with gamin (the process gam_server)?

TIA,
jbar

---

### Post by toppledgod on 2005-12-11
Mr. Worlord,
I followed your instructions and can see the 0.1.7-2 versions of all three.  Logged out of Gnome and X and have found my memory to be a much better 4.1mb, but the CPU still hovers between 73-78%.

---

### Post by g-a-c on 2005-12-20
This seems to have fixed the problem on my laptop, was getting unbearable on a 256Mb machine! Now all I need to do is fix the Firefox memory leaks when I leave it open too long and I'm sorted :)

---

### Post by asktoby on 2006-01-06
I am suffering from this gamin gam_server problem on my Kubuntu box (KDE3.5 on Linux 2.6.12-10-386)

I initially installed gamin 0.1.7 from source using './config; make; #make install' but this did not solve the problem. Like magnusbb was earlier in the thread, I suspect that I am still running the older version. (Not sure how to discover this, it's not shown in 'top' or 'ps ax')

I want to install the 0.1.7 packages from Dapper. Now I am stuck with a quandry as to what to do about this source install:

Should I do a 'make uninstall' of my new gamin? I'm terrified that this will remove gamin completely from my system and leave me crippled.

Should I just leave my new 'from source' gamin installed? Try to ignore it and put the Dapper packages over the top?

If you have any advice, I would love to hear it.

---

### Post by Titanium on 2006-01-06
Is there any official word on this bug?

I'm experiencing the same problem with KDE 3.5, kernel 2.6.12-10-386, and have to kill gam_server every 6-7 hours because it consumes all of my available memory (400-500 real, 600-700 virtual). Right now it only uses ~33MB, but it's stuck at using 17% of my CPU (Athlon64 3200+). The only solution I found on the forums that should work for everyone is setting up a cron job to kill it every hour.

---

### Post by asktoby on 2006-01-06
Yep there is an official word on it. It is marked resolved in the gamin bug tracker and should be fixed in the latest version.

My problem is how to go about getting the latest version installed properly now that I've tried to do it via the source.

---

### Post by magnusbb on 2006-01-06
This should have been fixed a long time ago. But, for now, the solution is to download the gamin package from Dapper - I did it, and my system is now normal. I experienced 100-200 MB of gam_server usage. Now my gam_server never passes 2 MB.

---

### Post by uglysmurf on 2006-01-31
I was encountering the same problem in Breezy, seemingly out of nowhere.  I followed WorLord's instructions, rebooted, and things seem all better now.

Thanks!

---

### Post by uglysmurf on 2006-01-31
Just noticed that my Applications menu was no longer displaying, and after some fishing around it seems to apply to [ubuntu  bug 20216]("http://bugzilla.ubuntu.com/show_bug.cgi?id=20216") ...see also [gnome bug 323064]("http://bugzilla.gnome.org/show_bug.cgi?id=323064")...

If you're having this symptom after following the instructions in this thread to use Dapper's gamin 0.1.7, try removing the dead symbolic link /etc/xdg/menus/debian-menu.menu

---

