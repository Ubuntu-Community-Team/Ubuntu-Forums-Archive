---
title: "Toshiba Satellite A105-S2194 won't boot into Kubuntu 9.10 after upgrading kernel."
date: 2010-01-01
forum: Hardware
---

### Post by PatrickD-52761 on 2010-01-01
I'm not sure if this has been posted prior or not, but I'm posting it now.  After upgrading to the latest kernel version, my laptop will not boot into Kubuntu anymore.  Originally I was getting the error about "One or more mounts in /etc/fstab cannot yet be mounted..."  Now, I get the following (and it appears to be locked up although CTRL+Alt+Delete will force it to terminate and reboot):

init: udevtrigger main-process(74) exited with a Status 1
init: udevtrigger post-stop(75) exited with a Status 1
init: udevmonitor main-process(73) killed by TERM Signal

One or more mounts listed in /etc/fstab cannot yet be mounted:
CTRL-D for Recovery Shell (I know what this is)
/: waiting for UUID=3ca5171a-.....
/tmp: waiting for (null)
/swap: waiting for UUID=879ae611-.....

It just hangs here until I hit CTRL+Alt+Delete.

On my desktop, I briefly see the message about One or more mounts, but then it continues.

The only thing I've found relating to the message is this bug [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/483205](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/483205) which has been ruled "Not a bug as it's a message".

I'm at a loss.  I can reinstall Kubuntu, but then I'm stuck at the old kernel (assuming it boots into that at all).  I can't even boot into recovery mode or the old kernel because of this issue.  So, my only alternative is to use a Live CD and edit the files as directed.

Thanks for any help with this.

Have a great day:)
Patrick.

---

### Post by PatrickD-52761 on 2010-01-16
I've narrowed this down to one of the security updates that was released between October 28, 2009 and the date of my original posting.

However, I have not narrowed it down to which update it is.  The way I found this out is that I reinstalled Kubuntu, and configured it to automatically install security updates.  Then I attempted to install the bugfixes and cancelled that while they were still downloading (as my wireless kept dropping).  I then rebooted, and found that the problem had returned (the items in fstab not being able to be mounted because they are waiting on some process to finish).

Now, I have a dead laptop again (as far as Kubuntu goes) so I'm downloading the 9.04 desktop image and will use that for a while.

If anyone has suggestions on what I can do to narrow this down (or what security fixes dealt with fstab) I'll be more than happy to try them out.

Have a great day:)
Patrick.

---

### Post by isaacf on 2010-01-27
I have this same problem with my lenovo thinkpad sl510. I did a fresh karmic install and everything was merry, but then I installed the updates and now find my system unusable.

---

### Post by isaacf on 2010-01-27
After reading through this thread: [http://newyork.ubuntuforums.org/showthread.php?t=1318593](http://newyork.ubuntuforums.org/showthread.php?t=1318593)

I edited /etc/fstab as described here: [http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html](http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html)

and so far things seem to be going well.

---

