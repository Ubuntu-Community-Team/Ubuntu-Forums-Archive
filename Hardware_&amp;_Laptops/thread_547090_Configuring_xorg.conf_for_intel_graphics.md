---
title: "Configuring xorg.conf for intel graphics?"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by deadowl on 2007-09-09
Alright, I have a Dell Latitude D820 with Intel 945GM graphics. I have experienced some problems. In addition, my monitor has a resolution of 1680x1050 (which I installed 915resolution to fix).

I had trouble playing HD videos, but added a line in my xorg.conf, but since then all videos have been playing with a bit of brightness. Also, games are so slow with the line that they're essentially unplayable.

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Inte$
        Driver          "i810"
        Option "LinearAlloc" "32768"
        BusID           "PCI:0:2:0"

The LinearAlloc option is the line I added when looking for solutions to the HD problem.

I also am having some trouble when plugging into my university's projectors. The two problems in general are:

1. The alignment of the screen is screwed up (the top is cut off and projected underneath everything. This is fixed by changing my resolution locally, but I honestly don't even want to have to think about it.

2. Videos running on top of X tend to have issues when showing through the projector and workstations, especially if I don't switch off of my local monitor.


Alright, and my last problem, though somewhat less related, audio (HDA Intel) is incredibly slow when playing SuperTux. This problem is independent of the video problem.

---

### Post by deadowl on 2007-09-15
Yea... I definitely haven't made any progress.

---

### Post by MrHippocampus on 2007-09-15
I think gusty ships with a vastly improved intel driver which might help with some of these problems. Try running a gusty livecd and see if it helps with anything. (unfortunately you wont be able to use the new driver with your existing feisty, but at least youll know whether gusty will solve your problems or not).

---

### Post by Linicks on 2007-09-16
Try the Intel driver - here are instructions from the dell wiki, but I guess it is this same for any machine:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues)

Nick

---

