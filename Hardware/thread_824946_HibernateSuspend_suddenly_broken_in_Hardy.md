---
title: "Hibernate/Suspend suddenly broken in Hardy"
date: 2008-06-10
forum: Hardware
---

### Post by Hylian7 on 2008-06-10
Something weird is going on here. I clean installed Hardy on my Toshiba A135-S2266 Laptop and everything was working fine. I got all the updates and my Hibernate and Suspend worked, for a bit. Then all of a sudden, both quit working. I tried the solution of temporarily enabling hardy-proposed and got the -19 kernel. That had no effect on my problem. I know there has to be some way for my hibernate and suspend to work, because it was working before, so "your hardware doesn't support it" is not the answer. I've Googled this a million times to no avail. Does anyone have a solution, or even a guess? Thanks in advance.

---

### Post by NJC on 2008-06-10
FWIW I've also lost the ability to Suspend with kernel -18. Can you run -17 or -16?

---

### Post by Hylian7 on 2008-06-10
I have tried -16, I do not have -17. Hibernate and suspend do not work on the -16 kernel for me anymore. They did before though.

---

### Post by mariner09 on 2008-06-10
Can you define the "does not work" details?

Does it try to suspend or hibernate and come right back to a log in or your desktop?

Does it suspend and not resume?

Does it hibernate and not power off?

---

### Post by Hylian7 on 2008-06-11
My apologies for not explaining properly.

Basically, my computer suspends or hibernates normally. Then, when I try to wake from suspend, the screen is black. The backlight does not come on, typing my password and hitting enter does nothing either. As for hibernate, it freezes on the Ubuntu boot splash screen. Let me know if you need any more info.

---

### Post by Hylian7 on 2008-06-11
I solved it. In the "MODULES=""" section of /etc/default/acpi-support, I needed to put "usbcore." This was because I had a cooling pad plugged in for my laptop, and as soon as I unplugged it work. Apparently the USB module did not unload, so that was the problem.

---

### Post by yyka on 2008-06-13
hello, can you explain in detail this :

 I needed to put "usbcore."

where you write or put "usbcore"? 

thanks

---

### Post by pedrogfrancisco on 2008-06-13
> **Hylian7 said:**
> I solved it. In the "MODULES=""" section of /etc/default/acpi-support, I needed to put "usbcore." This was because I had a cooling pad plugged in for my laptop, and as soon as I unplugged it work. Apparently the USB module did not unload, so that was the problem.



He meant, open a console and type:
```

sudo nano -w /etc/default/acpi-suport

```
scroll down until you see something like
```

MODULES=""

```
and add "usbcore" there as in
```

MODULES="usbcore"

```

---

### Post by Hylian7 on 2008-06-13
Pedrog's got it right. The only difference was I used gedit.

---

### Post by yyka on 2008-06-13
ok thanks for your response all :D

---

