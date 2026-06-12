---
title: "ubuntu and Windows 2000 AD"
date: 2004-12-21
forum: General Help
---

### Post by dobricchi on 2004-12-21
hello,

i'll retry again to search some help about my need to use windows 2000 authentication on ubuntu.

i'm now at this point:

- stopped samba and winbind services

- modified /etc/nsswitch.conf with this strings:
	passwd:     files winbind
	shadow:     files 
	group:      files winbind

-modified /etc/samba/smb.conf with this strings:
[global]
winbind separator = +
idmap uid = 10000-20000
winbind gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
template homedir = /home/NT/%D/%U
template shell = /bin/bash

- successfully joined AD domain with command:
net rpc join -D MYDOMAIN -U administrator

- restarted samba and winbind services

-tried wbinfo -u command, that successfully give me domain+user Ad user list

-tried wbinfo -g with same good result

-tried getent passwd that successfully give me back ubuntu and AD users

-tried getent group with same good result

-tried command smbclient -Uuser -L smbserver and after a password request it successfully make its job

-so happy at this point i tried to modify pam.d files:

common-account:
#account-required	pam_unix.so
account-required	pam_winbind.so

common-auth:
auth	sufficient	pam_winbind.so
auth	required	pam_unix.so nullok_secure use_first_pass

common-session:
session	required	pam_unix.so
session	required	pam_mkhomedir.so umask=0022 skel=/etc/skel/

sudo:
auth	sufficient	pam_winbind.so
auth	required	pam_unix.so use_first_pass


created /home/NT/MYDOMAIN directory

rebooted system.

i cannot still logon to with my windows AD account.
i can see in 7var/log/auth.log:
pam_winbind         user MYDOMAIN+user granted access
gdm                       unable to manage settings for user MYDOMAIN+user
pam_winbind         request failed: No such user, PAM error was 10, NT error was NT_STATUS_NO_SUCH_USER


any helpful idea?

tnx in adv.

---

### Post by dobricchi on 2004-12-21
i made a mistake with common-account,
the mistake was in
common-account:
account-required pam_unix.so
account-required pam_winbind.so

but the right file has this strings:

# account-required pam_unix.so
account-required pam_winbind.so

and now i'm able to login with my w2000 active directory native mode users! 

hope this post will help.

---

