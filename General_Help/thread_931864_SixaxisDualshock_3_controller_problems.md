---
title: "Sixaxis/Dualshock 3 controller problems"
date: 2008-09-27
forum: General Help
---

### Post by robglinka on 2008-09-27
My sixaxis controller connects, but the buttons don't do anything.

I've followed a few guides on how to install a Sixaxis controller over Bluetooth, and successfully got the controller to connect. ([https://help.ubuntu.com/community/Sixaxis]("https://help.ubuntu.com/community/Sixaxis") was very helpful. dmesg shows the controller connected, and the bluetooth properties show it connected.

If I do a cat /dev/input/js0, I can see a quick dump of some data, but pressing buttons doesn't show any new input.

If I use jscalibrator, it shows the correct controller connected, but buttons don't do anything. I've seen some people saying jscalibrator can cause problems, so I tried uninstalling it, but that didn't help.

If I try to play a game that should work, nothing happens. I've tried this controller on two computers now (one ubuntu, one xubuntu), and it does the same thing.

Any thoughts?

---

### Post by robglinka on 2008-10-01
Has no one had this issue in the past? I can't find anything on a google search about this.

I've even tried exchanging the controller for a new one, hoping it was a bad controller.

---

### Post by robglinka on 2008-10-01
I'm really trying here, but it is a bit discouraging that no one as replied to this thread.

After (hours of) googling, I found some information about older kernels not sending the "operational" command to the sixaxis controller. I'm thinking this might be the issue.

Here's a website I found: [http://ps3.jim.sh/sixaxis/usb/](http://ps3.jim.sh/sixaxis/usb/) where it describes the issue EXACTLY as I describe it, so I'm wondering if there's something that I'm not doing, or if there is some odd bug in Heron where HID_REQ_GET_REPORT is not being sent to the sixaxis.

Any thoughts? Help? Anything?!?!?!

---

### Post by mgc8 on 2008-10-03
Hello,

I posted some info at Phoronix, you may want to keep an eye over that thread as well:
[http://www.phoronix.com/forums/showthread.php?t=11053](http://www.phoronix.com/forums/showthread.php?t=11053)

Bottomline is, I have noticed the same problem -- the controller connects correctly via bluetooth, the js0 device is created, but no buttons/axis/whatever register. Seems to be a break in the communication stream somewhere between the bluetooth stack and joystick driver (joydev?).

You can run "hcidump -t -V -x" as root and you'll see the buttons and axis in the numbers, however /dev/input/js0 remains silent.

As a workaround, the joypad can be used via USB quite nicely (read the thread I mentioned for the obligatory remarks), at least until a solution is found to the wireless issue...

Hope this helps!

---

### Post by robglinka on 2008-10-03
Ah-HA, you're correct! (kind of)

hcidump DOES show responses from the controller, which means that everything is working correctly from the controller->BLUETOOTH->USB->Kernel. The breakdown is translating it from that to the joystick controller.

Does this give anyone else any ideas? I've posted all of this to our local Unix group and they've promised me an answer soon.

btw, if it matters, my goal is to get this working on my mythxubuntu server.

---

### Post by mgc8 on 2008-10-06
Heh, it turns out the problem was a simple overlook -- after applying the hidd patch, I started hidd and forgot to kill the old one...

So, here's a mini-howto for getting a SixAxis controller to work over bluetooth:

1. Go to [http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html) and download the sixpair.c and patch-hidd-3.19 files (best site ever, thanks Pascal for the great work!)

2. Connect via USB, use sixpair as instructed to pair the gamepad then disconnect USB cable.

3. Get a fresh hidd source and compile:
a) apt-get source bluez-utils
b) apt-get build-dep bluez-utils
c) go into the bluez-utils directory, patch -p2 < patch-hidd...
d) dpkg-buildpackage -rfakeroot
e) dpkg -i <the_new_bluez_utils_package>
f) optional: aptitude hold bluez-utils (at least until this patch gets into upstream)

4. Here is the point where I went wrong:
a) /etc/init.d/bluetooth stop -- make sure hcid and hidd are gone (ps ax|grep hidd) -- don't forget this!
b) hidd --server --nocheck -n (this is only needed the first time to make the gamepad known to the PC)
c) press the PS button
d) check that everything works (jstest, hcidump, etc.)
e) hold PS button for 10sec to stop gamepad, then Ctrl-C the hidd process
f) /etc/init.d/bluetooth start

5. Press the PS button again, and it should automagically connect and show up as a /dev/input/js0 device (if you have kdebluetooth or the gnome version thereof you'll also see a taskbar message to this effect).

Enjoy!

---

### Post by robglinka on 2008-10-06
Great Googlie Mooglies, I fsck'd up the bluez patching.

It works now. Being someone that really NEEDS step by step directions, when I read the really really really awesome directions on the pabr.org and Ubuntu How-To site, and they said "patch bluez-util" but didn't say HOW to patch it, I accidentally skipped that step.

Thanks a TON, everything works perfectly (so far).

I think we should post something because the official Ubuntu "how-to" doesn't have the steps for how to patch the bluez-utils.

Thanks again.

---

### Post by mgc8 on 2008-10-07
[quote="robglinka"]I think we should post something because the official Ubuntu "how-to" doesn't have the steps for how to patch the bluez-utils.[/quote]
I edited the [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis) page to specify the patching step, and I also added some more information regarding hot-plugging in newer X.Org versions. Have fun and feel free to contribute if I missed anything!

---

### Post by robglinka on 2008-10-07
Hey, just a couple updates just to make things crystal clear for people who don't know, like myself. 

Does this look correct? I don't want to add incorrect information into the how-to.

run this command: patch -p2 hidd/main.c patch-hidd-3.19-pabr3 

after the dpkg, cd .. to find the deb that was created (took me a while to figure this one out ;)

dpkg -i bluez-utils_<version>-0ubuntu3_<server type>.deb  (a lot of packages were sitting there waiting for me when I was done.)

Does this make sense.

---

### Post by mgc8 on 2008-10-08
> **robglinka said:**
> 
run this command: patch -p2 hidd/main.c patch-hidd-3.19-pabr3 


Hmm, actually I double-checked it now -- I had run the command from within the hidd/ directory, hence "-p2". When you are inside the main bluez-utils-x.xx/ directory, only "-p1" is required. The file name is not needed, so the correct command would be:
```
patch -p1 < patch-hidd-3.19-pabr3
```

> **robglinka said:**
> 
after the dpkg, cd .. to find the deb that was created (took me a while to figure this one out ;)


Yup, that's correct :)

> **robglinka said:**
> 
dpkg -i bluez-utils_<version>-0ubuntu3_<server type>.deb  (a lot of packages were sitting there waiting for me when I was done.)


Indeed, the source is used as basis for more binary packages. However only the bluez-utils one is required, so the correct line would be:
```
dpkg -i bluez-utils_<version>_<architecture>.deb
```

Note that "0ubuntu3" is actually part of the version and may change.

I've made these updates to the How-To, it should be ok now...

---

### Post by errdayimhustln on 2009-01-15
can some one post a step by step for ubuntu noobs i have only been using this for a few days and want to use my dualshock with mame without wires :)

---

### Post by robglinka on 2009-01-15
The best step by step is in the ubuntu help docs: [https://help.ubuntu.com/community/Sixaxis]("https://help.ubuntu.com/community/Sixaxis"). We've already updated it with all the steps we had to use to get the sixaxis running.

---

