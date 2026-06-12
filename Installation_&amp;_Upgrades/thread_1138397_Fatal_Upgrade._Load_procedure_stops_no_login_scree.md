---
title: "Fatal Upgrade. Load procedure stops no login screen"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Lektorvis on 2009-04-26
Hi
Something went wrong during my attempt to upgrade. 
Now the boot procedure freezes after showing this last line:
setting Advanced Power Management level to 0xfe (254)   (OK)

I've tried the recovery menu and the previous installation entry's in Grub all with the same result.

Here's in short what I did:
I started to Upgrade on-line from 8.10 to 9.04 using Update Manager.
Before Update Manager finished downloading all packages I cancelled.
Later I downloaded the I386 ISO and upgraded from the CD-drive. 

Any suggestion on how I can log in is appreciated.

---

### Post by gugus2009 on 2009-04-26
I have some similar problems on a hp 2730p (tablet-pc).

I updated to 9.04 this morning, since this i got some awful graphics (lines and stripes) on my screen after finishing progressbar-screen.

Hope anyone can help!

---

### Post by Lektorvis on 2009-04-26
> **Lektorvis said:**
> Hi
Something went wrong during my attempt to upgrade. 
Now the boot procedure freezes after showing this last line:
setting Advanced Power Management level to 0xfe (254)   (OK)


Seems the problem have changed, so now the loading screen starts up all right but after a minute or so the screen meses up turn weird violet and then burns over in white. 

---------------------------------------------------------------
If I try to start up in Recovery mode I see something like this:

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/bc3230d8-98-4d72-bc59-c43c14212b14 does not exist. Dropping to a shell! 

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) Built-in shell(ash)
Enter 'help' for a list of built-in commands.

(initramfs) 
---------------------------------------------------------------
Does this makes sense to any of you?

---

### Post by sroerick on 2009-04-26
Same thing here. Hideous lines and boxes immediately after install.

Startup screen works well, then everything goes to hell.

I have two video cards, and there is a distinct pattern of hideous lines and boxes for either one.

---

### Post by thermobee on 2009-04-26
> **sroerick said:**
> Same thing here. Hideous lines and boxes immediately after install.

Startup screen works well, then everything goes to hell.

I have two video cards, and there is a distinct pattern of hideous lines and boxes for either one.
I have the same problem even though i only have one video card. I have been very thankful for the community on this site when it comes to helping me with problems, but ive been trying to figure out this issue for 3 days now and there has been absolutely no help. The worst part is that no one ( at least in the post that i have) has even come up and said this is the issue and we are waiting on solution or something like that.

I must underline here that I am very thankful for this website and it has been of great help every time I needed it in the past.

---

### Post by Lektorvis on 2009-04-27
I'm up and running again :guitar:

I downloaded and burned the Alternate I386 CD

In Grub I selected the previouis recovery entry, when the load proces stucked I did this:

```

ctrl + alt + f1 (to start the terminal)

```
Login with user and password

I Inserted the Alternate CD

At first I tried this code without succes:
```
sudo apt-get upgrade --fix-missing
```

And another resultless attemt too:
```
sudo apt-get install update-manager
sudo update-manager -d

```

:KS But this third hit did it for mee:
```
sudo apt-get dist-upgrade

```

I found the code here: [http://ubuntuguide.org/wiki/Ubuntu:Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")

---

