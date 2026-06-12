---
title: "NX Authentication stopped working"
date: 2008-08-12
forum: General Help
---

### Post by sipickles on 2008-08-12
Hi,

I have suddenly got an authentication problem with NX. On the NX server machine I get this:

```
simon@simon-ubuntu:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.
simon@simon-ubuntu:~$ sudo /usr/NX/bin/nxserver --usercheck simon
NX> 900 Verifying public key authentication for NX user: simon.
NX> 900 Adding public key for user: simon to the authorized keys file.
NX> 716 Public key is already present in: /home/simon/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: simon.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: simon
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.
```

I had a few problems getting it to work, but I found this thread and changed my ssh config to match it. It worked last night, but not today.

[http://ubuntuforums.org/archive/index.php/t-449382.html](http://ubuntuforums.org/archive/index.php/t-449382.html)

Here's my /etc/ssh/sshd_config:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
AllowUsers nx simon
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2
#AuthorizedKeysFile	%h/.ssh/authorized_keys
#AuthorizedKeysFile	%h/.ssh/authorized_keys2

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

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

I am really stumped on this now.

---

