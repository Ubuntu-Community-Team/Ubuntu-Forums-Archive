---
title: "Non-Windows Partition Mounting"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by swalsh on 2005-04-28
I uninstalled a whole bunch of stuff from my Windows partition so I could move my stuff over to the Linux ext 3 partition. Then in windows I created another ext3 partition.  Any easy way to merge it with the existing ext 3 partition?

Thanks

---

### Post by nad on 2005-04-28
It seems that you wish to make your existing partition larger. As you can not resize a mounted filesystem you will need to do this from another os. The live cd is a good choice.

There is also no problem with leaving this as a separate partition and it actually has advantages. Once configured, you will not even notice that it is a separate partition.

Use synaptic to get the qtparted partition editor package to familiarize yourself with the operations involved.

---

### Post by swalsh on 2005-04-28
Where exactly would one find qtparted?  I looked in Synaptic but was unable to find it.  I also tried this, but with no luck:
```
stephen@swalsh:~$ sudo apt-get install gparted
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gparted
```

Anyone know what's up?

Edit: I found it.  It wasn't labeled qtparted, only parted.

Thanks, Dan.

---

### Post by jodef on 2005-04-28
Parted is the program itself qtparted is the frontend if you are not familiar with this program I suggest you download the latter and BE VERY VERY CAREFUL!

---

### Post by nad on 2005-04-28
You may need to enable Universe to find the qtparted or gparted packages in synaptic. I suggested a gui tool as they give you visual feedback to your requests and some people find them easier to use.

My favorite command line tool is cfdisk. You have also found parted. fdisk and sfdisk are also included in warty (im at a warty install at the moment). Do take the previous posters' warning to heart. Read the manuals, instructions and proceed cautiously. Always back up any important data.

---

### Post by swalsh on 2005-04-29
I'm still entirely new to Linux.  I program in other languages, but just now realized the genius behind this OS.  How to I get to all of this stuff you guys are talking about?  How do I enable universe?  I've managed to get two things working on my own after reading FAQs, but I am still very new to the process of unpacking stuff and installing it.  I'm used to .exe where you are babied through everything.  Thanks for all the help!

---

### Post by nad on 2005-04-29
You shouldn't have to unpack and hand install anything. That is the genius of debians' package management. Use synaptic (Universe is enabled through the repositories list). Learn how to use your new tools (additional repositories are easily added, configure away). There are some 9000 packages available from little shell utilities and tiny window managers  to math and bio-engineering apps not to mention half a dozen full blown office suites and programming ide's.

Once you have a little experience under your belt, you will realize that there are literally hundreds of files that are used to configure a GNU/Linux system. Some have gui front ends, all can be hand modified to make your computer work the way that you wish.

---

### Post by swalsh on 2005-04-29
So i figured out how to install the new respitories from the Unofficial User's Guide.  All went well and I used (sudo apt-get install superkaramba).  Now where did it go?  Is there a default folder that everything goes to when you use this (sudo apt-get install somefile) command?

Thanks

---

### Post by nad on 2005-04-29
One of the features of using packages fully supported by the ubuntu team is that they will (usually) add a launch item to your menus. Sometimes logging out and back in will correctly rebuild your menus. Other apps may need to be started at Applications -> Run Application (you may recognize the process from that other operating system). If the install completed without errors, the binary and necessary libraries should have been installed correctly. If not, it is a bug that needs to be reported.

Edit: Where did your previous question go?

---

