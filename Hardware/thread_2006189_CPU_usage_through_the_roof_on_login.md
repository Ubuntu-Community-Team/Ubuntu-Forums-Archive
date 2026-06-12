---
title: "CPU usage through the roof on login"
date: 2012-06-18
forum: Hardware
---

### Post by ejordanholidayedition on 2012-06-18
This just started a couple days ago- as soon as I log in to any of my desktop environments the system monitor looks like this:

[IMG]http://ubuntuone.com/21S6nhZvWP01TXMxyTizMG[/IMG]

but the processes tab looks like this:

[IMG]http://ubuntuone.com/7mi65fwsJrVARk23nRukI3[/IMG]

What is going on and can i fix it?

---

### Post by ejordanholidayedition on 2012-06-18
Also, it's a Lenovo y560p laptop.  Have Ubuntu 12.04 with cinnamon 1.04 installed

---

### Post by typhoon_tip on 2012-06-19
Post the output of (when the CPU is sky high loll):
```
top
```

The System Monitor is not showing the process that is using your CPU, but top will.

---

### Post by vasa1 on 2012-06-19
I see something similar. I guess it's something that could be turned off in the start-up menu. I haven't bothered finding out what because things return to normal pretty quickly.

---

### Post by ejordanholidayedition on 2012-06-19
Thanks!  I didn't even know about the top command, it turns out it was whoopsie and kworker going crazy.  Read around a little, and kworker will use a lot of cpu on some computers when the battery isn't fully charged or when running on battery power.  As for whoopsie i just had to disable the crash reports to Ubuntu and it stopped.

[http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-can-i-remove-it]("http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-can-i-remove-it")

All normal once more, thanks again for the help!

---

### Post by m_duck on 2012-06-19
For a more aesthetically pleasing top, try htop.

---

