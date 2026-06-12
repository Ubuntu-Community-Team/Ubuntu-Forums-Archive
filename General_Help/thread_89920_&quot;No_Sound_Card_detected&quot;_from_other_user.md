---
title: "&quot;No Sound Card detected&quot; from other users"
date: 2005-11-13
forum: General Help
---

### Post by ubuntu27 on 2005-11-13
HI everyone !! :D

I am here to learn more about Linux and Ubuntu :D

I have a little problem. 

In my computer, there are four user accounts [For Ubuntu], each of them, except me now cannot play any sound. The Volume control in the Gnome Bar have a litle "x" icon in red. It is not mute or anything, I cannot change to volume.

WHen I do System/Preferences/Sound

It tells me that there are no SoundCard. No SoundCard detected. 

That doesn't happen in my user account (The first user that I created when I installed Ubuntu, the one that has the ability to do "Sudo") .

In the other user account they always had sound, but somehoe they do not have now.

anybody have any ideas?

Thank you in advance guys. Thanks you. :)

---

### Post by Dr. Nick on 2005-11-13
I think I know the fix.

Go to system-administration-users and groups from your 1st account, go to groups tab/find audio group-hit properties and add the users you want to the group

---

### Post by ubuntu27 on 2005-11-13
[QUOTE=Dr. Nick]I think I know the fix.

Go to system-administration-users and groups from your 1st account, go to groups tab/find audio group-hit properties and add the users you want to the group[/QUOTE]

hi, thanks for the replay Dr. Nick.

I followed your instruction.

There is no Audio group in the User and Group.

Here is the list of group that I have:
**GROUP: GID**

USERS: 100
dhcp: 101
syslog: 102
klog: 103
ubuntu27: 1000
lpadmin: 104
scanner: 105
admin: 106
crontab: 107
ssh: 108
slocate: 109
messagebus: 110
hal: 111
gdm: 113
face2face: 1001
america: 1002
kyoto: 1003

---

### Post by Dr. Nick on 2005-11-13
oops didnt realize you have to check the show all users and groups box. See if that works

---

### Post by ubuntu27 on 2005-11-13
Thank you Dr. nick !! :D

Ok, now I found Sound Group and added all the users...
I don't know if the sound sowks now.. since I don't know their password and thus I am nto able to loigin to their accounts.

I will see if it works when thy are home ;)

---

### Post by Dr. Nick on 2005-11-13
Glad you found it, It should work as I just did it myself with another user account I had. Let us know for sure though once you find out.

---

### Post by teaker1s on 2005-11-13
you can also set audio in user privileges

---

### Post by Dr. Nick on 2005-11-13
[QUOTE=teaker1s]you can also set audio in user privileges[/QUOTE]

That you can do aswell, Just depends on how many users you want to add I guess. Thanks for the heads up, I hadn't gone that way before

---

### Post by ubuntu27 on 2005-11-15
[QUOTE=Dr. Nick]Glad you found it, It should work as I just did it myself with another user account I had. Let us know for sure though once you find out.[/QUOTE]


ALRIGHT! IT IS WORKING NOW!! THANK YOU DR. NICK !! :D  :KS 



teaker1s: Thank you for the tip.

---

