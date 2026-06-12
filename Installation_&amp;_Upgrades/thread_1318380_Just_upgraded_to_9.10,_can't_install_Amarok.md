---
title: "Just upgraded to 9.10, can't install Amarok"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by supercheetah on 2009-11-07
I just upgraded to Ubuntu 9.10 from 9.04.  Almost everything went smoothly, but I can't seem to install Amarok any more.

When I try to use aptitude, it says there is "No candidate version found for amarok."

"apt-cache show amarok" shows the following, but neither seem to be installable:
```

Package: amarok                          
Priority: optional                       
Section: kde                             
Installed-Size: 19152                    
Maintainer: Kubuntu Developers <kubuntu-devel@ubuntu.com>
Original-Maintainer: Modestas Vainius <modestas@vainius.eu>
Architecture: i386                                         
Version: 2:2.2.0-0ubuntu2                                  
Replaces: amarok-common (<< 2:2.1.1orig-0ubuntu2), amarok-kde4
Depends: amarok-common (= 2:2.2.0-0ubuntu2), amarok-utils (= 2:2.2.0-0ubuntu2), phonon-backend-xine | phonon-backend, kdebase-runtime (>= 4:4.3.2), kdelibs5 (>= 4:4.3.2), libc6 (>= 2.8), libcurl3-gnutls (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libgcrypt11 (>= 1.4.2), libglib2.0-0 (>= 2.14.0), libgpod4 (>= 0.7.0), libgtk2.0-0 (>= 2.8.0), liblastfm0, libloudmouth1-0 (>= 1.1.4-2), libmtp8 (>= 0.3.1), libmysqlclient16 (>= 5.1.21-1), libplasma3 (>= 4:4.3.2-0ubuntu3), libqt4-dbus (>= 4.5.1), libqt4-network (>= 4.5.1), libqt4-phonon (>= 4.5.1), libqt4-script (>= 4.5.1), libqt4-sql (>= 4.5.1), libqt4-svg (>= 4.5.1), libqt4-webkit (>= 4.5.1), libqt4-xml (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libstdc++6 (>= 4.4.0), libstreamanalyzer0 (>= 0.7.0), libstreams0 (>= 0.7.0), libtag-extras1 (>= 1.0.1), libtag1c2a (>= 1.6-2~), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4), libqtscript4-core, libqtscript4-gui, libqtscript4-network, libqtscript4-xml, libqtscript4-sql, libqtscript4-uitools                                                                                                                                       
Recommends: kdemultimedia-kio-plugins (>= 4:4.2.0), libqt4-sql-sqlite                                                                                            
Suggests: libqt4-sql-mysql, libqt4-sql-psql                                                                                                                      
Conflicts: amarok-engine-xine (<< 2), amarok-engine-yauap (<< 2), amarok-kde4                                                                                    
Filename: pool/main/a/amarok/amarok_2.2.0-0ubuntu2_i386.deb                                                                                                      
Size: 7250804                                                                                                                                                    
MD5sum: 0b8b42355c3bcc1358e66dc692d6d8fd                                                                                                                         
SHA1: 5fe8378032183160df980381f3a64f8c1bc9c128                                                                                                                   
SHA256: b2d3053adb7a5519a5d09cd408b337c3f2865d82296e231dc799292be0c0bff6                                                                                         
Description: easy to use media player based on the KDE 4 technology platform                                                                                     
 Amarok is a powerful music player with an intuitive interface. It makes                                                                                         
 playing the music you love and discovering new music easier than ever before                                                                                    
 and it looks good doing it! Amarok is based on the powerful Qt4 / KDE4                                                                                          
 technology platform and nicely integrates with KDE desktop.                                                                                                     
 .                                                                                                                                                               
 Much work has been invested into integrating Amarok 2 with various Web                                                                                          
 services:                                                                                                                                                       
   - Ampache                                                                                                                                                     
   - Jamendo Service                                                                                                                                             
   - Last.fm                                                                                                                                                     
   - Librivox                                                                                                                                                    
   - MP3tunes                                                                                                                                                    
   - Magnatune                                                                                                                                                   
   - OPML Podcast Directory                                                                                                                                      
   - Shoutcast Radio Directory                                                                                                                                   
 .                                                                                                                                                               
 Amarok comes with a lot of features including but not limited to:                                                                                               
   - Scripts - enhance your Amarok experience with community developed scripts.                                                                                  
   - Dynamic Playlists - create playlists that automatically update.                                                                                             
   - Context View - customize interface with the Plasma powered Context View.                                                                                    
   - PopUp Dropper - simplify drag&drop actions with revolutionary menu system.                                                                                  
   - Multiple Language Translations                                                                                                                              
   - Collection Management - organizing your music collection has never been                                                                                     
     easier with Amarok's powerful tagging, renaming, and sorting abilities.                                                                                     
   - Database Importing - import collections from Amarok 1.4 or iTunes.                                                                                          
   - Scriptable Services - integrate other web services into Amarok.                                                                                             
Homepage: http://amarok.kde.org                                                                                                                                  
Bugs: https://bugs.launchpad.net/ubuntu/+filebug                                                                                                                 
Origin: Ubuntu                                                                                                                                                   
Task: kubuntu-desktop, kubuntu-netbook, edubuntu-desktop-kde                                                                                                     

Package: amarok
Status: deinstall ok config-files
Priority: optional
Section: kde
Installed-Size: 16264
Maintainer: Kubuntu Developers <kubuntu-devel@ubuntu.com>
Architecture: i386
Version: 2:2.1mysql5.1.30-0ubuntu2~jaunty2
Config-Version: 2:2.1mysql5.1.30-0ubuntu2~jaunty2
Replaces: amarok-kde4
Depends: amarok-common (= 2:2.1mysql5.1.30-0ubuntu2~jaunty2), kdebase-runtime (>= 4:4.2.1), kdelibs5 (>= 4:4.2.1), libc6 (>= 2.8), libcurl3-gnutls (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libgcrypt11 (>= 1.4.0), libglib2.0-0 (>= 2.14.0), libgpod4-nogtk (>= 0.6.0) | libgpod4 (>= 0.6.0), libidn11 (>= 0.5.18), libloudmouth1-0 (>= 1.1.4-2), libmtp8, libphonon4 (>> 4:4.3.1), libplasma3, libqt4-dbus (>= 4.5.0~+rc1), libqt4-network (>= 4.5.0~+rc1), libqt4-script (>= 4.5.0~+rc1), libqt4-sql (>= 4.5.0~+rc1), libqt4-svg (>= 4.5.0~+rc1), libqt4-webkit (>= 4.5.0~+rc1), libqt4-xml (>= 4.5.0~+rc1), libqtcore4 (>= 4.5.0~+rc1), libqtgui4 (>= 4.5.0~+rc1), libstdc++6 (>= 4.2.1), libstreamanalyzer0 (>= 0.6.4), libstreams0 (>= 0.6.4), libtag-extras0, libtag1c2a (>= 1.5), libwrap0 (>= 7.6-4~), libxml2 (>= 2.6.27), phonon (>> 4:4.3.1), zlib1g (>= 1:1.1.4), libqtscriptbindings1
Recommends: kdemultimedia-kio-plugins (>= 4:4.1.96)
Suggests: libqt4-sql-sqlite, libqt4-sql-mysql, libqt4-sql-psql
Conflicts: amarok-kde4
Description: easy to use media player based on the KDE 4 technology platform
 Amarok is the media player with an intuitive interface. Amarok makes playing
 the music you love easier than ever before - and looks good doing it.
 .
 This package provides Amarok series 2 media player which is based on the KDE 4
 technology platform. Features include:
   - new fascinating look.
   - innovative user interface.
   - almighty Internet service framework.
   - powerful scripting.
   - dynamic and new biased playlists.
   - mobile devices support.
Homepage: http://amarok.kde.org
Original-Maintainer: Modestas Vainius <modestas@vainius.eu>

```

Note, this is Ubuntu, not Kubuntu.

Anyone know what's going on?

---

