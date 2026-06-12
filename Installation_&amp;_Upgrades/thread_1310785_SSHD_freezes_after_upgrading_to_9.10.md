---
title: "SSHD freezes after upgrading to 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by oydna on 2009-11-02
After I upgraded from 9.04 to 9.10 I can´t log in by SSH, when I was running 9.04 it was working. The SSHD accepts my connection and asks for my password, but after entering the password nothing happens. I can connect by VNC without any problems. If I connect by VNC and open a terminal on the Ubuntu 9.10 box and do a "ssh localhost" the same thing happens, after the password the shell freezes. 

Thanks for any help :)


Debug info below:

```

ssh -vv 192.168.1.11
OpenSSH_5.2p1, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.11 [192.168.1.11] port 22.
debug1: Connection established.
debug1: identity file /Users/oydna/.ssh/identity type -1
debug1: identity file /Users/oydna/.ssh/id_rsa type -1
debug1: identity file /Users/oydna/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
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
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 120/256
debug2: bits set: 496/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.11' is known and matches the RSA host key.
debug1: Found key in /Users/oydna/.ssh/known_hosts:1
debug2: bits set: 522/1024
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
debug2: key: /Users/oydna/.ssh/identity (0x0)
debug2: key: /Users/oydna/.ssh/id_rsa (0x0)
debug2: key: /Users/oydna/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/oydna/.ssh/identity
debug1: Trying private key: /Users/oydna/.ssh/id_rsa
debug1: Trying private key: /Users/oydna/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
oydna@192.168.1.11's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
[then freezes]

```


```

auth.log:
Nov  2 08:56:25 box sshd[7671]: debug1: PAM: password authentication accepted for oydna
Nov  2 08:56:25 box sshd[7671]: debug1: do_pam_account: called
Nov  2 08:56:25 box sshd[7671]: Accepted password for oydna from 192.168.1.138 port 59336 ssh2
Nov  2 08:56:25 box sshd[7671]: debug1: monitor_child_preauth: oydna has been authenticated by privileged process
Nov  2 08:56:25 box sshd[7671]: debug1: PAM: establishing credentials
Nov  2 08:56:25 box sshd[7671]: pam_unix(sshd:session): session opened for user oydna by (uid=0)

```

---

