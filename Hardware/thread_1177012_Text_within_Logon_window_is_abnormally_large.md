---
title: "Text within Logon window is abnormally large"
date: 2009-06-02
forum: Hardware
---

### Post by jus71n742 on 2009-06-02
I have just delt with this issue for some time and now I am just over it to the point I wish to fix it.  When I boot into Ubuntu I have your usual log in screen.  The problem comes when I begin to type, as I do so the text is well MASSIVE and you can't read anything you have put in.  I have gone back to my original post about this and the xorg.conf files produces the following.
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```
I am pretty confused as to what could cause this.

---

