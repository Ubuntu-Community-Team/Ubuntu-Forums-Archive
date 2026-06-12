---
title: "Installing Perl's XML::Xerces on Ubuntu x86_64"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Rhiknow on 2009-01-20
For the record...

Pain in the butt to install XML::Xerces, version 2.7.0 ([http://search.cpan.org/dist/XML-Xerces/](http://search.cpan.org/dist/XML-Xerces/)).

first:
sudo apt-get install libxerces27

then:
Install [http://search.cpan.org/CPAN/authors/id/J/JA/JASONS/XML-Xerces-2.7.0-0.tar.gz](http://search.cpan.org/CPAN/authors/id/J/JA/JASONS/XML-Xerces-2.7.0-0.tar.gz)

then:
export XERCESCROOT=/usr

then:
You then need to modify the Makefile.PL by applying the following diff:

```
<   $XERCES_CONFIG = "$XERCESCROOT/src/xercesc/$config_file";
---
>   $XERCES_CONFIG = "$XERCESCROOT/lib/libxerces27/$config_file";
```

Once all this is done:
perl Makefile.PL
make
make test
make install
make cleann
(as usual)

You then should edit your ~/.bashrc and append LD_LIBRARY_PATH and PERL5LIB (again, as usual).

---

### Post by cariboo on 2009-01-20
If you run [cpan]("http://www.cpan.org/") in a terminal as root you wouldn't have had to go to all that trouble. Once you have configured cpan at the cpan prompt type:

```
install XML::Xeces
```

and cpan will take care of downloading, compiling and installing perl modules.

Cpan is installed by default in Ubunutu.

Jim

---

