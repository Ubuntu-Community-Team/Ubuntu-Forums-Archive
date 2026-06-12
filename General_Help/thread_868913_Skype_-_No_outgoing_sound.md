---
title: "Skype - No outgoing sound"
date: 2008-07-24
forum: General Help
---

### Post by Kribulin on 2008-07-24
Hello all,

I'm really new to Ubuntu and have problems using Skype. I've installed it and everything works fine, except for one thing: the person I'm talking to cannot hear me. However, I can hear him without problems. In Windows I haven't had such a problem. I have a normal Acer Aspire 5100 laptop.

Any ideas what could be wrong?

Thanks in advance,
Christian

---

### Post by artmendez on 2008-07-24
Hello.

Does sound work with other applications?

Can the other party listen to you?

If so, it may be that the sound server is busy with that other application.

For some reasons some applications take over the sound server and when another application tries to reach it, it will be unable to use it. This issue is different.

For now, give this a try: close all applications that may be using sound (Music player, etc.). Try again. You might have Skype now being able to address the sound output.

saludos.

---

### Post by Potatoj316 on 2008-07-24
Well make sure your mic is plugged in to the correct spot (but you probably already did that)

You have to configure skype to use the correct input device.  Try looking around in the settings for sound options, or input device, or something.

---

### Post by Kribulin on 2008-08-13
Listening to music works, as well as hearing what my partner says in Skype. The problem is only the outgoing sound (which works in Windows). I don't have any other applications open, so that's not the problem either. It's really strange, seems to be something Ubuntu-related.

---

### Post by .Danny on 2008-08-18
I am having the same issue. Also when I talk, I can hear a sort of echo of myself in my own headset. However the other person hears nothing.

---

### Post by Calabresi on 2008-08-19
I had the same problem when I installed mine, Ubuntu and Skype, I solved it as follow:

Menus>>System>>>Preferences>>>>Sound ... then set **all** to Alsa (Advanced Linux...).

Go to Skype, >Options>>Device Setings>>> **ALL DEFAULT**, then inther, there's the make a test call, try it.

Mine sound device is an onboard Intel ICH5

---

### Post by robertyou on 2008-10-24
Hi guys,

Try looking into here:
[http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html]("http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html")

It solved the conflict between skype and music player on my ubuntu.

---

