---
title: "Failed to install drivers for Brother HL-5040 printer"
date: 2010-09-23
forum: Hardware
---

### Post by pcpain on 2010-09-23
I tried to install the drivers for Brother HL-5040 printer to my Ubuntu 9.10 PC, but failed. Now I cannot run Synaptic Package Manager. The error messages for the failed installation of the drivers are as follows:

 jlp@Gigabyte:~/Desktop$ sudo dpkg -i --force-all hl5040lpr-1.1.2-1.i386.deb
(Reading database ... 158263 files and directories currently installed.)
Preparing to replace hl5040lpr 1.1.2-1 (using hl5040lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl5040lpr ...
/var/lib/dpkg/info/hl5040lpr.postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: warning: old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error processing hl5040lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 126
Errors were encountered while processing:
 hl5040lpr-1.1.2-1.i386.deb


The subsequent error messages when using Synaptic Package Manager are as follows:

E: The package hl5040lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. 

Your help will be appreciated. I tried to re-install the drivers by repeating the above command line (sudo dpkg ...), but failed again.

---

### Post by sdgengineer on 2012-10-22
> **pcpain said:**
> I tried to install the drivers for Brother HL-5040 printer to my Ubuntu 9.10 PC, but failed. Now I cannot run Synaptic Package Manager. The error messages for the failed installation of the drivers are as follows:

 jlp@Gigabyte:~/Desktop$ sudo dpkg -i --force-all hl5040lpr-1.1.2-1.i386.deb
(Reading database ... 158263 files and directories currently installed.)
Preparing to replace hl5040lpr 1.1.2-1 (using hl5040lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl5040lpr ...
/var/lib/dpkg/info/hl5040lpr.postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: warning: old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error processing hl5040lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 126
Errors were encountered while processing:
 hl5040lpr-1.1.2-1.i386.deb


The subsequent error messages when using Synaptic Package Manager are as follows:

E: The package hl5040lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. 

Your help will be appreciated. I tried to re-install the drivers by repeating the above command line (sudo dpkg ...), but failed again.
I am also a Newbee.  I found the answer here:  [http://www.ihaveapc.com/2011/10/fix-annoying-the-package-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it-error-in-linux-mint-ubuntu/#comment-83038](http://www.ihaveapc.com/2011/10/fix-annoying-the-package-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it-error-in-linux-mint-ubuntu/#comment-83038)

Bottom line edit the "status" file and remove any evidence of the offending package.  You will need to reinstall but the package manager will again work!

SDGengineer

---

### Post by overdrank on 2012-10-22
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

