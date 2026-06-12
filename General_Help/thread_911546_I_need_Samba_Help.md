---
title: "I need Samba Help"
date: 2008-09-05
forum: General Help
---

### Post by afbase on 2008-09-05
Hi.

I was wondering how I could just connect to my windows share account. i have the following installed on hardy:
```
smbcacls    smbcquotas  smbmount    smbstatus   smbumount   
smbclient   smbd        smbpasswd   smbtar      
smbcontrol  smbget      smbspool    smbtree  
```its a [udrive account]("https://www.csun.edu/%7Ecsunitr/guides/webpublishing/general.html#publish"), if any of you are familiar with that (certain universities offer it).  Click on that last link.  It gives some background on what i've attempted to do in Gnome/Nautilus with no success.

I installed Samba client and samba server through synaptic.  I haven't modified the samba config file.  In gnome, i've tried numerous ways to connect to the windows share through Places > connect to a server > selecting Windows share > filling in the information smb://udrive.csun.edu/cmb33595.

No luck.  Any help is appreciated.

---

### Post by wolfen69 on 2008-09-05
do ```
gksudo gedit /etc/samba/smb.conf
``` go to the first section and change workgroup to whatever you need for your network. also change security to user. here is an example: ```
[global]
workgroup = **eds_network**
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = **user**
```

make sure nautilus-share is also installed. post back if you have any problems.

edit: you will also need to add yourself to sambashare group. ```
sudo adduser username sambashare
```

---

### Post by afbase on 2008-09-05
> **wolfen69 said:**
> do ```
gksudo gedit /etc/samba/smb.conf
``` go to the first section and change workgroup to whatever you need for your network. also change security to user. here is an example: ```
[global]
workgroup = **eds_network**
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = **user**
```make sure nautilus-share is also installed. post back if you have any problems.

edit: you will also need to add yourself to sambashare group. ```
sudo adduser username sambashare
```

still nothing.  It says that it cannot mount drive.

---

### Post by afbase on 2008-09-05
This is the global section of my smb.conf:
```

[global]
netbios name = Samba24
server string = %h server 
workgroup = 
security = cmb33595 
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24 
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
syslog = 0
panic action = /usr/share/samba/panic-action %d
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.%m
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = true
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins server =
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no


```There is no domain to the udrive server.  I'm supposed to just point it to smb://udrive.csun.edu/cmb33595 , type my username and password.

---

### Post by afbase on 2008-10-25
```
clinton@clinton-laptop:~$ smbclient  smb://udrive.csun.edu/cmb33595 -U cmb33595
Packet send failed to 255.255.255.100(137) ERRNO=Invalid argument
Connection to smb: failed (Error NT_STATUS_BAD_NETWORK_NAME)

```I've tried modifying my smb.conf but still no luck. My smb.conf file is shown at the post of this post.  the udrive is located at my university.  I am on a network at my home my ip is 10.0.0.105  and my router's ip range is 10.0.0.0/255.   I have tried pinging udrive.csun.edu and it isn't working.  I'm wondering if my networking configuration is the culprit.  I also checked to see if SMBD was running:
```
clinton@clinton-laptop:~$ sudo /etc/init.d/samba status
[sudo] password for clinton: 
 * SMBD is running

```smb.conf:
```
[global]
netbios name = Samba24
server string = %h server 
workgroup = 
security = user
hosts allow = 127. 192.168.0. 
interfaces = 127.0.0.1/8 192.168.0.0/24 10.0.0.0/155
remote announce = 10.0.0.255
remote browse sync = 10.0.0.255
syslog = 0
panic action = /usr/share/samba/panic-action %d
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.%m
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = true
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins server =
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =

```

---

### Post by mbeach on 2008-10-26
it looks to me like you are combining sharing and trying to mount a share.  What happens when you:

```

mkdir /home/yourusername/udrive
mount -t smbfs -o username=campusUserName,password=campusPassword //udrive.csun.edu/login /home/yourusername/udrive

```

edit:
you might need to use "sudo mount ..."
if it works, add the appropriate line to your /etc/fstab, then I believe you won't need to be root to mount it.

---

### Post by afbase on 2008-10-26
It just hangs.
```
clinton@clinton-laptop:~$ sudo mount -t smbfs -o username=cmb35,password=some_password //udrive.csun.edu/cmb35 /home/clinton/udrive
*cursor just blinks*

```
I've tried pinging and i get even stranger news:
```
clinton@clinton-laptop:~$ ping udrive.csun.edu
ping: unknown host udrive.csun.edu

```

---

### Post by sea_monkey987 on 2008-10-26
> **afbase said:**
> 
I've tried pinging and i get even stranger news:
```
clinton@clinton-laptop:~$ ping udrive.csun.edu
ping: unknown host udrive.csun.edu

```

you're not alone.  i'm getting that too.  pinging yahoo.com is successful though.

---

### Post by afbase on 2008-10-26
So i just realized why i haven't been able to connect to this stupid Udrive.  I have to be connected to the University VPN!!!! 

My professor failed to mention that part of the instructions.

Only trouble is I am not sure what to edit my setting to connect to the VPN.  CSUN gives instructions for windows, but i'm trying to put as much information into the gnome network manager to connect and it is still not working
[URL="http://www.csun.edu/it/training/guides/vpnwindguid.html"]
http://www.csun.edu/it/training/guides/vpnwindguid.html[/URL]

---

