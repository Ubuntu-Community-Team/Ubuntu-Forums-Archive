---
title: "ntel PRO/Wireless 3945ABG --Wireless"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by emrecim on 2007-05-09
As you can assume, I am newbie to Ubuntu as well as Linux... I have installed ubuntu without any problem, I have even install some packages and drivers, but I could not install my wirelss adapter yet. I have read some instructions, bu they were little complicated for me.
This is the Link :[http://bughost.org/ipw3945/](http://bughost.org/ipw3945/), I read... I have download the tar files needed. Can someone help me how to finish this installation please. Thankx..

---

### Post by NilsE on 2007-05-09
This should have worked out of the box but obviously not.  Can you tell us specifically what the problem is like is it just not seeing the card at all or you can not connect or icons missing etc.  In other words more detail on the problem.

You can look at this post and see what I did to get WPA security working but just look at the parts about making the card work.

[http://ubuntuforums.org/showthread.php?p=2579081#post2579081](http://ubuntuforums.org/showthread.php?p=2579081#post2579081)

---

### Post by emrecim on 2007-05-09
When I got to device manager, my wireless card seems to be not installed.. That is the main problem. I will check the link you gave and see if it work..

---

### Post by emrecim on 2007-05-09
One more quick question: Link u sent me saying "Install libpam-keyring".. I went to Synaptic Package, but there are many pack starting w/ libpam-xxx , but there is no  libpam-keyring. How can I find that one, I f I cant see under Synaptic

---

### Post by NilsE on 2007-05-09
> **emrecim said:**
> One more quick question: Link u sent me saying "Install libpam-keyring".. I went to Synaptic Package, but there are many pack starting w/ libpam-xxx , but there is no  libpam-keyring. How can I find that one, I f I cant see under Synaptic
It should actually show up in Synaptic but you can try this in a terminal window

sudo apt-get install libpam-keyring

---

### Post by emrecim on 2007-05-09
Okay, even the command did not work.. and here is the output...

[PHP]emre@emre-laptop:~$ sudo apt-get install libpam-keyring
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libpam-keyring
[/PHP]

---

### Post by NilsE on 2007-05-09
You may not have enough repositories turned on.  Go into Software Sources and add the couple at the bottom of the first screen by clicking on them.

Then go into Synaptic and reload and see if it is there.

Alternative to Synaptic is to do a 

sudo apt-get update 

before the install

---

### Post by stchman on 2007-05-09
> **emrecim said:**
> Okay, even the command did not work.. and here is the output...

[PHP]emre@emre-laptop:~$ sudo apt-get install libpam-keyring
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libpam-keyring
[/PHP]

Since your wireless card does not work how are connecting to the internet?  Synaptic needs internet access to download packages.  Use a wire.

---

### Post by emrecim on 2007-05-10
> **stchman said:**
> Since your wireless card does not work how are connecting to the internet?  Synaptic needs internet access to download packages.  Use a wire.


Of course I am using wire for now, but I am trying to get my wireless work too...

---

### Post by emrecim on 2007-05-10
> **NilsE said:**
> You may not have enough repositories turned on.  Go into Software Sources and add the couple at the bottom of the first screen by clicking on them.

Then go into Synaptic and reload and see if it is there.

Alternative to Synaptic is to do a 

sudo apt-get update 

before the install...

I went to Software Preferences (That was the only thing I could ve find similiar to Software Sources) I, then click the last two thing on the first tab, which were Ubuntu 6.06 LTS Security, or something like that. I went back to SYnaptic and still there was nothing... I then ran the command you told me  sudo apt-get update it did install some stuff but nothing changed yet.

I ll go crazy... How hard is to install wireless card here.. I have aso try to install gnome network manager. Supposebly, after installation and reboot, It should ve apper on the top roght area, but still no luck..

---

