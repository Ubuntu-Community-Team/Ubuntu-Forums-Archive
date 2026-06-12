---
title: "Touchpad Elan not working"
date: 2016-09-02
forum: Hardware
---

### Post by filippoaceto on 2016-09-02
Hi everyone.
I have an Asus f556uj with elan touchpad.
With last kernels the touchpad is recognized but won't work.
Everyone have the same issue?
In windows the touchpad work.


```
filippo@filippo-F556UJ ~ $ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Elan Touchpad                           	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB Camera                              	id=11	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]

```
 in /proc/bus/input/devices i have


```
I: Bus=0018 Vendor=04f3 Product=0005 Version=0000
N: Name="Elan Touchpad"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-6/i2c-ELAN1000:0$
U: Uniq=
H: Handlers=mouse1 event8
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=663800013000003

```


Thanks.

---

### Post by DuckHook on 2016-09-02
You may wish to try the fix described in the following links:

[http://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu](http://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu)
[http://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux](http://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux)

---

### Post by filippoaceto on 2016-09-03
> **DuckHook said:**
> You may wish to try the fix described in the following links:

[http://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu](http://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu)
[http://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux](http://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux)


Thanks,
I google before post in the forum and i've already found this solutions.
They won't work on my notebook :(

---

### Post by filippoaceto on 2016-09-06
EDIT:
My notebook have the integrated intel gpu and an nvidia 920.
When i use the integrated gpu the touchpad work!
with Nvidia Drivers not work.

---

### Post by DuckHook on 2016-09-10
> **filippoaceto said:**
> EDIT:
My notebook have the integrated intel gpu and an nvidia 920.
When i use the integrated gpu the touchpad work!
with Nvidia Drivers not work.

Try the last solution from the second link that I gave you (editing the /usr/share/X11/xorg.conf.d/50-synaptics.conf file). Make a backup copy of the file first so that you can revert to it if the edit fails. The idea would be to force a synaptic driver onto your HW. I have no idea if this will work. I have neither your HW to experiment with, nor prior knowledge working with your setup. If this won't do the trick, I'm out of ideas and afraid you will have to wait for help from others.

---

