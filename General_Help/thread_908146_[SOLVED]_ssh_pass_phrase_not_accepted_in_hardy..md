---
title: "[SOLVED] ssh pass phrase not accepted in hardy."
date: 2008-09-02
forum: General Help
---

### Post by MrGrey1 on 2008-09-02
I'm trying to connect to my server using ssh with encrypted pass key. The pass key was generated using putty, in gutsy I had no problems, in hardy it asks for the pass phrase but will not accept it, (yes the pass phrase is correct). I type in the pass phrase and it drops to another line asking for the pass phrase again. This happens 3 times at which point it says Permission denied (public key). I know the key works as I use it from winblows box using putty without any problems. I have searched around the forums and see some mention of a program called seahorse which I gather wasn't in gutsy, the solution there was to change the file type of the key using putty keygen and then import to seahorse. I do not want to have to do this, I would like it to work as it did in Gutsy ie, I just direct the ssh to my passkey, it asks for the pass phrase and I connect. Is there something I need to do in Hardy that was not required in gutsy to get a pass key working? Any ideas would be most appreciated.

---

### Post by joenix on 2008-09-02
Can you try running ssh in verbose mode? (ssh -vvv user@server)
Have you tried connecting with the same key from another box recently? If not, please do so, so we can be sure there is no problem on the server side.

---

### Post by MrGrey1 on 2008-09-02
> **joenix said:**
> Can you try running ssh in verbose mode? (ssh -vvv user@server)
Have you tried connecting with the same key from another box recently? If not, please do so, so we can be sure there is no problem on the server side.

~$ ssh -vvv *****@************** -i /media/disk/portablePrograms/portaputty/masterkey.ppk -p *****
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to *****@************** port *****.
debug1: Connection established.
debug3: Not a RSA1 key file /media/disk/portablePrograms/portaputty/masterkey.ppk.
debug2: key_type_from_name: unknown key type 'PuTTY-User-Key-File-2:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Encryption:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Comment:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Public-Lines:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type 'Private-Lines:'
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
debug2: key_type_from_name: unknown key type 'Private-MAC:'
debug3: key_read: missing keytype
debug1: identity file /media/disk/portablePrograms/portaputty/masterkey.ppk type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
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
debug2: dh_gen_key: priv key bits set: 132/256
debug2: bits set: 511/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: put_host_port: *****@************** port *****
debug3: put_host_port: *****@************** port *****
debug3: check_host_in_hostfile: filename /home/colin/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/colin/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host '*****@************** port *****' is known and matches the RSA host key.
debug1: Found key in /home/colin/.ssh/known_hosts:1
debug2: bits set: 480/1024
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
debug2: key: /media/disk/portablePrograms/portaputty/masterkey.ppk ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /media/disk/portablePrograms/portaputty/masterkey.ppk
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/media/disk/portablePrograms/portaputty/masterkey.ppk': 
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug2: bad passphrase given, try again...
Enter passphrase for key '/media/disk/portablePrograms/portaputty/masterkey.ppk': 
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug2: bad passphrase given, try again...
Enter passphrase for key '/media/disk/portablePrograms/portaputty/masterkey.ppk': 
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug2: bad passphrase given, try again...
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).


Thanks for the quick reply, I have ssh on the server setup up on a non default port, I direct ssh to the location of the key file just as I did on gutsy as above. 
I can connect and access the server from a dual boot windows install on the same machine as the hardy install using the same key and putty so I know the server is there and working properly and I know that I can get out through the router from this end. 
As you can see from the log above it says bad pass phrase given, I know without doubt I'm entering the pass phrase correctly. It doesn't seem to recognize the key type...any ideas other then converting the key? As I said this used to work on gutsy so what's changed?

EDIT: As I said 'I THINK' this used to work on gutsy so what's changed? ... It's been a while since I've done this as only needed when on holiday.

---

### Post by monkeyking on 2008-09-02
they updated some of the pub keys.

I would try removing all your old keys to a new folder and then try

```
mv .ssh .ssh_backup
```

That is if your on a unix machine trying to connect to your linux box.

If you use another ssh client the procedure is most likely different

---

### Post by MrGrey1 on 2008-09-03
> **monkeyking said:**
> they updated some of the pub keys.

I would try removing all your old keys to a new folder and then try

```
mv .ssh .ssh_backup
```

That is if your on a unix machine trying to connect to your linux box.

If you use another ssh client the procedure is most likely different


I'm sorry I don't really see what this would achieve?
When this problem started the .ssh file on the local machine was empty. I was referencing a usb drive where my ssh key was located. In Gutsy it used to ask me for a pass phrase, I'd enter it and away we'd go but now in Hardy it wont accept the pass phrase entered. I know the key works as I used it from a windows box with no problems. For some reason Hardy does not recognize or accept the pass phrase for the key. It's got me stumped... permissions are good, just don't know what else to try.

I may have got confused on this issue, it's been a fair while since I last used this setup and I've been working on it now so long I'm starting to double guess myself. Correct me if I'm wrong but all I should need on the local machine is the passkey and it's pass phrase to connect to my server? The key is a .ppk file generated in putty. I'm 99% sure it worked in Gutsy but as I said I'm beginning to double guess myself.
Thanks for the help anyway.

EDIT: [http://www.gossamer-threads.com/lists/openssh/dev/38839](http://www.gossamer-threads.com/lists/openssh/dev/38839)
This post suggests that it can't read the decrypted file so assumes I typed the key incorrectly... I think?

---

### Post by monkeyking on 2008-09-03
> **MrGrey1 said:**
> I'm sorry I don't really see what this would achieve?

The ssh server in ubuntu has updated [http://www.debian.org/security/2008/dsa-1571](http://www.debian.org/security/2008/dsa-1571) .

I didn't really understand your problem, so I told you to start from scratch.


What they did in short, was to replace their pub keys.

An ssh client(on ubuntu) keep a list of known sshservers.
So when you try log in, even though you have the key-password, it denies you access since the key for the server has changed.

Thats why I told you to remove the history of previous sessions.

you can disable this by setting StrictHostKeyChecking=no

I didn't know if this solution would apply to you,
but it was something I would try.

good luck

---

### Post by MrGrey1 on 2008-09-21
Resolved
I was using the wrong key file, ie the .ppk file which is for putty,
Big round of DERRR for me.

---

