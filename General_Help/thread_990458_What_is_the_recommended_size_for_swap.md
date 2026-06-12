---
title: "What is the recommended size for swap"
date: 2008-11-22
forum: General Help
---

### Post by ubix on 2008-11-22
Does anybody know if the recommendation for the swap space remains to be double of your RAM size, ie. if RAM is 3 GB should the swap space be 6 GB. My dual boot 8.04 Ubuntu system keeps crashing after selecting either OS in GRUB. I install Ubuntu behind WinXP. I reinstalled both OS'es after I changed motherboard and added 2 GB RAM. Now I have 3GB RAM and as I have said I did set swap space to 6 GB.

---

### Post by scragar on 2008-11-22
That used to be true, it's not now, personaly I have 1GB of ram and 512MB of swap, I have never needed anymore, and honestly I don't think I will(and if needed you can always make swap larger).

---

### Post by ubix on 2008-11-22
> **scragar said:**
> . . .(and if needed you can always make swap larger).That is not true if you use a separate partition rather than swap file! Elaborate file system layout has many advantages over a single fs. When you use 15 fileystems, it is not easy and very time consuming to change sizes.

Please see also ( [Error18 selected cylinder exceeds BIOS]("http://ubuntuforums.org/showthread.php?t=990505")) :confused:This may be related?

---

### Post by kerry_s on 2008-11-22
if i had 3gig ram i wouldn't even bother with swap.

---

### Post by sdennie on 2008-11-22
As kerry_s said, with 3G of RAM, unless you know you are going to be doing RAM intensive things, swap isn't strictly needed.  I would still recommend having it though.  If you are going to be using the hibernate functionality of the computer, you'll need swap at least as large as your memory.  Also, swap is good in that, if I remember correctly, running out of memory (and swap) does more graceful things with at least a little bit of swap.

---

### Post by ubix on 2008-11-23
There's plenty of talk about swap here, but nobody really makes a convincing argument or demonstrates what is the current situation regarding the size recommendations. Some  talk like ram is a very precious commodity but the truth is its the cheapest thing this days.  Unix/Linux philosophy is built around swap, and ram size plays a role.  _**However, my real problem is my boot problem, namely for some reason I can't boot now after I've changed my mother board**_. I get the following error and system hangs after that:```
Error 18 selected cylinder exceeds maximum supported by BIOS.
```Swap is just one of the possible things that came to my mind which could have gone wrong.  It is very time consuming to test a dual/boot system for all the possibilities. I have been installing such system configurations for over 10 years and have never got stuck so persistently. It usually meant GRUB problems or order of Windows and Unix/Lunux partitions. With ***[COLOR="Blue"]Hardy[/COLOR]*** installation of systems with multiple partitions and particularly multios systems become somewhat broken. And now this ***Error 18*** came out of the blue!

I was hoping somebody in Ubuntu community would have heard about similar problem, since it is very consistent and persistent.

---

### Post by DGortze380 on 2008-11-23
What is your new mobo?

What size is your hdd? Sounds like grub can't access the correct portion of your hdd to boot. Could be a mobo problem, hdd problem, or grub problem. 

After a big change like a mobo upgrade, I would recommend a reinstall if it's feasible. But at least backup your files and reinstall grub.

---

### Post by Dr Small on 2008-11-23
My SWAP space is 260MBs, and it never gets used. At one point, I just eliminated SWAP altogether.

---

### Post by DGortze380 on 2008-11-23
> **ubix said:**
> u]**However, my real problem is my boot problem, namely for some reason I can't boot now after I've changed my mother board**[/u].


I would suggest asking an admin to change the thread title to something like that. Or start a new thread for the separate question.

---

### Post by scragar on 2008-11-23
> **Dr Small said:**
> My SWAP space is 260MBs, and it never gets used. At one point, I just eliminated SWAP altogether.

I have a tendency to use swapoff from time to time, but when ram runs low I tend to swap it back on before I risk running out.

---

### Post by Slim Odds on 2008-11-23
> **scragar said:**
> I have a tendency to use swapoff from time to time, but when ram runs low I tend to swap it back on before I risk running out.

LOL, why don't you just leave it ON and let linux figure it out for you?

:lolflag:

---

### Post by scragar on 2008-11-23
> **Slim Odds said:**
> LOL, why don't you just leave it ON and let linux figure it out for you?

:lolflag:

Because swapoff is the only way I know of to make linux take what's in swap and move it back into ram, even if you change the swapiness it changes nothing about how it pulls information back from swap.

---

### Post by Slim Odds on 2008-11-23
ubix, Ubuntu is not designed to allow you to just change the motherboard without letting it know. That may actually be one area that Windows is better.

Check the BIOS settings on the new motherboard with respects to disk access. You may need to change it.

---

### Post by ubix on 2008-11-23
> **DGortze380 said:**
> What is your new mobo?

What size is your hdd? Sounds like grub can't access the correct portion of your hdd to boot. Could be a mobo problem, hdd problem, or grub problem. 

After a big change like a mobo upgrade, I would recommend a reinstall if it's feasible. But at least backup your files and reinstall grub.

You did not see I have done everything you are saying. I have other threads going just about this problem and have above already provided a link to one ( [_[COLOR="MediumTurquoise"]Error18 selected cylinder exceeds BIOS[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=990505")) and here's another one by someone else ([_[COLOR="Cyan"]http://ubuntuforums.org/showthread.php?t=990086[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=990086") my post is the 4th one in this thread). Nobody seems to care or knows what I am talking about. When I'm done testing I'll update these threads.

---

### Post by ubix on 2008-11-23
> **Slim Odds said:**
> ubix, Ubuntu is not designed to allow you to just change the motherboard without letting it know. That may actually be one area that Windows is better.

Check the BIOS settings on the new motherboard with respects to disk access. You may need to change it.Dream on Windows is better nowhere. It is the biggest f**kup in the computer industry:mad: Linux doesn't care if you change the motherboard - it works just fine with any change you make to the HW as long as it is supported HW. Windows dies if for nothing else for the registration and other proprietary nonsense ;)

---

### Post by ubix on 2008-11-23
The problem is resolved and described here:  ( [[color=green]*Error18 selected cylinder exceeds BIOS*[/color]]("http://ubuntuforums.org/showthread.php?t=990505") ) :)

---

### Post by Slim Odds on 2008-11-30
> **ubix said:**
> Dream on Windows is better nowhere. It is the biggest f**kup in the computer industry:mad: Linux doesn't care if you change the motherboard - it works just fine with any change you make to the HW as long as it is supported HW. Windows dies if for nothing else for the registration and other proprietary nonsense ;)

OK fanboy, but I've been around the block a few times and like to keep a little closer to the facts.

I'm no fan of windows and put forth plenty of criticism. But there are some things that it does reasonably well, and detecting hardware changes and dealing with them is one of them.

Ubuntu is plenty good at detecting the initial hardware and installing the proper drivers, etc. It's not so good with major changes like a whole new motherboard.

Your last sentence is especially funny.

Use whatever spare change you have to buy a clue and come back later.

---

### Post by sdennie on 2008-11-30
Please keep it civil.  If you want to argue Ubuntu vs. Windows, the Recurring Discussions forum is the proper place to do it: [http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by Outdoor83 on 2009-06-21
There were two questions.  Swap size was answered.  I'll answer the other one.  This is an adaptation of the old Gentoo guide for installing a mbr to Ubuntu programs.  A reinstallation of the mbr could fix you right up.

First, burn an Ubuntu CD of any kind (if you don't have one).  Boot into it, and get to a root command line.

```
mkdir /media/hdd
mount /dev/sda1 /media/hdd (this assumes /dev/sda1 is your Linux partition.  Substitute as appropriate)
cd /media/hdd
mount -t proc proc /media/hdd/proc
chroot /media/hdd /bin/bash (this gets you, basically, on your hdd)
grep -v rootfs /proc/mounts > /etc/mtab
/usr/sbin/update-grub
```

What you're doing is mounting your Linux partition, chroot'ing into it (basically just making that folder the new "root" of your shell; type 'exit' to get out if it) so Grub doesn't get confused, establishes what folders are mounted where for Grub to find, then reinstalls the mbr of the system.

I know this thread is 6 months old, but maybe this helps the next person.

---

