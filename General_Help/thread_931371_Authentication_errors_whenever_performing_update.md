---
title: "Authentication errors whenever performing update"
date: 2008-09-27
forum: General Help
---

### Post by hcaleman on 2008-09-27
When I attempt to perform updates either via synaptics or terminal I get the following signature errors.  Have been fooling around trying to get the proper authentication key with no luck, any advice on how to resolve this?

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by RedPandaFox on 2008-09-28
Read these, see if they help
[http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/57df939ea86de7e2](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/57df939ea86de7e2)
[http://ubuntuforums.org/archive/index.php/t-281428.html](http://ubuntuforums.org/archive/index.php/t-281428.html)

---

### Post by hcaleman on 2008-09-30
Thanks, the first link helped me figure out what I did wrong with the google repository (stupid typo).  

Still getting authentication errors with the ubuntu archives though, I'm able to resolve and download packages, but it always tells me that the updates can't be authenticated.  Here is the revised error:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: **The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>**
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

**W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  **

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2008-09-30
> 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


You could try to restore the default GPG signatures.

From **System > Administration > Software Sources > Authentication** click on **Restore Defaults**

My default signature for <ftpmaster@ubuntu.com> is 437D05B5 (See attachment)

---

### Post by hcaleman on 2008-09-30
I followed a bugpath on launchpad.  Seems to be a somewhat common issue for people with cached servers returning bad responses (for whatever reason).  I did an apt-get clean then changed my ubuntu repository server and problem went away.  Several updates showed up that I was missing.

---

### Post by pushpita1988 on 2011-07-12
I have a similar error, but none of the methods are working....
please help..
upon entering sudo apt-get update I get..
[B]GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
[/B]Please help

---

