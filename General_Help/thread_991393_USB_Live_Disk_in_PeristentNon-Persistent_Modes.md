---
title: "USB Live Disk in Peristent/Non-Persistent Modes"
date: 2008-11-23
forum: General Help
---

### Post by inneedofhelp7 on 2008-11-23
I have a live USB setup.  My goal is to customize my system and install desired drivers/apps, then "Lock" it so that it behaves like a live disk with only a single directory that is writable.  I don't want anything to persist from one boot to another, other than the contents of this one directory.  

It would be ideal if there were separate boot menu options -- one than allows for changes to the whole system to be made (regular updates), and one for general usage that acts like a live disk.

I've modified the boot menu file (text.cfg) to contain the following two options:

```

label live
  menu label ^Run Ubuntu Persistently
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
label live-clean
  menu label ^Run Ubuntu Live
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
```

Both work, but in an undesired way.  Changes made in the persistent boots do persist, but they are not present when i run the "live-clean" boot.  This only boots to the system as it was before I customized anything.

Please let me know how to get a real live (no saving, file-caching, history, cookie, recent files, etc) setup that shows the changes I intentionally make when I run Persistent.

Thanks.

---

### Post by inneedofhelp7 on 2008-11-23
Could someone point me to where there is a good explanation of how the boot option "persistent" affects the boot (Casper, root directory, etc.).  Ubuntu seems to have poorly documented boot parameters.

---

### Post by C.S.Cameron on 2008-11-27
Changes made on a usb-creator persistent install are saved in a file named casper-rw.
The rest of the files are an image of the Live CD and do not change.
It is also possible to create partitions labeled casper-rw, (which saves your newly installed programs and home-rw which will save your settings.
You can probably create a new account to log into that has no write privileges.

---

### Post by swmspam on 2009-01-11
I have the same problem with DebianLive.

I setup my Grub with two boot options:

0 - non persistent
1 - persistent

Grub boots default to 0 - non persistent.

I booted up in persistent mode, made the final adjustments to my custom build, and let the machine boot into non-persistent mode. The final adjustments that I previously made were **not** there.

I rebooted again into persistent mode, and the adjustments came back.

What I want is a **non-volatile (non-persistent) operating system that retains adjustments made during persistent sessions.**

> You can probably create a new account to log into that has no write privileges.

This is a unsatisfactory solution, because the system needs to make certain writes (such as log files) that I don't want written to Flash. I want the user/system to create new files when in non-persistent mode, but I don't want to see those files again after a reboot.

**It seems that non-persistent mode does not load the changes made during a persistent session.** I have the same question as inneedofhelp7: **How can I boot in a non-volatile environment (any changes are NOT written to flash) while using the changes made during prior persistent sessions?**

---

### Post by ebhomepc on 2010-04-15
> **swmspam said:**
> I have the same problem with DebianLive.
 
I setup my Grub with two boot options:
 
0 - non persistent
1 - persistent
 
Grub boots default to 0 - non persistent.
 
I booted up in persistent mode, made the final adjustments to my custom build, and let the machine boot into non-persistent mode. The final adjustments that I previously made were **not** there.
 
I rebooted again into persistent mode, and the adjustments came back.
 
What I want is a **non-volatile (non-persistent) operating system that retains adjustments made during persistent sessions.**
 
 
 
This is a unsatisfactory solution, because the system needs to make certain writes (such as log files) that I don't want written to Flash. I want the user/system to create new files when in non-persistent mode, but I don't want to see those files again after a reboot.
 
**It seems that non-persistent mode does not load the changes made during a persistent session.** I have the same question as inneedofhelp7: **How can I boot in a non-volatile environment (any changes are NOT written to flash) while using the changes made during prior persistent sessions?**
 
 
Yes i have the same problem i have a ubuntu 9.10 usb setup with persistent and all my changes made updates etc but i would now like to make it readonly but if i boot with nopersistent it just boots to default ubuntu desktop HELP!!!!!!!!!!!!! PLEASE.

---

### Post by AwesomeTux on 2010-04-27
If I understand you correctly: You want to boot a LiveUSB drive where only in Session 1 can you make changes, and in Session 2 the system boots always as you left it in Session 1. Correct?

Well I have a LiveUSB drive that works this way.

I would guess it would work something like this:

A user named "Modify" who has the permissions of root user (reading, writing and executing any file and directory on the system).
You login as "Modify" when you want to modify the system.

Another user named -- let's say -- "Bob", who has very restricted permissions (no writing or executing any file or directory on the system not owned by "Bob").
You login as "Bob" to use the system.

When you shutdown the system (the LiveUSB) a simple script runs that deletes any files and directories owned by "Bob".

Or when you login as "Bob" a script runs that mounts /home/Bob/ on a tmpfs, so when you shutdown "Bobs" home directory is automatically lost.

I personally don't know how my LiveUSB does this, because I didn't do it myself. I ordered mine from InaTux. The beautiful thing about Free Software is the businesses it creates, we end up with people who know how to do these things for us.

[http://www.inatux.com/diy](http://www.inatux.com/diy)

Tell 'em something like this:

"I want a bootable LiveUSB drive where only in Session 1 can I make changes, and in Session 2 the system boots always as I left it in Session 1."

See what they tell you.

---

### Post by acarlstein on 2010-04-28
I created a live usb with Ubuntu 9.10

I can store information and changes in it

I am trying to modify the installation menu.

I am compiling different versions of the kernel and I want to have a way to choose them.

update-grub is not working as it should.

Any ideas?

---

### Post by dcstar on 2010-04-28
> **acarlstein said:**
> I created a live usb with Ubuntu 9.10

I can store information and changes in it

I am trying to modify the installation menu.

I am compiling different versions of the kernel and I want to have a way to choose them.

update-grub is not working as it should.

Any ideas?

Live USBs are **not** designed to be like normal systems. They have specific limitations (by design) and are essentially boot CDs with some capabilities for saving data - and even that has significant issues because of the SQUASHFS it uses.

If you want a system to behave like a normal system, do a normal install on the USB drive.

If you want a system that shouldn't stress out your USB device too much, look at installing a UNR version.

---

