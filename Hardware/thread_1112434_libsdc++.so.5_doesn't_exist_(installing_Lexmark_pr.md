---
title: "libsdc++.so.5 doesn't exist (installing Lexmark printer)"
date: 2009-03-31
forum: Hardware
---

### Post by TRiG_Ireland on 2009-03-31
I was trying to install a Lexmark X1190 printer. After a little searching, I settled on a simple tutorial I found at [http://wiki.trodrigues.net/Lexmarkx1290](http://wiki.trodrigues.net/Lexmarkx1290).

Everything went swimmingly till I got to this point:

```
trig@TRiG:~$ /usr/lib/cups/backend/z600
/usr/lib/cups/backend/z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

So, back to Google. At [http://www.joewein.de/sw/swnotes002.htm](http://www.joewein.de/sw/swnotes002.htm) is a suggested solution for this problem in Linux 7.

> Explanation: libstdc++.so.5 (the library for gcc 3.2.x) is installed in /usr/local/lib However, the system will only seach /usr/lib (where the 2.95.0 and other older libraries are stored).

Solution: Create symbolic links to make the libraries appear in the old folder:

ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
ln -s /usr/local/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1

Well. I can't see libstdc++.so.5 in either location. And nor does the Synaptic Package Manager list it. libstdc++5, yes. libstdc++.so.5, no.

Any suggestions?

TRiG.

---

### Post by patmalcolm91 on 2009-10-05
I'm having the exact same problem. The package libstdc++5 provides the library libstdc++.so.5. My difficulty is that even though I have it installed, i still get this message saying the file doesn't exist, and I've verified it's there by doing "ls /usr/lib | grep -i libstdc++". Still no luck.. I had this working in jaunty, but ever since I upgraded to karmic, it's been broken.

---

### Post by mrblue8 on 2009-12-15
guys, 

I got the same problem here in Kubuntu Karmic, I had libsdc++6 installed and I thought libsdc++5 was not necessary. As nothing else seemed to work, I entered this site: [http://packages.debian.org/etch/libstdc++5](http://packages.debian.org/etch/libstdc++5) and installed packages gcc-3.3-base and libsdc++5 and voilà! It now prints! 

I do not take credit for this, I just followed some other instructions in other forums, and, unfortunately, I don't remember exactly where I got these from... but thanks anyway, Ubuntu community, your tips are always very helpful!!

---

