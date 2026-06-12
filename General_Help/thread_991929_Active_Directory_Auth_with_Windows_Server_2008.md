---
title: "Active Directory Auth with Windows Server 2008"
date: 2008-11-24
forum: General Help
---

### Post by wtfacoconut on 2008-11-24
Hey I've been looking around and racking my brain on how to get ubuntu to auth with win server 2008 as a client so far i've found this walk-through that's given he a good general info but I've run into a couple of problems:

[http://blog.scottlowe.org/2007/07/09/linux-ad-integration-with-windows-server-2008/]("http://blog.scottlowe.org/2007/07/09/linux-ad-integration-with-windows-server-2008/")

and I've been using this guide as well:

[http://64.233.169.132/search?q=cache:sGnfzSeEVR0J:www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html+ubuntu+8.10+client+with+windows+active+directory&hl=en&client=firefox-a&gl=us&strip=1]("http://64.233.169.132/search?q=cache:sGnfzSeEVR0J:www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html+ubuntu+8.10+client+with+windows+active+directory&hl=en&client=firefox-a&gl=us&strip=1")

One of the things i've run into so far is SFU. I have no idea if this is already integrated into 2k8 or not and from what I've gathered SFU-3.5 has was made for 2k & 2k3/r2 and I've been told that it has issues if installed on 2k8. So far I've gotten to the part where I start kerberos and that goes well, so here's the output: 
> 
linuxuser@linux11:~$ sudo kinit [email]Michael@NETADMIN.LAB[/email]
Password for [email]Michael@NETADMIN.LAB[/email]: 
linuxuser@linux11:~$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: [email]Michael@NETADMIN.LAB[/email]

Valid starting     Expires            Service principal
11/21/08 09:41:46  11/21/08 16:21:46  krbtgt/NETADMIN.LAB@NETADMIN.LAB


Kerberos 4 ticket cache: /tmp/tkt1000
klist: You have no tickets cached


When I try and finish up here's what I get:
> 
linuxuser@linux11:~$ sudo net ads join -U [email]Michael@NETADMIN.LAB[/email]
Enter [email]Michael@NETADMIN.LAB[/email]'s password:
[2008/11/24 09:22:24,  0] libads/kerberos.c:ads_kinit_password(356)
  kerberos_kinit_password [email]Michael@NETADMIN.LAB@NETADMIN.LAB[/email] failed: Malformed representation of principal
Failed to join domain: failed to connect to AD: Malformed representation of principal


I look all over online and the only thing I get is that its related to SFU. Any Ideas????
Here's my configuration scripts with Kerberso, samba, etc...:

Krb5.conf
> [logging]
default = FILE10000:/var/log/krb5lib.log

[libdefaults]
ticket_lifetime = 24000
default_realm = NETADMIN.LAB
default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

[realms]
NETADMIN.LAB = {
kdc = NETADMINDC1.NETADMIN.LAB
admin_server = NETADMINDC1.NETADMIN.LAB
default_domain = NETADMIN.LAB
}

[domain_realm]
.NETADMIN.LAB = NETADMIN.LAB
NETADMIN.LAB = NETADMIN.LAB


and here's the smb.conf:
> [global]
security = ads
netbios name = ubuntu11
realm = NETADMIN.LAB
password server = NETADMINDC1.NETADMIN.LAB
workgroup = NETADMIN
idmap uid = 500-10000000
idmap gid = 500-10000000
winbind separator = +
winbind enum users = no
winbind enum groups = no
winbind use default domain = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
domain master = no

If any more info is needed plz tell me, and thanks for your help in advance.

---

### Post by HermanAB on 2008-11-24
There are three methods:
1. Samba Winbind
([http://www.aerospacesoftware.com/LinuxActiveDirectory.html](http://www.aerospacesoftware.com/LinuxActiveDirectory.html))
2. Likewise ([http://www.likewisesoftware.com/](http://www.likewisesoftware.com/))
3. LDAP (Do it yourself)

Likewise is in the repos.  So it should be easy to get it to work.

See this:
[http://www.likewisesoftware.com/resources/user_documentation/Likewise-Open-5-Quick-Start-Linux.pdf](http://www.likewisesoftware.com/resources/user_documentation/Likewise-Open-5-Quick-Start-Linux.pdf)

Cheers,

Herman

---

