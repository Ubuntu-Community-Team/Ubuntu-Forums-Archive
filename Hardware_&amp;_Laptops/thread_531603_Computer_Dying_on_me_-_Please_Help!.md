---
title: "Computer Dying on me - Please Help!"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by cypher35 on 2007-08-21
My computer will no longer boot up properly.  Before I get ahead of myself though, here is a bit of background.  This problem started (assuming all of these instances are related) back in back in June or so.

Just for a quick reference, I've got four hard drives in total attched to my computer:
```
/       - 160gb IDE Hard Drive - partitioned into two drives, one mapped to root, one mapped to /vol/Y/
/vol/X/ - 250gb and 160gb IDE Hard Drives - using some "fasttrack" bios setting to raid together (requires dmraid under linux)
/vol/Q/ - 250gb SATA Hard Drive
```
^I would have copied the contents of /etc/fstab for you here, but at the moment I can't reach it.


The following is a list of (probably) related symptoms that have come up over this last summer:
[LIST=1]
[*]Starting around June, my "X" drive (at /vol/X/) started corrupting any new files that were created on the hard drive.  The files that were already on it could be read correctly, but when I'd write any new file to the drive, it would become partially corrupt.  For instance, I could transfer over a video and suddenly there would be artifacts all over the screen at certain parts of the video that had not been there previously.

[*]Occasionally, when going back to my computer after leaving it for a while, I could tell it had rebooted itself while I was away.  At first I passed it off as possibly being a momentary power loss or something, but the problem continued.

[*]**Sometimes the computer would reboot and map my 250gb SATA drive to a different device name.  For instance it would alternate between /dev/sda1 and /dev/sdc1 (or something like that, I don't recall the exact locations).  I noticed this because every once in a while I had to look it up and change the entry in /ect/fstab in order to mount it.**

[*]Occasionally (usually after rebooting), the sound card would not work and I would have to unplug my speakers and plug them into my mobo's on-board speaker jack.  This would alternate occasionally much like my "Q" drive mentioned above.
[/LIST]

------------------------

When I got my computer to my dorm room yesterday, it wouldn't turn on at all.  I tried a different outlet and pressed the power button again, and it managed to make a click noise like one of the fans just started to move, but it didn't do anything more.  The next day (today) I unhooked the power supply completely and tried using a paper clip to jump-start it.  This seemed to work just fine as the fan started moving and all that, but I have no idea if this an indication that it is working successfully.  Perhaps it behaves differently under stress or with more devices attached.

I tried unhooking everything from the motherboard except for the primary hard drive, the pci cards, and the necessary power cords.  Then I used the same paper clip to short the place where the power switch is supposed to attach to the motherboard.  I managed to get the computer to power up.  Then I reattached the switch and started using that again:

Here are the current symptoms after playing around with it for a while:
[LIST=1]
[*]My computer doesn't always turn on on queue.

[*]Sometimes after pressing the button and getting no response from the computer, it will boot itself up a good 30 seconds after I let go of the button.

[*]Sometimes the computer does not turn off when holding the button (it powers off and immediately powers on).
[/LIST]

------------------------

Possible problems:

a) The power supply
- tried jump-starting it and it worked fine, but perhaps it behaves differently under stress.

b) The power switch
- possibly a short in the power button cord that causes the flow of electricity to occasionally flicker off or on at times while depressed.  This could explain the times where the computer will immediately reboot when powering off.
- i don't know if this problem existed while using the paper clip to short the pins instead of the switch, because it is fairly difficult to reach or see and I am not sure how long I had held the paper clip over the pins before it turned on.
- this does not explain any of the previous symptoms however, such as the hard drive appearing under a different device name, etc.

c) The Motherboard
- the motherboard may have some sort of problem regulating the electricity, possibly tied to this awkward device mapping and file corruption.


Any insight that anyone could bring would be appreciated.  Does anyone know how the devices recieve their designated device mappings under linux?  For instance, why would a device alternate between /dev/sdc1 and /dev/sda1?  Could that be a software issue as well?  I sincerely hope the problem is not with the motherboard, as that is likely the most expensive item on this list to replace.

---

### Post by nosrednaekim on 2007-08-21
sounds like a hardware problem to me :(

---

### Post by cypher35 on 2007-08-22
That's why I posted this in the hardware forum...

I'm mainly curious as to what might cause the change in the name of the device mapping for my SATA drive.  Is that controlled by hardware or software?

---

### Post by w4ett on 2007-08-22
1.  Test the Power supply....beg, borrow or steal a tester and verify the output voltages

2.  Do a close visual inspection of the capacitors bordering the power connector and CPU socket for leakage or popped tops.

3.  Replace the cmos battery....spurious booting can sometimes be caused by CMOS checksum errors.

As always you mileage may vary  :)

---

### Post by cypher35 on 2007-08-23
Thanks, I'll give those a try.

---

