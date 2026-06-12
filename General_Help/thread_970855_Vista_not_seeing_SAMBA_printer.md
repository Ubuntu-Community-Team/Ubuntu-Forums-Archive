---
title: "Vista not seeing SAMBA printer"
date: 2008-11-04
forum: General Help
---

### Post by joel@parke.ods.org on 2008-11-04
Hi all,

Is there an expected bug related to using SAMBA shared printers with 8.10?  I upgraded from 8.04 where everything was working.  Now I can't see anything.  Windows Vista says:

\\PAKRE is not accessible. You might not have permissions to use this network resource.  Contact the administrator of this server to find out if you have access permissions.

The Server service is not started.

smbclient -L parke LISTS:
Enter joel's password: 
Domain=[PARKE] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	homes           Disk      Home Directories
	PhotoSmart      Printer   
	HPHP            Printer   
	joel            Disk      
	IPC$            IPC       IPC Service (Samba Server)
Domain=[PARKE] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            

Why can't I access the printer, or see any folders or printers?  From looking around, this might be related to a know bug. Is that true and any idea how long this will persist?

Thanks,
Joel Parke

PS if it helps, here is my smb.conf file:
joel@parke:/etc/samba$ cat smb.conf
# Global parameters
[global]
	level2 oplocks = no
	oplocks = no
	debug level = 1
	printing = cups
	printcap = cups
	server string = Samba Server
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passwd chat = *New*password* %n\n *Retype*new*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*
	unix password sync = Yes
	log file = /var/log/samba/%m.log
	max log size = 0
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	dns proxy = Yes
	disable spoolss = no

	interfaces = 192.168.1.0/255.255.255.0 127.0.0.1
	bind interfaces only = yes  

	workgroup = WORKGROUP
	security = user
	username map = /etc/samba/smbusers
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /bin/false
	winbind use default domain = no
	wins support = yes

[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0664
	directory mask = 0775
	browseable = Yes

[PhotoSmart]
	read only = Yes
	path = /var/spool/samba
	guest ok = Yes
	printable = Yes
	printer name = "PhotoSmart-8200"
	use client driver = yes

[HPHP]
	read only = Yes
	path = /var/spool/samba
	guest ok = Yes
	printable = Yes
	printer name = "Hewlett-Packard HP LaserJet 2200"
	use client driver = yes

[joel]
	path = /home/joel
	available = yes
	browsable = yes
	public = yes
	writable = yes

---

### Post by cmnorton on 2008-11-05
Any chance your samba (or other) config files were saved off and then new ones laid down during the upgrade?

---

### Post by joel@parke.ods.org on 2008-11-05
Hi,

Thanks for the reply.  I believe that I kept all the old samba config files during the upgrade.  Everything looks good - I can even connect to my shares on Ubuntu.  The problem is that I can't see them and I can't print to my printer on Ubuntu through Samba.  This all worked before the upgrade.

Any ideas out there on how to fix this, or is it a known bug????

Thanks,
Joel Parke

---

### Post by bab1 on 2008-11-05
I don't think this is a bug.  Vista has upgraded encryption.  See [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=954691") for some ideas.

---

### Post by joel@parke.ods.org on 2008-11-05
Thanks for these pointers.  But as far as I can determine, these are more related to seeing Vista shares from Ubuntu.  What I need to see are Ubuntu shares from Vista.  So the changes suggested didn't seem to change anything.

BUT THE PUZZLE is that all this worked seamlessly with Ubuntu 8.04 and now with 8.10 the shares and printers on Ubuntu are invisible when attempting to see them on Vista.  Although I can do something like net use x: \\parke\joel
and then dir x: lists all the files, etc.

So what changed in 8.04 -> 8.10????

Thanks!

---

