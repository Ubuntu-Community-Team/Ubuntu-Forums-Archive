---
title: "Touchpad not working after installing Ubuntu 8.10 in lenovo ACQ 4152"
date: 2009-04-30
forum: Hardware
---

### Post by neenz on 2009-04-30
[FONT=Tahoma]Hey Guys,

I am very much new to Ubuntu & I tried installing the Ubuntu version 8.10 in my lenevo laptop ACQ 4152. Which has resulted in my touchpad "not working":(.. Has anybody got some solution for it? Am not at all a tech savvy.. SO u wil have to help me with the max possible details:lolflag:.... 

Am looking forward to hear from you.... 

Thanks,

**Neenz(",)**
[/FONT]

---

### Post by dtom2444 on 2009-04-30
Try this: go to System -> Preferences -> Mouse  then click on the Touchpad tab and see if the "Enable Touchpad" option is checked. 

If that is checked, you can try downloading an app called Touchfreeze which may help. This can be done by clicking on Applications and at the bottom of the list is "Add/Remove..." or System -> Administration -> Synaptic Package Manager and in both cases type in Touchfreeze to automatically download and install it.

Hope this helps.

---

### Post by neenz on 2009-04-30
Hey DTom,
Thanks for your reply...!!

I tried enabling the touchpad setteings, which didnt do any good.. Then I tried downloading the app Touchfreeze, which gave me this error "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634"

I even tried downloading VLC & AMAROK & resulted in getting errors of the same kind...

Could you help?

Thnx,

Neenz(",)

---

### Post by dtom2444 on 2009-05-03
Yea, you'll need to find the public key somewhere for Touchfreeze.

My suggestion, skip Touchfreeze (it'll take too long to find that dang key) and try this -> first make sure gsynaptics IS installed via Synaptic Package Manager. Open the manager, type gynsaptics on the search bar. if installed, the little box will be solid green. If the box is empty, double click and select "mark", then select "Apply" towards the top left.  If gsynaptics is installed, try this link:
[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

The instructions are apparently confusing for some so here are the instructions in "layman's" terms that i found on a different thread:

> Also, because the instructions are a bit confusing, here's the step by step of how I turned off that damn button tap:

1) Go to you terminal and type gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi (Note: If you don't have "gedit", replace it with whatever simple text editor you have like "mousepad")

2) Next paste in this:
Code:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>

3) Save and close your text editor and reboot. Now you can access synclient.

4) Go back to your client and type in "synclient -l" this will list all the functions of your touchpad. TapButton1 is the variable that controls the function you want to turn off. So type in:
Code:

synclient TapButton1=0

and your good to go.

This setting will be reset when you turn off your computer, so to make it permanent...

5) Go to "autostart applications" in your settings manager, add an app, name and describe it properly, and type in "synclient TapButton1=0" in the command box. (dtom2444: not sure if #5 is needed in your case.)

Hope this helps. 
or


[http://www.samlesher.com/ubuntu/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810](http://www.samlesher.com/ubuntu/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810)   (plus the links on the last comment)

Unfortunately, it looks like you might have to edit some file,something i try as much as possible to avoid doing in fear of messing things up. Or else, it could just be driver issues or, worse, hardware problems.

Hope any of this helps. Best of luck.[PHP][/PHP]

---

