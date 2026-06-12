---
title: "How to do this?"
date: 2008-11-30
forum: General Help
---

### Post by rmcellig on 2008-11-30
How exactly do I do this. I am pretty new to this. I am the administrator.


'net usershare' returned error 255: net usershare add: cannot share path /home/rmcellig/Desktop/Link to My Storage as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

---

### Post by fragos on 2008-11-30
<Alt>F2
gksudo gedit /etc/samba/smb.conf

---

### Post by rmcellig on 2008-12-02
Thanks!!

Here is the Global section of the smb.conf file. How do I add the line of code mentioned in my origanal post?

[global]

# usershare owner only = False

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

---

### Post by Fahuadai on 2008-12-02
> **rmcellig said:**
> Thanks!!

usershare owner only = False




Remove the # from the line and save the file. (remove the comment)

Then you can restart samba from the terminal using:

sudo /etc/init.d/samba restart

---

### Post by rmcellig on 2008-12-02
That worked great!! Thanks so much!!

---

### Post by docew on 2008-12-09
This thread helped me a lot, thanks.

It seems silly that by default an administrator would not be able share a folder without going through this hassle. Is it meant to be esoteric? How would a beginner know which commands he needs to type in to the terminal to restart samba?

These forums are a real life saver.

---

