---
title: "Horizontal scrolling on Thinkpad USB Keyboard with Trackpoint"
date: 2015-03-26
forum: Hardware
---

### Post by gdi2k on 2015-03-26
Today I got a Thinkpad USB Keyboard with Trackpoint - this one to be precise: 
[http://shop.lenovo.com/us/en/itemdetails/0B47190/460/60AC6A0372B14F5BA7B12F1FF88E33C7](http://shop.lenovo.com/us/en/itemdetails/0B47190/460/60AC6A0372B14F5BA7B12F1FF88E33C7)

It works perfectly, including the trackpoint, aside from horizontal / sideways scrolling. 
It is attached to a Thinkpad X200, and horizontal scrolling works just fine on the laptop keyboard, but not on the new external one. 

I have tried: 
[LIST]
[*]"xinput set-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Axes" 6 7 4 5" as per [this]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint"). 
[*]Setting it with gpointing-device-settings
[*]Using the commands [here]("https://wiki.archlinux.org/index.php/TrackPoint").
[/LIST]

Nothing has worked so far. 

Any good suggestions how I might make this work? It's a really important feature for me due to much Libreoffice Calc usage. 

Thanks!

---

### Post by tgalati4 on 2015-03-26
If you open a terminal and run *xev*, and put the mouse cursor in the *xev* box, describe what happens when you run your finger along the bottom horizontal edge of the trackpad.  On my trackpad (on an Acer at this moment), there is no input and I have horizontal scrolling disabled in mouse preferences.

If I turn on both "edge scrolling" and "horizontal scrolling" in mouse preferences I can now see the XY coordinates as I drag my finger along the lower, horizontal edge of the trackpad.  I don't have my Thinkpad in front of me at the moment to test the behavior of the trackpoint to see if it behaves the same way.

Post the output of the following:

```
xinput --list --long
```

Cut down the list to include only the trackpoint information.

The X-Windows framework for handling input devices is quite cumbersome.  There is a "master pointer" and a "slave pointer" defined and it's possible that the preference settings that get set for the "master pointer" don't trickle down to the "slave pointer".  Manually making the preference settings in /etc/X11/xorg.conf file may be ignored by modern desktop environments.

Is there a way to turn off the internal trackpoint in BIOS?  If so, then perhaps the external trackpoint will pick up the settings.

It seems to be an issue in general:  

[http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html](http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html)

From the ThinkWiki page in your link, it could be a simple case of getting the axis ID's correct.

---

### Post by gdi2k on 2015-03-26
Thanks tgalati4, this is a trackPOINT (red knob on ThinkPads), not a trackpad, but interesting to see how xev behaves: 

On the Laptop, scrolling in different directions yields the following: 
Up: Button 4
Down: Button 5
Left: Button 6
Right: Button 7

On the external keyboard with TrackpoinUp: 
Button 4
Down: Button 5
Left: **Nothing**
Right: **Nothing**

So there's my issue - any ideas how I can get it to output something? Is this driver related? I think these are supposed to be the same keyboards as the Thinkpad 30 series (T430, X230 etc.) but I don't know if they are exactly identical.

---

### Post by gdi2k on 2015-03-26
Oh, and the output from: 

```
xinput --list --long
```

Is: 
```
gdi2k@x200:~$ xinput --list --long
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
	Reporting 10 classes:
		Class originated from: 13. Type: XIButtonClass
		Buttons supported: 22
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button 5" "Button 6" "Button 7" "Button 8" "Button 9" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
		Button state:
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Dial
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 4:
		  Label: Rel Vert Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 1.000000
		  flags: 0x0
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x0
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 4
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x2 ( preferred )
		Class originated from: 9. Type: XITouchClass
		Touch mode: direct
		Max number of touches: 0

&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 4. Type: XIButtonClass
		Buttons supported: 10
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None
		Button state:
		Class originated from: 4. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 4. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative

&#9116;   &#8627; Plantronics Voyager Legend              	id=9	[slave  pointer  (2)]
	Reporting 25 classes:
		Class originated from: 9. Type: XIButtonClass
		Buttons supported: 5
		Button labels: "Button Unknown" "Button Unknown" "Button Unknown" "Button Wheel Up" "Button Wheel Down"
		Button state:
		Class originated from: 9. Type: XIKeyClass
		Keycodes supported: 248
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 153.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 128.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 4:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 5:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 6:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 7:
		  Label: Abs MT Touch Major
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 8:
		  Label: Abs MT Touch Minor
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 9:
		  Label: Abs MT Width Major
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 10:
		  Label: Abs MT Width Minor
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 11:
		  Label: Abs MT Orientation
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 12:
		  Label: Abs MT Position X
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 13:
		  Label: Abs MT Position Y
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 14:
		  Label: Abs MT Tool Type
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 15:
		  Label: Abs MT Blob ID
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 16:
		  Label: Abs MT Pressure
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 17:
		  Label: Abs MT Distance
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 18:
		  Label: Abs MT Tool X
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 19:
		  Label: Abs MT Tool Y
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 20:
		  Label: None
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 21:
		  Label: None
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 9. Type: XITouchClass
		Touch mode: direct
		Max number of touches: 0

&#9116;   &#8627; Lenovo ThinkPad Compact USB Keyboard with TrackPoint	id=13	[slave  pointer  (2)]
	Reporting 10 classes:
		Class originated from: 13. Type: XIButtonClass
		Buttons supported: 22
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button 5" "Button 6" "Button 7" "Button 8" "Button 9" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
		Button state:
		Class originated from: 13. Type: XIKeyClass
		Keycodes supported: 248
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Dial
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 4:
		  Label: Rel Vert Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 1.000000
		  flags: 0x0
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x0
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 4
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x2 ( preferred )

&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 16. Type: XIButtonClass
		Buttons supported: 7
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
		Button state:
		Class originated from: 16. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 16. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative

&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
	Reporting 1 classes:
		Class originated from: 12. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 5. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 6. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 7. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 8. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; UVC Camera (17ef:480c)                  	id=10	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 10. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; Yubico Yubico Yubikey II                	id=11	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 11. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; Lenovo ThinkPad Compact USB Keyboard with TrackPoint	id=12	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 12. Type: XIKeyClass
		Keycodes supported: 248

    &#8627; Plantronics Plantronics BT300           	id=14	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 14. Type: XIKeyClass
		Keycodes supported: 248

```

---

### Post by tgalati4 on 2015-03-26
Oh, you are going to hate this suggestion.

Look for an old Ubuntu DVD like 10.04 or 12.04 and boot a Live Session.  Then make the changes from the links that you found.  See if the external trackpoint horizontal scrolling works.  If so, then you know that there was a framework change that either requires a bug fix or a clever work-around.

If you are running 13.04, then perhaps try 14.04 in a Live Session and see if there is a magic fix.

Some other things to try:

Remove the Plantronics keyboard.

If you are using a USB hub, remove that and use the Lenovo keyboard direct to a USB port.

---

### Post by gdi2k on 2015-03-26
Thanks, will give it a go tomorrow as I don't have a usable flash disk to hand right now. Earliest I could find was 12.04...

---

### Post by gdi2k on 2015-03-26
Doing more searching on this, I found an interesting review on Amazon about this exact issue. It's quite detailed, so I will post the relevant section here in the hopes that it will be useful to resolving this. 

It's from: 
[http://www.amazon.com/gp/product/B00F3U4TQS?ie=UTF8&camp=1789&creativeASIN=B00F3U4TQS&linkCode=xm2&tag=evuswemeevevu-20](http://www.amazon.com/gp/product/B00F3U4TQS?ie=UTF8&camp=1789&creativeASIN=B00F3U4TQS&linkCode=xm2&tag=evuswemeevevu-20)

> - - My 2 Problems with this keyboard - -
-1
I have yet to have found a way to remap the "Fn" and "LeftCtrl" keys.
I'm sure there is a way to do it. I need to search more in /usr/share/X11/xkb/*/*
But xev shows no output for the "Fn" key and this is normal. It's output is filtered by the driver, because it is not meant to be a Modifier Key ... on that level. It is suppose to be interpreted by the driver and the driver should only deliver the scancodes for the "Fn" modified key.

-2
Out of the box,
Horizontal Scrolling with the TrackPoint dose not work at all
# cat /dev/input/by-id/usb-Lenovo_ThinkPad_Compact_USB_Keyboard_with_TrackPoint-if01-event-mouse
Displays output while holding the centrer button and moving the pointer up/down
Displays NO output at all while holding the centre button and moving side to side

Interestingly,
# xinput list 10
Shows "Scroll info for Valuator 2" ... "type: 2 (horizontal)" which indicates that holding the middle button should enable Horizontal scrolling by default. Below that it shows "Scroll info for Valuator 3" ... "type: 1 (vertical)" and Valuator 4 as vertical as well as being marked ( preferred ).

When I cat the the USB device directly. The output confirms this.
The USB device shows output while moving the TrackPoint Left/Right and different output while holding the Middle mouse button. However, it shows NO Output while holding the middle mouse button and moving the TrackPoint Up/Down.

xinput also shows this keyboard with 22 button-maps.
It also shows these Button Labels in the 6 and 7 positions (which is where they should be)
"Button Horiz Wheel Left" "Button Horiz Wheel Right"

My Conclusion is that I need to modify the evdev driver.
I do not think this is a hardware problem and all it's problems can be solved in the driver.

---

### Post by gdi2k on 2015-03-27
> **tgalati4 said:**
> Oh, you are going to hate this suggestion.

Look for an old Ubuntu DVD like 10.04 or 12.04 and boot a Live Session.  Then make the changes from the links that you found.  See if the external trackpoint horizontal scrolling works.  If so, then you know that there was a framework change that either requires a bug fix or a clever work-around.

I downloaded a 12.04 Live CD, but still a no go. No horizontal scroll after making changes, and no output from xev on horizontal scroll either. :(
> **tgalati4 said:**
> If you are running 13.04, then perhaps try 14.04 in a Live Session and see if there is a magic fix.

Some other things to try:

Remove the Plantronics keyboard.

If you are using a USB hub, remove that and use the Lenovo keyboard direct to a USB port.
I am actually runnning fully updated 14.04. The Plantronics device is actually a headset - I removed that and also the hub, but still no difference.

---

### Post by gdi2k on 2015-03-27
In the same vein as above, I did try the latest available kernel from the kernel PPAs: 

```
Linux x200 4.0.0-040000rc5-generic #201503230035 SMP Mon Mar 23 04:36:26 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

But the situation is worsened; xev has no output for vertical or horizontal scrolling using this kernel. 

The X200 Trackpoint (on the laptop) works fine in all scroll directions, and also outputs xev events for all scroll directions. 

So is this a kernel bug? Should I file it?

---

### Post by tgalati4 on 2015-03-27
I would contact that Amazon reviewer and follow up to see if they came up with a work-around.  I know on an old HP multimedia keyboard that I have, I had to use several *setkeycodes* statements to get all 23 extra keys to work.  I was able to do it, but it took some trial-and-error.  Normally this would be handled by the module (driver) that gets loaded when the keyboard is detected.  If the module is deficient, then file a bug against the module and see if any work-arounds exist in the bug report.

At least you know two things:  1.  You are not the only one with this problem.  2.  You are not crazy.

I don't think a new kernel will fix this.  The problem is most likely the *evdev* module.

---

### Post by gdi2k on 2015-04-03
Thanks tgalati4, I contacted the Amazon reviewer, but no response yet. 

I played with showkey, but could get no output from scrolling in any direction - I am assuming it is not designed for mice. 

[QUOTE=tgalati4]At least you know two things: 1. You are not the only one with this problem. 2. You are not crazy.[/QUOTE]

1. Yes, that's good. 2. Not so sure about that! \\:D/

Bug filed: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1439948](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1439948)

---

