---
title: "ATI Radeon HD 5770"
date: 2010-03-31
forum: Hardware
---

### Post by Pressondude on 2010-03-31
Is anyone else having the same problem that I am? I have compositing working, and everything seems to be fine, but I cannot launch Catalyst Control Center (some sort of parsing error in the X.org file) and I have a watermark in the bottom right hand corner of my screen that is the AMD logo and the message "Unsupported Hardware."
My card is the HIS 5770.

---

### Post by RedSingularity on 2010-03-31
You did install the radeon drivers correct?

---

### Post by Pressondude on 2010-04-01
Yes, I used envyng and it was successful.

---

### Post by RedSingularity on 2010-04-01
I believe your card will use the "fglrx" driver.

---

### Post by Pressondude on 2010-04-01
> **RedSingularity said:**
> I believe your card will use the "fglrx" driver.

Envyng is a thirdparty installer that installs fglrx and modifies X.org automatically, rather than the long and difficult manual way.

---

### Post by RedSingularity on 2010-04-01
Ah, can you launch it as root?

---

### Post by Pressondude on 2010-04-02
Launch what? The drivers installed, it's just that CCC won't open, and the hardware is yelling at me. Actually, it appears to be working fine, except for the lack of CCC functionality and the watermark.

---

### Post by RedSingularity on 2010-04-02
Can you launch the control center as root?

---

### Post by Pressondude on 2010-04-02
Again, as previous stated, there's a parsing error. 
```
Parse error on line 9 of section Module in file /etc/X11/xorg.conf
        "Disable" is not a valid keyword in this section.
Parse error on line 9 of section Module in file /etc/X11/xorg.conf
        "Disable" is not a valid keyword in this section.

```

---

### Post by RedSingularity on 2010-04-03
Have you looked at your xorg config file for this "disable" feature?

---

### Post by Pressondude on 2010-04-03
I've never had this problem before, and what exactly would be "disabled"? The whole point is that I want to ENable CCC

---

### Post by RedSingularity on 2010-04-03
I am not sure what is disabled exactly.  We need to look at line 9 of your conf file.

Post the output of 

cat /etc/X11/xorg.conf

We can have a look there.

---

### Post by Pressondude on 2010-04-03
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

```

---

### Post by RedSingularity on 2010-04-03
Delete the section of that file that says 

Disable "dri2"

And save it.  Then try the control center again.

---

### Post by kblft on 2010-04-03
> Code:
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection
__________________

you should try and add a '#' in the beginning of the line that says Disable "dri2"

This appears to be the parsing problem

---

### Post by Pressondude on 2010-04-06
The problem disappears entirely if one installs the drivers directly from ATI. While this is a pain, it works perfectly.

---

