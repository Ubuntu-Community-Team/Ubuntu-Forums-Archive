---
title: "Horrendous disk IO performance"
date: 2010-06-13
forum: Hardware
---

### Post by mewrei on 2010-06-13
OK, I knew about the horrible random access performance of spinning disks before but now I'm wondering if there's something else wrong.

My current setup is I have 3 disks in question.  An external, USB 2.0 attached drive, and two internal drives, one for the root partition and one for the /home partition.

The external drive is NTFS, the root partition is ext4 and the /home partition is JFS.

For some reason I get big IO blocks randomly where my system's performance slows to an absolute crawl for a few seconds.

And in addition, when I'm attempting copy jobs (in this case, cp -r), I get a HUGE IO degredation (as in random freezeups across the board, and directory listings in GNOME taking 5-10 minutes depending on the size of the directory).

Further I've been trying to move 300GB of data and its literally taken 3 days.

I'm wondering if my controller is giving out (nForce 4) or if this a problem inherent to JFS.  I believe I'm using CFQ as my IO scheduler (default Ubuntu kernel, haven't touched anything along those lines because I've been trying to chase this bug down for months now).

Does anyone have any insights?

---

### Post by dtfinch on 2010-06-13
Is this mainly related to the external drive? At my work we have a couple backup servers which each make a secondary backup to identical external usb 1tb hard drives. One I left as NTFS (was preformatted), and the other I reformatted as EXT3. The NTFS one takes 5 hours to update (rsync scanning the whole drive and updating modified files), with the cpu maxed out the entire time, while the other takes only about half an hour.

Could also be related to this. I've had slowness in firefox (which calls fsync a lot, halting it until changes are written to disk) when copying large files locally in the background:
[https://bugzilla.kernel.org/show_bug.cgi?id=12309](https://bugzilla.kernel.org/show_bug.cgi?id=12309)

When copying from the command line, I'd prefix it with "ionice -c 3" to make it copy at idle i/o priority, which shouldn't eliminate the problem in most cases.

A slightly loose or bad drive cable can also cause random pauses.

---

### Post by mewrei on 2010-06-14
Thanks for the useful info, didn't realize that the web browsers were getting schizophrenic with the file system calls.

I've come up with a workaround until something better is done.

[http://peregrin.jmu.edu/~earmantg/notes/linuxAndWebBrowsers.html]("http://peregrin.jmu.edu/~earmantg/notes/linuxAndWebBrowsers.html")

Not the ideal solution but it does seem to increase performance.

Let me know what you think.

---

### Post by sdennie on 2010-06-14
> **mewrei said:**
> Thanks for the useful info, didn't realize that the web browsers were getting schizophrenic with the file system calls.

I've come up with a workaround until something better is done.

[http://peregrin.jmu.edu/~earmantg/notes/linuxAndWebBrowsers.html]("http://peregrin.jmu.edu/~earmantg/notes/linuxAndWebBrowsers.html")

Not the ideal solution but it does seem to increase performance.

Let me know what you think.

The fix you've found is the same as ibuclaw describes in better detail here: [http://ubuntuforums.org/showthread.php?t=1103926](http://ubuntuforums.org/showthread.php?t=1103926).  It's an fine solution if the problem is fsyncs.  

The problems you are describing are consistent with my experiences with NTFS vs. ext3/4.  At work, I have a Windows machine that has a VM with 1GB of RAM in it running Ubuntu 9.10.  To suspsend that VM to disk (so, a 1GB write), takes 1-2 minutes.  Conversely, at home, I have a 2GB Windows VM running under linux with ext4 and to suspend it to disk (so, a 2GB write) takes just a few seconds.  Both machines are using fast SSD's and in fact, the work machine has faster write speeds than my home machine.

In essence, the problem is NTFS.  It's poor no matter what implementation you use.

---

### Post by dtfinch on 2010-06-14
There's also an option I didn't know about before today. If you go to the url "about:config" in Firefox, add an integer called "toolkit.storage.synchronous" and set it to 0, it should have the same effect of disabling fsync without as much work.

---

