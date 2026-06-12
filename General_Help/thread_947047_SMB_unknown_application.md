---
title: "SMB unknown application"
date: 2008-10-13
forum: General Help
---

### Post by skydiver|goose on 2008-10-13
Last major bug with my new 8.04 setup. I have all my backed up files on my XP PC, network IP 192.168.0.102. When I go to Places > Connect to Server, select "Windows Share", enter the above IP for the location, and then try and connect, I get an error stating:

Can't display location "smb://192.168.0.102/"
No application is registered as handling this file



how can I fix this? 40 GB worth of files I need to get back on my laptop ASAP :/

---

### Post by Ocxic on 2008-10-13
You need to enter the server and the share in the dialog box that comes up.

---

### Post by skydiver|goose on 2008-10-13
what do you mean by the share?

---

### Post by tonytr on 2008-10-14
Try running smbclient from a terminal window against the ip address of your XP box. If you get a password prompt just hit return.

```
ttravlos@deli:~$ smbclient -L 192.168.1.250
Password: 
Anonymous login successful
Domain=[KERR_AVE] OS=[Unix] Server=[Samba 3.0.24]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (hp6535 server) 
	tonyt           Disk      
	samba           Disk      
	print$          Disk      Printer Drivers
	OfficeJet_G85   Printer   
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]

	Server               Comment
	---------            -------
	HP6535               hp6535 server

	Workgroup            Master
	---------            -------
	WORKGROUP            ZERO

```

You should see the XP shares listed, assuming you have "shared" from the XP box.

If smbclient is not found you can run "sudo apt-get install smbclient".

Regards

---

### Post by Ocxic on 2008-10-14
in the dialog box that come up, there is a box for the server and there is a seperate box for the share that you want to connect to. 

in windows you have to share a folder or drive to be able to access anything.

---

