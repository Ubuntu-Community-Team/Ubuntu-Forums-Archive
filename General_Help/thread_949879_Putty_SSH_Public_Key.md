---
title: "Putty SSH Public Key"
date: 2008-10-16
forum: General Help
---

### Post by Barnicle on 2008-10-16
Hi there,

I'm trying to configure Putty by using a SSH Public Key, so I can log on to various servers, without having to log in each time.

I downloaded PuttyGen, generated a public/private key, uploaded the public key to the server, and pointed Putty to my private key on my local computer.

When I try to log in to the server I'm testing this on, I get this error:

```
login as: admin
Server refused our key
admin@domain.com's password:
```

Any ideas?

---

### Post by HalPomeranz on 2008-10-17
When public-key-based authentication fails, there are several different possible problems:

1) You don't have PubkeyAuthentication set to "yes" in your SSH server config file (usually /etc/ssh/sshd_config) on the remote system

2) You're using the wrong key format.  If you're using the key to log into an Ubuntu system, you need to dump out the public key in OpenSSH format and not the ssh.com format (see the "Conversions" menu in Puttygen)

3) You've got the key public key installed in the wrong file on the remote machine.  Since you appear to be trying to log in as user "admin", the public key should be in the file ~admin/.ssh/authorized_keys

4) Permissions on the authorized_keys file and/or the directories it's kept in are too permissive.  Do this:

```

chmod go-w ~admin
chmod -R go-w ~admin/.ssh

```

The above lines will remove the "write" flag for "group" and "other" from admin's home directory and the .ssh directory for this account plus all files and directories under ~admin/.ssh

5) You're trying to log into an account that has UID 0, but you don't have PermitRootLogin set properly in your SSH server config.  In general, you shouldn't be SSH-ing around as root, though you can make this work by setting PermitRootLogin to "without-password", which means that root logins will be allowed as long as you're using something better than normal password authentication (e.g. a public key type login).

---

### Post by Barnicle on 2008-10-17
I figured out the solution if anyone is interested. There is an issue with PuttyGen's key that it generates. You have to generate a key through linux using this command:

```
ssh-keygen -b 1024 -t rsa -f username
```
-b is your bit rate. -t is the type of encryption. You will find other commands on the man page.

Anyway, after you generate your key, it will ask you for a passphrase. Once your key is finally generated, load it into PuttyGen, enter your passphrase, and save it. Proceed with adding your key to the SSH > Auth section inside Putty. It should work after.

Keys should be stored under a file called .ssh/authorized_keys on the server side. Also, change your hostname to administrator@X.X.X.X or whatever your username/server name is.

---

### Post by kevdog on 2008-10-17
Yes that solution will work -- OpenSSH keys and Putty generated keys are not compatible.  A conversion needs to be done!

---

### Post by legendofzash on 2008-10-21
I'm having the exact same issue... yet nothing seems to fix it.

I've tried generating the keys using ssh-keygen and converting the private key using Putty.  I've tried generating the keys on putty.  No matter what I do, I always get the dreaded "Server refused our key" message.  I'm beginning to think that it may just be a configuration error or something.  My .ssh directory is chmod 700 and my .ssh/authorized_keys file is chmod 600.

Any idea what's going on?

EDIT: Here is my configuration file...

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
AuthorizedKeysFile ~/.ssh/authorized_keys

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

---

