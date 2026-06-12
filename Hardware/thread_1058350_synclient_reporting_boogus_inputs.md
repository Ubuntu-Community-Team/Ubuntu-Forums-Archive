---
title: "synclient reporting boogus inputs"
date: 2009-02-02
forum: Hardware
---

### Post by mzakharo on 2009-02-02
Hi - I am having troubles with my synaptics touchpad. Everything works well, except for the fact that my touchpad seems to be reporting non existing events as noted by synclient output. Here is the output of synclient -m 100 command.```
   2.506  3776 2381  63 1  4  0 0 0 0 0  00000000   0  0  0   0   0
   2.607  3778 2378  34 1  4  0 0 0 0 0  00000000   0  0  0   0   0
   2.707     1 5855   1 2  5  0 0 0 0 0  00000000   0  0  0   0   0
   2.907     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   4.307  3952 2753  55 1  4  0 0 0 0 0  00000000   0  0  0   0   0
   4.408  3964 2765  62 1  4  0 0 0 0 0  00000000   0  0  0   0   0
   4.508  3971 2772  63 1  4  0 0 0 0 0  00000000   0  0  0   0   0
   4.608  3970 2770   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   4.708     1 5855   1 2  5  0 0 0 0 0  00000000   0  0  0   0   0
   4.908     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   6.109  3775 2600  10 1  5  0 0 0 0 0  00000000   0  0  0   0   0
   6.209  3797 2655  61 1  4  0 0 0 0 0  00000000   0  0  0   0   0
   6.309  3802 2650  63 1  4  0 0 0 0 0  00000000   0  0  0   0   0
   6.409     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   6.509     1 5855   1 2  5  0 0 0 0 0  00000000   0  0  0   0   0
   6.609     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0

```
As you may notice, after I let go the touch-pad, the last two or three output lines produce extra events at 1, 5855 location on my touch-pad, which indeed is beyond my touch-pad boundaries. The amount of erroneous data is random, and varies from push to push. The problem is that this severely affects my scrolling, as pages continue to scroll even after I let go the finger. I thought of trying to modify the source code by forcing the driver to ignore input at location 1, 5855, but I am not sure where to start, or whether this is an optimal solution. If anyone could generously provide with some insight, the effort is greatly appreciated.

---

