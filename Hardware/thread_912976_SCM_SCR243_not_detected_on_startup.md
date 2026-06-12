---
title: "SCM SCR243 not detected on startup"
date: 2008-09-07
forum: Hardware
---

### Post by natsbar on 2008-09-07
>Re: How To: Set up and use a DOD Common Access Card (CAC) for Army >Knowledge Online (
>Code:
>
>cw@ubuntu:~$ sudo pcscd -f
>[sudo] password for cw:
>pcscdaemon.c:294:main() pcscd set to foreground with debug send to stderr
>configfile.l:108:evaluatetoken() Error with device /dev/SCR24x0: No such >file or directory
>configfile.l:109:evaluatetoken() You should use 'DEVICENAME /dev/null' >if your driver does not use this field
>pcscdaemon.c:532:at_exit() cleaning /var/run
>pcscdaemon.c:551:clean_temp_files() Cannot unlink /var/run/pcscd.comm: >No such file or directory
>
>I'm getting the same error as joeprelude and that is the error above >that I get when I run pcscd -f.


I'm getting the same message as this person (barrett) from another thread (How To: Set up and use a DOD Common Access Card (CAC) for Army Knowledge Online (AKO)).  I started a new one because I can't reply to his message and I'm not entirely sure why. This question was never answered in the other thread, and I'm assuming it's because barrett came up with the same workaround as me.  He removed the pcmcia card (SCM SCR243) put it back in, ran the daemon, and it started to work.  I did a little investigation, and the error does reflect reality.  The pcmcia card is not detected on startup and so /dev/SCR24x0 does not exist.  Of course this changes when the card is removed and reinserted.  The question I have is this.  Can I get the card to be detected on startup?  Some background information.  I use an updated Xubuntu Hardy Heron (but I doubt it's Xubuntu specific, this is not a UI issue), and the driver for the card is a propiety driver.  I understand that this means that the problem might be with the driver and i'll have to contact the manufacturer.  Thanks for the help.

---

### Post by mmoses on 2008-12-09
Try running mknod in /lib/udev/devices to create your file:
sudo mknod SCR24x0 c 251 0

The udev startup (init.d) copies all these default device files into /dev at startup.  This fixed the issue for me.

---

### Post by prophet_ on 2009-01-10
I had the same problem with SCR241. There are few bugs in the script that udev uses when adding and removing this pcmcia reader. Script is copied in /etc/pcmcia directory when you install the driver and is called scr24x-node. You can fix it either to set it run using the bash shell by replacing first line
```
#/bin/sh
```
with
```
#/bin/bash
```
which is a dirty solution:)
or 
correct the errors in it so script can run under /bin/sh. 
To correct the errors you should change == with = when testing strings "add" and "remove" so it looks like this
```
if [ "add" = $1 ]; then
```
and
```
if [ "remove" = $1 ]; then
```
which will enable the udev to create device file.
 
Deleting & character in front of >, so you have
```
`/sbin/pccardctl ident | grep SCR24 > /dev/null`
```
and
```
`/sbin/pccardctl ident | grep PCDM > /dev/null`
```
will fix the remove device file functionality.

---

