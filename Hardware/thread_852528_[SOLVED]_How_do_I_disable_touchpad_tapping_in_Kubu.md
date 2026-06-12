---
title: "[SOLVED] How do I disable touchpad tapping in Kubuntu Acer 5220 Laptop?"
date: 2008-07-07
forum: Hardware
---

### Post by Rytron on 2008-07-07
Hi,
How do I disable touchpad tapping feature in Kubuntu on my Acer 5220 laptop? Can tapping be disabled in BIOS? I notice that when I use a live cd, tapping is always on by default. I really dislike the tapping feature because when I move around, I keep accidentally selecting stuff that I didn't want.

My Kubuntu is installed to my HDD.

Any suggestions?

Thanks.

---

### Post by mavi_yelkenler on 2008-07-07
Fn + F7 ???

---

### Post by sergiom99 on 2008-07-07
Is your touchpad a Synaptics? Then install Ksynaptics, that lets you configure the way it behaves.
I tried it in GG, but I dont need it because i seldom use the touchpad and mine has a on/off button.

---

### Post by Rytron on 2008-07-10
> **mavi_yelkenler said:**
> Fn + F7 ???

That disables touchpad. I want to use touchpad but with tapping disabled.

---

### Post by mavi_yelkenler on 2008-07-11
hi Rytron,

i cannot understand what you mean because of my bad English, but have a look at this, i hope this is what you need

> Laptop Touchpad: Using a laptop? If your cursor shoots off all over the place when you type, you might want to (carefully) do the following:

gksudo gedit /etc/X11/xorg.conf

Now find the section concerning your touchpad and copy the bold text below into your conf file, so it looks similar to the example below:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
**Option "SHMConfig" "true"**
EndSection

Make sure it all looks okay and that the "EndSection" text is in the right place, then close and save. Now, navigate to System > Preferences > Sessions and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot. Why isn't it default for laptop users? Well, apparently it's insecure. If you share your laptop with others, technically they could disable your touchpad.

regards and thank you for your friend request

---

### Post by Rytron on 2008-07-16
I settled for gsynaptics.
Works a charm.

---

### Post by lp.descamps on 2008-09-18
> **sergiom99 said:**
> Is your touchpad a Synaptics? Then install Ksynaptics, that lets you configure the way it behaves.
I tried it in GG, but I dont need it because i seldom use the touchpad and mine has a on/off button.


Hi,
i've got the same option on my hp but every time i reboot the laptop my touchpad is turned off and i ve to press the switch to turn it on everytime i logon on ubuntu.

any idea?

thanks

---

### Post by cptr13 on 2008-10-01
This thread helped me...thanks to all involved.  I added the line to xorg and install gsynaptics and it works like a charm.  Thanks!!

---

### Post by Rytron on 2008-10-02
> **cptr13 said:**
> This thread helped me...thanks to all involved.  I added the line to xorg and install gsynaptics and it works like a charm.  Thanks!!

That's great to hear cptr13, this truly is an amazing and friendly community.

---

### Post by SeattleDom on 2009-10-31
Ksynaptics is discontinued, use [KCM_Toucpad]("http://kde-apps.org/content/show.php/kcm_touchpad?content=113335")

---

### Post by Rytron on 2009-11-01
Thank you SeattleDom.

---

