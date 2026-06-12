---
title: "Open Office 3"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by KingAlanI on 2009-02-03
Okay, how do you upgrade from OO 2.4 to OO 3.0 (or whatever the latest version is)

sudo apt-get install $foo

What is the package name?

---

### Post by howefield on 2009-02-03
Add the repository and it'll do it almost by itself...

Instructions here

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by cyfur01 on 2009-02-03
Check out [this link]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml").

Edit:
I have to laugh, seeing how many people have said the same thing at once. A general tip for figuring out how to install anything in Ubuntu is to Google "ubuntu <program name>" or "apt-get <program name>". Doesn't always work, but my guess is that's how we all came up with this solution.

---

### Post by matt79 on 2009-02-03
Try this link: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
I see that we all found the same link :-)

---

### Post by ginnie6 on 2009-02-03
will this work on 8.04?

---

### Post by cyfur01 on 2009-02-03
I assume yes, if you change
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
to ```

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main

```


Otherwise you can try [this page]("http://ubuntuhelptipstricks.blogspot.com/2008/10/setting-up-openoffice-3-on-ubuntu-hardy.html") as an alternative if necessary.

---

### Post by morthrai08 on 2009-02-08
Isn't it great how I found this thread 20 minutes after I downloaded the entire ooo3 file from their website! :P Anyway, as an absolute beginner with Intrepid how do I get the tarball to install?

---

### Post by cyfur01 on 2009-02-08
I strongly recommend using the repos instead of installing from source. The repos automate the installation, upgrading and uninstallation (should you chose) of the whole suite, which in the long run will make things easier.

If you insist on installing from the tarball, extract the tarball (from a file browser, right-click and Extract Here, which should create a folder), then see if the folder includes a README or INSTALL file, or something similar about how to install things from source.

---

### Post by KingAlanI on 2009-02-11
Does OO 3.0 reside along OO 2.4, or does it replace it like other upgrades?

my university's wi-fi is intermittent for me [that's another issue, another thread]...so next time I feel like a computer-maintenance session, I may want to install this at home where I'm 5ft away from the router. (heck, I could even plug in Ethernet by that point.)

When using my Linux machine, I do sometimes want to read .docx and .xlsx without having to find a Windows box (the Windows boxen I have access to are all on Office 2007, helping accelerate my accumulation of OOXML documents)

yeah, I first tried to type in several sensible-sounding package names, which didn't work, so I'm not surprised there's this different method.

---

### Post by bgenc on 2009-02-12
Installing 3.0 is sort of trivial. Just add the repositories to your software sources and you are done.

Let me ask the more difficult question: How do I install the 3.1 alpha?

I got the DEBs from the mirror but I am not sure whether I need to uninstall 3.0 first. Will 3.0 and 3.1 live together peacefully? Did anybody try 3.1 so far?

---

### Post by bgenc on 2009-02-12
Ok, I got brave and installed the m41 build on top of my OOo3.0 installation. Well, it is not really an "on top of" issue. The dev build goes under the /opt/ directory and doesn't interfere with the stable 3.0 build. I will be testing it now. But it seems to work fine.

---

### Post by KingAlanI on 2009-02-12
Am trying this, the "softpedia" method.

It looks like I'm doing everything as per the instructions, but I get this from the Software Sources tool:

"
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/heron/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/heron/main/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
"

I have an Intel X86 chip; I got Ubuntu onto this machine via Wubi; Wubi set up as amd64.

---

### Post by ottosykora on 2009-02-13
I tried to install oo3 to 8.04 system, it seems it does not like it. It claims I have to upgrade to 8.10 first. However on that particular hardware, 8.10 will not run at all.

Is there then any way to update oo from 2.4 to oo3 on 8.04?

---

### Post by KingAlanI on 2009-02-16
I, too, am on 8.04

I downloaded the .tar.gz

Exploring the archive, I don't see obvious installation instructions.
I'll try adding the repo again...

---

