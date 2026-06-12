---
title: "How do I install these &quot;tar.bz2&quot; files?!"
date: 2008-10-24
forum: General Help
---

### Post by 4l13n666 on 2008-10-24
Hello there!

This has been driving me insane since I installed Ubuntu for the first time. Installations!
Some programs I have absolutely no problems installing by using the "Synaptic Packet Manager", but when it comes to installing programs that I really NEED such as Java etc, I get stuck because they are "tar.bz2" files.

I have NO IDEA WHATSOEVER of how to install these packages. I have read several guides and posts about how to install these packages but I simply do not understand what the guide is asking me to do. I am a semi-newb when it comes to Ubuntu, but it has never taken me this much time to figure our how to do something with Ubuntu. And this is just installing software!

So if there is someone out there that can help me by providing and EXTREMELY simple and IDIOT PROOF guide of how to install these package types I would be very very happy!

Thanks!
Erik

---

### Post by EvilBro on 2008-10-24
> **4l13n666 said:**
> ... but when it comes to installing programs that I really NEED such as Java etc, I get stuck because they are "tar.bz2" files.
Java is in the repository as far as I can tell.

And tar.bz2 files are simply zipped archives. What are they supposed to contain? The source of a program that you want to compile and build yourself?

---

### Post by MusicMastaMike on 2008-10-24
Download the file to your Desktop.  Open a terminal (Applications>Accessories>Terminal) and type:
```

sudo apt-get install build-essential
cd Desktop
tar xjf your_file.tar.bz2
cd program_directory/
./configure
make
sudo make install

```
That should do the trick... Note that the first line of code just installs the packages you need to build a program from source. Hope that helps!

---

### Post by geirha on 2008-10-24
You'll find java in synaptic too. [sun-java6-jdk]("apt://sun-java6-jdk") for the development kit or [sun-java6-jre]("apt://sun-java6-jre") if you just need the runtime environment.

tar.bz2 and tar.gz files are usually source code that needs to be compiled and installed manually, and you should avoid such packages if you can. You generally unpack them and read the README file they contain for instructions on how to compile and install, but the installed package will not be registered in the packaging system, and they may be hard to uninstall. Finding a .deb of the program is much better.

---

### Post by jerome1232 on 2008-10-24
Far as I know java is in the repo's, if you 'sudo apt-get install ubuntu-restricted-extras' it should pull in all the goodie codecs, flash, and java you need.

tar.bz2 is actually a compressed tape archive so there's no way to know from that description basically there are three ways to install programs in Ubuntu.

**Debian packages** - you are already familiar with these that is what is in the repos many site's will offer up .deb's as well, once downloaded you just double click them. (opera, limewire are both good examples of programs that offer these types of installers) Really the preferred method of installation due to the ability to update itself via update manger. (if you have the repo for the program that is)

**Binary installers** - Similar to a .exe in windows, usually come as a standalone binary, extensions vary wildly but common ones are .bin, .sh, .run and such. You just make them executable (right click, properties, permissions, check executable) than double click them to install them. For a system wide install you will need to run it as root.

**Binaries **- Again similar to a .exe in  windows and will usualy come packaged in a compressed archive (like .tar.bz2) you simply extract the archive and run the program by double clicking on the executable, similar to zipped programs in windows.

**Source Code** - By far the hardest method of installation but allows customization of the program and such, usually comes in a compressed archive again (like .tar.bz2) and you extract the program and compile it. Generally an INSTALL file or README file located in the archive will give you the details to what must be done.

---

### Post by 4l13n666 on 2008-10-24
The code that you provided me with 

sudo apt-get install build-essential
cd Desktop
tar xjf gtk-gnutella-snapshot.tar.bz2
cd program_directory/
./configure
make
sudo make install

Is how it looked when I edited it. This was an epic failure because apparently nothing happened. (Except when I only put in the first line (sudo apt-get install build-essential), then something was updating or installing I have no clue. But after that I could not do anything further, because I don't know how the code should look. 

So basically what I did was the following:

1. I copy and pasted the the first line (sudo apt-get install build-essential) in the terminal which did "something", most likely updating something.
2. I wrote cd desktop in the terminal. Nothing happened.
3. So what I did next was to close the terminal and then I opened it again and tried again with writing cd desktop but the same result was reached.
4. Then I tried to insert the next like (tar xjf gtk-gnutella-snapshot.tar.bz2), which I don't even know if this is how the command line should look.
5. Then I gave up.

If it's not too much to ask, can someone finish the code for me or at least tell me exactly what to do. 
Finally, why aren't all files in the "debian format"? It would make everything much much MUCH easier!

---

### Post by jerome1232 on 2008-10-24
gtk-gnutella is in the repo's, unless you need a new version no reason to compile from source.
```

Package: gtk-gnutella
Priority: optional
Section: universe/net
Installed-Size: 24788
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Luca Bruno <lucab@debian.org>
Architecture: amd64
Version: 0.96.5-1build1
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgnutls26 (>= 2.4.0-0), libgtk2.0-0 (>= 2.14.1), libpango1.0-0 (>= 1.21.6), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4)
Filename: pool/universe/g/gtk-gnutella/gtk-gnutella_0.96.5-1build1_amd64.deb
Size: 13656282
MD5sum: 52a76f3799b4d41c531ff4e111ff5ea9
SHA1: b1e0c04d2ea5ee2101b8addcf0e202ad3f554a74
SHA256: 3ef0185f664ef90562bd502d49d44ec67210cb2f3ad99add6c5a30d1a1526b8c
Description: shares files in a peer to peer network
 Gtk-Gnutella is a reliable and efficient Gnutella client, supporting the
 latest Gnutella protocol, bandwidth limitation (both incoming and outgoing)
 traffic compression, and advanced search filters among other features.
 .
 Gnutella is a peer-based file-sharing protocol that allows a user
 running a Gnutella client to search for and download files from other
 Gnutella users, as well as share some files of his/her own.
 .
 Gtk-Gnutella offers all the extra features you expect from a modern client:
 persistent downloads, searches and filters, intuitive interface, upload
 statistics, queuing, and of course total control over many configuration
 parameters.
Homepage: http://gtk-gnutella.sf.net/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

The reason changing directories failed is Linux is case sensitive and the folder is Desktop, not desktop. Did you check out the INSTALL file and README file, it might need more dependencies to get it compiled.

---

