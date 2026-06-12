---
title: "mounting external hard drive"
date: 2009-06-25
forum: Hardware
---

### Post by mystmaiden on 2009-06-25
This is a repost because I had originally posted it under my (dead thread) choosing an external hard drive.  I'm really confused on files systems, so I could use some help mounting my new external.

When I try to use it out of the box I get this:
(I ordered a simpletech 1TB external and it came yesterday but now I have a problem. It is set up for NTFS. it gives an option for using with MAC but I'm really not sure what I'm doing here. )

When I plugged it in I got this error: 

Unable to mount volume failed to mount '/dev/sdb1' operation not supported because NTFS is marked to be in use. Choose 1 option: If you have Windows then disconnect the external devices by clicking on safely remove hardware icon in the windows taskbar, then shut down windows cleanly. 

Choice 2:If you don't have Windows you can use the 'force' option for you own responsibility. For example type on the command line mount -t ntfs-3g/dev/sdb1/media/FV-U35 -0 force Or add the option to the relevant row in the /etc/fstab file 
/dev/sdb1/media/FV-U35 ntfs-3g force 0 0

My question is - am I going to be able to use this drive with linux? Is there something I can do to make it work. I'm running ubuntu 8.10 LTS which I installed in the default manner, with no changes. I have been on hold on simpletechs tech support for two hours now.  When I finally got the tech he said it could be set up for fat32, but would not help me do so because I'm using linux not mac or windows.


Thanks!!

---

### Post by aquavitae on 2009-06-25
sounds like it wasn't unmounted properly in windows. Try installing ntfs-utils (I think - just look in synaptic for something like that). Then, in a terminal run ```
sudo ntfsfix /dev/sdb1
```. You should be able to mount it normally after that.

---

### Post by mystmaiden on 2009-06-25
thanks! Its brand new and never been run in windows but I'll try that anyway

myst

edited to add: I searched  for ntfs-utils and it didn't come up in synaptic or add/remove but does show a few things when I search for just ntfs 

already installed are libntfs-3g23 and ntfs-3g

---

### Post by aquavitae on 2009-06-25
Just did a search - the one you want is called ntfsprogs.

---

### Post by mystmaiden on 2009-07-04
Success, I'm able now to mount the drive - thousand thanks folks! It has a backup program on it called Fabrik, but I haven't tried launching it because linux isn't supported at all and I don't know if the program would work at all. Any insight there would be great.


myst 

edited to add: I read somewhere in the wee hours on the forums here that ntfs might result in some data loss, anyone have experience with that? That worried me a little.

---

