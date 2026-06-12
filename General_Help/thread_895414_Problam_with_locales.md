---
title: "Problam with locales"
date: 2008-08-20
forum: General Help
---

### Post by kosc on 2008-08-20
Hi

After installing server 8.04 LTS and installing apt-show-versions I get warning from perl.

Here is list:
---------------------------------------------------
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US.ISO8859-1",
        LC_ALL = "en_US.ISO8859-1",
        LANG = "en_US.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
groff-base/hardy uptodate 1.18.1.1-16
sysv-rc/hardy uptodate 2.86.ds1-14.1ubuntu45
libmysqlclient15off/hardy uptodate 5.0.51a-3ubuntu5.1
libntfs-3g23/hardy uptodate 1:1.2216-1ubuntu2
python2.5-minimal/hardy uptodate 2.5.2-2ubuntu4.1
---------------------------------------------------


"dpkg-reconfigure locales" doesn't help perl still shows warning.
Is there anything else to set to remove warning/fix problem?

---

