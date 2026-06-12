---
title: "want to print a list of installed packages (as backup)"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by bishman on 2009-05-13
Hi all

I was wanting to print a list of all installed packages to print out so that, if I do a clean install, I can highlight what applications I had on the system.

I notice 'dpkg -l' will list in terminal - but how do I get dpkg -l to print to file?

Thanks

---

### Post by sjuranic on 2009-05-13
If you're using "bash" as your shell (or any of the Bourne shell variants: ksh, zsh, ash, etc), just do:

dpkg -l > packages.list

This will store all of your package selections in the file named "packages.list"

Also of interest to you is section 3.6 of the Bash info page (do "info bash", then look in the index via the "i" command and type "redirections").

Have fun.

---

### Post by sjuranic on 2009-05-13
Forgot to mention, if you're using a C-shell variant, things are a little trickier.  C-shell historically didn't support I/O redirects.  So it might be easier just to switch to bash, even if it is just for this one command.

---

### Post by lovinglinux on 2009-05-13
Follow this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

---

### Post by bishman on 2009-05-13
Thanks you both for your help - thats perfect.

lovinglinux, If I follow your instructions, will apt-get sort any packages dependencies / obsolutes that might not be needed after upgrading. Or will it just replicate the package list...

I should mention that I am upgrading 8.10 - 9.04. Thanks

---

### Post by lovinglinux on 2009-05-14
> **bishman said:**
> Thanks you both for your help - thats perfect.

lovinglinux, If I follow your instructions, will apt-get sort any packages dependencies / obsolutes that might not be needed after upgrading. Or will it just replicate the package list...

I should mention that I am upgrading 8.10 - 9.04. Thanks

That's a good question. It will sort dependencies, but I'm not sure about obsoletes. For instance, it installed Python 2.5 on my machine along with Python 2.6 (which is the default on Jaunty). Python 2.5 was not entirely obsolete, because 3 applications still depended on it, but my machine's overall performance was improved after removing it.

---

### Post by sjuranic on 2009-05-14
> **bishman said:**
> Thanks you both for your help - thats perfect.

lovinglinux, If I follow your instructions, will apt-get sort any packages dependencies / obsolutes that might not be needed after upgrading. Or will it just replicate the package list...

I should mention that I am upgrading 8.10 - 9.04. Thanks
Is there some reason that using "apt-get dist-upgrade" isn't working for you?

---

### Post by bishman on 2009-05-15
I am performing a clean install from cd for a couple of reasons, mainly a bandwidth usage issue.

However, I am now on the other side of it and all seems well. Other than that my mouse's clicking will occasionally stop working and I can't do alt-tab on the keyboard - only alt-f4 to quit (this is all the one issue btw) but these only happen occasionly and I have faith they will fix in a future update.

Thanks for your help!

---

