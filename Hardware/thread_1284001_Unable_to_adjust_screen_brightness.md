---
title: "Unable to adjust screen brightness"
date: 2009-10-06
forum: Hardware
---

### Post by Shamess707 on 2009-10-06
I have a gateway m-series laptop, and I just recently installed ubuntu 9.04 (x64) in attempts to broadening my OS use. For the most part this is working great, but my current issue is with my screen brightness. When attempting to adjust the brightness either through ubuntu or on my keyboard(fn+up or down) ubuntu shows that I am adjusting the brightness but there is no actual change. Any help would be greatly appriciated

---

### Post by urmish on 2010-04-22
try this

echo -n 20 > /proc/acpi/video/GFX0/DD03/brightness 

here 20 is the % brightness
set it up to anything you like till 100

you might have to do 
sudo su
for this

---

### Post by tomjennings on 2010-05-20
I'm having the same problem with a Samsung x460, has the Intel Mobile Series 4 (07) chipset. 

There are a number of threads about this chip, most people give advice like yours, poking a value into /proc, but does nto work here. I brute-furce tried DD01..DD05.

But here's an odd one: I get a write error if I do
```

echo -n 30 > /proc/acpi/video/GFX0/DD03/brightness 

```

but no error if I use:
```

echo -n 20 > /proc/acpi/video/GFX0/DD03/brightness 

```

Various other values fail/succeed., but none change screen brightness which on my machine is unusably dim. I may have to switch back to Win7 simply for screen brightness!


> **urmish said:**
> try this

echo -n 20 > /proc/acpi/video/GFX0/DD03/brightness 

for this

---

