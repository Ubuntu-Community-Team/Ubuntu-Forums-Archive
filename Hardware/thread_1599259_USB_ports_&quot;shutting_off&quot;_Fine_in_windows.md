---
title: "USB ports &quot;shutting off&quot;? Fine in windows"
date: 2010-10-17
forum: Hardware
---

### Post by Garandir on 2010-10-17
I've had many problems with USB ports on all distros. I can use anything fine on Windows 7, no problems. However, on Linux, they seem to "shut off" after 5 - 10 minutes. What happens EVERY TIME is the mouse freezes, then the keyboard. If I unplug and plug them back in, they will flash (keyboard is backlit, mouse has illuminated scroll wheel), and go black, like they are receiving no power from the USB ports. It happens with other keyboards and mouses, and still happens if I switch them after the problem occurs. This only happens to this one computer, but like I said, they work fine on Windows. I've tried:
Ubuntu 9.10
Ubuntu 10.04
Ubuntu 10.10
Fedora 12
A Linux Mint version I do not remember

----------------------------------------------------------------------------------------------------------------------------------

I know this thread is extremely old, but I'm updating with the solution for the sake of anyone else who may have my troubles. After posting on other forums, someone gave me a link to the foxconn motherboards & issues with linux. Using iasl, I decompiled the DSDT table, and recompiled to find errors. 2 errors and one warning. I googled both the errors, found fixes, applied them, and recompiled the DSDT into a hex. Everything I did after that can be found here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by JackNocturne on 2010-10-17
When that happens, can you post the output of **dmesg** command in terminal here :)

---

### Post by Garandir on 2010-10-17
Sure, but is there a shortcut key for terminal?

---

### Post by JackNocturne on 2010-10-17
I usually have the shortcut created on my desktop, i don't know a default quick shortcut.

---

### Post by Garandir on 2010-10-17
I can try, but I don't know how I'm going to copy the whole output without a mouse..

---

### Post by Garandir on 2010-10-17
This looks like an error to me, it's the last part of the output:
clocksource tsc unstable (delta = -272717895 ns)

---

### Post by JackNocturne on 2010-10-17
you could try redirecting the output to a file
```
dmesg > filename.txt
```

---

### Post by Garandir on 2010-10-17
This is no fun without a mouse. I think I did it right.

---

### Post by Garandir on 2010-10-17
Txt was too big, had to put it in a doc

---

### Post by Garandir on 2010-10-17
Bumpity bump.

---

### Post by JackNocturne on 2010-10-18
By the way what laptop/PC are you using?

---

### Post by Garandir on 2010-10-18
Gateway GM5084 with a few non factory parts.

---

### Post by Garandir on 2010-10-18
Can anyone figure out my problem from the dmesg output I posted?

---

### Post by Garandir on 2010-10-18
I'll be online for a good 5 hours if someone has any idea.

---

### Post by Garandir on 2010-10-18
Come on, we were getting somewhere.

---

### Post by Garandir on 2010-10-19
Still looking for help...

---

### Post by Garandir on 2010-10-20
](*,) bump..

---

### Post by Garandir on 2010-10-20
Read about disabling legacy usb support in BIOS, going to try it.

---

### Post by Garandir on 2010-10-20
The BIOS was already set with that option, so I tried adding noapic and nolapic to GRUBs boot list. I've been running about 15 minutes with no issues so far, a good sign.

---

### Post by Garandir on 2010-10-20
Nevermind the last post, it's still doing it. Help would be appreciated.

---

### Post by JackNocturne on 2010-10-20
You know what? The problem might be a bug, maybe thats why a lot of people don't know how to solve it.
 Last place to check is (System>Administration>System Testing) ,you'll go through a series of tests,its easy to see there what faulty hardware(or software bug) is the culprit.

---

### Post by Garandir on 2010-10-21
Thanks for the reply. I have a dentist appointment in 20 minutes, but I'll do it when I come back.

---

### Post by Garandir on 2010-10-21
It said the mouse test failed.
EDIT: Ok, since I have a different USB mouse, I'm going to reinstall Ubuntu using that mouse..

---

