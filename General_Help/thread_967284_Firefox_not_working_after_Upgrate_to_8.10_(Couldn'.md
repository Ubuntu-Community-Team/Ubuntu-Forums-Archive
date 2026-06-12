---
title: "Firefox not working after Upgrate to 8.10 (Couldn't load XPCOM.)"
date: 2008-11-01
forum: General Help
---

### Post by AlchemyMan on 2008-11-01
The title essentially explains it all. At first, everything seemed to work fine post upgrade (which struck me as very unusual, as I have already gone through about three of em). Of course, my suspicions were correct. When I try to start up Firefox, it simply won't start. When I tried in terminal, I am told simply that it "Couldn't load XPCOM." 

I tried completely removing Firefox and Firefox branding and then reinstalling them again, but that ain't working.

Am using SeaMonkey for the time being, which is is alright, but not ideal. Would love to have my Firefox back, what with the extensions and all. 

Please, any help in getting me back on track would be greatly appreciated. Thank you very much in advance.

---

### Post by AlchemyMan on 2008-11-02
Does anyone have any ideas at all?

---

### Post by nadamsieee on 2008-11-05
[http://ubuntuforums.org/showthread.php?t=951615](http://ubuntuforums.org/showthread.php?t=951615)

---

### Post by skoal on 2009-02-12
I had to fix my XPCOM problem a tad bit different. Something went foo foo.

Problem?  Whenever I would do anything with 
apt-get ? foobar
dpkg --configure -a

I would get...
> rocessing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libartsflow.so.1 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libvorbisfile.so.3 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libarchive.so.2 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libapm.so.1.0.0 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libarchive.so.1 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libkabc_dir.so.1 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libart_lgpl_2.so.2.3.20 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libartsflow.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libgmcop.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libsnmp.so.15 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libartsgslplayobject.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libvorbisfile.so.3 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libartsflow_idl.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libkabc_dir.so.1 is not a symbolic link

So, I had to start with

dpkg-query -S libartsflow.so.1
libarts1c2a: /usr/lib/libartsflow.so.1.0.0
libarts1c2a: /usr/lib/libartsflow.so.1

Then,

sudo apt-get install --reinstall libarts1c2a

To correct this package that when kaplooey somehow. Then, I repeated with each successive one in the list

libvorbisfile.so.3 to libkabc_dir.so.1

...until dpgk --configure -a succeeded, and it fixed all my firefox loading problems.

XPCOM then stopped puking all over my screen.

Hope that helps.

\\//_

---

