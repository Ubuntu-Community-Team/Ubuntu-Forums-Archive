---
title: "Cannot update nautilus-data. Corrupted config?"
date: 2008-11-04
forum: General Help
---

### Post by plapli on 2008-11-04
The following attempt to update nautilus-data on my ubuntu 8.04 (hardy), Kernel Linux 2.6.24-19-Generic, GNOME 2.22.3 failed:
 

************* Update Manager tries to install: nautilus-data    Version 1:2.22.5.1-0ubuntu1

Fails with the following:
 
E: /var/cache/apt/archives/nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb: subprocess new post-removal script returned error exit status 1
E: /var/cache/apt/archives/serpentine_0.9-5ubuntu2_all.deb: subprocess new post-removal script returned error exit status 1


************ Synaptic has it marked for upgrade and under dependencies says it conflicts with nautilus (<2.14.1-3) which seems the cause.

My installed version of nautilus-data: 1:2.22.3-0ubuntu2 and "latest available version": 1:2.22.5.1-0ubuntu1
My installed version of nautilus: 1:2.22.5.1-0ubuntu1 and "latest available version": 1:2.22.5.1-0ubuntu1


************ Result of trying this via terminal:

boss@P4:~$ sudo apt-get dist-upgrade

[sudo] password for boss: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  nautilus-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/4221kB of archives.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154388 files and directories currently installed.)
Preparing to replace nautilus-data 1:2.22.3-0ubuntu2 (using .../nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb) ...
Unpacking replacement nautilus-data ...
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: error processing /var/cache/apt/archives/nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Selecting previously deselected package rhythmbox.
Preparing to replace rhythmbox 0.11.5-0ubuntu8 (using .../rhythmbox_0.11.5-0ubuntu8_i386.deb) ...
Unpacking replacement rhythmbox ...
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: error processing /var/cache/apt/archives/rhythmbox_0.11.5-0ubuntu8_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Selecting previously deselected package serpentine.
Preparing to replace serpentine 0.9-5ubuntu2 (using .../serpentine_0.9-5ubuntu2_all.deb) ...
Unpacking replacement serpentine ...
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: error processing /var/cache/apt/archives/serpentine_0.9-5ubuntu2_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : error parsing attribute name
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : attributes construct error
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:77: parser error : Couldn't find end of Start Tag value line 76
            <string>fast_user_switch</string>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:78: parser error : Opening and ending tag mismatch: list line 54 and value
          </value>   
                  ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:79: parser error : Opening and ending tag mismatch: value line 53 and list
        </list>
               ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:80: parser error : Opening and ending tag mismatch: entry line 50 and value
      </value>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:81: parser error : Opening and ending tag mismatch: entrylist line 3 and entry
    </entry>
            ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:901: parser error : Opening and ending tag mismatch: gconfentryfile line 1 and entrylist
  </entrylist>
              ^
/usr/share/gconf/defaults/05_panel-default-setup.entries:903: parser error : Extra content at the end of the document
</gconfentryfile>
^
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb
 /var/cache/apt/archives/rhythmbox_0.11.5-0ubuntu8_i386.deb
 /var/cache/apt/archives/serpentine_0.9-5ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
boss@P4:~$ 




*********** My nautilus-data "installed files":

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/nautilus-data
/usr/share/doc/nautilus-data/README
/usr/share/doc/nautilus-data/TODO
/usr/share/doc/nautilus-data/AUTHORS
/usr/share/doc/nautilus-data/copyright
/usr/share/doc/nautilus-data/examples
/usr/share/doc/nautilus-data/examples/mount-archive.desktop
/usr/share/doc/nautilus-data/NEWS.gz
/usr/share/doc/nautilus-data/THANKS.gz
/usr/share/doc/nautilus-data/changelog.Debian.gz
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/nautilus.png
/usr/share/icons/hicolor/22x22
/usr/share/icons/hicolor/22x22/apps
/usr/share/icons/hicolor/22x22/apps/nautilus.png
/usr/share/icons/hicolor/24x24
/usr/share/icons/hicolor/24x24/apps
/usr/share/icons/hicolor/24x24/apps/nautilus.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/nautilus.png
/usr/share/icons/hicolor/scalable
/usr/share/icons/hicolor/scalable/apps
/usr/share/icons/hicolor/scalable/apps/nautilus.svg
/usr/share/nautilus
/usr/share/nautilus/ui
/usr/share/nautilus/ui/nautilus-desktop-icon-view-ui.xml
/usr/share/nautilus/ui/nautilus-directory-view-ui.xml
/usr/share/nautilus/ui/nautilus-icon-view-ui.xml
/usr/share/nautilus/ui/nautilus-list-view-ui.xml
/usr/share/nautilus/ui/nautilus-shell-ui.xml
/usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
/usr/share/nautilus/ui/nautilus-spatial-window-ui.xml
/usr/share/nautilus/glade
/usr/share/nautilus/glade/nautilus-bookmarks-window.glade
/usr/share/nautilus/glade/nautilus-file-management-properties.glade
/usr/share/nautilus/patterns
/usr/share/nautilus/patterns/blue_gray_rough.png
/usr/share/nautilus/patterns/blue_ridge.png
/usr/share/nautilus/patterns/blue_type.png
/usr/share/nautilus/patterns/brushed_metal.png
/usr/share/nautilus/patterns/burlap.jpg
/usr/share/nautilus/patterns/camouflage.png
/usr/share/nautilus/patterns/chalk.jpg
/usr/share/nautilus/patterns/cork.png
/usr/share/nautilus/patterns/countertop.png
/usr/share/nautilus/patterns/dark-gnome.jpg
/usr/share/nautilus/patterns/dots.png
/usr/share/nautilus/patterns/fibers.png
/usr/share/nautilus/patterns/fleur_de_lis.png
/usr/share/nautilus/patterns/floral.png
/usr/share/nautilus/patterns/fossil.png
/usr/share/nautilus/patterns/gnome.jpg
/usr/share/nautilus/patterns/green_weave.png
/usr/share/nautilus/patterns/ice.png
/usr/share/nautilus/patterns/manila_paper.png
/usr/share/nautilus/patterns/moss_ridge.png
/usr/share/nautilus/patterns/numbers.png
/usr/share/nautilus/patterns/ocean_stripes.png
/usr/share/nautilus/patterns/purple_marble.png
/usr/share/nautilus/patterns/reset.png
/usr/share/nautilus/patterns/ridged_paper.png
/usr/share/nautilus/patterns/rough_paper.png
/usr/share/nautilus/patterns/sky_ridge.png
/usr/share/nautilus/patterns/snow_ridge.png
/usr/share/nautilus/patterns/stucco.jpg
/usr/share/nautilus/patterns/terracotta.png
/usr/share/nautilus/patterns/wavy_white.png
/usr/share/nautilus/browser.xml
/usr/share/nautilus/nautilus-extras.placeholder
/usr/share/nautilus/nautilus-suggested.placeholder
/usr/share/mime
/usr/share/mime/packages
/usr/share/mime/packages/nautilus.xml
/usr/share/pixmaps
/usr/share/pixmaps/nautilus
/usr/share/pixmaps/nautilus/audio.svg
/usr/share/pixmaps/nautilus/backgrounds.png
/usr/share/pixmaps/nautilus/chit_frame.png
/usr/share/pixmaps/nautilus/colors.png
/usr/share/pixmaps/nautilus/emblems.png
/usr/share/pixmaps/nautilus/erase.png
/usr/share/pixmaps/nautilus/knob.png
/usr/share/pixmaps/nautilus/note-indicator.png
/usr/share/pixmaps/nautilus/thumbnail_frame.png
/usr/share/pixmaps/nautilus.xpm
/usr/share/gconf
/usr/share/gconf/defaults
/usr/share/gconf/defaults/10_nautilus-data
/usr/share/gconf/schemas
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas
/usr/lib
/usr/lib/bonobo
/usr/lib/bonobo/servers
/usr/lib/bonobo/servers/Nautilus_shell.server



************** Trying to remove rhythmbox and serpentine:

root@P4:/home/boss# apt-get remove rhythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libglib1.2ldbl menu
  gnustep-base-common libtwolame0 libmpich1.0gf libgsf-gnome-1-114 guile-1.6
  liblzo1 libgoffice-0-common libportaudio2 librdf0
  kdebase-runtime-data-common libgtk1.2 libkipi0 libosp5 libfame-0.9
  libgfortran2 gnustep-gui-common python-kaa-base kdebase-runtime kdelibs5
  libpvm3 libjack0.100.0-0 libqt4-qt3support libatk1-ruby1.8 python-pyogg
  libkexiv2-3 kde-icons-oxygen libexiv2-2 librasqal0 python-pyvorbis ruby1.8
  libsoprano4 nvidia-kernel-common blt python-kaa-metadata
  kdebase-runtime-bin-kde4 kdelibs5-data python-mutagen python-cddb
  libgnomecanvasmm-2.6-1c2a libhtml-tableextract-perl gnustep-common icedax
  libgconf2-ruby1.8 libxul0d libglib2-ruby1.8 transcode libqt4-sql libifp4
  libcairo-ruby1.8 libstreamanalyzer0 libphonon4 libzip1 python-sqlite
  libgdk-pixbuf2-ruby1.8 libmozjs0d libgtk1.2-common libffcall1
  gnustep-back-common libgtk2-ruby1.8 libpq5 libstreams0 xvfb libxul-common
  libruby1.8 python-eyed3 ladcca2 kdebase-runtime-data kde4libs-bin
  libglademm-2.4-1c2a libpango1-ruby1.8 libnjb5 libkdcraw3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nautilus-data
The following packages will be REMOVED:
  rhythmbox
The following packages will be upgraded:
  nautilus-data
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/1013kB of archives.
After this operation, 13.5MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing rhythmbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 rhythmbox
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@P4:/home/boss# apt-get remove serpentine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libglib1.2ldbl menu
  gnustep-base-common libtwolame0 libmpich1.0gf libgsf-gnome-1-114 guile-1.6
  liblzo1 libgoffice-0-common libportaudio2 librdf0
  kdebase-runtime-data-common libgtk1.2 libgda3-common python-gnome2-extras
  libkipi0 libosp5 libfame-0.9 libgfortran2 gnustep-gui-common python-kaa-base
  kdebase-runtime kdelibs5 libpvm3 libjack0.100.0-0 libqt4-qt3support
  libatk1-ruby1.8 python-pyogg libgdl-gnome-1-0 libkexiv2-3 kde-icons-oxygen
  libexiv2-2 librasqal0 python-pyvorbis ruby1.8 libsoprano4
  nvidia-kernel-common blt python-kaa-metadata kdebase-runtime-bin-kde4
  kdelibs5-data python-mutagen python-cddb libgnomecanvasmm-2.6-1c2a
  libhtml-tableextract-perl gnustep-common icedax libgconf2-ruby1.8 libxul0d
  libglib2-ruby1.8 transcode libqt4-sql libifp4 libcairo-ruby1.8
  libstreamanalyzer0 libphonon4 libzip1 python-sqlite libgdk-pixbuf2-ruby1.8
  libmozjs0d libgtk1.2-common libffcall1 python-4suite-xml libgda3-3
  gnustep-back-common libgtk2-ruby1.8 libpq5 libstreams0 xvfb libxul-common
  libruby1.8 python-eyed3 ladcca2 kdebase-runtime-data kde4libs-bin
  libglademm-2.4-1c2a libpango1-ruby1.8 libnjb5 libgdl-1-0 libkdcraw3
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nautilus-data
The following packages will be REMOVED:
  serpentine
The following packages will be upgraded:
  nautilus-data
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/4110kB of archives.
After this operation, 799kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing serpentine (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 serpentine
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@P4:/home/boss#

---

