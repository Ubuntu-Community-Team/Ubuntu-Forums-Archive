---
title: "Disable Touchpad Tapping on Xubuntu 8.10"
date: 2008-12-09
forum: Hardware
---

### Post by Recursive Acronym on 2008-12-09
Hello. I have an eeePC 1000HD. I installed Xubuntu 8.10 on it, and I wish to disable the touchpad tap-to-click feature. Under Settings>Settings Manager>Mouse there is no touchpad tab. I edited the /etc/X11/xorg.conf file, adding the content ```
Section "InputDevice" \ Identifier "Synaptics Touchpad" \ Option "MaxTapTime" "0"
``` to it. I edited the /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi and the /etc/hal/fdi/policy/shmconfig.fdi files, adding the content ```
<merge key="input.x11_options.MaxTapTime" type="string">0</merge>
``` and ```
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
``` under ```
<match key="info.product" contains="Synaptics Touchpad">
```. After doing these edits, the tapping was not disabled and I cannot run GSynaptics because it says that SHMConfig is disabled. Please help me correct this problem.

---

### Post by Recursive Acronym on 2008-12-10
bump

---

### Post by Recursive Acronym on 2008-12-14
bump

---

### Post by eldragon on 2008-12-14
this is my /etc/hal/fdi/policy/11-synaptics.fdi file

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- SHMCONFIG PARA PODER USAR SYNAPTICS TOUCHPAD. -->
	<merge key="input.x11_options.SHMConfig" type="string">True</merge>
	<merge key="input.x11_options.vertedgescroll" type="string">true</merge>
	<merge key="input.x11_options.horizedgescroll" type="string">true</merge>


	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

hope it helps

---

### Post by Recursive Acronym on 2008-12-14
Sorry, that doesn't help. It still taps, I still can't run gsynaptics, and there is still no "Touchpad" tab. Thanks anyway.

---

### Post by Recursive Acronym on 2008-12-15
bump

---

### Post by dogrando on 2008-12-30
I just went through this exact problem. Here's how I solved it. (I'm not an expert, so I can't promise that this is the best way, but it worked for me.)

(1) Find out the value of the info.product key for your touchpad, by searching 'input.touchpad' in the output of lshal: mine was 'AlpsPS/2 ALPS GlidePoint'.
(2) Copy /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi to /etc/hal/fdi/policy/11-x11-synaptics.fdi, if you haven't already done this.
(3) Edit the new file. Find the section with a match on info.product which corresponds to the value you found in step 1: mine had contains="AlpsPS/2 ALPS". Add the following, which disables the 1-, 2-, and 3-finger taps.
```

        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>

```
(4) Restart hald, with /etc/init.d/hal restart.
(5) Restart X, with ctrl+alt+backspace. (Make sure you shut X applications down as required first, obviously.)

Good luck.

---

### Post by papparonny on 2009-01-16
thanks dogrando! it worked like a charm! :D

reposted your fix at [http://crunchbanglinux.org/forums/](http://crunchbanglinux.org/forums/)

---

### Post by Sesetamhet on 2009-01-31
Thank you! That worked for me too!

---

### Post by RavUn on 2009-04-01
Could anyone help me, this isn't saving for me.  I hate that I can click with the touchpad because I'm always clicking things when I mean to be scrolling.

Anyway, I've followed the above poster's instructions: 
> 

(1) Find out the value of the info.product key for your touchpad, by searching 'input.touchpad' in the output of lshal: mine was 'AlpsPS/2 ALPS GlidePoint'.
(2) Copy /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi to /etc/hal/fdi/policy/11-x11-synaptics.fdi, if you haven't already done this.
(3) Edit the new file. Find the section with a match on info.product which corresponds to the value you found in step 1: mine had contains="AlpsPS/2 ALPS". Add the following, which disables the 1-, 2-, and 3-finger taps.
Code:

        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>

(4) Restart hald, with /etc/init.d/hal restart.
(5) Restart X, with ctrl+alt+backspace. (Make sure you shut X applications down as required first, obviously.)

Good luck. 


However, when I restart X the settings in /etc/hal/fdi/policy/11-x11-synaptics.fdi don't save.  I've tried it twice and made sure to use "sudo gedit" to edit the file.  lshal shows:
>     info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)


And I changed "/usr/share/hal/fdi/policy/20thirdparty/11-x11-synapics.fdi"
to include: 
```

        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>

```
where it says:
```

    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>

```
So it's bascially: 
```

    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>

```


I restarted hal with /etc/init.d/hal resstart
and restart X but everything I changed in /etc/hal/fdi/policy/11-x11-synaptics.fdi changes back to "default" and is missing what I edited.  I've made sure to save the changes and checked the changes showed after resetting hal but after restarting X they seem to reset.

---

### Post by pablolie on 2010-01-23
thanks for everybody that posted in this thread. 

through a combination of the bits and pieces in this thread i was also able to disable touchpad tapping, which is a liability in Xubuntu (it makes it too easy to erase the main panel, which can not be easily reconfigured).

i run Xubuntu 8.04, and the edits to the xorg.conf and downloading gsynaptics with SPM seemed to do the trick - for all users on the machine, too. great stuff.

---

