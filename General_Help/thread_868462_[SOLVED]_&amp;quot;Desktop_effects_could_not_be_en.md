---
title: "[SOLVED] &amp;quot;Desktop effects could not be enabled&amp;quot;"
date: 2008-07-23
forum: General Help
---

### Post by derrick991 on 2008-07-23
I'm on an Acer Aspire 5920 using intel GM965/GL960 graphics. any ideas?

---

### Post by northern lights on 2008-07-25
Can you run ```
compiz
```from a terminal and post the output? Thank you.

---

### Post by Flyingjester on 2008-07-25
usually this is because drivers are not installed or enabled for your video card or device.

---

### Post by uidb4056 on 2008-07-25
Look on menu System->Administration->Harware Drivers ans chech if there are restricted diver for your video card, if it's enable it, this will install the driver and you have to reboot. If after you can't enable compiz or there are no restricted drivers you can go to [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)  and download this script, run in the terminal and it give you information about the capability of your video card to run compiz.

---

### Post by derrick991 on 2008-07-28
> **northern lights said:**
> Can you run ```
compiz
```from a terminal and post the output? Thank you.

the output is:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


the output for the compiz check was this:

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
(at this point it opened the empty restricted drivers manager)

thanks for your help

---

### Post by overdrank on 2008-07-28
Hi and try reconfiguring your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with control, alt, backspace keys. Then try the compiz check again.

---

### Post by northern lights on 2008-07-28
> **Flyingjester said:**
> usually this is because drivers are not installed or enabled for your video card or device.
Which is exactly what's the case. And which is why
> **derrick991 said:**
>  Error: vesa driver in use 
your using the VESA driver.

Under > **uidb4056 said:**
> Look on menu System->Administration->Hardware Drivers you should be able to select the mesa driver.

---

### Post by derrick991 on 2008-07-28
> **overdrank said:**
> Hi and try reconfiguring your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with control, alt, backspace keys. Then try the compiz check again.

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


@ Northern Lights: The restricted drivers thing is blank

---

### Post by northern lights on 2008-07-29
> **derrick991 said:**
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[COLOR="Red"]GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge[/COLOR]. Settings from this path won't be read properly

mkey. You could run ```
sudo lshw -C display
```to reconfirm it's not the VESA driver anymore (after reconfiguring X), but the fact that the compiz (error) message has significantly shrunk and is not mentioning VESA should suffice.

The culprit as to why your compiz is not running is what I've marked in [COLOR="Red"]red[/COLOR]. Run ```
gconf-editor
```, navigate to "/apps/compiz/plugins/scale/allscreens/options/" and set the key "iniate_edge" to "Disabled".

compiz should thereafter function properly.

---

### Post by derrick991 on 2008-07-29
Thank you guys, it works perfectly now.:)

---

