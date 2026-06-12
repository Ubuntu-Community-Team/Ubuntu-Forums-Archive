---
title: "Sony Vaio w/NVIDIA g210m Screen/Resolution issues"
date: 2010-07-03
forum: Hardware
---

### Post by IEngineer on 2010-07-03
Ok so here is the deal... and this is my very first post every so please go easy on the noobness... I have a Sony Vaio Vpccw17fx with NVIDIA g210m graphics card with cuda and it is a 64-bit. I installed Ubuntu 9.10 and everything works great until I try to activate the restricted graphics card I reboot and get a black screen and I hear the login sound. So I searched the net and found this page: [http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)     

I did everything that was explained in the posts and I rebooted and I was surprised to see that I no longer had a black screen but I have 6 separate little screens with gray horizontal bars separating them and a big black bar right down the middle of the screen. I also tried the -->   Option   "NoValidation" "NoTotalSizeCheck"  but that didn't seem to do anything. I have tried searching all over the internet for a solution to this and I cant seem to find one. I have also tried installing the driver manually and I get the same results. So if some one could please please help me with this I would greatly appreciate it! I have spent one to many days on this and I am all out of ideas. So hopefully someone with infinitely more knowledge about ubuntu can give me a fix for this. And again I am new to Linux so please be patient with me.

---

### Post by IEngineer on 2010-07-03
YAY!!!!! I finally figured it out!!! After a little more searching and some luck I stumbled upon this page--->   [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)
and I used the custom EDID path that was described on the page and that seemed to do the trick!!! I was so excited when I rebooted to find that I had full resolution and 3D acceleration!!! So all in all i hope that this can help some one else out and save them a bunch of time! Im not sure if it works on 10.04 but I will soon find out..:)

---

