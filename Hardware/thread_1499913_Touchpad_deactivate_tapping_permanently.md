---
title: "Touchpad: deactivate tapping permanently"
date: 2010-06-02
forum: Hardware
---

### Post by Daniel_le_Rouge on 2010-06-02
Hi!

I would like to deactivate the tapping of my touchpad permanently. I tried to do the configuration with the touchpad preferences in the programme *gsynaptics*. This works only temporally. Every time I start a new session, tapping is active again.

I also tried to configure **/etc/hal/fdi/policy/11-x11-synaptics.fdi** and put in the following:

```
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
    </match>
```

SHM is activated. But it does not work. What I can I do to finally disable the tapping?

I am using Ubuntu 10.04 Lucid. I start *gsynaptics* like this **gsynaptics-init --sm-disable**. Below you will find some further information about my touchpad.

Thanks a lot for your help!

Daniel

```
daniel@daniel-laptop:~$ grep -B 5 mouse /proc/bus/input/devices 
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
--
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input8
U: Uniq=
H: Handlers=mouse1 event8 

```

---

### Post by John Bean on 2010-06-02
All I did with mine was go to System->Preferences->Mouse and uncheck the "Enable mouse clicks with touchpad" on the "Touchpad" tab.

It seems a bit simpler than your method... and it worked ;-)

---

### Post by utnubuuser on 2010-06-02
In 10.04 there is also a gpointing-device-settings package - maybe you have to add gsynaptics to your startup apps to have the settings carry-over from boot to boot.

---

### Post by Daniel_le_Rouge on 2010-06-02
@John Bean: It tried your method and worked nicely. I hope it will stay like this. Thanks a lot.

Daniel

---

### Post by ayc on 2010-06-09
Hey all,
what do you suggest to Ubuntu 10.04 users? Because there is no "Enable mouse clicks with touchpad"
checkbox in System->Preferences->Mouse.

---

### Post by John Bean on 2010-06-09
> **ayc said:**
> Hey all,
what do you suggest to Ubuntu 10.04 users? Because there is no "Enable mouse clicks with touchpad"
checkbox in System->Preferences->Mouse.

There is in mine, and the OP was also using 10.04.

---

### Post by wilee-nilee on 2010-06-09
There should also be a key combo that will disable the tap-pad if needed mine is fn-f7.

---

### Post by arma0012 on 2010-06-10
I'm trying to disable my touchpad on an acer 5735. I have disabled everything in the tocuhpad tab in system->preferences->mouse.

I have also tried disabling it using the Gsynaptic gui but that also has no effect.

I have also tried disabling it using gconf-editor in desktop/gnome/peiripherals/touchpad and deselecting touchpad_enabled, but this again has no effect.

Any suggestions greatly appreciated.

Cheers,
Sam

---

### Post by John Bean on 2010-06-11
You may be better off starting a new thread; this one is marked [SOLVED] and is likely to be ignored by a lot of people who may have answers for your problem, which is clearly different from the one in this thread.

---

### Post by laverde on 2010-08-18
@ayc and @arma0012 

It got the same problem as yours, it could be that your touchpad is not detected properly. 
Open a terminal and type 

xinput --list

Look the output, if there is no line with "TouchPad" then it could be your touchpad isn't recognized like a touchpad but like something else. In this case you will have to submit a bug report.

Check intructions in

[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

---

