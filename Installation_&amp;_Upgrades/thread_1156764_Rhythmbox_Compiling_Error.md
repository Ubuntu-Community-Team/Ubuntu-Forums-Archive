---
title: "Rhythmbox Compiling Error"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by illbashu on 2009-05-12
```

/usr/bin/install -c -m 644 fr/figures/rb-window.png /usr/local/share/gnome/help/rhythmbox/fr/figures/rb-window.png
/usr/bin/install -c -m 644 it/figures/rb-window.png /usr/local/share/gnome/help/rhythmbox/it/figures/rb-window.png
cd /usr/local/share/gnome/help/rhythmbox/oc/figures/ && ln -s -f ../../C/figures/rb-window.png rb-window.png
cd /usr/local/share/gnome/help/rhythmbox/ru/figures/ && ln -s -f ../../C/figures/rb-window.png rb-window.png
/usr/bin/install -c -m 644 sv/figures/rb-window.png /usr/local/share/gnome/help/rhythmbox/sv/figures/rb-window.png
/usr/bin/install -c -m 644 zh_CN/figures/rb-window.png /usr/local/share/gnome/help/rhythmbox/zh_CN/figures/rb-window.png
/usr/bin/install -c -m 644 C/figures/rb-window-small.png /usr/local/share/gnome/help/rhythmbox/C/figures/rb-window-small.png
cd /usr/local/share/gnome/help/rhythmbox/cs/figures/ && ln -s -f ../../C/figures/rb-window-small.png rb-window-small.png
cd /usr/local/share/gnome/help/rhythmbox/da/figures/ && ln -s -f ../../C/figures/rb-window-small.png rb-window-small.png
/usr/bin/install -c -m 644 de/figures/rb-window-small.png /usr/local/share/gnome/help/rhythmbox/de/figures/rb-window-small.png
/usr/bin/install -c -m 644 es/figures/rb-window-small.png /usr/local/share/gnome/help/rhythmbox/es/figures/rb-window-small.png
cd /usr/local/share/gnome/help/rhythmbox/el/figures/ && ln -s -f ../../C/figures/rb-window-small.png rb-window-small.png
/usr/bin/install -c -m 644 fr/figures/rb-window-small.png /usr/local/share/gnome/help/rhythmbox/fr/figures/rb-window-small.png
/usr/bin/install -c -m 644 it/figures/rb-window-small.png /usr/local/share/gnome/help/rhythmbox/it/figures/rb-window-small.png
cd /usr/local/share/gnome/help/rhythmbox/oc/figures/ && ln -s -f ../../C/figures/rb-window-small.png rb-window-small.png
cd /usr/local/share/gnome/help/rhythmbox/ru/figures/ && ln -s -f ../../C/figures/rb-window-small.png rb-window-small.png
/usr/bin/install -c -m 644 sv/figures/rb-window-small.png /usr/local/share/gnome/help/rhythmbox/sv/figures/rb-window-small.png
/usr/bin/install -c -m 644 zh_CN/figures/rb-window-small.png /usr/local/share/gnome/help/rhythmbox/zh_CN/figures/rb-window-small.png
/bin/bash ../mkinstalldirs /usr/local/share/omf/rhythmbox
/usr/bin/install -c -m 644 rhythmbox-C.omf /usr/local/share/omf/rhythmbox/rhythmbox-C.omf
/usr/bin/install: cannot stat `rhythmbox-C.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-cs.omf /usr/local/share/omf/rhythmbox/rhythmbox-cs.omf
/usr/bin/install: cannot stat `rhythmbox-cs.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-da.omf /usr/local/share/omf/rhythmbox/rhythmbox-da.omf
/usr/bin/install: cannot stat `rhythmbox-da.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-de.omf /usr/local/share/omf/rhythmbox/rhythmbox-de.omf
/usr/bin/install: cannot stat `rhythmbox-de.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-es.omf /usr/local/share/omf/rhythmbox/rhythmbox-es.omf
/usr/bin/install: cannot stat `rhythmbox-es.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-el.omf /usr/local/share/omf/rhythmbox/rhythmbox-el.omf
/usr/bin/install: cannot stat `rhythmbox-el.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-fr.omf /usr/local/share/omf/rhythmbox/rhythmbox-fr.omf
/usr/bin/install: cannot stat `rhythmbox-fr.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-it.omf /usr/local/share/omf/rhythmbox/rhythmbox-it.omf
/usr/bin/install: cannot stat `rhythmbox-it.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-oc.omf /usr/local/share/omf/rhythmbox/rhythmbox-oc.omf
/usr/bin/install: cannot stat `rhythmbox-oc.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-ru.omf /usr/local/share/omf/rhythmbox/rhythmbox-ru.omf
/usr/bin/install: cannot stat `rhythmbox-ru.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-sv.omf /usr/local/share/omf/rhythmbox/rhythmbox-sv.omf
/usr/bin/install: cannot stat `rhythmbox-sv.omf': No such file or directory
/usr/bin/install -c -m 644 rhythmbox-zh_CN.omf /usr/local/share/omf/rhythmbox/rhythmbox-zh_CN.omf
/usr/bin/install: cannot stat `rhythmbox-zh_CN.omf': No such file or directory
make[2]: *** [install-doc-omf] Error 1
make[2]: Leaving directory `/home/bash/Desktop/rhythmbox-0.12.1/help'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bash/Desktop/rhythmbox-0.12.1/help'
make: *** [install-recursive] Error 1


```

I got all the dependencies by running "sudo apt-get build-dep rhythmbox"
Anyone know what this error is about? from looking at it seems to not be able to find rhythmbox-sv.omf. how do I fix this? i am trying to build the latest rhythmbox 0.12.1

---

### Post by kpkeerthi on 2009-05-12
You can get the deb for 0.12.1 from here: [http://www.getdeb.net/app/Rhythmbox]("http://www.getdeb.net/app/Rhythmbox")

---

### Post by ostaja on 2009-12-22
This is old thread, but i have exactly same problem with rhythmbox 0.12.5 and 0.12.6, have not tried other versions. I also tried to find .deb packages, but without results. Ubuntu version is jaunty. Any ideas how to fix this?

---

