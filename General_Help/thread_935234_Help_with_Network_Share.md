---
title: "Help with Network Share"
date: 2008-10-01
forum: General Help
---

### Post by the_master on 2008-10-01
I need to know how to map a network drive in Ubuntu.  I've tried to do it by going to places->connect to server, but no luck.  I need to map a drive that i don't know much about other then the way i do it in windows is i type in "\\rmhsdata.mpsaz.org\myhome"  under "map a network drive" and it works.  This share is on a windows machine so i know i have to use samba, which i already have installed.  If anyone knows how to do it, it would be nice to see a screenshot of where and what i have to type in to get it working.

The tricky part is there are about 2000 different login usernames and passwords for the drive.  In windows you just have to log off and log back in in order to login with a different username.  I'm not sure if this is even possible with Ubuntu, if you know any information to help me out, that would be great.  Thanks for the help!

---

### Post by HermanAB on 2008-10-01
The simple way is to install the Konqueror file browser, then simply type:
smb://username:workgroup@server/share in the address box, then split the window and click drag drop files around.  With this Swiss Army knife, there is no need to mount shares.

Otherwise, you can manually mount a share with something like this:
# sudo mkdir /mnt/share
# mount -t cifs -o defaults,workgroup=workgroup,user=username,password=password //server/share /mnt/share

'Hope that helps!

Herman

---

### Post by the_master on 2008-10-01
> **HermanAB said:**
> The simple way is to install the Konqueror file browser, then simply type:
smb://username:workgroup@server/share in the address box, then split the window and click drag drop files around.  With this Swiss Army knife, there is no need to mount shares.

Otherwise, you can manually mount a share with something like this:
# sudo mkdir /mnt/share
# mount -t cifs -o defaults,workgroup=workgroup,user=username,password=password //server/share /mnt/share

'Hope that helps!

HermanThanks for the fast response.  I'd rather not install anything else that isn't really needed so i'd rather not install konqueror.

If i used the second method would the student have to type that command in and change their username and password every time?

---

### Post by HermanAB on 2008-10-01
Once you figured it out manually, you can add a line to /etc/fstab and have the distant share mounted when the machine reboots.

BTW, I think Nautilus (the Gnome file browser) also supports the smb protocol - it may be worth looking into.

Cheers,

Herman

---

### Post by the_master on 2008-10-01
> **HermanAB said:**
> Once you figured it out manually, you can add a line to /etc/fstab and have the distant share mounted when the machine reboots.

BTW, I think Nautilus (the Gnome file browser) also supports the smb protocol - it may be worth looking into.

Cheers,

Herman

well that would be the key to make this all work.  I'm still kinda confused on the address i'm being given where the drive is.  How do i know what part is the "//server/share /mnt/share" part? would that be the "\\rmhsdata.mpsaz.org\myhome" i posted in my first post?

---

### Post by MunkyJunky on 2008-10-01
> **HermanAB said:**
> 
BTW, I think Nautilus (the Gnome file browser) also supports the smb protocol - it may be worth looking into.


Nautilus does. 

And are you wanting to mount these shares at boot, every time?

---

### Post by the_master on 2008-10-01
> **MunkyJunky said:**
> Nautilus does. 

And are you wanting to mount these shares at boot, every time?

I guess, i want them to always be there when i login, but i have to use a different username and password for the share depending on who logs in.

---

### Post by the_master on 2008-10-05
Bump

---

### Post by the_master on 2008-10-07
Anyone else have any information that can help me out?

---

### Post by KeyserSoze93 on 2008-10-07
> **the_master said:**
> Anyone else have any information that can help me out?

Well, since your google obviously isn't working, try pointing your file browser (NAUTILUS or KONQUEROR) to "smb:///rmhsdata.mpsaz.org/myhome"

Linux uses forward slashes rather than backslashes, and it uses the Samba protocol to access windows shares, which means addresses must be prefixed with "smb:/", much like how internet addresses usually begin with "http://"

If you want to see all the shares on the network, as in Network Neighbourhood, just point it to smb://

---

### Post by the_master on 2008-10-07
> **KeyserSoze93 said:**
> Well, since your google obviously isn't working, try pointing your file browser (NAUTILUS or KONQUEROR) to "smb:///rmhsdata.mpsaz.org/myhome"

Linux uses forward slashes rather than backslashes, and it uses the Samba protocol to access windows shares, which means addresses must be prefixed with "smb:/", much like how internet addresses usually begin with "http://"

If you want to see all the shares on the network, as in Network Neighbourhood, just point it to smb://

My Google is working, i tried to search and find out some info that would help me out but couldn't, hence why i'm typeing this to you know...

But thank you for the information because it makes a lot more sense then anyone else.  I'll try it asap and then reply back with the results.

Edit: It did work and every time i log out and log back in it asks for a different username and password.  Thank you all so much for the help i'm one step closer to getting this installation working the way i want

---

