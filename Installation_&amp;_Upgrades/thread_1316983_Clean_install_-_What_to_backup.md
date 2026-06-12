---
title: "Clean install - What to backup?"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by B34N on 2009-11-06
I'm going to upgrade to 9.10 by doing a clean install.  There are a few program settings that I want to backup (Evolution and Firefox) but there are many programs that I don't want to bring over to the new install (failed MythTV install).  To accomplish what I want, do I only need to worry about the specific directories in the Home directory or do I need to backup additional files/directories?

Thank you!

---

### Post by Anzan on 2009-11-06
Try running

dpkg --get-selections > packages.txt

Then open the file, exclude the packages you don't want. after the install (assuming your home dir is backed up or on a separate partition) you can sudo apt-get install "the list copied from packages.txt".

The settings you need will be in the home dir.

---

### Post by audiomick on 2009-11-06
> **Anzan said:**
> Try running

dpkg --get-selections > packages.txt

Hallo.
I think I've been looking for that command for a while.

> Then open the file, exclude the packages you don't want. after the install (assuming your home dir is backed up or on a separate partition) you can sudo apt-get install "the list copied from packages.txt".


The list is long, and not really intuitive, but should do what I've been wondering about, which is

"Make it new, but just like it was"


> The settings you need will be in the home dir.

That bit works for sure; I've already discovered that, to my delight. That goes as far as Task Bar Icons magically reappearing after the appropriate program has been re-installed.

Anyway, thanks for the tip :-)
Michael

---

### Post by B34N on 2009-11-06
> **Anzan said:**
> Try running

dpkg --get-selections > packages.txt

Then open the file, exclude the packages you don't want. after the install (assuming your home dir is backed up or on a separate partition) you can sudo apt-get install "the list copied from packages.txt".

The settings you need will be in the home dir.

Thank you!  That will do nicely!

Do I need to worry about permissions or anything for the directories and files that I'm backing up from the home directory or can I just simply use the File Browser to drag a copy over to a USB drive?

---

### Post by Anzan on 2009-11-06
> **st8ofmi9d said:**
> Thank you!  That will do nicely!

Do I need to worry about permissions or anything for the directories and files that I'm backing up from the home directory or can I just simply use the File Browser to drag a copy over to a USB drive?


Hm. Not sure. But it's easy enough to chmod permissions in cli or just right-clicking and selecting it in properties.

Should be fine though.

---

### Post by solitaire on 2009-11-06
Best way is to use a FAT formatted drive for temp storage for your /home/ folder while you backup (FAT does not hold Security / owner info) So after the install you can just copy back the folders you want with no permission problems ^_^

I never take a list of the installed programs (if I need them i can install them as required.)
But i do take everything from my home and store it on a temp storage partition (see above!) So if I do need a program I've got it's config folder handy.

Then If I don't use a program after a few months I can safely delete the temp storage partition and it's files.

---

