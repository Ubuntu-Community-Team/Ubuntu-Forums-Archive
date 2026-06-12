---
title: "[SOLVED] sshfs and apache"
date: 2008-07-20
forum: General Help
---

### Post by Dr Small on 2008-07-20
Me and Rocket2DMn were trying to get this figured out over IRC, but we really couldn't so I'll present it to the community and maybe someone else can jib in and give a solution.

I have two computers, a local one, and a remote one.
The local one is called 'darkghost' and the remote one is called 'mycroft', and is the server.

Mycroft, the server, runs XAMPP/Apache and SSH.
Darkghost, the local machine, runs SSH.

I placed in my DVDrom drive, a DVD and mounted it with:
```
sudo mount /dev/dvd /mnt/dvd
```

I can then access all of the files that are in /mnt/dvd. I then installed sshfs on mycroft, and SSH'ed into the box and ran:
```
mkdir ~/public_html/dvd
sshfs drsmall@192.168.0.16:/mnt/dvd ~/public_html/dvd
```

I entered my password, and then it mounted everything that was in /mnt/dvd on the local machine to ~/public_html/dvd, and I could see and read it.

So then, in the browser, I try:
```
http://host/~user/dvd/
```

And I got a Forbidden Error. The permissions on ~/public_html/dvd are:
```
r-x r-x r-x
```

I have yet to get Apache to be able to read the directory, yet I can read it just fine in the terminal. Anyone have some insight on this?

Dr Small

---

### Post by Dr Small on 2008-07-20
As always, I solved my own problem again :D
Added 'user_allow_other' to /etc/fuse.conf and then used this command to mount the filesystem on mycroft:
```
sshfs -o allow_other,uid=1000,gid=1000 drsmall@192.168.0.16:/mnt/dvd dvd/
```

So, I wrote an alias to simplify things :)
```
alias sshfs='sshfs -o allow_other,uid=1000,gid=1000'
```

Problem solved. :D

Dr Small

---

### Post by davidgarcin on 2009-03-06
Thanks for the tip, works great!  I was wrestling with the exact same thing!

---

### Post by altonbr on 2009-11-18
Really odd that this occurs.

I posted parallel problem (not knowing your thread existed) and only got it working once I found your notes on '-o allow_other,uid=1000,gid=1000'

[http://ubuntuforums.org/showthread.php?p=8343262](http://ubuntuforums.org/showthread.php?p=8343262)

I appreciate your help but am a little confused why such a workaround is required.

---

