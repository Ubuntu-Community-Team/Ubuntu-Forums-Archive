---
title: "XrandR and hardware problems on Compaq TC1000 / tc1k"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by jonathan-tc1k on 2007-05-29
Hi guys,
I'm currently running Xubuntu on my tc1k tablet PC and nearly everything is working great.

However I ran into one big problem:
Switching to portrait mode using xrandr jusst won't work.

I've enabled the extension using 

nvidia-xconfig --randr-rotation

and it shows up correctly in /etc/X11/xorg.conf

However rotation is not possible.
Using
xrandr --verbose -o left
I get 
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 260mm x 195mm )  *50  
 1    800 x 600    ( 203mm x 152mm )   51   53  
 2    640 x 480    ( 162mm x 121mm )   52  
 3    640 x 384    ( 162mm x  97mm )   54  
 4    576 x 384    ( 146mm x  97mm )   55  
 5    512 x 384    ( 130mm x  97mm )   56  
 6    400 x 300    ( 101mm x  76mm )   57   58  
 7    320 x 240    (  81mm x  60mm )   59  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none
Setting size to 0, rotation to left
Setting reflection on neither axis
Failed to change the screen configuration!


The really strange thing is that the rotation worked one time using exactly this command.
Even resetting to normal worked. But no chance afterwards...

But even the one time the rotation worked I received another problem concerning the hardware, the pen axis were not rotated, so it was not possible to use the pen in portrait mode. The mouse cursor was moving in other directions than the pen was moved.
I guess I'll have to use a script to swap the pen axis in order to get this working, unfortunately I've no idea how to accomplish this.

As my xorg.conf might be interesting for this problem I have uploaded it.
It can be found here: [http://www.team-uac.de/Xubuntu/xorg.conf](http://www.team-uac.de/Xubuntu/xorg.conf)

Any help on this problem would be great!

greets
jonathan

/edit:

I've now managed to rotate the display.

Creating two launchers on the desktop containing the commands did the trick.
The commands are

xrandr -o left
and 
xrandr -o normal

Starting them with a doubleclick rotates the display / resets the dispaly.
God knows why these commands won't work in terminal...
However the problem regarding the Pen control remains unsolved.

If anyone has a clue about this I would be very happy for any assitance.

greets 
Jonathan

---

