---
title: "Ubuntu doesn't see windows raid 0 array"
date: 2010-10-05
forum: Hardware
---

### Post by Nate_is_cool on 2010-10-05
I have Windows 7 on a 2tb raid 0 hw array. I install Ubuntu on a separate drive and it doesnt see the array. I wanted to be able to play music/multimedia from this drive and in time make Ubuntu my main, as for now I just need it to see the drive (array)

Using the gigabyte ga-ma770-ud3. Its a hardware array of 2 WD 1TB Cavier Black. And ideas?

---

### Post by ronparent on 2010-10-05
Is your's a fakeraid? If so you may not have dmraid installed. In a terminal type dmraid -l. If not installed, install it.

> sudo apt-get install dmraid

I don't believe it installs automatically unless you are installing Ubuntu to the raid.

---

### Post by Nate_is_cool on 2010-10-06
I don't believe so. I just want to see my Windows 7 partition on my array. I installed that program but no luck. 

Ubuntu isn't on an array. nor do I want it to be on one. I just want it to see my ntfs array.

---

### Post by ronparent on 2010-10-06
If dmraid is installed in Ubuntu you will see the windows partition. If not you won't. You need dmraid to activate the raid partitions so that they may be seen.

In a terminal type:

> sudo apt-get install dmraid

If not installed, this will install it.

Whatever the outcome, what is the output of:

> sudo dmraid -ay

What do you see in the menu bar Places>Cpmputer?

---

### Post by Nate_is_cool on 2010-10-07
[QUOTE=nathan@Nathan-linux-desktop:~$ sudo dmraid -ay 
[sudo] password for nathan: 
RAID set "pdc_gjbeciae" already active
RAID set "pdc_gjbeciae1" already active
RAID set "pdc_gjbeciae2" already active
nathan@Nathan-linux-desktop:~$ 
[/QUOTE]

Now it shows up. Thanks! Quick question from keeping me from starting a new thread. My array takes like 5 minutes to power on. I'll hear the drives turn on 5 minutes after I start up my PC.

---

### Post by ronparent on 2010-10-07
I can think of nothing in any OS that would delay the power on to the drives for 5 min.s. Maybe a faulty power supply?

---

### Post by Nate_is_cool on 2010-10-07
I don't think so. Ill try switching it to a different rail. 

Why is it that my array always has a different name. How can I make a link to a folder on the array that will hold its location after a restart?

---

### Post by ronparent on 2010-10-07
> Why is it that my array always has a different name. How can I make a link to a folder on the array that will hold its location after a restart?


That doesn't sound good. It is not a good idea to move a fakeraid around. If you move it to a slots with a different raid chipset it is likely to rewrite the meta data and wipe the partition tables.

---

### Post by Nate_is_cool on 2010-10-07
I'm using the bios so setup my raid. but linux sees it as a different address each time I reboot.

---

### Post by nishtai on 2011-04-27
> **ronparent said:**
> If dmraid is installed in Ubuntu you will see the windows partition. If not you won't. You need dmraid to activate the raid partitions so that they may be seen.

In a terminal type:



If not installed, this will install it.

Whatever the outcome, what is the output of:

dmraid -ay

What do you see in the menu bar Places>Cpmputer?

Hey, I've got a problem with this. dmraid -ay says "no raid disks", although I see them from Windows and in Ubuntu, the Disc manager sees them, but I can't get them to work. 

Any help will be greatly appreciated

nishtai

---

