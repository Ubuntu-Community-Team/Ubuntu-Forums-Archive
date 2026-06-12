---
title: "Epia M10000 freezing playing video"
date: 2008-11-08
forum: Hardware
---

### Post by rockerZ71 on 2008-11-08
I have a Via Epia M10000 that I am trying to set up as a MythTV system.  I installed mythbuntu a few weeks ago and today upgraded to intrepid (to see if it would help any of my problems).  My biggest issue is that when I try to play video files off CD or the hard drive, the system completely locks up.  Sometimes its almost immediately, other times I can watch maybe 10 minutes or more before it happens.  No clues in any logs.  This is not just through mythtv;  I just tried starting an X session and running mplayer and it froze.  I can play DVDs.  Any ideas?

Thanks

---

### Post by rockerZ71 on 2008-11-09
It seems to work fine with xine.  Anyone know why?  I'd like to get mplayer working, just because I can't figure out how to control xine with a joystick (usb gamepad)

ETA:  never mind, although it seems for now I can watch videos with xine, I did manage to lock up the whole system by trying to open one of xine's menus

---

### Post by fiepel on 2009-01-21
I have the same issue. I would be interested if you found the solution.

Just installed Mythbuntu 8.10, but no improvement. After playing video for a few minutes the whole system locks-up.

My M10000 used to work fine with fedora 4 and mythtv 0.20.

---

### Post by fiepel on 2009-01-27
I solved the problem.

It seems the DRM module has some bug that makes the system lockup when playing video.
I added:
```
Section "Module"
    Disable    "dri"
EndSection
```

to my xorg.conf and now video playback works. Drawback is that 3D is not hardware rendered anymore.

---

### Post by fiepel on 2009-01-27
Never mind

---

### Post by rockerZ71 on 2009-03-25
I let it go for a while and reinstalled Mythbuntu the other day so I will be working with it again soon

---

### Post by Bwyan on 2009-07-01
> **rockerZ71 said:**
> I have a Via Epia M10000 that I am trying to set up as a MythTV system.  I installed mythbuntu a few weeks ago and today upgraded to intrepid (to see if it would help any of my problems).  My biggest issue is that when I try to play video files off CD or the hard drive, the system completely locks up.  Sometimes its almost immediately, other times I can watch maybe 10 minutes or more before it happens.  No clues in any logs.  This is not just through mythtv;  I just tried starting an X session and running mplayer and it froze.  I can play DVDs.  Any ideas?

Thanks

I had the same problem and found a solution that worked for me.

I made a guide that you can find here: [http://bwyan.dk/?p=374]("http://bwyan.dk/?p=374")

---

### Post by rockerZ71 on 2009-07-01
Thanks a lot!  I have had that project on the back burner for a while now so I will blow the dust off of it and see if it works for me.

---

