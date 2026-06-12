---
title: "dpkg problems"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by stebbo42 on 2009-05-09
I was just wondering if anyone has had some experience with this error?

I ran the update manager this evening on a fresh install of 8.10, and it appeared to hang for a fair while when restarting, so i hit the reset button. I'm going to assume it's pretty bad. But any help would be much appreciated.

The update manager now says that there's 301 new updates, and when i tell it to install all updates, it gets this error:

dpkg: parse error, in file '/var/lib/dpkg/available' near line 1:
 field name '
dpkg: parse error, in file '/var/lib/dpkg/available' near line 1:
 field name '
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

---

### Post by sisco311 on 2009-05-09
Open a terminal and run:
(Applications -> Accessories -> Terminal)

```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available

sudo apt-get update
```

---

### Post by stebbo42 on 2009-05-09
Thanks for the help, I just went to install Gmount-iso, and when i clicked apply changes, it came up with almost exactly the same error, being:

dpkg: parse error, in file '/var/lib/dpkg/available' near line 1:
 field name '

Any help would be great.

---

### Post by drs305 on 2009-05-09
Here is a different way to solve the 'available' file problem:
```

sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.bad
sudo touch /var/lib/dpkg/available

```
The above will create a new, empty "available" file. This may solve the problem. 

If you want, you can 'rebuild' the available file, which is now empty:
```

sudo apt-get install dselect
sudo dselect update

```

---

### Post by sisco311 on 2009-05-09
[s]try[/s]:
```
sudo dpkg --clear-avail

sudo apt-get update
```

EDIT: never mind.

---

### Post by stebbo42 on 2009-05-09
Thanks heaps. That appears to have cleared it all up.

---

### Post by drs305 on 2009-05-09
> **sisco311 said:**
> 
sudo dpkg --clear-avail
EDIT: never mind.

Actually though, that's a lot simpler way to empty 'available'.  

The update command doesn't appear to repopulate the file the way dselect does.

---

