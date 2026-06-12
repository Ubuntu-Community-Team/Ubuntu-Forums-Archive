---
title: "Accessing my Hard drive"
date: 2014-12-17
forum: Hardware
---

### Post by james_r2 on 2014-12-17
Hi there,

I hope this is the right place to post this,

I'm having some issues. Just recently put together a new PC but used the HDD and RAM from previously computer as they were working and compatible.

I wanted to find a way of backing up my hard drive without formatting it when installing windows so someone told me to instal ubuntu and create partitions so that I dont wipe data.

I created a 10gb partition on a 2tb hard drive and successfully installed ubuntu but now that i'm in all I can see is that 10gb, I cant find my hard drive and the data. I need to back up this hard drive befgore installing a operating systemand wiping it, can anyone help me?

James

---

### Post by Bashing-om on 2014-12-17
James_r2: Hi !

> **james_r2 said:**
> Hi there,

I hope this is the right place to post this,

I'm having some issues. Just recently put together a new PC but used the HDD and RAM from previously computer as they were working and compatible.

I wanted to find a way of backing up my hard drive without formatting it when installing windows so someone told me to instal ubuntu and create partitions so that I dont wipe data.

I created a 10gb partition on a 2tb hard drive and successfully installed ubuntu but now that i'm in all I can see is that 10gb, I cant find my hard drive and the data. I need to back up this hard drive befgore installing a operating systemand wiping it, can anyone help me?

James

- 10 gigs is a bit skimpy for an operating system - , but

In the file manager "nautilus" in the left pane should be all the differing file systems. A click on any one will open that file system, Depending on the imposed permissions, one might have to open the file manager from terminal with elevated (gksudo) privileges .

If one wants the filesystem(s) to be auto mounted, then one edits the FileSystem TABle file, '/etc/fstab'. 

Further advise pending, on what you want to do.

[INDENT][INDENT]it's ubuntu
[INDENT][INDENT][INDENT]it's doable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james_r2 on 2014-12-17
> **Bashing-om said:**
> James_r2: Hi !


If one wants the filesystem(s) to be auto mounted, then one edits the FileSystem TABle file, '/etc/fstab'. 



how does one do this!!

im sooo confused

---

### Post by yancek on 2014-12-17
How many hard drives do you have and what do you want to back up from and to what.  Boot Ubuntu and open a terminal and enter this command and post the output here:  sudo fdisk -l(Lower Case Letter L in the command).  You can open a terminal by simultaneously holding down the Ctrl+Alt+t keys.

---

### Post by Bashing-om on 2014-12-18
james_r2; Hello

> **james_r2 said:**
> how does one do this!!

im sooo confused

We are here to (UN)confuse the issue.

Tell us what you want, what you have done and we will redirect your efforts.

We do not want to overload you, however, we do want that you fully understand directives.
Please comply with yancek's request ( above) and we take up this simple matter.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

ain't nothing but a thing

---

