---
title: "Slow keyboard response/loud fan"
date: 2008-10-22
forum: Hardware
---

### Post by heimo11656 on 2008-10-22
Hello. I've been using ubuntu hardy successfully on my labtop for about 3 months now. All of a sudden, I bring my labtop back from suspend mode, and an unusual set of symptoms appears- all at once.

-The fan is as loud as it gets

-The keyboard is very slow to respond to my presses, I need to wait half a second between keys or it won't register.

-slowkeys option is not on

-The touchpad is very slow to respond, though attatching a USB mouse is fine


I appreciate any help, as I found no one else with this weird and sudden set of symptoms.

---

### Post by heimo11656 on 2008-10-22
I forgot to mention that this is a Dell Studio 15 Labtop. I also made another observation:

-When the labtop is in sleep mode, the LED blinks. Now with this sudden onset of problems, it blinks waaaaay slower in sleep mode.

-The system is not slow, just feels like it because keyboard+touchpad response is.

Basically a problem has sprouted with the keyboard, touchpad, and fan all at the same time... what could cause this?

---

### Post by bobyy on 2008-10-22
1 try to see how much RAM is used 
2                     CPU is used
3 see witch process is sloving down the system
4 see logs or dmesg

perhaps is a ACPI problem...

---

### Post by heimo11656 on 2008-10-22
RAM and CPU usage are just fine, I always have monitors for them on taskbar and there is nothing unusual. No process taking up much memory.As I said, the system itself is not running slow at all.

What should I be looking for in logs?
What is dmesg?
What is ACPI?

There are a lot of ACPI related messages in the log, but I don't understand them.

---

### Post by teaker1s on 2008-10-22
try in terminal 
```
top
```

---

### Post by heimo11656 on 2008-10-22
This is my result:

[[IMG]http://img406.imageshack.us/img406/7539/screenshotir8.png[/IMG]](http://imageshack.us)
[[IMG]http://img406.imageshack.us/img406/screenshotir8.png/1/w1259.png[/IMG]](http://g.imageshack.us/img406/screenshotir8.png/1/)

---

### Post by heimo11656 on 2008-10-23
I found that my keyboard is also slow-responsive in my BIOS menu. Does this mean that the problem has nothing to do with ubuntu?

---

### Post by heimo11656 on 2008-10-23
Problem Solved!

It was very... weird. Well, I decided this could have been a hardware problem. So I opened up my labtop (having no experience opening up labtops). And what do I see? A glob of hair and fur just sitting there on my fan. I removed it, popped everything back in, turned it on, and no more fan, keyboard, or touchpad problems!

---

