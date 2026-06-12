---
title: "Micro SD chip &quot;read only&quot;?"
date: 2014-12-18
forum: Hardware
---

### Post by PDA1 on 2014-12-18
I have a SanDisk Micro SD chip 32gb which is always "read-only". 

It can't be formatted or the partition deleted or any other process. 

So far permissions in root haven't changed the permission to read-write either.

Any ideas what to do?

---

### Post by yancek on 2014-12-18
What's on it?  Any data?  What filesystem type?  What are the current permissions?  Run the command from a terminal:  ls -l /media/user/disk

Changer 'user' above to your actual user name and change 'disk' to whatever the disk UUID shows as and post the results.

---

### Post by sudodus on 2014-12-18
It is a typical symptom of a failing pendrive or flash card.

Please copy (***backup***) all important files from the drive while it is still readable !!!

Then, if you wish try to wipe the drive (or at least the first megabyte) with mkusb.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Does it work? In that case, use gparted to create a partition table, and after that partitions and file systems.

Otherwise it is probably failing.

[This link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") describes how a flash drive works, and how it can fail, first getting read-only, then totally 'bricked'. [Read more about pendrives here]("https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites").

---

### Post by PDA1 on 2014-12-18
Here's the Terminal output-

$ ls -l /media/A811-0F0E/
total 32
drwx------ 2 c c 32768 Dec 18 07:48 LOST.DIR


I don't want to admit this but I bought one of those $30 RCA tablets are Walmart and it runs that @$@%^& Android "system".

The chip was to be used to have extra storage on the tablet but that wretched android system seized the chip and locked it.

Now that the chip has been removed from the tablet it's supposed to be used on my Ubuntu system....where it belongs.

Frankly, I hate google. I hate android. I won't and don't "google" anything.

---

### Post by sudodus on 2014-12-18
If the read-only feature is written into what normal mortal people can access, wiping should work. But if it is written into the low level control system of the flash card, you need some very special tool or knowledge to unlock it (and it is much cheaper to get a new flash card).

---

### Post by PDA1 on 2014-12-18
While the chip is in the tablet, files can be saved to the chip. But, if you try to edit the file (such as a spreadsheet file for example) the edits can't be saved back to the file. The original file remains intact.

The "mkusb" stuff looks too confusing to use.

---

### Post by sudodus on 2014-12-18
With 615 beans, I think you know more than enough to run mkusb ;-)

Install it via the ppa. It is not that difficult.

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

Many people have tried according to the wiki page, and I have improved what they have complained about. The same with the graphical user interface of mkusb. If you point to something confusing, I'll try to improve that too.

[https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

The work flow (zenity window sequence) is like this for wiping the first megabyte:

- menu: Starter menu (--> wipe)
- Warning and overview
- menu: Select device - and go ahead
- Final warning
- Work done

It is also described in the [pdf manual]("http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf")

---

### Post by PDA1 on 2014-12-18
Problems.....

$ sudo apt-get install mkusb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mkusb

---

### Post by sudodus on 2014-12-18
Which distro, flavour and version of linux are you running?

The following commands install mkusb in all the Ubuntu flavours and all current versions: 12.04 LTS, 14.04 LTS, 14.10 and 15.04 alpha plus re-spins and distros based on Ubuntu.

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

What is the output of the two previous commands? Those commands should work in order to make mkusb available via ppa.

-o-

It is not necessary, but if you want full functionality in standard Ubuntu, you should also install pv (which shows the progress, when mkusb writes to the target drive).

- Ubuntu 12.04 LTS

This link contains an extra instruction to get the repository **Universe**, where **pv** is stored [/install-to-ubuntu-12.04]("https://help.ubuntu.com/community/mkusb/install-to-ubuntu-12.04") 

- Ubuntu 14.04.1 LTS

This link contains a simpler instruction to get the repository **Universe**, where **pv** is stored [/install-to-ubuntu-14.04.1]("https://help.ubuntu.com/community/mkusb/install-to-ubuntu-14.04.1")

-o-

If you run other distros (not based on Ubuntu), you can install mkusb according to this link

[https://help.ubuntu.com/community/mkusb/v9#from_phillw.net](https://help.ubuntu.com/community/mkusb/v9#from_phillw.net)

---

