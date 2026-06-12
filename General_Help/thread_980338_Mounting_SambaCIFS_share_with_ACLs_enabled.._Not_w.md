---
title: "Mounting Samba/CIFS share with ACLs enabled.. Not working"
date: 2008-11-12
forum: General Help
---

### Post by bagg on 2008-11-12
My setup consists of a LDAP/Samba server, both work fine, with the exception that I can not get ACLs to work on the Linux client that is mounting the share.

Versions:
Server Debian Etch 
Server Kernel: 2.6.26-1-686
Server Samba: 3.2.4


Client OS: Ubuntu 8.04
Kernel: 2.6.24-21-generic
mount.cifs version: 1.10-3.0.28a

The following is on the server my client side will follow after it:
/etc/fstab/
```
/dev/sda1       /data_store     ext3    defaults,acl   0       2
```
/etc/samba/smb.conf
```
[global]
	workgroup = WORKGROUP
	server string = %h server
	null passwords = Yes
	obey pam restrictions = Yes
	passdb backend = ldapsam:ldap://192.168.1.100
	passwd program = /usr/sbin/smbldap-passwd %u
	passwd chat = *New*password* %n\n *Retype*new*password* %n\n *password*updat
ed*successfully* .
	log level = 0 
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 0
	name resolve order = wins lmhosts hosts bcast
	load printers = No
	printcap name = /dev/null
	disable spoolss = Yes
	add user script = /usr/sbin/smbldap-useradd -m %u
	delete user script = /usr/sbin/smbldap-userdel %u
	add group script = /usr/sbin/smbldap-groupadd -p %g
	delete group script = /usr/sbin/smbldap-groupdel %g
	add user to group script = /usr/sbin/smbldap-groupmod -m %g %u
	delete user from group script = /usr/sbin/smbldap-groupmod -x %g %u
	set primary group script = /usr/sbin/smbldap-usermod -g %g %u
	add machine script = /usr/sbin/smbldap-useradd -w %u
	logon path = 
	domain logons = Yes
	os level = 65
	preferred master = Yes
	domain master = Yes
	dns proxy = No
	ldap admin dn = cn=admin,dc=example,dc=com
	ldap group suffix = ou=groups
	ldap idmap suffix = ou=idmap
	ldap machine suffix = ou=machines
	ldap suffix = dc=lan
	ldap user suffix = ou=users
	panic action = /usr/share/samba/panic-action %d
	ldapsam:trusted = true
	invalid users = root
	printer admin = root
	ea support = Yes
	printing = bsd
	print command = lpr -r -P'%p' %s
	lpq command = lpq -P'%p'
	lprm command = lprm -P'%p' %j

[data]
	comment = data
	path = /data_store/public/
	read only = No
	force create mode = 02770
	inherit permissions = Yes
	inherit acls = Yes
	inherit owner = Yes
	hide unreadable = Yes
	dos filemode = Yes
```

On the client:
/etc/fstab
```
//192.168.1.100/data   /mnt/myserver smbfs  acl,auto,credentials=/etc/samba
/creds,rw,user 0 0
```

```
 ~ $ mount
//192.168.1.100/data on /mnt/myserver type cifs (rw,mand,noexec,nosuid,nodev)

```

```
 $ setfacl -m u:mark:rwx wtf.txt 
setfacl: wtf.txt: Operation not supported
```

Whew, with all that said, can someone help please?

---

