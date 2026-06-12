---
title: "Dell Latitude D630 LED Control"
date: 2009-07-24
forum: Hardware
---

### Post by mju4t on 2009-07-24
Hello

I am trying to make my bluetooth LED blink when I get a new email in checkgmail.  I cannot find where the LED control file is.  I've looked on the internet and supposedly it can be found in /sys/class/led but the directory /led does not exist.  Do any Dell Latitude D630 users out there know where I can find this elusive file? 

Thanks!
Alex

---

### Post by pajus on 2010-03-10
I have same problem with my vostro 1320
it is
/sys/class/leds
ia have directory mmc0:: in it

if i do "echo 1 > brightness" nothing happend :(
it looks like nothind that i change in this works

---

