---
title: "[SOLVED] Gedit won't save changes to the smb.conf file"
date: 2008-10-25
forum: General Help
---

### Post by FreakTimmah on 2008-10-25
So I'm trying to share a Ntfs hard drive but if I try to right click and hit "share this drive" it gives me an error message saying I need to add the line "userhare owner only=false" to the smb.conf file. I found the file and tried to edit it but because I wasn't logged in as root it wouldn't save. So I opened up the terminal and typed:

"sudo gedit /ect/samba/smb.conf" 

and tried to add the line that way, but it still won't save and gives the the error message 

"could not save the file /ect/samba/smb.conf unexpected error file not found" 

I feel like there must be something I'm missing here but I can't figure it out. I'm still learning the terminal so maybe that's part of it. 

Basically all I want to do is mount this drive on boot up and share it over my network. Can someone break it down for me and tell me what I need to do? I'd really appreciate any help I can get. Thanks!

---

### Post by drs305 on 2008-10-25
> **FreakTimmah said:**
> So I'm trying to share a Ntfs hard drive but if I try to right click and hit "share this drive" it gives me an error message saying I need to add the line "userhare owner only=false" to the smb.conf file. I found the file and tried to edit it but because I wasn't logged in as root it wouldn't save. So I opened up the terminal and typed:

"sudo gedit /[COLOR="Red"]ect[/COLOR]/samba/smb.conf" 

and tried to add the line that way, but it still won't save and gives the the error message 

"could not save the file /**ect**/samba/smb.conf unexpected error file not found" 

I feel like there must be something I'm missing here but I can't figure it out. I'm still learning the terminal so maybe that's part of it. 

Basically all I want to do is mount this drive on boot up and share it over my network. Can someone break it down for me and tell me what I need to do? I'd really appreciate any help I can get. Thanks!

You have a typo in the address. It should be /**etc**/ ....

Also, when using graphical apps, use 'gksudo' rather than sudo:

```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by FreakTimmah on 2008-10-25
Thank You that worked!!!! lol of course it was that simple. I really appreciate the help!

---

