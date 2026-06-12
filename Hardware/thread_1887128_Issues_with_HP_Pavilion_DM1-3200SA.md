---
title: "Issues with HP Pavilion DM1-3200SA"
date: 2011-11-26
forum: Hardware
---

### Post by Corporation on 2011-11-26
Hey all,

I've tried the IRC and got no response, so figured I'd try the forum.

Getting the following issues with the laptop on Ubuntu 11.10 and hoping I can get some fast and helpful responses:

_**1. Suspend/Hibernate Don't Work**_
I travel a lot, so have a need for a suspend or preferably hibernate function. Right now, when I do suspend or hibernate from the Unity interface, the programs close as expected, but I just end up with a black screen with a blinking cursor (screen backlight still on). This persists for several minutes until I eventually hard-boot the machine.

This is my most urgent and pressing issue, and it's really making this OS all but un-usable for me at the moment.

[U][B]2. Fn Key turns Wi-Fi Off, but not Back On
[/B][/U]When I press the F12 key to turn the wi-fi off, that works fine, but when I press it again, the networks menu in the system tray constantly shows my wi-fi card as 'device not ready'. The only way I've found to make it work again is to reboot the machine, even a logout/login doesn't seem to solve it.

[U][B]3. Frequent Crashes from Ubuntu Software Centre
[/B][/U]The software centre often crashes with no reason, I can work around this by using apt-get in a terminal window, but am wondering if these crashes are known about and if there is a fix for them.

If anyone can help with the above, it'll be much appreciated.

---

### Post by lsmithso on 2011-11-26
I have this exact same laptop, running 11.10 more or less successfully.

#1 Suspend
I had this problem until I uninstalled the proprietary ATI driver and replaced it with the OSS version. This works well enough with Unity, and suspend/resume works fine.

#2 Wifi
I had no wifi at all until I installed [http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip](http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip) - now it works fine, including the hardware kill switch on/off. The one downside is that I have to rebuild the driver on every kernel update - no biggy.

#3 works for me.

My one remaining problem is the trackpad. It only just works, but jumps about a lot, and scrolling/gestures do not work at all, even with the synaptics driver installed.

---

### Post by Corporation on 2011-11-26
> **lsmithso said:**
> I have this exact same laptop, running 11.10 more or less successfully.

#1 Suspend
I had this problem until I uninstalled the proprietary ATI driver and replaced it with the OSS version. This works well enough with Unity, and suspend/resume works fine.

#2 Wifi
I had no wifi at all until I installed [http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip](http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip) - now it works fine, including the hardware kill switch on/off. The one downside is that I have to rebuild the driver on every kernel update - no biggy.

#3 works for me.

My one remaining problem is the trackpad. It only just works, but jumps about a lot, and scrolling/gestures do not work at all, even with the synaptics driver installed.

#2 is no longer an issue as I've found a workaround - disabling then enabling wireless via the networking menu makes it pick the device back up again.

#1 - I can't really ditch the proprietary blobs as I play a lot of games which require 3D accel (Heroes of Newerth amongst others). I might try installing fglrx-unstable at some point and see if this is fixed in newer versions, as it sounds like it's related to the video drivers.

As for the trackpad, I have two finger scrolling and left/right mouse click. Can't remember what I did to change it. The only thing I dislike about my trackpad is that I don't have spiral scrolling, and can't click a button with one finger and drag with the other.

---

### Post by lsmithso on 2011-11-26
> **Corporation said:**
> 

As for the trackpad, I have two finger scrolling and left/right mouse click. Can't remember what I did to change it. The only thing I dislike about my trackpad is that I don't have spiral scrolling, and can't click a button with one finger and drag with the other.

That's odd. I can left-click and drag fine. If what you did to get gestures working comes back to you, please do tell.

---

### Post by Corporation on 2011-11-27
> **lsmithso said:**
> That's odd. I can left-click and drag fine. If what you did to get gestures working comes back to you, please do tell.

When I try to left click and drag with two fingers, it assumes I want to two finger scroll. That's the only gesture I have working btw.

Confirming that new fglrx didn't solve the hibernation issue.

Edit: I remember now what I did to get two-finger scrolling & right-click working. First of all, if you did anything to make the mouse work differently (like the type=expo or whatever it is), undo it.

Then, follow the instructions here to build [xerver-xorg-input-synaptics]("http://ubuntuforums.org/showpost.php?p=10744640&postcount=202") with the suse patches. This will fix synaptics driver for you.

I also managed to fix the suspend/hibernate issue, you create a file in /etc/pm/config.d (doesn't matter what it's called) and put the following in it:

SUSPEND_MODULES="hp_accel lis3lv02d"

After this, suspend and hibernate both seem to work fine with fglrx proprietary blob drivers installed.

---

### Post by arjai on 2012-02-12
Hi  Corporation,

I have the same laptop and Ubuntu version. Unsurprisingly I have the same Linux issues you had.

The hibernate problem is solved now. Thanks for that!

About the mouse, I managed to get some improvement based on other threads I read from 10.04, but I still cannot select, which is annoying. Building the package, is not working. 

I get the following error from dpkg-buildpackage:

 1 out of 1 hunk FAILED -- rejects in file conf/50-synaptics.conf

Any idea what this means?

Thanks

---

### Post by Psycopatologic on 2012-04-23
I don't know if you managed to solve the touchpad issues in Ubuntu 11.10 but i ran into the same trouble here today wen i bought a Pavilion dm1. I found a solution that it's easier than build a new server from scratch (actually i was trying that and i got stucked several times). I found the solution here in the forum. Here's a patch [http://ubuntuforums.org/attachment.php?attachmentid=204657&d=1318883346](http://ubuntuforums.org/attachment.php?attachmentid=204657&d=1318883346) for your server and here's the steps to fix it:

> This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

you must change the version of the file for the new one that is 3.0.0-12-generic. Thanks to the user Tomkear2006 to come out with this solution. The original thread and posts can be found here [http://ubuntuforums.org/showthread.php?t=1388164&page=23](http://ubuntuforums.org/showthread.php?t=1388164&page=23) post #265 contains the patch and #224 the instructions for a previous version.

Hope with this you can solve the touchpad issues, it worked for me in Ubuntu 11.10 64bits.

---

### Post by vishnuprakash on 2012-10-28
> **Psycopatologic said:**
> I don't know if you managed to solve the touchpad issues in Ubuntu 11.10 but i ran into the same trouble here today wen i bought a Pavilion dm1. I found a solution that it's easier than build a new server from scratch (actually i was trying that and i got stucked several times). I found the solution here in the forum. Here's a patch [http://ubuntuforums.org/attachment.php?attachmentid=204657&d=1318883346](http://ubuntuforums.org/attachment.php?attachmentid=204657&d=1318883346) for your server and here's the steps to fix it:


you must change the version of the file for the new one that is 3.0.0-12-generic. Thanks to the user Tomkear2006 to come out with this solution. The original thread and posts can be found here [http://ubuntuforums.org/showthread.php?t=1388164&page=23](http://ubuntuforums.org/showthread.php?t=1388164&page=23) post #265 contains the patch and #224 the instructions for a previous version.

Hope with this you can solve the touchpad issues, it worked for me in Ubuntu 11.10 64bits.


Hi
Thank you very much. It worked for me

---

### Post by Magalaan on 2012-12-25
I found out a solution for the right click in the touchpad

right click does not work. But if you right click with two fingers!

If you acivate scrolling with two fingers in the system settings that works fine too.

---

### Post by F i L on 2013-01-15
+1 @ Magalaan

However in lubuntu I cannot find any settings for mouse side scrolling. The activation option you say appears in gnome settings in ubuntu ?

---

### Post by Magalaan on 2013-02-22
> **F i L said:**
> +1 @ Magalaan

However in lubuntu I cannot find any settings for mouse side scrolling. The activation option you say appears in gnome settings in ubuntu ?

Sorry, you are right, I did not realize that I also had gnome3 installed and this gives these extra settings.

---

### Post by h3nr1ke on 2013-04-01
Hello guys... just to thanks for the answers... solved the problem with the suspend/close the notebook

just create a file in the /etc/pm/config.d, I named it of suspend and include the line... now its working...

I did it in the 12.04 LTS in the Pavilion Dm1 brazilian version

thanks

---

