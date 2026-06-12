---
title: "apt update always failing on translation-en_CA"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-01-17
I have 8.10 and when I do an update or repo source update, the fetching for tranlsation-en_CA are mostly failing no matter what repo server I use. 

Its only those specific fetching that fail.

What is this translation-en_CA ?

Where did this come from since most of those repo don't have this thing ?

Why are they often failing (been that way for months).

How can I fix it ?

- All other updates are always working. 
- I never have internet problems (extream high speed cable). 
- My connection is always working ok.
- NO matter which server I choose in the System/Administration/Software Sources menu (even if I tell it to pick the fastest one or even if I pick the Main Server one), those fetchings are the one that mostly fail

On the Software Sources Reload, they mostly show as Failed (no screenshots available).

> From console:
> sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Reading package lists... Done


---

### Post by Partyboi2 on 2009-01-17
I Only see ign in that output, which happen all the time. Ign mean that you have already the file and that it does not need to fetch it again.

---

