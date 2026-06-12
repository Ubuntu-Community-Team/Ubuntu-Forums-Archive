---
title: "Problems upgrading perl modules via CPAN"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by xxsegfaultxx on 2009-06-24
Hi all.

I recently upgraded my workstation from 7.10 - > 8.04 -> 8.10 -> 9.04. After I completed this a went on my merry way and everything was working perfectly.

Today, I started working on a perl script that would require a module for SQLite. I fired up cpan and ran upgrade. Things started off normal but then I started to get errors. I'm not sure if something got out of sync or what. 

Here's the output from CPAN. I googled a bit but found nothing that seemed similar. Anyone point me in the right direction?

```
Appending installation info to /usr/lib/perl/5.10/perllocal.pod
  KANE/CPANPLUS-0.84.tar.gz
  /usr/bin/make install  -- OK
CPANPLUS::Internals::Constants is up to date (0.01).
CPANPLUS::Internals::Constants::Report is up to date (0.01).
Running install for module 'Carp'
The most recent version "1.10" of the module "Carp"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Carp   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'DBM_Filter::compress'
The most recent version "0.02" of the module "DBM_Filter::compress"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install DBM_Filter::compress   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'DBM_Filter::encode'
The most recent version "0.02" of the module "DBM_Filter::encode"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install DBM_Filter::encode   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'DBM_Filter::int32'
The most recent version "0.02" of the module "DBM_Filter::int32"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install DBM_Filter::int32   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'DBM_Filter::null'
The most recent version "0.02" of the module "DBM_Filter::null"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install DBM_Filter::null   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'DBM_Filter::utf8'
The most recent version "0.02" of the module "DBM_Filter::utf8"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install DBM_Filter::utf8   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'DirHandle'
The most recent version "1.02" of the module "DirHandle"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install DirHandle   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'File::Basename'
The most recent version "2.77" of the module "File::Basename"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install File::Basename   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'File::CheckTree'
The most recent version "4.4" of the module "File::CheckTree"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install File::CheckTree   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'File::Copy'
The most recent version "2.13" of the module "File::Copy"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install File::Copy   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'File::DosGlob'
The most recent version "1.01" of the module "File::DosGlob"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install File::DosGlob   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'File::Find'
The most recent version "1.13" of the module "File::Find"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install File::Find   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'File::stat'
The most recent version "1.01" of the module "File::stat"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install File::stat   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'GDBM_File'
The most recent version "1.09" of the module "GDBM_File"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install GDBM_File   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'Getopt::Std'
The most recent version "1.06" of the module "Getopt::Std"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Getopt::Std   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'IPC::Open2'
The most recent version "1.03" of the module "IPC::Open2"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install IPC::Open2   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'IPC::Open3'
The most recent version "1.03" of the module "IPC::Open3"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install IPC::Open3   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'O'
The most recent version "1.01" of the module "O"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install O   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'POSIX'
The most recent version "1.15" of the module "POSIX"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install POSIX   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'PerlIO'
The most recent version "1.05" of the module "PerlIO"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install PerlIO   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'PerlIO::encoding'
The most recent version "0.11" of the module "PerlIO::encoding"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install PerlIO::encoding   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'PerlIO::scalar'
The most recent version "0.06" of the module "PerlIO::scalar"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install PerlIO::scalar   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'PerlIO::via'
The most recent version "0.05" of the module "PerlIO::via"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install PerlIO::via   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'Pod::Html'
The most recent version "1.09" of the module "Pod::Html"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Pod::Html   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'Socket'
The most recent version "1.81" of the module "Socket"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Socket   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'Tie::Handle'
The most recent version "4.2" of the module "Tie::Handle"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Tie::Handle   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'Tie::Hash'
The most recent version "1.03" of the module "Tie::Hash"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Tie::Hash   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'Tie::Scalar'
The most recent version "1.01" of the module "Tie::Scalar"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Tie::Scalar   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'Tie::StdHandle'
The most recent version "4.2" of the module "Tie::StdHandle"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install Tie::StdHandle   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'attributes'
The most recent version "0.09" of the module "attributes"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install attributes   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'blib'
The most recent version "1.04" of the module "blib"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install blib   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'ops'
The most recent version "1.02" of the module "ops"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install ops   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 CAPTTOFU/DBD-mysql-4.011.tar.gz              : make_test NO
 PMQS/DB_File-1.820.tar.gz                    : make NO
 CDENT/Purple/Purple-1.0.tar.gz               : make_test NO
 NWCLARK/perl-5.8.9.tar.gz                    : make NO isa perl
```

---

### Post by Beatbreaker on 2009-07-13
I've got the same errors, i'm installing perl for different reasons but i'll run this output

```
The most recent version "1.15" of the module "POSIX"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install POSIX   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz

```

and i don't know what to type to force the instilation of POSIX and other programs in that list, i'm sure it's pretty simple but the output doesn't explain it very well

---

### Post by x86-64-Scotland on 2012-01-20
> **Beatbreaker said:**
> I've got the same errors, i'm installing perl for different reasons but i'll run this output

```
The most recent version "1.15" of the module "POSIX"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install POSIX   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz

```

and i don't know what to type to force the instilation of POSIX and other programs in that list, i'm sure it's pretty simple but the output doesn't explain it very well

It can't be made much clearer, it says:

```
the module "POSIX"
is part of the perl-5.8.9 distribution. To install that, you need to run
  force install POSIX   --or--
  install N/NW/NWCLARK/perl-5.8.9.tar.gz
```
So:

force install POSIX

from within cpan

---

