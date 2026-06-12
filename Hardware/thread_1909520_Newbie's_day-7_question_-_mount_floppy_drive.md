---
title: "Newbie's day-7 question - mount floppy drive"
date: 2012-01-15
forum: Hardware
---

### Post by chenxinghao on 2012-01-15
Installed Ubuntu 11.10 on my IBM ThinkCenter A50P 8432-94U, with the dual-boot option; the master HD has the Windows XP Pro and half of the slave HD, while Ubuntu has the other half of the slave drive; both drives are WD 300GB. (I intended to let Ubuntu taking all of the slave HD, but the 11.10 installation process using default settings made such configuration selection while I was clueless about what is was doing. But I am OK with the setup for now, at the beginning on the learning curve.)

My question today is about accessing the floppy drive. The floppy drive icon does appear in the Home folder, next to the two HDs. I can mount and unmount the master HD (the one with Windows XP Pro installed) with the mouse. But with the floppy drive, it shows up in the Home folder's Device section as unmounted and the right-click with the mouse doesn't give me a "mount" option; click on the "Detect Media" (which only shows up in the floppy drive's menu) would lights up the GREEN light on the FD's panel.

Ran the "Additional Drivers" in Dash home's Installed apps several times already since day-one and it detected and installed nothing.

What do I need to do in order to get the floppy drive mounted?

(This is not a live-or-die issue because I can always use Windows XP Pro to access the FD and download the files and then transfer them on to my this Ubuntu installation - have done some already. But it is an item on my learning list. As an engineer, I like to get every pieces of hardware in working order.)

---

### Post by ajgreeny on 2012-01-15
To mount a floppy you now need to use udisks, which makes the command a bit more of a palaver.  Try ```
udisks --mount /dev/fd0
```in terminal.  This has been so since 10.04, though so few users now even have floppy disks to try this on that it has just dropped off the list of problems.

---

### Post by chenxinghao on 2012-01-15
Here is the error message:

chenxinghao@MyUbuntuSandBox:~$ udisks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: /dev/fd0 is not a valid block device

chenxinghao@MyUbuntuSandBox:~$

---

### Post by ajgreeny on 2012-01-15
Have a look in /dev for all the fd0u### device files, where ### is a three or four digit number, and try those listed there, one by one.

 I have read somewhere that other device names than fd0 are needed on some machines.

---

### Post by chenxinghao on 2012-01-15
There are only fd and fd0 under /dev; tried both but none worked; same error messages.

---

### Post by ajgreeny on 2012-01-15
Sorry.  In that case I've no idea.

---

