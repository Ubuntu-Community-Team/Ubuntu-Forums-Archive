---
title: "Problem changing mouse button mapping"
date: 2009-04-27
forum: Hardware
---

### Post by garyvdm on 2009-04-27
Hi

I'm trying to do this: [http://ubuntuforums.org/showthread.php?t=830773]("http://ubuntuforums.org/showthread.php?t=830773") on intrepid, but in intrepid, input setting in xorg.conf are ignored, as it uses input-hotplug. 

So I tried to run:
```
xinput set-button-map "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" 1 2 3 4 5
```

But I get this error:
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  29 (X_SetDeviceButtonMapping)
  Value in failed request:  0x3
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

It works for 1 2 3 4 5, but for any out the other options, I get the same error:

1 9 3 4 5
1 6 3 4 5 
etc...

I would also like to find out where the Mouse Preferences app saves it settings.

Gary

---

