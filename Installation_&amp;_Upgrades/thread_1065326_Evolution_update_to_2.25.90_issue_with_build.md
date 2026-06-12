---
title: "Evolution update to 2.25.90 issue with build"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by cheapsaket on 2009-02-09
I am running ubuntu 8.10 and was trying to build the updated evolution 2.25.90.
I was able to build the dependencies fine but during the build of evolution itself, it is failing somewhere trying to build the help files for different languages.
Can someone give tips on how to resolve the issue?

The output from make is below.

/bin/bash ../mkinstalldirs /usr/local/share/omf/evolution
/usr/bin/install -c -m 644 evolution-C.omf /usr/local/share/omf/evolution/evolution-C.omf
/usr/bin/install: cannot stat `evolution-C.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-cs.omf /usr/local/share/omf/evolution/evolution-cs.omf
/usr/bin/install: cannot stat `evolution-cs.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-de.omf /usr/local/share/omf/evolution/evolution-de.omf
/usr/bin/install: cannot stat `evolution-de.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-el.omf /usr/local/share/omf/evolution/evolution-el.omf
/usr/bin/install: cannot stat `evolution-el.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-en_GB.omf /usr/local/share/omf/evolution/evolution-en_GB.omf
/usr/bin/install: cannot stat `evolution-en_GB.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-es.omf /usr/local/share/omf/evolution/evolution-es.omf
/usr/bin/install: cannot stat `evolution-es.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-fr.omf /usr/local/share/omf/evolution/evolution-fr.omf
/usr/bin/install: cannot stat `evolution-fr.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-oc.omf /usr/local/share/omf/evolution/evolution-oc.omf
/usr/bin/install: cannot stat `evolution-oc.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-ru.omf /usr/local/share/omf/evolution/evolution-ru.omf
/usr/bin/install: cannot stat `evolution-ru.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-sv.omf /usr/local/share/omf/evolution/evolution-sv.omf
/usr/bin/install: cannot stat `evolution-sv.omf': No such file or directory
/usr/bin/install -c -m 644 evolution-mk.omf /usr/local/share/omf/evolution/evolution-mk.omf
/usr/bin/install: cannot stat `evolution-mk.omf': No such file or directory
make[3]: *** [install-doc-omf] Error 1
make[3]: Leaving directory `/home/taha/Desktop/evolution-2.25.90/help'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/taha/Desktop/evolution-2.25.90/help'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/taha/Desktop/evolution-2.25.90/help'
make: *** [install-recursive] Error 1

---

### Post by cheapsaket on 2009-02-11
Can some guru please help out here? Google does not seem to be helping with this specific issue.

---

