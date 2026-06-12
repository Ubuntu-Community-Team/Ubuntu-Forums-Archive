---
title: "Trust Wireless Tablet TB-3100 driver"
date: 2009-09-09
forum: Hardware
---

### Post by -Robert- on 2009-09-09
I am using Ubuntu for about a week now, and most things work pretty well.
The only problem is the installation of a [Trust Wireless Tablet]("http://www.trust.com/products/product.aspx?artnr=12579"). I have tried several things but it just won't work.
Although it is a Trust Tablet, Ubuntu seems to call it *Aiptek*.

I used this documentation for installing the driver: [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html) 

I started with "[COLOR=Blue]**Option 2: Building from source**[/COLOR]" and I used the latest driver version (wizardpen-0.7.0-alpha2).

Logfile step 1-6: [http://paste.ubuntu.com/268031/](http://paste.ubuntu.com/268031/)

The next step is "[COLOR=Blue]**Configuring and using your Wizardpen**[/COLOR]".

Logfile step 2: [http://paste.ubuntu.com/268033/](http://paste.ubuntu.com/268033/)

A part of the logfile from step 3: [http://paste.ubuntu.com/268037/](http://paste.ubuntu.com/268037/)

After that I created a new file with the name /etc/hal/fdi/policy/99-x11-wizardpen.fdi and I rebooted the computer.

[COLOR=Blue]**Calibrating your tablet**[/COLOR]

**1. Execute the following command: [FONT=monospace]lshal | less[/FONT]**

Result: [http://paste.ubuntu.com/268039/](http://paste.ubuntu.com/268039/)

**2. Search the section with the name of your tablet, as obtained from Step 2 in the configuration step. The line should read something like: [FONT=monospace]info.product = '[COLOR=#ff6666][Name of your tablet][/COLOR]'[/FONT]**

 - I found this: info.product = 'Aiptek'  (string)

**3. Scroll down until you find the following line: linux.device_file = '/dev/input/eventN' (N will a number)**

- That must be: linux.device_file = '/dev/input/event6'  (string)

**5. Using a terminal/console, execute the calibration program: calibrate/wizardpen-calibrate /dev/input/eventN (*Note: Subtitute /dev/input/eventN with the one obtained from Step 3)**

- I opened the terminal and typed this command: calibrate/wizardpen-calibrate /dev/input/event6

Result: [http://paste.ubuntu.com/268043/](http://paste.ubuntu.com/268043/)

**7. Edit the FDI file (/etc/hal/fdi/policy/99-x11-wizardpen.fdi) and subtitute the Top/Bottom/MaxX and Top/Bottom/MaxY values to the one obtained from the wizardpen-calibrate command**

I also did that: 

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<!-- This MUST match with the name of your tablet -->
<match key="info.product" contains="Aiptek">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.TopX" type="string">37</merge>
<merge key="input.x11_options.TopY" type="string">33</merge>
<merge key="input.x11_options.BottomX" type="string">2994</merge>
<merge key="input.x11_options.BottomY" type="string">2210</merge>
<merge key="input.x11_options.MaxX" type="string">2994</merge>
<merge key="input.x11_options.MaxY" type="string">2210</merge>
</match>
</device>
</deviceinfo>
```After I reboot my PC, the settings seem to be lost?

When I look at the *Xorg.0.log, *it seems that the tablet uses the* **evdev** *driver instead of the newly installed ***wizardpen*** driver.
I guess that's the reason why the tablet still isn't working the way it should be, but how can I change that?


A part of the Xorg.0.log:
```
(II) config/hal: Adding input device Aiptek
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Aiptek: always reports core events
(**) Aiptek: Device: "/dev/input/event6"
(II) Aiptek: Found 3 mouse buttons
(II) Aiptek: Found x and y relative axes
(II) Aiptek: Found x and y absolute axes
(II) Aiptek: Found absolute touchpad
(II) Aiptek: Found keys
(II) Aiptek: Configuring as mouse
(II) Aiptek: Configuring as keyboard
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Aiptek: xkb_rules: "evdev"
(**) Option "xkb_model" "logiclx300"
(**) Aiptek: xkb_model: "logiclx300"
(**) Option "xkb_layout" "us"
(**) Aiptek: xkb_layout: "us"
(**) Option "xkb_variant" "euro"
(**) Aiptek: xkb_variant: "euro"
(**) Option "xkb_options" "grp:alts_toggle,compose:lwin"
(**) Aiptek: xkb_options: "grp:alts_toggle,compose:lwin"
(**) Aiptek: (accel) keeping acceleration scheme 1
(**) Aiptek: (accel) filter chain progression: 2.00
(**) Aiptek: (accel) filter stage 0: 20.00 ms
(**) Aiptek: (accel) set acceleration profile 0
```I am really running out of options here, could someone help me please?

---

### Post by Favux on 2009-09-09
Hi Robert,

There are several tablet manufactures that then get their tablets rebranded.  From lshal you have an Aiptek not a wizardpen type tablet.

I think you want to go to Synaptic Package Manager and install the aiptek driver which I believe is xserver-xorg-input-aiptek 1.1.1.  Note down the driver version and other details.

Then you want to remove the wizardpen.fdi, after making a backup.  Or at least remove 'Aiptek' from the match key line.  We messed around with the aiptek.fdi on this thread:  [http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion](http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion)  Our "final" version is in post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion&page=5](http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion&page=5)  You may need to tweak a few things for your tablet.

If it works you could add your tablet name to the .fdi label line along with the Medion Md9570.

I hope this helps.

---

### Post by -Robert- on 2009-09-09
Hello Favux,

After opening Synaptic I installed **xserver-xorg-input-aiptek (1:1.1.1-1ubuntu1)**.
I removed /etc/hal/fdi/policy/99-x11-wizardpen.fdi and I rebooted the PC.
Then I made a new file (/etc/hal/fdi/policy/10-aiptek.fdi in which I copied this text (I changed nothing):

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

    <!-- Aiptek:  Medion Md9570; -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
        <merge key="input.x11_options.ZThreshold" type="string">5</merge>
        <merge key="input.x11_options.Pressure" type="string">linear</merge>
    </match>
  </device>
</deviceinfo>
```After another reboot the tablet works perfect!
The only thing that doesn't work are the twelve function keys, but that isn't a big problem.

This is a part of the *Xorg.0.log *as it looks now: [http://paste.ubuntu.com/268194/](http://paste.ubuntu.com/268194/)
I guess everything went well then?

Favux, thank you very much for bringing the solution!!! :)
I tried a lot of things before and it took me several hours, but I couldn't make it work.
Now I can finally use the tablet! 

Robert

---

### Post by Favux on 2009-09-09
Hi Robert,

Great!  Glad it worked.  You're welcome.

Your Xorg.0.log may be suggesting a few things, but I'm not sure what.  Aiptek driver documentation would be good, but I haven't really seen any.

---

