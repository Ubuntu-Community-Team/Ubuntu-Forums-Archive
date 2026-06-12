---
title: "Unable to reinstall apache2"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by mocka on 2009-11-10
I did something horribly wrong just now; I removed the /etc/apache2 directory while the package already was installed (I thought it wasn't). Now I'm unable to neither uninstall, install nor reinstall the package. What should I do?

By the way: I am using Ubuntu Server 9.04.

This also made my Transmission WebGUI stop working.

---

### Post by quixote on 2009-11-11
I *think* that directory will be recreated by fixing the package.  If so, this should reconfigure it: ```
sudo dpkg --configure apache2
```

If not, you may need to reinstall apache2, which is probably easiest to do via synaptic or apt-get ```
sudo apt-get --reinstall apache2
```

There's lots of detail on both commands, as I'm sure you know if you're running the server version :), by entering "man dpkg" or "man apt-get" (without quotes) as commands in a terminal.

---

### Post by mocka on 2009-11-13
I have tried to do as you say but the system think it as installed the package - although it hasn't (there is no apache2 directories created or whatsoever). Is my best bet to reinstall the whole system (I'd rather not)?

---

### Post by quixote on 2009-11-13
No, you shouldn't have to do a clean install just to get apache2 back.

Both apt-get and dpkg have "purge" options, which throws out every last bit of a package, including config files.  dpkg has various "force" options as well which you have to know what you're doing to use.  I don't, so I never have, but the command "man dpkg" describes it all.  Not in a way that made me confident enough to use it, but still, it's there.

Hopefully, somebody who actually knows how to do this will jump in.  My guess would be: ```
sudo apt-get purge apache2
```
And then reinstall via synaptic, or "sudo apt-get install apache2".

---

### Post by mocka on 2009-11-13
I agree, that sounds unreasonable. Although I have also tried "sudo apt-get --purge remove apache2" it hasn't helped at all. I'm tired of it all so I'll finish a script that installs all my packages and reinstall the whole ubuntu. Thank you for the help anyway.

EDIT: I made it.

For those interested or anyone who stumbles upon this thread with the same problem, this is how:

```

sudo apt-get remove --purge apache2.2-common
sudo apt-get clean
sudo apt-get install apache2

```

Thanks to the participants in this thread:
[http://ubuntuforums.org/showthread.php?t=471003](http://ubuntuforums.org/showthread.php?t=471003)

---

