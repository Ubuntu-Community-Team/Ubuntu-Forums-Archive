---
title: "Using Ubuntu to recover old hard drive, but can't see hard drive"
date: 2017-06-07
forum: Hardware
---

### Post by mb5398 on 2017-06-07
Hey my hard drive wasn't working for me anymore getting me stuck in a boot menu/app menu on my lenovo L540. I worked through the steps of fixing the hard drive, but ultimately found that while the hard drive was detected it failed a few of the storage tests as you can see here: [IMG]http://i.imgur.com/zOtZ7Or.png[/IMG]


Because my comp did seem to at least detect my hard drive I downloaded ubuntu on to a usb drive using rufus and this is what I'm using to communicate on this forum now. That being said, when I looked under computer I didn't see my hard drive as you can see below: 
[IMG]http://i.imgur.com/nqWB2jo.png[/IMG]

I know I can use the terminal to potentially find the hard drive, but not sure how.

---

### Post by LastDino on 2017-06-07
```

sudo fdisk -l
```

If it is recognizable, it should be shown for output of this command. 

If not, we might have some problems.

---

### Post by mb5398 on 2017-06-07
After all the ram I get this. Is the sdb the hard drive?
[IMG]http://i.imgur.com/YAumSjU.png[/IMG]

---

### Post by LastDino on 2017-06-07
That is your USB, if your HD was being detected, it would've been listed along with it. Something like /dev/sdb2

It's  time to take the smart test failure seriously. I don't know how to take  backup or recover from this situation, but contacting vendor if under  warranty may be wise.

---

