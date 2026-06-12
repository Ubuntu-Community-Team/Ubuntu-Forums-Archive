---
title: "X41 Tablet - Screen Rotation?"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by kderose on 2006-08-28
I'm new to having ubuntu on my laptop an ibm x41 tablet, and I have been trying to get some of the tablet features to work with mixed success...I would appreciate any help out there!

I've been trying to get the screen to rotate by following these instructions:

[http://gtt.blaubeermuffin.de/Screen_Rotation_with_IBM/Lenovo_ThinkPad_X41_Tablet](http://gtt.blaubeermuffin.de/Screen_Rotation_with_IBM/Lenovo_ThinkPad_X41_Tablet)

The last script on the list (a .sh extension) I try running it by typing python ibm-lidmode-listener.sh, but it just ends up hanging on the last line.  I'm not sure if I am on the right track or not but if anyone has gotten the screen to rotate another way or has any suggestions that would be great!

I have heard xrandr is supposed to work, but for some reason when I try the command xrandr -o left, i get the following error message despite the fact that my xorg.conf file has option "RandRRotation" "on" in it:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Thanks ahead of time for your help!!!

---

