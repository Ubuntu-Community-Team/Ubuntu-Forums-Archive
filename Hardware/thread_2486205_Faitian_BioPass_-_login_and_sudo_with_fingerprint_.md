---
title: "Faitian BioPass - login and sudo with fingerprint only?"
date: 2023-04-22
forum: Hardware
---

### Post by anutosho on 2023-04-22
Hi,

I just installed a Feitian BioPassFIDO2 Reader and can sudo with my sudo password and after that with the fingerprint.
Is it possible to omit the Password and use the fingerprint only for authentification?

My /etc/pam.d/sudo looks like this:

```

#%PAM-1.0

# Set up user limits from /etc/security/limits.conf.
session    required   pam_limits.so

session    required   pam_env.so readenv=1 user_readenv=0
session    required   pam_env.so readenv=1 envfile=/etc/default/locale user_readenv=0

@include common-auth

# BioPass fingerprint reader
#auth   sufficient  pam_u2f.so authfile=/etc/BioPass/u2f_keys 
auth    required   pam_u2f.so  authfile=/etc/BioPass/u2f_keys interactive prompt=[Finger bitte:]

@include common-account
@include common-session-noninteractive

```

The perfect solution would be to choose between fingerprint OR password.  My Lenovo E14 G4 supports this (if I press enter instead of password, I  can authenticate with my fingerprint).

I'm aware that a u2f device is meant for two factor authentification in the first place, but maybe my whish could be fulfilled nevertheless?

---

