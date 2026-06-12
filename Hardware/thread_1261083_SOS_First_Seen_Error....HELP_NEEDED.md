---
title: "SOS First Seen Error....HELP NEEDED"
date: 2009-09-08
forum: Hardware
---

### Post by red33m on 2009-09-08
I am running Ubuntu for some time now and I had not many errors.But this this one I cannot solve on my own.Every time I turn on my PC the system asks me in which OS I want to login.I have about 11 seconds to make my choice.But from yesterday it asks me where I want to login but stays there for 2 seconds and then everything turns black and nothing happens.The same thing happens with BIOS too.I want to change the Boot Sequence so I can reinstall Linux but it stays in the BIOS section for 2 seconds and then everything turns black.

What should I do? If YOU don't event know the answer just tell me if I can log into BIOS from the Ubuntu Desktop so I can change the Boot Sequence.

Thanks for all the help..appriciate it.

P.S. I bet you are wondering how'd I wrote this thread from my P.C....well I logged in from the backdoor(recovery mode)....

---

### Post by amac777 on 2009-09-08
I'm not sure I understand your description. You say that you can't select any operating system or enter BIOS because after 2 second "everything turns black and nothing happens". That sounds like a hardware problem. But then you say you booted using the recovery mode. So it seems like you can at least select recovery mode and it works.

Maybe the delay got changed in your grub menu? Check this file:

```
sudo nano /boot/grub/menu.lst
```

And look for the settings:
```
default         0
timeout         10

```

The default indicates which OS it will boot after the timeout (in seconds). 0 means the first one, 1 would be the second etc. Maybe increase the timeout to give yourself more time to make a choice?

---

### Post by red33m on 2009-09-08
I just typed really fast that's how I managed to login... :)

---

### Post by red33m on 2009-09-08
this won't fix anything cause it has to be a hardware problem but I will fight a little and manage to format it..! 

Thanks for the reply!

---

