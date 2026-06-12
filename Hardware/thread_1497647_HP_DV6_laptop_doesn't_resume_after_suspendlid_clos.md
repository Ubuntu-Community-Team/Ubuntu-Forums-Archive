---
title: "HP DV6 laptop doesn't resume after suspend/lid closed"
date: 2010-05-30
forum: Hardware
---

### Post by foxy123 on 2010-05-30
It works after hibernation but not after suspension. The screen stays black and a hot reboot is the only option. Quite annoying as it is always easy to close the lid rather then switch off.

---

### Post by lidex on 2010-05-31
Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend")

---

### Post by foxy123 on 2010-06-02
> **lidex said:**
> Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend")

Thanks a lot for the link but nothing worked for me :(

---

### Post by Vaun on 2010-08-15
I have a DV6-2170US and was having the same issues and still with the present kernel in Maverick.  I'm using the mainline kernel and suspend/resume works flawlessly.  The issue is some Ubuntu [SAUCE].  I have not yet figured out what [SAUCE] is causing the issue.

---

### Post by foxy123 on 2010-08-15
> **Vaun said:**
> I have a DV6-2170US and was having the same issues and still with the present kernel in Maverick.  I'm using the mainline kernel and suspend/resume works flawlessly.  The issue is some Ubuntu [SAUCE].  I have not yet figured out what [SAUCE] is causing the issue.

what do you mean by 'mainline kernel'?

---

### Post by Vaun on 2010-08-16
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html")

---

### Post by Vaun on 2010-08-16
I finally got around to filing a bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618813]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618813")

---

### Post by foxy123 on 2010-09-11
> **Vaun said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000542.html")

I have installed the mainline kernel and now resume works. However, I can only get wireless network resumed, not Ethernet. The kernel's version is:

```
~$ uname -r
2.6.35-20-generic

```

---

### Post by rjjcvb on 2011-02-23
> **foxy123 said:**
> I have installed the mainline kernel and now resume works. However, I can only get wireless network resumed, not Ethernet. The kernel's version is:

```
~$ uname -r
2.6.35-20-generic

```

Hi,

I've exactly the same problem, and the same PC...

With windows 7 64bit no problem at all entering and awaking from suspend mode, but with ubuntu 10.10 cannot wake from suspend mode.

The strangest sting is that the problem I have now, my other laptop (Compaq presario CQ51) had this problem with vista and windows 7, then when I&#472;e installed Ubuntu 10.10, no problems at all with suspension mode....

There is a witch doing dark magic out here....

Someone please explain or give me some advise???:confused:

---

### Post by core.ban on 2011-03-23
bump bump...same issue with HP DV7.

On resume after lid close and re-open, laptop freezes completely.

Can post logs -- let me know which to post.

However, am currently going through this to try to fix problem:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend)

---

### Post by fercactus on 2011-04-26
I have the HP dv6700z cto.  I just upgraded my BIOS to F.34 and this appears to have solved my problem with suspend to ram.  Will continue to test.

---

### Post by foxy123 on 2011-05-05
The problem is back after upgrading to Natty :(

---

### Post by mayotte on 2011-05-26
On my dv6033cl w/11.04, suspend causes my external USB keyboard to drop characters (the laptop keyboard works fine.)  So I can't unlock the screen with the external keyboard. I have to log in using the laptop keyboard.  I end up having to reboot to clear the issue.

---

### Post by Thedark7 on 2011-08-17
Same problem with HP ENVY - help? (Sorry for bump)

---

### Post by foxy123 on 2011-09-23
The problem remains in Oneiric :-(

---

### Post by foxy123 on 2011-10-03
I wonder if anyone tried a different distro on DV6 to see if the problem is Ubuntu specific. I cannot do it as the laptop is now my wife's main production machine.

---

### Post by Toz on 2011-10-03
This might be a long shot, but I've seen this fix work for a number of notebooks: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")

---

### Post by foxy123 on 2011-10-03
> **Toz said:**
> This might be a long shot, but I've seen this fix work for a number of notebooks: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")

thanks for the link but it does not help :-(

---

