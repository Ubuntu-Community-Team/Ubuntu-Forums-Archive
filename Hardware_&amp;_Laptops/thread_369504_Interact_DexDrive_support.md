---
title: "Interact DexDrive support?"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by T3h_Dohtem on 2007-02-24
I found my old Playstation 1 DexDrive, which is a drive to use PS1 memory cards more or less like a normal drive on your computer. I was wondering if anyone has found any drivers for using it on Linux. Ive searched all the normal places, and found a program called Dexux, which had no documentation, and was said to be in the "Pre-Beta" stage by the developer, but has since been abandoned. Anyone had more luck than me with this?

---

### Post by T3h_Dohtem on 2007-02-26
I guess not? :(

---

### Post by Astinsan on 2008-02-03
Yes there is.. I haven't used it and it looks very alpha. Going to try it out and give you the nitty gritty give me a few..

[http://dexux.sourceforge.net/](http://dexux.sourceforge.net/) is the project page. I think that some of the psx emulation software has support for it too... Not sure though. I'll look into that too... Source Forge and Fresh Meat is a good place to look for stuff like this. Just bear in mind that it is a device that isn't sold anymore and will probably not see to much development. Interact is defunct.

---

### Post by Astinsan on 2008-02-04
Very little had to be done to make it work just compiled and it worked.  So put it on the list. Now the author knows it doesn't look pretty but it wouldn't be to hard to make a front end.

---

### Post by wolffangalchemist on 2008-05-09
can someone help me compile this?

---

### Post by Astinsan on 2008-05-12
goto : [http://sourceforge.net/projects/dexux/](http://sourceforge.net/projects/dexux/)


Download the newest file. 

put the file into your home directory.


goto applications menu then to accessories load the terminal
(aka applications>accessories>terminal)

once it is up type cd ~

untar the file with this command 

tar -zxvf thefilename.tar.gz

stuff should start scrolling up as its untaring.

The first part of the filename is usually the directory it unzipped the file into ... minus the .tar.gz. Go there

cd thefilename

type make

thats all there is to it.

---

