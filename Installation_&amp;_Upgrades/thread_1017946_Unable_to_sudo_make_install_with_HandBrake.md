---
title: "Unable to sudo make install with HandBrake"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by rpete on 2008-12-21
Hi, I am having trouble installing HandBrake. I have the latest version of yasm, and subversion.  I have gotten messages in previous failures that two files failed libfaac and libfaad. These are both in the repository and I didn't get it this time. Below is the end of the output from the "make" command and after I tried "sudo make install".  Any ideas. What does "No rule to make target 'install'" mean?   

HandBrake/doc/BUILDSHARED
HandBrake/doc/COPYING
HandBrake/doc/CREDITS
HandBrake/doc/THANKS
HandBrake/doc/AUTHORS
HandBrake/doc/NEWS
HandBrake/doc/TRANSLATIONS
HandBrake/doc/BUILD
richard@dell-desktop:~/HandBrake$ sudo make install
make: *** No rule to make target `install'.  Stop.
richard@dell-desktop:~/HandBrake$

---

### Post by mc4man on 2008-12-21
What are you running the make install on?

Without trying not 100% but I believe handbrake and  hblib are done at 'make'
Then you would build the gkt gui and that would be installed with a 'sudo make install'

Edit: built a couple of times, seems to be a couple of ways, either with 'make' or './configure && jam'

when that's done
```
cd gtk && ./autogen.sh
```

At this point 'make 'installs to /usr/local, to change to /usr then,
```
./configure --prefix=/usr && make
```


And then either 
sudo make install, or (red to just make the .deb

```
sudo checkinstall --fstrans=no [COLOR="Red"]--install=no[/COLOR]
```

Make sure you give it a new version number in checkinstall (name, comments, ect. if wanted

---

