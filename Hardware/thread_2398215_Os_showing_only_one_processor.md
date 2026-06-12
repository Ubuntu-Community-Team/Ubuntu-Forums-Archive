---
title: "Os showing only one processor"
date: 2018-08-09
forum: Hardware
---

### Post by hrishikesh-umralia on 2018-08-09
[COLOR=#333333][FONT=&quot]I have 4 core processor but the system is only showing one core,[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Note : I am using acpi=off in grub entry ,If I don't use it, my system chrashes.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]What to do now?[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]output of inxi -C is

```
[/FONT][/COLOR]CPU:       Single core Intel Core i7-7700HQ (-UP-) cache: 6144 KB[COLOR=#333333][FONT=&quot]
[/FONT][/COLOR]
           speed/max: 899/3800 MHz[COLOR=#333333][FONT=&quot]
```
[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-08-09
What does terminal command ```
cat /proc/cpuinfo
``` show as output?

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

