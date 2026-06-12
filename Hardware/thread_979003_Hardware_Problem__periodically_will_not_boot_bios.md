---
title: "Hardware Problem | periodically will not boot bios"
date: 2008-11-11
forum: Hardware
---

### Post by dutler on 2008-11-11
Hello:
Yes, I think this has little to do with ubuntu, I do not have ms windows am confident this is not a operating system issue.  But Im posting here because I dont know what elese to do an have the impression that ububutu users are pretty savy :)

I have an IBM Z Pro (6220) Dual PIV workstation with 4GB RAM and 73GB SCSI HD and Nivda FX1100 AGP Pro - its a bit older but plenty good for me (if only support KVM)....

I have had ubuntu on it for over two years and have never had a lot of trouble other than getting OpenGL to work. In the last few months the machine will periodically not reboot - just happens about 75% and not 100% of the time. The machine powers up, but does not get to the memory check and certainly doesnt get to booting off the hard drive.

The solution is to unplug everything (Ethernet, firewire hd, audio connector, usb hub) and retry retry retry retry.... I have not determined a causative relationship (because the symptoms are erratic) but there seems to be a higher correlation of success with letting the computer set with out power for 5 min or so and also the unpluging the usb hub than unpluging the other devices.

I have observed electrical dischage from the usb cable (that runs from a rosewill powered hub at my desk, 15ft, to the IBM Z Pro in the closet) to the chasis when I  unpluged the cable with the computer powered up. Both the hub and the computer (all devices) are pluged in to the same UPS.

I have updated the motherboad bios, preformed a memcheck, direcly grouned the chasis...

High expectations of billiant insights, thank you for reading my post.
-tom

---

### Post by dutler on 2008-11-20
I rewired my server room (cough cough closet) by dropping some outlets and getting rid of an extension cord that ran parallel with the mentioned USB cable for ~8'
It was *only* a 15 amp circuit and *only* a faction of that in the heavy duty extension cord and *only* 8 feet, but that was enough inductance the screw with things.

-tom

---

