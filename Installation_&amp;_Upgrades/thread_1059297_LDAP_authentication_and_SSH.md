---
title: "LDAP authentication and SSH"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by jsfan on 2009-02-03
I have an Ubuntui box which authenticates against LDAP. IOt used to do that just find on an old version (don't remember which one but since I've upgraded to Hardy it only does it half way now.

I can authenticate fine on the console and X but SSH will only work with keys. How do I configure SSH to do the LDAP authentication, too?

There isn't anything useful in the logs and as sudo doesn't seem to do the authentication, either, copying and pasting is tedious. Here's the SSH login attempt

```
Feb  4 08:53:39 linux323b sshd[25330]: pam_ldap: could not open secret file /etc/ldap.secret (No such file or directory)
Feb  4 08:53:39 linux323b sshd[25330]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=linux323b  user=<undisclosed>
Feb  4 08:53:41 linux323b sshd[25330]: Failed password for <undisclosed> from 127.0.1.1 port 51364 ssh2
```

and for the sudo

```
Feb  4 08:54:10 linux323b sudo: pam_unix(sudo:auth): authentication failure; logname=<undisclosed> uid=0 euid=0 tty=/dev/tty2 ruser= rhost=  user=<undisclosed>
Feb  4 08:54:20 linux323b sudo: pam_unix(sudo:auth): conversation failed
Feb  4 08:54:20 linux323b sudo: pam_unix(sudo:auth): auth could not identify password for [clerrahn]
Feb  4 08:54:20 linux323b sudo: <undisclosed> : 1 incorrect password attempt ; TTY=tty2 ; PWD=/ ; USER=root ; COMMAND=/bin/su
```

My /etc/pam.d/common-* files look like this

common-account:
```
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account	required	pam_unix.so
```

common-auth:
```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth	optional	pam_group.so
#
auth	sufficient	pam_ldap.so use_first_pass
auth	sufficient	pam_unix.so nullok_secure
#auth	sufficient	pam_krb5.so minimum_uid=1000 ignore_root use_first_pass
#auth	sufficient	pam_ldap.so minimum_uid=1000 ignore_root use_first_pass
```

common-password:
```
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# The "md5" option enables MD5 passwords.  Without this option, the
# default is Unix crypt.
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# You can also use the "min" option to enforce the length of the new
# password.
#
# See the pam_unix manpage for other options.

password   requisite   pam_unix.so nullok obscure md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required	  pam_cracklib.so retry=3 minlen=6 difok=3
# password required	  pam_unix.so use_authtok nullok md5

# minimally-intrusive inclusion of smbpass in the stack for
# synchronization.  If the module is absent or the passwords don't
# match, this module will be ignored without prompting; and if the 
# passwords do match, the NTLM hash for the user will be updated
# automatically.
password   optional   pam_smbpass.so nullok use_authtok use_first_pass missingok
```

common-session:
```
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
session	required	pam_unix.so
```

and sshd (with symlink ssh pointing to it) looks like this
```
# PAM configuration for the Secure Shell service

# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so

# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account  required     pam_access.so

# Standard Un*x authorization.
@include common-account

# Standard Un*x session setup and teardown.
@include common-session

# Print the message of the day upon successful login.
session    optional     pam_motd.so # [1]

# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]

# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so

# Set up SELinux capabilities (need modified pam)
# session  required     pam_selinux.so multiple

# Standard Un*x password updating.
@include common-password
```

Any hints anyone? I can't see why LDAP authentication should work for the console/X but not on SSH :(

---

### Post by righteousjester on 2009-06-05
Hey jsfan

I have it working on our side, and I will give you our configs.  Just make sure your ssh plugs into PAM, which it should do out the box

Make sure the the following packages are installed
```

apt-get install libpam-ldap libnss-ldap libpam-cracklib
```/etc/pam.d/common-account
```

#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account    [default=bad user_unknown=ignore success=ok authinfo_unavail=ignore] pam_ldap.so
account    required     pam_unix.so
```/etc/pam.d/common-auth
```

# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
#auth    required    pam_unix.so nullok_secure
#
auth       required     pam_env.so
auth       sufficient   pam_unix.so try_first_pass likeauth nullok
auth       sufficient   pam_ldap.so use_first_pass
auth       required     pam_deny.so
```/etc/pam.d/common-password
```

#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# The "md5" option enables MD5 passwords.  Without this option, the
# default is Unix crypt.
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# You can also use the "min" option to enforce the length of the new
# password.
#
# See the pam_unix manpage for other options.

#password   required    pam_unix.so nullok obscure md5

password   required     pam_cracklib.so difok=2 minlen=8 dcredit=2 ocredit=2 try_first_pass retry=3
password   sufficient   pam_unix.so try_first_pass use_authtok nullok md5 shadow
password   sufficient   pam_ldap.so use_authtok use_first_pass
password   required     pam_deny.so

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required      pam_cracklib.so retry=3 minlen=6 difok=3
# password required      pam_unix.so use_authtok nullok md5
```/etc/pam.d/common-session 
```
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
#session    required    pam_unix.so
#session    optional    pam_foreground.so

session    required     pam_limits.so
session    required     pam_unix.so
session    optional     pam_ldap.so
session    optional     pam_mkhomedir.so
```/etc/ldap.conf```

uri ldap://ldapserver1.domain.com:389 ldap://ldapserver2.domain.com:389 ldap://ldapserver3.domain.com:389
base ou=users,dc=domain,dc=com
binddn someusername
bindpw somepassword

pam_filter objectclass=posixAccount
pam_login_attribute uid
pam_member_attribute memberuid
nss_base_passwd ou=users,dc=domain,dc=com
nss_base_shadow ou=users,dc=domain,dc=com
nss_base_group ou=users,dc=domain,dc=com
scope one

timelimit 10
bind_timelimit 10
bind_policy soft
```/etc/nsswitch.conf
```

passwd:         files ldap [NOTFOUND=return] db
group:          files ldap [NOTFOUND=return] db
shadow:         files ldap [NOTFOUND=return] db
```Good luck

---

### Post by RoscoPColtrane on 2009-07-07
Hey thanks righteousjester!

Your post just solved my login problem. I wish pam.d was easier to configure, all those plugins/rules are a bit confusing.

Thanks!

---

### Post by jsfan on 2009-07-29
Righteousjester, that did the trick!

Thanks for that!

Now, I'm only wondering why this works. ;) I do not claim to understand... ;)

---

### Post by TuxCrafter on 2010-08-23
On my Debian servers i had the same authorisation failures because the pam_unix is checked first and creates the error after this the pam_ldap is checked and succeeds.

I solved this issues by switching pam_unix and pam_ldap as the first authorisation module to be checked.

```
vim /etc/pam.d/common-auth
    auth    [success=2 default=ignore]      pam_ldap.so minimum_uid=1000
    auth    [success=1 default=ignore]      pam_unix.so nullok_secure use_first_pass
```

Be careful that you make sure you still can login as root and other system users!

---

### Post by compubomb on 2013-04-14
I messed up my common-password file and even my root password couldn't get me back into my machine. LOL Good ole format did the trick :(

---

