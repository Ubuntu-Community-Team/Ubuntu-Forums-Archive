---
title: "Removing COMPLETELY Openoffice and reinstalling"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by glósóli on 2009-06-23
hi!

after some regular sneaking at ubuntu from time to time (ubuntu 6, 7, 8..), trying to recover my xp machine I discovered with much joy that finally it support my wificard without going into ndiswrapper!

that was a big push to use Ubuntu, and now from 2 days I'm using it and I think it'll be my ultimate solution (with a VM rnning xp however). Very good OS as usual, and this time no hassle configuring my wifi!!

so, I'm configuring my ubu-box.
at first, I downloaded Openoffice64, then I removed all openoffice stuff on the pc running

```
sudo apt-get remove openoffice*.*
```

then I installed the package and the desktop-integration, perfect, brilliant!
After that, dunno if it's thanks to me messing around with "Computer Janitor", I've had any icons of openoffice left on the menu.
so I was wondering if the whole program disappeared or just the icons.

I run

```
locate openoffice
```

and I've seen lot of files

I've open computer janitor and I've seen lot of openoffice files listed.

so I wanted to erase it completely and reinstall; I used CJanitor to get rid of all stuff, opened Synaptic to check everything was gone, gone.

but if I run locate openoffice, I still get all this stuff....How can I erase them before going into a fresh install of OOo??

thanks a lot!!!

```
/etc/openoffice
/etc/openoffice/README.dictionary.lst
/etc/openoffice/psprint.conf
/etc/openoffice/soffice.sh
/etc/openoffice/sofficerc
/usr/bin/openoffice.org
/usr/lib/openoffice
/usr/lib/mime/packages/openoffice.org-calc
/usr/lib/mime/packages/openoffice.org-draw
/usr/lib/mime/packages/openoffice.org-impress
/usr/lib/mime/packages/openoffice.org-math
/usr/lib/mime/packages/openoffice.org-writer
/usr/sbin/update-openoffice-dicts
/usr/share/openoffice
/usr/share/app-install/desktop/openoffice.org-base.desktop
/usr/share/app-install/desktop/openoffice.org-calc.desktop
/usr/share/app-install/desktop/openoffice.org-draw.desktop
/usr/share/app-install/desktop/openoffice.org-impress.desktop
/usr/share/app-install/desktop/openoffice.org-math.desktop
/usr/share/app-install/desktop/openoffice.org-startcenter.desktop
/usr/share/app-install/desktop/openoffice.org-writer.desktop
/usr/share/application-registry/openoffice.applications
/usr/share/applications/openoffice.org-calc.desktop
/usr/share/applications/openoffice.org-draw.desktop
/usr/share/applications/openoffice.org-impress.desktop
/usr/share/applications/openoffice.org-math.desktop
/usr/share/applications/openoffice.org-startcenter.desktop
/usr/share/applications/openoffice.org-writer.desktop
/usr/share/bug/openoffice.org-base-core
/usr/share/bug/openoffice.org-calc
/usr/share/bug/openoffice.org-common
/usr/share/bug/openoffice.org-core
/usr/share/bug/openoffice.org-draw
/usr/share/bug/openoffice.org-emailmerge
/usr/share/bug/openoffice.org-gnome
/usr/share/bug/openoffice.org-gtk
/usr/share/bug/openoffice.org-impress
/usr/share/bug/openoffice.org-l10n-common
/usr/share/bug/openoffice.org-math
/usr/share/bug/openoffice.org-style-human
/usr/share/bug/openoffice.org-writer
/usr/share/doc/openoffice.org-base-core
/usr/share/doc/openoffice.org-calc
/usr/share/doc/openoffice.org-common
/usr/share/doc/openoffice.org-core
/usr/share/doc/openoffice.org-draw
/usr/share/doc/openoffice.org-emailmerge
/usr/share/doc/openoffice.org-gnome
/usr/share/doc/openoffice.org-gtk
/usr/share/doc/openoffice.org-help-en-gb
/usr/share/doc/openoffice.org-help-en-us
/usr/share/doc/openoffice.org-hyphenation
/usr/share/doc/openoffice.org-hyphenation-en-us
/usr/share/doc/openoffice.org-impress
/usr/share/doc/openoffice.org-l10n-common
/usr/share/doc/openoffice.org-l10n-en-gb
/usr/share/doc/openoffice.org-l10n-en-za
/usr/share/doc/openoffice.org-math
/usr/share/doc/openoffice.org-style-human
/usr/share/doc/openoffice.org-thesaurus-en-au
/usr/share/doc/openoffice.org-thesaurus-en-us
/usr/share/doc/openoffice.org-writer
/usr/share/fonts/truetype/openoffice
/usr/share/fonts/truetype/openoffice/opens___.ttf
/usr/share/icons/gnome/16x16/stock/generic/stock_openoffice.png
/usr/share/icons/hicolor/16x16/apps/openofficeorg3-base.png
/usr/share/icons/hicolor/16x16/apps/openofficeorg3-calc.png
/usr/share/icons/hicolor/16x16/apps/openofficeorg3-draw.png
/usr/share/icons/hicolor/16x16/apps/openofficeorg3-impress.png
/usr/share/icons/hicolor/16x16/apps/openofficeorg3-math.png
/usr/share/icons/hicolor/16x16/apps/openofficeorg3-printeradmin.png
/usr/share/icons/hicolor/16x16/apps/openofficeorg3-writer.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-database.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-drawing-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-drawing.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-extension.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-formula.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-master-document.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-database.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-drawing-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-drawing.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-formula.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-master-document.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-presentation-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-presentation.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-spreadsheet-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-spreadsheet.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-text-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-text.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-oasis-web-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-presentation-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-presentation.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-spreadsheet-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-spreadsheet.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-text-template.png
/usr/share/icons/hicolor/16x16/mimetypes/openofficeorg3-text.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-base.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-base.xpm
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-calc.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-calc.xpm
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-draw.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-draw.xpm
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-impress.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-impress.xpm
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-math.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-math.xpm
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-printeradmin.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-printeradmin.xpm
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-writer.png
/usr/share/icons/hicolor/32x32/apps/openofficeorg3-writer.xpm
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-database.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-drawing-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-drawing.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-extension.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-formula.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-master-document.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-database.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-drawing-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-drawing.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-formula.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-master-document.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-presentation-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-presentation.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-spreadsheet-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-spreadsheet.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-text-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-text.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-oasis-web-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-presentation-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-presentation.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-spreadsheet-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-spreadsheet.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-text-template.png
/usr/share/icons/hicolor/32x32/mimetypes/openofficeorg3-text.png
/usr/share/icons/hicolor/48x48/apps/openofficeorg3-base.png
/usr/share/icons/hicolor/48x48/apps/openofficeorg3-calc.png
/usr/share/icons/hicolor/48x48/apps/openofficeorg3-draw.png
/usr/share/icons/hicolor/48x48/apps/openofficeorg3-impress.png
/usr/share/icons/hicolor/48x48/apps/openofficeorg3-math.png
/usr/share/icons/hicolor/48x48/apps/openofficeorg3-printeradmin.png
/usr/share/icons/hicolor/48x48/apps/openofficeorg3-writer.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-database.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-drawing-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-drawing.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-extension.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-formula.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-master-document.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-database.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-drawing-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-drawing.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-formula.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-master-document.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-presentation-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-presentation.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-spreadsheet-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-spreadsheet.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-text-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-text.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-oasis-web-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-presentation-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-presentation.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-spreadsheet-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-spreadsheet.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-text-template.png
/usr/share/icons/hicolor/48x48/mimetypes/openofficeorg3-text.png
/usr/share/java/openoffice
/usr/share/java/openoffice/JREProperties.class
/usr/share/java/openoffice/java_uno.jar
/usr/share/java/openoffice/juh.jar
/usr/share/java/openoffice/jurt.jar
/usr/share/java/openoffice/ridl.jar
/usr/share/java/openoffice/unoloader.jar
/usr/share/lintian/overrides/openoffice.org-base-core
/usr/share/lintian/overrides/openoffice.org-calc
/usr/share/lintian/overrides/openoffice.org-core
/usr/share/lintian/overrides/openoffice.org-draw
/usr/share/lintian/overrides/openoffice.org-gnome
/usr/share/lintian/overrides/openoffice.org-gtk
/usr/share/lintian/overrides/openoffice.org-impress
/usr/share/lintian/overrides/openoffice.org-math
/usr/share/lintian/overrides/openoffice.org-writer
/usr/share/man/man1/openoffice.1.gz
/usr/share/man/man8/update-openoffice-dicts.8.gz
/usr/share/menu/openoffice.org-calc
/usr/share/menu/openoffice.org-draw
/usr/share/menu/openoffice.org-impress
/usr/share/menu/openoffice.org-math
/usr/share/menu/openoffice.org-writer
/usr/share/mime/application/vnd.openofficeorg.extension.xml
/usr/share/mime/packages/openoffice.org.xml
/usr/share/mime-info/openoffice.keys
/usr/share/mime-info/openoffice.mime
/var/lib/dpkg/info/openoffice.org-base-core.list
/var/lib/dpkg/info/openoffice.org-base-core.md5sums
/var/lib/dpkg/info/openoffice.org-base-core.postinst
/var/lib/dpkg/info/openoffice.org-calc.list
/var/lib/dpkg/info/openoffice.org-calc.md5sums
/var/lib/dpkg/info/openoffice.org-calc.postinst
/var/lib/dpkg/info/openoffice.org-calc.postrm
/var/lib/dpkg/info/openoffice.org-calc.preinst
/var/lib/dpkg/info/openoffice.org-common.conffiles
/var/lib/dpkg/info/openoffice.org-common.list
/var/lib/dpkg/info/openoffice.org-common.md5sums
/var/lib/dpkg/info/openoffice.org-common.postinst
/var/lib/dpkg/info/openoffice.org-common.postrm
/var/lib/dpkg/info/openoffice.org-common.preinst
/var/lib/dpkg/info/openoffice.org-core.list
/var/lib/dpkg/info/openoffice.org-core.md5sums
/var/lib/dpkg/info/openoffice.org-core.postrm
/var/lib/dpkg/info/openoffice.org-draw.list
/var/lib/dpkg/info/openoffice.org-draw.md5sums
/var/lib/dpkg/info/openoffice.org-draw.postinst
/var/lib/dpkg/info/openoffice.org-draw.postrm
/var/lib/dpkg/info/openoffice.org-emailmerge.list
/var/lib/dpkg/info/openoffice.org-emailmerge.md5sums
/var/lib/dpkg/info/openoffice.org-emailmerge.postinst
/var/lib/dpkg/info/openoffice.org-emailmerge.preinst
/var/lib/dpkg/info/openoffice.org-emailmerge.prerm
/var/lib/dpkg/info/openoffice.org-gnome.list
/var/lib/dpkg/info/openoffice.org-gnome.md5sums
/var/lib/dpkg/info/openoffice.org-gnome.postinst
/var/lib/dpkg/info/openoffice.org-gtk.list
/var/lib/dpkg/info/openoffice.org-gtk.md5sums
/var/lib/dpkg/info/openoffice.org-gtk.postinst
/var/lib/dpkg/info/openoffice.org-help-en-gb.list
/var/lib/dpkg/info/openoffice.org-help-en-gb.md5sums
/var/lib/dpkg/info/openoffice.org-help-en-gb.postinst
/var/lib/dpkg/info/openoffice.org-help-en-us.list
/var/lib/dpkg/info/openoffice.org-help-en-us.md5sums
/var/lib/dpkg/info/openoffice.org-help-en-us.postinst
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.list
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.md5sums
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postinst
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm
/var/lib/dpkg/info/openoffice.org-hyphenation.list
/var/lib/dpkg/info/openoffice.org-hyphenation.md5sums
/var/lib/dpkg/info/openoffice.org-hyphenation.postinst
/var/lib/dpkg/info/openoffice.org-hyphenation.postrm
/var/lib/dpkg/info/openoffice.org-impress.list
/var/lib/dpkg/info/openoffice.org-impress.md5sums
/var/lib/dpkg/info/openoffice.org-impress.postinst
/var/lib/dpkg/info/openoffice.org-impress.postrm
/var/lib/dpkg/info/openoffice.org-l10n-common.list
/var/lib/dpkg/info/openoffice.org-l10n-common.md5sums
/var/lib/dpkg/info/openoffice.org-l10n-en-gb.list
/var/lib/dpkg/info/openoffice.org-l10n-en-gb.md5sums
/var/lib/dpkg/info/openoffice.org-l10n-en-gb.postinst
/var/lib/dpkg/info/openoffice.org-l10n-en-za.list
/var/lib/dpkg/info/openoffice.org-l10n-en-za.md5sums
/var/lib/dpkg/info/openoffice.org-l10n-en-za.postinst
/var/lib/dpkg/info/openoffice.org-math.list
/var/lib/dpkg/info/openoffice.org-math.md5sums
/var/lib/dpkg/info/openoffice.org-math.postinst
/var/lib/dpkg/info/openoffice.org-math.postrm
/var/lib/dpkg/info/openoffice.org-style-human.list
/var/lib/dpkg/info/openoffice.org-style-human.md5sums
/var/lib/dpkg/info/openoffice.org-thesaurus-en-au.list
/var/lib/dpkg/info/openoffice.org-thesaurus-en-au.md5sums
/var/lib/dpkg/info/openoffice.org-thesaurus-en-au.postinst
/var/lib/dpkg/info/openoffice.org-thesaurus-en-au.postrm
/var/lib/dpkg/info/openoffice.org-thesaurus-en-us.list
/var/lib/dpkg/info/openoffice.org-thesaurus-en-us.md5sums
/var/lib/dpkg/info/openoffice.org-thesaurus-en-us.postinst
/var/lib/dpkg/info/openoffice.org-thesaurus-en-us.postrm
/var/lib/dpkg/info/openoffice.org-writer.list
/var/lib/dpkg/info/openoffice.org-writer.md5sums
/var/lib/dpkg/info/openoffice.org-writer.postinst
/var/lib/dpkg/info/openoffice.org-writer.postrm
/var/lib/dpkg/info/openoffice.org-writer.preinst
```

---

### Post by glósóli on 2009-06-23
after doing, as made the first time removing pre-installed OOo,

```
sudo apt-get remove openoffice*.*
```

and erased the hidden .openoffice folders under "home" folder, it remains

```
/etc/openoffice
/etc/openoffice/psprint.conf
/etc/openoffice/soffice.sh
/etc/openoffice/sofficerc
/opt/openoffice.org3
/opt/openoffice.org3/share
/opt/openoffice.org3/share/uno_packages
/opt/openoffice.org3/share/uno_packages/cache
/opt/openoffice.org3/share/uno_packages/cache/registry
/opt/openoffice.org3/share/uno_packages/cache/stamp.sys
/opt/openoffice.org3/share/uno_packages/cache/uno_packages
/opt/openoffice.org3/share/uno_packages/cache/uno_packages.db
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registered_packages.db
/opt/openoffice.org3/share/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/LICENCES-fr.txt
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/LICENSES-en.txt
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/META-INF
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/README_fr_FR.txt
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/README_hyph_fr_FR.txt
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/description.xml
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/dictionaries.xcu
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/fr_FR.aff
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/fr_FR.dic
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/hyph_fr_FR.dic
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/th_fr_FR_v2.dat
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/th_fr_FR_v2.idx
/opt/openoffice.org3/share/uno_packages/cache/uno_packages/KoC0aY_/dict-fr.oxt/META-INF/manifest.xml
/usr/share/app-install/desktop/openoffice.org-base.desktop
/usr/share/app-install/desktop/openoffice.org-calc.desktop
/usr/share/app-install/desktop/openoffice.org-draw.desktop
/usr/share/app-install/desktop/openoffice.org-impress.desktop
/usr/share/app-install/desktop/openoffice.org-math.desktop
/usr/share/app-install/desktop/openoffice.org-startcenter.desktop
/usr/share/app-install/desktop/openoffice.org-writer.desktop
/usr/share/fonts/truetype/openoffice
/usr/share/fonts/truetype/openoffice/opens___.ttf
/usr/share/icons/gnome/16x16/stock/generic/stock_openoffice.png
/usr/share/java/openoffice
/usr/share/java/openoffice/JREProperties.class
/usr/share/java/openoffice/java_uno.jar
/usr/share/java/openoffice/juh.jar
/usr/share/java/openoffice/jurt.jar
/usr/share/java/openoffice/ridl.jar
/usr/share/java/openoffice/unoloader.jar
/usr/share/mime/application/vnd.openofficeorg.extension.xml
/var/lib/dpkg/info/openoffice.org-calc.list
/var/lib/dpkg/info/openoffice.org-calc.postrm
/var/lib/dpkg/info/openoffice.org-common.list
/var/lib/dpkg/info/openoffice.org-common.postrm
/var/lib/dpkg/info/openoffice.org-core.list
/var/lib/dpkg/info/openoffice.org-core.postrm
/var/lib/dpkg/info/openoffice.org-debian-menus.list
/var/lib/dpkg/info/openoffice.org-debian-menus.postrm
/var/lib/dpkg/info/openoffice.org-draw.list
/var/lib/dpkg/info/openoffice.org-draw.postrm
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.list
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm
/var/lib/dpkg/info/openoffice.org-hyphenation.list
/var/lib/dpkg/info/openoffice.org-hyphenation.postrm
/var/lib/dpkg/info/openoffice.org-impress.list
/var/lib/dpkg/info/openoffice.org-impress.postrm
/var/lib/dpkg/info/openoffice.org-math.list
/var/lib/dpkg/info/openoffice.org-math.postrm
/var/lib/dpkg/info/openoffice.org-thesaurus-en-au.list
/var/lib/dpkg/info/openoffice.org-thesaurus-en-au.postrm
/var/lib/dpkg/info/openoffice.org-thesaurus-en-us.list
/var/lib/dpkg/info/openoffice.org-thesaurus-en-us.postrm
/var/lib/dpkg/info/openoffice.org-writer.list
/var/lib/dpkg/info/openoffice.org-writer.postrm
```

how can I get rid of them?!!?:(
I'm afraid that if i install OOo now, it will mess around with old plus new files...

---

### Post by dsavi on 2009-06-23
My instinct would be to just apt-get install OOo. Really if those files are actually used by OOo, then they will be replaced by dpkg. If it doesn't work you could try apt-get purge-ing it.

---

### Post by glósóli on 2009-06-23
> **dsavi said:**
> My instinct would be to just apt-get install OOo. Really if those files are actually used by OOo, then they will be replaced by dpkg. If it doesn't work you could try apt-get purge-ing it.

thanks for your contribute.

I also checked [this topic]("http://ubuntuforums.org/showthread.php?t=232633"), made some purge, sudo updatedb but running locate showed lot of files however..

never mind, installed OOo, it's working fine...
just hoping not to have left too much mess behind...

maybe I'm still too much Xp-minded... ;)

---

