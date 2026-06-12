---
title: "Touchpad not working"
date: 2010-05-30
forum: Hardware
---

### Post by 64mas on 2010-05-30
I didn't see a topic like this on page 1, so here goes:

Hi.
I just recently obtained a used laptop, and decided to try ubuntu. I got it installed, after some issues with acpi, and got it to boot up (had to disable acpi in grub). Now, having gone through that, I find that my touchpad isn't responding. so I borrow my dad's usb mouse, (im 15) and have been using that. I have been doing some research, trying to figure things out, and installed tpconfig. I ran it and heres the reults ```
tom@tom-desktop:~$ sudo tpconfig
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
tom@tom-desktop:~$ tpconfig
Could not open PS/2 Port [/dev/psaux].
tom@tom-desktop:~$ sudo tpconfig
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
tom@tom-desktop:~$ 
```

Thanks for any help you can give me,
                                              --Tom

Edit: I forgot to mention, I'm running 10.04, whatever animal that is.

---

### Post by 64mas on 2010-05-30
Still trying, if it helps, tpconfig looks like it's acting wierd still. 
```
tom@tom-desktop:~$ sudo tpconfig -d -x
[sudo] password for tom: 
Could not open PS/2 Port [-x].
tom@tom-desktop:~$ sudo tpconfig
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
tom@tom-desktop:~$ sudo tpconfig -d -i
Could not open PS/2 Port [-i].
tom@tom-desktop:~$ sudo tpconfig -x
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Performing software reset on TouchPad.
Software reset of TouchPad complete.
tom@tom-desktop:~$ tpconfig -i
Could not open PS/2 Port [/dev/psaux].
tom@tom-desktop:~$ sudo tpconfig -i
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click
tom@tom-desktop:~$ 
```

---

### Post by cefn on 2012-01-03
Hard to offer anything without knowing the model of your laptop. I'm struggling a bit with my touchpad, but it seems to be this bug, which is specific to Dell...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760142)

---

