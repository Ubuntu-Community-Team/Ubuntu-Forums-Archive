---
title: "Asus K56ca touchpad doesn't work"
date: 2013-04-03
forum: Hardware
---

### Post by Shipoopi on 2013-04-03
Hi i recently installed ubuntu on my Asus K56CA notebook and the right touchpad key didn't work.
I googled this problem and tried this in the terminal:

```
sudo modprobe -r psmouse && sudo modprobe psmouse
```

But now my touchpad doesn't work at all.

When i use xinput in the terminal i don't think my touchpad is even listed:

 ```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB Camera                              	id=10	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
```

All help is appreciated.

---

### Post by UltimateCat on 2013-04-03
Hi:

From the cmd that you ran "xinput list"
I don't even see your touchpad  or the word touchpad mentioned -- That's odd--
I compared it with article to understand and compare your issue with this other Asus owner--

[http://askubuntu.com/questions/82740/help-configuring-synaptics-touchpad](http://askubuntu.com/questions/82740/help-configuring-synaptics-touchpad)

I would look in this file:

> 
cat /usr/share/X11/xorg.conf.d/50-synaptics.conf
Look at this file too and see what's going on-

> /usr/share/X11/xorg.conf.d/50-synaptics.conf:

And see if the 

Identifier "touchpad catchall" is mentioned or commented out-


IF this is a driver issue these instructions and webpage may prove useful:

The Elantech touchpad is found amongst others in MSI laptops and the Asus EeePC 9xx and 1xxx. This driver adds support to the Linux kernel so the touchpad can be used with the Xorg Synaptics driver-It's a tar.gz.

[http://arjan.opmeer.net/elantech/](http://arjan.opmeer.net/elantech/)


 I'm not the expert on this. HTH
.;)

---

