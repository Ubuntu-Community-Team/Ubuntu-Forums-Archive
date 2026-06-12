---
title: "Compiz Desktop Cube - Stay zoomed while I press ctrl+alt"
date: 2008-10-08
forum: General Help
---

### Post by madiyaan on 2008-10-08
Hello:

I don't use the mouse that much, so I would like the desktop cube to stay zoomed out even when I don't click with the mouse.

So as long as I press ctrl+alt, the desktop cube should stay zoomed out without me having to hold the mouse button down. This behavior will be consistent with the behavior when I use alt+tab (at first I press alt and nothing shows up, then I press tab and the window switcher shows up, now if I lift my finger off the tab and keep pressing alt, the window switcher stays and keeps showing), and when I use super+tab (when I press super, nothing shows, but when I press tab the 3D window switcher shows and as long as I have super pressed, the switcher remains).

Can anyone tell me how to do this? At first when I should press alt+ctrl, nothing should show up. When I press an arrow with ctrl+alt, the cube should show up and stay zoomed out as a cube unless I lift the fingers off of ctrl+alt. To me this is much more intuitive and better eye-candy too. :)

Thanks,

---

### Post by madiyaan on 2008-10-10
Quick bump. Does anyone know how to do this?

---

### Post by madiyaan on 2008-10-14
Another bump. Anyone?

---

### Post by Wickd on 2008-10-14
just a question out of curiosity... Why do you need to be able to do that?

Chz

---

### Post by semitone36 on 2008-10-14
I know how to do this! I think...

Try going into compiz, clicking on the cube desktop, and somewhere under one of the tabs you will find a list of button combinations that operate the cube.  One of them should have "ctrl+alt+mouseclick" as the button combination.  If you edit that to just "ctrl+alt" you should get the desired effect.  

The only problem you may have is you might have to edit some of the other button combos because "ctrl+alt" might already be in use by another feature in compiz.

---

### Post by amylase on 2009-03-15
Not sure if this one works. It titles: **How to keep the compiz cube zoomed out and in 3d.**

[http://djbarney.wordpress.com/2008/05/28/how-to-keep-the-compiz-cube-zoomed-out-and-in-3d/](http://djbarney.wordpress.com/2008/05/28/how-to-keep-the-compiz-cube-zoomed-out-and-in-3d/)

Just in case the link dies, I captured the crucial part of it here:
> (Note: “\\” shows where I had to split the line. It should all be on one line.)

Make sure you have a backup of your X server config file.

sudo cp /etc/X11/xorg.conf \\
/etc/X11/xorg.conf.bak

Edit it …

sudo vim /etc/X11/xorg.conf

If you don’t like the command line you can use this …

gksudo gedit /etc/X11/xorg.conf

Find this section …

Section "InputDevice"

        Identifier "Configured Mouse"

        Driver "mouse"

        Option "CorePointer"

EndSection

Add this line …

Option "DragLockButtons" "3 2"

The section will now look like this …

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "DragLockButtons" "3 2"
EndSection

The first number after “DragLockButtons” is the button to be toggled. In this case button 3, the middle mouse button on my three button mouse. The second number is the mouse button to use to activate the toggle.

Save the xorg.conf file. Type “:”, then “wq”.

Logout of Ubuntu and then back in again. That will restart the x server without having to restart the entire system.

Now you can click the right mouse button over a clear area of desktop and the middle mouse button will lock allowing free rotation of the compiz cube. You can walk away and leave it in mid rotation. Hit the right mouse button again to let Compiz focus back to the active desktop.

There’s only one drawback here if you only have three mouse buttons. The defined lock button can no longer be used as a normal mouse button ! I just use the right click key on my keyboard.

:popcorn:

---

