---
title: "perl, mod_perl problems"
date: 2008-09-29
forum: General Help
---

### Post by meburke on 2008-09-29
OK, interesting problem: I seem to have perl, mod_perl, and apache2 installed so that they work, but I cannot get perl or cgi to work through the website.

cgi is enabled, so is perl.

I believe this is a configuration problem, but I'm having trouble figuring out how to troubleshoot it. No significant messages show up in the tail of /var/log/apache2/error.log.

My httpd.conf has:

PerlModule ModPerl::Registry

ScriptAlias /perl var/www/perl/

<Location "/perl/">
 SetHandler perl-script
 PerlHandler ModPerl::Registry
 Options +ExecCGI
</Location>

and I do have a perl directory in /var/www/perl with a couple of small test scripts. However, connecting to the url [http://XXX.XXX.XXX.XXX/perl/mperltest.pl](http://XXX.XXX.XXX.XXX/perl/mperltest.pl) gives me a message saying the url cannot be found on the server. I thought the "/perl/" in the config file became a place holder for the url. Am I misunderstanding this?

My goal is to run perl scripts through the website. Once I get mod_perl working I expect to install mason, but at this point I would be very happy jsut being able to run perl scripts from the cgi-bin and/or the test directory I created under /var/www.

Any help would be appreciated.

Thanks,

Mike

---

