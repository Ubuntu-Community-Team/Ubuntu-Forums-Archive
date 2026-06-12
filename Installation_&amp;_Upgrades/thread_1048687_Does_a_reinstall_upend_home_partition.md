---
title: "Does a reinstall upend /home partition"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by mailforbiz on 2009-01-23
Hi 

I have finally gathered the courage to upgrade my main laptop from 8.04 to Intrepid (I was holding off until now because I can't afford to run into issues with the new version and be stalled). The following is my partition scheme -its a dual boot because I need to have M$ exchange for a variety of reasons. 

```
Vista (primary)
Vista (primary)
/     (primary)
/home (extended logical)
/tmp  (extended logical)
swap  (extended logical)

```
From what I understand, its safe for me to reformat/reinstall on /, reformat /tmp and swap (just for the heck), and leave /home alone with all of my data and applications.
 
Am I missing something? What all will be touched on /home if anything? I thought of backup/restore of /home but that wouldn't do much good if application directories have anyways changed from 8.04 to 8.10.


Thanks in advance,
HT

---

### Post by taurus on 2009-01-23
If you want to do a fresh install of intrepid, just follow the screen until you get to the partition part.  Pick Manual option and make sure you mount the right partitions as / and /tmp.  Click the check mark to format them.  Now, mount whichever partition for your old /home to /home and _do not_ format that partition or all your data will be gone.  You don't have to do anything with the swap partition since the installer knows what to do with it.

---

### Post by mailforbiz on 2009-01-24
But won't some files be lost in the home directory as well because I'll need to recreate the linux user? For eg., bashrc will be lost, no? I just wanted to get some idea as to what all application data will be touched in /home by doing a reinstall this way. Ofcourse, I could find out the hard way. :p


> **taurus said:**
> If you want to do a fresh install of intrepid, just follow the screen until you get to the partition part.  Pick Manual option and make sure you mount the right partitions as / and /tmp.  Click the check mark to format them.  Now, mount whichever partition for your old /home to /home and _do not_ format that partition or all your data will be gone.  You don't have to do anything with the swap partition since the installer knows what to do with it.

---

### Post by mailforbiz on 2009-01-25
FWIW, I reinstalled on / and /tmp and everything went just fine. I did have some missing application links on the main panel but that I'd expected. Getting my wireless and Bluetooth travel mouse working was a breeze compared to Hardy. I still have some odd issues lingering from the Hardy install but am very happy with so far as a lot of issues have been fixed eg. bluetooth mouse losing connection after sometimed. Some of the tricky issues are:

[LIST]
[*]on Resume from Suspend, the password dialog box doesn't show up  after a couple of times, get either a blank screen or some messed up graphical artifacts
[*]streaming video on certain websites don't work eg cnn.com
[*]firefox *hung* once - there was a lot of scripting on the page
[*]gedit takes a while to load for large files
[/LIST]

Will keep you updated on how I fare on those and other ones not discovered yet.

---

