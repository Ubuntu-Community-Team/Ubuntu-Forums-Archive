---
title: "Ubuntu 10.10 Alps touchpad not working"
date: 2010-10-10
forum: Hardware
---

### Post by SamZebian on 2010-10-10
I have a Sony Vaio that I just installed 10.10 on, was using the Release candidate for about a week. Both the RC and final release have the same issue, my mousepad does not work. I have been using an external USB mouse for now. My laptop is a VPCF126FM using an Alps touchpad. I am not sure but maybe it has something to do with [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/641320")? (btw running 64bit, idk if the same problem exists in x86 version of ubuntu)

---

### Post by techdude3177 on 2010-10-10
Here check out this [Technical Document]("https://help.ubuntu.com/community/SynapticsTouchpad") it should have the answer your looking for.

Also make sure gsynaptics is installed.

---

### Post by huggis on 2010-10-10
Same problem on ubuntu 10.10 [32bit]. I can't solve the problem since 10.04. Touchpad is detected. It works during instalation proces but doesn't work on installed system. Anyone could help to fix this? My computer: hp pavilion dv5 with gforce 9600m GT (nvidia proprietary driver installed). Maby nvidia driver generates this problem?

---

### Post by Dark_Stang on 2010-10-10
Are you guys using existing home folders? I had similar issues upgrading from 10.04 to 10.10. But then I noticed that they worked fine under Root or a different account. Mine were solved by forcing Ubuntu to create a new .dbus folder in my home folder. Try renaming your .dbus folder to .dbus.old in recovery mode and rebooting.

---

### Post by rajadain on 2010-10-10
I'm using an HP dm4 with the newfangled Synaptics ClickPad (tm, probably). It supports multi-touch in Windows, but just behaves erratically when multi-touched in Ubuntu (a bit like this: [http://ubuntuforums.org/showthread.php?t=1590466](http://ubuntuforums.org/showthread.php?t=1590466), but only with two fingers, not one). But that's okay, I don't need multi-touch so much.
What's bothering me is the lack of a right-click. Left-click, right-click, scrolling and even middle-click (by touching top-right corner of the clickpad) were working fine in Lucid. Three of these (left, scroll and middle) are working in Maverick too, but right-click is gone. I tried the method with the HP Mini 210 (can't find the link right now), and that just makes it slow and removes scrolling + middle click.
I've also installed gsynaptics, and the general synaptics driver (both of which were already and also there in my old Lucid). I've explored every GUI option I could find, and a lot of code options as well. I've also enabled SHMConfig as told in the Ubuntu Synaptics guide (as specified above). I just want my right-click back.
Thanks for any updates.

---

### Post by SamZebian on 2010-10-10
no my touchpad never worked during install. I managed to install Gpointing device settings, which when launched with my usb mouse, shows only the usb mouse. If I select it with the mouse plugged in, unplug the mouse and launch it by hitting enter, all that happens is I get the ubuntu rotating pointer (like the hourglass on windows) and nothing ends up loading. I even tried looking at that document, tried
 "$ sudo evtest /dev/input/eventX > ~/evtest"
then
"$ cp /var/log/Xorg.0.log ~/Xorg.0.log"
it says to "Check your  /dev/input/eventX" but when I go to that directory, there is no such file or directory exists, even with hidden files shown. However, if I run "cat /proc/bus/input/devices", One of the things that shows up is this:

"I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Jogdial"
P: Phys=
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=40000 0 0 0 0
B: REL=100"

I'm thinking jogdial = mouse?
It says in the example that the "/dev/input/eventX  is  /dev/input/event8", so I'm thinking my /dev/input/eventx is /dev/input/event6 but I have no idea.

I'm really lost as to what to do here, do I file a bug, find a driver or what? I'm not too experienced with Ubuntu, been using it since 6.04 but only as a secondary OS, some help would be greatly appreciated. Thanks.

---

### Post by elisimmer on 2010-10-20
I am having the exact same problem with my Acer Aspire One 150.

---

### Post by piggyslasher on 2010-10-24
Guys,

I've tried every solution out there, but enabling shmconfig is the one that helped me. My touchpad was working during LiveCD and installation. However, it was not being detected when i started Ubuntu 10.10. I didn't even have the Touchpad tab in System>Preferences>Mouse.

I enabled shmconfig as instructed here, and everything works fine now!

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)


[http://www.techgarten.com]("http://www.techgarten.com")

---

