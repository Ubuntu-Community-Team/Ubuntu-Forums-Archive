---
title: "SSH no longer working"
date: 2008-09-20
forum: General Help
---

### Post by ahounsome on 2008-09-20
Hi, I've been fiddling around with SCP and SSH and seem to have broken ssh. I've de-installed it and re-installed on both my laptop and my proxy server, but i still can't get any communication between the two using ssh. The error message is "connect to host (hostname) port 22: connection refused."

---

### Post by issih on 2008-09-20
Is the box you are connecting to running the ssh server? I think you need to have the package openssh-server installed on the box you are sshing into.

```
sudo apt-get install openssh-server
```

Other than that I can only suggest there might be a router/firewall getting in the way blocking port 22.

---

### Post by ahounsome on 2008-09-20
Thanks for that. I have moved forward a bit, but now get the message -
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
b6:51:ae:0e:e5:e1:48:25:f8:27:59:71:ef:bb:e6:a1.
Please contact your system administrator.
Add correct host key in /home/ahounsome/.ssh/known_hosts to get rid of this message.
Offending key in /home/ahounsome/.ssh/known_hosts:2
RSA host key for omaha has changed and you have requested strict checking.
Host key verification failed.

---

### Post by issih on 2008-09-20
Ok, that is almost certainly because you have reinstalled ssh, but it is using keys generated for the previous version.

Simply edit the known hosts file it mentions (you will need root privileges), the following command should do it:

```
gksudo gedit /home/ahounsome/.ssh/known_hosts
```

Simply remove the entire line that mentions the host you are connecting to (e.g. if the box is called bob remove the line that mentions bob)

Then try sshing in again, this time, because ssh no longer has any info about the host in question it will ask if you trust that host, and if you answer yes it will regenerate the key and add the new correct key into that file for you.

Hope that helps

P.S. looking more carefully it looks like the box you are connecting to is called omaha, so just remove the line pertaining to that :)

---

### Post by ahounsome on 2008-09-20
Right, now we're getting somewhere! There was a whole load of random characters in the known_hosts file but no "real" names of hosts. So I deleted the lot and have now authenticated to the target machine. I now need to see whether I can SCP into it to copy a load of home directory stuff to the target box. If this works then you've cracked it!

---

### Post by ahounsome on 2008-09-20
Ok, now I've got the following errors -

utah ahounsome # scp -r ahounsome@utah:/home/ahounsome/ ahounsome@omaha:/home/ahounsome/
ahounsome@utah's password: 
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
lost connection

---

### Post by issih on 2008-09-20
No longer something I'm aware of myself, as I haven't used scp much, but this thread looks similar, even if its a bit long in the tooth:

[http://www.fedoraforum.org/forum/archive/index.php/t-1319.html](http://www.fedoraforum.org/forum/archive/index.php/t-1319.html)

either way its worth running the command with the -v option in order to get some better debugging output.

---

### Post by ahounsome on 2008-09-20
Hi, here's the verbose output -

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ahounsome/.ssh/identity
debug1: Trying private key: /home/ahounsome/.ssh/id_rsa
debug1: Offering public key: /home/ahounsome/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
debug1: read_passphrase: can't open /dev/tty: No such device or address
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
debug1: read_passphrase: can't open /dev/tty: No such device or address
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
debug1: read_passphrase: can't open /dev/tty: No such device or address
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).

---

### Post by issih on 2008-09-20
Odd, it appears to be having trouble opening the terminal somewhere, I'm not sure why...

could you try doing it as:

```
scp -r /home/ahounsome/ ahounsome@omaha:/home/ahounsome/
```

So that you aren't specifying the localhost explicitly, I'm not really expecting it to work, but its worth a whirl.

---

### Post by ahounsome on 2008-09-20
Hi, ok great it works! I had to delete the contents of the known_hosts file again, then use your suggested string, and bingo scp happily copying over my home directory to the target box. Thank you very much for your time and help. Andy.

---

### Post by issih on 2008-09-20
Excellent, glad you got it working :)

---

