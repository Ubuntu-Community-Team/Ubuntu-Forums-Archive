---
title: "How to find out which hardware i have"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by popeye on 2007-06-26
Hi,

I have a Fujitsu-Siemens Amilo Pro V3515. I have installed feisty from the livecd and got into some trouble. The screen resolution was not detected properly, but i have solved it for the time being. Still i like to optimise it and therefore i like to know how to find out which videocard i have. I have selected vesa in the configuration questions. The right one?
I have found the command:
```
lshw
```
but i have no clue how to interpreted it.

---

### Post by avik on 2007-06-26
I like to output it to an HTML file:

```
lshw -html > hw.htm
```

then open in a browser.  It's easier to interpret because of the distinct boxes setting each piece of hardware apart.

---

