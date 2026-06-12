---
title: "Enable Multi-touch for eee pc 1005ha and other non-natively Multi-touch touchpads"
date: 2010-01-19
forum: Hardware
---

### Post by bluetron on 2010-01-19
Hi,


I've just installed Kubuntu 9.10 Karmic Koala Netbook Edition on my brand new Asus Eee PC 1005HA, and was very surprised of not being able to use Multi-touch features like two-finger scrolling, two-finger rotate and pinch zoom, like advertised on the touchpad sticker. So that's how it can be done:

Ubuntu has replaced xorg.conf by hal to configure xorg drivers, so just create a new file in /etc/hal/fdi/policy:
```
kdesudo kate /etc/hal/fdi/policy/99-x11-synaptics.fdi
```Gnome users would do:
```
gsudo gedit /etc/hal/fdi/policy/99-x11-synaptics.fdi
```and paste the following lines into it:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
      <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">35</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">8</merge>
      <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
      <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
      <merge key="input.x11_options.JumpyCursorThreshold" type="string">245</merge>
      <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
      <merge key="input.x11_options.TapButton2" type="string">3</merge> <!-- right button -->
      <merge key="input.x11_options.TapButton3" type="string">2</merge> <!-- not functional -->
      <merge key="input.x11_options.FingerHigh" type="string">41</merge>
    </match>
  </device>
</deviceinfo>
```Then save, close the file, restart your computer and you're done! (Restarting is actually the last thing you would do in Linux, but doing /etc/init.d/kdm restart or "service hal restart" is apparently not sufficient)

This enables multi-touch scrolling and two-finger tapping (actually acting as clicking the right mouse button) by means of emulation. I didn't find how to emulate two-finger rotate and pinch zoom yet.

Hopefully this will work with other Ubuntu variants and other non-natively Multi-touch laptops too. Just take care of adapting EmulateTwoFingerMinZ, EmulateTwoFingerMinW, JumpyCursorThreshold and FingerHigh values to the most suitable for you. You can use
```
synclient -m 100
``````
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 35
```(or any other property/value) and
```
xinput watch-props "SynPS/2 Synaptics TouchPad"
```for this. All the information about driver options and device properties is available at: [http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html)



Greetings!

P.S.: By the way, Kubuntu Netbook edition is really nice with these features ;)

---

### Post by Nowaker on 2010-06-13
Hmmm, this doesn't work on Ubuntu 10.04. Using Asus 1005HA.

```

(1:06)[nowaker@nwkr-mini:~]% LC_ALL=en_US.UTF-8 sudo apt-get install xserver-xorg-input-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(1:07)[nowaker@nwkr-mini:~]% ls /etc/hal/fdi/policy/99-x11-synaptics.fdi 
/etc/hal/fdi/policy/99-x11-synaptics.fdi

```

---

### Post by Nowaker on 2010-06-13
Ubuntu 9.10 users use "sudo rmmod psmouse; sudo modprobe psmouse" instead of restarting.

---

### Post by moore.bryan on 2010-06-25
AFAIK, Lucid doesn't use HAL any more... so, any ideas how to get this working?

---

### Post by moore.bryan on 2010-06-30
Really? No ideas?

---

### Post by rudyd on 2010-07-19
> **moore.bryan said:**
> Really? No ideas?

Greetings!

Absolutely have no any ideas on this. 
But found this and it was working for me (on my acer notebook with ue2.7) :
[http://ubuntuforums.org/showpost.php?p=9115953&postcount=18](http://ubuntuforums.org/showpost.php?p=9115953&postcount=18)

Have found it here:
[http://ubuntuforums.org/showthread.php?t=1441300&page=2](http://ubuntuforums.org/showthread.php?t=1441300&page=2)
hope this helps.

---

### Post by moore.bryan on 2010-07-19
Thanks, rudyd, but I was more looking for the pinch-to-zoom features. Apparently, they're not implemented in the xorg yet...

---

