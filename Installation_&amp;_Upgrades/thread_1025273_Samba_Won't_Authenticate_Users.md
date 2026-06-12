---
title: "Samba Won't Authenticate Users"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by gn0s on 2008-12-29
I installed samba, added samba user by smbpasswd and changed the smb.conf on my-gNewSense machine enabling following:

comment = Home Directories
browseable = yes

I entered \\my-gNewSense in Explorer Address bar on a Microsoft Windows machine and can connect successfully and see pdf and printer and fax nodes there[1].

But when I enable this option

valid users = %S

I can't connect to my-gNewSense machine with the samba user account I created before, and its correct password. It asks for user/password again and again[2].


--
screen shots:

[1] [http://dzcyrg.bay.livefilestore.com/y1pQGBXfHvwC4vjSD4yV6eGHhuRb1u0dnM10osimRrs4NjHksTJwuDHR9Wr-3zcDBTGvDZ4Qim3xgJRHNC8g9AhGg/win-smb.bmp](http://dzcyrg.bay.livefilestore.com/y1pQGBXfHvwC4vjSD4yV6eGHhuRb1u0dnM10osimRrs4NjHksTJwuDHR9Wr-3zcDBTGvDZ4Qim3xgJRHNC8g9AhGg/win-smb.bmp)

[IMG]http://dzcyrg.bay.livefilestore.com/y1pQGBXfHvwC4vjSD4yV6eGHhuRb1u0dnM10osimRrs4NjHksTJwuDHR9Wr-3zcDBTGvDZ4Qim3xgJRHNC8g9AhGg/win-smb.bmp[/IMG]

[2] [http://dzcyrg.bay.livefilestore.com/y1pky2QciPZKtNvdPkcoN95f60GS7LdPND2apSNJBjCB5j972iTssVg5A8gq-0RdfJbB-nTCQqFV3c/win-smb-logon.bmp](http://dzcyrg.bay.livefilestore.com/y1pky2QciPZKtNvdPkcoN95f60GS7LdPND2apSNJBjCB5j972iTssVg5A8gq-0RdfJbB-nTCQqFV3c/win-smb-logon.bmp)

[IMG]http://dzcyrg.bay.livefilestore.com/y1pky2QciPZKtNvdPkcoN95f60GS7LdPND2apSNJBjCB5j972iTssVg5A8gq-0RdfJbB-nTCQqFV3c/win-smb-logon.bmp[/IMG]

---

### Post by gn0s on 2008-12-30
[http://wiki.gnewsense.org/ForumMain/SambaWonTAuthenticateUsers](http://wiki.gnewsense.org/ForumMain/SambaWonTAuthenticateUsers)

I replaced the smb.conf on gNS with the file smb.conf ftped from a debian machine, and it works : ) 

I'm sorry if it's too long for a post here. 

I read the diff result but still don't find out why : ) 

$ diff -u /etc/samba/smb.conf /etc/samba/smb.conf.bak --- /etc/samba/smb.conf 2008-12-30 16:44:59.000000000 +0800 +++ /etc/samba/smb.conf.bak 2008-12-30 09:57:35.000000000 +0800 -24,10 +24,10 

 ## Browsing/Identification ###

 # Change this to the workgroup/NT-domain name your Samba server will part of
- workgroup = Workgroup + workgroup = WORKGROUP 

 # server string is the equivalent of the NT Description field
- server string = %h server + server string = %h server (Samba, Ubuntu) 

 # Windows Internet Name Serving Support Section:
 # WINS Support - Tells the NMBD component of Samba to enable its WINS Server
-66,7 +66,7 

 # that connects
    log file = /var/log/samba/log.%m
-# Put a capping on the size of the log files (in Kb). +# Cap the size of the individual log files (in KiB). 

    max log size = 1000

 # If you want Samba to only log through syslog then set the following
-106,18 +106,22 

 # This boolean parameter controls whether Samba attempts to sync the Unix
 # password with the SMB password when the encrypted SMB password in the
 # passdb is changed.
-; unix password sync = no + unix password sync = yes 

 # For Unix password sync to work on a Debian GNU/Linux system, the following
 # parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
 # sending the correct chat script for the passwd program in Debian Sarge).
    passwd program = /usr/bin/passwd %u
- passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* . + passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 

 # This boolean controls whether PAM will be used for password changes
 # when requested by an SMB client instead of the program listed in
 # 'passwd program'. The default is 'no'.
-; pam password change = no + pam password change = yes + +# This option controls how nsuccessful authentication attempts are mapped +# to anonymous connections +map to guest = bad user 

 ########## Domains ###########
-169,12 +173,6 

 ;   printing = cups
 ;   printcap name = cups
-# When using [print$], root is implicitly a 'printer admin', but you can -# also give this right to other users to add drivers and set printer -# properties -; printer admin = @ntadmin - - 

 ############ Misc ############

 # Using the following line enables you to customise your configuration
-204,39 +202,51 

 ;   idmap uid = 10000-20000
 ;   idmap gid = 10000-20000
 ;   template shell = /bin/bash
-; -; The following was the default behaviour in sarge -; but samba upstream reverted the default because it might induce -; performance issues in large organizations -; See #368251 for some of the consequences of *not* having -; this setting and smb.conf(5) for all details -; + +# The following was the default behaviour in sarge, +# but samba upstream reverted the default because it might induce +# performance issues in large organizations. +# See Debian bug #368251 for some of the consequences of *not* +# having this setting and smb.conf(5) for details. 

 ;   winbind enum groups = yes
 ;   winbind enum users = yes
+# Setup usershare options to enable non-root users to share folders +# with the net usershare command. + +# Maximum number of usershare. 0 (default) means that usershare is disabled. +; usershare max shares = 100 + +# Allow users who've been granted usershare privileges to create +# public shares, not just authenticated ones + usershare allow guests = yes + 

 #======================= Share Definitions =======================
-[homes] - comment = Home Directories - browseable = no +# Un-comment the following (and tweak the other settings below to suit) +# to enable the default home directory shares. This will share each +# user's home directory as \\server\username +;[homes] +; comment = Home Directories +; browseable = no 

-# By default, the home directories are exported read-only. Change next -# parameter to 'yes' if you want to be able to write to them. - #writable = no - writable = yes +# By default, the home directories are exported read-only. Change the +# next parameter to 'no' if you want to be able to write to them. +; read only = yes 

 # File creation mask is set to 0700 for security reasons. If you want to
 # create files with group=rw permissions, set next parameter to 0775.
- create mask = 0700 +; create mask = 0700 

 # Directory creation mask is set to 0700 for security reasons. If you want to
 # create dirs. with group=rw permissions, set next parameter to 0775.
- directory mask = 0700 +; directory mask = 0700 

-# Restrict access to home directories -# to the one of the authenticated user +# By default, \\server\username shares can be connected to by anyone +# with access to the samba server. Un-comment the following parameter +# to make sure that only "username" can connect to \\server\username 

 # This might need tweaking when using external authentication schemes
- valid users = %S +; valid users = %S 

 # Un-comment the following and create the netlogon directory for Domain Logons
 # (you need to configure Samba to act as a domain controller too.)
-244,7 +254,7 

 ;   comment = Network Logon Service
 ;   path = /home/samba/netlogon
 ;   guest ok = yes
-; writable = no +; read only = yes 

 ;   share modes = no

 # Un-comment the following and create the profiles directory to store
-265,9 +275,9 

    browseable = no
    path = /var/spool/samba
    printable = yes
- public = no - writable = no - create mode = 0700 + guest ok = no + read only = yes + create mask = 0700 

 # Windows clients look for this share name as a source of downloadable
 # printer drivers
-285,10 +295,10 

 # A sample share for sharing your CD-ROM with others.
 ;[cdrom]
 ;   comment = Samba server's CD-ROM
-; writable = no +; read only = yes 

 ;   locking = no
 ;   path = /cdrom
-; public = yes +; guest ok = yes 

 # The next two parameters show how to auto-mount a CD-ROM when the
 #      cdrom share is accesed. For this to work /etc/fstab must contain
$

---

