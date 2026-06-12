---
title: "Ubuntu 8.04 - ssh and X forwarding doesn't work"
date: 2008-09-08
forum: General Help
---

### Post by crzdude on 2008-09-08
I have ran across other similar posts but none of them seemed to work for me. Basically, I am trying to "ssh -X" onto another linux box from my ubuntu 8.04 desktop and to launch xclock . This is what I do on my ubuntu desktop :

1. Open xterm
2. Type "xhost +"
3. Run "ssh -X <user>@<server>"

Now, I am on logged into the other linux box. I type xclock and after waiting for about 2 or 3 minutes I get:

Error: Can't open display: <my ip>:0

The very same steps above work if try them on a Windows box running X-Cygwin. 

FYI: I have already set the following :

$ grep "DisallowTCP=" /etc/gdm/gdm.conf
DisallowTCP=false

$ grep "Forward" /etc/ssh/sshd_config 
X11Forwarding yes

- "ssh -v -X " yields :

 $ ssh -v -X <user>@<server>
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to <my ip> [<my ip>] port 22.
debug1: Connection established.
debug1: identity file /home/<my user name>/.ssh/identity type -1
debug1: identity file /home/<my user name>/.ssh/id_rsa type -1
debug1: identity file /home/<my user name>/.ssh/id_dsa type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_4.1
debug1: match: OpenSSH_4.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '<my ip>' is known and matches the RSA host key.
debug1: Found key in /home/<my user name>/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/<my user name>/.ssh/identity
debug1: Trying private key: /home/<my user name>/.ssh/id_rsa
debug1: Trying private key: /home/<my user name>/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password:
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
Warning: No xauth data; using fake authentication data for X11 forwarding.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_CA.UTF-8

---

### Post by crzdude on 2008-09-08
FYI: Before anyone asks ... yes, I've made sure that the X server is not running with the nolisten option:

$ ps -ef | grep X
root     15271 15265  2 06:53 tty7     00:01:02 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7

---

### Post by xeth_delta on 2008-09-08
You could also try the -Y option, instead of -X

---

### Post by crzdude on 2008-09-08
I get the same behavior with "ssh -Y"

---

### Post by Grendelmon on 2008-09-20
I'm having the same exact issue.  I'm thinking that it has something to do with the "-nolisten" arguement (do a 'ps -ef|grep X' to see) for the X server.  I haven't figured out how to disable it yet... there are no arguments in the startx script.

---

### Post by smithsmg on 2008-09-26
I had same problem - this is solution: apt-get install xauth

---

