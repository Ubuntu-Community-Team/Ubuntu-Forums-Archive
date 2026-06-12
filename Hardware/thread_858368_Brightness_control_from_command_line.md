---
title: "Brightness control from command line"
date: 2008-07-13
forum: Hardware
---

### Post by retrow on 2008-07-13
Brightness of my Toshiba Satellite can't be controlled with the Fn keys provided. After searching through some guides I was able to find a way to control the brightness by passing values from terminal.

Like this -
```
echo -n 70 > /proc/acpi/video/VGA/LCD/brightness
```

However it wasn't working when I used a number larger than 70 (help guides said you can vary it between 0 and 100).

I decided to check the contents of the brightness file, and this is what I got.
```
root@tungsten:~# more /proc/acpi/video/VGA/LCD/brightness 
levels:  70 40 0 10 20 30 40 50 60 70
current: 70
```

I am however unable to append that file since it is recognized as a binary file by the system, or so it says when I try to open it with gedit or nano.

Now is there a way to append more values to the brightness file so that I can actually vary it between 0 and 100?

Thanks.

---

### Post by sdennie on 2008-07-13
The values in /proc/acpi are usually coming directly from the acpi.  It's possible that those values don't correspond to 0% to 70% but instead just represent 8 different brightness levels.  If you don't have another OS to contrast with, I think you'll have to assume that setting it to 70 means max brightness.

---

### Post by retrow on 2008-07-14
Thanks vor. I'm glad that its at least changing the brightness levels.
Phoenix BIOS is absolutely terrible.

---

