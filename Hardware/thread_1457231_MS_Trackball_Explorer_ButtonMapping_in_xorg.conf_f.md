---
title: "MS Trackball Explorer ButtonMapping in xorg.conf fails"
date: 2010-04-18
forum: Hardware
---

### Post by breaks_software on 2010-04-18
I have a "Microsoft Trackball Explorer 1.0 PS2/USB Compatible" trackball attached to my Ubuntu 9.10 (Karmic Koala) 64-bit system.  I used xuv to find the button numbers of the different buttons on my trackball, and reassigned them in xorg.conf based on the information I've found in this forum, and other web sites.  Unfortunately, the change in the mapping doesn't happen.  I can't seem to change the button mapping at all.  I've done quite a bit of searching and none of the various solutions seem to help me.  

Here is my current entry in xorg.conf:
Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "Buttons" "7"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
 Option "ButtonMapping" "1 2 8 4 5 9 7"
EndSection

I want to have button 8 (top right) activate the context menu, button 9 be the "Back" button, and I would really love to set button 3 to be a double-click (though I've found no way to accomplish this in Ubuntu at all).

Any suggestions would be most gratefully received.

---

### Post by pi/roman on 2010-04-18
You can remap the buttons for any attached mouse type device by editing the following file:
gksudo gedit .Xmodmap

Then enter the following line in, save it and it will take hold after rebooting:
pointer = 1 2 8 4 5 9 7

If you would like to just remap the buttons on your trackball then you would need to do it through xinput placed your startup commands.

---

### Post by breaks_software on 2010-04-22
Okay, I tried that with no success.

As an alternative, I tried doing this with an old Kensington Orbit Optical 2 button trackball.  Also with no success.  With the Kensington, I also tried creating a new .fdi file in /etc/hal/fdi/policy, and that didn't work either:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.product" contains="Kensington      Kensington USB/PS2 Orbit">
   <append key="input.x11_options.ButtonMapping" type="string">3 2 1</append>
   <append key="input.x11_options.Emulate3Buttons" type="string">true</append>
  </match>
 </device>
</deviceinfo>
```

This has GOT to be easier than all of this configuration *&$*!

Any other suggestions?

---

### Post by pi/roman on 2010-04-24
I normally use the solution I provided because it is simple and it works on any computer. It will work for you if it is done as i said.

The hal solution should work if it is done properly. This product, ```
Kensington      Kensington USB/PS2 Orbit
```, probably does not exist. The line should read more like:
  <match key="info.product" contains="Kensington USB/PS2 Orbit">
or to make sure to cover the Kensington device just use:
<match key="info.product" contains="Kensington">
The append key is probably unnecessary rather it should be a merge key:
   <merge key="input.x11_options.ButtonMapping" type="string">3 2 1</append>
   <merge key="input.x11_options.Emulate3Buttons" type="string">true</append>
If you use the hal configration method you must also remove your input device configuration from xorg.conf because they are conflicting.

Note that the buttons you are trying to map with your hal configuration are different than what you are trying map with your xorg.conf. Your hal configuration maps buttons "3 2 1" and you have xorg.conf set to "1 2 8 4 5 9 7".

---

### Post by pi/roman on 2010-04-24
I just noticed you have buttons 6 and 3 missing from your configuration which will nullify it. You must include these buttons even if it is at the end. So when you open .Xmodmap:
gksudo gedit .Xmodmap
add the 3 and 6 buttons to the end:
pointer = 1 2 8 4 5 9 7 3 6

---

### Post by breaks_software on 2010-05-02
Ah Ha!  That's why it works with the Kensington (3 buttons), but not the MS Trackball Explorer.  Finally getting back to this challenge, so thanks for your replies!  It should have occurred to me to just add in the extra button numbers at the end as SOMEthing else to try.  I'll check it out.

Thanks!

---

