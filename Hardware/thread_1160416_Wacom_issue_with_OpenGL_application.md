---
title: "Wacom issue with OpenGL application"
date: 2009-05-15
forum: Hardware
---

### Post by vmur on 2009-05-15
Hi,

I have a wacom table, and the new hot-plugging system in ubuntu 9.04 is great.

But, me and others guys are having problems with a OpenGL application and the new wacom system.

The application is Houdini, a 3D software, and this is the thread at SideFX forums,
[http://www.sidefx.com/index.php?option=com_forum&Itemid=172&page=viewtopic&t=15725](http://www.sidefx.com/index.php?option=com_forum&Itemid=172&page=viewtopic&t=15725)

The application don't respond to wacom clicks, if I unplug the wacom, all is nice and if I use the mouse 
the application works. But if I plug the wacom, the application don't respond to wacom/mouse inputs again.

I don't know if others OpenGL programs has the same issue.

Another trail, If I run another instance of the application, only one is freeze to wacom interaction.

Thanks and ... some info for this issue ?




Specs: (all 64 bits)

Ubuntu 9.04 
Wacom Bamboo
Nvidia 180.53 driver version

---

### Post by Favux on 2009-05-15
Hi vmur,

Welcome to Ubuntu!

I'm not sure I quite follow you regarding the problem.  Are you saying otherwise your Wacom tablet works?  Anyway while it could be a problem with Wacom and/or OpenGL and/or Xserver 1.6 you seem to be saying Houdini accepts Wacom input.  The Wacom mouse in other words.

My bet is the names HAL is returning from the info callout in the default 10-wacom.fdi file included in Jaunty is not recognized by Houdini.  You can see this by typing in a terminal:
```
xsetwacom list
```
that should return the Wacom input devices like stylus, eraser, cursor, and pad.  My bet is it is empty.  To see the names HAL is using try:
```
xinput --list
```
There are several ways to go if this is the problem.  Since you have an Bambooo maybe the simplest is changing the .fdi to a .fdi that correctly parses the HAL names so linuxwacom and Houdini understands them.  For the new .fdi see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

I hope this helps.

---

### Post by vmur on 2009-05-16
> **Favux said:**
> Hi vmur,

Welcome to Ubuntu!

I'm not sure I quite follow you regarding the problem.  Are you saying otherwise your Wacom tablet works?  


Yes, my table works like a charm, but not with this application.


> **Favux said:**
> 
Anyway while it could be a problem with Wacom and/or OpenGL and/or Xserver 1.6 you seem to be saying Houdini accepts Wacom input.  The Wacom mouse in other words.


Houdini don't respond to wacom inputs. 


> **Favux said:**
> 
My bet is the names HAL is returning from the info callout in the default 10-wacom.fdi file included in Jaunty is not recognized by Houdini.  You can see this by typing in a terminal:
```
xsetwacom list
```that should return the Wacom input devices like stylus, eraser, cursor, and pad.  
My bet is it is empty.


Yes, it's empty.


> **Favux said:**
> 
To see the names HAL is using try:
```
xinput --list
```

```

"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Logitech USB Receiver"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Logitech USB Receiver"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom Bamboo"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Bamboo pad"    id=5    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 4 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 71
        Resolution is 1
"Wacom Bamboo cursor"    id=6    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Bamboo eraser"    id=7    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

```> **Favux said:**
> 
There are several ways to go if this is the problem.  Since you have an Bambooo maybe the simplest is changing the .fdi to a .fdi that correctly parses the HAL names so linuxwacom and Houdini understands them.  For the new .fdi see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

I hope this helps.

My **/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi**

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
      <match key="info.product" contains="WALTOP">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>

</deviceinfo>

```

Thanks Favux for your prompt response, I continue with the investigation.
I will see that post.

---

### Post by vmur on 2009-05-16
I have used your  	**[Favux_Jaunty ext graphics_test 2_10-wacom.fdi.txt]("http://ubuntuforums.org/attachment.php?attachmentid=112835&d=1241728139")** and now I get

```

stylus           stylus    
pad              pad       
cursor           cursor    
eraser           eraser    

```

from **xsetwacom list** command. And **wacomcpl** works too. Thanks.

But don't work to fix the OpenGL problem.

---

### Post by Favux on 2009-05-16
Hi vmur,

Well at least wacomcpl works on your Bamboo now and you can calibrate and configure it.

Do you still think Wacom has anything to do with your problems with Houdini?

You've now removed any Wacom entries you may have had in xorg.conf?

Nvidia 180.29 display driver for Linux also fixes the following issues:  Fixed a stability issue for OpenGL programs that used FSAA.  Does Houdini use FSAA?  Maybe it isn't as fixed as they think?  From here:  [http://news.softpedia.com/news/New-Nvidia-Video-Drivers-for-Linux-Bring-OpenGL-3-0-Support-104336.shtml](http://news.softpedia.com/news/New-Nvidia-Video-Drivers-for-Linux-Bring-OpenGL-3-0-Support-104336.shtml)

Does Houdini use OpenGL 3.1?  Because nVidia released OpenGL 3.1 Beta drivers:  [http://www.tweaktown.com/news/12104/nvidia_releases_opengl_3_1_beta_drivers/index.html](http://www.tweaktown.com/news/12104/nvidia_releases_opengl_3_1_beta_drivers/index.html)  It lists the cards supported.  And you probably already have the OpenGL site:  [http://www.opengl.org/](http://www.opengl.org/)

Hope this helps.

---

### Post by vmur on 2009-05-17
Thanks Favux for your interest.


> **Favux said:**
> Hi vmur,

Well at least wacomcpl works on your Bamboo now and you can calibrate and configure it.

Nvidia 180.29 display driver for Linux also fixes the following issues: Fixed a stability issue for OpenGL programs that used FSAA. Does Houdini use FSAA? Maybe it isn't as fixed as they think? From here: [http://news.softpedia.com/news/New-Nvidia-Video-Drivers-for-Linux-Bring-OpenGL-3-0-Support-104336.shtml](http://news.softpedia.com/news/New-Nvidia-Video-Drivers-for-Linux-Bring-OpenGL-3-0-Support-104336.shtml)

Does Houdini use OpenGL 3.1?  Because nVidia released OpenGL 3.1 Beta drivers:  [http://www.tweaktown.com/news/12104/nvidia_releases_opengl_3_1_beta_drivers/index.html](http://www.tweaktown.com/news/12104/nvidia_releases_opengl_3_1_beta_drivers/index.html)  It lists the cards supported.  And you probably already have the OpenGL site:  [http://www.opengl.org/](http://www.opengl.org/)

Do you still think Wacom has anything to do with your problems with Houdini?


With wacom connected Houdini don't respond to clicks ... from wacom or Logitech mouse. 
If I unplug the wacom, I can use the mouse to interact with Houdini, all works ok.

> **Favux said:**
> 
You've now removed any Wacom entries you may have had in xorg.conf?


Yes
```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```It seems that the new hotplugging system in Ubuntu 9.04 isn't the problems.
I have used:

```

Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection

```to configure manually the wacom, all work again without hotplug, but no luck with this program.

This program works like a charm in others ubuntu versions with same Nvidia drivers.

I will continue investigating ... 


A new thing in this is when I open a second houdini ("not closing the first"), the second instance works perfectly!

---

### Post by Favux on 2009-05-17
Hi vmur,

> A new thing in this is when I open a second houdini ("not closing the first"), the second instance works perfectly! 
Interesting.  That now sounds like Houdini has a configuration file somewhere that is not telling it how to handle usb input devices correctly.

---

### Post by vmur on 2009-05-23
Definitively isn't a Ubuntu/Wacom problem.

Favux thanks for your support.

---

