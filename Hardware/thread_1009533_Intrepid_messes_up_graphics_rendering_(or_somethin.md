---
title: "Intrepid messes up graphics rendering (or something to that effect)."
date: 2008-12-12
forum: Hardware
---

### Post by JasonSpradlin82 on 2008-12-12
I've had a troublesome problem since installing Intrepid.  I rather like Intrepid, but I've been having major video glitches.  I'm using a Toshiba Satellite R15-S822.

```
$ glxinfo |grep direct
direct rendering: Yes
```

```
$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

Now, it is difficult for me to reproduce the error, but put simply, individual windows will, at times, appear to have their horizontal sync out (like on an old television) -- it looks like the content of the window has been twisted horizontally many times for a few seconds and then it fixes itself.  I believe this might also be the cause of literally awful graphics in Google Earth, but I've found out about the medibuntu googleearth and will try installing that before asking for advice on that.

I have included one screenshot that I was luckily able to get the other day which occured on the "Alt-Tab" window switcher... it would get stuck in that horizontal sync for the first thumbnail and cause everything behind the switcher to blink on and off quickly.

---

