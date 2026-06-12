---
title: "Error after attempting to update (8.10)"
date: 2008-11-13
forum: General Help
---

### Post by dustin_wielenga32 on 2008-11-13
So I was updating Ubuntu through the GUI "System>Update Manager".  I just installed Ubuntu 8.10 yesterday, and wanted to make sure it was all caught up.  It said there were 180 packages to update, with about 120MB to download.  I told it to go ahead.  After a while, the screen went blank, and moving the mouse, or hitting a key on the keyboard did nothing.  I waited a couple minutes, and tried again.  Nothing.  So, I restarted the computer (using the power button).

Now, when I run "sudo apt-get upgrade" it says the following:
```

dustin@dustin-mini:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
```

I select "Y".  Then:
```

Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                                                                      invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
dustin@dustin-mini:~$ 

```

I don't think it liked me restarting in the middle of an update, but I wasn't sure what to do, and thought the system had frozen.

Any idea what to do now to get it back in shape (and to get the system-tools-backend installed properly)?

The computer is an MSI Wind Barebone, with an Atom N230 (1.6GHz), no optical drive, and the OS is running from a 8GB Transcend CF card.  The printout of "df -h" says that 4.4GB are still available.

Any assistance would be much appreciated.  Thanks, and wish you all a great evening/day!

---

