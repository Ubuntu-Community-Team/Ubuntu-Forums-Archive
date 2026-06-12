---
title: "Adding PPA key to apt"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by lgp171188 on 2009-08-18
I tried to download and add a PPA key but I get an error like this

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D
[sudo] password for guru: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 7613768D
gpg: requesting key 7613768D from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

I am behind a proxy server and firewall. But adding --keyserver-option proxy-server=<proxy server> doesn't work either. Is there a way I can manually do the downloading and adding of the key? I am unable to download the key using gpg as well.

---

### Post by Partyboi2 on 2009-08-19
Hi, you can go [[COLOR=Blue]here[/COLOR]]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71346C8340130828") and copy and paste the contents into a text editor (Applications>Accessories>Text Editor) and save it to your Desktop. Then open Software Sources (System>Admin>Software Sources) and under the "Authentication" tab choose "import" and import the key you downloaded and saved to your Desktop. Then refresh your package list.

---

