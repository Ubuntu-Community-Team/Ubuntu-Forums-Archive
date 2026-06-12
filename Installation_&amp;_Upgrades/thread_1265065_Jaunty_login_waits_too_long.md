---
title: "Jaunty login waits too long"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by arashispencer on 2009-09-12
I've recently upgraded to Kubuntu Jaunty, but after restarts for the first time, the new Kubuntu logo appears,quite a while, and ended with the following message:

*-Boot args (cat /proc/cmdline)*

then finished with:

[I]-missing modules (cat /proc/modules;1s/dev)
ALERT! /dev/disk/by-uuid/...... does not exist. Dropping to a shell.

Result=failed[/I]:(

When I pressed 'esc' to select during the countdown, I selected the previous kernel (I think) without the recovery option, I could login but the desktop looks damaged. Something is missing or should I say, few things are... I do not have the installation cd as I upgraded online. Did not download anything too.

Should I update my kernel?
Or...?

---

### Post by running_rabbit07 on 2009-09-13
Use the recovery option and select repair packages.

---

### Post by arashispencer on 2009-09-13
Thanks... Just to make sure I know what to do when I reach the recovery option, what should I check for? I mean, I can't differentiate broken package yet...:confused:

Sad thing is, from the older kernel which I managed to login, I can't connect to the internet to update!!! I was thinking of using the terminal to update
*sudo apt-get update*
but nothing works... Not only the internet connection, many other things keep on prompting me with errors now even viewing a *.jpg image...

---

### Post by running_rabbit07 on 2009-09-13
> **arashispencer said:**
> Thanks... Just to make sure I know what to do when I reach the recovery option, what should I check for? I mean, I can't differentiate broken package yet...:confused:

Sad thing is, from the older kernel which I managed to login, I can't connect to the internet to update!!! I was thinking of using the terminal to update
*sudo apt-get update*
but nothing works... Not only the internet connection, many other things keep on prompting me with errors now even viewing a *.jpg image...

When you boot the recovery kernel there will be a small list of things to chose from. One of them is repair broken packages. That should fix you up.

---

### Post by arashispencer on 2009-09-14
Tried but...
A lot of things running initially... until..
*Begin: Waiting for root file system... ...*

Then

[I]
Done
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)[/I]


Exactly like the error on the 1st post...

At the end, there is a 
*Busybox v1.10.2 (ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)*

then

*(initramfs)* with underline waiting for command I don't know...

---

### Post by arashispencer on 2009-09-14
I managed to get a snapshot...
[ATTACH]128516[/ATTACH]

---

### Post by running_rabbit07 on 2009-09-14
I am starting to wonder if you will have to revert to Hardy or Intrepid to get your system back online. Or maybe download the ISO and do a clean install of Jaunty. Before you try reinstalling make sure you boot the LiveCD and back up your files if you don't have a /home partition.

---

### Post by arashispencer on 2009-09-14
My upgrade was actually from Hardy to Jaunty... Skipping Intrepid... Was that a possible reason?

ISO download is too slow for my connection... Requested a free cd so should be here in 10 weeks time.

Other than backing up my /home folder, how should I save my settings?

---

### Post by running_rabbit07 on 2009-09-14
> **arashispencer said:**
> My upgrade was actually from Hardy to Jaunty... Skipping Intrepid... Was that a possible reason?

ISO download is too slow for my connection... Requested a free cd so should be here in 10 weeks time.

Other than backing up my /home folder, how should I save my settings?

If you have a/home folder, then you shouldn't have anything to worry about. If you just did the factory install where there is just a swap and a / partition then you need to back up your file and in your home folder you copy all the hidden folders which are your settings.

---

