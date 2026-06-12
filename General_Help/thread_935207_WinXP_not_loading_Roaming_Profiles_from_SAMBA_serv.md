---
title: "WinXP not loading Roaming Profiles from SAMBA server"
date: 2008-10-01
forum: General Help
---

### Post by Avinash.Rao on 2008-10-01
Hi all,

I have configured Samba 3.0.28a on Ubuntu studio 8.04 - AMD64. It is configured as a PDC and the users get login to their respective home directories. But, the profile is not loading. So, if users make any changes to their desktop or my documents,they don't get loaded. The error is "windows didnot load your roaming profile and is attempting to log you on with your local profile.Changes to the profile will not be copied to the server when you logoff. Windows did not load your profile because a server copy of the profile folder already exists that does not have the correct security. Either the current user or the Administrator's group must be the owner of the folder." Contact your network administrator.


" Strangely, this used to work when i first created these user accounts. Below is my smb.conf file

# Global parameters
[global]
workgroup = abcd
netbios name = server
;interfaces = eth1, lo
;bind interfaces only = Yes
passdb backend = tdbsam

hosts allow = 10.10.10.0/24
security = user
smb ports = 139
add user script = /usr/sbin/useradd -m '%u'
delete user script = /usr/sbin/userdel -r '%u'
add group script = /usr/sbin/groupadd '%g'
delete group script = /usr/sbin/groupdel '%g'
add user to group script = /usr/sbin/usermod -G '%g' '%u'
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u'
include = /etc/samba/dc-common.conf
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

[share]
comment = Student common Share Directory
browsable=yes
path = /export/
read only = No
writable = yes

Contents of /etc/samba/dc-common.conf

# Global parameters
[global]
;shutdown script = /var/lib/samba/scripts/shutdown.sh
;abort shutdown script = /sbin/shutdown -c

domain logons = Yes
preferred master = Yes
domain master = yes
wins support = Yes
os level = 65

;logon path = \\%L\profiles\%U
;logon drive = h:
;logon home = \\%L\%U
;logon script = logon.bat
include = /etc/samba/common.conf

[homes]
comment = Home Directory
valid users = %S
read only = No
browseable = No
path = /home/%u

[profiles]
comment = Profile Share
path = /var/lib/samba/profiles
read only = No
;profile acls = Yes
writable = yes
browsable = no

Contents of common.conf

[global]

username map = /etc/samba/smbusers
log level = 1
syslog = 0
log file = /var/log/samba/%m
max log size = 50
smb ports = 139
name resolve order = wins bcast hosts
time server = Yes
printcap name = CUPS
show add printer wizard = No
;shutdown script = /var/lib/samba/scripts/shutdown.sh
abort shutdown script = /sbin/shutdown -c
utmp = Yes
map acl inherit = Yes
printing = cups
#veto files = /*.eml/*.nws/*.{*}/
#veto oplock files = /*.doc/*.xls/*.mdb/
;include =
# Share and Service Definitions are common to all servers
;[printers]
;comment = SMB Print Spool
;path = /var/spool/samba
;guest ok = Yes
;printable = Yes
;use client driver = Yes
;default devmode = Yes
;browseable = No
;[apps]
;comment = Application Files
;path = /apps
;admin users = sambauser
;read only = No

The profiles directory is under /var/lib/samba/profiles

The permissions of the /var/lib/samba directory is
drwxr-xr-x 8 root root 4096 2008-10-01 16:21 samba

The Permissions of the /var/lib/samba/profiles directory:
drwxr-xr-x 30 root root 4096 2008-09-24 16:37 profiles

Under the profiles directories, user directories are created and they have username.users permission. For example..
drwxr-xr-x 13 priya users 4096 2008-10-01 12:31 priya

Sorry for the long post.
can someone help me with this
Avinash

---

### Post by Avinash.Rao on 2008-10-04
Hi Guys, 

I am using WinXP - SP2 and i downloaded samba doc, but where can i find it?
I figured out the problem. There was a mistake in the profiles path. After installing samba, i used the pdbedit command to set account policies on each user, and i guess by mistake the profiles path was entered wrongly. I changed the profiles path using pdbedit command and it worked. But, i had to do this manually for each user.

**1) How can i use the pdbedit command to set account policies for all users at once? say for example i want to change the account password policy for 30 users at once?**

The above scenario leads me to a question. The default profiles path in samba is in the users home directory /home/username/profile directory. But, i have a different path set for profiles in smb.conf file which is /var/lib/samba/profiles/username. Now which takes the precedence?

I tested this yesterday, i created a new samba user, using smbpasswd -a username command. at the end, in the username details, the profile path is automatically set to /home/username/profile directory. But, in my smb.conf file i have defined a profiles share which is under /var/lib/samba/profiles/username. Now, there is a conflict here? 

[profiles]
comment = Profile Share
path = /var/lib/samba/profiles
read only = No
;profile acls = Yes
writable = yes
browsable = no
logon path = \\%L\profiles\%U
logon drive = p:

What is the use of using these parameters then? like logon path = \\%L\profiles\%U etc..?? 

Thanks for the support
Avinash


> **Avinash.Rao said:**
> Hi all,

I have configured Samba 3.0.28a on Ubuntu studio 8.04 - AMD64. It is configured as a PDC and the users get login to their respective home directories. But, the profile is not loading. So, if users make any changes to their desktop or my documents,they don't get loaded. The error is "windows didnot load your roaming profile and is attempting to log you on with your local profile.Changes to the profile will not be copied to the server when you logoff. Windows did not load your profile because a server copy of the profile folder already exists that does not have the correct security. Either the current user or the Administrator's group must be the owner of the folder." Contact your network administrator.


" Strangely, this used to work when i first created these user accounts. Below is my smb.conf file

# Global parameters
[global]
workgroup = abcd
netbios name = server
;interfaces = eth1, lo
;bind interfaces only = Yes
passdb backend = tdbsam

hosts allow = 10.10.10.0/24
security = user
smb ports = 139
add user script = /usr/sbin/useradd -m '%u'
delete user script = /usr/sbin/userdel -r '%u'
add group script = /usr/sbin/groupadd '%g'
delete group script = /usr/sbin/groupdel '%g'
add user to group script = /usr/sbin/usermod -G '%g' '%u'
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u'
include = /etc/samba/dc-common.conf
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

[share]
comment = Student common Share Directory
browsable=yes
path = /export/
read only = No
writable = yes

Contents of /etc/samba/dc-common.conf

# Global parameters
[global]
;shutdown script = /var/lib/samba/scripts/shutdown.sh
;abort shutdown script = /sbin/shutdown -c

domain logons = Yes
preferred master = Yes
domain master = yes
wins support = Yes
os level = 65

;logon path = \\%L\profiles\%U
;logon drive = h:
;logon home = \\%L\%U
;logon script = logon.bat
include = /etc/samba/common.conf

[homes]
comment = Home Directory
valid users = %S
read only = No
browseable = No
path = /home/%u

[profiles]
comment = Profile Share
path = /var/lib/samba/profiles
read only = No
;profile acls = Yes
writable = yes
browsable = no

Contents of common.conf

[global]

username map = /etc/samba/smbusers
log level = 1
syslog = 0
log file = /var/log/samba/%m
max log size = 50
smb ports = 139
name resolve order = wins bcast hosts
time server = Yes
printcap name = CUPS
show add printer wizard = No
;shutdown script = /var/lib/samba/scripts/shutdown.sh
abort shutdown script = /sbin/shutdown -c
utmp = Yes
map acl inherit = Yes
printing = cups
#veto files = /*.eml/*.nws/*.{*}/
#veto oplock files = /*.doc/*.xls/*.mdb/
;include =
# Share and Service Definitions are common to all servers
;[printers]
;comment = SMB Print Spool
;path = /var/spool/samba
;guest ok = Yes
;printable = Yes
;use client driver = Yes
;default devmode = Yes
;browseable = No
;[apps]
;comment = Application Files
;path = /apps
;admin users = sambauser
;read only = No

The profiles directory is under /var/lib/samba/profiles

The permissions of the /var/lib/samba directory is
drwxr-xr-x 8 root root 4096 2008-10-01 16:21 samba

The Permissions of the /var/lib/samba/profiles directory:
drwxr-xr-x 30 root root 4096 2008-09-24 16:37 profiles

Under the profiles directories, user directories are created and they have username.users permission. For example..
drwxr-xr-x 13 priya users 4096 2008-10-01 12:31 priya

Sorry for the long post.
can someone help me with this
Avinash

---

