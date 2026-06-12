---
title: "apt-get upgrade and errors in ghostscript"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by mohnkern on 2009-04-21
I recently did an sudo apt-get update; sudo apt-get upgrade, and it threw a ton of errors, all seeming to stem from problems upgrading ghostscript.  It told me it couldn't configure it so I did a:

dpkg --configure ghostscript

and got the following error:

root@Casa-Scott:/fs/shared# dpkg --configure ghostscript
Setting up ghostscript (8.63.dfsg.1-0ubuntu6.4) ...
Can't locate File/Copy.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/bin/defoma-subst line 7.
BEGIN failed--compilation aborted at /usr/bin/defoma-subst line 7.
Can't locate File/Copy.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/bin/defoma-subst line 7.
BEGIN failed--compilation aborted at /usr/bin/defoma-subst line 7.
dpkg: error processing ghostscript (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ghostscript

I can't even run cpan:

Can't locate File/Basename.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/CPAN/Tarzip.pm line 6.
BEGIN failed--compilation aborted at /usr/share/perl/5.10/CPAN/Tarzip.pm line 6.
Compilation failed in require at /usr/share/perl/5.10/CPAN.pm line 11.
BEGIN failed--compilation aborted at /usr/share/perl/5.10/CPAN.pm line 11.
Compilation failed in require at /usr/local/bin/cpan line 175.
BEGIN failed--compilation aborted at /usr/local/bin/cpan line 175.

doing an apt-get remove perl is going to cause a mess and a boatload of dependency issues.  Is there an alternative way to fix this?

---

