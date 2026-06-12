---
title: "problems with dpkg. all files missing"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by K_Boomer on 2009-11-03
Running Ubuntu 9.10.

Ok, first I'd like to say that I was foolish in the following actions. I was having problems downloading bcmwl-kernel-source and b34-xfcutter, because some packages were corrupted. So... I took some advice from a forum and tried this:

1. The package list files are in /var/lib/dpkg/info

  In my case /var/lib/dpkg/info/libgtk1.2.list was corrupted
  (its contents were binary cruft).

  So the best way to go about this is to

2. Manually reinstall the affected package

  # move the info dir containing corrupted data out of the
  # way, and create a new 'info' dir
  cd /var/lib/dpkg
  sudo mv info info.bak
  sudo mkdir info

  # reinstall the affected package, in my case this was
  sudo apt-get --reinstall install libgtk1.2

  # this will print lots of warnings about missing list
  # files for the dependencies, which is obvious.
  # now move the newly generated files in 'info/' to the
  # 'info.bak/' directory containing info for all packages
  # this will replace the information for the package
  # we just installed
  sudo mv info/* info.bak/

  # and now get things back to where they were
  sudo rm -rf info
  sudo mv info.bak info


now things are in shambles and I get this error:

**dpkg: warning: files list file for package `file name' missing, assuming package has no files currently installed.**

where file name is one of MANY files listed.

also, I receive this message:

[B]Preparing to replace python2.6-minimal 2.6.4~rc2-0ubuntu1 (using .../python2.6-minimal_2.6.4~rc2-0ubuntu1_i386.deb) ...
Unpacking replacement python2.6-minimal ...
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.4~rc2-0ubuntu1_i386.deb (--unpack):
 unable to create updated files list file for package python2.6-minimal: No such file or directory
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.4~rc2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

If someone could help me, I would be so grateful. Also, I am trying to learn more about these problems so I can address them better in the future. If you can tell me what is going on instead of just posting commands, that would be excellent.

thanks in advance

---

### Post by K_Boomer on 2009-11-04
Solution: 

Just reinstalled 9.10 from disk. Some things are better left untinkered....

---

