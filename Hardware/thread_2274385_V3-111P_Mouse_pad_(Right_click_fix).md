---
title: "V3-111P Mouse pad (Right click fix)"
date: 2015-04-20
forum: Hardware
---

### Post by gregory954 on 2015-04-20
Not sure if this is the right forum, but I have the Aspire V11 Touch and upon loading Lubuntu 14.10 (and other Ubuntu flavours) the mouse would work but right click would not.
I figured out these small set of commands to enable right click support, just thought I'd share since I seen people recompiling different mouse pad drivers and such to fix this problem.

```
#!/bin/bash
xinput --set-prop "SYN1B7D:01 06CB:2991 UNKNOWN" "Synaptics ClickPad" 1
xinput --set-prop "SYN1B7D:01 06CB:2991 UNKNOWN" "Synaptics Middle Button Timeout" 0
xinput --set-prop "SYN1B7D:01 06CB:2991 UNKNOWN" "Synaptics Soft Button Areas" 734 0 561 0 0 0 0 0
synclient VertTwoFingerScroll=0
```

The script looks for "SYN1B7D:01 06CB:2991 UNKNOWN" to make sure you have the same mouse pad as I do run the command "xinput" and it should be listed under "Virtual core pointer"
This script also disables two finger scroll  (I hate it).

Hope it helps someone!

---

### Post by koenr on 2015-05-04
Thanks a lot for this!
I made the change permanent on an Acer Travelmate B115 by following the advise from cesar on [http://askubuntu.com/questions/310729/how-to-make-an-xinput-command-persistent-after-standby](http://askubuntu.com/questions/310729/how-to-make-an-xinput-command-persistent-after-standby). I added a file 95synaptic to /etc/X11/Xsession.d/ containing your code, except the bash-line. This makes the change work for other users and the guest session.

---

