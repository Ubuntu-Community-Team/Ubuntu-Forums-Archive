---
title: "Samba share no longer working (after update)"
date: 2008-11-22
forum: General Help
---

### Post by svaens on 2008-11-22
Hi all, 

Just then I needed to access my share on ubuntu Hardy, and it didn't work. 
It used to work.

I remember seeing several updates to samba since i've last used it. I didn't think to check it then, but now... i know a problem occurred.

In the first place, I created my share simply by using the new functionality in nautilus, right-click-> Sharing options, clicked a couple check-boxes and it was finished. Since it worked right away, I didn't think to have a closer look (at the smb.conf file) or make a backup. 

Having a look at it now, I notice that there is absolutely no reference to the path which i wanted to share! And when I (using nautilus) unshare it, and reshare it, still no reference to it in the smb.conf file. 


QUESTION 1: Should there be an entry in the smb.conf file after creating a share via nautilus? 

QUESTION 2: If the answer to QUESTION 1 is 'NO', where is it then configured?

QUESTION 3: should I create an entry? 

QUESTION 4: What happened to the great nautilus samba share functionality?


If anyone knows, i would love to hear it!

Kind Regards, 

svaens

---

### Post by svaens on 2008-11-22
bump

geez... 3 hours and not a single answer? Doesn't anyone have any idea?
It'd be nice if you said so. a simple, 
dunno
would be nice

---

### Post by svaens on 2008-11-23
bump...

---

### Post by svaens on 2008-11-26
bump. 
hi there. 
i'm really quite a nice guy. There's no reason not to say hello in this thread. I just want to know how to fix my Samba!

---

### Post by svaens on 2008-11-26
hmmm...

I'd still like to know how it works. 
I just checked my samba share again, and now it is working. 
BUT there is still no reference to the folder that I have shared in the smb.conf file. 

I would have expected to see something like this:

[myshare]
    path = /home/sean/myshare
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755


But, there is nothing of the sort. Well.. no reference to myshare anyway. 

How is nautilus using samba to share this directory? Where can I find the configurations if it is not in smb.conf??

please and thank you.

---

### Post by cariboo on 2008-11-26
Have a look here:

[http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html](http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html)

This may help you with your samba problem.

I've never used Nautilus to set up shares, I always use /etc/samba/smb.conf to setup my shares.

Jim

---

### Post by bab1 on 2008-11-26
> How is nautilus using samba to share this directory? Where can I find the configurations if it is not in smb.conf??

Nautilus now talks to Samba through dbus (using gvfs).  The configuration files are at: /var/lib/samba.  The dbus (gvfs) is new to 8.10, prior versions used Gnome-vfs libs. 

BTW -- The policy for bumping the thread is to wait 24 hours.

---

### Post by svaens on 2008-11-26
Hi and thank you to both of you. 

@bab1 - yes. Granted, Perhaps It was a bit hasty bumping after 3 hours. 
But I have since waited 3 days before bumping. 
I will try to be more patient next time. 

@cariboo907 - thank you. I will definitely have a look. It will no doubt come in handy when nautilus doesn't work again.

---

