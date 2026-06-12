---
title: "MSI AE1900 Touchscreen &amp; 10.10 How-To"
date: 2011-04-07
forum: Hardware
---

### Post by kubug on 2011-04-07
I just wanted to post my finding in how to get the touchscreen working on a MSI AE1900. Out of the box the X and Y coordinates are backwards and the dimensions are off. 

I found a bunch of old posts for Jaunty and earlier, but they all don't work. I finally found a working solution from here: [http://setupguides.blogspot.com/2010/10/calibrating-touchscreen-in-ubuntu-1010.html]("http://setupguides.blogspot.com/2010/10/calibrating-touchscreen-in-ubuntu-1010.html"). It makes mention to use the 'xinput_calibrator', and upon following the steps, I couldn't get it to work. So back to the manual part of the blog...


First start with finding your device id:

```
xinput list
```

That should produce this:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Comfort Curve Keyboard 2000   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; IDEACO  IDC 6681                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; IDEACO  IDC 6681                       	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Comfort Curve Keyboard 2000   	id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=10	[slave  keyboard (3)]
    &#8627; BisonCam, NB Pro                        	id=14	[slave  keyboard (3)]
    &#8627; MSI WMI hotkeys                         	id=15	[slave  keyboard (3)]

```

I used ID 12, the first occurrence of the IDEACO touchpad.

Here is the command that set the proper values for me:

```
sudo xinput set-int-prop 12 "Evdev Axis Calibration" 32 7550 660 7300 960
``` 

The last four numbers are the actual calibration numbers:

1.) 7550 - X axis start value (change this number to change the start point on the X axis - left side)
2.) 660  - X axis multiplier/accelerator (change this number to change the end part of the X axis - right side)
3.) 7300 - Y axis start value (change this number to change the start point on the Y axis - top)
4.) 960  - Y axis multiplier/accelerator (change this number to change the end point on the Y axis - bottom)

Once you found the values that work for you, make it permanent:


Type:
```
gksu gedit /etc/X11/Xsession.d/98x11-common_touchscreen
```

And paste the command with the value that worked for you (without the leading 'sudo' part.

Hope this helped someone. To be honest, beyond this I am not sure how else help.

---

