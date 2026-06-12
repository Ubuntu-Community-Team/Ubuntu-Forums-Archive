---
title: "General - Shell based installer file removal"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by nuke on 2009-04-07
Hi!

This is a general questions and may be in the wrong place.  I'm confused about using a shell based installer and what the package contents look like and how to remove after an install.

We have numerous installs of Ubuntu 8.04 LTS.  We needed Acrobat Reader 9.x installed and at the time we installed, we only found the installer download from Adobe. There was nothing in the repositories.

The installer files was a shell based installer.  There was no .deb files.
 
Now the package is available in the repository, so we would prefer to delete the shell based installer files and install using Synaptic. 

My end goal is to safely remove the installed files from the shell based installer. 

In normal practice, would there be a file list in the .sh installer that indicates where the files should be installed so I can manually delete those files?

I believe that the package was installed in the /opt directory.  If this is the case, and there is nothing else in /opt, can I delete this directory to remove all the files?  The follow-on question is:  Is it normal practice that when you install something into /opt that the files only go there or is there a likelyhood that there are some files in /usr/local/bin?  I realize that this depends on who wrote the installer script, but I hope to be able to read the sh file somehow so I can check this directly.

I googled and searched the forums but didn't find anything that helped.  I appreciate any suggestions on where or how to search for this information so I can learn this better.

Thank you in advance.

---

### Post by scragar on 2009-04-07
Shell based installers can be rather messy, I would assume it's default install location would be /opt with a launcher in /usr/bin
You might also have to remove the menu entry as well.

---

### Post by nuke on 2009-04-07
Thank you.

Is there some way to read the file.sh to see where everything gets installed?  Would gedit or something like that work in a normal circumstance?  Or are these type of files usually a binary? I'm not sure how I would figure it out.

Thanks again!

---

### Post by lloyd_b on 2009-04-07
> **nuke said:**
> Thank you.

Is there some way to read the file.sh to see where everything gets installed?  Would gedit or something like that work in a normal circumstance?  Or are these type of files usually a binary? I'm not sure how I would figure it out.

Thanks again!

With a name like "file.sh", I would expect it to be a shell script, which you can open up in any editor and see what it did.  But it may or may not call a binary to do the actual installation...

Lloyd B.

---

### Post by nuke on 2009-04-07
Thanks for your help.

Now that I am forearmed, I'll start on uninstall road.

I much appreciate everyone's quick replies.

---

