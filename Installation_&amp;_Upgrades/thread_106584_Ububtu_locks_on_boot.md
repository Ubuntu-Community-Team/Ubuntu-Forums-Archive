---
title: "Ububtu locks on boot"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by Connollyir on 2005-12-21
I just intalled a fresh version of Ububtu, the 386 variant, and it is my first install. I have a problem though. When I try to boot to Ubuntu, I can sucessfully get to the logon screen but after I put in my name and password and press enter, Ubuntu becomes unresponsive and I am left with a blurred out Ubuntu logo (its like speed lines going sideways across the logo).

Now I have tried the installation several different times and I'm definitely thinking that Ubuntu chokes on my video card (EVGA Geforce 7800) and the machine hangs because of it but I don't know what to do about it, I'm too new with Ubuntu.

I can get into "safe mode" (I don't remember what Ubuntu calls it) so if we can change something to get me in so I can install the Nvidia drivers, I would love some advice.

Any help? :confused:

---

### Post by heimo on 2005-12-21
Go to virtual console (hit ctrl+alt+F1 after you see logon screen or choose recovery mode in boot menu) and reconfigure Xorg settings using:
```
sudo dpkg-reconfigure xserver-xorg
```


Experiment using vesa driver instead of nv or nvidia. You can also try to install nvidia-glx package (it's in "restricted" part of Ubuntu repositories) and using nvidia driver:
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable (I'm not 100% this is correct)

```


Also try running:
```
sudo /etc/init.d/gdm stop (to stop Xorg)
```and then:

```
startx
```
And see if you get any error messages / warnings. These will probably get us some more information of this situation (at least I don't have too clear idea what's going on). Hopefully you'll get it solved. :)

---

### Post by Connollyir on 2005-12-21
Thanks for the info man but I actually just read some of the same on another post and ended up changing some of my driver info and how x would run and it worked.


Thanks for the post.

---

### Post by heimo on 2005-12-21
[quote=Connollyir]Thanks for the info man but I actually just read some of the same on another post and ended up changing some of my driver info and how x would run and it worked.


Thanks for the post.[/quote]
Great! :) Could you send link to the post or tell us what you need to change  to fix this problem (just in case someone with similar problems finds this thread). Thanks!

---

### Post by Connollyir on 2005-12-21
This is actually a thread in this forum that I had missed. Its going to bring up a program that will guide you very nicely through reconfiguring X and at the end of that I had video back.

[http://ubuntuforums.org/showthread.php?t=98700&highlight=vesa+console](http://ubuntuforums.org/showthread.php?t=98700&highlight=vesa+console)

Worked wonders for me, hope it also works for others.


-Ian

---

