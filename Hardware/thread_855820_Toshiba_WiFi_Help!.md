---
title: "Toshiba WiFi Help!"
date: 2008-07-10
forum: Hardware
---

### Post by Toshibawarrior on 2008-07-10
Hello guys, 

Well I've been using Ubuntu for a while now, and I've come across a few problems, that could be fixed. But as far as my laptop's wifi goes...hmmm...

I have a Toshiba Satellite A135 S4527 as my signature states...everything works except the dual monitor thing (S-Video out only works in clone output mode) but that's besides the point.

What I really need help with is my wifi card which an Atheros AR242x (I ran "lspci" on the terminal and gave back that output). I can actually connect to the internet and my wireless card works flawlessly. EXCEPT for the power button not working.

Back in Vista if I wanted to save battery power I could turn off the wifi card with the power button (on front of the laptop of course). But now in Ubuntu it doesn't seem to work. If I turn it off it just keeps working normally and consuming battery.

So any help toward this issue will be greatly appreciated! If any more info is needed please let me know.

Thanks in advance! :):popcorn:

---

### Post by Daelyn on 2008-07-11
> **Toshibawarrior said:**
> Hello guys, 

Well I've been using Ubuntu for a while now, and I've come across a few problems, that could be fixed. But as far as my laptop's wifi goes...hmmm...

I have a Toshiba Satellite A135 S4527 as my signature states...everything works except the dual monitor thing (S-Video out only works in clone output mode) but that's besides the point.

What I really need help with is my wifi card which an Atheros AR242x (I ran "lspci" on the terminal and gave back that output). I can actually connect to the internet and my wireless card works flawlessly. EXCEPT for the power button not working.

Back in Vista if I wanted to save battery power I could turn off the wifi card with the power button (on front of the laptop of course). But now in Ubuntu it doesn't seem to work. If I turn it off it just keeps working normally and consuming battery.

So any help toward this issue will be greatly appreciated! If any more info is needed please let me know.

Thanks in advance! :):popcorn:


Seems like the action by the key/switch aint identified.

Push/switch button once and post output of
```
 dmesg | tail 
```
If it's a switch, switch back and post the new output (two actions).

This hopefully will identify the key, and how the system identifies the action, if it at all does.

If "dmesg | tail" doesn't change after key/switch action, I guess some more experienced linux guy will have to look into this.

---

### Post by Toshibawarrior on 2008-07-11
Thanks for your quick reply...but sadly it didn't change...

It is  a switch, so in the "on" position the output is:

```
ivan@ivans-laptop:~$ dmesg | tail
[  104.529374]  domain 0: span 03
[  104.529376]   groups: 01 02
[  104.529379]   domain 1: span 03
[  104.529381]    groups: 03
[  104.529383] CPU1 attaching sched-domain:
[  104.529385]  domain 0: span 03
[  104.529387]   groups: 02 01
[  104.529390]   domain 1: span 03
[  104.529392]    groups: 03
[  123.428493] ath0: no IPv6 routers present
```

On the "off" position it is:

```
ivan@ivans-laptop:~$ dmesg | tail
[  104.529374]  domain 0: span 03
[  104.529376]   groups: 01 02
[  104.529379]   domain 1: span 03
[  104.529381]    groups: 03
[  104.529383] CPU1 attaching sched-domain:
[  104.529385]  domain 0: span 03
[  104.529387]   groups: 02 01
[  104.529390]   domain 1: span 03
[  104.529392]    groups: 03
[  123.428493] ath0: no IPv6 routers present
```

---

### Post by Toshibawarrior on 2008-07-12
BUMP...anyone?...please...?

---

### Post by Toshibawarrior on 2008-07-13
Hello?...Can anyone help me?...

---

