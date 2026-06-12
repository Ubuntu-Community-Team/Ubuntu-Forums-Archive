---
title: "Mouse"
date: 2010-11-13
forum: Hardware
---

### Post by sdas944 on 2010-11-13
Hi,

I installed Ubuntu 10.10 in my laptop. It installed successfully, but I am facing some issue with touch mouse in my laptop. The USB mouse working fine.
Please tell me what to do regarding this.


Souvik Das

---

### Post by matt_symes on 2010-11-13
Hi

What issues are you having? You need to be more specific.

Kind regards

---

### Post by sdas944 on 2010-11-13
Hi,

The Touch pad of my laptop is not functioning while if I connect a external USB mouse it is working fine.

Souvik

---

### Post by matt_symes on 2010-11-13
Hi

From the terminal type

xinput --list

and post the results back here

Kind regards

---

### Post by sdas944 on 2010-11-13
Hi,

souvik@souvik-Rev-1-0:~$ xinput
usage :
    xinput get-feedbacks <device name>
    xinput set-ptr-feedback <device name> <threshold> <num> <denom>
    xinput set-integer-feedback <device name> <feedback id> <value>
    xinput get-button-map <device name>
    xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
    xinput set-pointer <device name> [<x index> <y index>]
    xinput set-mode <device name> ABSOLUTE|RELATIVE
    xinput list [--short || --long] [<device name>...]
    xinput query-state <device name>
    xinput test [-proximity] <device name>
    xinput create-master <id> [<sendCore (dflt:1)>] [<enable (dflt:1)>]
    xinput remove-master <id> [Floating|AttachToMaster (dflt:Floating)] [<returnPointer>] [<returnKeyboard>]
    xinput reattach <id> <master>
    xinput float <id>
    xinput set-cp <window> <device>
    xinput test-xi2 <device>
    xinput list-props <device> [<device> ...]
    xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
    xinput set-float-prop <device> <property> <val> [<val> ...]
    xinput set-atom-prop <device> <property> <val> [<val> ...]
    xinput watch-props <device>
    xinput delete-prop <device> <property>
    xinput set-prop <device> [--type=atom|float|int] [--format=8|16|32] <property> <val> [<val> ...]
souvik@souvik-Rev-1-0:~$ ^C
souvik@souvik-Rev-1-0:~$ 


Regards,
Souvik Das

---

### Post by matt_symes on 2010-11-13
Hi

You need to type

xinput **--list**

not just 

xinput

Kind regards

---

### Post by sdas944 on 2010-11-13
Hi,

souvik@souvik-Rev-1-0:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                          id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
souvik@souvik-Rev-1-0:~$ 

Regards,
Souvik Das

---

### Post by matt_symes on 2010-11-13
Hi

Well your touchpad is recognized. 

Might be the synaptics module.

In the terminal type
cat /var/log/Xorg.0.log | grep -i synaptics

and post the results back.

There are some known bugs with synaptic touchpads.

Kind regards

---

### Post by ikonitas on 2010-11-13
hello Matt_symes

I am facing the same problem with my touchpad

I tryed : 

xinput [B]--list

[/B]```
ed@ed:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
```

than i tryed : 

cat /var/log/Xorg.0.log | **grep -i synaptics**

But , I am not getting any messages at all.

DO you know how to solve this?

---

### Post by matt_symes on 2010-11-13
Hi
> 
DO you know how to solve this?Possibly. I am trying to determine the state of your current setup.

1. Ensure you have xserver-xorg-input-synaptics package installed. You can do this from the package manager.

2. Ensure the touchpad is enabled. From the terminal type

gconftool-2 -R /desktop/gnome | grep touchpad

This will show you if it is enabled. Type

gconftool-2 -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true

to enable it if it is not. This will need a reboot after if it is not enabled.

Kind regards

---

### Post by ikonitas on 2010-11-14
i just tryed your commands :

```
ed@ed:~$ gconftool-2 -R /desktop/gnome | grep touchpad
  /desktop/gnome/peripherals/touchpad:
   touchpad_enabled = true
ed@ed:~$ gconftool-2 -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true

```

After restart still the same touchpad is not working :mad:

---

### Post by matt_symes on 2010-11-14
Hi

Silly question, but is the touchpad enabled in your BIOS?

Kind regards

---

### Post by ikonitas on 2010-11-14
Yes it is enabled touchpad in bios, few weeks ago I checked on windows live cd it was working fine

---

