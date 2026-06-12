---
title: "I've deleted an installation file by rm -r ... what to do to fix the re-installation"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by soha on 2009-06-13
Hello all,

 i'm a non professional user of Ubuntu. i've just installed 9.04.
i've insalled as well the Acrobat reader 9.1 using the .deb installer. but after installation i found it was a deutsh version. 

i've tried to uninstall it using "sudo apt-get remove acroread" but i've received an error msg saying that the package does not exist.

i've tried to use another option which is" cd /opt/Adobe/Reader9/bin && sudo ./UNINSTALL" but also i've received another error msg saying UNINSTALL no such file or directory

i've tried to install the english version over the existing one, but nothing happened and the deutsh display remains the same.

when i fed up, i've made a dump action which is removing the installation directory of Adobe by rm -r ... and of course that's wrong, and now i can't install the other english edition.

Any suggestions ..???
thanks in advance
soha

---

### Post by ajgreeny on 2009-06-13
If you installed using the deb installer, you should probably use ```
sudo dpkg purge packagename
```You need to know exactly what the .deb was called but not worry about the version numbers etc etc.  Where idi you get the .deb from, and why did you use that way instead of using synaptic and searching for acroread, which is in the archive.canonical repos (look in the third party tab of System >Admin > Software sources)

If there are problems, you may need to reinstall the package you used first time, then uninstall it properly, and then start again with synaptic.  I don't bother any more with acroread, however, as I find that evince does all I want and more.

---

### Post by soha on 2009-06-13
> **ajgreeny said:**
> If you installed using the deb installer, you should probably use ```
sudo dpkg purge packagename
```You need to know exactly what the .deb was called but not worry about the version numbers etc etc.  Where idi you get the .deb from, and why did you use that way instead of using synaptic and searching for acroread, which is in the archive.canonical repos (look in the third party tab of System >Admin > Software sources)

If there are problems, you may need to reinstall the package you used first time, then uninstall it properly, and then start again with synaptic.  I don't bother any more with acroread, however, as I find that evince does all I want and more.


Thank you ajgreeny, you were of great help .. i've used the 

sudo dpkg - p adobereader-deu  // for purging

and

sudo dpkg -r adobreader-deu  // for removing 

and i've successfully remove it and install the english version.

but i've a question for you:

what is the difference between "sudo apt-get install/remove package_name"  and  "sudo dpkg"? i mean when to use each of them?!!

thank you really for your great help
soha

---

### Post by ajgreeny on 2009-06-13
You use *dpkg* for local .deb files already on your drive, and *apt-get*, (or synaptic or Add/Remove) to download and install from the repositories, it's as simple as that!

---

