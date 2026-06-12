---
title: "Cannot drag windows onto 2nd monitor"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by joels on 2007-07-10
Okay, I finally got my two video cards to work - my geforce 4 mx440 and my riva 128 (both nvidia). The geforce is using nvidia drivers, the riva is using the nv drivers.
So the desktop displays on both monitors, and I can move the mouse between them, but for some reason I can't drag windows from the geforce 4 mx440 screen (screen0 - the default) to the riva screen (screen1). I'm a newbie to linux and all, and any help will be most appreciated. Thanks.

---

### Post by renatoc8 on 2007-07-10
Hello, that is the default configuration of the Nvidia driver. Try this:

1) login as root (you can probably sudo it in the terminal but I forgot the command to bring up the Nvidia Config app), click on Applications -> System Tools -> NVIDIA X Server Settings.

2) Click on X Server Display Configuration

3) Now, here you have 2 options, you can use TwinView and have it act like the default Windows dual-monitor set-up. Or you can Enable Xinerama, which makes X use both of your monitors as one big monitor.

  TwinView:
     Click: Configure... under the Display label, and choose "TwinView"

   Xinerama:
     Check Enable Xinerama

4) Click "Save to X Configuration File"

5) Restart.

You can experiment with the 2 modes and find the one you like best. 
Hope this helps!

 -Renato

---

