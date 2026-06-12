---
title: "Webcam not working - Sony VAIO"
date: 2012-04-01
forum: Hardware
---

### Post by Hungry Man on 2012-04-01
Sony VAIO VPCEC290X

I'm on 12.04 - didn't work on 11.10 either.

Ideas?

---

### Post by sanderj on 2012-04-01
> **Hungry Man said:**
> Sony VAIO VPCEC290X

I'm on 12.04 - didn't work on 11.10 either.

Ideas?

First check: is there a camera?

If so, two things to check as a start:

```
sander@R540:~$ grep -i camera /var/log/syslog

Apr  1 19:43:52 R540 kernel: [   18.487856] uvcvideo: Found UVC 1.00 device USB 2.0 PC Camera (1210:25f4)
Apr  1 19:43:52 R540 kernel: [   18.492474] input: USB 2.0 PC Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input5
sander@R540:~$ 


sander@R540:~$ ll /dev/ | grep -i video
crw-rw----   1 root video      10, 175 2012-04-01 19:43 agpgart
crw-rw----   1 root video      29,   0 2012-04-01 19:43 fb0
crw-rw----+  1 root video      81,   0 2012-04-01 19:43 video0
sander@R540:~$ 

```

So what's the output of those two commands on your system?

---

### Post by Hungry Man on 2012-04-01
Definitely a camera lol

> colin@colin-vaio:~$ grep -i camera /var/log/syslog
Apr  1 15:43:03 colin-vaio kernel: [   15.265896] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6409)
Apr  1 15:43:03 colin-vaio kernel: [   15.287319] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input9
Apr  1 15:44:31 colin-vaio kernel: [  103.801255] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6409)
Apr  1 15:44:31 colin-vaio kernel: [  103.808466] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input11


> colin@colin-vaio:~$ ll /dev/ | grep -i video
crw-rw----   1 root video      29,   0 Apr  1 15:43 fb0
crw-rw----+  1 root video      81,   0 Apr  1 15:44 video0


---

### Post by sanderj on 2012-04-01
What's that " colin-vaio kernel:"? Did you compile your own kernel?

Back to your camera: Make sure "vlc" is installed, and then run "vlc v4l2:///dev/video0". What happens?

---

### Post by Hungry Man on 2012-04-01
I installed skype + smoe other thing recommended by the wiki and suddenly it's working lol sooooo case closed.

edit: And thank you for the help anyways, nope didn't isntall my own kernel - working my way up to that.

---

