---
title: "[SOLVED] Getting an Epson T11 printer to work with 8.10"
date: 2008-12-31
forum: Hardware
---

### Post by swudee on 2008-12-31
Hi

I am still trying to get this printer to work.
I have tried following this thread.

[http://ubuntuforums.org/showthread.php?t=964784](http://ubuntuforums.org/showthread.php?t=964784)

I follow the link to download the driver .rpm's but the file downloaded extracts to a .install  :confused:

So Alien doesn't recognize it!
OK so I try renaming the file to a .rpm and I get the following.


root@ubuntu:~# alien --scripts --keep-version pips-*.rpm
Error executing "LANG=C rpm -qp --queryformat %{NAME} pips-st20-Fedora9-3.1.0-CG.rpm":  at /usr/share/perl5/Alien/Package.pm line 482.
root@ubuntu:~# sudo dpkg -i ./pips-*.deb
dpkg: error processing ./pips-*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./pips-*.deb

I am guessing it doesn't like Intrepids kernel version or something, wrong version dependency?

Does anyone have any ideas how to get this paper weight to print.
I am a thousand miles from home (Thailand) and trying to get this set up for my niece.

Thanks

I tried setting it up on a live cd just in case it was the dual language that was upsetting it, No change:(

---

### Post by Maccabee on 2009-04-01
Can you tell me how did you solved it??

---

### Post by Tjawi on 2009-09-26
Hi There,

Please visit the reference below. :)

[http://newyork.ubuntuforums.org/showthread.php?p=8012824#post8012824](http://newyork.ubuntuforums.org/showthread.php?p=8012824#post8012824)

---

