---
title: "File permissions for USB printer"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by skimitar on 2005-04-27
Hi,

I have an Epson usb printer. 

In order to get it to print, I find that I need to do a  'chmod o=rw /dev/usb/lp0' after every boot in order to set the correct permissions.

I could simply put this command in a start-up script to run at boot, but is there a more elegant solution? I am sure that I am missing something obvious here.....

Thanks
Jon.

---

### Post by accuser on 2005-04-28
Are you using CUPS to manage printing to this printer? The file permissions should be:
```
$ ls -l /dev/usb/lp0
crw-rw----    1 root lp 180, 0 2005-04-28 07:56 /dev/usb/lp0

```
You shouldn't need to set the o=rw permissions for this to work.

---

### Post by petertc on 2005-04-29
you are a star, 

the sudo chmod o=rw /dev/usb/lp0 worked like a dream  

there is a probelm with the permissions i am using Kubuntu and have been play about with things cups.conf  apart from getting to use admin from localhost:631 then getting the error cant open device i've been pulling my hair out. 

I think this will solve a lot of peoples problems 

thanks

---

### Post by hector on 2005-04-29
I'm having the same problem with /dev/usb/lp0 permissions. Everytime I reboot I have to change them again... is there a better way?


thanks!

hector

---

### Post by FrankVaLi on 2005-04-30
Thanks a lot. Finally got the printer to work again.

But, are there an explanation as to why a perfectly good printer quits working  because of permissions ?

---

### Post by hector on 2005-05-02
anyone could help me with my usb printer permissions? Is there a way of not having to change the permissions of /dev/usb/lp0 each time I reboot in order to be able to print?

thanks


hector

---

### Post by eddy42 on 2005-05-03
Hi,

I had the same problem and found this solution reading other posts :

1. Edit the "/etc/udev/permissions.d/udev.permissions" file as root and search line :
```
usb/lp[0-9]*:root:lp:0660
```in the printer devices section.

2. Change the last character of this line to get :
```
usb/lp[0-9]*:root:lp:0666
```
Now the permissions of the /dev/usb/lp0 device file will always let you print without problems :
```
ls -l /dev/usb/lp0
crw-rw-rw-  1 root lp 180, 0 2005-05-03 15:46 /dev/usb/lp0
```I guess i shouldn't have to do that but at least it works !

---

### Post by hector on 2005-05-03
thank you a lot! this solved the problem.

hector

---

