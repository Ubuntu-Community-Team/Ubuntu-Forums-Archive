---
title: "Writable / Passwordless Samba Share ?"
date: 2008-07-16
forum: General Help
---

### Post by remitaylor on 2008-07-16
Can anyone provide an example smb.conf (the relevant parts) that allows guests to write to samba shares?

I typically don't have any trouble with Samba but, since a fresh install of Hardy, I can't seem to setup any Samba shares so guests can write to the shares.  Either the shares are read-only or I get Permission Denied errors, based on the configuration (the actual directory being shared is a+rwx)

I don't care if it's a security = share configuration or security = user, I just want people to be able to access the share without using a username/password AND be able to write to it.

Thanks!

btw - i've tried dozens of different configurations so it's not worth it for my to post my current smb.conf.  after someone replies with advice, i'll try it out and post back with my full smb.conf if it doesn't work.

TIA

---

### Post by arkara on 2008-07-16
> **remitaylor said:**
> Can anyone provide an example smb.conf (the relevant parts) that allows guests to write to samba shares?

I typically don't have any trouble with Samba but, since a fresh install of Hardy, I can't seem to setup any Samba shares so guests can write to the shares.  Either the shares are read-only or I get Permission Denied errors, based on the configuration (the actual directory being shared is a+rwx)

I don't care if it's a security = share configuration or security = user, I just want people to be able to access the share without using a username/password AND be able to write to it.

Thanks!

btw - i've tried dozens of different configurations so it's not worth it for my to post my current smb.conf.  after someone replies with advice, i'll try it out and post back with my full smb.conf if it doesn't work.

TIA

I dont thing it is possible to do have samba with no password..
but to create a samba user
give in the terminal..
```
 smbpasswd -a username 
```
and you will get the following..
for example
```
root@Kubuntu:/home/aris# smbpasswd -a aris
New SMB password:
Retype new SMB password:

```
after that you will have the username and password created to get on from an other computer through samba on this computer, (hope i helped)

---

### Post by sea_monkey987 on 2008-07-16
I've attached a samba configuration file that is very close to the default one.  Changes from default:
1) guest account = nobody line.  I simply uncommented it.
2)added a netbios name line under workgroup.  This is the name windows computers will see you ubuntu by.  Uncomment this line to enable the netbios name.
3)Changed the "wins support = no" line.  Uncommented it and changed to yes.
4) Added a sample share which will allow guests (i.e. not user or password) to read/write to directory.

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
;   netbios name=insert_name_here_for_widows_to_see

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = nobody
   invalid users = root

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
[sampleshare]
path =/var
read only = no
guest ok = yes
valid users = nobody
directory mask=0777

```

Please change the path in the sample share at the end of the file.  You shouldn't share your /var.  Also note that the user "nobody" must have write permissions to the directory you are sharing.  A
```

chmod -R 777 /path/to/dir

```
will fix that.  Or, you may be able to use chown since I've read making a directory and its contents 777 permissions is not a good idea due to security.

---

### Post by remitaylor on 2008-07-16
arkara, thanks.  i had passwordless samba working fine in Gutsy.  i didn't port over my smb.conf because i was initially planning on using the Right-click > 'Sharing Options' that comes with Hardy and because i don't typically have trouble with Samba.

you'll find lots of example configurations if you google for 'passwordless samba' ... typically, the configurations use security = share and allow guests to read/write to the share, but i haven't been able to get it to work yet in Hardy.

i've seen other setups which claim to be more secure that force a user/group and keep security = user.

i'm fine with either setup, but i can't get any of them to work!  :(

i'll try one more time and post back with my smb.conf, so people have something to work with.  i have the original smb.conf backed up, tho, so i can easily apply someone's recommendation to a fresh ubuntu Hardy smb.conf.

@sea_monkey987, just spotted your reply ... trying it out ... (i know 777 is bad, just using it to test to make sure permissions aren't the issue :))

---

### Post by remitaylor on 2008-07-16
WHOA.

Thanks @sea_monkey987.  Soooo ... I used your smb.conf and changed the path to my own share, but I forgot to change the name of the share from [sampleshare]

It worked.

I changed the name of the share back ... and it broke!  Changed it to [sampleshare] again ... and it worked!

NOTE TO SELF: don't name a samba share "share"

The name of my share was [share], which has worked forever - until I did a fresh Hardy install?  Weird.  I never thought to try changing the share name!  I've tried everything else imaginable.

Lesson learned!  Thanks sea_monkey987!

---

### Post by sea_monkey987 on 2008-07-16
it should work if you change the name.  You need to restart samba:
```
sudo /etc/init.d/samba restart
```
If the client is windows, it might take a while for the name to change, but it difinitely should work.  No reason to be stuck with "sampleshare"

---

### Post by Ed1000 on 2008-08-16
Thanks for the smb.conf file.
Unfortunately though it is not working for me. Before I used your file, I could see the files on my kubuntu share from my XP machine, but did not have write access. After I used your file that is still the same. Anybody any suggestions how I could proceed to have passwordless access to my Kubuntu Shares?



Thanks

---

### Post by mb_webguy on 2008-08-16
Just out of curiosity, why does everyone still seem to be manually setting up samba shares?  I haven't done that since I installed Hardy and realized I could right-click on a folder in Nautilus, go to Sharing Options, and set up the share with the GUI.

---

### Post by Ed1000 on 2008-08-17
I finally did get it working, apparently CHMOD had not worked the first time around.
Oddly enough I still do not get the proper Workgroup name. If I leave out the "workgroup=xxxxx", it defaults to 'MSHOME'. If I then set it to "workgroup = NAME_I_Want", it is suddenly just named 'WORKGROUP'. Anybody any tips there?

@mb_webguy
I can only reply for Kubuntu: I had started out doing this in the system interface, but apparently did not get the priviliges to work, so I dived into smb.conf. In hindsight, maybe just using chmod after using the system interface would maybe have done the trick as well.

---

