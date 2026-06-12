---
title: "keyserver.ubuntu.com problem"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by uv101 on 2009-10-16
Anyone else having problems getting keys?
 
I was OK until yesterday.
 
```
xbmc@xbmc-app:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 318C7509 9317790E
[sudo] password for xbmc:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 318C7509 9317790E
gpg: requesting key 318C7509 from hkp server keyserver.ubuntu.com
gpg: requesting key 9317790E from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
xbmc@xbmc-app:~$

```
 
From another PC is i browse to [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6D975C4791E7EE5E](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6D975C4791E7EE5E) I also get an error. I beleive this link should give me key as a text file for manual import.
 
I was trying to get the nvidia key last night too and that gave me the same problem.
 
keyxerver.ubuntu.com resloves as 91.189.94.173 which I can ping (altough I suspect this is a hide address)
 
Anyone having/not having problems with keys?
 
Ian

---

### Post by uv101 on 2009-10-16
Anyone else having problems getting keys?
 
I was OK until yesterday.
 
```
xbmc@xbmc-app:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 318C7509 9317790E
[sudo] password for xbmc:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 318C7509 9317790E
gpg: requesting key 318C7509 from hkp server keyserver.ubuntu.com
gpg: requesting key 9317790E from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
xbmc@xbmc-app:~$

```
 
From another PC is i browse to [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6D975C4791E7EE5E](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6D975C4791E7EE5E) I also get an error. I beleive this link should give me key as a text file for manual import.
 
I was trying to get the nvidia key last night too and that gave me the same problem.
 
keyxerver.ubuntu.com resloves as 91.189.94.173 which I can ping (altough I suspect this is a hide address)
 
Anyone having/not having problems with keys?
 
Ian

---

### Post by anthro398 on 2009-10-30
There are a list of alternate servers at [https://bugs.launchpad.net/ubuntu-website/+bug/435193/comments/14]("https://bugs.launchpad.net/ubuntu-website/+bug/435193/comments/14")

From that page:
keyserver hkp://subkeys.pgp.net
keyserver hkp://pgp.mit.edu
keyserver hkp://pool.sks-keyservers.net (random server)
keyserver hkp://keys.nayr.net
keyserver [http://keys.gnupg.net](http://keys.gnupg.net)
keyserver [http://wwwkeys.xx.pgp.net](http://wwwkeys.xx.pgp.net) where xx is a two-letter country code.

---

### Post by AnomalyDetected on 2009-11-16
If you time out while connecting to keyservers, it's probably that your firewall is blocking the necessary tcp port (11371, I believe).

If you can open up that port in your firewall, you'll be good to go. If you cannot, here's a workaround:

Browse to [http://keys.gnupg.net/](http://keys.gnupg.net/)
Search for the key name you are looking for (i.e. "Nvidia" or "Wine PPA").
When found, click the key ID number.
Copy/paste the pgp key into a text editor (i.e. gedit) and save the text file locally.
Under System/Administration/Software Sources, go to the Authentication tab, click Import Key File, and browse to the text file you saved.
All done! (You can delete the text file now).

This has helped me on a work network where I had no access to change the firewall rules.

---

### Post by caio2112 on 2010-10-29
You can force it to use port 80:
sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 318C7509 9317790E


> **uv101 said:**
> Anyone else having problems getting keys?
 
I was OK until yesterday.
 
```
xbmc@xbmc-app:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 318C7509 9317790E
[sudo] password for xbmc:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 318C7509 9317790E
gpg: requesting key 318C7509 from hkp server keyserver.ubuntu.com
gpg: requesting key 9317790E from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
xbmc@xbmc-app:~$

```
 
From another PC is i browse to [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6D975C4791E7EE5E](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6D975C4791E7EE5E) I also get an error. I beleive this link should give me key as a text file for manual import.
 
I was trying to get the nvidia key last night too and that gave me the same problem.
 
keyxerver.ubuntu.com resloves as 91.189.94.173 which I can ping (altough I suspect this is a hide address)
 
Anyone having/not having problems with keys?
 
Ian

---

