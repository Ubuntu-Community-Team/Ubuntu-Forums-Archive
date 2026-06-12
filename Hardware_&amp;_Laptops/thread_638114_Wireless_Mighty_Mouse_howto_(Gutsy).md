---
title: "Wireless Mighty Mouse howto (Gutsy)"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by superm1 on 2007-12-11
I recently picked up a Mighty Mouse and set it up to work properly on my Gutsy box.

There are several other threads that I used to populate this, but I figured a direct howto for Gutsy would be good for people.

First off, make sure you've got the gnome bluetooth applet installed.   It will show up as a little BT icon in your notification tray.

1) Power on your Mighty Mouse.  There is a little switch on the bottom

2) Modify the default bluetooth configuration
```
sudo gedit /etc/default/bluetooth
```

2a) ```
BLUETOOTH_ENABLED=1
```
2b) ```
HIDD_ENABLED=1
```

3) Restart bluetooth service
```
sudo /etc/init.d/bluetooth restart
```

3) From a terminal, type
```
sudo hidd --search
```3) You will be asked for a passkey by the gnome BT applet.  It is **0000**.

4) Make sure that your mouse works (basically).  As of right now the vertical scrolling and buttons 1-3 should work properly.

5) Store the mouse configuration so it is available on startup
```
sudo gedit /etc/bluetooth/hcid.conf
```

5a) Add a section to the bottom.  You will need the mac address from your hidd --search before
```

device 00:14:51:D4:08:B0 {
    name "Mighty Mouse"
    auth enable;
    encrypt enable;
}

```

6) Edit your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

6a) ADD this section:
```
Section "InputDevice"
        Identifier  "Apple Mouse"
        Driver      "evdev"
        Option     "SendCoreEvents" "true"
        Option "Name" "Apple Computer, Inc. Mighty Mouse"
        Option "HWHEELRelativeAxisButtons" "6 7"
        Option "Buttons" "8"
EndSection

```

6b) In your ServerLayout section, add this line:
```
        InputDevice    "Apple Mouse" 
```

7) Restart your X server.

8) Open up firefox and go to this address:
```
about:config
```

9) In that address, modify these values:[LIST]
[*]mousewheel.horizscroll.withnokey.action to 0
[*]mousewheel.horizscroll.withnokey.numlines to 1 (determines horizontal scrolling speed; adjust to your preference. Higher values mean faster; negative is possible to reverse direction).
[*]mousewheel.withnokey.numlines to 3 (determines scrolling speed, adjust to your preference)
[*]mousewheel.withnokey.sysnumlines to false[/LIST]This should turn on horizontal scrolling in firefox too.

-----------

Now in theory, the 8th button (squeeze) should work too, but I'm not sure about it yet.

---

### Post by electronic-man on 2008-01-01
Hello superm1

thanks for this great detailed howto - it helped my al lot !  =D>

**Today I've "reinstalled" my WirelessMightyMouse an now it works perfect**. :grin:

[SIZE="4"][COLOR="Red"]You have made a sad man very happy[/COLOR][/SIZE]

The trouble I had before:

After Gutsy was installed I could bundle the mouse via the gnome BT Applet: 

[COLOR="SlateGray"](Preferences->Services->klick to Input Service->add-Button under Input devices->passkey in Bubble etc.)[/COLOR]

- but no scrolling etc. worked. Only the left and right button plus moving the arrow - very sad.

So I edited xorg.conf with a mouse-section for cable-driven USB-MightyMouse I've found via Google - but nothing changed. 

Trough your howto  I figured out that the option "SendCoreEvents" in Xorg.conf was missing (6a) an even the HHID-entry in the bluetooth-configuration (2a) was  set to "0".


That Firefox could be modified in a way, that four-direction scrolling work is a great deal - thanks for this hint - it is "the cherry on the cake" of your HOWTO.

best regards

electronic-man

---

### Post by citybird on 2008-01-25
the sudo hidd --search command comes back with nothing every time.

the bluetooth on my phone can see my laptop but my laptop cannot find my phone or my mighty mouse.

---

### Post by superm1 on 2008-01-25
> **citybird said:**
> the sudo hidd --search command comes back with nothing every time.

the bluetooth on my phone can see my laptop but my laptop cannot find my phone or my mighty mouse.
The only solution here would be to power cycle the mighty mouse before you run the command.

---

### Post by SaiHayashi on 2008-04-27
First of all thx for writing up this guide, however I come to face the following issue.

When I tried to follow ur guide to connect the mighty mouse it works perfectly fine with click buttons working, however after i restart, both clicking buttons never worked anymore, vertical scrolling and cursor movement are still functional tho.

So how can i cure this?

Im running the new Ubuntu 8.04 on VAIO sz series.

---

### Post by superm1 on 2008-04-27
Hi:

For Ubuntu 8.04, this guide isn't entirely accurate anymore.  My mouse is semifunctional (after the upgrade), so it's a little hard to determine what pieces are still needed.

Also, after about 20 minutes of inactivity the mouse stops working.  I can see the adapter receiving stuff (it flashes blue when it gets activity), but the mouse doesn't work in X until I unplug and replug the adapter again.

---

### Post by SaiHayashi on 2008-04-27
> **superm1 said:**
> Hi:

For Ubuntu 8.04, this guide isn't entirely accurate anymore.  My mouse is semifunctional (after the upgrade), so it's a little hard to determine what pieces are still needed.

Also, after about 20 minutes of inactivity the mouse stops working.  I can see the adapter receiving stuff (it flashes blue when it gets activity), but the mouse doesn't work in X until I unplug and replug the adapter again.
i dont get why it worked the first time but not after reboot...
its gota be a nice reason behind it.

sigh...  it worked on vista =.="

---

### Post by superm1 on 2008-04-27
Okay, here's the big thing, all the hidd stuff shouldn't be done anymore.

You should be pairing directly with the little applet.

---

### Post by encompass on 2008-05-09
I am trying to setup my WIRED usb mightymouse with my hardy setup.
The xorg is slightly different to me this time around.  But I can't seem to get the side scrolling to work anymore. :(  With my weenie of a screen it would be nice to get it running again.
If I remember correctly the setup of the mightmouse in terms of the xorg.conf files is the same for wireless and wired.  Right?

---

### Post by SaiHayashi on 2008-05-11
> **superm1 said:**
> Okay, here's the big thing, all the hidd stuff shouldn't be done anymore.

You should be pairing directly with the little applet.

the default bluetooth applet pairs the mouse but wouldnt "CONNECT".



#EDIT
BIG NEWS

i installed Blueman manager and it pairs up with the MIGHTY MOUSE perfectly fine! 
i tested on 
   1. power off and on the mouse without rebooting the machine
   2. power off the mouse then off the machine, and on the machine then on the mouse.
   3. power recycle the machine without turning off the mouse.

and all test are passed!

Now since im still new to linux, i dont know the theory behind this and alternative to this, so anyone wants to step this step forward please do so.

NB. as said above Im running Ubuntu 8.04 Hardy

EDIT #2
find out that when the mouse is idle for a set period ( maybe 20mins im not sure) mighty mouse would fall asleep and would not turn back on by clicking, need to shut down the mouse and turn back on physically

---

### Post by Gonzell on 2008-05-31
Me before reading this tutorial == :confused::(:mad:

Me after reading this tutorial == :):):)

---

### Post by superm1 on 2008-06-01
Regarding the disconnect problem: take a look at this bug:[https://bugs.edge.launchpad.net/ubuntu/+source/kdebluetooth/+bug/175743](https://bugs.edge.launchpad.net/ubuntu/+source/kdebluetooth/+bug/175743)

---

