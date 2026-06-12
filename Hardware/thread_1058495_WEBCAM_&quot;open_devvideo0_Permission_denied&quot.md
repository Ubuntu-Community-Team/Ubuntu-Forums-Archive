---
title: "WEBCAM: &quot;open /dev/video0: Permission denied&quot;"
date: 2009-02-02
forum: Hardware
---

### Post by switchseven on 2009-02-02
I've run into a problem while installing my webcam for use in amsn and skype etc.

Part of the problem perhaps is that its one of the awkward Ricoh Motion-Eye webcams discussed in detail [[here]]("http://ubuntuforums.org/showthread.php?t=968381").
Specifically a VGP-VCC2 in a Sony Vaio VGN-SZ3XWP.

```
user@host:~$ lsusb
Bus 005 Device 003: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
```

I suspect I've installed the driver correctly as I've created /dev/video0 and I can get the package 'webcam' to take a snapshot and save it via SSH on localhost. But aMSN, Cheese and Camorama won't detect it. (I've installed it  as described by epvipas in post #55, on kernel 2.6.27-11-generic).

Strangely, webcam without admin rights returns...
```
user@host:~$ webcam
reading config file: /home/user/.webcamrc
v4l2: open /dev/video0: Permission denied
v4l2: open /dev/video0: Permission denied
v4l: open /dev/video0: Permission denied
no grabber device available
```

However, with root access works fine...
```
user@host:~$ sudo webcam
reading config file: /home/user/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=5, bottom=240, right=320
ssh config [ftp]:
  user@localhost:/home/user/cam
  uploading.jpeg => webcam2.jpeg
```

Stanger still, aMSN, Cheese and Camorama still won't conect to the webcam when run as root.

eg. sudo camorama
Error Dialog: Error (camorama) 
Msg: Could not connect to the video device (/dev/video0). Please check the connection.


Has anyone experience of this of can offer a solution?
Thanks.

---

### Post by pnavarrc on 2009-02-14
Hello,

   I solved the problem. You must give to the user (you) permission for use video devices. Go to *System > Administration > Users and Groups*. Unlock and select your username. In user privileges, you must enable the line "*Capture video from TV or webcams, and use 3d acceleration*", log off and log in.

   I hope that help you. Greetings,

      Pablo.

---

### Post by onecrustybaker on 2009-05-04
after days of pulling my hair out your solution made my skype work...thanks very much.

---

### Post by markp1989 on 2009-06-10
> **pnavarrc said:**
> Hello,

   I solved the problem. You must give to the user (you) permission for use video devices. Go to *System > Administration > Users and Groups*. Unlock and select your username. In user privileges, you must enable the line "*Capture video from TV or webcams, and use 3d acceleration*", log off and log in.

   I hope that help you. Greetings,

      Pablo.

How do i do this from the command line?

Thanks Markp1989?

---

### Post by ubu_dynamite on 2009-07-26
Use usermod to ad the group video
man usermod
```
sudo usermod -a -G group user
```
After that logout and back in and it will work.

---

### Post by wierdlmate on 2009-11-25
It doesn't work for me!!  I have 

$ ls -l /dev/video0 
crw-rw-rw-+ 1 root video 81, 0 2009-11-25 13:45 /dev/video0
$ grep video /etc/group
video:x:44:dori,marci,apu
$ whoami
apu

$ xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.31-15-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Engedély megtagadva
v4l2: open /dev/video0: Engedély megtagadva
v4l: open /dev/video0: Engedély megtagadva
no video grabber device available

(Engedély megtagadva = Permission denied)

---

