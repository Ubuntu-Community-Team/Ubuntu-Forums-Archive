---
title: "Busybox after Wubi 8.04.1 Installation"
date: 2008-08-20
forum: General Help
---

### Post by Kazrasm on 2008-08-20
Hey there,

First time linux user, and I've been getting a Busybox screen after using Wubi to install Ubuntu 8.04.1.

I downloaded  ubuntu-8.04.1-desktop-i386.iso  and  Wubi-8.04.1-rev506.exe

The installation seems to go fine, up until it asks me to reboot my computer to complete the installation. After clicking accept, and choosing Ubuntu from the boot menu, the Busybox screen appears. While in verbose mode, the error "sda: rw=0" followed by a long string of numbers and the message "attempt to access beyond end of device" is displayed. It repeats this for about a minute before finally stopping and going to Busybox and (initramfs).


Anyone able to offer some advice or a fix for this issue, or is there some sort of error log I need to post?

---

### Post by Orlsend on 2008-08-21
Usually Caused by a bad Windows Shut Down, Try loading Windows and when you get to the login just click shut down rigth away....wait...when its done you should be ok,But some of the cases are a bit Harder... like it migth have detected Erros in your HD, In windows you should check for errors (If their are any fix them and do a successful shut down)

---

### Post by Autodidactic on 2008-08-23
Hi Orlsend, Just a quick thanks for this simple explaination and fix. I could not boot into Ubuntu this morning and found your short answer (after trying all sorts of other suggestions found in other posts and getting sooooo frustrated). Your suggestion of booting to the Windows login screen and then doing a normal shutdown made so much sense and it worked for me; 
I now have my Ubuntu desktop back!
Cheers and thanks again.

---

