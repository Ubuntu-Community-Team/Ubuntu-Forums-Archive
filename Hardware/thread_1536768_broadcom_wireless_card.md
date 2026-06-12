---
title: "broadcom wireless card"
date: 2010-07-22
forum: Hardware
---

### Post by themordy on 2010-07-22
i know this has been talked about, but nothing i read makes any sense to me, or i get halfway though and don't get the results i'm told i will. can anyone tell me in simple, easy to understand, step-by-step instructions how i might get my broadcom wireless card working on my dell inspiron 1300?

---

### Post by snowpine on 2010-07-22
The Ubuntu Wiki page is really good:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The most important command is the first one:

```
lspci -vvnn | grep 14e4
```

That will tell you exactly which card you have. Armed with that information, you can skip ahead to the relevant section of the wiki page.

ps Welcome to the forums!

---

### Post by themordy on 2010-07-22
okay now i have an even bigger problem. i followed another guide that told me to remove all current broadcom drivers first. i think it deleted my lan card as well. i just rebooted and now autoeth0 won't connect either so i have NO internet connection and can't seem to get it working at all wired or wireless

---

### Post by themordy on 2010-07-23
alright, so i downloaded the iso image on another computer and made a disk. then i booted up my laptop with the cd in the tray. went to System>Administration>Hardware Drivers and reinstalled my drivers. suddenly, not only do i have a network connection again, but my wifi works as well. so, happy ending here. thanks for the help!

---

