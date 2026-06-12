---
title: "Help with WU-FTPD"
date: 2008-12-02
forum: General Help
---

### Post by lilmansplace on 2008-12-02
So I've successfully installed WU-FTPD and having it authenticate using Kerberos and Active Directory.  I can log in and put and retrieve files without any troubles.  But I did notice that with firezilla or windows explorer ftp the folders and files are prepended with a time stamp.  Which breaks things.  Here is an example of what I'm talking about:

[IMG]http://users.sisna.com/theinternet/wu_ftpd_wierdness.gif[/IMG]

Here is the ftpaccess config I have setup:
> 
email [email]user@domain.com[/email]

allow-uid DOMAIN\ftpuser

greeting brief

class   all     real,guest,anonymous    *

limit   all     10      Any                     /etc/wu-ftpd/msg.toomany

message /welcome.msg            login
message .message                cwd=*

readme  README*    login
readme  README*    cwd=*

compress        yes             local remote all
tar             yes             local remote all

log transfers anonymous,guest,real inbound,outbound

shutdown /etc/wu-ftpd/shutmsg

noretrieve /etc/passwd /etc/group
noretrieve core

passwd-check    rfc822  enforce

rename          no              anonymous               # rename permission?
delete          no              anonymous               # delete permission?
overwrite       no              anonymous               # overwrite permission?
chmod           no              anonymous               # chmod permission?
umask           no              anonymous               # umask permission?
delete          yes             guest                   # delete files permission?
overwrite       yes             guest                   # overwrite files permission?
rename          yes             guest                   # rename files permission?
umask           no              guest                   # umask permission?
compress        yes             all
tar             yes             all

upload  /home/ftp       *               no
upload  /home/ftp       /pub/incoming   yes     ftp     daemon  0666    nodirs

path-filter     anonymous       /etc/pathmsg  ^[-+A-Za-z0-9_.]*$  ^\.  ^-

alias   incoming:       /pub/incoming
cdpath  /pub


Can someone tell me how to fix this?

Thanks in advance.

---

### Post by lilmansplace on 2008-12-08
Did I post in the wrong section to get no help on this?  Or is this issue so daunting to everyone? :(

---

