---
title: "T530 Sound Issues"
date: 2012-12-31
forum: Hardware
---

### Post by iamnoahc on 2012-12-31
I'm currently having issues getting my sound to work.  I've read others have had luck with upgrading their kernel and I've done that:


   ```
 noahc@blackbox:~$ uname -r
    3.7.0-030700-generic
```


I get this for output:

    ```
noahc@blackbox:~$ sudo aplay -l
    **** List of PLAYBACK Hardware Devices ****
    card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
     Subdevices: 1/1
     Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
     Subdevices: 1/1
     Subdevice #0: subdevice #0
```
and

```
noahc@blackbox:~$ alsamixer
cannot open mixer: No such file or directory
```

You might find: [http://www.alsa-project.org/db/?f=93ba04342d5b6aad4fb080434dc1dcc7d7528656](http://www.alsa-project.org/db/?f=93ba04342d5b6aad4fb080434dc1dcc7d7528656) useful as well.


I've read that others have had luck with plugging in a set of headphones, which I have tried and had no such luck.

Any ideas on how to move forward with this?

---

### Post by iamnoahc on 2012-12-31
I got it fixed by following this:

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)

---

