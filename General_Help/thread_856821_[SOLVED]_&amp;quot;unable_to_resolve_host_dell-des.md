---
title: "[SOLVED] &amp;quot;unable to resolve host dell-desktop&amp;quot;"
date: 2008-07-11
forum: General Help
---

### Post by jbeaunaux on 2008-07-11
I'm completely new to Ubuntu, running a Dell Inspiron 530n that had been delivered w/ 7.10 but that I have updated to 8.04.

I've been running into problems trying to install an adobe/flash plug-in for Firefox 3, launching Synaptic Package Manager, launching Software Sources, or running various different commands in the Terminal. In these situations I've been receiving the same error message which tells me 'unable to resolve host dell-desktop'. I've taken a look in my System Log viewer after trying to launch Synaptic to see if I could try to figure out what's going on. This is what I see under /var/log -> auth.log:

Jul 9 21:28:35 dell-desktop sudo: john-daniel: unable to resolve host dell-desktop
Jul 9 21:28:35 dell-desktop sudo: PAM unable to dlopen(lib/security/pam_smbpass.so
Jul 9 21:28:35 dell-desktop sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Jul 9 21:28:35 dell-desktop sudo: PAM adding faulty module: /lib/security/pam_smbpass.so

Is there any way of correcting this, and how should I go about doing it? I know that there is a very similar thread in the Known Hardy Bugs section, but I don't know that this particular issue was addressed. Thanks in advance for any help!

---

### Post by HalPomeranz on 2008-07-11
See this thread: [http://ubuntuforums.org/showthread.php?t=807171](http://ubuntuforums.org/showthread.php?t=807171)

---

### Post by drs305 on 2008-07-11
Your hostname may be messed up. Look at System, Administration, Network. Click on Unlock and enter your password. Look at Hosts and see if the first 2 lines look like:
```

127.0.0.1 localhost
127.0.1.1 *yourcomputername*

```

If there is a period and an extra value after *yourcomputername* write it down but then remove it.  For example, if it says *yourcomputername**.somethingelse*** remove the **.somethingelse**

---

### Post by jbeaunaux on 2008-07-14
Thanks! Removing the addition to my computer's hostname did the trick! Everything seems to be working just fine now.

---

### Post by jbeaunaux on 2008-07-14
Problem solved.

---

### Post by drs305 on 2008-07-14
> **jbeaunaux said:**
> Problem solved.

Glad to hear the solution worked. 

The way to mark a thread solved is to go to the "Thread Tools" link near the top right of the first post - click on it and there is a 'Solved' option.

By the way, Welcome to Ubuntu!  :)

---

### Post by jbeaunaux on 2008-07-17
Thanks again for the help and for the pointer!

---

