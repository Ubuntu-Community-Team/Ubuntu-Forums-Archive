---
title: "No Internet.  Can I benifit from the repositories?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Buttons840 on 2009-04-26
A friend of mine doesn't have an Internet connection at his house.  He's been trying Ubuntu (9.04), but wants to download some new programs for it.

In Windows, I could download a installation file, put it on a CD or USB stick and he could take it and install it at his house.  Can a similar thing be done with Ubuntu?

Specifically, how can we obtain compiz (and a few other programs) and all their dependencies from the repositories and then install them on his computer, which doesn't have Internet access?

Thank you.

EDIT:

New question:
Our goal is to obtain a program and all it's dependencies.  Like a Windows installer, we want to be able to go to any Linux (or at least any Ubuntu) machine and have everything we need to install the program without needing the Internet.

My friend is frustrated because everything is so Internet dependent.  We go through a complex process to get a program installed on one computer using the Internet, and then we have to go through the same process again for the second computer, again depending on the Internet.  Is it possible to just obtain the program and be able to install it on any computer and any configuration we encounter?  If this is not possible in Ubuntu, then is there another Linux distro that is more Internet independent?

---

### Post by cariboo on 2009-04-26
Compiz is installed by default, for other packages go [here]("http://packages.ubuntu.com/").

---

### Post by Partyboi2 on 2009-04-26
You could also use [[COLOR=Blue]keryx[/COLOR]]("http://keryxproject.org/"), which saves you having to manually download the dependencies.

---

### Post by Buttons840 on 2009-04-26
Thank you.  But my general question still remains.

How can I transfer something from the repositories onto a computer that cannot connect to the Internet?  Is this possible?

---

### Post by mcduck on 2009-04-26
> **Buttons840 said:**
> Thank you.  But my general question still remains.

How can I transfer something from the repositories onto a computer that cannot connect to the Internet?  Is this possible?

It was already answered by cariboo907.. ;)

Al the packages can be downloaded from [http://packages.ubuntu.com]("http://packages.ubuntu.com"). The real problem is solving dependencies, as the package manager won't be able to help you there without having Internet connection to get information about available packages.

---

### Post by EXCiD3 on 2009-04-26
[Keryx]("http://keryxproject.org") does the same thing as going to [http://packages.ubuntu.com](http://packages.ubuntu.com) only its MUCH easier. It's like using Synaptic on any machine but getting the files for the offline ones. You should check it out.

---

### Post by apparle on 2009-04-26
Your friend is lucky at least he knows someone who has a friend with ubuntu and net connection.
There are many options.
Run the command
```
tar -czf package.tgz /var/lib/apt/lists /var/cache/apt/pkgcache.bin /etc/apt/sources.list
```
then take the packages.tgz to the friends computer. Goto the directory where packages.tgz is located and
```
tar -C / -xzf package.tgz
```
you will have to repeat the above procedure whenever the repositories are updated 

Now all the packges which you have installed are in the directory
/var/cache/apt/archives
Copy the direcoty to friends computer and then install from synaptic. That will be installed.

In case your friend wants to install something which not installed on your PC then goto this link
[http://ubuntuforums.org/showthread.php?t=310020](http://ubuntuforums.org/showthread.php?t=310020)

---

### Post by Buttons840 on 2009-05-07
The problem is we want to *have* the programs, not just *install* them.  In Windows, you can obtain a program, put it on a CD, and use this same CD to install on any Windows computer you encounter.

We want to obtain program x (for example) and put it on a disk, then be able to take this disk and install program x on any Linux (or at least any Ubuntu) machine we encounter.

Let me put it another way.  So far there have been several *specific* solutions offered, but we are looking for a *comprehensive* solution that will work for many computers, not just one specific computer and configuration.

I guess I should have been more clear in my OP.

Thanks again.

---

### Post by Partyboi2 on 2009-05-07
Maybe [[COLOR=Blue]aptoncd[/COLOR]]("http://aptoncd.sourceforge.net/") might be better suited for your needs.

---

### Post by HyRax on 2009-05-07
AptOnCD for a typical installed machine is a much better solution than downloading packages one by one. Take an Internet connected PC, install the relevant apps you want, then run AptOnCD to backup all the cached downloads including dependencies, then restore that cache to the non-connected PC and install away as though you were connected to the Internet.

Another solution is to take a complete mirror of the Ubuntu repositories so you can have them handy on a HDD to install whatever you want whenever you want, and the only thing you'll be missing is on-going updates (unless you bring the mirrored data back to an Internet connection to update it every so often). Your PC won't know the difference - it will think it's getting the files from the Internet anyway.

A complete mirror of Ubuntu Jaunty 9.04 for both 32-bit and 64-bit architectures is 33GB. Ongoing updates are worth about 1-3GB per week.

Obviously getting a complete mirror means that you are also going to copy a lot of data that you will probably never use, but the convenience of having a mirror cannot be understated.

---

### Post by Buttons840 on 2009-05-07
A complete mirror huh?  My friend would like that option.

However, I ain't downloading it on my connection, I have bandwidth caps. :(

So this AptOnCD, it include **_all_** needed dependencies?

---

### Post by HyRax on 2009-05-07
> **Buttons840 said:**
> A complete mirror huh?  My friend would like that option.

However, I ain't downloading it on my connection, I have bandwidth caps. :(

So this AptOnCD, it include **_all_** needed dependencies?

Yes, because it backs up the cache of the Internet-connected PC that you originally installed it on, ie: if you installed say CompizConfig-Settings-Manager, there are some Python-related dependencies required in order to make it run, so Synaptic goes and installs them. When you tun AptOnCD and backup that cache, it will backup not only the main CompizConfig-Settings-Manager package, but also the othe Python packages too because they're sitting there in the cache too.

The only time AptOnCD will not work properly is if the cache contains old packages that have since been replaced with NEW packages, or if the cache on that PC has been cleared recently, so when making an AptOnCD cache, do it with a freshly installed PC (a virtual machine is perfect for this).

Going back to the mirror, if you don't want to download 33GB or so because of download limits, consider sites like [On-Disk](http://on-disk.com/product_info.php/cPath/28_257_174/products_id/644) who can sell you a copy (and mail it out to you) of a snapshot of the entire Ubuntu repository on about 4 dual-layer DVD's (for one architecture only, ie: 32-bit or 64-bit) for about USD$34. Ubuntu will then happily say "Please insert On-Disc Ubuntu Repository Disc Number 3" or something when you are installing software. I used to use these guys for awhile before I found some Internet access to generate my own mirror and I've been maintaining it ever since.

Alternatively again, see if someone near you who already has a full mirror is willing to Sneakernet you a copy if you mail them a hard-drive or a large USB flash memory stick and some cash to cover postage and their time. I've done this for several people in Australia before (but not internationally).

---

