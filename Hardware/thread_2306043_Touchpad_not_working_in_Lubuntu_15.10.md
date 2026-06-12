---
title: "Touchpad not working in Lubuntu 15.10"
date: 2015-12-11
forum: Hardware
---

### Post by Rex Bouwense on 2015-12-11
I have done a new install of Lubuntu 15.10 on Dell Inspiron 14.  Unfortunately the trackpad does not work.  xinput yields the following :

> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Wireless Mouse        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; DLL06AC:00 06CB:78F1                    	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys   

I have tried to enable the touchpad with ```
xinput --enable 14
```, but it does not work.  An external wireless mouse when added is fully functional.  Any suggestions.

---

### Post by vasa1 on 2015-12-11
Hi,

Can you try this?

```
xinput list-props "AlpsPS/2 ALPS GlidePoint" | grep Capabilities
Synaptics Capabilities (308):1, 1, 1, 0, 0, 1, 0
```
but replace "AlpsPS/2 ALPS GlidePoint" with whatever you think your device is:
"SynPS/2 Synaptics TouchPad"
or
"DLL06AC:00 06CB:78F1" (though that seems a little odd and possibly suspicious).

One explanation of **Synaptics Capabilities** is here: [http://linux.die.net/man/4/synaptics](http://linux.die.net/man/4/synaptics) or in your local man page for **synaptics**.

You can also look at the output of **synclient** and see if "TouchpadOff" is **0** or **1**. Sorry I can't be of more help.

Edit: there's a longish thread about touchpad issues starting here: [https://lists.ubuntu.com/archives/lubuntu-users/2015-November/010150.html](https://lists.ubuntu.com/archives/lubuntu-users/2015-November/010150.html)

---

### Post by Rex Bouwense on 2015-12-12
Thank you for your reply vasa1.  This has never happened to me before.  TouchpadOff is at 0.

---

### Post by sudodus on 2015-12-12
Does the touchpad work when booting Lubuntu 15.10 live?

Does the touchpad work when booting Lubuntu 14.04.x LTS live in that computer?

And what about Xenial? Has something happened to the touchpad driver? In that case when did it happen?

I have not experienced that problem in the laptops of my family. And I have iso-tested Wily and now Xenial. On the contrary, I'm often turning off the touchpad to avoid actions because the palm of my hands getting too close to the touchpad :-P

---

### Post by Rex Bouwense on 2015-12-12
sudodus, the touchpad does not work with either 14.04.3 or 15.10 live.  As I have said I have never experienced this before.  I have no idea if something has happened to the touchpad driver and wouldn't begin to know where to look and what to look for if I did.

---

### Post by Rex Bouwense on 2015-12-12
Just fooling around now.  I turned off secure boot and tried to boot the two live flash drives.  Still no luck.  Out of idle curiosity I disabled UEFI and enabled legacy and booted both flash drives in turn and have an active touchpad in each case.  That is not supposed to be necessary when you are using the whole drive to install.  Not sure what is going on.

Is there any danger in installing Lubuntu in that state, secure boot off and UEFI disabled and legacy enabled?

---

### Post by sudodus on 2015-12-12
I do not understand why secure boot and UEFI can affect the touchpad. Probably a faulty UEFI/BIOS system.

If you are not forced to use UEFI (because you want to dual boot with pre-installed Windows), you are free to use BIOS/CSM/legacy boot. It should work like in old computers, I don't think UEFI really improves the performance for you, the main purpose is probably to make it easier for Microsoft to lock out other operating systems.

I have two computers, one Toshiba and one Lenovo and my children have HP laptops, where we can run linux in UEFI and BIOS mode. These computers are more than two years old, but I know that some newer computers are more difficult for linux.

---

