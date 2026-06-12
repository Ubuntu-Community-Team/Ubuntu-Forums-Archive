---
title: "Window shares"
date: 2008-09-25
forum: General Help
---

### Post by trestamanos on 2008-09-25
I am trying to connect my laptop with Ubuntu to the Server using Win 2003 Business.  
From what I have read is not easy for the average user to fig this out?

What do i need to know to make this work?

I know three things: User name, password and the name of the Workgroup thats being shared.  I also know the IP Address to connect remotely.

Anything else i need to know?

I did some reading on Samba but I dont understand the fields equivalent to Windows.

Any help would be appreciated.

Thanks!

tres

---

### Post by ryanhaigh on 2008-09-25
If your ubunut machine is the client connecting to the shares on the Win2k3 server all you need to do is press Alt-F2 to bring up the run dialog, then enter:
```

smb://IP.Of.Ser.ver/share
```
You will then be asked for the username/password, note that you can also use the servers hostname/computername rather than the ip address.

There is a lot of information on using [samba with ubuntu]("https://help.ubuntu.com/community/SettingUpSamba") here but if connecting as a client is all you need then what I have suggested above should be all you need

---

### Post by trestamanos on 2008-09-26
IT TIMES OUT...........](*,)](*,)

I read on that link you sent me that certain clients have to use cifs instead of smb when dealing with win 2003 server?

thanks for your input

tres

---

### Post by ryanhaigh on 2008-09-26
Have you tried the CIFS option. I had a quick look and found t[his page]("http://www.swerdna.net.au/linhowtosambacifs.html") which has a section on mounting a CIFS share temporarily which is all you need to test that it works. Once that is done you can look at using the more involved process mentioned in the previously linked page.

---

