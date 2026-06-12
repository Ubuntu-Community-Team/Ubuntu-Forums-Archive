---
title: "Complete Reinstall"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by jsdieorksw on 2009-07-27
Will a re-install of Ubuntu completely delete all of the settings and bugs and stuff? I'm trying to clear my harddrive (if anyone can give me the easiest way to do this too I would be much obliged) so I can then re-install Ubuntu without all of the changes I've done to system over the years and start from scratch.  My computer's been lagging lately and I want to just "start over from scratch"

---

### Post by philcamlin on 2009-07-27
yes it will all be gone

to do this you boot into the live cd 
install gparted
go to terminal and type sudo gparted format the hdd 
go back to the desktop 
click install icon on desktop 
there you go :popcorn:

---

### Post by jsdieorksw on 2009-07-27
This might be a stupid question but I'm running 9.04, do I have to use a 9.04 live cd or can I use one of the older ones? The only reason I ask is because at the moment I only have a live cd of 7.04

---

### Post by Ratscallion on 2009-07-27
I think you could just try a ```
sudo apt-get install gparted
``` in your Live CD. Then you can do it from there.

---

### Post by lisati on 2009-07-27
> **jsdieorksw said:**
> This might be a stupid question but I'm running 9.04, do I have to use a 9.04 live cd or can I use one of the older ones? The only reason I ask is because at the moment I only have a live cd of 7.04

You can use just about ANY Live CD, but I'd advise that you try to get hold of a newer version than 7.04, because otherwise you won't be able to easily apply updates.

---

### Post by philcamlin on 2009-07-27
7.04 is allright but higher is better im most cases 
8.04 lts is good also most people have 9.04 though so help is more supported because more people are running it

---

### Post by merlinus on 2009-07-27
An easier option is to boot from the live cd, select install, and at the partitioning screen choose use entire disk.

---

### Post by jsdieorksw on 2009-07-27
> **merlinus said:**
> An easier option is to boot from the live cd, select install, and at the partitioning screen choose use entire disk.

This seems the easiest option, will this really delete EVERYTHING? All settings, bugs, and crap that's slowing my system down?

---

### Post by Ratscallion on 2009-07-27
> **jsdieorksw said:**
> This seems the easiest option, will this really delete EVERYTHING? All settings, bugs, and crap that's slowing my system down?

Yup, absolutely everything. All settings, files, programs, everything.

---

### Post by merlinus on 2009-07-27
If you are concerned that something will not be overwitten during formatting, then use dban first to completely wipe everything on your hdd.

[http://www.dban.org/](http://www.dban.org/)

---

