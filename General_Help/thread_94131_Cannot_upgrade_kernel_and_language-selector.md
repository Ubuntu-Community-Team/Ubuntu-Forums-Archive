---
title: "Cannot upgrade kernel and language-selector"
date: 2005-11-23
forum: General Help
---

### Post by CArenas2 on 2005-11-23
i am unable to install the following new packages:
[LIST]
[*]linux-image-2.6.12-10-386
[*]linux-restricted-modules-common
[*]language-selector
[/LIST]

this is the transcript of what occurs when trying to use apt-get:
```

root@nomada:~ # apt-get -y dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be upgraded:
  language-selector linux-image-2.6.12-10-386 linux-restricted-modules-common
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/18.1MB of archives.
After unpacking 52.6MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `linux-image-2.6.12-10-386' missing, assuming package has no files currently installed.
80901 files and directories currently installed.)
Preparing to replace language-selector 0.1 (using .../language-selector_0.1.1_all.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Permission denied
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/language-selector_0.1.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Permission denied
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Preparing to replace linux-image-2.6.12-10-386 2.6.12-10.24 (using .../linux-image-2.6.12-10-386_2.6.12-10.24_i386.deb) ...
dpkg (subprocess): unable to execute new pre-installation script: Permission denied
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.24_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace linux-restricted-modules-common 2.6.12.4-11 (using .../linux-restricted-modules-common_2.6.12.4-11.1_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-common_2.6.12.4-11.1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/language-selector_0.1.1_all.deb
 /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.24_i386.deb
 /var/cache/apt/archives/linux-restricted-modules-common_2.6.12.4-11.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

can someone please explain to me why this is happening?  thanks!

---

### Post by chintan_agarwal on 2006-03-12
I get :
E: Couldn't find package language-selector
Any help?
Thanks

---

### Post by mempf on 2006-03-12
Add sudo infornt of your apt-get line

---

### Post by chintan_agarwal on 2006-03-13
I had earlier tried with sudo added. The package does not seem to appear in Synaptic also. Is there any other way to download language-selector?
Thanks.

---

### Post by bjweeks on 2006-03-13
[QUOTE=chintan_agarwal]I had earlier tried with sudo added. The package does not seem to appear in Synaptic also. Is there any other way to download language-selector?
Thanks.[/QUOTE]

Try...

> sudo apt-get update
            sudo apt-get dist-upgrade

---

### Post by chintan_agarwal on 2006-03-15
No luck. Still the same situation. The package does not even exist in the live CD.(I booted from the live CD and in the System-->Administration, I could not find any language-selector option.In fact I could not find it in any of the menus) Even synaptic of Live CD does not have it.
Is this(language-selector) an add on package(i.e. is it installed during upgrades/updates)? If so, is it possible that the firewall(word based) of my institution blocks me from getting the necessary files?
Thanks.

---

