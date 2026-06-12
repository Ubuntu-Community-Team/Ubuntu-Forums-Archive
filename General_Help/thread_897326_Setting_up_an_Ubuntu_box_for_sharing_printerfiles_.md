---
title: "Setting up an Ubuntu box for sharing printer/files over LAN"
date: 2008-08-22
forum: General Help
---

### Post by MaxIBoy on 2008-08-22
I plan on building a simple computer and installing Ubuntu, and using it to share two printers (inkjet color and laser grayscale) over our wired Ethernet LAN, as well as sharing files. Our LAN consists of a simple 4-port Linkseys hub. Two WinXP Home SP2 boxes and one Ubuntu laptop will connect to this network and use the printers.

Before I buy the parts and build the server, I'd like to prototype it out with my Ubuntu laptop, as a mockup, just so I'll easily be able to do it again with the actual server. If I can successfully share a printer and some files with my laptop as the server and the XP boxes as clients, I'll build the server. If it's not possible, I'll save the money.

So guide me. I have absolutely no idea how to set up IP addresses and ports or whatever, I've tried and failed to set up networked printers before, I'm just over my head.

---

### Post by tuxulin on 2008-08-22
since its over your head i thought id provide you
with both a text illustration and visual and sound
way to get your proto working

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

i hope they help
Tuxulin

---

### Post by MaxIBoy on 2008-08-22
Thank you for those!

---

### Post by MaxIBoy on 2008-08-22
The SettingUpSamba link is more helpful because it's more up-to-date than the video.


I've run into a problem: I do everything right, but then my laptop doesn't show up in the list. In the screenshot, I can only see the two XP boxes.

---

### Post by MaxIBoy on 2008-08-22
Oh, sorry, and here is smb.conf:

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
create mask = 0644
directory mask = 0755

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
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

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

guest account = nobody
   invalid users = guest

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
comment = Home Directories
browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
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

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom



#because I couldn't find the [public] section in the file, but it was suggested in the tutorial:

[public]
   comment = shared files
#I have in fact created a folder called /home/public
   path = /home/public 
   public = yes
   writable = yes
   printable = no

```

---

### Post by qstraza on 2008-08-22
isnt your laptop running a linux? if it does, thats the reason why you cannot find it.
Samba is to see windows shares. You have to run samba server on your laptop, so all pcs will be visible, also open port 139 (i think)

EDIT:
you have 2 windows pcs and your laptop running ubuntu? On screenshot, you cannot see yourself?
im confused

---

### Post by MaxIBoy on 2008-08-22
That's right, two XP boxes and my laptop is running Linux. I'd like to configure a shared folder on the laptop that all the computers on the LAN have read/write access to, and also put all my printers on the laptop and share them. (Note that if I can successfully do this, I'm going to build a dedicated server and set it up the same way, so I can use the laptop for something else. The laptop was just a convenient Ubuntu computer which I could use as a mockup.)

---

### Post by qstraza on 2008-08-22
```

[share]
  comment = share
  path = /home/username/sharedfolder
  guest ok = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  force user = username
  force group = users

```

put this in your smb.conf, this will do a trick, go on win box and type in exprorer \\ip_of_laptop

for printer part, im in a hurry right now, will help you tomorow, if nobody else will:p

---

### Post by MaxIBoy on 2008-08-22
Thanks.

---

### Post by qstraza on 2008-08-22
Install cups if not already and add the following code in to smb.conf
```
 
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
  
printing = cups
printcap name = cups

```

---

### Post by my_key on 2008-08-22
The shortest and easiest tutorial on how to share printers in linux:

1 make sure you have "cups" installed
2 point your browser to the web interface: [http://localhost:631](http://localhost:631) 
3 tick box: make printers available for other pc's

Done. If windows doesn't pick it up add the printer by adding the following network printer from the windows box "http://<ip_of_print_server>:631/printers/<name_of_printer>"
e.g. [http://192.168.1.55:631/printers/hp3500c](http://192.168.1.55:631/printers/hp3500c)

If prompted for a user and password by the web interface, this is allways you systems username and password (possible that it needs to be a sudo-er).

This should normally work, but I don't have my ubuntu machine handy. So naming of actions might differ a little.

Edit: I've been a little incomplete, but check out this tutorial, it's great: [http://linuxreality.com/docs/ep29notes.txt](http://linuxreality.com/docs/ep29notes.txt)

---

### Post by MaxIBoy on 2008-08-23
Thanks to you both. The filesharing now works like a charm, I'm going to set up the printers tomorrow (too late tonight,) I'll let you know how it goes.

---

### Post by MikeCheck on 2008-09-06
> **tuxulin said:**
> since its over your head i thought id provide you
with both a text illustration and visual and sound
way to get your proto working

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

i hope they help
Tuxulin

That first link tells me this is in my network configuration on Ubuntu:
> 
Windows Networking
Tick Enable Windows networking
Description:       <whateveryouwant>
Domain/Workgroup:  <yourdomainorworkgroup>


My network configuration doesn't have anything about Windows networking.  It only has "Host Name" and "Domain Name."

Does anyone know where I can go to enter a workgroup name?
Thank you


Edit: I also don't have a "Shared Folders" option under my "Administration" menu.  I'm running 8.04.

---

### Post by nobull on 2008-09-06
I believe that workgroup name and domain name are essentially the same.  For home networks without a domain controller they just called it workgroup.  I just always put my workgroup name in the domain name spot.

I don't have the shared folders under administration either.  I do have an option when I right click on the folder that I want to share.

---

