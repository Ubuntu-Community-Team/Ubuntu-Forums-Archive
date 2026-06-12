---
title: "Help! Sound problem ubunto melt-down."
date: 2008-09-01
forum: General Help
---

### Post by enderal on 2008-09-01
Help!

I was using the tutorial Sticky: Comprehensive Sound Problem Solutions Guide and followed the instructions.

I did...
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then...
sudo apt-get install linux-sound-base alsa-base alsa-utils

I did see that it said...
"VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following

Code:
sudo apt-get install gdm ubuntu-desktop"

But since I didn't understand what that meant, I rebooted and am now stuck with a dos screen and command line.

I was able to log in and I tried running the command above...
sudo apt-get install gdm ubuntu-desktop

but no help.

Anything I can do short of reinstalling? I hope not because I was just getting things the way I wanted and don't want to go through that all over again.

Thank you.

---

### Post by stoneage on 2008-09-01
As far as I know there should be no problem installing from the command line in those circumstances. I take it you know now that gdm is Gnome Display Manager ?

What message did the apt-get install command return ?

---

### Post by enderal on 2008-09-01
It says...

"Could not resolve [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) failed to fetch.

I guess because there is no internet connection.

---

### Post by enderal on 2008-09-01
I wonder if there are any files I can get off the CD to get this up and running?

---

### Post by stoneage on 2008-09-01
Yeah, they should be on the disc. Open it with the package manager.

I'm not an Ubuntu Guru, do you need a Desktop to access the net ?

---

### Post by enderal on 2008-09-01
When I shut down out of the screen it said it was shutting down wlan0 so that means it must be running but no way to tell if it is accessing the wireless driver.

---

### Post by Elfy on 2008-09-01
Except you can't get to the desktop - you could try editing the sources list while in recovery mode and enabling the livecd as a source. Assuming that you have the cd in your sources but that it is disabled do this - 

boot into recovery mode and use the menu to get to the root prompt

open the file for editing with this command

```
nano -B /etc/apt/sources.list
```

You will have a line, hopefully, that looks like this remove the #

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
```

any lines below that which start deb or deb-src put a # in front of them - the only line without the # should be the cdrom line.

Close and save nano with Ctrl+O, enter, Ctrl+X

Update the sources 
```
apt-get update
```

and try to install gdm and ubuntu-desktop again

```
apt-get install gdm ubuntu-desktop
```

---

### Post by enderal on 2008-09-01
Thanks. But it didn't work.

It is not reading the cdrom. It told me to use apt-cdrom to add it but I tried and it didn't work. Maybe there is a path I need to know to the CD.

I tried the whole thing a couple times and did all I could.

---

### Post by stoneage on 2008-09-01
sudo apt-cdrom add ?

---

### Post by enderal on 2008-09-01
> sudo apt-cdrom add

Yep. That part worked. Still it complained about duplicates after I ran apt-get update and after running apt-get install gdm ubuntu-desktop it told me to run apt-get update.

---

### Post by stoneage on 2008-09-01
What was the exact message ?

apt-get update should resolve duplicates

When you opened sources.list did you leave any uncommented ?

---

### Post by enderal on 2008-09-01
Yes I did miss an uncommented line. Line 2 under my nose.

After running: 
apt-get install gdm ubuntu-desktop


Error: 
"Package gdm is not available, but is referred to by another package. This may mean that the packaage is missing, has been obsoleted, or is only available from another source.
E: Package gdm has no installation candidate."

I tried running the commands before and after running:
sudo apt-cdrom add

---

### Post by stoneage on 2008-09-01
OK, did you get ubuntu-desktop installed ?
Are you running from the live CD ? Have a look at the last post here:-http://ubuntuforums.org/showthread.php?t=627906

---

### Post by enderal on 2008-09-01
I panicked in the beginning. This is the first time I've ever used "help" in the subject line and I made two posts on this site.

Minky311 suggested I try startx and it did get me in. There are some desktop files missing and the volume control problem is still there.

Is there any way to know which lines on the sources file I commented?

---

### Post by stoneage on 2008-09-01
If you have a gui now, go to Administration => Software Sources and check the ones you want to use in the Third Party Software tab. 

main
universe
security updates
recommended updates
restricted and multiverse are optional
you could leave out source code unless you build from source and want it updated.


Basically, this sort of thing:-

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe restricted multiverse main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports universe main multiverse restricted

---

### Post by enderal on 2008-09-01
Actually, I can tell which lines because the ones I commented don't have a space after the comment.

But there are other things wrong and since this is such a new install I don't want to compound errors and I will not be able to trust the  so will likely bite the bullet and reinstall, pity that it is.

Thanks so much for your assistance.

---

