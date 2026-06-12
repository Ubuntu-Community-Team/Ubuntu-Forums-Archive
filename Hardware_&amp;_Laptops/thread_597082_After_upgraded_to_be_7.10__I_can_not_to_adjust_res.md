---
title: "After upgraded to be 7.10  I can not to adjust resolution to 1024X768"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by noname2 on 2007-10-30
After I upgraded to be 7.10 I can not to adjust resolution to 1024X768
It's very dim , screen is blink all time and some area not clear. I solve the problem by adjust to 800X600
It's OK but I don't this resolution I prefer 1024X768

Last week I used 7.04 and I can use 1024X768 It's OK no dim no blink. 
Why I upgraded to 7.10 this problem appear with me.

I use Compaq Evo N800v It's labtop. How to solve this problem. Thank you :):):)

[[IMG]http://img81.imageshack.us/img81/8599/screenshot1lg7.png[/img]](http://imageshack.us)

---

### Post by por100pre1 on 2007-10-31
Try selecting the driver for your video card manually using your card model number as a reference. This command should take you there:

```
gksu displayconfig-gtk
```

If you don't know the exact number model of the video card use this:

```
hal-device-manager
```

---

