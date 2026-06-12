---
title: "TouchPad enable/disable problem"
date: 2010-04-18
forum: Hardware
---

### Post by Techer on 2010-04-18
Hi fellow Ubuntians,

I am dual-booting Ubuntu 10.04 and Win7 on my laptop, and there are no disappointments except  a problem I have with my touchpad: it has a button which disables it --  it works in Ubuntu as well but it seems it only detects *changes*  of the button's state rather than checking the actual state  (enabled/disabled), so if I boot into Ubuntu, disable the touchpad,  reboot into Win7, enable the touchpad, then boot into Ubuntu again,  Ubuntu still thinks it is disabled and when I press the button  (enable/disable) Ubuntu switches to the other state (enable=disable;  disable=enable).
So if this happens I will not be able to use my touchpad at all until I  boot Win7 and switch state again (both Ubuntu and the touchpad unit  itself practically disables the touchpad so it is disabled if either is  disabled).

Is there a way I can make Ubuntu check the state, or a method I can use  to change Ubuntu's touchpad enable state?

Thanks in advance, Techer

Update: Bump!

---

### Post by epitaph123 on 2010-04-30
Same here,

Dual boot Vista SP2 & Ubuntu 10.04

If the touchpad is disabled in Vista, when i reboot into Ubuntu it does not recognize that windows has it disabled. So if i hit Fn+F7 to enable it, it shows disabling touchpad when it is already disabled and hitting Fn+F7 again shows re-enabling it but it still doesn't work until i reboot into vista and enable it there.

So if the touchpad is enabled in Vista and i reboot into Ubuntu the touchpad works fine, i am able to enable/disable perfectly. But if its disabled in Vista then Ubuntu can't enable or disable it at all.

This didn't happen in any other version of Ubuntu, only in 10.04.

---

### Post by epitaph123 on 2010-04-30
Does anyone know how to make Ubuntu 10.04 recognize that Vista has the touchpad disabled?

---

### Post by StolenPie on 2010-04-30
could be related to the fact that touchpads in general seem to be not detected in 10.04...
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

---

### Post by Techer on 2010-05-21
<span style="text-decoration:line-through">
I have digested the problem and come down to a simple temporary workaround:

In terminal:
```
~$ echo gconf-editor /desktop/gnome/peripherals/touchpad/touchpad_enabled > gconf_touchpad_enabled
~$ chmod +x gconf_touchpad_enabled
~$ sudo mv gconf_touchpad_enabled /usr/bin/
```Then you go to (in the menu):
System->Preferences->Keyboard Shortcuts::
    [Add]:: (ignore the double quotes)
        Name="Go to touchpad_enabled in gconf-editor"
        Command="gconf_touchpad_enabled"
    [Apply]
And set a shortcut for your new command.
Then when you use the shortcut, and the gconf-editor appears, you just press [tab][tab][space][space] and your touchpad will be working :guitar:
Hope that works for ya!
</span>

[SIZE=5]***EDIT: Please see roger_1960's solution instead!***[/SIZE]

---

### Post by roger_1960 on 2010-05-21
Hi

I installed gpointing-device-settings from synaptic, created a launcher to it and found that it allows me to turn the touchpad on and off.

---

### Post by Techer on 2010-05-21
> **roger_1960 said:**
> Hi

I installed gpointing-device-settings from synaptic, created a launcher  to it and found that it allows me to turn the touchpad on and  off.

OK your solution beats mine :(
I'll edit mine to point to yours.

---

### Post by spike_naples on 2010-06-27
Hi guys, I was wondering about this problem. I happened to turn my touchpad off from the BIOS but now that I want to turn it on again from there I am unable to. I tried following the directions posted here but it still doesn't work. 

Hope someone could help me. Thanks in advance.

---

### Post by wilee-nilee on 2010-06-27
> **spike_naples said:**
> Hi guys, I was wondering about this problem. I happened to turn my touchpad off from the BIOS but now that I want to turn it on again from there I am unable to. i tried following the directions posted here but it still doesn't work. 

Hope someone could help me. Thanks in advance.

Your saving the change in bios I assume. What is the computer model?

---

### Post by spike_naples on 2010-06-27
Toshiba Satellite A355D-S6889.
AMD Turion X2

---

### Post by BRTPOB on 2010-06-28
I installed the software and when I run it through the console, I get:

** (gpointing-device-settings:2296): CRITICAL **: gpds_ui_new: assertion `module != NULL' failed

** (gpointing-device-settings:2296): CRITICAL **: gpds_ui_is_available: assertion `GPDS_IS_UI(ui)' failed

(gpointing-device-settings:2296): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Anyone else having that issue?

---

### Post by coolwanglu on 2010-08-30
Thanks for the workaround, it saved me.
And I suggest a better one

```

gconftool-2 -t bool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled "True"

```


> **Techer said:**
> <span style="text-decoration:line-through">nks
I have digested the problem and come down to a simple temporary workaround:

In terminal:
```
~$ echo gconf-editor /desktop/gnome/peripherals/touchpad/touchpad_enabled > gconf_touchpad_enabled
~$ chmod +x gconf_touchpad_enabled
~$ sudo mv gconf_touchpad_enabled /usr/bin/
```Then you go to (in the menu):
System->Preferences->Keyboard Shortcuts::
    [Add]:: (ignore the double quotes)
        Name="Go to touchpad_enabled in gconf-editor"
        Command="gconf_touchpad_enabled"
    [Apply]
And set a shortcut for your new command.
Then when you use the shortcut, and the gconf-editor appears, you just press [tab][tab][space][space] and your touchpad will be working :guitar:
Hope that works for ya!
</span>

[SIZE=5]***EDIT: Please see roger_1960's solution instead!***[/SIZE]

---

