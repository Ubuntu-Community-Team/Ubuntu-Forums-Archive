---
title: "Gnome won't let me use my mouse pad"
date: 2012-06-10
forum: Hardware
---

### Post by PizzaLover101 on 2012-06-10
I usually use a mouse when I am at home, but some times I use my mousepad, for simple things. However, whenever I use gnome now, my mouse pad stops working, but my mouse works. When I use ```
xinput list
``` 
This is what I get 
```
 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Dell Dell USB Optical Mouse             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys  
```
I have a Compaq Presario CQ61 laptop, Ubuntu 12.04

Edit: I should probably note that it works fine in the login menu, and I am booting Ubuntu 12.04 of an external HD right now with no problems

---

### Post by PizzaLover101 on 2012-06-12
After digging around, I found this
[http://askubuntu.com/questions/66907/touchpad-not-working-on-msi-u130-after-login-in]("http://askubuntu.com/questions/66907/touchpad-not-working-on-msi-u130-after-login-in")

Look for the second one down, I'll quote it here
> Installing the synaptics utility and changig settings didn't work for me. I found something that fixed it in a [comment in a Bug report][1]:

Install dconf-tools (dconf-tools in synaptic package manager or dconf Editor in the Ubuntu Software Center)

Launch it, it's called "dconf Editor" (It's in the "System" group if you use filters)

Find the setting "touchpad-enabled" in "/org/gnome/settings-daemon/peripherals/touchpad/" (See the pic below) and enable it.

Quit the editor and you're done.

Note, this did not require a restart or logout/in for me, the touchpad started working straight away.

My laptop is an MSI i7 running 64 bit Ubuntu 11.10, upgraded from a clean install of ll.04



---

