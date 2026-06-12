---
title: "Take a screenshot every 20 seconds or so"
date: 2008-07-22
forum: General Help
---

### Post by tom66 on 2008-07-22
I would like to take a screenshot every 20 seconds or so and save it to a folder behind the scenes. Is this possible, if so, how?

Thanks,
Tom

---

### Post by Dr Small on 2008-07-22
You could write a shell script:
```
#!/bin/bash

while true; do
    scrot ~/screenshots/%M-%S.png
    sleep 20
done

exit 0
```

---

### Post by tom66 on 2008-07-22
It beeps every time. Can I stop it from doing that?

Thanks,
Tom

---

### Post by anotherdisciple on 2008-07-22
Are you spying on someone? lol... is it a system beep or speakers beeping?

---

### Post by Dr Small on 2008-07-22
> **anotherdisciple said:**
> Are you spying on someone? lol... is it a system beep or speakers beeping?
It's a system beep. I know, because it does it on mine. But I dunno how to disable the pcspkr.

---

### Post by tom66 on 2008-07-22
No, it's an experiment of mine. I like to film myself coding then put it into a timelapse.

Anyways I decided to compile from source and comment out 'XBell' in main.c. Great. 'cept I can't seem to compile it. Could someone point instructions. I've configured fine, then make, then sudo make install, are there more steps or something?

---

### Post by grim4593 on 2008-07-22
I ran the script, and it does not make a beep for me.

---

### Post by tom66 on 2008-07-22
Okays, I found that temporarily disabling the pcspkr module works for me:

rmmod pcspkr

Thanks for everyone's help. It now works fine. :)

---

### Post by ibuclaw on 2008-07-22
To remove the system speaker module, type in the terminal:
```
sudo modprobe -r pcspkr
```

Run the script again, and with a bit of blind faith. It should be quiet now :)

To make this change permanent, edit your blacklist file.
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the line
```
blacklist pcspkr
```
at the bottom.

Regards
Iain

---

