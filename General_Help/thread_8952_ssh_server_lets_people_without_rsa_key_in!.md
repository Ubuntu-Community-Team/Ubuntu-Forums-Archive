---
title: "ssh server lets people without rsa key in!"
date: 2004-12-22
forum: General Help
---

### Post by Razvan on 2004-12-22
HI all,

i set up an ssh server to allow only people with rsa authentication access. cleartextpasswords are disabled.

at least, that's what the configfile says. When i connect from a pc, that doesnt have a pub key in my sstem, the server just asks for a cleartext password and lets me in!

what should i do?

thanks, Maerin

---

### Post by Averatec5400 on 2004-12-22
[QUOTE=Razvan]HI all,

i set up an ssh server to allow only people with rsa authentication access. cleartextpasswords are disabled.

at least, that's what the configfile says. When i connect from a pc, that doesnt have a pub key in my sstem, the server just asks for a cleartext password and lets me in!

what should i do?

thanks, Maerin[/QUOTE]
 first ssh is encrypted, it is not "Cleartext" in the FTP sense.

and then the sshd_config in /etc/ssh will need a line like this:
PasswordAuthentication no

Then you need to make sure there is something like this in there so you can login with a public key.

PubkeyAuthentication    yes
AuthorizedKeysFile      .ssh/authorized_keys

I might have missed something in there, if I did feel free to correct me or add more :)

---

### Post by Razvan on 2004-12-22
this is a snip of my /etc/ssh/sshd_conf

```
# Authentication:
LoginGraceTime 600
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to no to disable s/key passwords
ChallengeResponseAuthentication yes

# Change to yes to enable tunnelled clear text passwords
PasswordAuthentication no
```

what am i doing wrong? i guess the prob is between chair and keyboard again  :oops:

---

### Post by randy on 2004-12-23
Did you restart ssh after modifying the config file?

---

### Post by nocturn on 2004-12-23
[QUOTE=Razvan]this is a snip of my /etc/ssh/sshd_conf

```
# Authentication:
LoginGraceTime 600
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to no to disable s/key passwords
ChallengeResponseAuthentication yes

# Change to yes to enable tunnelled clear text passwords
PasswordAuthentication no
```

what am i doing wrong? i guess the prob is between chair and keyboard again  :oops:[/QUOTE]


If restarting SSH does not help.  Check the ssh file in /etc/pam.d (I'm not on my Linux box right now, so I can't be sure).

---

### Post by Razvan on 2004-12-23
mhh...thats wierd

i have restarted my server several times...
the /etc/pam.d/ssh file was there but I dont have clue what it's about ;-)

what are the authorized_key files doing? 

the funny thing is, if a user uploads a public key, its fine, but before he  uploaded one, the server would just let him hin without a rsa key. just via password.
Isnt it supposed to block people that dont have keys in my server?

Thanks so far, Martin

---

### Post by nocturn on 2004-12-24
[QUOTE=Razvan]mhh...thats wierd

i have restarted my server several times...
the /etc/pam.d/ssh file was there but I dont have clue what it's about ;-)

what are the authorized_key files doing? 

the funny thing is, if a user uploads a public key, its fine, but before he  uploaded one, the server would just let him hin without a rsa key. just via password.
Isnt it supposed to block people that dont have keys in my server?

Thanks so far, Martin[/QUOTE]

Can you check if there is any reference to PAM in your sshd_config file?
AFAIK, ssh will use the PAM file by default to determine which authentications can proceed.  So, I'm guessing that the PAM file is included and that it allows password auth.

Merry christmas!

---

### Post by Razvan on 2004-12-24
all right, i figured it out :-)

i just told him not to use pam...he does as wanted now

thanks for everyones help!

---

