---
title: "UBUNTU 23.10 - Keyboard backlight not working"
date: 2023-11-12
forum: Hardware
---

### Post by melion2309 on 2023-11-12
Hello everyone!

Brand new Ubuntu user here (and an aspiring - soon to be full stack developer hopefully). :-)

I just installed **Ubuntu 23.10** and I noticed that the keyboard lights of my Acer Nitro AN515/57 no longer works.

I have tried to do some research on the internet but I cannot seem to find an appropriate solution for this problem.

I hope that you can help you. 

Thanks, 
Mel.

---

### Post by #&amp;thj^% on 2023-11-12
Have you tried key combo>>[Fn + space bar]
The [Fn] key will need to be pressed and held while a tap or two on the space bar lights the backlight.

---

### Post by melion2309 on 2023-11-15
Hey! Yes - I tried but still doesn't work. :/

---

### Post by jeremy31 on 2023-11-15
What result for ```
ls /sys/class/backlight
```

---

### Post by Yellow Pasque on 2023-11-15
[https://medium.com/@prabhatmaurya907/how-to-make-your-acer-nitro-5-linux-ready-2821ea23cd81](https://medium.com/@prabhatmaurya907/how-to-make-your-acer-nitro-5-linux-ready-2821ea23cd81)

---

### Post by priyanshjs on 2024-02-02
> **Yellow Pasque said:**
> [https://medium.com/@prabhatmaurya907/how-to-make-your-acer-nitro-5-linux-ready-2821ea23cd81](https://medium.com/@prabhatmaurya907/how-to-make-your-acer-nitro-5-linux-ready-2821ea23cd81)

the link you provided above gives a 410 page

---

### Post by nobrainghost on 2024-10-31
Try this
cd /sys/class/leds
list all with ls
check the folder in the format "input{number}::scrolllock
the folder with the highest number is normally the one that works.
cd into it, example "cd input8::scrolllock"
run "sudo nano brightness"
Delete the value there and change it to a 1
save and exit, your RGB should be on

---

### Post by nobrainghost on 2024-10-31
Try this
cd /sys/class/leds
list all with ls
check the folder in the format "input{number}::scrolllock
the folder with the highest number is normally the one that works.
cd into it, example "cd input8::scrolllock"
run "sudo nano brightness"
Delete the value there and change it to a 1
save and exit, your RGB should be on
or just run
cd /sys/class/leds && ls && cd $(ls -d input*::scrolllock | sort -V | tail -n 1) && sudo nano brightness

---

