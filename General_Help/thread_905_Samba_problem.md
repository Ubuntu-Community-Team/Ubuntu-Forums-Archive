---
title: "Samba problem"
date: 2004-10-16
forum: General Help
---

### Post by WimVriend on 2004-10-16
Hello,
From my Ubuntu computer I can see the other 2 WinXP computers in our house/network. But I did not see the shared printers on those WinXP computers.
And from a WinXP computer i can not see my Ubuntu computer. In Gnome conf editor I saw that my computer belongs to the domain workgroup, how can I change this to werkgroep ?
TIA
Wim

---

### Post by triad169 on 2004-10-16
Computer menu -&gt; System Configuration -&gt; Networking

Click on the *general* tab and you can set there.

Printers do not show up under gnome network browser but you can add via Computer menu -&gt; System Configuration -&gt; Printing

Triad

---

### Post by WimVriend on 2004-10-16
[quote=triad169]Computer menu -&gt; System Configuration -&gt; Networking

Click on the *general* tab and you can set there.

Printers do not show up under gnome network browser but you can add via Computer menu -&gt; System Configuration -&gt; Printing

Triad[/quote]
Sorry,
I forgot to mentioned that, but I did that already. That's why I found it strange to see in gnome conf editor that there is still workgroup instead of werkgroep.  And  when I try to connect from a win computer I have to fill in a username  and password, I rather have a share connection without username and password, because I don't know how to manage that :-)
wim

---

### Post by triad169 on 2004-10-16
can u post ouput of

```
cat /etc/samba/smb.conf
```

when run from terminal/

Triad

---

### Post by WimVriend on 2004-10-16
[quote=triad169]can u post ouput of

```
cat /etc/samba/smb.conf
```

when run from terminal/

Triad[/quote]

Hello Triad,
Here is what you asking for.
Really preciate you're help

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Werkgroep

# server string is the equivalent of the NT Description field
   server string = %h (Samba, Ubuntu)

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


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton &lt;aluton@hybrigenics.fr&gt; for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
 ;  load printers = no

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &amp;

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
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
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by triad169 on 2004-10-16
Samba workgroup definition is setup properly.  I noticed under my gconf-editor it shows workgroup name as empty.  Might be a bug in gnome because my workgroup is properly designated for the network.

As for password less access to your computer I do not recommend this.  Doesnt windows XP give you the option of remembering the username and password when you connect to a network share? Just do a search under Google for:
> windows xp network password username remember

Lot's of guide on how to setup XP.  Its pretty basic.
 

Setting up Samba for user access is pretty straightforward.  at terminal type:

```
smbpasswd -a username
```

it will ask you what password you want use twice.  username is either your user account on Ubuntu or if you have created a specific user via User and Groups for network access.  (This must be a valid user on you computer)

Once that is done just edit your smb.conf file and add a share at the end of the file.  I took your smb.conf and created an example from it as follows
> 
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = Werkgroep
server string = %h (Samba, Ubuntu)
dns proxy = no


#### Debugging/Accounting ####

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0

####### Authentication #######

security = user
encrypt passwords = true
passdb backend = tdbsam guest
obey pam restrictions = yes
; guest account = nobody
invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
; unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton &lt;aluton@hybrigenics.fr&gt; for
# sending the correct chat script for the passwd program in Debian Potato).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .


############ Misc ############

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

#======================= Share Definitions =======================

[share]
   comment = Shares
   path = /mnt/share/
   valid users = triad
   public = no
   writable = yes
   printable = no


A good basic guide for samba setup can be found here:

[http://www.gentoo.org/doc/en/quick-samba-howto.xml](http://www.gentoo.org/doc/en/quick-samba-howto.xml)

It pertains to setting up on gentoo but alot of the points can be used in Ubuntu.  There is a GUI Management Program for Samba called SWAT but unfortunatly it is not is the Restricted repositories under synaptic.  They do have in Unverse but it forces you to Upgrade Samba and I dont know how wise this might be under Ubuntu.  Might break something.

Also if you make any changes to smb.conf always run


```
sudo /etc/init.d/samba restart
```

This will restart your samba server and put your changes into effect.  this is alot to digest but you have to Understand that Samba is Full fledged Server Component.

Oh well I hope this helped out.

Triad

---

### Post by cseg on 2004-10-19
This is just to note that I have installed Ubuntu twice now, and Samba seems broken now.

The first installation (first release of Warty), samba worked.  I could access shares on other computers via the Network option on the menu, and after installing smbfs, I could mount then locally.

I just finished installing the second release of Warty (10/13) from scratch.  Samba now does not work.  I can neither see shares via the Network option, nor can I mount them locally.  When I try to do so, I get this:

mount: wrong fs type, bad option, bad superblock on //host/share
       or too many mounted file systems

Further, smbfs no longer seems to be a separate package.  I /may/ have enabled universe last time, I don't recall.  But this time I have not (so far) and smbfs is definitely not available outside the samba package.

---

