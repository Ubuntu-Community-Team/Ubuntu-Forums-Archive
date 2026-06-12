---
title: "OpenOffice APT error when upgrading from 8.04 to 8.10"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by naurus on 2009-05-18
Hello All!
I am trying to upgrade from Ubuntu 8.04 to 9.04, and taking the intermediate step of first upgrading to 8.10. The upgrade process goes smoothly until this:

> Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-help-en-gb_1%3a2.4.1-9ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I think I've seen errors thrown by package names with percent signs in them before, but I'm not sure.

Does anybody have have a clue why this won't work? If nobody does, is there a way to rollback the changes that were made to my system before this error? Either solution would be GREAT!

Thank you :)
Naurus

---

### Post by ptn107 on 2009-05-18
The filename[1] should be 'openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb', why it's using '1%3a' in the filename I don't know.  Do the following:
```
sudo mv /var/cache/apt/archives/openoffice.org-help-en-gb_1%3a2.4.1-9ubuntu1_all.deb /var/cache/apt/archives/openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb
```
and try updating again.

Here's a direct link to the file if you want to try and manually download it and move it to '/var/cache/apt/archives/':
[_openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb_]("http://mirrors.kernel.org/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb")

---

### Post by naurus on 2009-05-18
Thanks, that worked perfectly :)

> **ptn107 said:**
> The filename[1] should be 'openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb', why it's using '1%3a' in the filename I don't know.  Do the following:
```
sudo mv /var/cache/apt/archives/openoffice.org-help-en-gb_1%3a2.4.1-9ubuntu1_all.deb /var/cache/apt/archives/openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb
```
and try updating again.

Here's a direct link to the file if you want to try and manually download it and move it to '/var/cache/apt/archives/':
[_openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb_]("http://mirrors.kernel.org/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-en-gb_2.4.1-9ubuntu1_all.deb")

---

