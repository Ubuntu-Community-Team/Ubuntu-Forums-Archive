---
title: "How to boot Vista in vmware"
date: 2008-09-13
forum: General Help
---

### Post by azathrael on 2008-09-13
Hello, I am a Ubuntu newbie and I got frustrated of having to reboot for Vista (I am currently dual booting Vista and Ubuntu, with Vista being on one HDD and Ubuntu on a separate HDD).  I heard about vmware from my friend so I downloaded the vmware server to try and boot Vista from it.  I tried looking for guides online and in this forum, but I did not have much luck.

Is there a way for me to boot Vista that is already installed on vmware server? Can someone give me a guide how to go about doing this without crashing everything and having to reinstall everything all over again?

Thanks in advance.

---

### Post by DanDwalker on 2008-09-13
Mis read the post the first time, think your out of luck on that one mate.  Reason being vmware just creates a virtual machine out of storage on the current partition.  That is my understanding anyways

---

### Post by Tag_yer_dead on 2008-09-13
Dan is correct, vmware is just a way to run exe programs through emulation.  I think you may be out of luck.

---

### Post by DanDwalker on 2008-09-13
i'm still pondering it though, because if i remember on one of my previous endeavors using linux i remember duel booting with vista lingering in the background (this is a clean build just ubuntu) but i remember being able to see all of the files on the other partition.  So if you could grab those files toss them on a thumb drive or external than get the usb devices working once you get vista installed on a vmware build you could move your data but the apps would still be in the registry and you would be forced to reinstall all of that regardless.

UNLESS if you tried using something like Norton ghost to create an image of your vista build you may be able to use that image to install a build into VMWare, however doing something like that would be a pain in the neck because of the compression on ghost however it may work... acronis would probably be a better solution but not sure never used either just know how they work.

If you were going to do this, i would highly recommend backing everything up first as well use VirtualBox, i use VMWare but virtualbox runs smoother and it sounds like you still want to have some usefulness... to the apps anyways.

sorry for the rant... if anyone has an idea on that, don't see why norton's go back utility or whatever they have wouldn't work as far as i know it just creates an iso that you reinstall

if you try this i would love to know the results as it would be a slim but possible solution

-DanDWalker

---

### Post by cariboo on 2008-09-13
I'm not sure but I seem to remember that you could only run Vista Business or Ultimate in a vm. If you have Home Basic or Premium they won't work.

Jim

---

### Post by DanDwalker on 2008-09-13
I have home premium currently installed on both VMware and Virtualbox. major difference and reason i use VMWare is because it supports the 64bit os over virtual box who only does 32bit...

However the virtual machine shouldn't be biased of the OS. it just creates a virtual pc for the most part

-DanDWalker

---

### Post by DanDwalker on 2008-09-13
So i think i figured out the final solution, create a virtual partition and use acronis to load the restore that it creates and you should be golden, double checked with a few people who know the software better than i do and said it should be fine.

---

