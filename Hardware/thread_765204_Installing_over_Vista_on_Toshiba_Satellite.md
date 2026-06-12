---
title: "Installing over Vista on Toshiba Satellite?"
date: 2008-04-24
forum: Hardware
---

### Post by EnigmaX on 2008-04-24
I've recently purchased a Toshiba Satellite Laptop, which came with Win Vista (only option).  I'm really not liking Vista to much, and was wondering how much it would take to switch my laptop over to Ubuntu?  Would I run into any compatibility issue's with wireless, devices, drivers, etc?

Would it be possible to run, or somehow setup a dual boot first to ensure everything functions properly before taking 100% plunge?

Any advice to this Ubuntu noob would be GREATLY appreciated!

---

### Post by ingManiac on 2008-04-24
Hello! I own a toshiba Laptop myself. It's a P200d-11m. Ubuntu(7.10) works right out of the box, with a few little problems. Dual Boot is no problem and is the preffered type of installation.
Ubuntu 8.04 will be tested maybe this weekend.
Problems and how to solve:
Ati Radeon HD2600 - follow the wiki and use proprietary display-drivers.
Wlan: works with Ndiswrapper (be sure to disable bcm43xxfwcutter before!) follow the wiki instruction.
Sound. Works also right out of the Box, but if you plug in your headphones the laptopspeakers don't mute. I've found a way to trick it, use google and search for acer sound problem. There is a description how to set various possibilities. I found two solutions  basically working. just try.

When I'm playin with 8.04 I'll inform you.
If you have any further problems: ask. Maybe I can help you out.
It's pretty hard to find anything on the toshiba laptops, so I just tried around and after 2 weeks everything worked.

hope this helps

---

### Post by EnigmaX on 2008-04-24
ingManiac,

Thanks for the information!  I've come across the same problem, finding Ubuntu information for Toshiba's (specifically Sat's).

I'm not to familiar with Ubuntu and linux commands as far as upgrades go, but I'm willing to give it a shot.  I've installed Ubuntu once before on a Desktop and have used VM to tinker around with it.  I'm assuming I can run the Live CD option to ensure everything is compatible?  

I guess I'll go with 8.04 off the bat and see what I get, I just hope I don't screw up my new laptop lol.

I'll keep you posted on how everything comes along, might have a couple questions through the process.

---

### Post by ingManiac on 2008-04-24
Excuse me I missed the topic!
Dualboot is automatically activated when installing ubuntu.

With the installation of Ubuntu, the Bootmanager "Grub" is automatically installed.
Grub detects your Vista and you can choose on every startup If you'd like to go Ubuntu or Vista.

Ubuntu is now very stable and I had never problems when installing. Although a Backup would be worth the Time.

Short Installation Instruction:
Create 4 new Partitions
first: primary, size: 10 GB
second: extended partition: (your preffered size of Data partition)+(2 x size of your RAM)
third: primary size: your preffered size of Data partition
fourth: 2 x size of your RAM
Note! third and fourth partition must be inside the extended!

Install Ubuntu
When the screen appears where you can select the partition method, use custom! Otherwise your HDD will completely used by Ubuntu.
Mark Part1 to format(ext3) set mountpoint to /
Mark Part3 to format(ext3) set mountpoint to /home
Mark Part3 to format(swap)

follow the instructions and enjoy ubuntu on your Laptop! 

Excuse my english I'm not a native speaker!

---

### Post by Liv3dN8as on 2008-04-24
I to installed Ubuntu on a Toshiba Satellite about 6months ago. I tried a dual boot the first time and some how my bootloader got messed up. I got rid of Vista entirely. Vista stinks.
The only problem I am having as of right this minute is I can't get my function key to switch between screens to work(fn+f5). It is giving me some grief but I hope it will be resolved soon.

---

### Post by ingManiac on 2008-04-24
You won't get anyurther with the live-CD, cause your settings and Data is lost every Shut-Down.
There is a way to Use a USB-Stick to keep settings. But i don't recommend it. I tried it once, and it's awful, slow, not worth the Time.

By the way which model do you have and which Hardware?

Mine is:
AMD Athlon64 X2 Tl-60
ATI Radeon Mobility HD2600
2 GB Ram
250 GB HDD
Atheros AR5007EG wireles
Realtek High definition Audio

---

### Post by ingManiac on 2008-04-24
Hello liv3dN8as!
Is monitor switching working without the function keys?

---

### Post by Liv3dN8as on 2008-04-25
> **ingManiac said:**
> Hello liv3dN8as!
Is monitor switching working without the function keys?
I'm not sure what you mean. Is there another way to switch without using the function keys? The main reason why I would like to switch is so I can watch movies on my tv without burning them to a disc. I don't have a media center right now, so my laptop will have to do.

---

### Post by ingManiac on 2008-04-25
I used proprietary ATI-drivers. So i was able to change with ccc.
Maybe you have to configure manually TV-out in xorg.conf.

---

### Post by VMan on 2008-04-26
Which model do you have.  If it's one of the A135 series, I might be able to help with some problems.  I have 7.10 on it right now, but will be installing 8.04 this weekend (hopefully).  You might also check the laptop testing team pages.  Someone may have your exact model and already solved any problems.

---

### Post by cyc1989 on 2008-12-09
I installed Ubuntu 8.04 last 1-2 months ago.
I installed it in my laptop (TOSHIBA M100)...
and i had face some problem below...

1)when i doing mu stuff, then suddenly it jump to black screen with some words. As the picture below.

[[IMG]http://img360.imageshack.us/img360/6412/16112008nd3.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img360.imageshack.us/img360/16112008nd3.jpg/1/w320.png[/IMG]](http://g.imageshack.us/img360/16112008nd3.jpg/1/)

2) i cannot run the bluetooth.(i search nothing with my hp)

I hope that anyone who face this problem before and had already aolve it can teach me for the solution, thanks.

regards.

CYC

---

