---
title: "After crash, Ubuntu does not come up, ext3 root filesystem fails to mount"
date: 2008-09-15
forum: General Help
---

### Post by amit_ch on 2008-09-15
Hello,

Ubuntu 8.0.4 crashed while opening a .mpg in totem player. it was a hang, no response to keyboard, the mouse was moving but not response to clicks. Ctrl+Alt+F1, etc did not open a console.
On a reboot, the system did not come up. Neither did rescue mode. Rescue mode shows the last few kernel messages were
    ext3: recovery required
   Orphan cleanup on readonly filesystem

which means Root filesystem with ext3 fails to mount.

I then tried booting with the 8.04 live CD, even the CD never boots up. When running without the flags quiet & slpash, again the above statements are the last printed.

I tried all of following Ubuntu live cds, 8.04.1, 7.10, 7.04, no luck. The message is not printed in the last one, but it is stuck.

Does anyone know of any solution? Is there a way of not loading the rootfs from the live CD?

I also found there is a fix for infinite loop in 2.6.27 ([http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.27-rc1](http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.27-rc1)), but am not sure if this is that issue

Thanks
Amit

PS: I have also filed a bug, [https://bugs.launchpad.net/ubuntu/+bug/270371](https://bugs.launchpad.net/ubuntu/+bug/270371)

---

### Post by amit_ch on 2008-09-15
Ok, so it was the problem from the link, rebooting from a live cd for Intrepid (Ubunty 8.10) Alpha 5 which has kernel 2.6.27 fixed it.
Incase your box hangs or goes in an infinite loop after a crash, this is one of the solutions.

It printed some error messages such as bad orphan node, did you run e2fsck, n_inode = 1 , etc and then rebooting off the installed Ubuntu worked.

Amit

---

### Post by amit_ch on 2008-09-15
Should mention, this is bad. Users should not have to go through kernel patches, logs and try out alpha OSes to boot up from a crash.

---

### Post by amit_ch on 2008-09-16
Reply from Ted Tso on the linux kernel mailing list. Includes a suggestion for live cd (two ways to do it, either run e2fsck automatically or mine, provide a way of not mounting disk filesystems) and another for patch ubuntu kernel.

Regards
Amit

----------------
-------- Original Message --------
Subject: 	Re: ext3 mount infinite loop over orphan list issue, please release 2.6.27
Date: 	Tue, 16 Sep 2008 08:53:46 -0400
From: 	Theodore Tso <tytso@mit.edu>
To: 	Amit Chaudhary <amitch@rajgad.com>
CC: 	[email]linux-kernel@vger.kernel.org[/email]
References: 	<48CEDD12.4060901@rajgad.com>


On Mon, Sep 15, 2008 at 03:09:22PM -0700, Amit Chaudhary wrote:
> Over the weekend, due to a crash, I ran into the ext3 mount infinite  
> loop over orphan list issue. This was on Ubuntu 8.04. I tried many  
> things, including using 18 month old distributions, nothing works. Only  
> solution is to boot off a alpha version of next Ubunuty which has the  
> 2.6.27 kernel (rc1 has the fix), more details are below:
>
> Can you please release 2.6.27 so that it can make it to stable  
> distributions.

As you point out, this problem has been fixed in 2.6.27-rc1.
Unfortunately, it is a problem which has been around for a very long
time --- perhaps since ext3 was first written.  No one had noticed the
problem for a very long time; in fact the first time someone reported
it as far I know was June 6, 2008, when Sami Liedes found it via a
synthetic testing program, fsfuzzer, which creates filesystems, then
corrupts them randomly and then sees whether or not they cause the
kernel to panic or hang when they are mounted.

You seem to have had the bad luck of running into the problem in a
real world situation relatively recently, but this has been a
long-standing problem.

As far as releasing 2.6.27, there still is a fairly large set of
regressions (i.e., bugs introduced in 2.6.27-rc1 or later) which need
to be fixed before we can release it; otherwise more users will have
bad experiences when older kernels that had worked fine for them will
break for them.  So while it might have helped you to have released
2.6.27, it could make things worse for many other users.  So that's
not a realistic option.  If I had to guess, given currently the
projected regression bug fix rates, there still is at least 2 or so of
bug fixing that still needs to be done before 2.6.27 is ready for
release.

We could take this bug fix and nominate it for release in the next
2.6.26-stable series, which distributions could then pick up --- maybe
we should have, but when the patch went in, it was seen was a fix for
largely theoretical problems, and not something that needed
accelerated handling.  This is still something we could do, but
realistically I'm not sure it's going to help the Ubuntu Intrepid
release, since it's pretty late in their schedule.  You might be
better off asking the Ubuntu kernel team if they are willing to cherry
pick the commit in question (ae76dd9a) and include it in their
release; they do have the ability to do that without waiting for an
upstream release, you know.

You also should have been able to work around the problem if you had
booted a rescue CD and checked your filesystem from the rescue CD.
That is the normal way these sorts of problems are fixed, and I'm a
bit surprised you didn't try this first.  It could be that Ubuntu
Rescue CD's could be made better by automating the ability of (upon
request) detecting the root filesystem on Ubuntu systems and then
running e2fsck on the filesystem before trying to mount them.

If you are willing to help out, we can always use more testers to test
the development kernels.  We can't do this alone, you know.  We've
wanted to shorten the release window, but in order to do that we need
more people helping to find and fix bugs during the development cycle.
Remember, this is open source.  If you see a problem you don't like,
you can help fix it.  And in fact, that's the most likely way that it
will get fixed.

Best regards,

						- Ted

---

### Post by Pipey on 2008-09-25
so for us noobs, what is the exact commands we should be entering at the terminal?

e2fsck /dev/sda5 

returns

/dev/sda5:  clean, 167741/184054 files, 988707/3674860 blocks


i assume there is a switch im supposed to be adding here... "e2fsck, n_inode = 1" doesnt seem to be it

---

### Post by Pipey on 2008-09-25
> **Pipey said:**
> so for us noobs, what is the exact commands we should be entering at the terminal?

e2fsck /dev/sda5 

returns

/dev/sda5:  clean, 167741/184054 files, 988707/3674860 blocks


i assume there is a switch im supposed to be adding here... "e2fsck, n_inode = 1" doesnt seem to be it


well, for all us noobs out there

go download the latest Intrepid Ibex Alpha .iso

here's a link:  [http://cdimage.ubuntu.com/releases/intrepid/alpha-6/](http://cdimage.ubuntu.com/releases/intrepid/alpha-6/)

burn that baby

boot from it(make sure to check that bios)

i wasnt able to boot from the cd the first time, the second try, i used the f4 option "safe graphics mode" which worked correctly

now that you have booted from the disk in "safe graphics mode", you need to open up a terminal

at the terminal you will type this

e2fsck -f /dev/sda5   

## /dev/sda5 is the location of your borked system.  it may be called something else. 

then it will spit a bunch of y/n questions

answer y to them

restart as normal


i really hope that works for you

<3 rtfman e2fsck

---

