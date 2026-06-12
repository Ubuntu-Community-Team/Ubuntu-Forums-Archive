---
title: "Clean Install Advice? I want to keep track of what's already installed?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2009-09-21
I went from a Wubi install, converted to a hard disk install of 8.10, to an upgrade to 9.04, and there's enough that's sort of flakey that I think I want to do a fresh install when Karmic is released. My machine is dual boot (XP + Ubuntu), and my working data is on a separate NTFS partition that is being shared with XP.

I've added lots of programs and tweaks along the way, and while recreating won't be the end of the world, I'm wondering if there's an efficient process to somehow inventorying (and potentially saving) what I have.

I'm pretty new to this, so any help is appreciated.

---

### Post by presence1960 on 2009-09-21
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

> dpkg --get-selections > ~/my-packages


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository.

---

### Post by drs305 on 2009-09-21
You can now also create a list of installed apps with Synaptic.

System, Administration, Synaptic: File > Save Markings.
Enter a /path/name for the new list.
Be sure to check/enable "Save full state, not only changes" or you will probably create an empty file.

To import the list, you would use the "Read Markings" option.

---

### Post by donato roque on 2009-09-21
@drs305:  I use Synaptic's Save Markings to save all my packages for a reinstall or an upgrade later.  But I have not tried restoring from the file using Read Markings.  Hope it works.

---

### Post by drs305 on 2009-09-21
> **donato roque said:**
> @drs305:  I use Synaptic's Save Markings to save all my packages for a reinstall or an upgrade later.  But I have not tried restoring from the file using Read Markings.  Hope it works.

I have generated the list several times and inspected the contents - I see no reason why it won't work as designed. The one thing to be sure of is to mark the "Save full state" and check the file size after running it. In my tests, not marking the "Save full state" created a file, but it was always 0 bytes.

---

### Post by c5vetter on 2009-09-21
okay, relative newb to Ubuntu - installed 9.0.4 using Wubi, and have been told some of the files did not install properly - have been advised to do a "reload" from a LiveCD - just received a CD from Canonical today

so, ready to do the install, but had a question or two - this thread seems to be perhaps what I need to do??? will using Synaptics Save Markings save everything?

by everything, will it save the CUPS settings for printers; wireless settings; Thunderbird settings, such as Address Book

bottom line - I need to be able to save all of my current settings - is this possible? know that for instance within XP, I can reinstall certain parts of the OS - so, is that possible in Ubuntu?

---

