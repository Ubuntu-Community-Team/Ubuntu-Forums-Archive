---
title: "Problem with Jaunty Jackalope + Microsoft Bluetooth Notebook Mouse 5000"
date: 2009-04-25
forum: Hardware
---

### Post by K. Hendrik on 2009-04-25
Hi, i upgraded to Jaunty and now my mouse doesn't work. Under Intrepid everything was fine but now it says connetion Successful established but it immidiatly breaks down and nothing works.
(sorry for my poor english)

---

### Post by shoobs on 2009-04-25
I can confirm this. My Microsoft Bluetooth Notebook Mouse 5000 was working fine in Intrepid.

Just installed Jaunty today. Going through the "setup new bluetooth device" works, but no connection is established with the mouse.

It seems as if this is a known problem. There is a bug report here (with a hackish workaround):
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727)

---

### Post by K. Hendrik on 2009-04-25
Hi, thanks that worked, i don't know if it will be working after a restart but I'll check that later.

---

### Post by wamukota on 2009-04-29
I used [http://blog.chinthaka.org/2008/09/getting-microsoft-bluetooth-mouse.html](http://blog.chinthaka.org/2008/09/getting-microsoft-bluetooth-mouse.html) to get my MS bluetooth notebook mouse 5000 to work in the 9.04 / 64 bit on my Dell Vostro 1310, and that worked.  Only now my keyboard and synaptic-touchpad are borked. No respons at all. Ik have to reboot and remove the Bluetooth dongle in order to get them working again, but then I am stuck without my bluetooth mouse.

Any clues what I might do?

Alain

---

### Post by K. Hendrik on 2009-05-01
Hi, I don't really know how that could break your keyboard and touchpad but after some testing i just want to let you now the workaround in the bugreport mentioned before works perfect for me perhaps you should try that

---

### Post by wamukota on 2009-05-02
I do think now that the problem of frozen KB has nothing to do with bluetooth.  It occurs even with any bluetooth service running now.

I think that it could be linked to running the 64-bit, but I will continue this issue in the Dell Ubuntu Support forum.

Txs

Alain

---

### Post by netwarriorwy on 2009-05-05
[COLOR="DarkOrange"]It's working so far for me[/COLOR]

Thanks a lot! I haven't reboot yet but as soon as i do i'll tell u what happened.

---

### Post by charcaroth on 2009-05-30
I found a solution on the launchpad site.[ ]("http://https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727") I'm using MS bluetooth mouse 5000 and Ubuntu Jaunty on a Toshiba A105-S4004 model laptop (as well as on an HP 2133 netbook) to replace a two year old Logitech V220 that's losing connectivity when it gets more than a foot from the receiver. (I think it's overall a loss of power issue to the USB ports that's causing the Logitech's issues.)  I'll post what I found below:  
>>
>>
abais wrote on 2009-04-01: (permalink)

I had the same problem with Jaunty Beta (Microsoft notebook 5000 for my Netbook Samsung NC-10)
I've solved the problem :

1) install the bluez-compat package with terminal

sudo apt-get install bluez-compat

2)Pair the mouse with the bluetooth manager. The manager will say that the pairing is "successfull"
Although the mouse won't worked... this step has to be down...

3) In the terminal, type :

sudo hidd --search

You should see something like

Searching ...
Connecting to device 00:XX:XX:XX:XX:XX (your mouse MAC)

Done. Your mouse should be working now.
>>
>>

Yes, this seems similar to a fix suggested on another part of this site, but that fix didn't work and the one on launchpad did.  Just wanted to share this solution.

---

### Post by HealyHQ on 2009-06-19
> **charcaroth said:**
> I found a solution on the launchpad site. I'm using MS bluetooth mouse 5000 and Ubuntu Jaunty on a Toshiba A105-S4004 model laptop (as well as on an HP 2133 netbook) to replace a two year old Logitech V220 that's losing connectivity when it gets more than a foot from the receiver. (I think it's overall a loss of power issue to the USB ports that's causing the Logitech's issues.)  I'll post what I found below:  
>>
>>
abais wrote on 2009-04-01: (permalink)

I had the same problem with Jaunty Beta (Microsoft notebook 5000 for my Netbook Samsung NC-10)
I've solved the problem :

1) install the bluez-compat package with terminal

sudo apt-get install bluez-compat

2)Pair the mouse with the bluetooth manager. The manager will say that the pairing is "successfull"
Although the mouse won't worked... this step has to be down...

3) In the terminal, type :

sudo hidd --search

You should see something like

Searching ...
Connecting to device 00:XX:XX:XX:XX:XX (your mouse MAC)

Done. Your mouse should be working now.
>>
>>
ed like a ch
Yes, this seems similar to a fix suggested on another part of this site, but that fix didn't work and the one on launchpad did.  Just wanted to share this solution.

Thanks so much! Worked like a charm! :D

---

### Post by Xinef on 2009-07-06
1- This is not a fix, this is a workaround, using deprecated utilities to get a mouse to work is not a viable way to handle it on the longer run.

2- I use a microsoft BT presenter 8000 on a Lenovo x200, and it turns out the mouse will not directly connect upon boot. More precisely, it is connected as it is visible in the bluetooth properties, and the bluetooth activity led blinks when I move the mouse around, but for some reason, it is not recognized as an input device, and I have to switch the mouse off then back on to get it to work properly.

I tried to compile and install the latest bluez packages, but the result is the same.

This seems to be a double issue, one with the mouse not being properly paired without doing an hidd --search, and another one where the mouse device is not properly set up right after boot.

edit: just tested this on an up-to-date fedora 11 install and got no problem, hope this get fixed in a soon to come update...
edit2: I even tried to compile and install the latest gnome-bluetooth package. Though I got a nice and up to date bluetooth management under gnome, and no longer have to bother with retro-compatibility issues when adding the mouse, I still get the same problem of connected but not correctly setup mouse upon startup... this is a problem beyond bluetooth it seems. Wonder if it has anything to do with HAL... :/

---

### Post by picaresqu3 on 2009-08-17
> **charcaroth said:**
> I found a solution on the launchpad site.[ ]("http://https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727") I'm using MS bluetooth mouse 5000 and Ubuntu Jaunty on a Toshiba A105-S4004 model laptop (as well as on an HP 2133 netbook) to replace a two year old Logitech V220 that's losing connectivity when it gets more than a foot from the receiver. (I think it's overall a loss of power issue to the USB ports that's causing the Logitech's issues.)  I'll post what I found below:  
>>
>>
abais wrote on 2009-04-01: (permalink)

I had the same problem with Jaunty Beta (Microsoft notebook 5000 for my Netbook Samsung NC-10)
I've solved the problem :

1) install the bluez-compat package with terminal

sudo apt-get install bluez-compat

2)Pair the mouse with the bluetooth manager. The manager will say that the pairing is "successfull"
Although the mouse won't worked... this step has to be down...

3) In the terminal, type :

sudo hidd --search

You should see something like

Searching ...
Connecting to device 00:XX:XX:XX:XX:XX (your mouse MAC)

Done. Your mouse should be working now.
>>
>>

Yes, this seems similar to a fix suggested on another part of this site, but that fix didn't work and the one on launchpad did.  Just wanted to share this solution.

Wish we could put this one to bed for good, but thanks so much for the workaround :D

---

### Post by Alabamian on 2009-09-13
Charcaroth's post, number 8, worked for me. BTW, I got the message from the Setup Devices GUI app that the 5000 MS Mouse did NOT pair, but it worked anyway.  Yay!

Thanks!

---

### Post by kirschjoghurt on 2010-09-10
I've just installed bluez-compat and removed-paired again the mouse. and it worked! =)

---

