---
title: "Ubuntu 10.04 64Bit Logitech MX5500 Will not Connect Properly"
date: 2010-04-29
forum: Hardware
---

### Post by Dustout on 2010-04-29
Hey, i have just upgraded to Ubuntu 10.04 64bit from Ubuntu 9.10 32bit and my logitech MX5500 keyboard produces the following message upon any key press
[http://img532.imageshack.us/img532/7021/screenshotvgy.png](http://img532.imageshack.us/img532/7021/screenshotvgy.png)
When i hit grant it does nothing, and when i hit "Always Grant Access" it still keeps asking me if i wish to grant access.

Has anyone found a fix to this problem, also as a side node the MX5500 connects via a USB dongle and that USB dongle works at boot and within windows as a plug and play device

---

### Post by adibadi on 2010-04-30
> **Dustout said:**
> Hey, i have just upgraded to Ubuntu 10.04 64bit from Ubuntu 9.10 32bit and my logitech MX5500 keyboard produces the following message upon any key press
[http://img532.imageshack.us/img532/7021/screenshotvgy.png](http://img532.imageshack.us/img532/7021/screenshotvgy.png)
When i hit grant it does nothing, and when i hit "Always Grant Access" it still keeps asking me if i wish to grant access.

Has anyone found a fix to this problem, also as a side node the MX5500 connects via a USB dongle and that USB dongle works at boot and within windows as a plug and play device

I can confirm, I have the same problem with the Logitech dinovo Edge keyboard using the USB dongle

---

### Post by Dustout on 2010-04-30
my solution was to just bypass the dongle and connect directly via bluetooth, but in the future it would be nice to have it plug and play again

---

### Post by K1mp3 on 2010-05-02
> **Dustout said:**
> my solution was to just bypass the dongle and connect directly via bluetooth, but in the future it would be nice to have it plug and play again

I've got this same problem, when I try typing on wireless keyboard or move the mouse I get this popup, which seems to indicate some system policy is blocking the device.
how did you bypass the dongle? or do you have an additional bluetooth on your motherboard?

this is really annoying bug as everything was working fine in 9.10, then update manager popped up promoting an upgrade.... now the machine is just unusable until a fix is found; definitely the last time I'll upgrade; I wonder if its possible to downgrade back to 9.10..?

---

### Post by adibadi on 2010-05-02
Using it on a laptop, so I used the laptop's built in bluetooth.  Hope the problem gets fixed soon though, I don't like this solution since my laptop's bluetooth switch also turns on the wi-fi which I then have to manually disable.

---

### Post by Mr Treat on 2010-05-02
Ubuntu is not responding to my mouse or keyboard at all. When the log in screen comes up, mouse pointer is in the middle of the screen and will not move.

---

### Post by Dustout on 2010-05-02
> **K1mp3 said:**
> I've got this same problem, when I try typing on wireless keyboard or move the mouse I get this popup, which seems to indicate some system policy is blocking the device.
how did you bypass the dongle? or do you have an additional bluetooth on your motherboard?

this is really annoying bug as everything was working fine in 9.10, then update manager popped up promoting an upgrade.... now the machine is just unusable until a fix is found; definitely the last time I'll upgrade; I wonder if its possible to downgrade back to 9.10..?
i have bluetooth on my motherboard, so kinda lucked out that way. Also as a side note my old friend "randomly enable the control pointer with keyboard" option is still around.
[http://img232.imageshack.us/img232/6960/screenshotpa.png](http://img232.imageshack.us/img232/6960/screenshotpa.png)
:(

this new release is really growing on me tho, just wish i could get google chrome to move the close buttons onto the left :)

---

### Post by K1mp3 on 2010-05-03
I cannot see anything obvious on the log either... no errors as far as I can see

(II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event5)
(**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event5"
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event6)
(**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event6"
(II) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
(II) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
(II) Logitech Logitech BT Mini-Receiver: Found relative axes
(II) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
(II) Logitech Logitech BT Mini-Receiver: Found absolute axes
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
(WW) Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse2)

---

### Post by raggari on 2010-05-03
This is an issue also for me. I have Dell BT mouse and keyboard. They are connected to the Dell BT dongle. The only way to get them working are:
1) Use Gnome BT manager
2) Boot computer and use keyboard and mouse during boot. If you wait until X starts then the don't work anymore.

I think that there is enough information to open bug report for this issue.

---

### Post by K1mp3 on 2010-05-03
I found a workaround for Logitech from this bug report [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288)

change a line in /lib/udev/rules.d/70-hid2hci.rules
 from
 # Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 

to


 KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

the only drawback is, I've lost the bluetooth icon from top right... but I rather have working keyboard and mouse than the BT icon

---

### Post by moresun on 2010-05-03
Thanks to K1mp3

:popcorn:

changing the lines in /lib/udev/rules.d/70-hid2hci.rules as you proposed worked for me as well on a 32bit 10.04 Ubuntu.

Greetings
Max

---

### Post by evzonas on 2010-05-03
how do i change these lines??? 
i tried changing them and then save as ,and an eroor 'could not save the file'' appeared.

How do i proceed???

---

### Post by smottt on 2010-05-04
Have you tried doing sudo?

```
sudo gedit 70-hid2hci.rules
```or

```
sudo nano 70-hid2hci.rules
```this should work.

---

### Post by Dustout on 2010-05-16
i tried that fix and wow so much better than having to re-connect each time i boot into a different OS. Thanks so much for the fix :P:P:P:P

---

### Post by miesnerd on 2010-05-27
hey all-
My mx5500 and the corresponding mouse work just fine, but the keypad wont work. Any help on that?

---

### Post by Roanoke on 2010-06-19
Well, this fixed the keyboard for me.

But now my mouse does not work (better, I guess).

I have found nothing but pain in 10.10 (why would you ever change bluetooth management, the keyboard worked perfectly before ubuntu started getting involved, the dongle and the devices communicated and everyone was happy). I will continue my search, I guess.

---

