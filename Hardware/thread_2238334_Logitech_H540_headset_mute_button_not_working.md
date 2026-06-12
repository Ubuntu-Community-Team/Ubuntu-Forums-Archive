---
title: "Logitech H540 headset mute button not working"
date: 2014-08-07
forum: Hardware
---

### Post by rcano on 2014-08-07
Hi,

I'm using a Logitech H540 USB headset with Ubuntu 14.04 64 bit and it works perfectly. Audio is good, microphone works, volume side buttons work, but mute side button does not work.

When I press the button I see a red light in the USB cable coming from the headset going red, but nothing happens.

I've tried xev to see if I was receiving an event from that button but I see nothing.

Is there any other way of checking if the headset is generating an event to the OS?

Thanks in advance,
Roberto

---

### Post by eric-desrochers-z on 2014-10-31
Hi rcano,

I plan to buy the logitech H540 headset for my laptop running 14.04 (trusty) did you figure out the problem with the mute button ? Do you recommand me to buy it or you sugget me another model ?

---

### Post by rcano on 2014-11-01
Hi Eric,

I couldn't solve the problem. The headphones are in fact really good, but couldn't find the way to make the mute work. It is not even recognised by X event system. The headphones were given to me by my company, so I'm stuck with them. I haven't tried others. If you don't mind much about the mute, the rest works like a charm.

Good luck!

---

### Post by eric-desrochers-z on 2014-11-02
Hi Roberto,

I bought the H540 headset and it works like a charm, thanks for the good advice.
The mute button work for me without doing any thing in particular to make it work, if you want we can work this out together by comparing my OS configuration and yours to hopefully make your mute button works too.

$ uname -a
Linux macbuntu 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

---

### Post by rcano on 2014-11-03
Hi Eric,

Great to hear that! This is my conf:

$ uname -a
Linux cylon 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"


As you can see, exactly the same. Have you installed any additional drivers for it? I'm trying to use the mute feature mainly with Skype, but anyway I see that in System settings->Sound the mute button is doing nothing. However the red light on the headphones is going on and off (I can imagine it is hardwired to the button).

Thanks for your help!

---

