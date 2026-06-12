---
title: "Aiptek, Gimp and HAL frustration"
date: 2009-10-12
forum: Hardware
---

### Post by Alexis Phoenix on 2009-10-12
Does anyone know how to disable xorg from using HAL for it's input device configuration?  Only as far as I can see this is the only way I will be able to make my Aiptek 8000u graphics tablet work properly (or as nearly properly as it did work) again.  Or someone might be able to enlighten me as to the Way Of HAL.

A bit of background information.

Tablet worked mostly fine with Intrepid Ibex.  It had a pen, a mouse and an *emulated* eraser.  I have now upgraded to Jaunty Jackalope, using the same 2.6.29.4 kernel I was using with Intrepid.  After discovering the tablet no longer worked, I found all the commented out entries in my xorg.conf, and found out about the file /etc/hal/fdi/policy/10-aiptek.fdi, the contents of which are:```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_identifier" type="string">Pen</merge>
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.zThreshold" type="string">"1"</merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
      <merge key="input.x11_options.zMax" type="string">511</merge>
      <merge key="input.x11_options.xTop" type="string">0</merge>
      <merge key="input.x11_options.yTop" type="string">0</merge>
      <merge key="input.x11_options.xBottom" type="string">1024</merge>
      <merge key="input.x11_options.yBottom" type="string">768</merge>
      <merge key="input.x11_options.KeepShape" type="string">On</merge>

    </match>
  </device>
</deviceinfo>
```

Here's my lshal output for the tablet:```
lshal -u usb_device_8ca_10_noserial_if0_logicaldev_input
udi = '/org/freedesktop/Hal/devices/usb_device_8ca_10_noserial_if0_logicaldev_input'
  access_control.file = '/dev/input/event11'  (string)
  access_control.type = 'mouse'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard', 'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.keys', 'input.mouse', 'input.tablet', 'button', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8ca_10_noserial_if0'  (string)
  info.product = 'Aiptek'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8ca_10_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_8ca_10_noserial_if0'  (string)
  input.product = 'Aiptek'  (string)
  input.x11_driver = 'aiptek'  (string)
  input.x11_identifier = 'Pen'  (string)
  input.x11_options.KeepShape = 'On'  (string)
  input.x11_options.Mode = 'absolute'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.Type = 'stylus'  (string)
  input.x11_options.USB = 'On'  (string)
  input.x11_options.xBottom = '1024'  (string)
  input.x11_options.xTop = '0'  (string)
  input.x11_options.yBottom = '768'  (string)
  input.x11_options.yTop = '0'  (string)
  input.x11_options.zMax = '511'  (string)
  input.x11_options.zMin = '0'  (string)
  input.x11_options.zThreshold = '"1"'  (string)
  input.xkb.layout = 'gb'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input11/event11'  (string)
```

I had tried putting in the identifier and x and y coordinate info to try to resolve my Gimp problems, which works since I have rebooted the computer, which annoys the stuffing out of me, since this is Linux and rebooting is heresy!.

Problem number 1
Buttons on pen don't work.  Pressing the point of the pen to click is okay, but sometimes I need to right click.
Problem number 2 (solved?)
When using the Gimp with extended tool options enabled to get pressure sensitivity, the cursor would move around as expected, but the indicated position of the drawing tool (as per the little black arrows on the rulers) would be in the top left of the screen.  Violent movements would produce some lines indicating pressure sensitivity working.  [COLOR="Red"]Apparent Solution[/COLOR]  Insert the x and y coordinate lines into the fdi file.  I don't know why this works.  I'm not even sure of the tablet's resolution anymore, so just used numbers that looked sane.
Problem number 3
There does not appear to be a way to define the mouse and eraser devices (defining the eraser is less important since it is emulated, though according to [http://aiptektablet.sourceforge.net/xserver.html]("http://aiptektablet.sourceforge.net/xserver.html") gtk expects it).  The mouse moves the cursor around but the buttons are mixed up.  I'm pretty sure I need to be able to give it a name in order to sort out the buttons.  I inserted the identifier line into the fdi file as a possible way to resolve this, but it doesn't appear to be recognised.

HAL is a great idea, but there doesn't seem to be any documentation as to how to use it to configure X11!

---

### Post by Favux on 2009-10-12
Hi Alexis Phoenix,

Although it looks like a different Aiptek tablet we came up with a aiptek.fdi in post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion&page=5](http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion&page=5)  We play with the buttons in the thread.

The freedesktop servers seem to be down so I can't link you to the HAL 0.5.* Specifications right now.

Edit:  Here's the 5.10 spec. anyway:  [http://www.marcuscom.com/hal-spec/hal-spec.html](http://www.marcuscom.com/hal-spec/hal-spec.html)

---

### Post by Alexis Phoenix on 2009-10-26
Hi Favux

Thanks for your response.  I've been having a bit more of a play with the tablet, 10-aiptek.fdi, xinput and xev, and still no luck.  I've noticed when the buttons on the pen are pressed, it stops the timer on xev, and the light on the tablet flashes, in ```
xinput query-state Aiptek
``` the only value that changes is Proximity=In to Proximity=Out, however the state of button[number] doesn't change.

I added these lines to 10-aiptek.fdi```
      <merge key="input.x11_options.Button2" type="string">2</merge>
      <merge key="input.x11_options.Button3" type="string">3 </merge>
```I also added the line ```
<merge key="input.x11_options.ButtonMapping" type="string">1 2 </merge>

```which has been used sucessfully for a multibutton mouse ([http://www.alanbriolat.co.uk/2009/06/mouse-button-remapping-with-hal/]("http://www.alanbriolat.co.uk/2009/06/mouse-button-remapping-with-hal/"))

Apart from stopping the timer, and the in/out thing, it's as if the two buttons don't exist.  The tablet's 16 "F keys" also no longer work.  I wonder if there is a HAL way to map them (xinput query-state lists 32 "keys" which don't do anything, I wonder if those correspond to the F keys?).  I tried the tablet on windows 7, and interestingly the pen's two buttons don't work there too.  It looks like win7 is catching up with Linux there as well as in other areas...  This is all the more frustrating since the everything worked before.  Grrrrrr....

---

### Post by Favux on 2009-10-27
Hi Alexis Phoenix,

Well first thing is if the stylus requires a battery I'd check if you need a fresh one.

The string in your button mapping looks to truncated to me.  Didn't the thread I referred you to have a command to query Xinput for the button map?

The conclusion I think we came to was that the Aiptek driver prevented button mapping through Xinput.  It had 'grabbed' the stylus so the driver needs code to support the stylus buttons.  It may be in there but isn't compatible with the Xserver in Jaunty.  As I remember it supports one stylus button.

Did the 16 "F keys" work in Intrepid?  With the Wacom driver there is some code called hal-setup-wacom.  It allows you to make a info.callout in the .fdi and append sub-devices like pad (tablet) buttons.  Again it looks like somebody needs to go through the driver and write some new code to update it.

Anyway these are my guesses as to what's going on.

---

### Post by Alexis Phoenix on 2009-10-28
Whew!  What a quick reply!

Well, the stylus had a new battery recently, so it's not that.  Xinput reports 5 buttons, and the tip of the stylus corresponds to button 1, according to xinput query-state Aiptek.  Changing the button mapping line in the fdi file didn't make any difference.  The 16 "F keys" did work in Hardy Heron (I didn't use Intrepid), even though I didn't actually use them.

I'll have to look into this info.callout and see if I can write one.  I tried adding ```
<merge key="info.product" type="string">stylus</merge>
```but it hasn't made any difference.

I still can't see a way to create separate devices for the stylus, emulated eraser, and mouse (though the mouse works ok anyhow, apart from the button mapping, which is fixable).

Well, anyway, apart from that it looks like I will have to wait for someone to update the driver.

Many thanks for all your help, Favux.  If I make any progress I'll be sure to post my results.

Cheers,
Alexis

---

### Post by hva on 2010-05-02
I'm experiencing exactly the same problems since upgrading from hardy to lucid. this is really annoying as it worked like a charm on hardy and it's totally useless in lucid, and I need it for my everyday work.
I reported a bug in launchpad, but it seems aiptek driver is more or less unmaintained

---

### Post by hva on 2010-05-03
hi Alexis, if you're on Ubuntu Lucid I think I have more or less solved a part of the problem.
see here:
[http://ubuntuforums.org/showthread.php?t=122735&page=14&highlight=aiptek](http://ubuntuforums.org/showthread.php?t=122735&page=14&highlight=aiptek)

---

