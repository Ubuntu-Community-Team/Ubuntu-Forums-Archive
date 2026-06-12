---
title: "Synaptic borked - can't remove kstars"
date: 2008-08-28
forum: General Help
---

### Post by ronnielsen1 on 2008-08-28
After an interrupted installation, Synaptic wants to remove kstars-data but ends up with the error
> E: kstars-data: unable to delete control info file `/var/lib/dpkg/info/kstars-data.md5sums'

I looked in /var/lib/dpkg/info and there is no file so I tried to make one as root. It wouldn't let me. Anyone know how to fix synaptic?[COLOR="Red"][/COLOR][COLOR="Red"][COLOR="Red"][COLOR="Red"][/COLOR][/COLOR][/COLOR]

---

### Post by drs305 on 2008-08-28
Try running this to see if it resets things:
```

sudo cp /var/lib/dpkg/status $HOME/Desktop/status.bak
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

```

If that doesn't work, reset to the way things were:
```

sudo cp $HOME/Desktop/status.bak /var/lib/dpkg/status 

```

---

### Post by phidia on 2008-08-28
The debian apt-get [guide]("http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html") maybe helpful-remember you will need to preface those commands with "sudo".

---

### Post by ronnielsen1 on 2008-08-28
Worked like a charm! This is my first attempt at Ubuntu since Ubuntu 5. I like it. There's alot of difference now. It seemed too buggy before and I went to KDE. I think it's going to stay on my box now.

---

### Post by ronnielsen1 on 2008-08-28
Spoke too soon. I tried to install in synaptic and same thing.

---

### Post by drs305 on 2008-08-28
Here are a few more possible remedies:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update

```

or:
```
sudo dpkg --force-all --purge kstars

```

or:
```

sudo rm /var/lib/dpkg/info/kstars*

```

or finally, remove the sections on kstars and kstars-data:
```

gksu /var/lib/dpkg/status

```

Please let us know which, if any, are successful and mark the thread solved if you are able to clear this up. 

If you are still having the problem let us know what error messages you are still getting.

---

### Post by markbuntu on 2008-08-28
If synaptic is stuck trying to remove kstars stilln you can try a force downgrade and then try to remove it. 

That was the only thing that worked for me once when synaptic got stuck trying to remove a package that it was unable to due to some bogus link it was unable to get over. It completely borked Synaptic and apt. I could get nothing until I force downgraded the package.

---

### Post by ronnielsen1 on 2008-08-29
Appreciate everybody's help. It was a new enough install I just reinstalled. I tried all the command line fixes and none worked. I'll be a little more careful about selecting repositories this time. I think I upgraded with one enabled I shouldn't have.

---

