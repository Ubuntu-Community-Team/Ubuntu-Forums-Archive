---
title: "direct rendering: No"
date: 2008-06-08
forum: Hardware
---

### Post by james.paige on 2008-06-08
Hey Guys,

I have an ATI Radeon X600 128mb video card.

I play WOW and other games fine as this is plenty enough to run them.

I'm trying to setup WOW in linux through wine using this document:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

As you notice the first step is to run

glxinfo | grep rendering

and it should come up yes.

Mine comes up No.

Do I have the wrong video drivers installed?

Is there a command I can run that lets me know what drivers I have?

Any help would be great thanks.

- Jimmy

---

### Post by xfceuser on 2008-06-08
```

glxinfo | grep vendor

```

shows which driver vendors you are using.
i had a similar problem that solved it here (altough my ati was older but it may work for you also):

[http://ubuntuforums.org/showthread.php?t=814518](http://ubuntuforums.org/showthread.php?t=814518)

---

### Post by nickdbliss on 2008-06-08
Seems like you are using open driver for ATI. For enabling direct rendering you have to tweak your xorg.conf file. Or alternatively try installing Closed drivers by selecting System>Adm>Restricted Hardware Drivers and enable. Thx

---

