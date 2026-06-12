---
title: "touchpad not working after login"
date: 2010-06-26
forum: Hardware
---

### Post by matshofman on 2010-06-26
Hi,

From one day to another I suddenly have the problem that when I boot my laptop (HP Pavilion 1120ED) the touchpad works but a soon as I log in it doesn't work anymore.

I think it is something with the driver stops after I log in.

Does anyone know how to fix this?

---

### Post by matshofman on 2010-06-29
I solved the problem, after lots of searching I found [this]("http://ubuntuforums.org/showpost.php?p=9315670&postcount=6") command line that worked for me.

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

---

### Post by ghsfr33d0m on 2010-09-18
Worked for me as well, I'm amazed actually. I have been booting into a BT4r1 USB boot a lot recently, and that effected my touchpad settings somehow. All worked well in the USB boot, and at the login screen, but past that, no touchpad at all. I boot a ThinkPad, so I was able to revert to the BS little red mouse input thing. Anyway, glad to have my touchpad back, thanks. 

ghsfr33d0m

---

### Post by basharat on 2010-10-10
thanks, it solved my problem :)

---

### Post by subjucha on 2010-10-29
Thank you, it solved my problem too on Ubuntu 10.10

---

### Post by Linux Lover II on 2010-10-31
Solved for me too!

---

### Post by Brando753 on 2010-11-10
Worked for me to :D :popcorn:

---

### Post by Willynux on 2010-11-21
Yessssss ALL ok now \\:D/
Spent my afternoon looking for this, will link this solution in the other hundreds of threads i have read today...

like launchpad (one had to go to post 93 to get this answer...)
 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all)

---

### Post by NealCrosby on 2010-11-26
Nice!  The same issue popped up for me.  Thanks for the solution!

---

### Post by Aquinus on 2010-12-08
Worked great for me too on both Ubuntu and Gentoo. Thank you!

---

### Post by Navyblue on 2011-05-27
Today I realise that I have this problem.

Works for me too, thanks. :)

I Googled "touch pad not working after login", I didn't even bother to specify Ubuntu and Google pointed me right to this thread. Hate to say this but if Ubuntu can not solve basic functionality bugs like this at version 11.04 I wonder if it will ever be ready for prime time.

---

### Post by sennett on 2011-08-20
Just to push up on Google.  Thanks mate worked a treat.

---

### Post by svabhishek on 2011-08-23
Dont know why but in 11.04 it doesn't work ... :( tried all options and in all possible ways ... also tried logging into Ubuntu Classic .... dont know why :(

---

### Post by Steviepower on 2011-11-03
Mine is having the same problem in 11.10. this solution didn't work for me I'm afraid. does anyone else have any ideas?

---

### Post by Jeff Hill on 2011-12-04
Sorry, guys - it didn't do it for me.
I have an Acer5920 dual booting vista and Ubuntu 11.10. I have a USB wireless mouse dongle plugged in for desk use, but need to use the touchpad often. Touchpad fully-functional in Vista, and seems to work before login in Ubuntu. Then stops during login, as though something loaded clashes. Have had this problem before, but until the last version of Ubuntu, it seems to have sorted itself out (or maybe an update cured it each time). On this model, Acer uses the "Media Keys" as 'Touchpad 1', and the real touchpad is allocated to 'Touchpad 2' - i don't know if this is the problem. Any help appreciated.

---

### Post by RonsBrain on 2011-12-08
Found a solution that worked for me with 11.10, figured I'd direct this thread to it, as this thread was the first Google result for this issue.

[Resolution for touchpad not working in Ubuntu 11.10]("http://www.upubuntu.com/2011/11/is-your-laptop-touchpad-not-working.html")

---

### Post by hyundai on 2012-03-16
Sorry to ask this question after seeing so many good appreciation to this solution. How and where  do I enter in this command 
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

---

### Post by verderben on 2012-04-02
you enter it in the gnome-terminal

just press strg+alt+t

---

### Post by t1m0xa on 2012-04-15
Hey, guys,
I've replied to a similar post at another website - 
[http://superuser.com/a/412663/128393](http://superuser.com/a/412663/128393)
It concerns Lenovo x220 with Ubuntu 11.10, but may be a solution

---

### Post by Memophysic on 2012-11-19
> **matshofman said:**
> I solved the problem, after lots of searching I found [this]("http://ubuntuforums.org/showpost.php?p=9315670&postcount=6") command line that worked for me.

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

This didn't work on Lenovo Y580, but RonsBrain's solution worked like a charm!

> **RonsBrain said:**
> Found a solution that worked for me with 11.10, figured I'd direct this thread to it, as this thread was the first Google result for this issue.

[Resolution for touchpad not working in Ubuntu 11.10]("http://www.upubuntu.com/2011/11/is-your-laptop-touchpad-not-working.html")

Incredible to see it was in fact disabled! :KS

---

