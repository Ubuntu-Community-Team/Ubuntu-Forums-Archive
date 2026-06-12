---
title: "Samsung notebook touchpad and video card issues"
date: 2012-12-28
forum: Hardware
---

### Post by windowsh8r on 2012-12-28
I just got a Samsung 535 laptop, and the touchpad registers as a Logitech mouse, there is no toucphad option in the System>Administration>Mouse tool.  I looked around the internet a bit and found a Solved similar issue, but the fix does not work for me ([http://ubuntuforums.org/showthread.php?t=1628673&page=2](http://ubuntuforums.org/showthread.php?t=1628673&page=2))  When I try to do the build action from that link, it says the Elantech v6 is not found.  I can use the touchpad, but it is very sensitive and I cannot disable the touch click.  

Also, I cannot enable desktop effects, and the function keys to adjust the brightness or volume lock up the keyboard, forcing me to reboot.  Thanks

Oh, I am using 10.04 with all updates installed

---

### Post by windowsh8r on 2012-12-29
here is the output from xinput list

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; WebCam SC-13HDL12131N                   	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]


How can I disable the tap-click?

---

### Post by windowsh8r on 2013-01-13
Anyone?

---

