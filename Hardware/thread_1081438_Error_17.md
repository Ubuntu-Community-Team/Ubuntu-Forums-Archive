---
title: "Error 17"
date: 2009-02-26
forum: Hardware
---

### Post by anij on 2009-02-26
Hello all,
Here is my problem:
I have a compaq b1900 on dual boot with windows XP and ubuntu. I recently put Windows into hibernate. When I started it up again it gave me a message that there was some problem (sorry, I did not think that it was important at the time so I do not remember exacltly what it said) and that if I don't want to fix it now I have to press f11 during start up to fix it the next time. Wanting to access the computer immediately I said continue without fixing the problem. It then rebooted and once it came to the grub menu it now says Error 17. I searched on google and saw the other thread on ubuntu forums but it has not helped me.
When I put a CD in and start up it cannot find the wifi card so I cannot directly access internet. I am now using my friend's computer temporarily to handle this problem. Also, when I try to access the windows part of the hard drive it says that it cannot mount that volume as it has been hibernated.
I have quite a bit of important documents that I need to recover from that part of the hard drive. Since I have access only temporarily to the internet a fast response would be very appreciated.
Thanks,
Aniruddha

---

### Post by caljohnsmith on 2009-02-26
How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition sdaX (like sda3 for example) and do:
```
[[ $(mount | grep [COLOR="Blue"]sdaX[/COLOR]) ]] || sudo e2fsck -fv /dev/[COLOR="Blue"]sdaX[/COLOR]
```
If that completes successfully, see if you can mount the Ubuntu partition:
```
sudo mkdir /media/ubuntu
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /media/ubuntu && nautilus /media/ubuntu &

```
If mounting the Ubuntu partition is successful, you should also get a nautilus file browser that pops up and lets you browse your Ubuntu file system. Next note which is your Windows partition sdaY from the fdisk output above, and try:
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/[COLOR="Blue"]sdaY[/COLOR] /media/windows -o remove_hiberfile
```
If the mount command is successful, you should be able to browse to /media/windows and access all your Windows files. If mounting the Ubuntu partition was successful, you could try rebooting and see if you still get the Grub error 17. Please let me know the results for all the commands, and we can work from there if you want.

---

### Post by anij on 2009-02-27
> **caljohnsmith said:**
> How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition sdaX (like sda3 for example) and do:
```
[[ $(mount | grep [COLOR="Blue"]sdaX[/COLOR]) ]] || sudo e2fsck -fv /dev/[COLOR="Blue"]sdaX[/COLOR]
```
If that completes successfully, see if you can mount the Ubuntu partition:
```
sudo mkdir /media/ubuntu
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /media/ubuntu && nautilus /media/ubuntu &

```
If mounting the Ubuntu partition is successful, you should also get a nautilus file browser that pops up and lets you browse your Ubuntu file system. Next note which is your Windows partition sdaY from the fdisk output above, and try:
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/[COLOR="Blue"]sdaY[/COLOR] /media/windows -o remove_hiberfile
```
If the mount command is successful, you should be able to browse to /media/windows and access all your Windows files. If mounting the Ubuntu partition was successful, you could try rebooting and see if you still get the Grub error 17. Please let me know the results for all the commands, and we can work from there if you want.

I tried as you suggest and everything except for the last command.
It says:

"
Windows is hibernated, refused to mount.
Failed to mount 'dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows properly, so mounting can be done safely.
"
Thanks for the help.

---

### Post by caljohnsmith on 2009-02-27
Were you able to mount the Ubuntu partition and access its file system? If so, are you still getting the Grub error 17 on start up, or can you at least boot into Ubuntu yet? Please provide as much information as possible, otherwise it is difficult to troubleshoot your problem.

---

### Post by anij on 2009-02-27
> **caljohnsmith said:**
> Were you able to mount the Ubuntu partition and access its file system? If so, are you still getting the Grub error 17 on start up, or can you at least boot into Ubuntu yet? Please provide as much information as possible, otherwise it is difficult to troubleshoot your problem.

Hi,
I will try to give as much information as possible. But as I am a beginer I don't know what information to give or where it is.

I was able to mount the linux partition and browse through the files. i.e. it opened up in a Nautilus window and I was able to see and read what I have on the linux partition.

I still get the Error 17. If there is some other useful information that I can give, please tell me and I will post it.

Thank you very much for your help.

Aniruddha

---

### Post by caljohnsmith on 2009-02-27
Are you getting the Grub error 17 before seeing the Grub menu or after you get the Grub menu and try to boot Ubuntu? I would assume it is the former case, but I need to make sure. How about doing the following:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know if all the above commands complete successfully, and if so, reboot and see if you get the Grub menu on start up. Also, when you ran the e2fsck on the Ubuntu partition, did it return any errors?

---

### Post by anij on 2009-02-27
> **caljohnsmith said:**
> Are you getting the Grub error 17 before seeing the Grub menu or after you get the Grub menu and try to boot Ubuntu? I would assume it is the former case, but I need to make sure. How about doing the following:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know if all the above commands complete successfully, and if so, reboot and see if you get the Grub menu on start up. Also, when you ran the e2fsck on the Ubuntu partition, did it return any errors?

Hi,
Thank you very much for your help. It worked. I am able to start windows now.
I have not tried loading Ubuntu yet but I guess that it should work too.
Have a nice weekend,
Aniruddha

---

### Post by caljohnsmith on 2009-02-27
Glad to hear you could at least boot into Windows; let me know if you have any problems booting Ubuntu, but otherwise it sounds like you should be fine. Cheers and hope you don't have any more Grub errors any time soon.

---

