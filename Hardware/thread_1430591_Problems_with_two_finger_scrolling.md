---
title: "Problems with two finger scrolling"
date: 2010-03-15
forum: Hardware
---

### Post by CharlesA on 2010-03-15
Hi,

Running Ubuntu desktop 9.10 on my ASUS 1005HA netbook. it seems almost everything works except for two finger scrolling with the touchpad.

I found the thread here: [http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)

But when I ran "synclient VertTwoFingerScroll=1" It set it to "1" but I still cannot use two finger scrolling, since the mouse jumps all over the place.

Any ideas?

Thanks.

---

### Post by Manslen on 2010-03-26
Same problem here. I have found [this thread]("http://ubuntuforums.org/showthread.php?t=1426782#3") suggesting a two-finger emulation but it is no good either.

Running ```
synclient -m 50
``` shows me that the ALPS touchpad does not recognize more than 1 finger, nor does it detect width (so emulation is probably out of the question). Does this mean I have no hope?

I am running a Dell Latitude D630.

Sample reading from the output:

```
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000   843  353   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   1.204   388  441 126 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   1.505   388  431   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   1.805   384  355   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.105   385  352  86 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.705   777  297 119 1  0  0 0 0 0 0  00000000   0  0  0   0   0

```

---

### Post by LieToPurify3 on 2011-06-03
Did you ever find a solution to this? I also have a Latitude D630 and would love to be able to get two-finger scroll working on it.

---

### Post by Erkkimon on 2012-10-05
I'm also having problems with two finger scrolling on Dell Latiude D630. I'm running Ubuntu 12.04.

Any ideas?

---

