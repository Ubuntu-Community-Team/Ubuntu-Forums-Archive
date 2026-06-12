---
title: "checking root file system error"
date: 2006-05-07
forum: Hardware &amp; Laptops
---

### Post by wegen on 2006-05-07
I have Ubuntu running on my smaller computer PII, 350 Mhz.
It works fine, but once in a while this message comes up during startup.
"checking root file system error" and it says that it is someting to do with 
some bad line 2 in etc/fstab. How can i access and check this line?
This happens every third month or so....i do nothing special that can make this happen. I can reinstall the whole Ubuntu, but it take a while. I just wonder if someone can give me some tips so i won´t have to re-install the whole sysytem.

---

### Post by ranf on 2006-05-07
You can open the file with any editor you like.
Or simply run `less' (this only shows it without a possibility to edit it)
```
less -N /etc/fstab
```

The -N parameter puts line numbers in front.

---

### Post by wegen on 2006-05-10
Ok, the thing is that Uduntu wont start up at all...it just stops at the beginning after this message shows.
what exactly is the root file system? It can mount it, but hangs when it 
checking root file system. 
I tried to start with a diffrent kernel in the menu at the startup, but same thing appears...
My Ubuntu is dead...=(
So i guess i must reinstall all over again and for some weeks it will be the same thing all over again...happens three times til now....
Maybe will try some other distro...

---

### Post by kranz on 2006-05-12
Before leaving Ubuntu try this:
 [http://www.ubuntuforums.org/showthread.php?t=128910&highlight=%22Checking+root+file+system%22]("http://www.ubuntuforums.org/showthread.php?t=128910&highlight=%22Checking+root+file+system%22")

And then You could look at this:
[http://www.ubuntuforums.org/showthread.php?t=163500&highlight=%22Checking+root+file+system%22](http://www.ubuntuforums.org/showthread.php?t=163500&highlight=%22Checking+root+file+system%22)

---

