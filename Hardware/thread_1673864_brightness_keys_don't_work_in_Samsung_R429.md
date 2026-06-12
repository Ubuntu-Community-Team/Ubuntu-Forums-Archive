---
title: "brightness keys don't work in Samsung R429"
date: 2011-01-23
forum: Hardware
---

### Post by breaky9973 on 2011-01-23
Hi all,

The brightness keys don't work in my Samsung R429 (plus some other hot keys)

So far what I have done is added my laptop model (as R478/R429 according to dmi) to "95-keyboard-force-release.rules"

Now if I push the brightness up or down it does show the brightness slider going up or down but it doesn't do anything.

So where do I go from here?

---

### Post by studon on 2011-01-27
Hi breaky9973,

Hopefully you are sorted by now. I've justed got a Samsung RV510 working - your force release hint came in handy, so thanks for that. 

There are a couple more steps required:edit /etc/default/grub adding "acpi_backlight=vendor". 

Have a look at [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/%7Evoria/+archive/ppa") 
then sudo add-apt-repository ppa:voria/ppa 
then sudo apt-get update
then sudo apt-get install samsung-backlight
then sudo reboot

With any luck you should be sorted. 

I do note from [http://www.voria.org/forum/viewtopic.php?f=3&t=296&start=135](http://www.voria.org/forum/viewtopic.php?f=3&t=296&start=135) that                  xcflysurfer is having problems on  2.6.35-25 - I guess fortunatley for me uname -a informs the RV510 is using 2.6.35-24. 

Best regards,

studon

---

### Post by studon on 2011-01-28
'k, well having disabled voria ppa and updated to 2.6.35-25 backlight control continues to operate as before and as expected.

---

### Post by breaky9973 on 2011-02-11
Hi Studon,

Just came back from holiday so didn't have time for awhile to check the forums.

Thanks for the links to the PPA. I will try them out on my laptop and let you know the results.

---

### Post by scummie50 on 2012-01-03
Hey Studon, I just got a samsung rv510 and I'm curious if you'd be willing to do a step by step for noobs guide to fixing this problem.  I have installed ubuntu via wubi.  Just test driving it and figuring out all the bugs before I completely switch over.  The function keys seem to work, but like the other person in this thread the brightness bar shows up and moves when hitting the keys but it doesn't change anything.  I am very new to linux but have ample time to do some research if needed.

---

