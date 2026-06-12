---
title: "Fail to update? Whats this?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by noveus on 2009-10-31
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

---

### Post by Partyboi2 on 2009-10-31
Hi, you need to add the key, to do this open a terminal (Applications>Accessories>Terminal) and type
```
gpg --keyserver keyserver.ubuntu.com --recv 5A9BF3BB4E5E17B5
gpg --export --armor 5A9BF3BB4E5E17B5 | sudo apt-key add -

``````
sudo apt-get update
```

---

### Post by noveus on 2009-10-31
KK, ill give it a try. Thanks.

---

### Post by noveus on 2009-10-31
Im afraid it still the same.
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

---

### Post by noveus on 2009-10-31
yeongren@yeongren-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv 5A9BF3BB4E5E17B5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
yeongren@yeongren-laptop:~$ gpg --export --armor 5A9BF3BB4E5E17B5 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

---

### Post by noveus on 2009-11-01
Can anyone help me with this please?

---

### Post by Sef on 2009-11-01
Here's a youtube video of [installing a ppa]("http://video.google.com/videosearch?hl=en&rlz=1C1CHMI_enUS345US345&q=ubuntu+install+ppa+key&um=1&ie=UTF-8&ei=_SHtSoKuAYuuswOu2dj1Aw&sa=X&oi=video_result_group&ct=title&resnum=4&ved=0CBgQqwQwAw#").

Read this also: [PPA Install]("https://help.ubuntu.com/community/Repositories/CommandLine#Adding Launchpad PPA Repositories")
> Adding Launchpad PPA Repositories
Ubuntu 9.10, Karmic Koala, introduces a convenient new command for adding Launchpad PPA (Personal Package Archive) repositories via the command line: add-apt-repository.

The repository is registered with APT and an entry is created in the /etc/apt/sources.list.d folder.
If a public key is required and available it is automatically downloaded and registered.
sudo add-apt-repository ppa:<repository-name>
Example: sudo add-apt-repository ppa:nhandler

---

