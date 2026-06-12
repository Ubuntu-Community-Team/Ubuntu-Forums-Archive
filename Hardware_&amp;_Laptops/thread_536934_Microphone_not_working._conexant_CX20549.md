---
title: "Microphone not working. conexant CX20549"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by jlouwerse on 2007-08-28
Hello,

I have a compaq c540 with soundcarddrivers from conexant CX20549.
 
I unmuted everything and i still dont get sound trough my microphone input.
I know my mic and my hardware is working because i tested it on my windows vista boot on the same laptop.

How can i make my microphone work?

greetings J

---

### Post by linuxwizard on 2007-08-28
Have you tried this

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by jlouwerse on 2007-08-28
thank you for responding.
Unfortunately i dont have a capture tab in my volume control so i cant fix it like that. :(

---

### Post by TorchlightJay on 2007-08-28
upgrade your ALSA. I had a really similar problem and once i upgraded all of my alsa and the plugins, everything worked just fine.

---

### Post by jlouwerse on 2007-08-31
When i tried to install the new alsa drivers i got an error:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

i checked the config log and it told me the following:

 /usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

what is wrong?

Greetings, 
                    J

---

