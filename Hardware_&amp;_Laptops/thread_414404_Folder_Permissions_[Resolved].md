---
title: "Folder Permissions [Resolved]"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by StevenAFC on 2007-04-19
Hi,

This is my first time using Linux, and I have to say I'm loving it so far!!! 

A few issues, I'm trying to install SongBird, and have downloaded the tar.gz file from their site, however I have no idea what to do with it now. I extracted it and opened the program, and it ran fine, but it isnt installed.

[http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

That site shows you how to install it, I tried to move it to the folder they say but, I get "You dont have permission".

If I right click to change permission, it says I'm not the owner. When I try to change permission of the root, it says 

Owned: Unknown
Access: Read Only

Group: Unknown
Access: Read Only

Others
Access: Read Only

If I change read only it says "Sorry could not change the permissions of 'Filesystem'"

How can I let it know I'm the owner, Im the only user on the PC.


Also side question, how do I execute commands like:

tar xzvf Songbird_0_2_1_linux-i686.tar.gz

Thanks in advance!

---

### Post by marcosXL on 2007-04-19
are you using the "sudo" command with it?? to open some files it is required to have admin rights,
and sudo wiil grant you that right for that particular operation/installation or modifying files that required root permissions.

                    I hope this help you, I myself am a newbie!!.


                                But I  like linux alot..

---

### Post by aysiu on 2007-04-19
Try this script:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

---

### Post by StevenAFC on 2007-04-20
Thanks SongBird is now installed! Ill have a look into sudo, now I've found the Terminal!

---

### Post by aysiu on 2007-04-20
> **StevenAFC said:**
> Thanks SongBird is now installed! Ill have a look into sudo, now I've found the Terminal!
This will help:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

