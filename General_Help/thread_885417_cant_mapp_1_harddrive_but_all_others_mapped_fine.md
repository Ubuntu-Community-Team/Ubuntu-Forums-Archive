---
title: "cant mapp 1 harddrive but all others mapped fine"
date: 2008-08-10
forum: General Help
---

### Post by chrismitt2002 on 2008-08-10
as the title says i cant map 1 hd from my ubuntu server to my main ubuntu box (running 804 btw) i used this command to map the drives i 1st use this sudo mkdir /media/name_of_folder
2ed i gave the folder write permission 3erd i did this 
sudo smbmount //192.168.1.2/name_of_windows_share /media/name_of_folder_u_created -o username=username_of_windows_pc,password=pass_of_windows_pc,uid-1000,mask000
this worked on all drives but my 250gb hd named 250gb#3F and i recived this error owner@amd-quad:~$ sudo smbmount //192.168.1.4/250gb#3F /media/250gb#3F -o username=my_user_name,password=my_password,uid-1000,mask000c
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
ps the names are correct, permissions are correct, and i have mounted 10  other drives the same way from the same box

---

### Post by cdtech on 2008-08-10
Your SMB address's are different. Is that correct?

---

### Post by chrismitt2002 on 2008-08-10
yes the 3 of the drives are on my ubuntu print/file server the rest are on my windows box

---

### Post by chrismitt2002 on 2008-08-10
bump

---

### Post by chrismitt2002 on 2008-08-10
bump

---

