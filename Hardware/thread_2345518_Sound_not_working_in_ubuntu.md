---
title: "Sound not working in ubuntu??"
date: 2016-12-05
forum: Hardware
---

### Post by 1ritesh on 2016-12-05
Hello,
In my computer sound is not working why?
how to install or  trouble shot sound problem?

---

### Post by ajgreeny on 2016-12-05
Please tell us a lot more about your system.

Ubuntu version?
Hardware used, particularly CPU, amount of RAM, graphic card, audio card, etc etc?

Without that we are all shooting in the dark and can not offer any useful assistance.

---

### Post by 1ritesh on 2016-12-06
Hello all,
The hardware motherboard is m2n68 am se2
4 gb ram
80gb hardisk ata
no graphic card no sound card

thats all

---

### Post by Yellow Pasque on 2016-12-06
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by 1ritesh on 2016-12-08
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

what to do after this?

---

### Post by karl96 on 2016-12-08
Open /tmp/alsa-info.txt

You should try ```
 sudo alsactl init 
```

---

### Post by 1ritesh on 2016-12-08
> [B]Open /tmp/alsa-info.txt
[/B]

How to do this?
and i got this result.

hello sound is working...

thanks guys dear guys

---

### Post by karl96 on 2016-12-08
Did it work?

You have to go to the /tmp filesystem
```
 cd /tmp 
```
```
 ls 
```
```
 gedit alsa-info.txt.0mc8pFl6pN 
```

If you've rebooted recently you'll have to run it again as /tmp files are cleared on restarts.

---

### Post by 1ritesh on 2016-12-08
> If you've rebooted recently you'll have to run it again as /tmp files are cleared on restarts.
yes this happen how to fix it?

---

### Post by karl96 on 2016-12-08
Run the script again, it'll make another temporary file. By the looks of alsactl your hardware is fine, possibly the channel is muted, try ```
alsamixer
``` and see if automute is enabled.

---

### Post by 1ritesh on 2016-12-08
How to fix it permanently ?

here it is

hello,
how to maintain sound permanently?

---

### Post by Yellow Pasque on 2016-12-10
What did you do to get it working temporarily?

---

### Post by 1ritesh on 2016-12-14
[COLOR=#000000][INDENT]What did you do to get it working temporarily?

i want it to work 24x7 without any problem when i shut it down it should not ask for any activate sound command.
please tell how to use it ?[/INDENT]
[/COLOR]
[INDENT]
[/INDENT]

---

