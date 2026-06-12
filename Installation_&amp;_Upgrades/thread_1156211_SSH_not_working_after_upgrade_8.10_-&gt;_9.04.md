---
title: "SSH not working after upgrade 8.10 -&gt; 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by rpsimao on 2009-05-11
Hi

I upgrade my ubuntu server form 8.10 to 9.04.
Now when I try to connect via SSH i get this error message:
PTY allocation request failed on channel 0

And I can't connect.

Any advice
Thanks
Ricardo

---

### Post by lvleph on 2009-05-11
When I upgraded it asked if I wanted to overwrite my SSH config file. I would check that first.

---

### Post by ThomasTC on 2009-05-13
I have the same problem. Just to clarify, it is the SSH *client* that stopped working on the recently upgraded host. The problem is not on the server side, because using PuTTY under Windows I can log in just fine.

Here's the output of ssh -vvv:
```
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/thomas/.ssh/config
debug1: Applying options for tweek
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to tweek [192.168.1.2] port 22.
debug1: Connection established.
debug1: identity file /home/thomas/.ssh/identity type -1
debug3: Not a RSA1 key file /home/thomas/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/thomas/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/thomas/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.5p1
debug1: match: OpenSSH_4.5p1 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
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
debug2: kex_parse_kexinit: ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: dh_gen_key: priv key bits set: 141/256
debug2: bits set: 478/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/thomas/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/thomas/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'tweek' is known and matches the DSA host key.
debug1: Found key in /home/thomas/.ssh/known_hosts:1
debug2: bits set: 548/1024
debug1: ssh_dss_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/thomas/.ssh/id_rsa (0x7f882d10ea20)
debug2: key: backdown@cartman (0x7f882d114d30)
debug2: key: /home/thomas/.ssh/identity ((nil))
debug2: key: /home/thomas/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,keyboard-interactive
debug3: start over, passed a different list publickey,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/thomas/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 533
debug2: input_userauth_pk_ok: fp 0d:46:a8:5f:21:33:8c:54:27:49:f3:4b:2c:2b:cd:c9
debug3: sign_and_send_pubkey
Agent admitted failure to sign using the key.
debug1: Offering public key: backdown@cartman
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Server accepts key: pkalg ssh-rsa blen 533
debug2: input_userauth_pk_ok: fp 00:d5:d9:97:06:44:c4:53:26:d1:bc:44:03:d0:ea:c1
debug3: sign_and_send_pubkey
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: x11_get_proto: /usr/bin/X11/xauth  list :0.0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 0
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env HISTSIZE
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env MPD_HOST
debug3: Ignored env LD_LIBRARY_PATH
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PATH
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug3: Ignored env EDITOR
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env PS1
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env FIGNORE
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LESS
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env XAUTHORITY
debug3: Ignored env COLORTERM
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug1: Remote: X11 forwarding disabled in user configuration file.
debug2: channel_input_confirm: type 100 id 0
PTY allocation request failed on channel 0
debug2: channel 0: rcvd adjust 131072
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0
```

---

### Post by ThomasTC on 2009-05-13
After some further experiments, the problem appears to be with the gnome-keyring-daemon. It popped up when I tried to SSH, but I denied it because I haven't used that key in ages and forgot the password.

After killing gnome-keyring-daemon I simply got the passphrase prompt in the console, hit Enter, typed my normal SSH password and it worked fine. Any clues on how to solve this permanently?

---

