---
title: "TV out- Radeon XPRESS 200M 5955 (PCIE)"
date: 2008-12-07
forum: Hardware
---

### Post by chris.arney on 2008-12-07
I've got a Presario M2000 with a Radeon XPRESS 200M 5955 (PCIE). I've read through several forums talking about getting video out working, but I can't seem to get it right. I'd really like to get this laptop working with XBMC or Boxee on my TV, so I want to mirror the laptop display on TV out. I thought I knew a little bit, but apparently I'm a linux newb.

I was running Xubuntu 8.04, and played around with displayconfig-gtk, envy, and a couple of other things. I then upgraded to 8.10. I've tried a couple of things, but I really don't know what I'm doing here. "sudo atitvout -detect" and it outputs "CRT is attached." I tried "atitvout -f t", and says "Forcing Rage Mobility/Rage 3D Pro LT mode", but nothing happens.

I have gotten it to change resolution of the laptop display when I reboot with the TV out plugged in, but nothing happened on the TV. It didn't flicker or anything. I unplugged it, rebooted, and the resolution was back to normal.

I don't know what I'm doing... Please help.

---

### Post by chris.arney on 2008-12-10
Any suggestions?

---

### Post by asiersar on 2008-12-25
I have TV out with a 200m using the free radeon driver.

```
sudo apt-get install xserver-xorg-video-radeon
```


And then:

```
sudo gedit /etc/X11/xorg.conf
```

Add this to your Device section:

```
Section "Device"
	Identifier	"Xpress 200m"
	Driver		"radeon"
	Option		"ForceTVOut" "on"
EndSection
```

PD: I had TV out using the fglrx driver too. You can install it using the Restricted Drivers option in System>>Administration

---

