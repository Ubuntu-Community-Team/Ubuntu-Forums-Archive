---
title: "Motorola KZ500 Bluetooth keyboard issues"
date: 2012-09-06
forum: Hardware
---

### Post by Squall_DA on 2012-09-06
I recently purchased a Motorola KZ500 bluetooth keyboard and touchpad combination. The keyboard is supposed to be compatible with any device that is compatible with the bluetooth HID profile. I can connect the keyboard to my xubuntu computer but neither the keyboard or the touchpad work while connected. I can see in blueman that it is connected but nothing works.

If I try to connect the keyboard to my ubuntu computer with gnome3, it fails to connect every time. As soon as I type the pin code into the keyboard and press enter bluetooth manager tells me the connection failed. I then tried to connect the keyboard to a windows 7 computer and it connected and worked flawlessly. In windows the keyboard uses the standard bluetooth HID driver. I also tried the keyboard in android and it worked flawlessly there too.

I am at a loss as to where to look now. Any help would be greatly appreciated.

---

### Post by cookevillain on 2012-09-06
I just got mine and had the same problem. The problem was the BT applet in GNOME (it is just plain terrible for a miriad of other reasons):

Run `sudo hcidump' (install it if you do not already have it), carefully watch the messages (it helps if you have no other bluetooth activity at the moment) and wait for the message that says

> HCI Event: User Passkey Notification (0x3b) plen 10
    bdaddr 00:00:00:00:00:00 passkey 123456

(your bdaddr and passkey will be different though). You will notice that the passcode that the applet is displaying is different. Enter the pascode that hcidump displays. The keybord should pair. The touchpad will not work, unfortunately (if you keep watching the link with hcidump you will see that the touchpad is functioning but the driver is ignoring it).
Hope this helps.

PS. The bluetooth applet is probably one of the worst software bits in ubuntu (or GNOME, who cares): it has been having problems for years now and nothing has ever got even looked at (say, it is STILL impossible to disable bluetooth and not have it reenabled on on the next login).


> **Squall_DA said:**
> I recently purchased a Motorola KZ500 bluetooth keyboard and touchpad combination. The keyboard is supposed to be compatible with any device that is compatible with the bluetooth HID profile. I can connect the keyboard to my xubuntu computer but neither the keyboard or the touchpad work while connected. I can see in blueman that it is connected but nothing works.

If I try to connect the keyboard to my ubuntu computer with gnome3, it fails to connect every time. As soon as I type the pin code into the keyboard and press enter bluetooth manager tells me the connection failed. I then tried to connect the keyboard to a windows 7 computer and it connected and worked flawlessly. In windows the keyboard uses the standard bluetooth HID driver. I also tried the keyboard in android and it worked flawlessly there too.

I am at a loss as to where to look now. Any help would be greatly appreciated.

---

### Post by Squall_DA on 2012-09-07
I guess I should have been more specific I want to use this keyboard on a xubuntu 12.04 machine. So the default desktop manager is XFCE. But I did try to use hcidump anyways and once again I got the keyboard to connect but it still will not do anything. I can see that the keyboard is connected in bluetooth manager but when I try to use the keyboard it does not work. I am still not sure how to troubleshoot it further.

---

### Post by cookevillain on 2012-09-07
Interesting ... Have you looked at hcidump output to see that the keyboard is transmitting keypresses (in other words, every time you press a key, you see an ACL message flashing by)? If not, then it is not really paired, if yes, something might be wrong with the HID driver. Also, you only need to pair the keybord with the machine once, as it will remember the link key after that. I hate giving `windows style' advice but have you tried to reboot and reconnect the keyboard? Probably stopping bluetoothd is enough but who knows.

Added in edit: can you post your hcidump output after pairing and pushing a few keys?

---

### Post by Squall_DA on 2012-09-07
I thought about the old windows advice of restarting the computer before and it does not fix it. But I do have the output of an hcidump while moving my finger on the trackpad and pushing a few buttons. 

```
device: hci0 snap_len: 1028 filter: 0xffffffffffffffff
> ACL data: handle 35 flags 0x02 dlen 9
    L2CAP(d): cid 0x0042 len 5 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 9
    L2CAP(d): cid 0x0042 len 5 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 9
    L2CAP(d): cid 0x0042 len 5 [psm 0]
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x00 interval 0
    Mode: Active
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x02 interval 20
    Mode: Sniff
> ACL data: handle 35 flags 0x02 dlen 9
    L2CAP(d): cid 0x0042 len 5 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 9
    L2CAP(d): cid 0x0042 len 5 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 9
    L2CAP(d): cid 0x0042 len 5 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 9
    L2CAP(d): cid 0x0042 len 5 [psm 0]
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x00 interval 0
    Mode: Active
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x02 interval 80
    Mode: Sniff
> ACL data: handle 35 flags 0x02 dlen 14
    L2CAP(d): cid 0x0042 len 10 [psm 0]
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x00 interval 0
    Mode: Active
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x02 interval 20
    Mode: Sniff
> ACL data: handle 35 flags 0x02 dlen 14
    L2CAP(d): cid 0x0042 len 10 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 14
    L2CAP(d): cid 0x0042 len 10 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 14
    L2CAP(d): cid 0x0042 len 10 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 14
    L2CAP(d): cid 0x0042 len 10 [psm 0]
> ACL data: handle 35 flags 0x02 dlen 14
    L2CAP(d): cid 0x0042 len 10 [psm 0]
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x00 interval 0
    Mode: Active
> HCI Event: Mode Change (0x14) plen 6
    status 0x00 handle 35 mode 0x02 interval 80
    Mode: Sniff
```
The first three ACL data messages are the trackpad the rest are me pushing random keys. So it appears that the keyboard is sending data to the computer. I'm guessing it is a driver issue. Any thoughts on what to do from here? T

Thanks for your help so far

---

### Post by cookevillain on 2012-09-07
Looks like it does pair (running hcidump -x will also show the content of the ACL packets but I have no doubt they are the keypresses).

Do you have both hid and hidp drivers loaded (run `lsmod | grep hid' to check)? Sorry, I am grasping for straws now.

Here is what I get as the result of the command above:

hidp                   22351  2 
hid                    77367  1 hidp
bluetooth             148869  32 hidp,rfcomm,bnep,btusb

Do you have any other desktops/laptops running a different version of ubuntu, or even a different distro to try it out on? I am typing this on the very keyboard we are discussing in Ubuntu 10.4 so the hardware should be fine. Hang in there!

---

### Post by ChipperJones on 2012-09-07
I have been using one of these [wireless motorola bluetooth keyboard]("http://www.wirelessground.com/motorola-wireless-bluetooth-keyboard-with-trackpad.html") with my Xoom for a while and just now thought about pairing it to my desktop, glad i found this before i tried...will deffinately be subscribing to this thread..

---

### Post by Squall_DA on 2012-09-07
Yes both drivers show that they are loaded using lsmod | grep hid. I have tried this on both a xubuntu desktop and an ubuntu laptop and it does not work with either. Both are version 12.04 so my only guess is that something must have changed since 10.04. Now the question is what changed that broke compatibility with this keyboard.

---

### Post by cookevillain on 2012-09-07
Hmm, I am running low on ideas. Can you try to switch to a text console (Ctl-Alt-F2 will take you to one and Ctl-Alt-F7 will take you back to X) and see if the keyboard works there. If the driver is at fault, this would do nothing, but just on the off-chance it is GNOME's fault ...

---

### Post by Squall_DA on 2012-09-08
It doesn't work in console either.
Im beginning to think something was changed in ubuntu that broke compatibility with the keyboard

---

### Post by cookevillain on 2012-09-08
One more thing: can you boot into one of the older kernels (you have probably run upgrades by now and as most people kept the old kernels installed)? You can do it from the grub menu at boot up. Sorry about lack of suggestions, I will have a better idea when I upgrade to 12.??

---

### Post by nPoc on 2012-09-11
Any updates on this?

I got the keyboard to pair, and hcidump is showing output, but no keypresses or mouse movement get's translated to the screen.

I think theres more than a few of us who bought these keyboards on woot recently.  I'll probably take a closer look tomorrow.

---

### Post by nPoc on 2012-09-11
Launchpad bug opened.

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1048944](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1048944)

Let's try to keep most of the questions, and this affects me posts in this thread, and only useful information in the bug.  The Ubuntu devs are overworked as it is.

---

### Post by Squall_DA on 2012-09-11
I did try a few older kernels and there was no change. I didn't go back super far though.

Edit: yeah I bought this on woot also to use with an htpc I was really disappointed when it didn't work

---

### Post by nPoc on 2012-09-18
Has anyone made any progress on this?

---

### Post by Squall_DA on 2012-09-18
I'm going to guess no. I have not had anytime to look at it myself. I am very busy with my senior design class right now. I am hoping to have some more time in a couple of weeks, but currently I'm not going to have time.

---

### Post by nPoc on 2012-09-18
If this affects you make sure to go here
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1048944](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1048944)

and click the 
This bug affects me link at the top.

---

### Post by cookevillain on 2013-01-30
Seems there has not been any progress on this so far. I have finally `upgraded' to 12.04 (also switched to Mint on another machine): both machines have trouble with the keyboard. I have found some references that the DBus layer in bluez got changed which is causing all sorts of problems. I have also noticed in Mint the mouse shows up as a battery (?). It may be that the BT messages contain someting about the state of the battery but then again it has been showing empty for the last three months ... . In any case, I intend to wait for the bluez devs to fix this mess: should be any decade now.

---

### Post by kiniyaloca1 on 2013-02-12
Hey guys, I too was having trouble connecting my keyboard to Ubuntu 12.04. I did some Googling and some tinkering and finally got it working. 

First I installed Blueman Device Manager (It is in the Ubuntu software center)

Removed the keyboard from my devices

Followed the steps here: ([http://goo.gl/E0U8t]("http://goo.gl/E0U8t")) on page 6 to factory reset my keyboard and forget all other devices it has connected to.

Opened Devices on the Blueman applet (you may have to re-log in order to enable it, then it is accessible from the notification bar)

Proceeded to add my keyboard via Blueman, and entering '0000' for the pin. 

Finally, allowed it to use the Input Service for the keyboard.

And that should do it. Hope it helped you guys :)

---

### Post by cookevillain on 2013-03-06
Nope, this does not seem to work. Still the same: connects, pairs and produces keystrokes (verified by hcidump) but no output on the console.
I am trying to move away from Ubuntu, anyone has any ideas which distribution offers somewhat sane hardware support? I just do not have time to mess with so much silliness. Everything used to work just fine until Ubuntu folks decided to `improve' things.

---

### Post by cookevillain on 2013-03-06
The manual you linked to is a different model (does not have the touchpad, for example, also the pin is not 0000 in every case as the manual suggests, verified by experience). Thanks for the input. Back to my question: anyone knows a distro that does not use dbus, systemd and relies on something other than idiot-designed bluez?

---

