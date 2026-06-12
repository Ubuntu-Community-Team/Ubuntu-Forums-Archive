---
title: "I killed 8.10 with Compiz. Help!"
date: 2008-11-14
forum: General Help
---

### Post by DetCochese on 2008-11-14
Hi all.

I'm fairly new to Ubuntu and Linux in general. I hate windows so I figured what the hell. I used Digital unix in high school in the mid 90's but it's been a long time. 

Anyhoo, I am running 8.10 on two machines. One is the XPS M1330 I'm on now, and the other is my new Dell Inspiron Mini 9. It came with a Dell version of 8.04 with memory capped to 1GB because of some stupid Dell/M$ agreement.

Anyway, I have a 2GB stick on the way to max the RAM and had to put 8.10 on it for the new NM and to uncap the RAM limit. To get to the point, I was playing with Compiz on the Mini 9 after finding a Matrix active desktop that I wanted to throw onto the Mini 9. I got to peeking around at the settings in Compiz Config settings manager. I was messing with the settings and effects and now my Mini 9 is unusable.

The desktop GUI goes black and distorts and I can't read anything, click on menus, get back into the config to edit, nor do I know what the conflict is.

Aside from reloading 8.10 onto this machine with a USB key, is there a way to fix compiz and keep my current OS intact?

Thanks.

---

### Post by Vadi on 2008-11-14
Try blindly loading into the broken ubuntu, press Alt+F2, and type "metacity --replace". Do you get back to a usable screen after?

---

### Post by ajgreeny on 2008-11-14
It could be that you can not see anything when in the desktop, however, even if you see nothing in the Alt+F2, just type and hit enter and it should still work.

---

### Post by DetCochese on 2008-11-14
> **Vadi said:**
> Try blindly loading into the broken ubuntu, press Alt+F2, and type "metacity --replace". Do you get back to a usable screen after?

You are a badass.

I'm not sure what that did, but it fixed it. 

Anything else I need to do? 

How can I go about fixing my compiz config?

I was going for this...

[http://www.youtube.com/watch?v=kYgV2GlsufI](http://www.youtube.com/watch?v=kYgV2GlsufI)

Ideas?

...and thanks to both of you!

---

### Post by DetCochese on 2008-11-14
Here is the newest error!

"Please contact your system administrator to resolve the following  problem:     SIOCIFFLAGS error: No such device"

Wireless is not working.

---

### Post by mssever on 2008-11-15
> **DetCochese said:**
> You are a badass.

I'm not sure what that did, but it fixed it.
It killed Compiz and used Metacity instead.

---

### Post by Vadi on 2008-11-15
> **DetCochese said:**
> Here is the newest error!

"Please contact your system administrator to resolve the following  problem:     SIOCIFFLAGS error: No such device"

Wireless is not working.

Who told you that error? (ubuntu usually doesn't tell you to contact any admin... you're the admin usually!)

---

### Post by chrestomanci on 2008-11-15
Perhaps you could get rid of the compiz packages and start again.

Reboot the laptop, and select recovery mode, then chose the option to get a command prompt (I forget the name). You should get a root command prompt. Run the command:

```
apt-get remove --purge compiz-core
```

This will remove all the compiz packages, and get rid of all the configuration preferences you have added for compiz. You should then get rid of your personal compiz settings. In your home directory, there should be a directory called .compiz. You should delete it and all it's contents. Once all the packages are gone you should be able to reboot to the desktop normally. Then 

If you later decide to put compiz back, you can, and you should get a default set of settings.

---

