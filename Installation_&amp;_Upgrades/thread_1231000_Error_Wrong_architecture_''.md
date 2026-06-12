---
title: "Error: Wrong architecture ''"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by jadhav333 on 2009-08-04
I am attempting to install the following application.. **djv 0.8.2 x86** (downloaded from the following url: **[http://djv.sourceforge.net/download.html#0.8.2](http://djv.sourceforge.net/download.html#0.8.2)**)

I get the following error message.. **Error: Wrong architecture ''**
my system architecture is 'i686' as checked with command **uname --m**

So what is the issue?
what should be the suffix of the application which is compatible with i686?

---

### Post by Sef on 2009-08-04
Maybe you downloaded the 64-bit version by mistake or a version for a different os.

---

### Post by jadhav333 on 2009-08-04
The file downloaded was for linux, 32bit, filename: djv-0.8.2_linux-x86.deb

---

### Post by kelvin spratt on 2009-08-04
Just to clarify I just downloaded both 32 and 64bit debs and they both say "wrong architecture" so i don't think you did anything wrong.

---

### Post by jadhav333 on 2009-08-04
> **kelvin spratt said:**
> Just to clarify I just downloaded both 32 and 64bit debs and they both say "wrong architecture" so i don't think you did anything wrong.

u bet.. i tried that too :)

---

### Post by realzippy on 2009-08-04
sudo dpkg -i --force-architecture djv-0.8.2_linux-x86.deb

..the hard way?

---

### Post by jadhav333 on 2009-08-04
> **realzippy said:**
> sudo dpkg -i --force-architecture djv-0.8.2_linux-x86.deb

..the hard way?

What will this command do? Is it safe to do so (i.e. force architecture)?

Will it pick up the deb file that I have downloaded (which seems very unlikely)? Or Do I have to provided a <path>/djv-0.8.2_linux-x86.deb at the end of the command?

---

### Post by nmaster on 2009-08-04
> **jadhav333 said:**
> What will this command do? Is it safe to do so (i.e. force architecture)?

Will it pick up the deb file that I have downloaded (which seems very unlikely)? Or Do I have to provided a <path>/djv-0.8.2_linux-x86.deb at the end of the command?

i usually use --force-architecture to install a 32-bit deb on a 64-bit OS.  i've never had a problem with it.

you need to provide the path unless you are in the same directory as the deb.

---

### Post by realzippy on 2009-08-05
> **jadhav333 said:**
> 
Will it pick up the deb file that I have downloaded (which seems very unlikely)? Or Do I have to provided a <path>/djv-0.8.2_linux-x86.deb at the end of the command?

Assuming your .deb is on your Desktop,open terminal,type:

**cd Desktop**

then type:

**sudo dpkg -i --force-architecture djv-0.8.2_linux-x86.deb**

---

