---
title: "HOW TO: Passwordless ssh to MyBook World Edition"
date: 2010-08-28
forum: Hardware
---

### Post by mikkellund42 on 2010-08-28
Hi,

In order to run an automated [rsync]("http://samba.anu.edu.au/rsync/") backup script, I have been trying to access my MyBook World Edition 1 TB NAS (white light) through ssh. The trouble is that I have to enter the ssh password to access the NAS, and therefore I can not run the script as an automated backup routine (*i.e.* through crontab).

I found a solution based on [this post on LiNUX Horizon]("http://www.linuxhorizon.ro/ssh-wo-passw.html"), but the original article is meant for access from one computer to another, and the setup of the MyBook World Edition (mbwe) requires some tweaking. Please note that this solution requires changing some of the root files on your mbwe and thus could render your device unusable. Use this how-to at *your own risk*.

**Enable ssh**
First of all you will need to enable ssh on your mbwe. Log on to the Network Storage Manager (web admin interface) and select "Advanced Mode" from the top menu, then select "Advanced" from the "System" tab. Under "SSH access" tick the "Enable" box and click submit. Your mbwe will probably need to reboot in order for the changes to take effect.

**Access mbwe as root**
In the examples below I will assume that your mbwe has the address 192.168.1.2. Once your mbwe is back online from rebooting go to your terminal and type
```
ssh root@192.168.1.2
```
The default password is "welc0me". You should change this password - especially if your mbwe is visible outside your home network.

Change the password by typing
```
passwd root
```

**Preparing mbwe**
We will now enable passwordless access from your computer to the mbwe as outlined in the article by [LiNUX Horizon]("http://www.linuxhorizon.ro/ssh-wo-passw.html"). In summary this is done by creating an authorization key on you local computer and copying this key to your mbwe. In this way your mwbe will know that whenever a computer with this authorization key is trying to access via ssh, it does not need to ask for a password.

To enable passwordless ssh access we need to alter the file /etc/ssh_config. To do this we will use the vi editor, as it is installed on your mbwe by default. Assuming that you are still connected to your mbwe as root type
```
vi /etc/ssh_config
```
and locate the lines
```
#   IdentityFile ~/.ssh/identity                                   
#   IdentityFile ~/.ssh/id_rsa                
#   IdentityFile ~/.ssh/id_dsa 
```

We need to uncomment the line "IdentityFile ~/.ssh/id_rsa". Assuming you are not familiar with the vi editor (I wasn't), I will go through the details: To remove the comment character "#"  place the cursor at the beginning of that line and press "r" and then "space" (r means _r_eplace current character with (in this case) space). Then press the escape key and type
```
:wq
```
(meaning _w_rite to file and _q_uit. Remember the ":" at the beginning of this command).

We just told the mbwe that it can find the identity file at the location ~/.ssh/, but this directory does not exist. To create it type
```
mkdir /shares/.ssh
```

and change its permissions by typing
```
chmod 700 /shares/.ssh
```

You can now close the ssh connection to mbwe by typing
```
exit
```

**Generate RSA key**
The mbwe now knows where to find the rsa authorization keys, but it still doesn't know the key of your computer. To generate an authorization key pair type
```
ssh-keygen -t rsa
```
in your terminal and press "Enter" three times (you don't want a password on your rsa key, as you would then have a password protected passwordless connection ;)).

This newly generated key will need to be added to the mbwe list of authorized keys. In the terminal type
```
cat ~/.ssh/id_rsa.pub | ssh -l root 192.168.1.2 'cat >> /shares/.ssh/authorized_keys'
```
and enter the root password (hopefully this should be the last time you enter a password).

Voilà! Your mbwe should now be ready for passwordless ssh access. You can test this by typing
```
ssh 192.168.1.2
```
(assuming that there exists a user on your mbwe with the same user name as on your computer). You should now be logged on without the password prompt - otherwise you may find help in the troubleshooting section of the article by [LiNUX Horizon]("http://www.linuxhorizon.ro/ssh-wo-passw.html").

**rsync**
The next step is to make a great backup script, that can run from your crontab. Inspiration on rsync scripts can be found on the [rsync examples page]("http://samba.anu.edu.au/rsync/examples.html").

**Tip:**
For safety reasons you should now change the permissions of the authorized_keys file. Log onto your mbwe as root and type
```
chmod 600 /shares/.ssh/authorized_keys
```

---

### Post by aCruceSalus on 2011-04-12
I have tried this post as well as several others with no success in connecting without a password prompt.

Here are some links to other guides that I have tried and failed:
[http://www.topwebhosts.org/articles/remote-backup-tar-ssh-cron.php](http://www.topwebhosts.org/articles/remote-backup-tar-ssh-cron.php)
[http://www.linuxquestions.org/questions/linux-server-73/ssh-automated-login-via-public-key-not-working-748134/](http://www.linuxquestions.org/questions/linux-server-73/ssh-automated-login-via-public-key-not-working-748134/)
[http://www.smallnetbuilder.com/nas/nas-howto/30871-how-to-back-up-nas-to-nas-part-3](http://www.smallnetbuilder.com/nas/nas-howto/30871-how-to-back-up-nas-to-nas-part-3)

Right now I am just using terminal from my mac to connect to MyBook WE White Light via ssh. Then I want to move on to using my remote Linux server to connect. Both my Mac and Linux are remotely connecting to the MBWE drive, but not without having to enter a password.

Here is my ssh_config file:
```
# Host *
#   ForwardAgent no
#   ForwardX11 no
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
   IdentityFile ~/.ssh/identity
   IdentityFile ~/.ssh/id_rsa
   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-c$
#   EscapeChar ~

```Here is my sshd_config file:
```
#Port 22
#Protocol 2,1
#ListenAddress 0.0.0.0
#ListenAddress ::

# HostKey for protocol version 1
#HostKey /etc/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh_host_rsa_key
#HostKey /etc/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 768

# Logging
#obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6

#RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      ~/.ssh/authorized_keys

# For this to work you will also need host keys in /etc/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication mechanism.
# Depending on your PAM configuration, this may bypass the setting of
# PasswordAuthentication, PermitEmptyPasswords, and
# "PermitRootLogin without-password". If you just want the PAM account and
# session checks to run without PAM authentication, then enable this but set
# ChallengeResponseAuthentication=no
#UsePAM no
#PermitRootLogin without-password

#AllowTcpForwarding yes
#GatewayPorts no
#X11Forwarding no
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
UsePrivilegeSeparation yes
#Compression yes
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10

# no default banner path
#Banner /some/path

ClientAliveInterval 15
ClientAliveCountMax 4

# override default of no subsystems
Subsystem       sftp    /usr/sbin/sftp-server

```Here is the connection info with the -v switch:
```
OpenSSH_5.2p1, OpenSSL 0.9.8l 5 Nov 2009
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to 12.34.56.78 [12.34.56.78] port 22.
debug1: Connection established.
debug1: identity file /Users/username/.ssh/identity type -1
debug1: identity file /Users/username/.ssh/id_rsa type 1
debug1: identity file /Users/username/.ssh/id_dsa type 2
debug1: Remote protocol version 1.99, remote software version OpenSSH_3.9p1
debug1: match: OpenSSH_3.9p1 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '12.34.56.78' is known and matches the RSA host key.
debug1: Found key in /Users/username/.ssh/known_hosts:8
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/username/.ssh/identity
debug1: Offering public key: /Users/username/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Offering public key: /Users/username/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: password
root@12.34.56.78's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.

```Maybe someone can shed some light on my issue.
Thanks

---

### Post by aCruceSalus on 2011-04-14
I finally got it working. After upgrading ssh on MBWE using this link, [http://mybookworld.wikidot.com/update-ssh](http://mybookworld.wikidot.com/update-ssh), I was able to connect using a public key.

---

