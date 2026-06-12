---
title: "Install Transmission 1.61"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by mocka on 2009-06-01
Hi, is there any way to install the new Transmission 1.61? When I try to install through terminal (which I have to since I've got Ubuntu Server), with sudo apt-get install transmission-cli, I only get the 1.51 version.

Thanks in advance for answers.

---

### Post by sisco311 on 2009-06-01
You can get transmission 1.61 from the ppa repos:
[https://launchpad.net/~transmissionbt/+archive/ppa]("https://launchpad.net/~transmissionbt/+archive/ppa")

[s]uh, this is only for developers[https://launchpad.net/~bortis/+archive/ppa]("https://launchpad.net/~bortis/+archive/ppa")[/s]

---

### Post by mocka on 2009-06-01
Thank you. Anyhow, I'm all new to using the PPA repositories and have some trouble with adding the key. In the tutorial they say the key is something like "B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5", though I can only find a key that looks like this:  "1024R/F45955CE". What should I do?

---

### Post by mcduck on 2009-06-01
> **mocka said:**
> Thank you. Anyhow, I'm all new to using the PPA repositories and have some trouble with adding the key. In the tutorial they say the key is something like "B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5", though I can only find a key that looks like this:  "1024R/F45955CE". What should I do?

Click the key link on the repository's launchpad page and you get the full key (in this case it's a36aeec13a6f1a9edeb4b518fca4a9d8f45955ce).

---

### Post by sisco311 on 2009-06-01
usually is enough to use the last 8 hexadecimal digits:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com **F45955CE**
```

you can also click the link ([1024R/**F45955CE**]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xA36AEEC13A6F1A9EDEB4B518FCA4A9D8F45955CE&op=index")) to get the full key id:
> Search results for '0x**a36aeec13a6f1a9edeb4b518fca4a9d8f45955ce**'
Type bits/keyID    Date       User ID
pub  1024R/F45955CE 2009-01-21 Launchpad PPA for bortis
the bold part is the key id.

---

### Post by mocka on 2009-06-01
Thanks, it worked like a charm.

---

### Post by Pasdar on 2009-06-01
Next time just go to getdeb.net and download a deb file, easy install with two clicks.

---

### Post by mcduck on 2009-06-01
> **Pasdar said:**
> Next time just go to getdeb.net and download a deb file, easy install with two clicks.
Repositories are even better. Bit more work the first time but after that you'll always have the latest available version without doing anything..

I'd take a decent repository over single .deb package on a web site any day. :D

(That being said, getdeb.net *is* a great site.)

---

### Post by Tibuda on 2009-06-01
> **sisco311 said:**
> You can get transmission 1.61 from the ppa repos:
[https://launchpad.net/~bortis/+archive/ppa]("https://launchpad.net/~bortis/+archive/ppa")
This PPA suggests to use another one:
> Private repository. The repository is used only for developing and quality management purpose. If you search for transmission [Bittorrent client] binaries, please have a look at [https://launchpad.net/~transmissionbt/+archive/ppa](https://launchpad.net/~transmissionbt/+archive/ppa) and use these binaries instead!

---

### Post by sisco311 on 2009-06-01
> **danielrmt said:**
> This PPA suggests to use another one:

You are right, I've edited my first post.](*,)

I'm sorry for the inconvenience.

---

