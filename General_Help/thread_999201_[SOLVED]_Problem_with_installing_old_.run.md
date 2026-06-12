---
title: "[SOLVED] Problem with installing old .run"
date: 2008-12-01
forum: General Help
---

### Post by ubuntoooooo on 2008-12-01
I'm trying to install an older .run file.
I found a good site that helped, sorta [="http://www.g-loaded.eu/2007/02/25/error-when-using-old-runbin-installers-under-linux/"](="http://www.g-loaded.eu/2007/02/25/error-when-using-old-runbin-installers-under-linux/") 
I say sorta because it seems to only run without errors when I use:
```
sh path/to/file.run
```
But without the root permission I can't install it, so anyways with root it gives me this error:
```
will@will-desktop:~/Desktop$ sudo sh wolfmp-linux-1.1*
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 2860345088 2466252757
```
This is after I enter the "export _POSIX2_VERSION=199209" cmd.

I'm stumped.

---

### Post by ubuntoooooo on 2008-12-01
No ideas?

```
will@will-desktop:~/Desktop$ sh wolfmp-linux-1.0.b2.x86.run 
Verifying archive integrity...OK
Uncompressing Wolfenstein Multiplayer..........................................................................................................................................................................................................
Warning: No writable targets in path... [COLOR="red"]You may want to be root[/COLOR].

```

the code for a successful run, but, without the sudo in front.

---

### Post by taurus on 2008-12-01
How about 

```
chmod 755 wolfmp-linux-1.0.b2.x86.run
sudo ./wolfmp-linux-1.0.b2.x86.run
```

---

### Post by ubuntoooooo on 2008-12-02
I solved it, I used the cmd in the first linked site as well as 
```
sudo su
```
I can't remember exactly right now, but I think that did the trick.

Might've been...
```
sudo sh wolfmp-linux-1.1* tail -n +6
```

I feel bad that I can't even remember 4 hours back in time.

---

