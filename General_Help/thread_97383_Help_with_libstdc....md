---
title: "Help with libstdc..."
date: 2005-11-30
forum: General Help
---

### Post by sgbzona on 2005-11-30
Hi, I have a problem with VRMLVIEW ([http://www.sim.no]("http://www.sim.no")) This software uses libstdc++-libc6.1-1.so.2 , I made the following:

```
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++-libc6.1-1.so.2

```
but when executes it, shows the following message:

```
sgb@zona-2:~$ vrmlview &
[1] 21783
sgb@zona-2:~$ vrmlview: symbol lookup error: vrmlview: undefined symbol: __builtin_new

[1]+  Exit 127                vrmlview
sgb@zona-2:~$
```

What can i do? :( 

:confused:  I hope someone can help me...

---

### Post by ccolon on 2008-04-10
This reply is 3yrs too late, but maybe it will help others.

The SIM VRML View is available here:-

[http://www.km.kongsberg.com/ks/web/nokbg0237.nsf/AllWeb/E1DB099B3F91AC26C12572DB004D4EE1?OpenDocument](http://www.km.kongsberg.com/ks/web/nokbg0237.nsf/AllWeb/E1DB099B3F91AC26C12572DB004D4EE1?OpenDocument)

It appears to be closed source, but is actually a good VRML viewer, unlike the various other viewers on Linux.

You can fix the problem mentioned above by doing the following:-

```
sudo aptitude install libstdc++2.10-glibc2.2
```

Then:-

```
sudo ln -s /usr/lib/libstdc++-libc6.2-2.so.3  /usr/lib/libstdc++-libc6.1-1.so.2
```

Then you can extract the binary from the downloaded .tat file and run:-

```
./vrmlview
```

Without getting the error message mentioned in the previous post.

At least this worked on Ubuntu Gutsy Gibbon.

---

