---
title: "Failed 8.10 -&gt; 9.04 Server Upgrade"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Scottie_ on 2009-06-16
Decided to upgrade a server at home from 8.10 to 9.04 tonight and it seems I've hit a snag.

The do-release-upgrade exec has a problem upgrading a package. Its got itself stuck on a Perl CPAN library I've installed myself which is apparently missing a function causing the upgrader it to throw an error.

```
root@aslan:~# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'jaunty.tar.gz'
authenticate 'jaunty.tar.gz' against 'jaunty.tar.gz.gpg'

.... etc etc etc ....

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-server
Errors were encountered while processing:
 libxml-sax-expat-perl

Could not install the upgrades

The upgrade is now aborted. Your system could be in an unusable
state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bug report.
E:Sub-process /usr/bin/dpkg returned an error code (1)

Setting up libxml-sax-expat-perl (0.40-1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::Expat with priority 50...
Fatal: cannot call XML::SAX->save_parsers_debian().
You probably have a locally installed XML::SAX module.
See /usr/share/doc/libxml-sax-perl/README.Debian.gz .
dpkg: error processing libxml-sax-expat-perl (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libxml-sax-expat-perl

Upgrade complete

The upgrade is completed but there were errors during the upgrade
process.


Could not install the upgrades

The upgrade is now aborted. Your system could be in an unusable
state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bug report.
installArchives() failed

Setting up libxml-sax-expat-perl (0.40-1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::Expat with priority 50...
Fatal: cannot call XML::SAX->save_parsers_debian().
You probably have a locally installed XML::SAX module.
See /usr/share/doc/libxml-sax-perl/README.Debian.gz .
dpkg: error processing libxml-sax-expat-perl (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libxml-sax-expat-perl

Upgrade complete

The upgrade is completed but there were errors during the upgrade
process.

root@aslan:~# do-release-upgrade
Checking for a new ubuntu release
No new release found

```I'm wondering if I do manage to fix that package (and i assume all the other CPAN packages that have been upgraded manually) would it be possible to resume the upgrade. If so how would i go about it? If not, is there anyway to recover the OS or is it best to just reinstall?

---

