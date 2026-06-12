---
title: "Source Problems Again!"
date: 2008-08-22
forum: General Help
---

### Post by Pandyrenim on 2008-08-22
I got help with my line 53 of my sources list. but now when i run my update it downloads the packages and then gives me this error message

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Alaric on 2008-08-22
I doubt you really need the source code to the programs in that repository anyway.  Try running 'sudo vim /etc/apt/sources.list', and press a to go into edit mode.  Then put a # in front of the troublesome line so ubuntu will ignore it.  Then press <escape> : w q <enter> to save the file and quit.  

Or, if you're not feeling adventurous, you could always use a standard GUI text editor with 'gksu gedit /etc/apt/sources.list' to add the # mark.  Good luck :)

---

### Post by Catalyst2Death on 2008-08-22
apologetically, I don't know how to regenerate sources.list for apt from the command line, but to do it via the gui:

System>Administration>Software Sources
Check the appropriate ones, probably everything except source code.  Then choose a mirror.  Go to Third-party Software, and uncheck all of these (unless your sure that they're working)

Then select close and reload, and it should be gold.  Otherwise do it again, select revert and then close and reload.

Hope this works!

---

### Post by Pandyrenim on 2008-09-03
I still haven't been able to figure this problem out. its still giving me the same error message and i don't see any of that in my list.

------------------------------------------------------------------
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I don't know what do to :confused:

---

### Post by Pandyrenim on 2008-09-03
Still Need Help!:(

---

