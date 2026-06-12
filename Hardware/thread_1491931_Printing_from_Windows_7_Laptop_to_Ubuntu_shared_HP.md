---
title: "Printing from Windows 7 Laptop to Ubuntu shared HP Printer"
date: 2010-05-24
forum: Hardware
---

### Post by fireman71 on 2010-05-24
I am running into a very vexing problem. I am trying to setup my better
half's laptop running windows 7 (she wont convert...yet) so that it can
print to a HP Officejet 5600 series all in one. This printer works fine
from ubuntu, from my laptop running ubuntu, from her old laptop running
windows XP, and from a friend's laptop running windows vista.

I have tried several howtos and discussions regarding different ways to
install the printer on windows 7. I have IPP installed (several other
discussions claimed their problem was fixed by installing this in
windows 7, but it doesn't seem to affect mine.)

/var/log/cups/access_log shows no entries when I try to print from the
windows 7 laptop and error_log as well as page_log are empty.

samba logs show the windows 7 laptop connecting to shared file systems
just fine.
I have included my smb.conf, cupsd.conf, and the printers.conf files
below.

All assistance is greatly appreciated!

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#

#======================= Global Settings =======================

[global]
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*
\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        username map = /etc/samba/smbusers
        map to guest = bad user
        passwd program = /usr/bin/passwd %u
        dns proxy = no
        netbios name = server
        writeable = yes
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        workgroup = MYGROUP
        os level = 20
        security = user
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        usershare allow guests = yes
        max log size = 1000
        pam password change = yes
;       encrypt passwords = yes
;       passdb backend = tdbsam
;       netbios name = server
;       os level = 20

## Browsing/Identification ###

#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT
both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

# What naming service and in what order should we use to resolve host
names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine
is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog.
Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to
log
# through syslog you should set the following parameter to something
higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix
account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the
Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the
following
# parameters must be set (thanks to Ian Kahan
<<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian
Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are
mapped 
# to anonymous connections

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
# Another common choice is storing the profile in the user's home
directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the
SAMR
# RPC pipe.  The example command creates a user account with a disabled
Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password
--gecos "" %u

# This allows machine accounts to be created on the domain controller
via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine
account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the
SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes
load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
        printing = cups
   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5)
and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup
package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s'
&

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

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

# Maximum number of usershare. 0 (default) means that usershare is
disabled.
;       usershare max shares = 100
;       guest ok = no
;       guest account = nobody

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones

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

# Directory creation mask is set to 0700 for security reasons. If you
want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain
Logons
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
        create mask = 0700
        comment = All Printers
        printable = yes
        path = /var/spool/samba
;       guest ok = no
;       read only = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
;       browseable = yes
;       read only = yes
;       guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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

[Home]
        writeable = yes
        path = /home/fireman71

***cupsd.conf****

LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job
Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription
Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job
Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer
CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default
CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer
Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs
Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer
Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs
CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job
Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription
Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job
Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
Require user @OWNER @SYSTEM
Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer
CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
  Require user @SYSTEM
  Order deny,allow
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer
Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs
Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer
Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs
CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Require user @OWNER @SYSTEM
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>

***printers.conf***

# Printer configuration file for CUPS v1.4.1
# Written by cupsd on 2010-05-23 08:06
<DefaultPrinter Officejet-5600-series>
Info HP Officejet 5600 series
Location server.fireman71.us
MakeModel HP Officejet 5600 Series hpijs, 3.9.8
DeviceURI hp:/usb/Officejet_5600_series?serial=CN75MDW09104CY
State Idle
StateTime 1274568348
Type 8425484
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 100 foomatic-rip
Filter application/vnd.cups-pdf 0 foomatic-rip
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer Officejet-5600-series-Fax>
Info HP Fax
Location server.fireman71.us
MakeModel HP Fax hpijs
DeviceURI hpfax:/usb/Officejet_5600_series?serial=CN75MDW09104CY
State Idle
StateTime 1272078684
Type 8392716
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 100 foomatic-rip
Filter application/vnd.cups-pdf 0 foomatic-rip
Filter application/vnd.cups-command 0 commandtops
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by fireman71 on 2010-05-30
hmmm, no replies yet....very vexing problem...

Some additional information after playing with this for a good bit.

I can occasionally get a document to print. To do so I have to completely remove all printers and printer ports from the windows 7 machine. I then go and add the printer back to the windows 7 machine and have to set it up as a local printer, add a local port that points to \\server\Officejet-5600-series and about 50% of the time it will manage to print a test page. When I can get it to print everything seems to work normally. The laptop then gets carried to a different network (work wireless) brought back home and it refuses to print again until i repeat the above steps (usually several times). So this is telling me that it appears to be a strictly windows problem. I have tried using cups as IPP and it wont print, tried just connecting through samba to a shared printer and it wont print. The only way I have come close to resolving this is as described above.

Anyone have any ideas?

---

### Post by fireman71 on 2010-05-31
Some more information that has come to light trying to find a fix for this problem.

I can boot the windows 7 laptop and get the printer installed and printing just fine setting it up as a local printer and configuring a local port which points to the printer on the ubuntu server. Everything will continue to work until the laptop is restarted or put into sleep/hibernation mode. When it is brought back up it refuses to print necessitating removing the printer, the local printer port, and reconfiguring everything.

If I find anything else I will post it as well. God I hate windows, but the better half wont budge......yet

---

### Post by milhouse on 2010-07-21
I'm having the same issue. Surprisingly though there don't seem to be a lot of people having this problem. My setup couldn't be more standard (or so I think).

In my case I have a ML-2010 printer attached to my 10.04 machine via USB. The printer is "shared" via IPP and Samba. I can print w/o issue from my other Ubuntu machines. The only windows machine in the house is running Win 7 Home Premium x64. On this machine administrator accounts can print, but standard user accounts cannot. When I try to print from a standard account applications tend to hang, it takes maybe 30 seconds for the printer dialog to show, and after clicking print the applications will periodically become unresponsive. Eventually the print job silently fails and the application is responsive again. Occasionally I bring home a Win 7 Pro x64 laptop from work and it has the same issues printing too.

I'm just digging into this as my kids have started complaining that they can't print. It seems (at least in my case) that the issue may be related to authentication. Here are a couple of discussions I just dug up. Note that the responses are garbage, but the initial posts may provide some hints:

[[COLOR="Blue"]Printing to a CUPS printer via HTTP / IPP[/COLOR]]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/a965d71f-e0b0-4c32-a163-de8c6a81f722")
[[COLOR="blue"]IPP based printer wont authenticate on some print jobs[/COLOR]]("http://social.technet.microsoft.com/Forums/en-US/w7itpronetworking/thread/79555bf0-5c23-41a0-a09b-14d669ae5894")

I'm going to try disabling authentication and seeing if that helps.

[[COLOR="Blue"]How to turn off cups print authentication?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1068932")

I'll report back my results...

---

