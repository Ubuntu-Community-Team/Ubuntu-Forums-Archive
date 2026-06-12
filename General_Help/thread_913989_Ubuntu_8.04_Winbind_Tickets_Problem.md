---
title: "Ubuntu 8.04 Winbind Tickets Problem"
date: 2008-09-08
forum: General Help
---

### Post by monkeylnxjr on 2008-09-08
Hello,

I have recently installed Ubuntu 8.04 and configured Samba/Winbind, everything works except that when I log in I see no cached kerberos tickets in /tmp

Below a copy of my pam files for you to analyze:

common-account 

account sufficient      pam_winbind.so krb5_auth debug try_first_pass cached_login
account required        pam_unix.so


common-auth

auth    sufficient      pam_winbind.so krb5_auth krb5_ccache_type=FILE
auth    sufficient      pam_unix.so nullok_secure try_first_pass
auth    optional        pam_smbpass.so migrate missingok


common-password 

password   optional   pam_smbpass.so nullok use_authtok use_first_pass missingok

common-session

session required        pam_unix.so
session optional        pam_foreground.so
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel silent

Samba 3.0.28a is installed, Winbind 3.0.28a are both installed.

Could someone help me get my kerberos tickets in /tmp? I need to cache the KRB tickets upon login.

Thanks

---

### Post by aniketvb on 2008-10-03
Hi

even I have the same problem. After a reboot . if I do "klist" , I see no tickets . Due to this, AD accounts login via winbind  fails and I have to login as a local user, get a new ticket and then AD login works. 

Also , I noticed that /tmp (where the tickets files are kept) is cleared on every reboot. 

Please help me !!

PS: I have exactly similar setup in a fedora 9 machine, and it does not have any problems and the AD logins keep working even after reboots.But I am very keen on getting this working with Ubuntu as I noticed that my users feel much more comfortable with Ubuntu than fedora and I want to deploy Ubuntu on a larger scale.

---

### Post by Causer1984 on 2008-11-14
Not an answer I know, but a solution. The smb.conf file is pretty long, and I'm pretty sure a line in it is stopping tickets being kept. If you wipe it clean and put the following (taken from ActiveDirectoryWinbindHowTo in the Ubuntu community docs.)

```

[global]
        security = ads
        realm = LAB.EXAMPLE.COM
        password server = 10.0.0.1
# note that workgroup is the 'short' domain name
        workgroup = LAB
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2


```

it should work (with any luck!)

---

### Post by aniketvb on 2008-11-14
Okk!
I got around it!!
I modified the following lines. The bold part is what I removed, 
> 
common-account 

account sufficient pam_winbind.so **krb5_auth debug try_first_pass cached_login**
account required pam_unix.so


common-auth

auth sufficient pam_winbind.so **krb5_auth krb5_ccache_type=FILE (added cached_login here )** 
auth sufficient pam_unix.so nullok_secure try_first_pass
auth optional pam_smbpass.so migrate missingok



Now it works fine , even after those tickets are lost . I did not change anything in my smb.conf file.

---

### Post by Causer1984 on 2008-11-14
Actually, scrap that. I got round the problem by adding to /etc/pam.d/common-auth

```
auth optional pam_krb5.so ccache=/tmp/krb5cc_%u 
auth sufficient pam_winbind.so use_first_pass

```

but your solution looks much nicer aniketvb

Many thanks

---

