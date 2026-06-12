---
title: "need some help no gui"
date: 2011-02-26
forum: Hardware
---

### Post by jstnhd on 2011-02-26
ok iv been looking around for a day or to and nothing i have found has  worked what i got from my research so far is ubuntu isn't recognising  the graphics card. i wiped the hard drive and did a fresh install on a  hp pavilion 4145 everything was going smooth untill the desktop is about  to load it gets to the ubuntu screen with the loading dots and makes  the start up sound but then it just sits at that screen and nothing  happens. i have tried the following things with no prevail

sudo get-apt update
sudo get-apt upgrade
sudo reconfigure xserver xorg - when i do this nothing happens 
startx  -  this says fatal server error server is already active for display 0
lspci - ATI radeon mobility U1

i have also tried booting from the cd and turning off nomodest but still  nothing if someone could help me out that would be great!

---

### Post by sikander3786 on 2011-02-26
Welcome to the forums :-)

Try using the nomodeset or an alternative boot parameter.

From your Bios screen, press and hold down Shift key until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Using arrow keys, navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Hopefully, you'll see the desktop this time.

Once on the desktop, make sure you are connected to the Internet. Now go to System > Administration > Hardware Drivers (Lucid) or Additional Drivers (Maverick) and check if any proprietary drivers are available for your graphics card. If there are any, activate the current/recommended one's and the problem should go away forever.
[B]
nomodeset alternatives for other Graphic Cards[/B]

According to our senior member *oldfred* at ubuntuforums.org, you need to replace nomodeset with some other parameters for different cards.

```
Older Intel video card: i915.modeset=1 or i915.modeset=0
nVidia: nomodeset
Generic: xforcevesa or nouveau.modeset=0
Radeon: radeon.modeset=0

```

Source: [http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by jstnhd on 2011-02-26
thanks for getting bakc quickly the radon.nomodest=0 worked i went in and checked for drivers and there wernt any restarted the pc and it does the same thing is there anyway to save that so i dont have to edit it every time

---

### Post by sikander3786 on 2011-02-26
There should be drives for your graphics card. Let us know which one is it exactly. Go to Applications > Accessories > Terminal and post the output of this command please.

```
lspci | grep VGA
```

---

### Post by misterbiskits on 2011-02-26
> **jstnhd said:**
> it just sits at that screen and nothing  happens.

I had this same problem while trying to get my second video card (ATI HD5450) working.
[Manually installing the driver]("http://ubuntuforums.org/showthread.php?t=1682743") from a fresh ubuntu install worked for me...just skip past my moaning and read the last post in the thread.

---

