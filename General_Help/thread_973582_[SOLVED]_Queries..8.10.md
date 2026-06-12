---
title: "[SOLVED] Queries..8.10?"
date: 2008-11-06
forum: General Help
---

### Post by Yezinki on 2008-11-06
[B]Hello every one,

I am new to Ubuntu after spending 15 years with windows.......I shall be grateful if you could take the time & reply to my issues which may be simple to you but not a new bie like me?

1. I have a Sony Vaio machine VGC-LS1......2 GB physical ram @ 667MHZ, T2400 CPU,  250 GB HD.  [http://reviews.cnet.com/desktops/sony-vaio-vgc-ls1/4505-3118_7-32028400.html](http://reviews.cnet.com/desktops/sony-vaio-vgc-ls1/4505-3118_7-32028400.html)

2. I would prefer I OS ie Ubuntu on it.........whether hardy or 8.10.....which do you recommend?

3. How would you size the partitions, during a clean install?

4. What file system shall you use....ext 3 or XFS?

5. How an one link a data/storage partition to /home....if for some reason OS has to be reinstalled only / would need a format?

6. Why does anything which is downloaded goes in /, My Documents & not /home?

7. When VBOX installs a software/OS, where are these drives created?

8. What is the utilization of wine?

9. How to open/run Linux file formats like tar etc.?

10. Personally what would you recommend for me:

    a. Ubuntu 8.10

    b. Ubuntu hardy.
  
    c. Dual boot with XP MCE & either of Ubuntu.

11. The cons of this machine is that does not have a separate graphics card rather uses 128 MB of physical ram & uses Intel 945 GM mobile graphics accelerator.

12 I have installed a usb optical drive since its generic DVD RAM is very picky about media?

Hoping to hear from you smart, intelligent Ubuntu geniuses,

Regards,

Yezinki.[/B]

---

### Post by Yezinki on 2008-11-06
Hi there,

Shall be grateful even if could answer any.........

Regards,

Yezinki.

PS:** WRDN, cdtech** if you are on-line kindly answer in depth........considering the ocean of Linux knowledge you got.

---

### Post by beno1990 on 2008-11-06
> **Yezinki said:**
> [B]Hello every one,

I am new to Ubuntu after spending 15 years with windows.......I shall be grateful if you could take the time & reply to my issues which may be simple to you but not a new bie like me?

1. I have a Sony Vaio machine VGC-LS1......2 GB physical ram @ 667MHZ, T2400 CPU,  250 GB HD.  [http://reviews.cnet.com/desktops/sony-vaio-vgc-ls1/4505-3118_7-32028400.html](http://reviews.cnet.com/desktops/sony-vaio-vgc-ls1/4505-3118_7-32028400.html)


Well more than enough to run Ubuntu.

> 
2. I would prefer I OS ie Ubuntu on it.........whether hardy or 8.10.....which do you recommend?


Intrepid Ibex (8.10). It fixes a lot of problems that were in Hardy Heron.

> 
3. How would you size the partitions, during a clean install?


If you're using only Ubuntu, I'd say a 2GB Swap partition, 100MB~ /boot partition, and the rest for /. You could also use the defaults, it sets it to a common and typical desktop partition setup.

> 
4. What file system shall you use....ext 3 or XFS?


ext3 is normally good enough for a desktop computer.

> 
5. How an one link a data/storage partition to /home....if for some reason OS has to be reinstalled only / would need a format?


Just set /home as a separate partition in the partition manager. If you do that setup, make /usr about 16GB, / (root) about 8GB, and the rest in /home, in addition to the partition sizes I gave above.

If you reinstall the OS later on, you would just need to tell the partitioner NOT to reformat the /home partition.

> 
6. Why does anything which is downloaded goes in /, My Documents & not /home?


You can change your default download location in your browser.

> 
7. When VBOX installs a software/OS, where are these drives created?


You can set that in the program by selecting a directory.

> 
8. What is the utilization of wine?


Can you clarify that? It's simply to run Windows programs on Linux, often games and such. But it's not 100% reliable and not all programs work with it, and others have glitches or stability problems in Wine.

> 
9. How to open/run Linux file formats like tar etc.?


If you're in Nautilus, it should open the archive manager automatically when you double click the archive.

> 
10. Personally what would you recommend for me:

    a. Ubuntu 8.10

    b. Ubuntu hardy.
  
    c. Dual boot with XP MCE & either of Ubuntu.


That's down to what you want to use your computer for. Personally I'd say go for 8.10 Intrepid Ibex. But you might want a second opinion, which is always a good idea.

> 
11. The cons of this machine is that does not have a separate graphics card rather uses 128 MB of physical ram & uses Intel 945 GM mobile graphics accelerator.


That's a common situation with OEM computers/laptops. Most embedded devices are Linux compatible, though.

> 
12 I have installed a usb optical drive since its generic DVD RAM is very picky about media?


Can you clarify that one please?

---

### Post by benhur99ph on 2008-11-06
Dude... you got a lot of questions there. I would want to answer it one by one... but... I recommend that you do try installing Ubuntu first. There are plenty of step by step installation instructions around ... and I doubt that you need one because the installation is a very straight-forward process. As a tip, run the LIVE-CD first and try it for yourself. When running the LIVE-CD, you should see an icon on the desktop named "install". If you are installing it on a dedicated machine, you do not need to concern yourself with partitions and such. Just accept the defaults (or use the entire disc). I recommend installing Ubuntu 8.10 since it is the latest.

After the successful installation, you should be able to use it right away. As far as opening file formats like tar, its easy. I think gnome can handle it, if not just search for some commonly used linux commands. It's really easy. 

For your inquiries about Vbox... you can read the documentation on their website for an in depth explantion. 

The best way is to try it first hand. Get your hands dirty. That, for me, is the best way to learn.

Hope this helps even if only a little.

Happy Ubuntu-ing! 
-Ben

---

### Post by James- on 2008-11-06
> 1. I have a Sony Vaio machine VGC-LS1......2 GB physical ram @ 667MHZ, T2400 CPU, 250 GB HD. [http://reviews.cnet.com/desktops/son...-32028400.html](http://reviews.cnet.com/desktops/son...-32028400.html)

Ubuntu only needs 256MB ram to run not a problem

> 
2. I would prefer I OS ie Ubuntu on it.........whether hardy or 8.10.....which do you recommend?

I recommend 8.10 better screen detection: I remember always trying to fiddle with screen resolution back in the day(Dell XPS 1920x1200)

> 
3. How would you size the partitions, during a clean install?

200MB for /boot
*insert your ram here* for SWAP
16-20GB /
*rest* /home

> 
4. What file system shall you use....ext 3 or XFS?

if you ever want to resize go with ext3(atleast you can do it)
other than that no diff really

> 
6. Why does anything which is downloaded goes in /, My Documents & not /home?

firefox setting..you can change it

> 
8. What is the utilization of wine?

Run windows apps on linux(only use it if you HAVE to: linux alternitives are out there)

> 
9. How to open/run Linux file formats like tar etc.?

it comes with an archieve manager if you want rar support just install "rar" and "unrar" through package manager
> 
10. Personally what would you recommend for me:

a. Ubuntu 8.10

b. Ubuntu hardy.

c. Dual boot with XP MCE & either of Ubuntu.

Dual boot only if you have proprietary software that you can't live without. If not 8.10 ftw(see #2)

> 
11. The cons of this machine is that does not have a separate graphics card rather uses 128 MB of physical ram & uses Intel 945 GM mobile graphics accelerator.

it's still strong enough to run ubuntu (dunno about compiz(probably))

> 
12 I have installed a usb optical drive since its generic DVD RAM is very picky about media?

K3B is a very nice burning tool and Linux has support for almost everything

---

### Post by Yezinki on 2008-11-06
Thanks for all your replies,

At the moment am using Ubuntu 8.10 on the sony machine.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
How do you see these partitions.........expert comments!

Thanks!

---

### Post by James- on 2008-11-06
I do recommend a 200MB part for /boot, I was trying to upgrade 8.04 to 8.10 @ work with 100MB and said I needed more space(because 60% was already in use)

---

### Post by Yezinki on 2008-11-06
What is Boot partition, size 200 MB for?

Can I create that in here using G parted?

Regards,

Yezinki.

---

### Post by James- on 2008-11-06
Your swap is a little big... 2GB will be fine(its like the page file in windows, only used if memory is over flowing)

p.s. boot is just to fix a partition dedicated to /boot kinda like home it's optional because / englobes it

---

### Post by Yezinki on 2008-11-06
So you mean there shall be :

1. Boot

2. /.

3. /home.

4. /swap

Yes??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
> **James- said:**
> Your swap is a little big... 2GB will be fine(its like the page file in windows, only used if memory is over flowing)

p.s. boot is just to fix a partition dedicated to /boot kinda like home it's optional because / englobes it

How do I create Boot & resize swap?

Regards,

Yezinki.

---

### Post by James- on 2008-11-06
> **Yezinki said:**
> So you mean there shall be :

1. Boot

2. /.

3. /home.

4. /swap

Yes??

Regards,

Yezinki.

as I said boot is totally optional I only put it because I wanted dedicated hard drive for that folder but I ran into trouble while setting it too low

if you don't want any issues:
/
/home
/swap

---

### Post by James- on 2008-11-06
> **Yezinki said:**
> How do I create Boot & resize swap?

Regards,

Yezinki.

right click on swap: Resize/Move
if you are now booted in ubuntu you will have to reboot in live CD and reinstall 

if you are in the liveCD installing then just proceed with the resize

---

### Post by Yezinki on 2008-11-06
[B]Should I resize swap?

How could I link/home & data partitions.

The DVD RAM drive easily reads only Verbatim media??[/B]

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
I am booted in Ubuntu.

---

### Post by Yezinki on 2008-11-06
Why would I need to **reinstall** after resizing & rebooting?

Regards,

Yezinki.

---

### Post by James- on 2008-11-06
> **Yezinki said:**
> Why would I need to **reinstall** after resizing & rebooting?

Regards,

Yezinki.

because resizing swap is a pain in the @$$ specially when LiveCD auto-mounts it

---

### Post by Yezinki on 2008-11-07
Thanks for the clarification.

Since I uncheck hibernation in windows , won't Ubuntu need even a smaller swap ...just a guess?

Where are features like Hibernation, standby, Hard drive to keep running or stop after a specific time etc present?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-07
What's the use of StartUp-Manager Utility?

Regards,

Yezinki.

---

### Post by beno1990 on 2008-11-07
> **Yezinki said:**
> What is Boot partition, size 200 MB for?

Can I create that in here using G parted?

Regards,

Yezinki.

It stores all of the files required for booting your computer, like your bootloader and kernel images.

EDIT: Oops, seems I didn't notice that the thread was already two pages long when I posted, so my reply is well behind the flow of the thread now.

---

### Post by Yezinki on 2008-11-07
Hi there beno1990,

Could you care to make a partition strategy plan for Ubuntu only & a dual boot of XP MCE & Ubuntu, on the 250 GB HD.

Personally would like a single OS i.e Ubuntu only.....but want to get familiar with it first......

Regards,

Yezinki.

---

