---
title: "[SOLVED] Lost write access on Ubuntu Server"
date: 2008-10-02
forum: General Help
---

### Post by Ed1000 on 2008-10-02
I installed Ubuntu Server (8.04) to attach my storage media to.
I added a 1 Terabyte disk and that worked just about out of the box with regard to accessibility. I could read and write on it without having to do anything regarding my Samba config file, other than define it as a share. The section in my config file looked like this:

[Terabyte]
	browseable = yes
	user = ed,nobody
	write list = ed,nobody
	path = /media/disk

Then after a few days, I suddenly lost connection to that drive. In Webadmin I saw it was no longer mounted and I also saw I lost the mount directory 'disk' in 'media'

So I created that directory again, mounted my drive again and presto!!

However.. Though I now can read the disk, I do not have writeaccess to it anymore.
I tried adding:
     create mask=0775
     directory mask = 0775
to the Drive definition and even went as far as to give a chmod 0777 command on the directory but still no write access.


It seems to look much like the USB stick I added. On that I never managed to get write access. That definition gradually grew to:

[usb512]
	delete readonly = yes
	path = /media/usb
	force directory mode = 0775
	guest ok = yes
	force create mode = 0775
	user = ed,nobody
	create mode = 0775
	directory mode = 0775
        create mask=0777

without getting any write access

What happened here. How can I restore write access to my harddrive and how can I get it on my USB stick ( I did mount it)

Thanks
Ed

---

### Post by Ed1000 on 2008-10-02
Just in case it would help, I attach my full smb.config file below: Thanks for any help


#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	write list = ed,nobody
	username map = /etc/samba/user.map
	map to guest = bad user
	null passwords = yes
	public = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	writeable = yes
	server string = %h server (Samba, Ubuntu)
	invalid users = root
	path = /home
	unix password sync = yes
	workgroup = HOME
	valid users = ed,nobody
	syslog = 0
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###


;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

;   syslog only = no


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.

;   security = user

;   guest account = nobody


########## Domains ##########

;   domain logons = yes

;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile


;   logon drive = H:
;   logon home = \\%N\%U


;   logon script = logon.cmd


; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########


;   load printers = yes


;   printing = bsd
;   printcap name = /etc/printcap


;   printing = cups
;   printcap name = cups

############ Misc ############


;   include = /home/samba/etc/smb.conf.%m


;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


;   domain master = auto


;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


;   winbind enum groups = yes
;   winbind enum users = yes


;   usershare max shares = 100


#======================= Share Definitions =======================


;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


;   valid users = %S


;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no


;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes



;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[UbuntuEdDocs]
	path = /home/ed/Documenten


[rom0]
	path = /media/cdrom0
[Terabyte]
	browseable = yes
	user = ed,nobody
	write list = ed,nobody
	path = /media/disk
create mask=0775
directory mask = 0775



[usb512]
	oplocks = no
	delete readonly = yes
	locking = no
	path = /media/usb
	force directory mode = 0775
	force create mode = 0775
	create mask = 0777
	user = ed,nobody
	create mode = 0775
	directory mode = 0775

---

### Post by Ed1000 on 2008-10-02
Now I am completely baffled. Apparently at the same time I could not write to my harddisk anymore -something I always could before- I now CAN write to my USB stick. Something I could NOT do before.

The only change I see is that before I lost the mount for the disk the hard disk registered as a SCSI C device and the Flashdrive as a SCSI A device. After I remounted that was the other way around. Anybody have any idea?

---

### Post by Ed1000 on 2008-10-05
I am obviously left to my own devices here but I think I have it sorted. Apparently the files and folders I put on the disk were owned by 'root'. I could not alter the priviliges from within webmin and also not from the ubuntu machine because Ubuntu wil not lat you do that on a 'vfas' (FAT) formatted disk. Never mind what some people will say about adding a specific disk line to fstab.
So I emptied the disk and reformatted it in ext3. Made sure the files had no owner (on XP) and then copy them back to the disk. Runs like a charm. Obvioiusly I still wonder why at first -while still under FAT- it also worked. Problems started when it became a SCSI A instead of SCSI C
In spite of what som

---

