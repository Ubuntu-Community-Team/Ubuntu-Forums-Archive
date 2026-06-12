---
title: "Lenovo y510 - Bad sound"
date: 2008-08-03
forum: General Help
---

### Post by crazysteve on 2008-08-03
Hello all,

I have used Ubuntu for years now, and have gotten away without posting a thing due to the fact that this forum is great. 

I just installed ubuntu on a lenovo ideapad y510, and the sound is not as good as it should be. It has dolby digital surround sound with a subwoofer, but it sounds just like any other laptop. Ubuntu is the best out there, but right now it just does not know how to use my sound card. 

A few things to note...

I have ubuntu 8.04. I tried to install 3 operating systems out of the box, but the partitioning did not go well and I had to do a complete system restore. I now have vista (it sounds amazing), and ubuntu (it sound bad).

There are lots of postings on the y510 and sound, but no solutions have worked for me. I do not know why opening 

 /etc/modprobe.d/alsa-base file 

and adding 

options snd-hda-intel model=lenovo-ms7195-dig

to it does not solve the problem when it has helped others. I do not see LFE (subwoofer) setting anywhere.

Another thing to note is the fact that when I go to System > Preferences > Sound and choose OSS, the sound is louder then when I choose ALSA. 

I have tried and tried, but have not found a solution. Help!

---

### Post by sroske on 2008-08-04
I did it too and got the LF subwoofer setting, as well as the others, they just don't do anything. The drivers on this laptop are all proprietary, so this accounts for many problems. I really wish teh s-video worked, for example. Perhaps if we pester lenovo they might release driver for linux. We can only try!

---

### Post by evets25 on 2008-08-07
If you read through the "Y510 is a GO!" thread, you'll see that you have to manually compile a newer version of alsa-base in order to get it working. Sounds scary, I know, bu there's detailed instructions right in the thread. Just follow the steps and you'll be fine. Myself and others on this forum who own a Y510 HAVE gotten it working, so don't give up!

---

### Post by KaiSkylerBliss on 2011-03-14
This just worked for me on Ubuntu 10.10

/etc/modprobe.d/alsa-base file 

and adding 

options snd-hda-intel model=lenovo-ms7195-dig

Then reboot and everything works, even the sub!

---

