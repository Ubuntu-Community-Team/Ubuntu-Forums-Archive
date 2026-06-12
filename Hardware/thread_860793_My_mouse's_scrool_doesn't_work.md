---
title: "My mouse's scrool doesn't work?"
date: 2008-07-15
forum: Hardware
---

### Post by NikolasP on 2008-07-15
Hi,

I have installed Ubuntu and loving it but I have one problem.  My RocketFish mouses scroll pad doesn't work?

How can I solve this problem?  Any ideas?

Also my other problem I have is.  I have CrossOver Linux and now I try to install it but in the Archive Manager it tells me file type not supported??


Thanks,

nikolas

---

### Post by vreppeto on 2008-12-12
I tried to post my solution to this thread:
[http://ubuntuforums.org/showthread.php?t=355695&page=4](http://ubuntuforums.org/showthread.php?t=355695&page=4)

but it is no longer active. So here is my solution for 8.04 hardy.

I assume you are trying to use the Bluetooth dongle that came with rocketfish mouse and keyboard.  The thread listed above will explain why your scroll wheel does not work.

   1)  Turn the pc off. Press the pairing button on the keyboard and then the dongle.  Now the keyboard will work work even for bios settings and grub but not the multimedia keys.  now unplug the rocketfish dongle.
2) Obtain and plugin a generic bluetooth dongle (I use a trendnet tbw-101ub and there is another listed in the aforementioned thread) and a standard ps2 or usb keyboard.  follow the instructions in this article: 
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)
or
a) Right click the bluetooth icon in the toolbar and choose preferences.
b) Click the services tab and select input services..
c) Push the pairing button on the mouse.
d) Click the "add" button in bluetooth preferences. After a few seconds the mouse will appear in the list and you can select it and click "connect".
e) Now choose the adapter tab in bluetooth preferences, highlight the mouse device and click "make trusted."

3) Now you can plug in your rocketfish dongle and your keyboard and mouse should work fine.  

     You will probably want to unplug your rocketfish dongle any time you want to add another bluetooth device. 

BTW  my rocketfish kb and mouse are the old model RF-BTMKY.

---

### Post by stampeder on 2009-02-26
That list of instructions probably works with the newer models too (RF-BTCMBO) but here's a similar method I wrote to get it working from any environment including the command line: 

[http://www.user.dccnet.com/jonleblanc/code/bmw.txt](http://www.user.dccnet.com/jonleblanc/code/bmw.txt)

---

### Post by stampeder on 2009-02-27
Today I put the 2 USB Bluetooth dongles side-by-side and booted up the machine. When I ran the script the hidconfig command segfaulted and locked out both the keyboard and mouse! I separated the 2 dongles by about 6 inches and hit the reset button. All is running properly again.

---

