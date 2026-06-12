---
title: "[SOLVED] Samba and XBOX1"
date: 2008-08-29
forum: General Help
---

### Post by Voorhees1979 on 2008-08-29
Hi there

Hoping someone can help me here. I did a fresh install of Hardy. Both of my drives were ntfs format so I copied the files over to the other drive to format to ext3 them back again to format the other drive after having to CHMOD 777 to each drive so I could even write them. Ok all good so far. Went to  drive 1 right clicked the "Movie" folder and clicked share, got an error about permissions, rebooted and the error went and the folder was then shared. Drive 2 has TV right clicked and shared and it was shared as well. All good so far. Went downstairs and booted the xbox1 searched for samba shares and it was found, it played everything from both drives, some folders I had to enter my ubuntu user and password into and I dont know why. I have shared movies folder, in that folder will have Kids,Horror etc folders. I have to enter ubuntus user and pass to enter the kids folder but the horror folder I can click on and enter just fine. Just seems really odd. Anyway forget the user and password errors on some folders the problem is is I rebooted. Restarted samba but now the xbox1 wont pick up the shares???

any help would be great

---

### Post by Voorhees1979 on 2008-08-30
Ok it was just a permissions issue.

There is one thing I would like to fix if anyone can help me. When I boot the xbox goto the media centre and select shares. I have to enter my ubuntu user and pass to axxs each drive that has shares. Is there away around this so the drives are not locked and need unlocking with ubuntu user and pass?

Many Thanks for any help

---

### Post by Voorhees1979 on 2008-08-30
SOLVED

The answer to stop the xbox1 asking for a password is:

sudo gedit /etc/samba/smb.conf
security = share
guest account = nobody

add this to the bottom:
# [Share tv]
writable = yes
path = /path/to/directory
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes

i added the txt twice for both different shares on the 2 drives

When you right click the folder to share make sure the guest part at the bottom is ticked.

Thats how I stopped my xbox1 asking for passwords. If some movies dont play just check the permissions on the file.

---

