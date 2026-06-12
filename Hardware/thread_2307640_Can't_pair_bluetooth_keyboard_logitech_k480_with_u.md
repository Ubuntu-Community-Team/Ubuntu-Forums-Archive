---
title: "Can't pair bluetooth keyboard logitech k480 with ubuntu 15.10"
date: 2015-12-27
forum: Hardware
---

### Post by MechaMechanism on 2015-12-27
The GUI simply never shows anything.  Some workarounds exist, but there real old and use commands that don't exist anymore.  What do I do.

---

### Post by tokyobadger on 2015-12-27
> **MechaMechanism said:**
> The GUI simply never shows anything.  Some workarounds exist, but there real old and use commands that don't exist anymore.  What do I do.
1. Hardware specs of the machine with Ubuntu 15.10 installed
2. Confirm if Ubuntu/Kubuntu/Xubuntu/other
3. Output of uname -a
4. Output of hcitool dev
5. Output of hciconfig
6. "GUI" of what application
7. Which workarounds have you looked at - urls 
8. Which "commands" no longer exist
9. Ensure that your replies to #3, #4, #5 are placed in code tags

---

### Post by MechaMechanism on 2015-12-27
> **tokyobadger said:**
> 1. Hardware specs of the machine with Ubuntu 15.10 installed
2. Confirm if Ubuntu/Kubuntu/Xubuntu/other
3. Output of uname -a
4. Output of hcitool dev
5. Output of hciconfig
6. "GUI" of what application
7. Which workarounds have you looked at - urls 
8. Which "commands" no longer exist
9. Ensure that your replies to #3, #4, #5 are placed in code tags

1.  System76 - Wild Dog Pro - With factory installed bluetooth.  Bought it on November 26th I think and got it on December 4th 2015.
2. Ubuntu 15.10 64 bit with all updates as applied of December 26th, 2015.
3.  ```
nate@frontier:~$ uname -a
Linux frontier 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
4.  ```
nate@frontier:~$ hcitool dev
Devices:
    hci0    7C:5C:F8:19:FB:E4
```
5.  ```
nate@frontier:~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 7C:5C:F8:19:FB:E4  ACL MTU: 1021:5  SCO MTU: 96:6
    UP RUNNING PSCAN ISCAN 
    RX bytes:8511 acl:0 sco:0 events:187 errors:0
    TX bytes:4163 acl:0 sco:0 commands:143 errors:0
```
6.  Ubuntu 15.10 - System Setting / Bluetooth.
7a.  [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1035431/comments/9](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1035431/comments/9)
7b.  [https://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/Pairing-Logitech-k480-and-Kubuntu-14-04/m-p/1311477](https://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/Pairing-Logitech-k480-and-Kubuntu-14-04/m-p/1311477)
8.  bluez-simple-agent

Hope this helps.

---

### Post by jeremy31 on 2015-12-27
I am not sure what you need to do but my K480 works with Ubuntu 15.10 but it isn't as nice to type on as the keyboard on my laptop, I just picked it up today to use with my tablet

I presses and held the button for Windows/Android/Chrome OS until it started flashing then used the bluetooth GUI to search.  It did take a little longer than normal for the next button to be able to be pressed to continue to pairing which involved typing a PIN on the K480 and pressing Enter

---

### Post by MechaMechanism on 2015-12-27
> **jeremy31 said:**
> I am not sure what you need to do but my K480 works with Ubuntu 15.10 but it isn't as nice to type on as the keyboard on my laptop, I just picked it up today to use with my tablet

I presses and held the button for Windows/Android/Chrome OS until it started flashing then used the bluetooth GUI to search.  It did take a little longer than normal for the next button to be able to be pressed to continue to pairing which involved typing a PIN on the K480 and pressing Enter

YES!  That's it!  I needed to press and hold the button to put it in discovery mode.  The packaging did not contain any instructions as to how to put the keyboard in dicovery mode.  Thank you.  Problem solved.

---

### Post by tokyobadger on 2015-12-27
Glad to hear jeremy31's advice resolved the issue.

Thank you for the detailed information in reply to my questions - they may help another person in the future, as might [this how-to](http://www.karansinghsisodia.com/how-to-setup-logitech-k480-keyboard-with-ubuntu-14-04/)

If you haven't already, mark the thread as solved - this also helps others when looking for a successful solution to their problems

---

### Post by MechaMechanism on 2015-12-27
> **tokyobadger said:**
> Glad to hear jeremy31's advice resolved the issue.

Thank you for the detailed information in reply to my questions - they may help another person in the future, as might [this how-to]("http://www.karansinghsisodia.com/how-to-setup-logitech-k480-keyboard-with-ubuntu-14-04/")

If you haven't already, mark the thread as solved - this also helps others when looking for a successful solution to their problems

Thank you.  Thread marked solved.

---

