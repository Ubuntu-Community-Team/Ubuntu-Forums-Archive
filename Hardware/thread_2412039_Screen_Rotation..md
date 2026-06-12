---
title: "Screen Rotation."
date: 2019-02-07
forum: Hardware
---

### Post by Mark_Ryan on 2019-02-07
Hello guy's,

I have just bought a little laptop it's a Geo Flex, it ca be used in Tent Mode, Tablet Mode etc.

It came with Windows 10 which I wiped and installed Ubuntu 18.04. I now have a lovely little laptop with three issues:-

1, This laptop has rotation sensors which are not working on Ubuntu so the screen does not auto rotate when I flip it. Does anyone know how to get these working?
2, Is there a way to get the keyboard to auto shut off when I use the tablet in Tablet Mode?
3, The Touch-pad is a little to sensitive and the left & right click do not work. Is there a way to fix this?

Thanks for any help.

Regards,

Mark.

---

### Post by TheFu on 2019-02-07
The Ubuntu Desktop Guide usually has the best answers for GUI questions:
* [https://help.ubuntu.com/](https://help.ubuntu.com/) let's you pick the specific version.
* [https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en](https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en)
*  [https://help.ubuntu.com/stable/ubuntu-help/mouse.html.en](https://help.ubuntu.com/stable/ubuntu-help/mouse.html.en) 

Assuming those links don't help, then more drastic options are possible.

I don't know much about auto-rotation.
I do know that X11 config files have a way to specify rotation, but this is not dynamic.  The specific GPU driver and commercial GPU GUI might let you do that. IDK. The manpage for xorg.conf has all the details.  Looks like the "Monitor" section is where the ```

       Option "Rotate" "rotation"
              This optional entry specifies the initial rotation of the  given
              monitor.   Valid  values  for  rotation  are  "normal",  "left",
              "right", and "inverted".  (RandR 1.2-supporting drivers only)
```
can be used. I didn't find any other reference to rotation control in the manpage.  Using the xorg.conf file would be my last choice, after researching all other options.

xrandr has a rotation and orientation options according to that manpage:```

       --rotate rotation
              Rotation can be one of 'normal', 'left', 'right' or  'inverted'.
              This  causes  the output contents to be rotated in the specified
              direction. 'right' specifies a clockwise rotation of the picture
              and 'left' specifies a counter-clockwise rotation.

       -o, --orientation rotation
              This specifies the orientation of the screen, and can be one  of
              normal, inverted, left or right.
```
I see examples in the manpage.

As for the touchpad, there is a driver for that too. The specific settings that any driver accepts is specific to that driver.  My chromebook touchpad uses the synclient program to control touchpad settings.  I believe this is fairly common, but there are lots of exceptions.  From the manpage:```

       synclient  -  commandline  utility to query and modify Synaptics driver
       options.
```  It has lots of options.  I force left-button taps into the left side. This includes 2-finger scrolling. Right-button taps only work in the lower right-hand corner.  Other people have problems using my setup, but it works perfectly for me, which is all that matters.

There are 50+ different settings that it controls.

I've seen tools that disable the touchpad while typing.  [https://askubuntu.com/questions/773595/how-can-i-disable-touchpad-while-typing-on-ubuntu-16-04-syndaemon-isnt-working](https://askubuntu.com/questions/773595/how-can-i-disable-touchpad-while-typing-on-ubuntu-16-04-syndaemon-isnt-working)

Anyways, hope this is helpful.

---

