---
title: "Troubles using a 5.25 floppy drive"
date: 2013-02-10
forum: Hardware
---

### Post by WakeUpWolfgang on 2013-02-10
I have an old Sharp 7000 computer with no OS on it and I am trying to install one but my computer will not let me use my 5.25 inch floppy drive.

I get Daemon is Inhibited when I try to format a blank floppy. I tried "Sudo killall udisks" then I get the error

Error calling fsync(2) on /dev/fd0: Input/output error

In fstab I have
"/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0"

When I try to mount the drive I get "mount: /dev/fd0 already mounted or /media/floppy0 busy" 
or I get 
"mount: I could not determine the filesystem type, and none was specified"

---

### Post by Bucky Ball on 2013-02-10
Might help if you let us know what you are trying to install.

Will an old disk that size have the capacity to hold the install ISO for Ubuntu?

---

### Post by WakeUpWolfgang on 2013-02-10
I am trying to put free dos or DSL on it but I am using ubuntu to put the image onto the floppy. But my Ubuntu computer is having problems with the 5.25" drive.

---

### Post by oldfred on 2013-02-10
A couple of threads had these suggestions.

       [http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
[http://ubuntuforums.org/showthread.php?p=11244050#post11244050](http://ubuntuforums.org/showthread.php?p=11244050#post11244050) post #2 coffeecat
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

---

### Post by WakeUpWolfgang on 2013-02-11
When I try udisks --mount /dev/fd0 I get 

Mount failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

