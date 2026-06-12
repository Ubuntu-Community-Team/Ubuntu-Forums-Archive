---
title: "Ubuntu 12.04 Freezes on Lenovo L430"
date: 2012-09-10
forum: Hardware
---

### Post by Linux_cat on 2012-09-10
Hi, seems like a common issue accross the board with no real resolution, I have a Lenovo L430 which I purchased recently, I installed 64-bit Ubuntu 12.04 with kernal 3.2.0.30-generic, with unity desktop and im getting system freezes a few times a day, I have to do a hard reset (hold power button down) to reset my machine, the mouse pointer freezes and the laptop is completely unresponsive. 

The action I've taken so far:

1. Removed Unity desktop, replaced with Xfce
2. Replaced Open Java with Sun

I however still got a freeze, very annoying.

I know allot of people are experiencing these issues at the moment, and upgrading to 3.4 kernal seems to be an option, however im a bit reluctant in case it makes matters worse as I use the latop for work and cant afford to have a load more crashes during my work day.

Any recommendations?

---

### Post by linrunner on 2012-09-10
Hi,

you may try the boot option **noapic**.

---

### Post by offgridguy on 2012-09-10
Although I am not much help, I am very interested in this thread as I have a recent install
ubuntu 12.04,  3.2.0.30-generic with unity desktop also on a lenovo laptop, in my case L512.

---

### Post by Linux_cat on 2012-09-10
Thanks, ill try the noapic option and see how it goes, I had another crash today but lucky it was right towards the end of the day.

Ill run it for a couple of days and report back.

---

### Post by Linux_cat on 2012-09-11
The noapic option didnt help, my lappy has crashed already today after about 10 mins of work!

really trying to isolate whats going wrong, its a total freeze so I cant see anything in the logs, anyone else have any ideas?

---

### Post by Linux_cat on 2012-09-11
So ive managed to find some output in the kern.log, im getting the following:

    1.065192] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug

any ideas

---

### Post by Linux_cat on 2012-09-11
ok, so I set the pci=nocrs option in grub, i then get the following:

```
PCI: Using host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
```

then when i change it back, i get

```
PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
```

you have to be kidding me!

---

### Post by Linux_cat on 2012-09-11
ive installed the  3.5.0-030500-generic, i still see the pci error in the dmesg and logs, ill let everyone know if its anymore stable

---

### Post by Linux_cat on 2012-09-12
OK, im hoping that I am not speaking to soon...but the kernel upgrade has seemed to fix the freezing, also reinstalled unity and everything is working fine..


now just to get the trackpoint working!

---

### Post by linrunner on 2012-09-12
> **Linux_cat said:**
> now just to get the trackpoint working!
The workaround is to load the **psmouse** kernel module with the option **proto=exps**:
```
echo "options psmouse proto=exps" | sudo tee /etc/modprobe.d/trackpoint.conf
```Reboot.

Unfortunately it is impossible to use the middle button for scrolling. 

See [LP #967399]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/967399"). You should sign up there as affected.

---

### Post by Waschmittel on 2012-10-02
Since I do not use the touchpad anyway, I found a way to make scrolling work with the Trackpoint's middle button:

[LIST=1]
[*]Make the Trackpoint work by degrading it to a standard mouse as described above:
```
echo "options psmouse proto=bare" | sudo tee /etc/modprobe.d/trackpoint.conf
```
[*]Reboot or use modprobe + rmmod to reload the "psmouse" module.
[*]Activate scrolling by doing this after booting:
```
xinput set-int-prop "PS/2 Generic Mouse" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "PS/2 Generic Mouse" "Evdev Wheel Emulation Button" 8 2
```
[*]Enjoy scrolling :-)
[/LIST]

Source: [URL="http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint"]http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint
[/URL]

---

### Post by buddyshashank on 2013-02-19
I too facing this issue from long time. I have updated kernel version and Bios version too but nothing helped me. I am really frustrated now with this model. Now i think  i have two option left as i am not getting desired output from anyone. One to buy a new laptop and second to switch to windows, which i will not love at all.

---

### Post by dantata on 2013-02-25
Anyone tried installing an older kernel?

---

### Post by lencho on 2013-04-04
> **dantata said:**
> Anyone tried installing an older kernel?

Yes, please see the appropriate post:
[http://ubuntuforums.org/showthread.php?t=2086263](http://ubuntuforums.org/showthread.php?t=2086263)

I only got the buttons working but read elsewhere that the whole thing works with kernel series 2.6.

---

