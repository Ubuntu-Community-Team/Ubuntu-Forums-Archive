---
title: "Home Key Not Working"
date: 2009-07-09
forum: Hardware
---

### Post by glancep on 2009-07-09
I just installed Ubuntu 9.04 and now I am noticing that my "Home" key on my (fairly standard) keyboard is not working.  It does not seem to work in any app.  I let the installer pick a standard US keyboard layout (105 key)... so I don't know what the deal is.  When I press Home in xev, I get the following output:

```

FocusOut event, serial 35, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 35, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

I have not noticed any problems with other keys... End works just fine.

Any ideas?  Thanks...
Gideon

---

### Post by glancep on 2009-07-11
Oops... I figured it out.  I had Kubuntu 8.04 installed prior to moving to Ubuntu 9.04, and it was still using my .xmodmaprc I had created for Kubuntu... apparently someone on my map was redirecting Home to one of my multimedia keys.  I still have no idea why the map wouldn't work when switching from Kubuntu 8.04 to Ubuntu 9.04.  Now I guess I need to recreate it.

---

