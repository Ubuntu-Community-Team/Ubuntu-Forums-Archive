---
title: "Just Installed, so of course some problems"
date: 2008-10-07
forum: General Help
---

### Post by jonathan041 on 2008-10-07
Allright ubuntu community.  Here's my story.

So I was using the Live CD, checking things out, said wow, its pretty nice and decided to install.  I clicked it and there you go.

The problem is, you're gonna laugh, is there a way i can get back to the windows that was previously installed on this thing?  

or did i completely kick windows off of my entire system?  

If i did kick it off oh well, but if there is a way to get back to it, that would be kind of cool too.  so far i have rebooted and there is no option whatsoever to try and switch, which is why im already jumping to that conclusion that it is completely gone.

i guess its fine, but if you could let me know how to force quit something that would be great.  haha, thanks all.

---

### Post by mrtomservo on 2008-10-07
Hmmm.  Well under normal conditions if you had both Windows and Ubuntu on your machine, you would be presented with a boot loader menu allow you to choose which OS you want to run.  Chances are if you're not getting the choice, you probably wiped out your Windows.  :(  This is by no means a definitive answer though! 

You could try viewing the file /boot/grub/menu.lst and see if it has a listing for Windows that isn't commented out.

---

### Post by jonathan041 on 2008-10-07
yea i was just using the live cd, clicked on the install thing and that was it.  

when i do boot up i get my thinkvantage notice (because it is a lenovo) and then it starts booting ubuntu.

it looks like it is gone, soo, i dont know.  if anyone else can think of something let me know.

if it looks like windows is dead in the water for my laptop...then hook me up with some links.  things i should know about, how to customize the look of it, and other things.

i basically have a brand new computer.

---

### Post by 16777216 on 2008-10-07
LOL, Glad to see the los of Windows is OK with you.
You can press **ESC** right before Ubuntu starts to load to get a boot menu. ( You should see a message like, "Loading GRUB... press ESC in *n* seconds for boot menu." with the *n* counting down from around five seconds or so. )

As for themes, Icons, etc., [gnome look]("http://www.gnome-look.org/") is the place. ( Unless you are using Kubuntu then [KDE look]("http://www.kde-look.org/") is where you want to go all of the "*-look.org" sites are linked at the top. )

---

### Post by mrtomservo on 2008-10-07
[https://help.ubuntu.com/community/Beginners/Guide]("https://help.ubuntu.com/community/Beginners/Guide")

[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

Might be some places to get some useful info.  The switch from Windows to Ubuntu can be tough if it's forced on you.  Me, it took about a month before I was comfortable.  That really stinks that the Ubuntu install removed your Window partition.  I don't know how old your laptop is, or if it came with recovery discs, but that might be an option if you don't wanna dive head first into Ubuntu.

Some basic stuff you might wanna check for customizing...
On the Menu: System, Preferences, Appearance

I personally use Evolution for my email, Rhythmbox for my music, and Open Office for my word processing.

---

### Post by christianvaldes on 2008-10-07
> **mrtomservo said:**
> [https://help.ubuntu.com/community/Beginners/Guide]("https://help.ubuntu.com/community/Beginners/Guide")

[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

Might be some places to get some useful info.  The switch from Windows to Ubuntu can be tough if it's forced on you.  Me, it took about a month before I was comfortable.  That really stinks that the Ubuntu install removed your Window partition.  I don't know how old your laptop is, or if it came with recovery discs, but that might be an option if you don't wanna dive head first into Ubuntu.

Some basic stuff you might wanna check for customizing...
On the Menu: System, Preferences, Appearance

I personally use Evolution for my email, Rhythmbox for my music, and Open Office for my word processing.

Is there an sudo apt-get install
for Rhythmbox

---

### Post by Steve1961 on 2008-10-07
Lets first check if your windows partition really has gone.  Boot into your Ubuntu system and from the applications menu choose accessories and then terminal.  In the terminal that opens type this:

```
sudo fdisk -l
```

Enter your password when asked and then post the output here

---

### Post by jonathan041 on 2008-10-07
is this it?


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
jonathan@jonathan-laptop:~$

---

### Post by Soupcan on 2008-10-07
> **christianvaldes said:**
> Is there an sudo apt-get install
for Rhythmbox
I believe that it comes pre-installed. It should be under Sound & Video in the Applications menu. As for installing it from terminal, you got it. ```
sudo apt-get install rhythmbox
```
Copy and paste what your terminal said exactly. It's ctrl+shift+c to copy in the terminal, in case you didn't know. It took me a while to figure that out.

---

### Post by Steve1961 on 2008-10-07
> **jonathan041 said:**
> is this it?


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
jonathan@jonathan-laptop:~$


no, my guess is you used a one rather than a small L.  Just copy and paste this command into the terminal and re-post:

sudo fdisk -l

you should get something that looks similat to this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4312    34634848+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4313        9729    43512052+   5  Extended
/dev/sda5            4313        9501    41680611   83  Linux
/dev/sda6            9502        9729     1831378+  82  Linux swap / Solaris

---

### Post by karlr42 on 2008-10-07
> **jonathan041 said:**
> is this it?


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
jonathan@jonathan-laptop:~$

You typed it in wrong. It's sudo fdisk -l    that's an "el"(L) at the end.

---

### Post by jonathan041 on 2008-10-07
> **Steve1961 said:**
> no, my guess is you used a one rather than a small L.  Just copy and paste this command into the terminal and re-post:

sudo fdisk -l

you should get something that looks similat to this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4312    34634848+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4313        9729    43512052+   5  Extended
/dev/sda5            4313        9501    41680611   83  Linux
/dev/sda6            9502        9729     1831378+  82  Linux swap / Solaris



ok i got this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
jonathan@jonathan-laptop:~$

---

### Post by Soupcan on 2008-10-07
> **jonathan041 said:**
> ok i got this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
jonathan@jonathan-laptop:~$

It seems that Windows is no longer there. The same thing happened to me when I installed, Vista was wiped off my system. Of course, that didn't bother me.

---

### Post by Steve1961 on 2008-10-07
> **jonathan041 said:**
> ok i got this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
jonathan@jonathan-laptop:~$

Sorry to tell you this, but windows has gone!  Your whole disc is now taken by Linux.  Hey, it could be the best thing that's happened, so look on the bright side.  Many of us here use Linux as our primary or only system, and for good reasons.  Welcome to the community!!  Even if it was forced on you somewhat.  If you need any help just post your questions here

---

### Post by karlr42 on 2008-10-07
Yep, you've wiped Windows :(

---

### Post by philidox on 2008-10-07
Just so you know for next time Ubuntu live cd has an feature during installation that allows you to import Windows into the grub menu.  To make things even easier you can install ubuntu from WITHIN windows like a video game.  The only difference is when you install from within windows the windows boot loader ask you for os of choice.

---

### Post by jonathan041 on 2008-10-07
yea it looks like it is gone, and i am kind of ok with it, it is a learning process and i well, im gonna have to try real hard to see whats up.

i will read the help links that i saw earlier in this post.

so far it is running ok, had to restart once because the bottom panel was kind of buggy.  so i will be here if i have problems.

thanks for the welcome.  and any other helpful tips i should know of RIGHT NOW, would definitely be very cool.

---

### Post by Steve1961 on 2008-10-07
> **jonathan041 said:**
> yea it looks like it is gone, and i am kind of ok with it, it is a learning process and i well, im gonna have to try real hard to see whats up.

i will read the help links that i saw earlier in this post.

so far it is running ok, had to restart once because the bottom panel was kind of buggy.  so i will be here if i have problems.

thanks for the welcome.  and any other helpful tips i should know of RIGHT NOW, would definitely be very cool.

First things first, UPDATE

sudo apt-get update
sudo apt-get upgrade

Just enter each command in the terminal in turn.

---

### Post by jonathan041 on 2008-10-07
ohh yea, as soon as i booted up it had about 128 updates. hahaha.  

here's another question, since i am seriously new to this.

do i need like a firewall or a virus scanner?  it seems like a no, but i have to ask.

laugh all you want, you are dealing with the biggest newbie on these forums.

---

### Post by Steve1961 on 2008-10-07
> **jonathan041 said:**
> ohh yea, as soon as i booted up it had about 128 updates. hahaha.  

here's another question, since i am seriously new to this.

do i need like a firewall or a virus scanner?  it seems like a no, but i have to ask.

laugh all you want, you are dealing with the biggest newbie on these forums.

A firewall is a good idea, but you don't need a virus scanner.  For the firewall do:

sudo apt-get install firestarter

You will then find firestarter in the System menu.  Just launch it and follow along

By the way, the updates are important as they solve lots of issues.  Just bite the bullet and do it

---

### Post by jonathan041 on 2008-10-07
cool, thanks for the firewall suggestion.  and i did do all the updates.  i guess i made it sound like i laughed them off, like i used to with windows.  

thanks you have been a huge help dude!!!!

---

