---
title: "How to Install Acer 5920 Integrated Acer Crystal Eye webcam"
date: 2008-09-25
forum: Hardware
---

### Post by sukhhari on 2008-09-25
Hello,

I would like to know, how to install Acer 5920 - Integrated Acer Crystal Eye webcam on Ubuntustudio 8.04 (amd64 version).

Regards

Harish:confused:

---

### Post by sukhhari on 2008-09-27
You need to install Cheese

Regards

Harish

---

### Post by jens83 on 2008-10-13
ive got acer 2930 and my webcam doesnt work either. i followed natirips post ( [http://ubuntuforums.org/showthread.php?t=715366](http://ubuntuforums.org/showthread.php?t=715366) ) and tried downloading:

File Type: gz  	linux-uvc.tar.gz (92.5 KB, 548 views)

then i was supposed to follow these codes:

./svn-version.sh
sudo make
sudo make install

after first code i got: cant find file or directory-error message.

also tried installing cheese, but this makes my computer freeze at once.
thanks for any help

---

### Post by guardian93 on 2008-10-19
I have the same problem with my Acer Extensa 5420, AMD 64. I followed many tips, still can't get my integrated webcam to work in either of cheese, vlc, ekiga, etc. It's a Cystal Eye Webcam.

Runnind dmesg | grep Crystal returns:
[   51.973055] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (5986:0105)

Can anyone help?

---

### Post by bm13084 on 2008-11-22
cheese recognizes my cam and it works... but i cant get firefox to work it...

any ideas?

---

### Post by Rumplesmigskin on 2008-11-24
I have similar problems with the new release, Acer 2920, Crystal Eye Webcam. It was working fine in Hardy. Guess something must have been broken in the update. Neither cheese nor camorama can get input from the webcam, but aMSN and luvcview / xawtv have no problems whatsoever. Possibly something to do with v4l(2)?

---

### Post by 1902 on 2008-11-26
i've tried hardy on my aspire 4930G, crystal eye cam didn't work as well as the wifi, but in 8.10 everything works out of the box.

---

### Post by TorokLev on 2008-12-02
On my Acer emachines e520 using Interpid Ibex (ubuntu 8.10) the web cam didn't start automatically.  After google-ing I found a thread
which solved my problem:

[http://forum.notebookreview.com/showthread.php?p=3849059](http://forum.notebookreview.com/showthread.php?p=3849059)
solves the problem.

I suggest everyone to take a chance.
If it works for you, you may make it a permanent solution.
(modprobe will be forgotten at reboot)
So type in a terminal:

sudo gedit /etc/modules

add a line to the list:

uvcvideo

save it and write

sudo gedit /etc/modprobe.d/options

add a line 

options uvcvideo quirks=2

then reboot the computer and skype should recognize the webcam
w/o any intervention.

Lev

---

