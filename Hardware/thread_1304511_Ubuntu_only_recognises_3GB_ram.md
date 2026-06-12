---
title: "Ubuntu only recognises 3GB ram"
date: 2009-10-29
forum: Hardware
---

### Post by karimruan on 2009-10-29
For some reason, can't remember how I got thsi info, but ubuntu is only recognizing 3 GB RAM out of 4GB. Any ideas?

---

### Post by Wiebelhaus on 2009-10-29
Your using the 32bit image , if you have a 64bit CPU , Download the 64bit Image.

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by karimruan on 2009-10-29
That's okay, I would rather not have to do another install. 3GB ram is fine with me then. I have things (finally) the way I like it!

---

### Post by Giblet5 on 2009-10-29
It's a numbers thing.

32 bits allows for 2³² memory address space = 4G

Your PC maps about 1G for PC hardware (depends heavily on video card memory).

Windows has this thing called PAE that you can't easily access. It trades about half of the performance for that extra 1G.

2 to the 64th is a much bigger number.

---

### Post by karimruan on 2009-10-29
That makes sense. Glad I don't run windows anymore! Thanks everyone!

---

