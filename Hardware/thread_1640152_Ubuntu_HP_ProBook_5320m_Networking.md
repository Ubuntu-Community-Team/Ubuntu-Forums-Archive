---
title: "Ubuntu HP ProBook 5320m Networking"
date: 2010-12-07
forum: Hardware
---

### Post by lenooh on 2010-12-07
I just installed Ubuntu 10.10 on a HP ProBook 5320m and networking didn't work. Neither wired or wireless.

It has a Broadcom BCM4313 wireless and a Realtek RTL8111/8168B ethernet controller.

There is a proprietary module (driver) for the wireless, but you cannot enable it without wired network...

I googled and found out that the default r8169 module for the wired network is a problem and should be replaced by the r8168 module. I did that using this thread [http://www.uluga.ubuntuforums.org/showthread.php?t=1022411]("http://www.uluga.ubuntuforums.org/showthread.php?t=1022411") but it didn't help. 

So I rebooted into BIOS and:
[LIST]
[*]disabled all the HP crap under System Configuration->Device Configuration (HP DayStarter, HP QuickLook, HP QuickWeb, etc) and disabeld LAN Power Save
[*]disabled Wireless Button State and LAN/WLAN Switching in System Configuration->Build-In Device Options
[/LIST]
(I also disabled Bluetooth and Fingerprint Device because I don't need them.)

Then I booted to Ubuntu and networking was working :-) (with both r8169 and r8168 module, so **you do not have to install the r8168 module**). I enabled the proprietary Broadcom driver and wireless was also working after a reboot.

I later re-enabled LAN Power Save in BIOS, and things are still working.

I tried booting Ubuntu 10.04 from a USB drive, and it also works :-)


Hope this helps!

br

---

### Post by Millemillimeter on 2010-12-13
Hello,

Thanks for the info!

Did you try if the webcamera is working as well?

Im thinking of buying one of these. I've read that you can get one with only FreeDos, no money to microsoft..

Regards

---

### Post by lenooh on 2010-12-13
> **Millemillimeter said:**
> Hello,

Thanks for the info!

Did you try if the webcamera is working as well?

Im thinking of buying one of these. I've read that you can get one with only FreeDos, no money to microsoft..

Regards
Yes, the camera works, high resolution as well.

I recently replaced the builtin HDD with an Intel X25M SSD, and it works like a rocket now :-) The boot time is around 13s (including BIOS and login to desktop). Battery life is around 3-4 hours now, it was 2-3 with the original HDD. Applications start instantly... 


br

---

### Post by ProBook on 2011-02-03
Hi!

First, i'm sorry for my english; then, i'm new in this forum and in linux-world, but i really love this world!

I buoght an hp probook 5320m and I installed ubuntu 10.10.
It works well, webcam ok, ethernet and wireless ok.
I've just some few problems:

the fingerprint doesn't works, and i'm following this page:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089)
and hope that a driver arrives soon :D

I cannot use the gps: does it go only in order to use the internet connection with the sim card? or can I use it like a navigator?

and the worst problem: I cannot use the bluetooth! if I open System->Preferences->Bluetooth the program says that there's no bluetooth device connected.. how can i use it?

I hope that you pro-user know the answers :D
if i can help you in somethings just tell me!

---

### Post by ProBook on 2011-02-05
@lenooh: I saw ur video on the tube [http://www.youtube.com/watch?v=6DSTZd_A_b4](http://www.youtube.com/watch?v=6DSTZd_A_b4) and I see that when you boot up ubuntu appears a message about the intel graphic controller.
I've the same message and I think it is a problem with the driver (ubuntu loads the vesa driver instead the correct intel driver).
I ask info about that here: [http://ohioloco.ubuntuforums.org/showthread.php?p=10431121#post10431121](http://ohioloco.ubuntuforums.org/showthread.php?p=10431121#post10431121)
and I'm waiting an answer...
maybe do u know something about that?

---

### Post by lenooh on 2011-05-24
Hi ProBook,

I have plymouth disabled, that is why in my Ubuntu boot video you see the black and white screen. I have no problems with the graphics card. I am sure you do not have them either.
Can you enable the visual effects? (shadows, window animations, etc.). If you can, everything should be fine.

Bluetooth works fine for me, but you have to enable it by pressing the wireless button twice on your keyboard (it becomes orange first, then blue again). Also, make sure it is enabled in BIOS.

The 5320m model does not have a GPS. At least I don't have it :-)


Regards.

---

### Post by kalamaster on 2012-12-03
First of all, I'm sorry to resume this 3d but Linux O.S. works great with old stuff!

My question is: You found a trouble for work out the audio microphone? I read that this HP ProBook has only a one hole for both audio jack...

thanks in advance and ... sorry 4 my bad english!

---

### Post by lenooh on 2012-12-03
> **kalamaster said:**
> First of all, I'm sorry to resume this 3d but Linux O.S. works great with old stuff!

My question is: You found a trouble for work out the audio microphone? I read that this HP ProBook has only a one hole for both audio jack...

thanks in advance and ... sorry 4 my bad english!
yes, there is just one hole, but it has an integrated microphone and it works without problems.

---

