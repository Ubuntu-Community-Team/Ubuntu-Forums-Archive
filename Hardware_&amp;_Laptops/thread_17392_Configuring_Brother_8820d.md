---
title: "Configuring Brother 8820d"
date: 2005-02-28
forum: Hardware &amp; Laptops
---

### Post by billjw on 2005-02-28
Hi all

just made the switch (finally) to Linux. This should be the last stop on an enjoyable journey. Only problem is ... I can't get the printer to print. A few distro's ago it did as a generic printer. Now, nothing.

Brother has a download for this model which I have downloaded, but how to install it is the question.

I have done the sudo -install thing but here is the response ...

Unpacking replacement mfc8820dlpr ...
/var/lib/dpkg/info/mfc8820dlpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing mfc8820dlpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8820dlpr-1.1.2-1.i386.deb

Not being a Linux guru this all looks greek to me.

I know I am missing something here. any ideas?

Bill

---

### Post by aaazman on 2008-04-05
BillJW:

I had the same problem. The only way, I found, to fix this problem is by actually going directly to the
**/var/lib/dpkg/info** directory. You have to **sudo gedit mfc8820dlpr.post** file and comment out line 3. The next thing I did was a **sudo dpkg -r --force-all --force-architecture mfc8820dlpr** and it gives me a **Removing mfc8820dlpr** statement.

Good Luck!

---

