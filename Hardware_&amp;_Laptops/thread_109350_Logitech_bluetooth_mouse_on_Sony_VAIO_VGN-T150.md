---
title: "Logitech bluetooth mouse on Sony VAIO VGN-T150"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by fastluck on 2005-12-28
I got a Logitech bluetooth mouse P/N 852295, PID LZ543AA and it won't work under Breezy.

I installed kdebluetooth, and now when I boot, kbluetoothd pops up a window saying "bluetooth adapter found".

When I run hcitool inq, scan and con, I get absolutely nothing:

```
root@roadrage:/home/fastluck# hcitool inq
Inquiring ...
root@roadrage:/home/fastluck# hcitool scan
Scanning ...
root@roadrage:/home/fastluck# hcitool con
Connections:

```

Any ideas will be greatly appreciated.

Cheers,

John

**Update: ** Solved--see fix below.

---

### Post by fastluck on 2005-12-28
I wrote the following script and called it from my bootmisc.sh and now my mouse works flawlessly.  Just replace "XX:XX:..." with the address on the bottom of your mouse:

```
#!/bin/bash
modprobe hidp
hcid
hidd --server
hidd --connect XX:XX:XX:XX:XX:XX
```

I used an & following the name of the script (which I called bluetooth-mouse), so that boot time wouldn't be increased.  So sometimes the mouse doesn't work right away in the login screen--it takes a couple of seconds after the login screen to come up before you can move the cursor.

If you don't know the address to pass to the --connect argument, push the button on the bottom of the mouse after loading hidp and hcid, and type this code:
```
hidd --search
```

It might take a couple of tries--if it doesn't work the first time, give it a few seconds after hitting the button and try it again.

FWIW, it took me about 45 minutes to get my mouse working under linux.  It took me three times as long to get it working on Windows, because I had to figure out (on my own) about unloading and reloading some other drivers. It also took me three tries to get Logitech's mouse software installed.  So much for non-free software.

---

### Post by tungsai on 2007-11-30
Ok-- I'm trying everything here... let me just verify to another owner of the M-RBB93, that you just hold down the "Reset" button for about a second, the little LED under the "ON" position blinks, and then you should be able to type > hidd --connect <address> ?

'cause, well, that don't work for me. :(

it's like Ubuntu can see my mouse, but can't connect to it. I am trying to locate the product manual from logitech but they don't have it easily findable.

WAB

---

