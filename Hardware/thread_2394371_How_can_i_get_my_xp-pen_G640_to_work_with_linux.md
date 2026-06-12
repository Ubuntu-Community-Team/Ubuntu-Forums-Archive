---
title: "How can i get my xp-pen G640 to work with linux?"
date: 2018-06-15
forum: Hardware
---

### Post by itzhard on 2018-06-15
So i bought this tablet a couple of days ago and i can't figure out how to make it work on linux mint 18.3 (same for ubuntu).


my kernel is 4.13.0-45 generic.


any help would be appreciated.



some basic commands output:

lsusb:

Bus 001 Device 004: ID 28bd:0094  

------------------------------------------

xinput list:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; XP-PEN STAR G640                        	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; XP-PEN STAR G640                        	id=18	[slave  keyboard (3)]

--------------------------------------------

xinput test 17:

only buttons work


--------------------------------------------

[FONT=&quot]usbhid-dump -es:

tracking and buttons works

---------------------------------

ls /dev/input:

[/FONT]by-id    event1   event12  event15  event18  event20  event23  event4  event7  mice    mouse2
by-path  event10  event13  event16  event19  event21  event24  event5  event8  mouse0  mouse3
event0   event11  event14  event17  event2   event22  event3   event6  event9  mouse1  mouse4

---------------------------------------------

ls /dev/input/by-id:

usb-XP-PEN_STAR_G640-event-mouse
usb-XP-PEN_STAR_G640-if01-event-mouse
usb-XP-PEN_STAR_G640-if01-mouse
usb-XP-PEN_STAR_G640-mouse

----------------------------------------------

---

### Post by vangelos on 2018-11-17
I have the same issue on archlinux [https://bbs.archlinux.org/viewtopic.php?id=240275](https://bbs.archlinux.org/viewtopic.php?id=240275)

---

