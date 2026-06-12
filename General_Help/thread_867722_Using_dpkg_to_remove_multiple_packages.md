---
title: "Using dpkg to remove multiple packages"
date: 2008-07-23
forum: General Help
---

### Post by smaug42 on 2008-07-23
I have been working through how to use dpkg, and have it figured out for installing single and multiple debs, and can list all installed debs based on a pattern+wildcard

eg :
 dpkg -i foo*.deb to install
 dpkg -l foo* to show all foo_1 to foo_n installed
 dpkg -r foo_1 to remove one package

But... how do I tell dpkg to remove all packages based on a pattern+wildcard?  dpkg -r foo* does not work.  dpkg -l gives too much information so I can't easily redirect to a file and cat the output through dpkg... 

Is there any easy way to use dpkg to remove multiple packages in one step?

---

