---
title: "Help with chmod/chroot and Samba"
date: 2008-08-21
forum: General Help
---

### Post by voteforpedro on 2008-08-21
Finally got Samba working - great. :guitar:

It's going to be serving files to my girlfriend's XP machine, my Ubuntu desktop and my MythTV media centre. I was going to share a unique folder for each file type (music, videos, photos etc) but for the Windows machine it's going to be a lot of mapped network drives so I'm going down a different route. I'm going to share my /media/sda/share folder which will contain child directories for each file type, thus, one network share.

There will only be one Samba user account which we will use on all three.

Directory structure will therefore be as follows:

/media
... /sda
...... /share
......... /music
......... /video
......... /photos
......... /docs
......... /www (apache2 default root)

and so on...

Now I'm just getting to grips with Linux so I'm a bit lost as to how to set permissions for the folders. :confused:

We won't have access to /media or /sda across the network, which is fine.

I want it so that we can't (well, *she* can't lol) write, delete or make a directory in /share but can do as we please in its sub-directories.

How can I achieve this using chmod or chroot?

When she accesses the share it asks for a username and password, which, as I said, is shared between the four workstations. I haven't added a username to Samba but my local username and password works. Does this mean that anything created etc in this share, even on the XP machine, will be owned my by Ubuntu user? If so, this is good.

Thanks. :)

---

### Post by EMCGFX on 2008-08-21
No you must add user to your computer first then to samba.

1 -> Add User in Ubuntu:
System > Administration > Users and Groups (you should see "Users Settings" now).
Click on "Unlock" type your root password. Ones unlocked click on "Add User".
Ones in "New user account" window.
Type: Username, select "Unprivileged" profile and type the password.
Then click "Advanced" tab and where it says "Shell" type: /bin/null
Then in "Main group" select "sambashare".

2 -> Add User to Samba:
Open terminal login to root, sudo -i then your password.
To add user type: smbpasswd -L -a your_username
then your samba password, same as you did for ubuntu user.

3 -> Configure your Samba File:
Here is an example smb.conf file.
```
[global]
workgroup = WORKSTATION
server string = Ubuntu Server
dns proxy = no
security = user
socket options = TCP_NODELAY
wins support = no

[Media]
path = /media/
available = yes
browsable = yes
public = yes
writable = no

```

In terminal type: gedit /etc/samba/smb.conf
ones opened paste above code and modify to your needs.

When done, simply restart samba and login from windows by ip \\192.168.1.10 (your ubuntu server ip) or by hostname (if you have one).

Restart samba by typing this in terminal: /etc/init.d/samba restart

Also, make sure you have your firewall configured correctly. (if you need help, let me know).

Now, I hope I did not miss anything, but if I did reply here I will help.

---

