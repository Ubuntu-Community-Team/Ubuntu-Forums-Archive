---
title: "Hibernation problem on HP Pavilion X360"
date: 2018-02-26
forum: Hardware
---

### Post by danjde on 2018-02-26
Hi friends,
my laptop Pavilion X360, suspend fine, but if I try to hibernate, all seem to work fine but at the and of resuming the computer freeze totally, and only an hard reboot can unlock the situation!
Could you suggest me if there any way for debugging or if exist some special configuration for this laptop?

Many many thanks!

Davide

---

### Post by #&amp;thj^% on 2018-02-26
Not enough information to give you a smart answer.:(
What Version Ubuntu are you using?
Ram and Swap are also important here!
So to start to help get the ball rolling here for you, Paste back the return of these commands:
```
free
```
And:
```
lsb_release -a
```
And while you wait for someone to jump in and help, have a read here: [https://websiteforstudents.com/enable-hibernation-ubuntu-17-10-desktop/](https://websiteforstudents.com/enable-hibernation-ubuntu-17-10-desktop/)
BTW Hibernation works fine here: But This feature is not very stable with Ubuntu machines.. so it was disabled by default.
```
Machine:   Device: desktop System: HP product: 750-417c v: 1.01 serial: N/A
           Mobo: HP model: 828A v: 1.01 serial: N/A
           UEFI [Legacy]: AMI v: F.14 date: 09/19/2016

```
Good Luck :)

---

### Post by kerry_s on 2018-02-26
hibernate is not recommended, which is why its disabled on most linux systems. a clean boot is just as fast.

---

