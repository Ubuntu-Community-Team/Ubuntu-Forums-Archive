---
title: "Brother MFC-J6510DW scanning"
date: 2013-09-12
forum: Hardware
---

### Post by gleedadswell on 2013-09-12
I have recently done a new install of 12.04 and it's time to get scanning working.

I have followed the Brother website as well as (my own) instructions from 

[http://ubuntuforums.org/showthread.php?t=1842372](http://ubuntuforums.org/showthread.php?t=1842372)

to try to get wireless network printing working.  I've also followed instructions from

[http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother](http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother)

about adding the two lines to /lib/udev/rules.d/40-libsane.rules, adding users to the lp group, and installing libsane-extras.  But when I open xsane it fails to find the scanner.   Everything *looks* like it should work.  I can do

```

root@kinetic-poincare:~# brsaneconfig4 -q
....
Devices on network
  0 SCANNER                      "MFC-J6510DW"                I:192.168.1.100

```

So brsaneconfig4 -a seems to have worked.  Also

When I ran 

```

brscan-skey

```

and then checked with 

```

brscan-skey -l

```

initially it showed the scanner as active.  But it still wasn't detected.  Now when I run brscan-skey -l I get no output.  I tried rerunning brscan-skey but this doesn't resolve the problem.

Any ideas about to try next?

---

### Post by gleedadswell on 2013-09-12
Uninstalled brscan4 and brscan-skey and then reinstalled them.  Also, I had made an error in adding the lines to 40-libsane.rules.  I had added the lines after the 

```

[COLOR=#000000][FONT=Arial]LABEL="libsane_rules_end"[/FONT][/COLOR]

```

I also followed 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

and installed [COLOR=#000000][FONT=Arial]brother-udev-rule-type1-1.0.0-1.all

But still no luck.[/FONT][/COLOR]

---

### Post by gleedadswell on 2013-09-12
Hrmph!  It doesn't even work if I plug the scanner in via USB.  I plugged it in and ran brscan-skey again.  Now brscan-skey -l gave the output

```

 SCANNER           : brother4:net1;dev0  : 192.168.1.100        Active
 MFC-J6510DW       : brother4:bus5;dev1  : USB                  Active

```

But running xsane it still didn't detect the scanner.

---

### Post by kurt18947 on 2013-09-12
I wonder if you're being bitten by this bug:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

This problem is not exclusive to Brother, and I think due to a problem with the way Alien converts .rpm to .deb.

---

### Post by gleedadswell on 2013-09-14
Thanks kurt18947,

I wondered about that because some of the threads talked about copying those files.  I think it may be worse.  When I go looking for them those files don't exist.  I don't even have a /usr/lib64 directory.  Running locate from the root directory doesn't show those files anywhere.  Does anyone know which package was supposed to create those files?

Before someone asks, yes I'm sure I'm running 64-bit Ubuntu.  For example:

```

geoff@kinetic-poincare:~$ uname -a
Linux kinetic-poincare 3.5.0-40-generic #62~precise1-Ubuntu SMP Fri Aug 23 17:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Cheers!
Geoff

---

### Post by gleedadswell on 2013-09-14
I just uninstalled brscan4, brscan-skey and  brother-udev-rule-type1.  Then I created the /usr/lib64 directory manually, reinstalled the three packages and ran brsaneconfig4 and brscan-skey.  But the files did not appear in /usr/lib64 and xsane still fails to find the scanner.

Given that:

brsaneconfig4 -q shows the scanner
brscan-skey -l shows the scanner and lists it as active
BRAdmin Lite shows the scanner and lists the device status as active

the problem is probably at the end of sane.  Does sane have some diagnostic that I can run to get more information?

Cheers!

---

### Post by gleedadswell on 2013-09-14
Ha ha!!

I noticed while I was fiddling around with it that the brscan4 package file I had was

brscan4-0.4.1-6.i386.deb

which clearly isn't right since I'm running 64-bit.  I went to the Brother site and saw that the (red) visited link was indeed to the 64-bit version, but that the links to 32 and 64 bit were reversed in order to how they were everywhere else on the site.  So, suspicious, I went to the 32-bit package link to see what it would give me.  As I suspected it gave me

brscan4-0.4.1-6.amd64.deb

So I uninstalled everything again, reinstalled them (with the right brscan4 version this time) reran brsaneconfig4 and brscan-skey.  Just to be safe I linked the files that now existed in /usr/lib64/sane to usr/lib.  i.e.

```

root@kinetic-poincare:/usr/lib# ln -s /usr/lib64/sane/libsane-brother4.so .
root@kinetic-poincare:/usr/lib# ln -s /usr/lib64/sane/libsane-brother4.so.1 .
root@kinetic-poincare:/usr/lib# ln -s /usr/lib64/sane/libsane-brother4.so.1.0.7

```

Now everything works.  So, check which files you've got!  The links on the Brother site for the brscan4 packages are reversed and don't go to the files they say they go to!  So I've sent a support e-mail to Brother telling them about this mix-up, so hopefully others won't have this problem.  I'll mark this thread as SOLVED.

---

