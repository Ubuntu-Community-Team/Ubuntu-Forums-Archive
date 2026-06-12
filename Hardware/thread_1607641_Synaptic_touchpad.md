---
title: "Synaptic touchpad"
date: 2010-10-28
forum: Hardware
---

### Post by cabagekiller on 2010-10-28
Ok. I have looked up all the ways to fix my touchpad, but none seem to work. Many use older outdated things such as HAL. It was working fine earlier today, but just stopped. For the specs I have a sony vaio VGN-CS260j. Also, I know it works. I have this dual booting with windows 7. That had problems too until I reinstalled the drivers. If anyone has help I would greatly appreciate it. Thank you.

---

### Post by cabagekiller on 2010-10-28
Ok, so I used 
$cat /var/log/Xorg.0.log | grep -i synaptics 
and its output was 
[    32.425] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    32.425] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    32.425] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    32.425] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "enable synaptics SHMConfig"
[    32.425] (II) LoadModule: "synaptics"
[    32.426] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    32.426] (II) Module synaptics: vendor="X.Org Foundation"
[    32.426] (II) Synaptics touchpad driver version 1.2.99
[    32.484] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5728
[    32.484] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4548
[    32.484] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    32.484] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    32.484] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    32.520] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.520] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.536] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    32.536] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    32.536] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    32.536] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    32.536] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    32.572] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.572] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[    32.572] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    32.572] (II) Synaptics touchpad driver version 1.2.99
[    33.164] (EE) SynPS/2 Synaptics TouchPad no synaptics event device found
[    33.201] (EE) Query no Synaptics: 6003C8
[    33.201] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[    33.201] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[    33.201] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[    33.201] (II) UnloadModule: "synaptics"
[   250.176] (--) SynPS/2 Synaptics TouchPad: touchpad found
It now looks like it cannot start my touchpad. Does anyone have any solutions to this?

---

### Post by cabagekiller on 2010-10-28
shameless bump. Does anyone have any idea as to how to get this functioning again? My only other option is to buy a USB dongle mouse to use with ubuntu because for some reason my computer hates my BT mouse and will not auto connect to it.
addition. I see that the synaptic module is unloading. How can I insmod it? does anyone know the location of it?
Ok I tried tpconfig but it said "Could not open PS/2 Port [/dev/psaux]."

---

### Post by irv on 2010-10-28
First: does your pad tab show up in your System> Preferences> Mouse Preferences, and if it does what does it look like?
[ATTACH]173778[/ATTACH]

---

### Post by cabagekiller on 2010-10-28
Yes, it does. It looks exactly like yours except mine does not offer the two finger swipe.

---

### Post by irv on 2010-10-28
> **cabagekiller said:**
> Yes, it does. It looks exactly like yours except mine does not offer the two finger swipe.

I am using version 10.10. What version are you on?
Why don't you set your version in your profile under "Edit Your Details" in  the forum.
[ATTACH]173779[/ATTACH]  [ATTACH]173780[/ATTACH]

---

### Post by cabagekiller on 2010-10-28
Oh, Sorry. I am on 10.10 also. It worked fine since I installed ubuntu back when 9.10 came out, but messed up yesterday when apparently my windows partition also had the touchpad stop responding. I managed to get that working again.

---

### Post by cabagekiller on 2010-10-28
ok. Now when I ran sudo tpconfig it shows "Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode)."
I feel that my input is just not being recognized. It shows that my touchpad is here but it does not allow it to function.

---

### Post by d_hinds on 2010-10-28
> **irv said:**
> I am using version 10.10. What version are you on?
Why don't you set your version in your profile under "Edit Your Details" in  the forum.
[ATTACH]173779[/ATTACH]  [ATTACH]173780[/ATTACH]

As someone knowledgeable about Synaptic touchpads, perhaps you could tell me how to turn mine off, on a ThinkPad X100e running Ubuntu Netbook Remix.

In: System / Mouse / Touchpad "Disable TouchPad while typing" is checked but it doesn't disable.

Since I use either the Thinkpad's trackpoint or a USB mouse and sometimes hit the touchpad accidentally while typing, I'd rather have it permanently off.

Any pointers re how to do this would be appreciated.

---

### Post by irv on 2010-10-28
> **d_hinds said:**
> As someone knowledgeable about Synaptic touchpads, perhaps you could tell me how to turn mine off, on a ThinkPad X100e running Ubuntu Netbook Remix.

In: System / Mouse / Touchpad "Disable TouchPad while typing" is checked but it doesn't disable.

Since I use either the Thinkpad's trackpoint or a USB mouse and sometimes hit the touchpad accidentally while typing, I'd rather have it permanently off.

Any pointers re how to do this would be appreciated.
The only option I see is to turn it off while typing. It does not have the option to just turn it off. This must of changed because it was there a couple of versions ago.

---

### Post by d_hinds on 2010-10-28
> **irv said:**
> The only option I see is to turn it off while typing. It does not have the option to just turn it off. This must of changed because it was there a couple of versions ago.

As mentioned, "turnoff touchpad while typing" is checked but it continues to function anyway.

I have Mint LXDE Edition installed on another partition and it lets me turn off the touchpad completely.

I was hoping there was a way to turn off or install a different Synaptics driver that provides that option.

For instance: Mint LXDE uses a different File Manager but I had no trouble installing and using Nautilus.

What kept me hanging on to Windoze was my Windoze PIM which is running just fine under Wine on Ubuntu Netbook remix.  Even the Fn key commands are working well (adjusting the screen brightness, for instance). Free at last - but I really would like to turn off that Touchpad.

Thanks for taking a look.

---

### Post by irv on 2010-10-28
> **d_hinds said:**
> As mentioned, "turnoff touchpad while typing" is checked but it continues to function anyway.

I have Mint LXDE Edition installed on another partition and it lets me turn off the touchpad completely.

I was hoping there was a way to turn off or install a different Synaptics driver that provides that option.

For instance: Mint uses a different File Manager but I had no trouble installing and using Nautilus.

What kept me hanging on to Windoze was my Windoze PIM which is running just fine under Wine on Ubuntu Netbook remix.  Even the Fn key commands are working well (adjusting the screen brightress, for instance). Free at last - but I really would like to turn off that Touchpad.

Thanks for taking a look.

I would think there is a command that would turn it off and on again, but I am not aware of it. If any one know of one please post it on this thread or give a link to one if there is one. Inquiring minds would like to know?

---

### Post by d_hinds on 2010-10-29
> **irv said:**
> I would think there is a command that would turn it off and on again, but I am not aware of it. If any one know of one please post it on this thread or give a link to one if there is one. Inquiring minds would like to know?

There may be a way to inhabilitate the TouchPad from the Bios. I'll check tomorrow and will report here if successful.

(ThinkPads have their Fn Keys before the Ctrl, which has always caused me problems -this is my 3rd ThinkPad- but the X100e's Bios let me reverse their order - for example).

---

### Post by cabagekiller on 2010-10-29
Ok. This is really odd. My touchpad does not work in any LiveCD I tried. It only works in windows 7 when I uninstall all its drivers and it uses a generic one.
Now that I am looking at the Xorg log some more, it looks like it reads the touchpad then seems to scan it again but not find it. How can I force load the module?

---

