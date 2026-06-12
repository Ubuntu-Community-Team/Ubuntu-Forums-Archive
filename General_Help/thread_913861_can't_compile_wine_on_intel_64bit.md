---
title: "can't compile wine on intel 64bit"
date: 2008-09-08
forum: General Help
---

### Post by gnarlin on 2008-09-08
Hello. 
I hope there is someone here that can help me with this problem.
I guess I have to tell the whole story for it to make sense.

Originally I wanted to host a warcraft3 game on my lan. However I found out that there is a bug in wine that makes warcraft3 incapable of hosting games.
Thankfully I found this: [http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

I ran apt-get build-dep wine without problems. However, every time I run ./configure in the wine folder it complains with this message:

checking for freetype-config... freetype-config
checking for -lfreetype... not found
configure: error: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.
Use the --without-freetype option if you really want this.

The thing is, I already installed libfreetype6-dev. Besides, shouldn't build-dep have taken care of this problem already?
I even got so desperate that I did this:

for i in $(apt-cache search freetype|grep "\-dev"|cut -f1 -d\ );do sudo apt-get install $i;done

I hope that someone can help me with this infuriating problem.

---

### Post by regala on 2008-09-08
> **gnarlin said:**
> Hello. 
I hope there is someone here that can help me with this problem.
I guess I have to tell the whole story for it to make sense.

Originally I wanted to host a warcraft3 game on my lan. However I found out that there is a bug in wine that makes warcraft3 incapable of hosting games.
Thankfully I found this: [http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

I ran apt-get build-dep wine without problems. However, every time I run ./configure in the wine folder it complains with this message:

checking for freetype-config... freetype-config
checking for -lfreetype... not found
configure: error: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.
Use the --without-freetype option if you really want this.

The thing is, I already installed libfreetype6-dev. Besides, shouldn't build-dep have taken care of this problem already?
I even got so desperate that I did this:

for i in $(apt-cache search freetype|grep "\-dev"|cut -f1 -d\ );do sudo apt-get install $i;done

I hope that someone can help me with this infuriating problem.

Could you give us the output of "ldd /usr/lib/libfreetype.so*" ?

rgds

---

### Post by gnarlin on 2008-09-08
Thanks for helping me.
Here is the output:

/usr/lib/libfreetype.so:
	linux-gate.so.1 =>  (0xb7f41000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7ea6000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d57000)
	/lib/ld-linux.so.2 (0xb7f42000)
/usr/lib/libfreetype.so.6:
	linux-gate.so.1 =>  (0xb7fd3000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7f38000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7de9000)
	/lib/ld-linux.so.2 (0xb7fd4000)
/usr/lib/libfreetype.so.6.3.16:
	linux-gate.so.1 =>  (0xb7f09000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7e6e000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d1f000)
	/lib/ld-linux.so.2 (0xb7f0a000)

---

### Post by regala on 2008-09-08
> **gnarlin said:**
> Thanks for helping me.
Here is the output:

/usr/lib/libfreetype.so:
	linux-gate.so.1 =>  (0xb7f41000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7ea6000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d57000)
	/lib/ld-linux.so.2 (0xb7f42000)
/usr/lib/libfreetype.so.6:
	linux-gate.so.1 =>  (0xb7fd3000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7f38000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7de9000)
	/lib/ld-linux.so.2 (0xb7fd4000)
/usr/lib/libfreetype.so.6.3.16:
	linux-gate.so.1 =>  (0xb7f09000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7e6e000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d1f000)
	/lib/ld-linux.so.2 (0xb7f0a000)

ahem, weird, seems there is really no problem at all with freetype.
could you give us the output from:
dpkg -l "*freetype*" ?

---

### Post by gnarlin on 2008-09-08
Woops. I think I may have run ldd on my local laptop at work and not my ssh session for home. Here it is again:

/usr/lib/libfreetype.so:
        linux-vdso.so.1 =>  (0x00007fffabffe000)
        libz.so.1 => /usr/lib/libz.so.1 (0x00007fbba3a72000)
        libc.so.6 => /lib/libc.so.6 (0x00007fbba3710000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fbba3f21000)
/usr/lib/libfreetype.so.6:
        linux-vdso.so.1 =>  (0x00007fffc33fe000)
        libz.so.1 => /usr/lib/libz.so.1 (0x00007fd7bae60000)
        libc.so.6 => /lib/libc.so.6 (0x00007fd7baafe000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fd7bb30f000)
/usr/lib/libfreetype.so.6.3.16:
        linux-vdso.so.1 =>  (0x00007fff0d9fe000)
        libz.so.1 => /usr/lib/libz.so.1 (0x00007ff1053f8000)
        libc.so.6 => /lib/libc.so.6 (0x00007ff105096000)
        /lib64/ld-linux-x86-64.so.2 (0x00007ff1058a7000)

Here is the dpkg -l output:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  freetype       <none>         (no description available)
un  freetype0      <none>         (no description available)
un  freetype0-dev  <none>         (no description available)
un  freetype1      <none>         (no description available)
un  freetype1-dev  <none>         (no description available)
un  freetype1-tool <none>         (no description available)
ii  libfreetype6   2.3.5-1ubuntu4 FreeType 2 font engine, shared library files
ii  libfreetype6-d 2.3.5-1ubuntu4 FreeType 2 font engine, development files

NOTE: I'm running the 64bit version of ubuntu.

---

### Post by tluck on 2008-10-27
You need the 32-bit library symlinks and ./configure command posted here:

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

### Post by weirddan455 on 2008-12-08
I'm having the same problem... had to configure with --without-freetype.  Looked all over the Internet and seems other people are having this problem too.  Doesn't make any sense.  I followed the wiki exactly and freetype is defiantly installed.

---

