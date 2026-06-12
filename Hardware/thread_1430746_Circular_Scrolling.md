---
title: "Circular Scrolling"
date: 2010-03-15
forum: Hardware
---

### Post by Snowingheart on 2010-03-15
I want to enable this for my laptop, but even though I've searched a bit, I can still find no way to do this.
I encountered gSynaptics, which wouldn't initialize, showing this message:

> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynapticsAnd I looked around and figured it had to do with my touchpad, thinking it was not related to synaptics.

So, the result from 'xinput list | grep "id=" ' yields:
> 
"Virtual core pointer"    id=0    [XPointer]
"Virtual core keyboard"    id=1    [XKeyboard]
"Asus Laptop extra buttons"    id=2    [XExtensionKeyboard]
"AT Translated Set 2 keyboard"    id=3    [XExtensionKeyboard]
"CKF8156"    id=4    [XExtensionKeyboard]
"Sleep Button"    id=5    [XExtensionKeyboard]
"Video Bus"    id=6    [XExtensionKeyboard]
"Power Button"    id=7    [XExtensionKeyboard]
[B]"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
"ImPS/2 Logitech Wheel Mouse"    id=9    [XExtensionPointer][/B]

Now, I've no idea if I have to config these using udev rules(in which case, I'd like appreciate some pointers as to what to name the rule, cuz that's about the only thing that wasn't clear to me), as I no longer have an etc/X11/xorg.config file, or is there any software available that can help me here...

Thanks in advance.

__[SIZE=1]____________________________________________________________________________
System specs: 
Ubuntu 9.10 (karmic)
Kernel Linux 2.6.31-19-generic
GNOME 2.28.1

*any other *necessary* info will be provided as required ^_^[/SIZE]

---

### Post by dadrc on 2010-03-15
To activate SHM for your touchpad, which is what you need to do to get gSynaptics up and running, do the following:

Open the file /etc/hal/fdi/policy/shmconfig.fdi (using vim in this example...)
```
sudo vim /etc/hal/fdi/policy/shmconfig.fdi
```and paste the following
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>
```After rebooting, you should be good to go.

---

### Post by Snowingheart on 2010-03-15
Thanks for the reply dadrc.

I just tried that, but I had no "/etc/hal/fdi/policy/shmconfig.fdi" file.
Even so, I created one, pasted the code, but still am unable to execute gSynaptics, same error msg.

Any other thoughts?

---

### Post by dadrc on 2010-03-16
That one worked for me on my Thinkpad, can't think of a reason why it shouldn't do for you, sorry.

---

