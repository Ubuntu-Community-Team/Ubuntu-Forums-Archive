---
title: "Kernel will not update, stuck at 2.6.27-12-generic"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by smoosh on 2009-03-02
I have a Sony Vaio VGN-FW139e with ATI graphics and Atheros wireless (in case that matters).  The only thing I can think of is these DSDT patches I have installed to fix the brightness adjust (it's a laptop) - [http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/](http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/)

Other than that ????  What gives?  It has been updating normally, no indications that anything was missing...

Anybody know how to get it back updating or how to install the latest kernel?

Thanks in advance!

---

### Post by taurus on 2009-03-02
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by smoosh on 2009-03-02
the update returned this:

W: Failed to fetch [http://ubuntu.org.ua/getdeb/Release.gpg](http://ubuntu.org.ua/getdeb/Release.gpg)  Could not connect to ubuntu.org.ua:80 (91.193.124.193), connection timed out

W: Failed to fetch [http://ubuntu.org.ua/getdeb/en_US.bz2](http://ubuntu.org.ua/getdeb/en_US.bz2)  Unable to connect to ubuntu.org.ua http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by taurus on 2009-03-02
Either that site, [http://ubuntu.org.ua](http://ubuntu.org.ua), is down or dead.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of [http://ubuntu.org.ua](http://ubuntu.org.ua) repos to comment them out for now.  Save it and run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by smoosh on 2009-03-02
No errors this time (except one about my Wine repository being a duplicate), but no update either!

---

### Post by taurus on 2009-03-02
Are you sure there is a new kernel?

---

### Post by smoosh on 2009-03-02
Yeah, apparently the newest is 2.6.28-7...

[http://www.kernel.org/](http://www.kernel.org/)

I only found this out because I was asking about a suspend problem in 2.6.27.12 and was informed that my kernel was way out of date.

---

### Post by whoop on 2009-03-02
Maybe you have the new kernel but it is just not showing in your grub menu? Maybe grub is not updating it's list.
check /boot and see if the kernel you are missing is there. If it is it's just a grub problem.

---

### Post by smoosh on 2009-03-02
Not there.  Should I get out the hammer?

---

### Post by taurus on 2009-03-02
> **smoosh said:**
> Yeah, apparently the newest is 2.6.28-7...

[http://www.kernel.org/](http://www.kernel.org/)

I only found this out because I was asking about a suspend problem in 2.6.27.12 and was informed that my kernel was way out of date.

So there is a new kernel but it has not hit the Ubuntu repos.  You can either wait for it to get into the repos or build it yourself if you can't wait.

---

### Post by smoosh on 2009-03-02
Oooooooooooh, sorry (head smack), the person who responded to my suspend problem post simply said "the latest stable version is 2.6.28.7", insinuating that since my kernel was behind, the suspend issue was moot.  he he.  Is there somewhere I can check what the current kernel is just to make sure?  Thanks for the help in figuring out that I don't know my *** from my elbow...

---

### Post by taurus on 2009-03-02
If you keep your system up-today, then you are running the latest kernel.
Again, that might not be the newest one so if you need the newest one, build it yourself unless you want to wait for it to hit the repos and who knows how long that would take or it might not, only in the new release.

```
uname -a
```

---

