---
title: "perl -MCPAN problem"
date: 2005-11-11
forum: General Help
---

### Post by kurgan on 2005-11-11
I'm trying to run the following in order to get the perl modules that Bugzilla needs installed, and it has a make problem at the end:

root@Apollo:/opt/bugzilla-2.20# **/usr/bin/perl -MCPAN -e 'install "PatchReader"'**
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 11 Nov 2005 16:45:04 GMT
Running install for module PatchReader
Running make for J/JK/JKEISER/PatchReader-0.9.5.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/PatchReader-0.9.5.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/PatchReader-0.9.5.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS](ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS)
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS.gz)
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS](ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS)
Couldn't cwd pub/CPAN/authors/id/J/JK/JKEISER at /usr/share/perl/5.8/CPAN.pm line 2260.
Fetching with Net::FTP
  [ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS.gz)
Couldn't fetch CHECKSUMS.gz from ftp.perl.org

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS](ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS)
--17:13:42--  [ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS](ftp://ftp.perl.org/pub/CPAN/authors/id/J/JK/JKEISER/CHECKSUMS)
           => `-'
Resolving ftp.perl.org... 64.186.250.53, 128.121.60.235
Connecting to ftp.perl.org|64.186.250.53|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/CPAN/authors/id/J/JK/JKEISER ... done.
==> PASV ... done.    ==> RETR CHECKSUMS ... done.
Length: 3,223 (3.1K) (unauthoritative)

100%[=================================================================================================>] 3,223         --.--K/s

17:13:42 (157.67 KB/s) - `-' saved [3223]

Checksum for /root/.cpan/sources/authors/id/J/JK/JKEISER/PatchReader-0.9.5.tar.gz ok
Scanning cache /root/.cpan/build for sizes
PatchReader-0.9.5/
PatchReader-0.9.5/lib/
PatchReader-0.9.5/lib/PatchReader/
PatchReader-0.9.5/lib/PatchReader/DiffPrinter/
PatchReader-0.9.5/lib/PatchReader/DiffPrinter/template.pm
PatchReader-0.9.5/lib/PatchReader/DiffPrinter/raw.pm
PatchReader-0.9.5/lib/PatchReader/NarrowPatch.pm
PatchReader-0.9.5/lib/PatchReader/FilterPatch.pm
PatchReader-0.9.5/lib/PatchReader/Base.pm
PatchReader-0.9.5/lib/PatchReader/FixPatchRoot.pm
PatchReader-0.9.5/lib/PatchReader/AddCVSContext.pm
PatchReader-0.9.5/lib/PatchReader/Raw.pm
PatchReader-0.9.5/lib/PatchReader/CVSClient.pm
PatchReader-0.9.5/lib/PatchReader/PatchInfoGrabber.pm
PatchReader-0.9.5/lib/PatchReader.pm
PatchReader-0.9.5/Changes
PatchReader-0.9.5/MANIFEST
PatchReader-0.9.5/META.yml
PatchReader-0.9.5/Makefile.PL
PatchReader-0.9.5/README
PatchReader-0.9.5/t/
PatchReader-0.9.5/t/001use.t

  CPAN.pm: Going to build J/JK/JKEISER/PatchReader-0.9.5.tar.gz

[I]Checking if your kit is complete...
Looks good
Writing Makefile for PatchReader
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible[/I]

What am I missing?  I did the base install and then installed the smp kernel.
Also, One of the packages Mail::Mailer requires a version beyond what the package application says is the latest - how do I deal with that?

Thanks

---

