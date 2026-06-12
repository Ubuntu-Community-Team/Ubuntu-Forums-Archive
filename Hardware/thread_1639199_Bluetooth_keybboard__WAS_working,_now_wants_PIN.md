---
title: "Bluetooth keybboard  WAS working, now wants PIN?"
date: 2010-12-06
forum: Hardware
---

### Post by michaelveloz on 2010-12-06
Hiya
I have a Microsoft bluetooth keyboard that works fine on my laptop with my previous version of Ubuntu.

I'm now dual booting my desktop machine and trying to pair the keyboard with it. The pairing process seems to have changed and something isn't working..

When I pair, I get prompted to enter some digits + Enter into the keyboard, which I do. So far so good.

Here's the new thing.. right after the dialog comes back and says that the pairing was completed, another dialog pops up that says the keyboard wants to pair with the desktop, and would I please enter an PIN.

WTH?  I've never had to enter a PIN when connecting thins keyboard to any of my systems. Honestly, I don't even know what a PIN is in the context of Bluetooth.

Any ideas on how I might try to get this keyboard working?
(Also, when I dual boot this desktop machine back to windows, it has no problem pairing with the keyboard)

THANKS!
Michael

---

### Post by pricetech on 2010-12-06
Try 0000 as a PIN.  Not sure how you'll enter it unless you have another keyboard, but that's probably what it wants.

Check your BlueTooth settings on your computer also.  I'm pretty sure you can preconfigure that.

---

### Post by michaelveloz on 2010-12-06
thanks for the reply. 0000 didn't seem to help.

Another weird thing. Sometimes a few minutes after I add the device (whether I enter a PIN of 000 or just cancel out of that dialog) the keyboard light starts blinking (like it does when I manually put it into discovery mode).  I'm not sure who's initiating this later conversation - the keyboard or ubuntu?

In any event, it still aint working :*(

Michael

---

### Post by fbolduc on 2011-02-22
I've got the same problem with my Microsoft Bluetooth Keyboard 6000.

Also, /var/log/syslog says:

bluetoothd[...]: pin_code_request (sba={some_address}, dba={some_address})
bluetoothd[...]: Connection refused (111)

I don't know what the PIN is. Is this hardcoded into the keyboard or is it something one can set?

---

### Post by fbolduc on 2011-02-23
I finally got it to working by compiling my own version of bluez and blueman as explained on this thread:

[http://askubuntu.com/questions/12502/how-do-i-get-the-apple-wireless-keyboard-working-in-10-10/24050#24050](http://askubuntu.com/questions/12502/how-do-i-get-the-apple-wireless-keyboard-working-in-10-10/24050#24050)

It references this post:

[https://prodigyone.com/in/doc/docs.php?keyname=UBUNTU%2BBLUETOOTH](https://prodigyone.com/in/doc/docs.php?keyname=UBUNTU%2BBLUETOOTH)

Not for the faint-hearted, but it works. I hope this gets fixed in 11.04.

---

### Post by glennst01 on 2011-06-29
> **michaelveloz said:**
> thanks for the reply. 0000 didn't seem to help.

Another weird thing. Sometimes a few minutes after I add the device (whether I enter a PIN of 000 or just cancel out of that dialog) the keyboard light starts blinking (like it does when I manually put it into discovery mode).  I'm not sure who's initiating this later conversation - the keyboard or ubuntu?

In any event, it still aint working :*(

Michael
Hi,   Did you ever get it to work?  I am using a bluetooth keybd and mouse on my iMAC.  Both are trying to initiate pairing.  Only get response concerning pairing mouse  -  but can't use keybd to enter PIN.  Finally, Ubuntu gives up. So, back to my opening question - did you get it to work or can you provide any additional insight?

---

