---
title: "Laptop Screen Wont Wake Up after &quot;Screen Off&quot; timeer"
date: 2011-11-22
forum: Hardware
---

### Post by mykrob on 2011-11-22
Running 11.10 on my Lenovo Ideapad Z570.
When the screen turns off from inactivity, it will not come back on, I have to hard power down..

Any ideas? What do you need from me to help troubleshoot?

Thanks,
-myk

---

### Post by matt_symes on 2011-11-22
Hi

> **mykrob said:**
> Running 11.10 on my Lenovo Ideapad Z570.
When the screen turns off from inactivity, it will not come back on, I have to hard power down..

Any ideas? What do you need from me to help troubleshoot?

Thanks,
-myk
> 
 it will not come back on

What is exactly happens ?

Is your computer suspending, hibernating or just blanking the screen when inactive ?

Does this happen on battery power, mains power or both ?

Don't hard reset. Try the magic key combination.

Press and hold alt + sysreq then hitthe keys *r e s i u b* leaving 5 seconds after each key press.

Kind regards

---

### Post by mykrob on 2011-11-22
It is just from screen blanking while inactive. I have disabled automatic hibernate and suspend to isolate the problem. It occurs while plugged in or on battery, the power source seems to make no difference.

I'll set it up to the the key combination a bit later today and reduce the screen blank timer to a few minutes to force it to happen and see what it does.

My desktop, which has an nVidia graphics card, doesn't exhibit this behavior. Wonder if its something to do with the particular intel chipset in this laptop.. But All my previous laptops were intel graphics and never seen this before 11.10.

Thanks, I'll report back once I have more info.

---

### Post by matt_symes on 2011-11-22
Hi

The magic key combination should reboot your PC. You can also switch your PC off with

alt + sysreq r e i s u o

where the last letter is *o*. This is much, much better than a hard reset.

You can help eliminate suspend and hibernate by opening a terminal and typing

```
sudo pm-suspend
```and

```
sudo pm-hibernate
```You will have to enter your password. It will not be echoed to the screen.

To see if the dpms screen blanking is causing your problem, from the terminal again

```
xset dpms force standby
```You can change standby for *suspend*

```
xset dpms force suspend
```*off *

```
xset dpms force off
```and *on*

```
xset dpms force on
```Post back on the results of these commands. Hopefully, this will help to narrow down the problem.

Kind regards

---

### Post by jsiret on 2012-06-07
For anyone who has this problem in the future...

Press FN + [up_arrow]

This will restore the brightness.

---

