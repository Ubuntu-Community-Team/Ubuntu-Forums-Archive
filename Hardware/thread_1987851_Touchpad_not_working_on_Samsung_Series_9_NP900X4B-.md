---
title: "Touchpad not working on Samsung Series 9 NP900X4B-A02US"
date: 2012-05-26
forum: Hardware
---

### Post by mikematic on 2012-05-26
Hello All,

OS: Ubuntu 12.04 64bit on Samsung Series 9 NP900X4B-A02US

Issue: Touch pad is not working.

synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

 xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Webcam SC-13HDL11624N                   	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

dmesg | grep -i syna returns nothing indicating that there was no synaptics device detected during session start.

If anyone knows how to fix this issue I would greatly appreciate it.

Thanks and Regards,

---

### Post by mikematic on 2012-05-27
I have identified this to be an issue with the linux kernel not detecting the synaptics touchpad devices. Ticket has been created and filed under Ubuntu/Linux. URL for the bug is below.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1005215](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1005215)

Regards,

Michael

---

### Post by mikematic on 2012-05-28
Issue is resolved. The touchpad was disabled on the BIOS. Enabling it fixes the issue.

---

