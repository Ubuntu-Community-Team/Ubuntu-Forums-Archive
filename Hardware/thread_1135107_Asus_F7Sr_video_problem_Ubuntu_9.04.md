---
title: "Asus F7Sr video problem Ubuntu 9.04"
date: 2009-04-24
forum: Hardware
---

### Post by Sladdin on 2009-04-24
Hello.
I have been trying to get Ubuntu 9.04 to work on my Asus F7Sr laptop. The graphic card is a **ATI Radeon Mobility HD2400**, the installation boots up smoothly in fail safe graphic mode and the MESA driver works properly inside Ubuntu after the installation but when I install the restricted ATI drivers from the Ubuntu repo and reboot the computer it doesn't start X successfully and I even tried to follow the installation guide on [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide).

_**Here is a image of the "result" after the driver installation **_
[IMG]http://i43.tinypic.com/245apz7.jpg[/IMG]


Would be thankful for any help!:)

---

### Post by sibnick on 2009-04-24
Can you specify platform (amd64 or x86) and RAM size?
I also have trouble with 9.04 on Asus F7SR (I can't install amd64 version in graphics mode at all).

---

### Post by Sladdin on 2009-04-24
> **sibnick said:**
> Can you specify platform (amd64 or x86) and RAM size?
I also have trouble with 9.04 on Asus F7SR (I can't install amd64 version in graphics mode at all).

_Asus F7Sr Specs:_
Ubuntu x86
ATI Mobility 2400HD
Inte Core2 
3GB RAM

---

### Post by Sladdin on 2009-04-24
Anyone that might now any possible solution? :(

---

### Post by zancoste on 2009-04-25
I am having the same problem too. 
Now I just want to be able to boot up without the restricted drivers. However, I don't know how to do so.  :(

---

### Post by zancoste on 2009-04-25
I was able to fix the problem :)

Reboot your computer into recovery mode, choose root prompt perform the followings:
```
sudo apt-get remove xorg-driver-fglrx
```

Then try to start normally. Now if it works but the resolution is messed up, you can always run 
```
sudo dpkg-reconfigure xserver-xorg --frontend=gnome
```

It worked for me :)
I hope it does for you too.

---

### Post by Sladdin on 2009-04-25
> **zancoste said:**
> I was able to fix the problem :)

Reboot your computer into recovery mode, choose root prompt perform the followings:
```
sudo apt-get remove xorg-driver-fglrx
```

Then try to start normally. Now if it works but the resolution is messed up, you can always run 
```
sudo dpkg-reconfigure xserver-xorg --frontend=gnome
```

It worked for me :)
I hope it does for you too.

Thanks that also worked for me but no 3D acceleration, did you manage get that to work?

---

### Post by Sladdin on 2009-04-25
Or are there any other open source drivers that might work for this card?
Thanks for any help!:)

---

### Post by zancoste on 2009-04-25
I don't know if there is anything for now... I think we are just going to have to wait :(

For now I am just happy that I got rid of this Black-Red Screen of Death. 
There is always the choice of downgrading back to 8.10 ...

---

### Post by Beaon on 2009-04-25
THanks for the fix, my screen was also scrambled. Now how do we get HW acceleration back?

---

### Post by Beaon on 2009-04-25
Someone opened a bug but his fix did not help me whatsoever.

[https://bugs.launchpad.net/ubuntu/+bug/366529](https://bugs.launchpad.net/ubuntu/+bug/366529)

---

### Post by Prodoc on 2009-04-25
I found that the problem is ATI, not Ubuntu. Support for quite a number of cards was dropped as of Catalyst 9.4. Catalyst 9.3, however, does not support X Server 1.6 which is included in Ubuntu 9.04. Ironically support for X Server 1.6 was introduced in Catalyst 9.4. Please, let ATI know what you think of this and ask them to include those cards for just one more round to let them have X Server 1.6 support: [http://www.amd.com/us/LinuxCrewSurvey](http://www.amd.com/us/LinuxCrewSurvey)

---

### Post by Beaon on 2009-04-28
What the heck! I pay $500 bucks premium for a card less then a year old and it's already unsupported? What kind of crap is this. It's not like the 3870 is exactly old. We're not talking about 9800 pros here! Thats dissapointing news.

Any rate thanks for the infoz.

---

### Post by MaindotC on 2009-04-28
I've had the x850 for almost 4 years and it's always handled graphics wonderfully.  Unfortunately, I may have to get something better if I want to use 9.04.  I'm using the open-source driver just to boot into gdm.

---

### Post by waspinator on 2009-04-30
Hey! I still have a 9800 Pro. And I expect it to show something up on the screen. It does everything I need it to do in Windows Vista. I hope I won't need to change my card just becuse ati is being a dick.

---

