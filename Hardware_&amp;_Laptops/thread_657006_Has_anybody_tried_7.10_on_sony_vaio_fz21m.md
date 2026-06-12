---
title: "Has anybody tried 7.10 on sony vaio fz21m"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by eternalsunshine on 2008-01-03
I want to try it on my fz21m but first i need to know if there is any incompatible hardware like wireless or sound controls on the panel or anything else. also if i install ubuntu on my laptop will the recovery partition in my hard disk be ruined or lost?

Thank you...

---

### Post by Borbus on 2008-01-03
Try it. Download the live CD and boot from it. The live CD will not alter your current configuration in any way so if it doesn't work then you can just choose to not install it.

If you choose the manual paritioning option during setup then you can choose to leave your recovery partition. Just make sure you don't delete the partition and do not check it for formatting (this is default in manual partition).

---

### Post by eternalsunshine on 2008-01-04
Live cd didnt see the nvidia 8400gt I guess it will be a big problem in the future.

---

### Post by h0ffa on 2008-01-05
I have a  sony vaio fz21m runnung Gutsy (7.10) some problems did came up, but they are all fixed now.

after fresh installation do these things in the following order.

in [sofware sources] click these:

[Ubuntu Sofware]
x (main)
x (universe)
x (restricted)
x (multiverse)

[Updates]
x (gutsy-security)
x (gutsy updates)
  (gutsy-proposed)
x (gutsy-backports) (this one you need later to enable the headphones-jack.

update system with Update Manager
and reboot.

install Envy, get it from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
envy will not be able to install without you enabling the tings in [software sources].

use envy to install the proper nvidia drivers.

Now for the audio-jack problem (sound refuses to come out trough the headphones-jack.)

Edit /etc/modprobe.d/alsa-base (sudo gedit /etc/modprobe.d/alsa-base) and add this in the bottom of it

options snd-hda-intel model=vaio

then do this:

sudo apt-get install linux-backports-modules-$(uname -r)


do these things and enjoy your fz21m

---

### Post by eternalsunshine on 2008-01-05
> **h0ffa said:**
> I have a  sony vaio fz21m runnung Gutsy (7.10) some problems did came up, but they are all fixed now.

after fresh installation do these things in the following order.

in [sofware sources] click these:

[Ubuntu Sofware]
x (main)
x (universe)
x (restricted)
x (multiverse)

[Updates]
x (gutsy-security)
x (gutsy updates)
  (gutsy-proposed)
x (gutsy-backports) (this one you need later to enable the headphones-jack.

update system with Update Manager
and reboot.

install Envy, get it from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
envy will not be able to install without you enabling the tings in [software sources].

use envy to install the proper nvidia drivers.

Now for the audio-jack problem (sound refuses to come out trough the headphones-jack.)

Edit /etc/modprobe.d/alsa-base (sudo gedit /etc/modprobe.d/alsa-base) and add this in the bottom of it

options snd-hda-intel model=vaio

then do this:

sudo apt-get install linux-backports-modules-$(uname -r)


do these things and enjoy your fz21m

Thank you for your answer is there any problem using wireless switch, bluetooth , sound buttons on the panel and fn buttons.
Excuse my curiosity I was a fan user before with my older laptop , i want to use it with this one with more more joy of performance :D

---

### Post by sojusnik on 2008-01-06
Hi,

Can you say something about the fan and how it sounds/reacts with Ubuntu 7.10.
The next days I want to buy a Sony Vaio VGN-FZ21E and hoping that the build-in fan is silent.

---

### Post by h0ffa on 2008-01-06
the wireless works wine the LED-indicator for wifi at the front just doesn't light up. Bluetooth seems to work fine, I was able to connect to my cell without any hazzle.
the volume buttons works, but not the others (play, stop rw and so on). but I guess it's not that of a problem, more a matter of key binding.

now, the down sides.
the 'motion eye' doesn't work, but work is in progess (just search 'vaio' in the forum).
same thing with the FN-keys.

sojusnik:
I think my fan is silent. However, I'm a xbox360 owner, so my hearing isn't that good =).
Using Vista, I found the laptop becoming much warmer forcing the system to use the fans more.
Linux is more easy on the system. (Vista, 1000mb RAM used, just to have it running no extra progs. Ubuntu, 260mb with GIMP, openoffice and a bunch of other programs running)

---

### Post by sojusnik on 2008-01-11
> the volume buttons works, but not the others (play, stop rw and so on). but I guess it's not that of a problem, more a matter of key binding.
Maybe you should try [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/).
It works fine with my ACER's Multimedia Buttons, so I think it will work with Sony too.

---

### Post by sojusnik on 2008-01-14
> **sojusnik said:**
> Maybe you should try [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/).
It works fine with my ACER's Multimedia Buttons, so I think it will work with Sony too.
Got my new VAIO FZ21E and tried to install these buttons with keyforge, but I had no success. 
Any ideas how to enable "S1" "AV Mode" and the other media control buttons?

---

### Post by h0ffa on 2008-01-17
what are the S1 and AV mode buttons for?
I never read instruction manuals =)

---

### Post by sojusnik on 2008-01-17
Well, I dont't know for what they stand in Vista, but I want to use them in Ubuntu for example to start Firefox and Thunderbird.

Any idea about enabling them?

---

