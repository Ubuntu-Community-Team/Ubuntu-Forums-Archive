---
title: "how to un mount dubble mounted samba shares"
date: 2008-08-10
forum: General Help
---

### Post by chrismitt2002 on 2008-08-10
as the title says i have 2 samba shares dubble mounted my 320 and my o drive whitch is a daemon-tools drive on my windows box when i try to un mount them ubntu just says unable to unmount O-Daemon-tools
unmount: it seems  /media/O-Daemon-tools is mounted mutiple times 
the 320 says the samething how do i unmount the 2nd mount for thos drives ?

---

### Post by sisco311 on 2008-08-10
Open a terminal and post the output of the *mount* command.

---

### Post by chrismitt2002 on 2008-08-10
sudo smbmount //192.168.1.2/O-daemon-tools /media/O-Daemon-tools -o username=my_username,password=my_password,uid-1000,mask000
thats for the o drive 

sudo smbmount //192.168.1.4/320gb#1 /media/320gb -o username=my_username,password=my_password,uid-1000,mask000 
thats for the 320

---

### Post by chrismitt2002 on 2008-08-10
bump

---

### Post by HermanAB on 2008-08-10
Howdy,

Couple things:
a. Don't use smbmount.  The smbfs is deprecated.  Use cifs with the ordinary mount command instead.
b. Unmount stubborn things using the 'lazy unmount' parameter:
# umount -l /mnt/sambashare
and repeat it till all shares are gone.

Cheers,

Herman

---

### Post by chrismitt2002 on 2008-08-10
HermanAB what do u mean by this Use cifs with the ordinary mount command instead plez explan more aka commands to use

---

### Post by chrismitt2002 on 2008-08-10
bump

---

