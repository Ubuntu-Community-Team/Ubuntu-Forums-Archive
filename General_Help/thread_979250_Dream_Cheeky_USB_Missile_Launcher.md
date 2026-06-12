---
title: "Dream Cheeky USB Missile Launcher"
date: 2008-11-11
forum: General Help
---

### Post by hambone79 on 2008-11-11
I stumbled upon a cool little program over at Google code to operate the Dream Cheeky USB missile launcher ([http://code.google.com/p/pyrocket/](http://code.google.com/p/pyrocket/)). The program works great for the most part...it allows me to move the launcher in any direction and even allows me to use my Logitech gamepad. The only problem is that it won't fire the missiles.

I filed a problem report on the Google code project page, but so far I haven't heard anything from the developer. I'm just wondering if anyone has used the pyrocket software with the green Dream Cheeky missile launcher and if they have been able to get the fire button to work.

---

### Post by Dennis_Rocket on 2008-12-12
Hey guys,

I'm using the pyrocket under Kubuntu Hardy Heron and I got the Blue USB Webcam Missile Launcher. The problem I have is the following error upon starting pyrocket:

Located blue Rocket Launcher device.
Traceback (most recent call last):
File "/usr/bin/pyrocket", line 27, in <module>
launcher = RocketWindow()
File "/var/lib/python-support/python2.5/rocket_frontend.py", line 179, in __init__
self.connect_everything()
File "/var/lib/python-support/python2.5/rocket_frontend.py", line 371, in connect_everything
err_msg = self.rocket_controller.acquire_devices()
File "/var/lib/python-support/python2.5/rocket_backend.py", line 39, in acquire_devices
return_code = launcher.acquire( dev )
File "/var/lib/python-support/python2.5/rocket_backend.py", line 98, in acquire
except usb.USBError, e:
AttributeError: 'module' object has no attribute 'USBError'

I'm new in Linux and can't get it done so if anyone of you has some hints I would be really glad!
And has anyone tried to combine pyrocket with the motion program?

Thx:guitar:

---

### Post by zeronothing on 2008-12-27
I too just recently bought the Cheeky Dream Missile Launcher with Webcam. I installed the pyrocket and when I go to lauch the program I get this message terminal:

Frame acquisition failed.
Located blue Rocket Launcher device.
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/rocket_frontend.py", line 244, in cb_select_new_launcher
    for i, state in enumerate( launcher.check_limits() ):
  File "/usr/lib/python2.5/site-packages/rocket_backend.py", line 208, in check_limits
    limit_signal, = bytes
ValueError: need more than 0 values to unpack
Traceback (most recent call last):
  File "/usr/bin/pyrocket", line 27, in <module>
    launcher = RocketWindow()
  File "/usr/lib/python2.5/site-packages/rocket_frontend.py", line 180, in __init__
    self.cb_select_new_launcher(self.laucher_id)
  File "/usr/lib/python2.5/site-packages/rocket_frontend.py", line 244, in cb_select_new_launcher
    for i, state in enumerate( launcher.check_limits() ):
  File "/usr/lib/python2.5/site-packages/rocket_backend.py", line 208, in check_limits
    limit_signal, = bytes
ValueError: need more than 0 values to unpack


I installed the .deb package from the google code page and I also tried the source code with still the same result. I noticed though if I have the device unplugged and launch the program it will work. When I say it works I mean the application will load but because the device is unplugged you can't control the missile launcher. any help would be great..

---

### Post by kramulous on 2009-01-04
I got that error and not quite sure what the fix was.

Firstly, try different usb ports.  The ones on my Dell monitor didn't work but on the front of the box they do.

Secondly,
try: sudo pyrocket

---

### Post by zeronothing on 2009-01-05
That actually worked. I switched the usb cables to a different port. It seems as though the program doesn't like when you plug the usb cable into a usb hub. The camera part works in the usb hub but the launcher, not so much.

---

### Post by deathromp on 2009-02-06
I'm trying to write a script that will tail the auth log and fire if someone types an incorrect password. What I need help with is figuring out how to send the signals to the device. 

Any suggestions??

When I try echoing the characters to the usb devices, it tells me access denied even as root.

Any help would be appreciated.

---

### Post by //yardo on 2009-03-04
> **deathromp said:**
> I'm trying to write a script that will tail the auth log and fire if someone types an incorrect password. What I need help with is figuring out how to send the signals to the device. 

Any suggestions??

When I try echoing the characters to the usb devices, it tells me access denied even as root.

Any help would be appreciated.

Sounds cool. Wish I had some suggestions...

---

### Post by craig100 on 2010-06-23
I've had a launcher gathering dust for a few years but only just realised there were control packages in the repositories.  I tried pymissiles which works correctly ONCE then dies when you try to open it again. So I tried pyrocket which fires missiles no matter which button is pressed!  My launcher is made by Tenx Technology Inc. and has USB ID: 1130:0202. Has anyone got this type of launcher to work under Ubuntu Lucid?

---

