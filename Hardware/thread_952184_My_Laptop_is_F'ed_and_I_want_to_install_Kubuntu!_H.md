---
title: "My Laptop is F'ed and I want to install Kubuntu! Help!"
date: 2008-10-18
forum: Hardware
---

### Post by BirdIsTheWord on 2008-10-18
So here is my problem:

I have really recent Toshiba laptop, problem being that I just broke the cd-rom out of it, I mean completely out, the cable ripped off too.(don't ask)

So anyway, I have been running Vista for some time, and my friend got me started on ubuntu. well I want to make the switch to Kubuntu but I have a dilemma.

I want to reformat all my partitions: the vista and the ubuntu on it, but since my cd-rom is broken I cannot boot the vista cd to go through the boot-repair-reformat options. I have tried to use an external cd-rom and boot through USB, but it does not detect the cd-rom or something. I don't have a floppy obviously because it is a new computer.

Is there anyway I can reformat my computer and boot kubuntu? Or is there anyway that I can install kubuntu and just wipe everything else, maybe install from windows and then from kubuntu wipe the windows partition?

I just want to be able to format my comp and just start with Kubuntu! GAA!! 

Thanks!

---

### Post by wakojakop on 2008-10-18
Did you iinstall kubuntu with wubi
i am going to assume you did
1)boot kubuntu
2)edit the boot.ini in the hd with windows on it
3)delete the windows line
4)copy the kubuntu line over the default os
5)save the thing
6)reboot

---

### Post by BirdIsTheWord on 2008-10-18
> **wakojakop said:**
> Did you iinstall kubuntu with wubi
i am going to assume you did
1)boot kubuntu
2)edit the boot.ini in the hd with windows on it
3)delete the windows line
4)copy the kubuntu line over the default os
5)save the thing
6)reboot

Well I installed Ubuntu using Wubi, I didn't know you could install Kubuntu. 
I will try that, although I am not that sure what it all means. If you could put that in a little bit easier terms that would be great.
In the mean time I will try. Thanks for your help!

---

### Post by BirdIsTheWord on 2008-10-18
> **wakojakop said:**
> Did you iinstall kubuntu with wubi
i am going to assume you did
1)boot kubuntu
2)edit the boot.ini in the hd with windows on it
3)delete the windows line
4)copy the kubuntu line over the default os
5)save the thing
6)reboot

I couldn't figure out this method. I am new to Ubuntu so I don't know how to even look at what drive my windows is on or anything.

Isn't there just away to boot Ubuntu from a flash drive or something and re-partion everything?

---

### Post by sethvath on 2008-10-18
Yes there is but its not easy for a novice to get started to say the least. 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by BirdIsTheWord on 2008-10-19
> **sethvath said:**
> Yes there is but its not easy for a novice to get started to say the least. 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

Thanks the first link gave me exactly what I wanted!

Ended up liking ubuntu more than kubuntu so I just did the same thing and usb load/boot ubuntu thanks so much!

---

### Post by MJMON62 on 2008-10-19
> **BirdIsTheWord said:**
> So here is my problem:

I have really recent Toshiba laptop, problem being that I just broke the cd-rom out of it, I mean completely out, the cable ripped off too.(don't ask)

So anyway, I have been running Vista for some time, and my friend got me started on ubuntu. well I want to make the switch to Kubuntu but I have a dilemma.

I want to reformat all my partitions: the vista and the ubuntu on it, but since my cd-rom is broken I cannot boot the vista cd to go through the boot-repair-reformat options. I have tried to use an external cd-rom and boot through USB, but it does not detect the cd-rom or something. I don't have a floppy obviously because it is a new computer.

Is there anyway I can reformat my computer and boot kubuntu? Or is there anyway that I can install kubuntu and just wipe everything else, maybe install from windows and then from kubuntu wipe the windows partition?

I just want to be able to format my comp and just start with Kubuntu! GAA!! 

Thanks!

I have been pretty sucessful in removing the hard drive and installing ubuntu with an old desktop and an adaptor. Then just choose the recovery mode when you get it back into the laptop and it will update. Be sure to have it plugged in to an ethernet connection. Problem is that it won't work this way for any Windows newer than "98 My laptop doesn't even have an option for booting to CD/Rom but what the heck I am liking Ubuntu so much now that I don't care about having Windows :-)

---

