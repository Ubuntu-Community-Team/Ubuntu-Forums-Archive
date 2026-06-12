---
title: "Lenovo X61 Tablet. Weird touch rotation issue."
date: 2010-09-06
forum: Hardware
---

### Post by Anastasios Marmaras on 2010-09-06
Hello,

I have to report a weird problem i am experiencing with touchscreen rotation on my Lenovo X61 tablet currently running Lucid. (i am aware of this problem since Jaunty).

I am following a variant of the procedure described on [thinkwiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_an_X61_Tablet") to create a screen, stylus, eraser and touch rotation script.

To rotate the screen i am using:
/usr/bin/xrandr -o $orientation
(where orientation can be: normal, left, inverted, right)

To rotate the stylus i am using:
/usr/bin/xsetwacom set "Serial Wacom Tablet" rotate  $orientation
(where orientation can be: NONE, CCW, HALF, CW)

To rotate the eraser i am equivalently using:
/usr/bin/xsetwacom set "Serial Wacom Tablet eraser" rotate $orientation

And to rotate the touch input i am using:
/usr/bin/xsetwacom set "Serial Wacom Tablet touch" rotate $orientation

To calibrate all three input devices i am using:
/usr/bin/xsetwacom set $device_name $parameter $value
(where $parameter can be: TopX, TopY, BottomX, BottomY)

Screen, stylus and eraser work perfectly on all orientations. Touch works perfectly on normal orientation but behaves strangely on the other three. In particular, touching the screen moves the pointer to the exact touched location but releasing the touch returns the pointer to the location it would have been placed if the touch device had NOT been rotated. For example in "HALF", touching the upper left corner of the screen moves the pointer to that corner but upon releasing the pressure the pointer moves to the lower right corner of the screen. The final behavior is almost the equivalent of a click_drag_and_release motion which eg. selects text boxes but does not press buttons.

Any ideas where this can be coming from ?

thanks,
Anastasios

---

### Post by jasqs on 2010-09-15
I have exactly the same problem.
In my opinion it isn't problem of rotating generally but only of rotating touch. If I make /usr/bin/xsetwacom set "Serial Wacom Tablet touch" rotate half or any other orientation except "none" I will get the same problem as you.
I will try to work at it but if you already have found the solution, share it with me, please.

thanks,
Jasqs

---

### Post by Favux on 2010-09-15
Hi Anastasios Marmaras & jasqs,

Welcome to Ubuntu forums!

I'm going to guess both of you are using Lucid.  ODDie reported the same problem on his Lenovo X200 tablet to the LWP's bug tracker:  [http://sourceforge.net/tracker/?func=detail&aid=3041514&group_id=69596&atid=525124](http://sourceforge.net/tracker/?func=detail&aid=3041514&group_id=69596&atid=525124)  As you see he fixed it by updating xf86-input-wacom.

For instructions on cloning the xf86-input-wacom git repository see Section 2 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") or II. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

Hope this helps.

---

### Post by Anastasios Marmaras on 2010-09-18
Dear Favux,

Yes, the xf86-input-wacom did the trick for me too, thanks a lot! I appreciate it!

I have two things to say:

One is to report that a strange behavior that could be considered a bug is still there:

When one rotates one device, say, the touch:

 xsetwacom set "Serial Wacom Tablet touch" rotate HALF

Then the other devices (eraser and stylus) will also be rotated, although

 xsetwacom set "Serial Wacom Tablet stylus" rotate
 xsetwacom set "Serial Wacom Tablet eraser" rotate

both return "NONE"

Trying, say:
xsetwacom set "Serial Wacom Tablet eraser" rotate NONE

will return ALL three devices back to normal although:

xsetwacom get "Serial Wacom Tablet touch" rotate 

will still return: "HALF"

It does not impede functionality in any way but it IS weird. It is as if there are two different types of system variables, one the actual state of all three device and the other the reported state of each individual device which get only individually updated when the xsetwacom command is invoked but do not reflect the REAL state of the devices. Well, just had to report it.


The second thing is just a little suggestion: In both links, [linuxwacom]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") and [bamboo]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") the instructions to install the xorg macros contain a "make" step which fails with a "nothing to do" error. Which is normal because there is nothing to compile, the scripts just need the make install step. However this can really confuse a newbie like myself! ;)

Thanks again!
Anastasios

P.S.   jasqs, did it work for you ?

---

### Post by Favux on 2010-09-18
Hi Anastasios Marmaras,

Good!  :)

I'm beginnning to think the xsetwacom rotate command has gotten a little wonky.  We were just unable to use it to rotate a tablet to left handed mode for a leftie and had to resort to:

Option "Rotate"  "Half"

in the usb snippet of 10-wacom.conf.  I think you ought to report your findings to the LWP's bug tracker:  [http://sourceforge.net/tracker/?group_id=69596&atid=525124](http://sourceforge.net/tracker/?group_id=69596&atid=525124)

> The second thing is just a little suggestion: In both links, linuxwacom and bamboo  the instructions to install the xorg macros contain a "make" step which fails with a "nothing to do" error. Which is normal because there is nothing to compile, the scripts just need the make install step.
I'll have to check that out.  I guess I'm cannulated by the "configure, make, and make install" triumvirate.

---

### Post by jasqs on 2010-09-20
Hi

Solution from posts above-mentioned works for me properly. Thank you Favux.

In fact bug with wrong reading rotate state for different devices also appears to me. I noticed it after Anastasios Marmaras had mentioned it. It isn't problematic for me because rotate (especially autorotate) works perfectly now. But it is wired.

thanks Favux

/jasqs

---

