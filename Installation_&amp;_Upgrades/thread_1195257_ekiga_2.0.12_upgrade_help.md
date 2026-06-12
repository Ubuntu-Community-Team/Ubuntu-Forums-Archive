---
title: "ekiga 2.0.12 upgrade help"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by woop on 2009-06-23
ekiga isnt working in 8.10 for me I can ring the echo test but the call back test never calls back............does 2.0.12 ever work??

am I better upgrading? which version do I upgrade to? and how?

Im a beginner so take that into account when explaining please

thanks:D

---

### Post by woop on 2009-06-24
anybody??

---

### Post by spcwingo on 2009-06-24
You can add this PPA:

[https://launchpad.net/~sevmek/+archive/ppa]("https://launchpad.net/~sevmek/+archive/ppa")

by opening Applications>Accessories>Text Editor and copying/pasting this in:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXYvBwEEAO0K/lSuYF1TZraRrOwHAVY2lvg1TE5QrFYzlXitw3roJJ+oxqtxICEFjRvs
jN/abLtVNqM3KvLtmL+6e0KOeIZKFGDIAdNO8AvAXSvjVIIQ7uv2ZKFZ6zeLr9MbgLHFuxrs
GJ8lSdvThFEDSOlh+41yNA9URGwrwe2spUir7jWjABEBAAG0IExhdW5jaHBhZCBQUEEgZm9y
IFlhbm5pY2sgRGVmYWlziLYEEwECACAFAkl2LwcCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIX
gAAKCRAl2vn+gwRIUZkIA/9w5+imGUD6lswMAtOhqZTzMnqqgoCmW0Cfd2cvue6Rk+AchlU5
xjXkivhNp4aa6tQ9N+2cyjxHTkzP0RWsNVcvZfCcOGs3ZmQqOnk5Hz/g5lY8r+yknloA/H0a
EKeJnnJIny9hhV9mEkwdHG52OHlyaubBMJW9RzdEBuvHMf5tvA==
=u5r+
-----END PGP PUBLIC KEY BLOCK-----
```

then saving as ekiga.gpg in your home directory.  After that press ALT+F2 and in the run dialog that appears enter:

```
gksu gedit /etc/apt/sources.list
```

At the bottom of that file add these two lines:

```
deb http://ppa.launchpad.net/sevmek/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/sevmek/ppa/ubuntu intrepid main
```

Save and exit.  Open a terminal (Applications>Accessories>Terminal) and copy/paste this command in:

```
sudo apt-key add ./ekiga.gpg && sudo apt-get update && sudo apt-get dist-upgrade
```

This should update you to version 3.0.  I know that 3.2 is out now, but I couldn't find a PPA with it built yet.  The only other way that I know of is to compile from source with check install.

---

