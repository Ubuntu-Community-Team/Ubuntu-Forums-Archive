---
title: "No file locks with Ubuntu 8.04 and Samba"
date: 2008-09-29
forum: General Help
---

### Post by brucehohl on 2008-09-29
I have set up a Samba server on Ubuntu 8.04 with the following smb.conf:

[global]
   workgroup = ABC
   wins support = yes
   security = user
   passdb backend = tdbsam
   nt acl support = no
   unix extensions = no

[Tim]
   comment = Tim's Files
   path = /home/shares/Tim
   read only = no
   browseable = yes
   create mask = 0777
   directory mask = 0777
   writable = yes
   valid users = 

If a WindowsXP PC opens a file in the "Tim" share, and then a second WindowsXP PC opens the *same* file, the second Windows PC only has read access to that file.  This is the expected behavior.

If a Windows PC opens a file in the "Tim" share, and then an Ubuntu 8.04 PC opens the *same* file, the Ubuntu 8.04 PC has read and *write* access to that file.  This is not expected (should not have *write* access). 

On the Ubuntu 8.04 PC I have confirmed this behavior with OpenOffice and Gedit. 

The "Tim" share was mounted as follows:
mount.cifs //192.168.0.100/Tim /home/John/mnt/FS1/Tim \
-o username=john,file_mode=0666,dir_mode=0777

Can anyone confirm this behavior with Ubuntu 8.04?
Can anyone confirm expected behavior with Ubuntu 8.04?
Thanks, BH

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

