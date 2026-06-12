---
title: "Problems installing Boxee"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by flyingmonkiesiscool on 2009-04-04
I'm having an incredible amount of problems installing Boxee on Ubuntu Intrepid Ibex 8.10. When I added the boxee repo 
```
deb http://apt.boxee.tv intrepid main
```
I was unable to download it because it could not find the pubkey/GPG/whatever. I was finally able to fix the problem, but when I ran 
```
sudo apt-get update
```
I got the following error:
```
W: Failed to fetch http://apt.boxee.tv/dists/intepid/main/binary-i386/Packages.gz  404 Not Found

```
After a Google search, I found out that this is a problem with *every* Boxee release. Packages.gz is supposed to redirect, I think. However, what it redirects to changes with every version. What is the .deb file I am supposed to download?

Thanks.

---

### Post by Partyboi2 on 2009-04-04
You could try  manually installing the boxee deb package. You can download the deb package from [[COLOR=Blue]here[/COLOR]]("http://apt.boxee.tv/dists/intrepid/m...8.intrepid.deb") and double click to install.

---

### Post by SDNick484 on 2009-04-06
I [wrote a script]("http://forum.boxee.tv/showthread.php?t=7497") which allows you to compile and install the latest Boxee from source on 8.10 (works on both i686 & amd64).  Post 14 indicates it works on Jaunty as well although personally I haven't given it a go.

---

