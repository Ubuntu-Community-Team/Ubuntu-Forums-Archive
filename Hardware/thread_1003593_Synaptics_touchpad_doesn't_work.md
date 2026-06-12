---
title: "Synaptics touchpad doesn't work"
date: 2008-12-06
forum: Hardware
---

### Post by Fzang on 2008-12-06
I tried to install the synaptics touchpad configs and when I start it I get this error message

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

What do I do?

---

### Post by spawn. on 2008-12-06
Locate your 'xorg.conf' file and set 'SHMConfig' to 'true'

Type xorg.conf in the search box, then open as root (administrator); then scroll until you find SHMConfig and set to 'true' and SAVE.

E.G. let's say you find the file using the search method (on your local drive), but you cannot open as root (administrator) to make any changes, here's what you do:

Open Terminal
type 'gksudo nautilus' *This will open a new window of your files as root (administrator)

---

### Post by Fzang on 2008-12-06
There's no SHMConfig section in x.org, what do I do? Create it somewhere?

---

### Post by spawn. on 2008-12-06
If you decide to -add a section in to the configuration file-, I would recommend backing up the original first. You might have better luck if you added more repositories to your sources. That way, you can have more options for software in synaptic package manager.

What kind of computer do you have? I was able to find synaptic touchpad software for a complicated ThinkPad, no editing of any files. There may be another option if you are using a standard touchpad...?

---

### Post by Fzang on 2008-12-06
I have a Zepto Nexus (which you've probably never heard about) with a synaptics touchpad

---

### Post by spawn. on 2008-12-06
lol, you're right. I had to look it up. Did you install any synaptic software yet from Synaptic Package Manager?

---

### Post by anubhavrocks on 2008-12-06
Can you try 

```
 gnome-mouse-properties
```
also you can try xinput

> **Fzang said:**
> I tried to install the synaptics touchpad configs and when I start it I get this error message

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

What do I do?

---

### Post by Fzang on 2008-12-06
It says I have the drivers installed but I just can't configure them because of this odd X problem...

---

### Post by Fzang on 2008-12-06
Bump! What to do? Can I add the missing entry somehow?

---

### Post by anubhavrocks on 2008-12-12
> **Fzang said:**
> Bump! What to do? Can I add the missing entry somehow?

Can you provide the output of 

 ```
xinput  --list
```

---

### Post by Nepherte on 2008-12-12
Open your /etc/X11/xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```
and find the section that looks like:
```
Section "InputDevice"
   ...
   Identifier  "SynapticsTouchpad"
   Driver      "synaptics"
   ...
EndSection
```
The Identifier might be different, but make sure Driver is the same. Then add SHMConfig "True" to it:
```
Section "InputDevice"
   ...
   Identifier  "SynapticsTouchpad"
   Driver      "synaptics"
   **Option      "SHMConfig" "True"**
   ...
EndSection
```
Now you have to logout and login again.

---

