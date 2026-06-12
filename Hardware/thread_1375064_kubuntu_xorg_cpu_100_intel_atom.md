---
title: "kubuntu xorg cpu 100 intel atom"
date: 2010-01-07
forum: Hardware
---

### Post by max7 on 2010-01-07
I have nettop when I start it works fine but after some time.

xorg start to consume 9%, 30% and finally 99-100% cpu
(I use top and ps auxf to check it)

I found that many people propose to add
Option "AccelMethod" "XAA"
to xorg.conf but it does not helps

Do you have any ideas how to work arround it?

---

### Post by max7 on 2010-01-07
here is top 
```

19466 root      20   0  422m  90m 5656 R  100  4.6   8:26.91 Xorg
19666 user      20   0  227m  16m 9.8m S    3  0.8   1:20.08 kmix
19956 user      20   0  856m  67m  17m S    2  3.4   2:23.51 chrome
20106 user      20   0  167m  24m  13m S    2  1.3   0:29.59 npviewer.bin
20021 user      21   1  933m 183m  14m S    1  9.3   2:07.25 chrome
19631 user      20   0 19132 1380  968 R    1  0.1   0:24.12 top
 1673 user      20   0  755m  11m 1032 S    0  0.6   2:45.59 java
20146 user      21   1  841m  33m  11m S    0  1.7   0:09.27 chrome
    1 root      20   0 19452 1180  648 S    0  0.1   0:02.20 init

```

---

