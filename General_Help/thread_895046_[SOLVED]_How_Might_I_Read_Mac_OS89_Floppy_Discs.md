---
title: "[SOLVED] How Might I Read Mac OS8/9 Floppy Discs?"
date: 2008-08-19
forum: General Help
---

### Post by Anlace on 2008-08-19
Greetings,

I have a pile of floppy discs from a client, he asked if I might be able to pull the files off of them.  They were created in Mac OS 8 and 9.  What do I need to install to be able to mount and read these things?

Thanks for any and all help ;-)

Peace,
Gail

---

### Post by Cheesehead on 2008-08-19
Get ready for adventure!

In Synaptic, look for the packages 'hfsplus' to mount a mac hfs+ disk.
If an older hfs disk, try 'hfsutils'.

Add them and try your disks.
If the disk doesn't mount, try using the mount command:
```
sudo mkdir /media/macdisk
sudo mount -t /dev/fd0 /media/macdisk
```

Let us know the crazy errors and failures is as much detail as you can so we can help....

---

### Post by Anlace on 2008-08-19
Ok, here we go . . . .

sudo mount didn't work at all so I tried mounting via KDE/Dolphin.  I got the error message

> mount: wrong fs type, bad superblock on /dev/fd0, missing codepage or helper program, or other error in some cases useful info is found in syslog -try dmesg | tail or so

> gail@gail-kde:~$ dmesg | tail
[  433.687279] hfs: unable to parse mount options.
[  560.074030] hfs: unable to parse mount options.


Almost forgot to mention that I used Synaptic to install hfsplus, hfsprogs, hfsutils, hfsutils-tcltk, and libhsfp0.

Hmmm, I'll try another disc and see what happens.  These could be hosed discs too since they are old as the hills.

Thanks for the help!

---

### Post by Anlace on 2008-08-19
So far no luck, same error as above or this one:

> Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I am thinking that the message above is coming from broken discs since they don't seem to be even trying to read (no floppy disc sounds).

---

### Post by Cheesehead on 2008-08-19
Next steps:

*Is the hardware working?*
Do other (non-mac) known good floppies work in the drive?
Is your floppy drive really located at /dev/fd0?

*Is the software working?*
If you have a mac disk that is known good, then successfully mounting it will be a great victory (known good hardware, functioning software, adequate settings)

If you have a blank, you might be able to create a good mac disk using the hfs utilities you installed, then unmount it, remount it, and check it.

*Is it worth the hassle at all?*
Have you, by chance, any convenient access to a mac with a working floppy drive to check the disks?  If so, network access or a usb slot would save a lot of hassle...

---

### Post by Anlace on 2008-08-19
> Is the hardware working?

Yes, it works fine so that means the drive mounts correctly for other discs (formatted and unformatted).

> Is the software working?

Using hfsutils I am able to work with a known good floppy - formatted with hfs filesystem, added directories and files.  Let's try again with the old ones because I may have learned something new here (heaven forbid).

> Is it worth the hassle at all?

Maybe not so much to me but definitely to my client ;-)

---

### Post by Anlace on 2008-08-19
Ok this is as far as I am getting:

> gail@gail-kde:~$ sudo hmount /dev/fd0 /media/MacFloppy
Volume name is "Homecoming"
Volume was created on Thu Aug  1 14:48:41 1996
Volume was last modified on Mon Apr 12 08:18:11 1999
Volume has 84992 bytes free


What I am struggling with is navigating to the floppy drive directory, viewing the files on it, and being able to copy them into a hard disc directory.

When I try hcopy this happens:

> gail@gail-kde:~$ sudo hcopy /media/MacFloppy /share/Clients/Walt/Disc01
hcopy: "/media/MacFloppy": no such file or directory


I get this message for hcd too:

> gail@gail-kde:~$ sudo hcd /media/MacFloppy
hcd: "/media/MacFloppy": no such file or directory


I can hear the floppy accessing but am not able to view files.

xhfs crashes when I try to access the floppy as well.  I uploaded the crash info from the terminal if that helps.

---

### Post by BUSHYBOB on 2008-08-19
You can only read 1.4mb disks on a pc floppy drive, if they are 800kb or 400kb then you need a mac.

---

### Post by Anlace on 2008-08-20
Most of them appear to be 1.44 MB floppies.  The one that I am currently working with (and posting messages about) is a 1.44 MB floppy.

Apple quit building floppy drives into their computers a long time ago, something like 2000.  The oldest Mac that I have seen lately is the one in my office - a PowerMac G3 (AGP) and it does not have a floppy drive and the motherboard does not have a connector for one.

Will a USB external floppy drive work or will I have the same problems?  I would think it'd make no difference.

---

### Post by BUSHYBOB on 2008-08-20
I have a Mac boot floppy which I can read on my Gutsy machine. On my laptop running Hardy Heron I can see the Disk by its disk name in the Places menu but when I try to open it I get an "invalid option" error. Strangely I have Basilisk on the laptop and when I ran it it booted from the floppy disk. Weird

---

### Post by Anlace on 2008-08-20
I got about 2/3 of the floppies to read enough to copy the contents off of them.  The remainder were either 800k (or less) format or were bad.

After making the appropriate directory I was able to mount good disks using:
> sudo mount /dev/fd0 /media/MacDisk

Heck of a way to spend the afternoon!

---

### Post by no_way on 2010-01-10
Hi Anlace,

I'm no Linux expert, but I did mount my Mac disks wth BasiliskII and Sheepshaver.
Maybe you might refer to this:[http://www.emaculation.com/forum/](http://www.emaculation.com/forum/)
if you have problems installing a Mac emulator.

Best wishes!
[]("http://ubuntuforums.org/member.php?u=293269")

---

