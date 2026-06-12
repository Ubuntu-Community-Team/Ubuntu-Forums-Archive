---
title: "Samba with AD integration stopped working"
date: 2008-10-03
forum: General Help
---

### Post by GTHvidsten on 2008-10-03
I don't know what caused my Samba server (with AD integration) to stop working (or when), but the fact is it doesn't cooperate anymore.
I have three shares on my Samba. One public share that is accessible and writable by everyone, one for each user's home directory, and one for a common file store readable by everyone but only writable by my user.
The public share is writable for everybody (files get the nobody:nogroup membership) and works just about as it should.
The home directory share is writeable for the current user and works perfectly.
The file store share, however, doesn't work like it should at all.
The share is fully readable by my user, but I can't get it to be writable. When I check a file/folder's security properties in Windows neither the read/write/execute checkboxes are checked, and if I do try to set the permissions I get an access denied error.
I can change the permissions on the home directory just fine, though.
What do I need to do to get full access to the file store share again?

Here's my smb.conf in case you need it:

[global]
workgroup = SERVER
realm = DOMAIN.NET
preferred master = no
server string = Samba file server
security = ADS
encrypt passwords = yes
log level = 3
log file = /var/log/samba/%m
max log size = 50
winbind separator = +
printcap name = cups
printing = cups
idmap uid = 10000-20000
idmap gid = 10000-20000

[homes]
comment = Home Directories
browseable = no
writable = yes
valid users = %D+%U
obey pam restrictions = yes
create mask = 755
directory mask = 755
map hidden = no
map system = no
map readonly = no
map archive = no
store dos attributes = yes

[filestore]
comment = File Store
path = /filestore
read only = no
create mask = 755
directory mask = 755
guest only = yes
guest ok = yes
map hidden = no
map system = no
map readonly = no
map archive = no
store dos attributes = yes

[public]
comment = Public
path = /public
read only = no
create mask = 755
directory mask = 755
guest only = yes
guest ok = yes
map hidden = no
map system = no
map readonly = no
map archive = no
store dos attributes = yes

---

### Post by GTHvidsten on 2008-10-22
Here's some more information:

It seems that when I create a folder on my share that is accessible and writable to everyone anything I create gets the nobody:nogroup ownership.

You can also look at the following screenshot taken from a folder (with correct linux ownership) and see that all the permissions are gone, and I can't set them again because I don't have the permission.

[IMG]http://default.whitestone.no/temp/SambaADErrorFolderProperties.gif[/IMG]

---

