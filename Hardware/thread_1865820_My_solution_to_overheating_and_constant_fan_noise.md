---
title: "My solution to overheating and constant fan noise"
date: 2011-10-20
forum: Hardware
---

### Post by errrn on 2011-10-20
Hi,

I finally managed to solve the never-ending problem of overheating and producing myself partial deafness due to constant fan noise.

My setup is an Acer 5740G laptop (i3, Ati HD 5650, among the relevant features), running ubuntu 11.10, freshly installed after a horrible upgrade.

In the webupd8 blog they featured Jupiter as asolution for the power regression in the kernel. I installed it but I couldn't see a major difference.

Then what I did was to add the following lines to the grub conf:


[LIST]
[*] i915.i915_enable_rc6=1
[*] i915.i915_enable_fbc=1
[*] pcie_aspm=force
[/LIST]
 
the first two were detailed in phoronix. and with powertop (a must) I could verify that the battery started lasting more (went up from 50 min to 70).

and then after failing several times, I decided to try installing again the ati propietary drivers.I did this from the additional drivers menu, not from the terminal. this, in addition to the last line added to the grub made a HUGE difference. fans turned off (which was the main reason for overheating, ironically), temperature dropped from 90°C !! to 45-60°C, and the battery goes now for up to 3:30 hours.

So, to sum up:


[LIST]
[*] Jupiter
[*] Powertop
[*] ATi Propietary drivers (NOT the post-launch update... I don't know if that would make a difference, but are the ones I chose)
[*] grub like this:
[/LIST]
 ```
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 pcie_aspm=force quiet splash"
```

I hope this helps someone

cheers!
H.

---

### Post by razorxpress on 2011-10-22
Hi, I wrote this [post]("http://ubuntuforums.org/showthread.php?t=1859945"). Without the addition of i915_enable_rc6 I already had more than 3 hours battery backup. I had used i915.i915_enable_rc6=1 and i915.i915_enable_fbc=1 in the past (Ubuntu 11.04), but it solved some heating problems, but graphics glitches were on. Now when I have enabled i915.i915_enable_rc6=1 with all other settings as described in my previous post the battery indicator shows more than 4 hours (without touching brightness). Jupiter had already started showing temperature between 45 (fresh boot) and 65 (two days laptop on and gaming). Most of the time it stays at 55 degrees. And the good part is, I can play Nexuiz without any glitches this time, but I can see some graphics performance degradation when I tested it using some OpenGL code. Since it can run Nexuiz I don't think the impact on graphics performance is not as it was in 11.04. I have still not tested the enable_fbc (which also had graphics glitches in Ubuntu 11.04), but I think I will give it a try.

---

### Post by errrn on 2011-10-24
Hi,

yes, I saw your post shortly befor making changes to my setup. It helped a lot. Specially, knowing that there was some kind of workaround to theese type of problems.

Sadly I don't have switchable graphics (according to the notebookreview's accer 5740 owner's lounge). But I did experience some weirdness in graphics (really slight) in firefox with theese changes. I don't use my computer for gaming, so I can't really talk about its performance in that area.

cheers

---

### Post by Bucic on 2011-10-25
After applying all of the known tricks I lowered the power consumption on my both laptops down by just 10% out of ~50% lost when compared to windows! Please support fixing the ****** kernel by voting "this affects me":
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)

---

### Post by errrn on 2011-10-26
I'm also still nowhere near the efficiency I had in windows. Also it's hard to compare to the old days due to the damage the battery suffered needing to be plugged in constantly.

btw, I clicked in the bugs it did affect me (2 out of 3) ;)

---

### Post by Julian1942 on 2011-11-02
great errrn[]("http://ubuntuforums.org/member.php?u=1303292") ! I'm having the same problem and I hope this is the final solution.
BUT (and because I'm a total noob at Ubuntu), I have a silly question: how do I edit grub config ? If I paste the CODE into terminal, just nothing happens....

---

### Post by Bucic on 2011-11-02
> **Julian1942 said:**
> great errrn[]("http://ubuntuforums.org/member.php?u=1303292") ! I'm having the same problem and I hope this is the final solution.
BUT (and because I'm a total noob at Ubuntu), I have a silly question: how do I edit grub config ? If I paste the CODE into terminal, just nothing happens....
If you're such a noob ;) I think you shouldn't do permanent changes to grub. Instead you could boot holding SHIFT to bring up the gru menu and use E key to edit the parameters for a single session.

To edit the grub options permanently:
```
gksudo gedit /etc/default/grub
```
- copy paste the original line and comment it out using hash sign (#)
- modify the other one
- save and close the gedit
```
sudo update-grub
```
reboot

---

### Post by Julian1942 on 2011-11-04
Thanks a lot. Finally, I could edit grub successfully. Sadly, that didn't solve my problem. It's like my GPU were not properly installed, I've already tried several ways...

Thanks anyway guys !

---

### Post by razorxpress on 2011-11-08
My performances are actually quite good now. If unity did not break on xorg-edgers I would have enabled xorg-edgers ppa for all the graphics update. I hope they will fix that someday. However there was a xorg-server update recently on oneric. Kernel 3.1 seemed to have lots of improvements for graphics performance, but I could not get the ubuntu deb package working and I did not wanted even to compile the kernel and waste a lot of time. May be I could get 3.2 working. In Linux 6 packages are inter-related when it comes to gpu performance. The kernel, xorg(server), xserver-xorg-video-intel, mesa, libdrm and libva. It is always better to get the latest (ofcourse if you are going with open source driver). Since I happen to never get AMD catalyst working I always end up using opensource drivers.

---

### Post by b3n_hysteria on 2011-11-15
hi guys,

current i'm using notebook HP 431
here information for my mechine 

[IMG]http://i.imgur.com/MqFuN.png[/IMG]

I'm using dual OS, as you see from the picture, I'm using windows 7 ultimate 64 bit, and ubuntu 11.10 64 bit,

my problem in ubuntu is : 
1. overheat (
I've tried use your solution, but nothing happen for me, still over heat, up to 70C(:-(:-(:-(:-(:-()
I've tried use jupiter to, but it still same..
)
2. my system menu like user, launch bar, everything is gone.. except standard menu like file.. but without administrator menu
   it's happen, after i install driver for ati radeon in ubuntu 11.10

any suggestions? or maybe found same problem and you solved it? 

Note : sorry for my english is not good

---

### Post by elfandereth on 2011-12-28
For the first issue I still have no solutions in a satellite R830, but for the second do the following

When your logged in press Ctrl+Alt+F1 and relogin. Then execute 

unity --reset 

The problem is caused by an error in compiz.

Best regards,
Javier



> **b3n_hysteria said:**
> hi guys,

current i'm using notebook HP 431
here information for my mechine 

[IMG]http://i.imgur.com/MqFuN.png[/IMG]

I'm using dual OS, as you see from the picture, I'm using windows 7 ultimate 64 bit, and ubuntu 11.10 64 bit,

my problem in ubuntu is : 
1. overheat (
I've tried use your solution, but nothing happen for me, still over heat, up to 70C(:-(:-(:-(:-(:-()
I've tried use jupiter to, but it still same..
)
2. my system menu like user, launch bar, everything is gone.. except standard menu like file.. but without administrator menu
   it's happen, after i install driver for ati radeon in ubuntu 11.10

any suggestions? or maybe found same problem and you solved it? 

Note : sorry for my english is not good

---

### Post by adiasd on 2012-01-29
Hi Folks,

I was also having the battery problems described in this thread and tried 3 of 4 measures suggested here (the grub line, jupiter and ATI proprietary drivers). After that the situation improved a lot, since I was having half of the battery time as compared to Windows and now I have about 80%. As an attempt to further optimize battery performance I decided to try also powertop. I installed the package from software manager and then went to use it with the command:

sudo powertop

However, when I did this I got the following error messages:

Cannot load from file /var/cache/powertop/saved_results.powertop
Cannot load from file /var/cache/powertop/saved_parameters.powertop

These messages are very briefly displayed (I could identify them only after I directed the output to a file) and then the terminal goes blank and back to the prompt. Oddly enough after that the terminal isn't responsive anymore.

Does anyone have any idea why I can not get meaningful output with powertop? Is there another way to invoke it?

Thanks

---

