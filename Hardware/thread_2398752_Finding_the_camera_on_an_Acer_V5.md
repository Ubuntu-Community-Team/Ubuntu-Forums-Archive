---
title: "Finding the camera on an Acer V5"
date: 2018-08-16
forum: Hardware
---

### Post by m005kennedy on 2018-08-16
I bought a used acer v5 that had Windows 10 on it but was  a windows 8 machine. it had been upgrade to 6 gigs of Ram. It didn't even run properly because the OS was too much for it. So I am trying out Ubuntu Studio at the moment. The machine might not be enough for it, but I was hoping to edit some photographs and do some short video editing. I have not been able to detect the built in camera. I tried to capture video with VLC but I could not get the camera to come up.  Is there a way to find the camera or install some software to make it work?  or am I just pipe dreaming that i can get this netbook working for this?

---

### Post by westie457 on 2018-08-16
Welcome to UF m005kennedy,

Can you please open a terminal and post the output of the command lsusb

---

### Post by m005kennedy on 2018-08-16
here you go
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

[COLOR=#4CE64C]**michael@michael-Aspire-V5-122P**[/COLOR]:[COLOR=#295FCC]**~**[/COLOR]$ lsusb
Bus 002 Device 002: ID 064e:e330 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04f3:009d Elan Microelectronics Corp. 
Bus 004 Device 004: ID 0489:e05f Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=#4CE64C]**michael@michael-Aspire-V5-122P**[/COLOR]:[COLOR=#295FCC]**~**[/COLOR]$

---

### Post by westie457 on 2018-08-17
If I remember correctly when the camera on my Acer laptop was not found all I did was install 'Cheese Webcam Booth'```
sudo apt install cheese
```
It came to life immediately.
If that does not work post the terminal output of the following please ```
uname -a
lsmod | grep video
```
Also could you use code tags by selecting 'Adv Reply' > click on the '#' symbol and paste the text between the code brackets

Thank you

---

### Post by m005kennedy on 2018-08-17
tried both, her is the out put of the second
michael@michael-Aspire-V5-122P:~$ uname -a
Linux michael-Aspire-V5-122P 4.15.0-32-lowlatency #35-Ubuntu SMP PREEMPT Fri Aug 10 19:18:19 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
michael@michael-Aspire-V5-122P:~$ lsmod | grep video
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
video                  45056  1 acer_wmi
michael@michael-Aspire-V5-122P:~$

---

### Post by m005kennedy on 2018-08-17
I thought the simplest way to test it was with vlc, but the web camera option doesnt come up

---

### Post by m005kennedy on 2018-08-17
well I guess I just dont know what Im doing. Cheese does work and capture video. I thought it was some type of driver, not a separate  program. so I guess I record in cheese then move the video to an editing program.  I"ll experiment with it and see what kind of quality I can get out of it. The webcam is probably the limiting factor?

---

### Post by m005kennedy on 2018-08-17
I get a low quality video with extremely low sound. Ill try some separate webcams next. I think I have a logotec one that works with linux.

THANKS FOR ALL YOUR HELP,

---

### Post by westie457 on 2018-08-18
You can now try with VLC, the results won't be brilliant. The built in webcam is a very low resolution at 1.3 or 2 megapixels.

---

### Post by m005kennedy on 2018-08-18
yes, Ill try some webcams.  Ive picked up a number of them used.

---

