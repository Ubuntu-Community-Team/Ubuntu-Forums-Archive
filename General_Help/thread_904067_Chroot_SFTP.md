---
title: "Chroot SFTP"
date: 2008-08-28
forum: General Help
---

### Post by DasDuke on 2008-08-28
I'm trying to get an openssh SFTP server to chroot users to their home directory, currently using a test user.

sshd_config file:

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
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp
UsePAM yes

Match user duke
	ChrootDirectory /home/duke
	ForceCommand internal-sftp


```

Error given
```

/etc/ssh/sshd_config: line 80: Bad configuration option: ChrootDirectory
/etc/ssh/sshd_config line 80: Directive 'ChrootDirectory' is not allowed within a Match block
                                                                         [fail]

```


Suggestions?

---

### Post by Jozza The Wick on 2008-10-03
I'm having problems with this, too. I assume you've downloaded, compiled & installed OpenSSH 5.0 or later?


I've been looking at the Howto that lusixhan put together, but haven't succeeded myself yet. Have a look at his, and see if there are any pointers there that might help you out?

[http://ubuntuforums.org/showthread.php?t=858475](http://ubuntuforums.org/showthread.php?t=858475)

Of course, this maybe what you've been following already! It's kind of like the blind leading the blind here, but hopefully we can figure it out... I'm currently getting a 'home/jail directory not found' error when trying to log in, after following the instructions in the howto listed above...

---

### Post by jeff.m on 2008-10-28
Hello,
I faced the same problem on a Fedora 8.After downloading and install of OpenSSH-5.1, several configurations tests result always in the "directive not allowed" error message.

I finally found a solution for my (maybe specific) problem. On my Fedora distro, sshd was installed in /usr/sbin. The compilation / installation processes resulted in sshd to be installed in /usr/local/sbin, so I modified the /etc/init.d/sshd script this way :

```
SSHD=/usr/sbin/sshd
```

to

```
SSHD=/usr/local/sbin/sshd
```


Hope this helps

---

### Post by geirha on 2008-10-28
The init script is different on Ubuntu, so the equivalent of jeff.m's suggestion would be to first make a backup of the current init script
```
sudo cp /etc/init.d/ssh /etc/init.d/ssh.backup
```

Then replace all occurances of /usr/bin/sshd with /usr/local/bin/sshd

```
sudo sed -i 's,/usr/bin/sshd,/usr/local/bin/sshd,g' /etc/init.d/ssh
```

I haven't tried this myself so I don't know if it will work. Just giving you an idea to work with.

---

### Post by ram.coelho on 2009-06-20
Ok,

It is on a VMWare 64 bits running Ubuntu 8.10:

uname -a:
```
Linux server 2.6.27-7-server #1 SMP Fri Oct 24 07:37:55 UTC 2008 i686 GNU/Linux
```

This is what I am trying to do.
What follows was done locally, but happens just the same on remote clients:


```
user@server:/var$ sftp 192.45.2.137
Connecting to 192.45.2.137...
user@192.45.2.137's password:
Couldn't read packet: Connection reset by peer
```



/var/log/auth.log:

```
Jun 18 20:45:57 server sshd[23658]: debug1: Bind to port 22 on ::.
Jun 18 20:45:57 server sshd[23658]: Server listening on :: port 22.
Jun 18 20:45:57 server sshd[23658]: debug1: Bind to port 22 on 0.0.0.0.
Jun 18 20:45:57 server sshd[23658]: Server listening on 0.0.0.0 port 22.
Jun 18 20:46:03 server sshd[23658]: debug1: Forked child 23664.
Jun 18 20:46:03 server sshd[23664]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jun 18 20:46:03 server sshd[23664]: debug1: inetd sockets after dupping: 3, 3
Jun 18 20:46:03 server sshd[23664]: Connection from 192.45.2.137 port 42626
Jun 18 20:46:03 server sshd[23664]: debug1: Client protocol version 2.0; client software version OpenSSH_5.1p1 Debian-3ubuntu1
Jun 18 20:46:03 server sshd[23664]: debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
Jun 18 20:46:03 server sshd[23664]: debug1: Enabling compatibility mode for protocol 2.0
Jun 18 20:46:03 server sshd[23664]: debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
Jun 18 20:46:05 server sshd[23664]: debug1: user user matched group list sftp at line 80
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: initializing for "user"
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: setting PAM_RHOST to "192.45.2.137"
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: setting PAM_TTY to "ssh"
Jun 18 20:46:05 server sshd[23664]: Failed none for user from 192.45.2.137 port 42626 ssh2
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: password authentication accepted for user
Jun 18 20:46:06 server sshd[23664]: debug1: do_pam_account: called
Jun 18 20:46:06 server sshd[23664]: Accepted password for user from 192.45.2.137 port 42626 ssh2
Jun 18 20:46:06 server sshd[23664]: debug1: monitor_child_preauth: user has been authenticated by privileged process
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: establishing credentials
Jun 18 20:46:06 server sshd[23664]: pam_unix(sshd:session): session opened for user user by (uid=0)
Jun 18 20:46:06 server sshd[23671]: debug1: SELinux support disabled
Jun 18 20:46:06 server sshd[23671]: debug1: PAM: establishing credentials
Jun 18 20:46:06 server sshd[23664]: User child is on pid 23671
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: cleanup
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: deleting credentials
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: closing session
Jun 18 20:46:06 server sshd[23664]: pam_unix(sshd:session): session closed for user user
```



/etc/passwd:

```
user:1003:1003:User,,,:/:/usr/sbin/nologin
```



/etc/group:
```

sftp:1004:user
```



/etc/ssh/sshd_config:

```
# Logging
SyslogFacility AUTH
LogLevel DEBUG
Subsystem sftp internal-sftp
Match group sftp
ForceCommand internal-sftp
ChrootDirectory /var/sshbox
```


```

user@server:/var$ ls -l
drwxr-x--- 2 root root 4096 2009-06-18 20:05 sshbox
```



Did I miss something?

---

### Post by narcisgarcia on 2010-10-10
I've been working with a lot of internet tutorials. Here my compendium to configure better clients and servers:

[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(special care of users and permissions)

---

