---
title: "samba/windows file server woes, can't connect to a share"
date: 2008-09-09
forum: General Help
---

### Post by jerome1232 on 2008-09-09
Okay I've had this working before my desktops motherboard recently kicked the bucket so now I have a spare in there, during my troubleshooting when funny things were going wrong I reinstalled my nicely configured Ubuntu (including formating my /home and /mnt/data)

So now I'm reconfigureing getting it the way I like it, all of my media files are sitting on a Windows Vista SP1 Home Premium (god I hate the 20 versions MS does) Laptop. So I tell vista to share some folders:

c:/Users/Jeremy/Videos
c:/Users/Jeremy/Music
c:/Users/Jeremy/Pictures
c:/Users/Jeremy/Documents

I run over to my ubuntu machine, username is jeremy and run
```
sudo smbpasswd jeremy
```
type the password for windows, retype it now I run
```
jeremy@lifebane:~$ smbtree
Password: 
MSHOME
HOMELAN
	\\DARKSHORE      		
		\\DARKSHORE\Users          	
		\\DARKSHORE\Public         	
		\\DARKSHORE\print$         	Printer Drivers
		\\DARKSHORE\IPC$           	Remote IPC
		\\DARKSHORE\D$             	Default share
		\\DARKSHORE\C$             	Default share
		\\DARKSHORE\ADMIN$         	Remote Admin
jeremy@lifebane:~$ smbclient //DARKSHORE//Users
Password: 
Domain=[DARKSHORE] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
jeremy@lifebane:~$ smbclient //DARKSHORE//Users -U jeremy -W HOMELAN
Password: 
Domain=[DARKSHORE] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
jeremy@lifebane:~$ smbclient //DARKSHORE//Users -U Jeremy -W HOMELAN
Password: 
Domain=[DARKSHORE] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
jeremy@lifebane:~$ smbclient -L DARKSHORE -U jeremy
Password: 
Domain=[DARKSHORE] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	D$              Disk      Default share
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	Public          Disk      
	Users           Disk      
Domain=[DARKSHORE] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
```

I am at a complete loss as to why this is failing... (yes I am positive I'm using the correct password)



EDIT: Well using nautilus works (ctrl+l, smb://DARKSHORE/Users) asks me for a password then shows the share so problem solved but what am I doing wrong on the command line?

---

