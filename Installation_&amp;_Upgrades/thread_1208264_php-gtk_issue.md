---
title: "php-gtk issue"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by esafwan on 2009-07-09
Hi,
I'm trying to download php-gtk on my Ubuntu (jaunty). But i have some troubles.

I downloaded the latest source from php-gtk.net 
([http://gtk.php.net/distributions/php-gtk-2.0.1.tar.gz](http://gtk.php.net/distributions/php-gtk-2.0.1.tar.gz))

Extracted it... then typed used this command.. 
```
./buildconf

```
but i'm getting some error
```
checking for PHP executable in /usr/bin... configure: error: Could not locate PHP executable
```

I have installed php5 and php5-dev from the repository with all the dependencies.

What might be causing the problem?

---

### Post by Partyboi2 on 2009-07-09
Hi, check that you have the php5-cli package installed, if not install it.
```
sudo apt-get install php5-cli
```

---

