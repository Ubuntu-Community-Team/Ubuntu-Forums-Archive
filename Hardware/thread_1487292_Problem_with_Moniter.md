---
title: "Problem with Moniter"
date: 2010-05-18
forum: Hardware
---

### Post by Chaze the Chat on 2010-05-18
Hello! I'm a first time poster. I just got Ubuntu 9.04 today and I was experiencing a little difficulty. It is my monitor. The screen is a little off center and I can't fix it. Any solutions?

Another problem I have is that the res. will only go up to 800 by 600, and I need 1280 by 1024. Any help with that as well will be greatly appreciated. :)

---

### Post by Phrea on 2010-05-18
What type of monitor is it? CRT or TFT?

---

### Post by Chaze the Chat on 2010-05-18
Um, how can I tell?

EDIT: If this helps, I have a Samsung SyncMaster 191TPlus.

---

### Post by Phrea on 2010-05-18
That's a TFT monitor, just so you know.
CRT's are those really big bulky ones which are as deep as they are wide. ;)

Have you installed drivers for your graphics card?
System --> Administration --> Hardware Drivers

---

### Post by Chaze the Chat on 2010-05-18
I have not. I will try it.

EDIT: OK, that was weird. I logged onto Ubuntu, and it sort of fix'd itself, but then when I logged in, the screen went black and a message said, "Video Mode not compatible." Help?

---

### Post by Phrea on 2010-05-18
Hmmm, I only found 1 result on Google with "Video Mode not compatible", and that didn't help at all, that person didn't know what he/she did to fix it...

---

### Post by Chaze the Chat on 2010-05-18
Oh, that sucks.

---

### Post by Chaze the Chat on 2010-05-19
Sorry for double post, but it still won't work

---

### Post by realzippy on 2010-05-19
Did you install -as suggested- a driver before error occurred?If so,which one?

---

### Post by Chaze the Chat on 2010-05-19
Sorry, but now I can't even log into Ubuntu, so yeah. And, it says "Video Mode not Supported." Sorry for my mistake.

---

### Post by Chaze the Chat on 2010-05-19
> **realzippy said:**
> Did you install -as suggested- a driver before error occurred?If so,which one?
I think I installed the Moderate Effects one.

---

### Post by Phrea on 2010-05-19
> **Chaze the Chat said:**
> I think I installed the Moderate Effects one.

That's not a driver...

Did you check: System --> Administration --> Hardware Drivers again?

---

### Post by Chaze the Chat on 2010-05-19
I can't. I can't see the screen for ubuntu because of the message. The screen goes black, and that is all there is.

---

### Post by realzippy on 2010-05-20
So boot in recovery mode,drop to root shell,open xorg.conf:

```
sudo nano /etc/X11/xorg.conf
```
look for "driver" line and change
*nvidia* to *vesa*, then reboot.
This should prevent your not working nvidia driver from loading...

---

### Post by Chaze the Chat on 2010-05-20
Thanks! I'll try it.

---

### Post by Chaze the Chat on 2010-05-20
Could you make it a little simpler please? I typed in every thing you said up until find driver folder, but after I typed in the xorg.conf thingy, it went to a black screen with me having to type in things. Help please?

I'm sorry if that sounded a little rude, I just don't really know what to do after typing in the sudo nano thingy.

---

### Post by Chaze the Chat on 2010-05-20
Oh, and when in the recovery mode, it is off center about an inch, so I can't see some of my writing.

---

### Post by realzippy on 2010-05-21
ok,if you cannot see the whole screen,working with "nano" is bad,especially
if you never did it before.So,forget that "xorg-thingy".
Boot in recovery mode,is there an option called "xfix" ?If so,run it.

Why not installing 10.04?

---

### Post by Chaze the Chat on 2010-05-21
OK! That allowed me to log on. I still have the first problems though. Any help on that? (It was the driver btw)

---

### Post by Chaze the Chat on 2010-05-21
Whenever I install a driver, the message comes up.

---

### Post by Chaze the Chat on 2010-05-22
Bump

---

### Post by Chaze the Chat on 2010-05-23
Um, seriously, need help.

---

### Post by inso_741 on 2010-05-23
can you provide us with some information on your hardware
like graphics card/chipset  are you using for starters

---

### Post by realzippy on 2010-05-25
So,as you can log in,which driver are you trying to install?What is offered in

System --> Administration --> Hardware Drivers   ??

---

### Post by aastarwar on 2010-05-25
please help monitor problem...

---

### Post by mk1w86 on 2010-05-25
> **aastarwar said:**
> please help monitor problem...

Is your problem the same as the original poster's?

Chaze the Chat, does your monitor have an auto adjustment mode to centre the image, there is normally a button on the front of it for this?

Could you please post the output of

```
lspci
```

so we can see what hardware you have.

Also, have you tried a newer version of Ubuntu?

---

### Post by Elfy on 2010-05-28
> **mk1w86 said:**
> Is your problem the same as the original poster's?

t'was a spammer :(

---

