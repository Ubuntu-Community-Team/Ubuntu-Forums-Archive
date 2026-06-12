---
title: "After upgrading from 8.04 can longer use apt-get"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by broth420 on 2009-05-19
I upgraded my Ubuntu Server 8.04 to 8.10 today (I think it went to 8.10) and now I can' run any apt commands. when I run
sudo apt-get update it hangs on each repo and then tell me: 

Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

over and over again. I can't upgrade the OS to 9.04, and I can't run apt-get upgrade

I think it is my sources.list file, but not sure.
Any ideas on what could be wrong or how to fix it
Thanks, bill

---

### Post by Partyboi2 on 2009-05-19
Are you using a proxy? If so check that the settings are correct in Synaptic (Synaptic>Pref>Network)

---

### Post by broth420 on 2009-05-28
no proxy server, and I just built a new 9.04 server, set the nic static, and no connection any more. check resolv/conf file and it has the correct dns server listed.

---

### Post by broth420 on 2009-05-28
PS  just changed my address back to dhcp and it is fine. I am using server 9.04 64

---

### Post by broth420 on 2009-06-01
Anyone have any idea about this, or where I can look? It has happened on three different servers with different hardware.
Thanks, Bill

---

