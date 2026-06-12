---
title: "external harddrive with music &amp; pictures"
date: 2009-02-19
forum: Hardware
---

### Post by c3tb0x on 2009-02-19
Hi :)

I recently downloaded xubuntu, I can't remember the right version but it was 8.x.x. 
And all my life I've been using Windows but I am just simply sick and tired of the whole Windows thing. So I tried Xubuntu and I feel like installing it on my Acer Extensa 5220 laptop, instead of having Vista. 
But can I access my external harddrive on xubuntu? The directory or what, it is quite confusing!

Currently I am running xubuntu with VMware Workstation..

---

### Post by mikewhatever on 2009-02-19
You should try booting from the installation cd and trying Xubuntu. This way, you can test almost anything without making any permanent changes. There should be no problem to access an external hdd.

---

### Post by astro-swe on 2009-02-19
> **mikewhatever said:**
> There should be no problem to access an external hdd.

Hi all!
Well ain't that quote spot on :) There really SHOULD'NT be, but unfortunally there are. Way too often, I've learnt. But with a good fix the problem will not reaccur for the same user again, hopefully haha.

c3tb0x; First off, there's tons of information on the subject. Work the search engines, you'll learn ALOT that way :) When running commands use a Terminal. Follow these steps to find/narrow down the solution and of course report back if it works out, and if not what happens.

1. Have you looked in the **/media** and **/mnt** dir? That's where drives are auto mounted.

2. If the drive wasn't unmounted correctly before unplugging when used last time that may result in the drive not being mounted at all, since the mount program then requires the **-o force** option which is used at own risk. Run **man mount** later on to the get some info on that. Plug it into a Windows box and be sure to unmount it properly.


3. If that didnt work out you gotta find out if linux even detects it.
Unplug the drive. Run **ls -l /dev | grep -E 'sd|hd'** to list detected devices but only show the ones that has the words sd or hd in their name. Plug it in, wait a second and run the command again - notice any changes about the output?

Detected harddrives are usually named **sdX** where X is any (uncapitalized) letter. Partitions on the drive are named **sdX1**, **sdX2** and so on.

If you now know the device name and partition number you can try mount it manually:
[B]sudo mkdir /media/usb_test
sudo mount -t auto /dev/[/B]sdX#** /media/usb_test**


Well, good luck! :D

Edit: Oh, just checked up on this and realized that you dont express any real problems with the disk and that you're maybe running xubuntu via wmware from windows? haha.. Been too dug into, now solved, HDD problems last week :) ...

---

