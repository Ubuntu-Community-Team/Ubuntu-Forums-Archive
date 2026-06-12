---
title: "Gmailfs on Startup.."
date: 2008-07-18
forum: General Help
---

### Post by Ubunutu Newbie on 2008-07-18
Hi,

I am still not really sure if it is the right Thread for my problem.. :confused:

Yesterday, I installed Gmailfs on my Ubuntu Hardy Heron System, but now I am asking myself if it is possible to start Gmailfs automatically on startup? Can anybody help me??

Normally, I mount my Gmailaccount using this code

```

sudo mount.gmailfs /usr/lib/python2.5/site-packages/gmailfs.py /media/gmailfs -o username=my googlemail username,password=my googlemail password,fsname=zOlRRa

```

It is working great. But I don't want to type this in terminal, all the time when I am needing it. I want that my system is doing it automatically.

// edit: and is there a way to get access with out root? I mean when I want to upload something on my gmail account, I have to open it with

```

sudo nautilus

```

then change to my gmailfs folder and finally, I can upload any file I want. But is this also possible to get access as a normal user??

Thanks for any help.. :)

---

### Post by joshsmith on 2008-07-18
to do something automatically at startup, simply add the command in the dialog 
system>preferences>sessions

as you have a program needing sudo permissions. you need to supply the password

you can have it ask you for the password by making the command be
gksu mount.gmailfs /usr/lib/python2.5/site-packages/gmailfs.py /media/gmailfs -o username=my googlemail username,password=my googlemail password,fsname=zOlRRa

or have it do it automatically by doing
echo yourpassword | sudo -S mount.gmailfs /usr/lib/python2.5/site-packages/gmailfs.py /media/gmailfs -o username=my googlemail username,password=my googlemail password,fsname=zOlRRa
(replacing yourpassword)

---

### Post by norkov on 2009-05-02
First you create a folder under media where you have writing permissions:

```

sudo mkdir /media/gdrive 
sudo chown your-user-name /media/gdrive 

```The the little secret is to add yourself to the fuse group:

```
 sudo chgrp fuse /dev/fuse
 sudo usermod -a -G fuse your-user-name
```Then you can mount without using sudo/gksudo:

```
mount.gmailfs /usr/lib/python2.5/site-packages/gmailfs.py /media/gdrive -o username=your-gmail-username,password=your-gmail-password,fsname=anything-you-want-that-is-hard-to-guess

mount.gmailfs /usr/lib/python2.5/site-packages/gmailfs.py /media/gdrive -o username=your-gmail-username,password=your-gmail-password,fsname=anything-you-want-that-is-hard-to-guess

```And you can add that to startup applications as stated above and you have your gmail filesystem mounted at startup.

You may want to check these threads too:
[http://ubuntuforums.org/showthread.php?t=660493](http://ubuntuforums.org/showthread.php?t=660493)

[http://ubuntuforums.org/showthread.php?t=660493](http://ubuntuforums.org/showthread.php?t=660493)

And use curlftpfs if you're interested in mounting ftp sites at startup:
[http://ubuntuforums.org/showthread.php?t=789091](http://ubuntuforums.org/showthread.php?t=789091)

---

