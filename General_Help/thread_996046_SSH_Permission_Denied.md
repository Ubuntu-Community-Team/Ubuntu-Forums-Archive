---
title: "SSH Permission Denied"
date: 2008-11-28
forum: General Help
---

### Post by spongypants23 on 2008-11-28
Hi guys, having a bit of a problem with the OpenSSH-server running on my computer. Up until around a week ago, I could log in to it no issues, then all of a sudden I get a "Permission Denied (publickey)" error when going remotely or locally. PuTTY gives a "No authentication methods available" error, or something along the lines of that. I can't remember the exact text.

(Really long post. Sorry!)

Terminal output of "ssh -v localhost":
```
simon@M1530:~$ ssh -v localhost
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/simon/.ssh/identity type -1
debug1: identity file /home/simon/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/simon/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/simon/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/simon/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/simon/.ssh/identity
debug1: Trying private key: /home/simon/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

```


Here is the sshd_config file:
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
PermitRootLogin yes
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

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
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


My ~/.ssh folder is chmod'd to 700, and the authorized_keys (chmod 600) file contains the public key associated with the private key i'm using.

I have absolutely no idea what is going on, any help would be much appreciated.

---

### Post by spongypants23 on 2008-11-28
As much as I hate bumping, I would like this problem solved.

*bump*

---

### Post by Peter09 on 2008-11-28
Your config file shows RSA authentication is enabled - is this true?

---

### Post by spongypants23 on 2008-11-28
Fairly sure it is. Unless my config file is lying.

---

### Post by Peter09 on 2008-11-29
Thanks for that ----:)
are you using RSA?

---

### Post by Peter09 on 2008-11-29
Hi - ignore the RSA bit - misread you thread.

I have had a look at my sshd and the only difference between the two appears to be that I have disabled root login and increased the login time out to 120.

---

### Post by spongypants23 on 2008-11-29
Unfortunately disabling root login didn't make a difference. Still getting the same error, "Permission denied (publickey)".

---

