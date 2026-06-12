---
title: "Proftpd error"
date: 2005-12-05
forum: General Help
---

### Post by GuruMadMat on 2005-12-05
i get this error when i log in via router
```

Entering Passive Mode (192,168,2,100,7,60).
    Opening data connection to 192.168.2.100 Port: 1852
    LIST -aL
    0 bytes transferred. (N/A/s) (0 ms)
    Timeout (40s).
 
Automatic failover of data connection mode from "Passive Mode (PASV)" to "Active Mode (PORT)".

```

when i want to log in with my local ip adress it works but it does not work when i use my global ip adress although i have forwarded my ALL my ports but it does nothing it logs me in but it stalls when it wants to display the data

what is wrong with my config?
```

  GNU nano 1.2.4               Bestand: /etc/proftpd.conf

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "test server"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

#DenyFilter                     \*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
PersistentPasswd                off

# Uncomment this if you would use TLS module:
#TLSEngine                      on

#Quotas                         on

# Uncomment this if you would use ratio module:
#Ratios                         on

ServerIdent                  on       "you got in"

DefaultRoot /var/www/

# Port 21 is the standard FTP port.
Port                            25001

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
#DelayEngine                    off



RootLogin off

```

---

### Post by GuruMadMat on 2005-12-07
does nobody knows?

---

### Post by edonnelly on 2005-12-20
[QUOTE=GuruMadMat]
when i want to log in with my local ip adress it works but it does not work when i use my global ip adress although i have forwarded my ALL my ports but it does nothing it logs me in but it stalls when it wants to display the data[/QUOTE]

I really don't know for sure, but since nobody else has answered...

Check if your ftp client program has an option to "Ignore PASV address" - I use gftp and I've had to use this option in the past. It has something to do with the router returning its internal ip address instead of its public one in passive mode. It might explain why it's ok when you're inside your own network but not ok when you're using your public ip. Not sure if it will solve your problem, but it's easy enough to try.

Good luck

---

### Post by GuruMadMat on 2005-12-20
thnx a lot i will try this!

---

### Post by GuruMadMat on 2005-12-20
I think i will use vsftp and throw Pro ftpd in the trashbin!

---

