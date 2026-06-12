---
title: "/etc/rc.d/rc.keymap equivalent"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by tmussche on 2007-07-11
I installed Ubuntu 7.04 on a NEC laptop. The keyboard is the standard US keyboard except for one key. I found a website of a user with the same laptop but running slackware. 

[http://65.78.2.122:8080/~jesse/NEC.html](http://65.78.2.122:8080/~jesse/NEC.html)

He gives solutions to the problem for the X server and for the terminal. The X server solution works, but his terminal solution is the following:

> In Slackware, put the following commands in /etc/rc.d/rc.keymap.

    loadkeys << EOF
    keycode 86 = backslash
    shift keycode 86 = bar
    EOF
    

Make sure the file is executable. For other distributions, you want to put those commands in whatever scripts are executed at startup.

Now i can't find the /etc/rc.d/rc.keymap file, does anyone know the equivalent file in Ubuntu? So where do i have to put this code such that at startup this key gets remapped properly?

Thanks in advance!

Tim

---

