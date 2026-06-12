---
title: "Logitech webcam: /dev/video0 not found?"
date: 2009-08-08
forum: Hardware
---

### Post by jorx on 2009-08-08
Hi everybody,
I've been googling already for a while and have been toubleshooting-
I've got a Logitech Inc, Quickcam PTZ webcam. (or so it says through the command 'lsusb')

No matter what software or cam capture program I use- I get the same error: "/dev/video0 missing or not found".

It worked once on me, through a live USB attempt- (and loaded fine in Skype).  Since then I have not been able to replicate my success on any machine with the same webcam. 

I'm still a relative newb/noob to Linux (with a poweruser Windows background). Through googling I found out about the dmesg -c command, which lists the changes to hardware.

SO I unplugged the webcam, ran it, ('dmesg -c') plugged it in, ran again, and I got this code.

```

[ 7932.616018] usb 1-6: new high speed USB device using ehci_hcd and address 4
[ 7932.939719] usb 1-6: configuration #1 chosen from 1 choice
[ 7932.940097] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c2)
[ 7933.936126] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[ 7934.936130] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[ 7934.936135] uvcvideo: Failed to initialize the device (-5).
[ 7935.904017] 4:3:3: cannot set freq 16000 to ep 0x86
```

Any advice? I'm dependent on this webcam to talk to my family... so I would really appreciate your help!

Thanks,

---

