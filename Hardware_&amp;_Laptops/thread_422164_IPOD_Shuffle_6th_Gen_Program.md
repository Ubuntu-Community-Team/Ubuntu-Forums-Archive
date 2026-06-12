---
title: "IPOD Shuffle 6th Gen Program?"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by xflatlinex on 2007-04-24
Has anyone had any success with transferring music to a 1GB IPOD shuffle, (the small square one)  or any programs that will easily do this. I have tried Banshee and Songbird and have had zero success. Any program suggestions would be appreciated

---

### Post by pay on 2007-04-24
I think that you need to compile and install libmtp (microsoft transfer protocol) and then compile the player with support for mtp. Thats what I have to do with my Creative Zen Vision M.

---

### Post by xflatlinex on 2007-04-24
> **pay said:**
> I think that you need to compile and install libmtp (microsoft transfer protocol) and then compile the player with support for mtp. Thats what I have to do with my Creative Zen Vision M.

Do you know where I can find a guide for that?

---

### Post by pay on 2007-04-24
sudo aptitude install cvs



Alternatively you can check the source out via annonomous CVS login.[LIST]
[*]cvs -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp login
[*]*no password*
[*]cvs -z3 -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp co -P libmtp[/LIST]To build from CVS run the following commands in the libmtp directory[LIST]
[*]./autogen.sh
[*]./configure
[*]make
[*]sudo make install # or use checkinstall to create a deb[/LIST]Give me a second and I'll see how to compile banshee, and if it even supports libmtp

---

### Post by xflatlinex on 2007-04-24
I have Banshee and I cannot get it work with my IPOD.

---

### Post by pay on 2007-04-24
After compiling mtp (and probably njb) compile banshee like this```
wget http://banshee-project.org/files/banshee/banshee-0.12.1.tar.gz
tar zxvf banshee-0.12.1.tar.gz
cd banshee-0.12.1 
./configure --help
./configure --enable-ipod --enable-njb --enable-mtp --prefix=/usr/local
make
sudo make install # checkinstall for a deb
```and then banshee should have support for ipods

---

### Post by xflatlinex on 2007-04-24
Cool, thanks, I will try that. I had it installed but just never added support for IPOD

---

### Post by pay on 2007-04-24
I just noticed that my instructions for libmtp are showing up as smilies. [Here's](http://libmtp.sourceforge.net/index.php?page=download) the link for how to do it. Also njb isn't needed like I said before.

---

### Post by rubbsdecvik on 2007-04-27
I have a 6th gen 1Gb shuffle.  I got it to work with [Songbird]("http://www.songbirdnest.com"), but not on anything else.  :(  But I am starting to like songbird so that isn't all that bad.

---

