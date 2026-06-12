---
title: "PLaces &gt; Connect to Server = Broken"
date: 2008-10-09
forum: General Help
---

### Post by skydiver|goose on 2008-10-09
I can't SSH into my friend's server, or SMB into my networked PC with all my media on it.

When I try and SSH, it just times out.

When I try and SMB, it says there's no application suited to handle it.

How can I fix this?

---

### Post by bluefrog on 2008-10-09
by giving more information.

where is your client pc, where is your server pc?
are they both switched on?
is one behind a firewall/router/modem router?
is ssh server installed on the server?
is samba installed-activated on the server?
and so on...

---

### Post by skydiver|goose on 2008-10-09
the networks are fine, I used to SSH onto both with my old laptop which was running 7.10 32 bit.

This is my new laptop, running 8.04 64 bit.

SMB and SSH both worked previously, I can do them both from other computers.

---

### Post by cariboo on 2008-10-09
Can you ping the other computers on the network? What has changed since you got a new laptop?

To ping the other computers on the network go to System-->Administration-->Network tools-->Ping, and enter the network address of one of the computers on the network. If you can ping you've got half of the battle won.

Jim

---

### Post by skydiver|goose on 2008-10-09
I can ping the server and other computers, I just can't connect to them.

New laptop, upgraded OS, 64 bit.

Nothing server side network side or computer side changed

---

### Post by cariboo on 2008-10-09
I just did a reinstall of Intrepid, and I had the same problem, ssh wouldn't let me connect using sftp in Nautilus. The way I fixed the problem was to open up a terminal and connect using ssh, my server asked if it was ok to connect as it looked like my new install was an unknown computer I said yes and connected with know problem. You might have a problem if you are using shared keys.

Jim

---

### Post by geeth on 2008-10-09
> **skydiver|goose said:**
> 

When I try and SMB, it says there's no application suited to handle it.

How can I fix this?


Tick the box to save the details as a bookmark when you enter the server details.
Then after the error message go to places > bookmarks and look for the name that you gave it. this should open the smb share.

With SSH have you tried from the terminal?

---

### Post by skydiver|goose on 2008-10-10
Yes, I've tried it through terminal and Place > Connect to a server

Neither works for SSH and SMB.

I'm running winSCP and PUTTY through WINE right now to be able to connect to my server x.x

and I still can't even SMB and get all my backed up files from my networked PC to my new laptop!

---

### Post by skydiver|goose on 2008-10-10
bump

---

### Post by Sam on 2008-10-10
From a linux box install the package "nmap" then run
```
nmap -p 22 host
```where "host" is the ip address of the server.
It will tell you if the SSH port is visible from the outside world.

---

### Post by skydiver|goose on 2008-10-10
goose@goose-laptop:~$ nmap -p 22 SERVER.org

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-10-10 19:48 CDT
Interesting ports on [www.SERVER.org](www.SERVER.org) (64.62.XXX.XX):
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.351 seconds
goose@goose-laptop:~$

---

### Post by Sam on 2008-10-10
Strange...

What's the output when you try to connect with ssh ?

---

### Post by skydiver|goose on 2008-10-10
goose@goose-laptop:~$ ssh -vvv [email]goose@SERVER.org[/email]
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to SERVER.org [64.62.XXX.XX] port 22.
debug1: Connection established.
debug1: identity file /home/goose/.ssh/identity type -1
debug1: identity file /home/goose/.ssh/id_rsa type -1
debug1: identity file /home/goose/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-2
debug1: match: OpenSSH_5.1p1 Debian-2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 131/256
debug2: bits set: 510/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/goose/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/goose/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'SERVER.org' is known and matches the RSA host key.
debug1: Found key in /home/goose/.ssh/known_hosts:1
debug2: bits set: 517/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/goose/.ssh/identity ((nil))
debug2: key: /home/goose/.ssh/id_rsa ((nil))
debug2: key: /home/goose/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/goose/.ssh/identity
debug3: no such identity: /home/goose/.ssh/identity
debug1: Trying private key: /home/goose/.ssh/id_rsa
debug3: no such identity: /home/goose/.ssh/id_rsa
debug1: Trying private key: /home/goose/.ssh/id_dsa
debug3: no such identity: /home/goose/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
[email]goose@SERVER.org[/email]'s password: 
debug3: packet_send2: adding 64 (len 57 padlen 7 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 255
debug3: tty_make_modes: 7 255
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 1
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 1
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug1: Sending environment.
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env SHELL
debug3: Ignored env DESKTOP_STARTUP_ID
debug3: Ignored env TERM
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

---

### Post by skydiver|goose on 2008-10-10
bump

---

### Post by skydiver|goose on 2008-10-11
re bump

omg hax help please bbq

---

### Post by skydiver|goose on 2008-10-11
buuuuuuuuuuuump

heeeeeeeeeeeeeeelp

---

### Post by skydiver|goose on 2008-10-11
there has to be SOMEONE out there who can help me

---

### Post by skydiver|goose on 2008-10-11
pleeeeeeeeeeeeeeeeeeeeeease?

---

### Post by _sAm_ on 2008-10-11
Have you tried to stop SSH from timing out? [http://ubuntu.wordpress.com/2006/02/03/keeping-ssh-sessions-alive/](http://ubuntu.wordpress.com/2006/02/03/keeping-ssh-sessions-alive/)

Have you tried to manually mount the SMB shares(meaning without Nautilus)?

I cant use Nautilus to connect to SMB shares either, and hope (and guess) it is fixed in gnome 2.24 witch upcoming Ubuntu use.

---

### Post by skydiver|goose on 2008-10-11
didn't work :/

---

### Post by _sAm_ on 2008-10-11
SSH timeout or SMB?

---

### Post by skydiver|goose on 2008-10-11
SSH timeout, SMB is "Unknown application type"

---

### Post by skydiver|goose on 2008-10-13
buuuuuuuuump

---

