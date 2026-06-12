---
title: "Floppy drive not mounted"
date: 2009-06-18
forum: Hardware
---

### Post by Tulya on 2009-06-18
My installation of Ubuntu is from the Linux Format cover disc, which contains Intrepid with Gnome, KDE and Xfe as well as lots more apps.
I have been using this for nearly six months now and everything is working perfectly

Except

The other day I had to format a floppy disk and found I had no floppy drive mounted..
It is not listed in fstab or mtab and lshw does not find it.

LiveCD versions of PCLinux and Mepis8 find it and mount it at bootup.

So, my question is, has floppy drive support been dropped from Ubuntu, or do I have a problem?

---

### Post by wpshooter on 2009-06-18
That's a good question, I will try to remember to check when I get home to my great little Ubuntu machine !!!

---

### Post by jlh68 on 2009-06-18
Good question, I have not had floppy support since version 7.10.  I have submitted several bug reports to the Launchpad Ubuntu, without ever getting enough info to get it working. > 255651@bugs.launchpad.net

Responses I get from launchpad indicate 1.  That someon is working on it, 2. a fix has been made (although I don't get it to work), 3.  who knows what is happening on it.

Good luck and maybe someone will respond to this thread with something that will work.

Basically at this point with my two desktops, the only thing that dies not work is being able to use the floppy drives.

---

### Post by Tulya on 2009-06-18
So it`s not just me then!

---

### Post by wpshooter on 2009-06-19
I just tried it on 9.04 and my floppy works just fine.  Comes up under PLACES upon initial boot, stick a floppy in the drive and it works fine.  Can then dismount it and remount it just fine.

---

### Post by jlh68 on 2009-06-27
I sure wonder why it worked on your (**wpshooter**) computer and not mine.

All I have is a floppy LED that stays on all the time.  I do not get any floppy icon in  my places menu.

It would be nice if someone would direct me in the way to even start digging into my computer to find out what file(s) could be missing or miss-configured. Then maybe I could get some resolution.

---

