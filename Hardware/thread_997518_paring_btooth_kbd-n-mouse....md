---
title: "paring btooth kbd-n-mouse..."
date: 2008-11-29
forum: Hardware
---

### Post by zander1013 on 2008-11-29
hi,

hardware involved: apple macbook pro run by mac os x, apple bluetooth keyboard and mighty mouse, ibm thinkpad t42 run by ubuntu 8.10

i am trying to pair apple bluetooth keyboard and mouse with ibm t42 thinkpad laptop using the ubuntu bluetooth setup wizard on the applet bar of the ubuntu desktop.

the mouse paired and worked for awhile on the ibm. then i removed it and the keyboard from the apple laptop bluetooth device list that they had been paired with before to avoid conflict with the ibm t42.

i removed the bluetooth keyboard and mighty mouse from the apple laptop bluetooth device list at the same time and then closed the bluetooth preferences dialog on the apple.

i went back to the ibm laptop restarted it and tried to pair the keyboard and mouse again but it keeps failing to pair either one of them now.:(

how can i pair the bluetooth keyboard and mighty mouse with the ibm? if the mouse paird once then shouldn't it pair again? and if the mouse paired shouldn't the keyboard too?

each device when switched on gives a continuous on signal then goes to a two short flash sequence that cycles.

when i try to pair the kbd and mouse with the ibm using the bluetooth setup wizard it can recognize the keyboard and mouse but when i try to pair with them the wizard says that pairing failed.

please advise.

---

### Post by finito on 2008-11-29
do u have internal bluetooth or a dongle?

---

### Post by zander1013 on 2008-11-29
> **finito said:**
> do u have internal bluetooth or a dongle?

i have a dongle. the btooth xcver is just plugged directly into the usb port on the ibm.

---

### Post by finito on 2008-11-30
just unplug and plug it, I have the same problem, which is corrected by unplugging and plugging it back in.

---

### Post by zander1013 on 2008-11-30
> **finito said:**
> just unplug and plug it, I have the same problem, which is corrected by unplugging and plugging it back in.

i tried that and it's still not working. i put fresh batteries in the mouse just to be sure.

i am still not able to pair them.

i repairded them with the macbook pro and they paird just fine.

so if we could just get them to work with the ibm again...

---

### Post by zander1013 on 2008-11-30
i got the mouse paired again. the solution was to choose System > Preferences > Bluetooth > computername-0. then check "always visible", delete the device name from known devices and then set it up from scratch again.

at least that worked for the mouse.

---

