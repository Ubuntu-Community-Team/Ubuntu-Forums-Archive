---
title: "Turning off hybrid graphics on a DV7"
date: 2012-01-30
forum: Hardware
---

### Post by biodiesel-bri on 2012-01-30
I have an HP dv7-6b78us with hybrid graphics - an ATI Radeon and an Intel graphics card.  They're both on by default and the Intel is more than enough power for my use.  Here's how I managed to turn off the Radeon and save massive battery life:

First, make sure you've uninstalled any proprietary graphics drivers.  There's a proprietary driver thingy in the administrative menu for that.

Next, add these to /etc/rc.local above the 'exit 0' line (e.g. sudo nano /etc/rc.local from the terminal):
```

modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

And then add this to /etc/modprobe.d/blacklist-local.conf, also as sudo:
```
blacklist fglrx
```

Reboot.  Verify by doing the following:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch

```

You should see something like this:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```

IGD is the Intel chip, the + means it's the one in use, and Pwr means it's on.  DIS is the ATI card and if it says Off, you're saving a ton of battery.

This is a permanent fix that lasts across reboots.

---

### Post by jonnyboysmithy on 2012-03-04
Thank you SOO much!! This solves the fan on always and short battery life issue. 
Again, thankyou!!

By the way, If your system can't find vgaswitchroo its probably because you have the proprietary drivers installed. I can't confirm but I have a suspicion it is.

---

### Post by frohfroh on 2012-05-01
I'd been using this method to great success until I updated to 12.04 and it stopped working, that is to say the laptop is overheating and the verification suggested confirms that both are powered.
Does anyone have any ideas?

---

### Post by zimbico on 2012-11-06
This just worked great for me on my HP Pavillion dv7-6b01tx running Ubuntu 12.10 =D
Thanks!
I'm yet to figure out how to switch between the GPUs though.. =P

---

### Post by varunRox123 on 2012-11-29
how to check whether the proprietary drivers are installed and are in use?
im a little new to ubuntu..
help would be appreciated :)

---

### Post by markackerman8@gmail.com on 2012-12-18
If anyone has had any luck with the use of fglrx and HP's Envy series of laptops please tell me how you did it- 13 months and still no luck, except with the open source default driver and Kubuntu which at least for the past month has decent functionality, but still leaves me dual booting into windows for gaming.

Please and Thanks , Mark
[email]markackerman8@gmail.com[/email]
hp envy 17-2195 Intel HD3000/ AMD ATI Radeon 6850m

---

