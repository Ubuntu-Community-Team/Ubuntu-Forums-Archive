---
title: "gnome-app-install can't update"
date: 2008-07-21
forum: General Help
---

### Post by Hatch3r on 2008-07-21
I  hate having to make my first post a cry for help but this is giving me an endless headache at the moment!

Running " sudo apt-get upgrade " from the command line finds one package that needs to the be upgraded, gnome-app-install.
However, it returns this error message before completion:
```
(Reading database ... 
dpkg: serious warning: files list file for package `binfmt-support' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `jockey-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-accessibility-themes' missing, assuming package has no files currently installed.
164693 files and directories currently installed.)
Preparing to replace gnome-app-install 0.5.2.7-0ubuntu1 (using .../gnome-app-install_0.5.2.8-0ubuntu1_all.deb) ...
Unpacking replacement gnome-app-install ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/gnome-app-install_0.5.2.8-0ubuntu1_all.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-app-install_0.5.2.8-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried removing and purging with no luck. Any ideas greatly appreciated!

Thanks
Hatch3r

---

### Post by ercferret18 on 2008-07-21
maybe try installing binfmt-support, jockey-common, and gnome-accessibility-themes packages... see if that works

---

### Post by Hatch3r on 2008-07-21
Tried to install binfmt-support (sudo apt-get install binfmt-support) and that didn't work, generated this error:
```
(Reading database ... 
dpkg: serious warning: files list file for package `binfmt-support' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `jockey-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-accessibility-themes' missing, assuming package has no files currently installed.
164693 files and directories currently installed.)
Preparing to replace gnome-app-install 0.5.2.7-0ubuntu1 (using .../gnome-app-install_0.5.2.7-0ubuntu1_all.deb) ...
Unpacking replacement gnome-app-install ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: warning - unable to delete old directory `/usr/lib/python2.5/site-packages/gnome_app_install-0.5.2.8_0ubuntu1-py2.5.egg-info': Directory not empty
dpkg: error processing /var/cache/apt/archives/gnome-app-install_0.5.2.7-0ubuntu1_all.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-app-install_0.5.2.7-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This happened with the other 2 you suggested as well, same error message each time (but with the respective package).

Thanks for the prompt reply.
Hatch3r

---

### Post by drs305 on 2008-07-21
You probably have corrupted files in /var/lib/dpkg/info. 

**Option 1:**

Start by running this to try to restore the corrupted info file:
```
sudo aptitude download gnome-app-install
```
Then:
```

sudo dpkg -i /*path.to.download.location*/gnome-app-install_0.5.2.8-0ubuntu1_all.deb

```

That will update the files. Hopefully this will clear all the errors and you won't have to run this for each package.

**Option 2:**
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-bad
gksu gedit /var/lib/dpkg/status

```

Find the gnome-app-install line and change the status to:
"purge ok not-installed"

---

### Post by Hatch3r on 2008-07-21
Ok, I tried Option 1 and it returned the same error message as I first posted up.
So I moved on to Option 2 and the first command generated an error message about /var/lib/dpkg/status-bad not being a directory. However, I'm at the point where it's kill or cure so I went with the second command (I presumed the first one was just to backup the status file) and after running the second command editing the file as specified. "sudo apt-get upgrade" and "aptitude install gn..." all return this error message:
```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6704 package `gnome-app-install':
 Configured-Version for package with inappropriate Status

```

Thanks again :-)

---

### Post by drs305 on 2008-07-21
Sorry it didn't work. The first error was due to  a cut/paste error on my part which I've fixed. In the second section, I believe you have to delete the remainder of the section below the status line... Make a backup copy first.

If the status indicates:
Status: install ok installed

then the problem isn't with the status file although there must still be something in the info files that isn't correct.

---

### Post by Hatch3r on 2008-07-24
The status file does not indicate "install ok installed" it reads: "install reinstreq half-installed"

So, I'm still at exactly the same problem unfortunately. Has anyone got any more suggestions?

Thanks

---

### Post by drs305 on 2008-07-24
> **Hatch3r said:**
> The status file does not indicate "install ok installed" it reads: "install reinstreq half-installed"

So, I'm still at exactly the same problem unfortunately. Has anyone got any more suggestions?

Thanks

My next recommendation would be to back up the file and change the status to deinstall. I'd try it this way:

Create a list of installed packages:
```
sudo dpkg --get-selections >~/Desktop/package-list
```
Edit the list, removing any reference to the troublesome apps/package(s):
```
gksudo gedit ~/Desktop/package-list
```
Save, then:
```
sudo dpkg --set-selections <~/Desktop/package-list
sudo apt-get update
sudo apt-get dselect-upgrade

```

After this I've run out of suggestions.

---

### Post by Hatch3r on 2008-07-27
Dammit, good try unfortunately still got exactly the same problem.
Thanks for the suggestions. Anyone care to take up the challenge?

Thanks
Hatch3r

---

