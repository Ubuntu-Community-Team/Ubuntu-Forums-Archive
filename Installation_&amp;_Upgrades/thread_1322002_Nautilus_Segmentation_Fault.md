---
title: "Nautilus Segmentation Fault"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Karmatica on 2009-11-10
Hello all this is my first post
First of all I had started with 9.04 and really no major problems. after I upgraded to 9.10 I could no longer access nautilus whether it was via places or teminal. Thisis the error message I get:

(nautilus:11385): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:11385): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:11385): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:11385): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault

So i tried many things including checking on here. I consequently did a new fresh install and low and behold Nautilus began working again...But after installing Adobe Flash and the related dependencies(sorry can't remember all of them), As well as allowing the update manager to update Nautilus is yet again not working. So next I removed flash and the dependencies and still Nautilus doesn't work .So I have to assume it has something to do with one of the updates and there was over 38 so does anyone have a clues as to what is causing this problem?

---

### Post by Mr_Bumpy on 2009-11-10
Hi,

A friend of mine is having the same problem.  Here's a couple of things I've noticed:
1) No desktop icons are showing (which Nautilus is responsible for).  Is it the same case for you?
2) I had my friend create a second user account, and Nautilus works fine in that account, so it seems that Nautilus might be choking on a configuration option or something.  I've tried changing/deleting options I could find to no avail.

Please post back if you are able to find a solution, and I'll be sure to post any solutions I come across as well.

---

### Post by Karmatica on 2009-11-10
thanks for your response. And I also have the same problem with the desktop. funny thing is mind you I can in some programs navigate the file system, but not with nautilus. I have tried setting up a different user as well and no luck there either. I am going to reinstall 9.10 and install each upgrade one at a time until  nautilus gives out that should narrow things down I hope...wish me luck!

---

### Post by jfrorie on 2009-11-18
> **Karmatica said:**
> thanks for your response. And I also have the same problem with the desktop. funny thing is mind you I can in some programs navigate the file system, but not with nautilus. I have tried setting up a different user as well and no luck there either. I am going to reinstall 9.10 and install each upgrade one at a time until  nautilus gives out that should narrow things down I hope...wish me luck!

I don't know if it will add any info, but I've had the same problem.  I am however able to run 

sudo nautilus

Dunno if that helps.

---

### Post by jfrorie on 2009-11-18
> **jfrorie said:**
> I don't know if it will add any info, but I've had the same problem.  I am however able to run 

sudo nautilus

Dunno if that helps.

Also, do any of you run samba shares and have bookmarks under nautilus?

Anyone know where this info is stored in the system?

---

### Post by teh_luke on 2009-11-20
hi, i had the same problem.
i tracked it down to this:
the folder ~/.local/share/gvfs-metadata became corrupted. deleting it solved the problem. don't know which file exactly.
please confirm.

---

### Post by saisho on 2009-11-21
Thanks teh_luke!

Deleting the folder did solve the problem for me. I guess something went wrong during the upgrade to 9.10. This was the most annoying problem after upgrading. Great to have the community support to solve problems.

---

### Post by teh_luke on 2009-11-23
ok great.
the flawed behaviour occured to me after my system froze. not after update (was a clean install).
maybe someone can mark this as resolved.

---

### Post by astro_dave on 2009-12-21
> **teh_luke said:**
> hi, i had the same problem.
i tracked it down to this:
the folder ~/.local/share/gvfs-metadata became corrupted. deleting it solved the problem. don't know which file exactly.
please confirm.

Thanks teh_luke! That solved my issue.

After updating to Karmic Koala, nautilus no longer worked correctly. No icons were displayed on the desktop and I couldn't navigate graphically using windows. I do usually use the command line so I left it alone for a month or two, but it bugged me that something wasn't working.

Anyone nervous of deleting that folder - you could always backup the contents elsewhere. e.g.:
cd ~/.local/share
mkdir gvfs-metadata.backup
mv gvfs-metadata/* gvfs-metadata.backup/.

---

### Post by crazymonkey on 2010-03-24
I started to get the same problem after having a USB key fail to unmount properly.

I removed the ~/.local/share/gvfs-metadata folder and it started to work again.

Thanks alot teh_luke

---

### Post by frimdaddy on 2010-03-24
I tried deleting ~/.local/share/gvfs-metadata but it still segfaults.

using sudo nautilus also doesn't work. About ready to give up on the GUI and go straight console for my server... unless we get a helping hand here... anyone?

TIA,   Giacomo

---

### Post by afrodeity on 2010-05-24
Mine still seg faults after the upgrade.

```

Program received signal SIGSEGV, Segmentation fault.
0x002cf189 in g_type_check_instance_cast () from /usr/lib/libgobject-2.0.so.0
(gdb) backtrace full
#0  0x002cf189 in g_type_check_instance_cast () from /usr/lib/libgobject-2.0.so.0

```

The rest of the backtrace is here:

[http://paste.ubuntu.com/438481/](http://paste.ubuntu.com/438481/)

There is a bug which has been filed [https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/413152](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/413152)

---

### Post by afrodeity on 2010-05-25
```
afrodeity-desktop kernel: [122911.291879] nautilus[13859]: segfault at 7 ip 0035a189 sp bff4ab20 error 4 in libgobject-2.0.so.0.2400.1[330000+3d000]
```

Found this in /var/log/messages

---

### Post by afrodeity on 2010-05-25
```
afrodeity-desktop kernel: [122911.291879] nautilus[13859]: segfault at 7 ip 0035a189 sp bff4ab20 error 4 in libgobject-2.0.so.0.2400.1[330000+3d000]
```

Found this in /var/log/messages

---

### Post by afrodeity on 2010-06-07
[http://ubuntuforums.org/showthread.php?p=9424292#post9424292](http://ubuntuforums.org/showthread.php?p=9424292#post9424292)

---

### Post by giorgio_fornara on 2010-12-31
> **teh_luke said:**
> hi, i had the same problem.
i tracked it down to this:
the folder ~/.local/share/gvfs-metadata became corrupted. deleting it solved the problem. don't know which file exactly.
please confirm.
GREAT! after a sys crash I got nautilus segfault.
your suggestion worked great for me.
MANY THANKS

---

### Post by Light-kun on 2011-06-23
deleting  .local/share/gvfs_metadata didn't fix
still getting 

```
kernel: [22304.357478] nautilus[18464]: segfault at 1 ip 0808fb0c sp bff07a70 error 4 in nautilus[8048000+1af000]

```

Any ideas?

---

