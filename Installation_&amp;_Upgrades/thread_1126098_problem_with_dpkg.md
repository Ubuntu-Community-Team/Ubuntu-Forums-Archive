---
title: "problem with dpkg"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Magnetronitbhu on 2009-04-15
today when i ran 
sudo apt-get install -f
I got an error " dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

then following the error message I ran "dpkg --configure -a"
I got a long list of unmet dependencies and finally an error

this was the error message

Setting up xulrunner-1.9 (1.9.0.8+nobinonly-0ubuntu0.8.10.1) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Dpkg.pm line 12.
Compilation failed in require at /usr/sbin/update-alternatives line 11.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 11.
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 9
Setting up procps (1:3.2.7-9ubuntu2.1) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Dpkg.pm line 12.
Compilation failed in require at /usr/sbin/update-alternatives line 11.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 11.
dpkg: error processing procps (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of dolphin:
 dolphin depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing dolphin (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.27-11-generic (2.6.27-11.31) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 9
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-11-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libssl0.9.8 (0.9.8g-10.1ubuntu2.2) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing libssl0.9.8 (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of kdebase-bin:
 kdebase-bin depends on dolphin; however:
  Package dolphin is not configured yet.
 kdebase-bin depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing kdebase-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librdf0:
 librdf0 depends on libssl0.9.8 (>= 0.9.8f-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing librdf0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq5:
 libkonq5 depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing libkonq5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime:
 kdebase-runtime depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing kdebase-runtime (--configure):
 dependency problems - leaving unconfigured
Setting up totem-gstreamer (2.24.3-0ubuntu1) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Dpkg.pm line 12.
Compilation failed in require at /usr/sbin/update-alternatives line 11.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 11.
dpkg: error processing totem-gstreamer (--configure):
 subprocess post-installation script returned error exit status 9
Setting up galeon-common (2.0.6-2) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Dpkg.pm line 12.
Compilation failed in require at /usr/sbin/update-alternatives line 11.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 11.
dpkg: error processing galeon-common (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of kdebase-runtime-bin-kde4:
 kdebase-runtime-bin-kde4 depends on kdebase-runtime (>= 4:4.1.3); however:
  Package kdebase-runtime is not configured yet.
 kdebase-runtime-bin-kde4 depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing kdebase-runtime-bin-kde4 (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.2.3-1ubuntu3.4) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of transmission-gtk:
 transmission-gtk depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing transmission-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on kdelibs5 (= 4:4.1.4-0ubuntu1~intrepid1.1); however:
  Package kdelibs5 is not installed.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.2.3-1ubuntu3.4); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcurl3:
 libcurl3 depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libcurl3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kfind:
 kfind depends on kdebase-runtime (>= 4:4.1.3); however:
  Package kdebase-runtime is not configured yet.
 kfind depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing kfind (--configure):
 dependency problems - leaving unconfigured
Setting up ufw (0.23.3) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing ufw (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of smb4k:
 smb4k depends on samba-common; however:
  Package samba-common is not configured yet.
 smb4k depends on smbclient; however:
  Package smbclient is not configured yet.
dpkg: error processing smb4k (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdns43:
 libdns43 depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libdns43 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.8+nobinonly-0ubuntu0.8.10.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem-gstreamer (= 2.24.3-0ubuntu1) | totem-xine (= 2.24.3-0ubuntu1); however:
  Package totem-gstreamer is not configured yet.
  Package totem-xine is not installed.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up ghostscript (8.63.dfsg.1-0ubuntu6.3) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Dpkg.pm line 12.
Compilation failed in require at /usr/sbin/update-alternatives line 11.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 11.
dpkg: error processing ghostscript (--configure):
 subprocess post-installation script returned error exit status 9
Setting up perl (5.10.0-11.1ubuntu2.2) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Dpkg.pm line 12.
Compilation failed in require at /usr/sbin/update-alternatives line 11.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 11.
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 9
Setting up cups-bsd (1.3.9-2ubuntu9) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing cups-bsd (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of redland-utils:
 redland-utils depends on librdf0 (>= 1.0.6); however:
  Package librdf0 is not configured yet.
dpkg: error processing redland-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror-nsplugins:
 konqueror-nsplugins depends on kdebase-runtime (>= 4:4.1.3); however:
  Package kdebase-runtime is not configured yet.
 konqueror-nsplugins depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing konqueror-nsplugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of khelpcenter4:
 khelpcenter4 depends on kdebase-runtime (>= 4:4.1.3); however:
  Package kdebase-runtime is not configured yet.
 khelpcenter4 depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
dpkg: error processing khelpcenter4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker:
 tracker depends on procps (>= 1:3.2.7-9); however:
  Package procps is not configured yet.
dpkg: error processing tracker (--configure):
 dependency problems - leaving unconfigured
Setting up openoffice.org-common (1:2.4.1-11ubuntu2.1) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Debian/DictionariesCommon.pm line 5.
Compilation failed in require at /usr/sbin/update-openoffice-dicts line 9.
BEGIN failed--compilation aborted at /usr/sbin/update-openoffice-dicts line 9.
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror:
 konqueror depends on kdebase-runtime (>= 4:4.1.3); however:
  Package kdebase-runtime is not configured yet.
 konqueror depends on kdelibs5 (>= 4:4.1.4); however:
  Package kdelibs5 is not installed.
 konqueror depends on libkonq5; however:
  Package libkonq5 is not configured yet.
dpkg: error processing konqueror (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates:
 ca-certificates depends on openssl; however:
  Package openssl is not configured yet.
dpkg: error processing ca-certificates (--configure):
 dependency problems - leaving unconfigured
Setting up vim-tiny (1:7.1.314-3ubuntu3.1) ...
Usage: UNIVERSAL::isa(reference, kind) at /usr/share/perl/5.10/base.pm line 79.
BEGIN failed--compilation aborted at /usr/share/perl5/Dpkg.pm line 12.
Compilation failed in require at /usr/sbin/update-alternatives line 11.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 11.
dpkg: error processing vim-tiny (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of libraptor1:
 libraptor1 depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not configured yet.
dpkg: error processing libraptor1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpq5:
 libpq5 depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libpq5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.2.3-1ubuntu3.4); however:
  Package samba-common is not configured yet.
 samba depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on udev (>= 117-5); however:
  Package udev is not configured yet.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-data:
 kdebase-data depends on kdebase-bin (>= 4:4.1.4-0ubuntu1~intrepid2); however:
  Package kdebase-bin is not configured yet.
dpkg: error processing kdebase-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-samba:
 system-config-samba depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing system-config-samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libdns43 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); however:
  Package libdns43 is not configured yet.
 dnsutils depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not configured yet.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of soprano-daemon:
 soprano-daemon depends on libraptor1 (>= 1.4.16); however:
  Package libraptor1 is not configured yet.
 soprano-daemon depends on librdf0 (>= 1.0.6); however:
  Package librdf0 is not configured yet.
dpkg: error processing soprano-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on samba-common (= 2:3.2.3-1ubuntu3.4); however:
  Package samba-common is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsoprano4:
 libsoprano4 depends on soprano-daemon (= 2.1.1+dfsg.1-0ubuntu1); however:
  Package soprano-daemon is not configured yet.
dpkg: error processing libsoprano4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker-utils:
 tracker-utils depends on tracker (= 0.6.6-1ubuntu5.1); however:
  Package tracker is not configured yet.
dpkg: error processing tracker-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of raptor-utils:
 raptor-utils depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not configured yet.
 raptor-utils depends on libraptor1 (>= 1.4.16); however:
  Package libraptor1 is not configured yet.
dpkg: error processing raptor-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:265: process_queue: Assertion `!queue.length' failed.



please help me , I don't want to format my system

---

