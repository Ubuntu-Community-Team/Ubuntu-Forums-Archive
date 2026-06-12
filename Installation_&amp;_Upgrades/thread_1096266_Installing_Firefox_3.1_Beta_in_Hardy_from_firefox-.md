---
title: "Installing Firefox 3.1 Beta in Hardy from firefox-3.1b3.tar.bz2"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by mlnease on 2009-03-14
Hello,

I've been trying to install Firefox 3.1 Beta in Hardy from firefox-3.1b3.tar.bz2.  I'm accustomed to installing tar files via the command line using 'sudo tar -xzvf etc.'.  I gathered after some Googling that what I needed was to 

run the command 'tar -xvjf firefox-3.1b3.tar.bz2'; 

close Firefox; 

then run ~/firefox/firefox from terminal.

Here's the terminal output from step one:

firefox/
firefox/firefox
firefox/libnssdbm3.so
firefox/libnssckbi.so
firefox/application.ini
firefox/updater.ini
firefox/libnssutil3.so
firefox/libssl3.so
firefox/plugins/
firefox/plugins/libnullplugin.so
firefox/libsoftokn3.so
firefox/libsoftokn3.chk
firefox/updater
firefox/modules/
firefox/modules/ISO8601DateUtils.jsm
firefox/modules/distribution.js
firefox/modules/PluralForm.jsm
firefox/modules/Microformats.js
firefox/modules/PlacesDBUtils.jsm
firefox/modules/debug.js
firefox/modules/WindowDraggingUtils.jsm
firefox/modules/SpatialNavigation.js
firefox/modules/XPCOMUtils.jsm
firefox/modules/DownloadUtils.jsm
firefox/modules/utils.js
firefox/old-homepage-default.properties
firefox/crashreporter-override.ini
firefox/components/
firefox/components/FeedConverter.js
firefox/components/aboutSessionRestore.js
firefox/components/nsLoginManager.js
firefox/components/aboutPrivateBrowsing.js
firefox/components/jsconsole-clhandler.js
firefox/components/nsBlocklistService.js
firefox/components/nsUrlClassifierLib.js
firefox/components/libnkgnomevfs.so
firefox/components/storage-mozStorage.js
firefox/components/aboutCertError.js
firefox/components/nsTryToClose.js
firefox/components/nsHandlerService.js
firefox/components/nsURLFormatter.js
firefox/components/nsMicrosummaryService.js
firefox/components/nsContentPrefService.js
firefox/components/nsBadCertHandler.js
firefox/components/nsSessionStartup.js
firefox/components/fuelApplication.js
firefox/components/nsExtensionManager.js
firefox/components/storage-Legacy.js
firefox/components/libimgicon.so
firefox/components/nsPrivateBrowsingService.js
firefox/components/nsSafebrowsingApplication.js
firefox/components/nsContentDispatchChooser.js
firefox/components/nsSetDefaultBrowser.js
firefox/components/libmozgnome.so
firefox/components/aboutRobots.js
firefox/components/nsLivemarkService.js
firefox/components/nsBrowserGlue.js
firefox/components/nsTaggingService.js
firefox/components/nsSidebar.js
firefox/components/nsHelperAppDlg.js
firefox/components/nsBrowserContentHandler.js
firefox/components/nsUrlClassifierListManager.js
firefox/components/libbrowserdirprovider.so
firefox/components/nsWebHandlerApp.js
firefox/components/FeedWriter.js
firefox/components/nsProxyAutoConfig.js
firefox/components/nsDefaultCLH.js
firefox/components/nsLoginManagerPrompter.js
firefox/components/FeedProcessor.js
firefox/components/nsSearchSuggestions.js
firefox/components/nsPlacesDBFlush.js
firefox/components/nsSessionStore.js
firefox/components/nsDownloadManagerUI.js
firefox/components/nsSearchService.js
firefox/components/pluginGlue.js
firefox/components/nsFilePicker.js
firefox/components/nsLoginInfo.js
firefox/components/nsAddonRepository.js
firefox/components/libdbusservice.so
firefox/components/WebContentConverter.js
firefox/components/libbrowsercomps.so
firefox/components/browser.xpt
firefox/components/nsPlacesTransactionsService.js
firefox/components/nsUpdateService.js
firefox/components/aboutRights.js
firefox/components/txEXSLTRegExFunctions.js
firefox/libxpcom.so
firefox/run-mozilla.sh
firefox/libsqlite3.so
firefox/mozilla-xremote-client
firefox/libnspr4.so
firefox/Throbber-small.gif
firefox/.autoreg
firefox/libfreebl3.chk
firefox/crashreporter.ini
firefox/extensions/
firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/
firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
firefox/dictionaries/
firefox/dictionaries/en-US.dic
firefox/dictionaries/en-US.aff
firefox/libxul.so
firefox/firefox-bin
firefox/libfreebl3.so
firefox/icons/
firefox/icons/mozicon128.png
firefox/icons/mozicon16.xpm
firefox/icons/document.png
firefox/icons/mozicon50.xpm
firefox/searchplugins/
firefox/searchplugins/answers.xml
firefox/searchplugins/wikipedia.xml
firefox/searchplugins/eBay.xml
firefox/searchplugins/creativecommons.xml
firefox/searchplugins/yahoo.xml
firefox/searchplugins/google.xml
firefox/searchplugins/amazondotcom.xml
firefox/README.txt
firefox/libplc4.so
firefox/platform.ini
firefox/res/
firefox/res/forms.css
firefox/res/table-add-row-after-active.gif
firefox/res/table-add-row-after-hover.gif
firefox/res/table-add-row-before.gif
firefox/res/broken-image.gif
firefox/res/table-add-column-after-active.gif
firefox/res/unixcharset.properties
firefox/res/fonts/
firefox/res/fonts/mathfont.properties
firefox/res/fonts/mathfontStandardSymbolsL.properties
firefox/res/fonts/mathfontSTIXSize1.properties
firefox/res/fonts/mathfontUnicode.properties
firefox/res/fonts/mathfontSTIXNonUnicode.properties
firefox/res/langGroups.properties
firefox/res/contenteditable.css
firefox/res/quirk.css
firefox/res/table-add-column-before-hover.gif
firefox/res/table-add-column-after-hover.gif
firefox/res/designmode.css
firefox/res/hiddenWindow.html
firefox/res/arrow.gif
firefox/res/table-remove-column.gif
firefox/res/html/
firefox/res/html/folder.png
firefox/res/table-remove-column-hover.gif
firefox/res/arrowd.gif
firefox/res/table-remove-row-active.gif
firefox/res/dtd/
firefox/res/dtd/mathml.dtd
firefox/res/dtd/xhtml11.dtd
firefox/res/grabber.gif
firefox/res/table-remove-row-hover.gif
firefox/res/language.properties
firefox/res/viewsource.css
firefox/res/table-add-row-before-hover.gif
firefox/res/table-add-column-before.gif
firefox/res/entityTables/
firefox/res/entityTables/html40Latin1.properties
firefox/res/entityTables/mathml20.properties
firefox/res/entityTables/html40Symbols.properties
firefox/res/entityTables/html40Special.properties
firefox/res/entityTables/transliterate.properties
firefox/res/entityTables/htmlEntityVersions.properties
firefox/res/table-add-column-before-active.gif
firefox/res/charsetalias.properties
firefox/res/EditorOverride.css
firefox/res/mathml.css
firefox/res/ua.css
firefox/res/table-add-row-after.gif
firefox/res/table-add-column-after.gif
firefox/res/loading-image.gif
firefox/res/table-remove-row.gif
firefox/res/charsetData.properties
firefox/res/html.css
firefox/res/svg.css
firefox/res/table-remove-column-active.gif
firefox/res/table-add-row-before-active.gif
firefox/chrome/
firefox/chrome/reporter.jar
firefox/chrome/classic.jar
firefox/chrome/en-US.manifest
firefox/chrome/classic.manifest
firefox/chrome/pippki.manifest
firefox/chrome/en-US.jar
firefox/chrome/pippki.jar
firefox/chrome/icons/
firefox/chrome/icons/default/
firefox/chrome/icons/default/default32.png
firefox/chrome/icons/default/default48.png
firefox/chrome/icons/default/default16.png
firefox/chrome/reporter.manifest
firefox/chrome/toolkit.jar
firefox/chrome/browser.jar
firefox/chrome/comm.manifest
firefox/chrome/browser.manifest
firefox/chrome/toolkit.manifest
firefox/chrome/comm.jar
firefox/browserconfig.properties
firefox/defaults/
firefox/defaults/pref/
firefox/defaults/pref/firefox-branding.js
firefox/defaults/pref/reporter.js
firefox/defaults/pref/firefox.js
firefox/defaults/pref/channel-prefs.js
firefox/defaults/pref/firefox-l10n.js
firefox/defaults/profile/
firefox/defaults/profile/prefs.js
firefox/defaults/profile/mimeTypes.rdf
firefox/defaults/profile/bookmarks.html
firefox/defaults/profile/localstore.rdf
firefox/defaults/profile/chrome/
firefox/defaults/profile/chrome/userContent-example.css
firefox/defaults/profile/chrome/userChrome-example.css
firefox/defaults/autoconfig/
firefox/defaults/autoconfig/prefcalls.js
firefox/defaults/autoconfig/platform.js
firefox/libsmime3.so
firefox/removed-files
firefox/crashreporter
firefox/blocklist.xml
firefox/libnss3.so
firefox/greprefs/
firefox/greprefs/xpinstall.js
firefox/greprefs/all.js
firefox/greprefs/security-prefs.js
firefox/libmozjs.so
firefox/libplds4.so

I've done these steps several times now, with only the result that Firefox 3.0.7 opens as usual.  Am I missing something?  Any help much appreciated.

mike

---

### Post by taurus on 2009-03-14
Where did you save firefox-3.1b3.tar.bz2, $HOME or desktop ($HOME/Desktop)?

```
ls -la ~
ls -la ~/Desktop
```

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> Where did you save firefox-3.1b3.tar.bz2, $HOME or desktop ($HOME/Desktop)?

```
ls -la ~
ls -la ~/Desktop
```

Hi Taurus,

Thanks for the quick response.  I saved it to $HOME--would it help if I posted the terminal output from 'ls -la ~'?

mike

---

### Post by taurus on 2009-03-14
If you unpacked it in $HOME, then try

```
cd ~/firefox
./firefox
```

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> If you unpacked it in $HOME, then try

```
cd ~/firefox
./firefox
```

OK, this opened Firefox 3.0.7 again--here's the output:

mn@mn-desktop:~$ cd ~/firefox
mn@mn-desktop:~/firefox$ ./firefox
mn@mn-desktop:~/firefox$ 

Thanks again--

mike

---

### Post by taurus on 2009-03-14
So it says 3.0.7 in Help -> _A_bout Mozilla Firefox?

You sure you downloaded the 3.1b3 version?

```
ls -la ~
```

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> So it says 3.0.7 in Help -> _A_bout Mozilla Firefox?

You sure you downloaded the 3.1b3 version?

```
ls -la ~
```

Yes to both.  I noticed that there's no hidden Firefox file (./firefox) in HOME; here's a screenshot of the section of HOME containing the firefox 'folders'.

---

### Post by taurus on 2009-03-14
You have ~/firefox & ~/firefox (2).  Who's the owner of ~/firefox anyway since there is a lock on it?

Do you really need all those firefox versions on your machine or are you just trying them out to see which one you'd like?

Applications -> Accessories -> Terminal
```
ls -la ~
```

---

### Post by mlnease on 2009-03-14
You have ~/firefox & ~/firefox (2). Who's the owner of ~/firefox anyway since there is a lock on it?

    The owner is 'root'--the owner of all those locked '+nobinonly' files is '501'(?).

Do you really need all those firefox versions on your machine or are you just trying them out to see which one you'd like?

    Those have--I think--appeared as I've run updates from the Hardy notifications icon.  I'd like to be rid of them but have never known how to determine which it's safe to get rid of.  I'd like to know.--

Applications -> Accessories -> Terminal

ls -la ~

mn@mn-desktop:~$ ls -la ~
total 64340
drwxr-xr-x 160 mn    mn         12288 2009-03-14 16:02 .
drwxr-xr-x   5 root  root        4096 2008-10-17 17:08 ..
drwx------   2 mn    mn          4096 2008-07-23 18:30 .AbiSuite
drwx------   3 mn    mn          4096 2008-07-19 17:06 .adobe
drwxrwxr-x   2 mn    mn          4096 2006-10-22 12:00 all-20061022
drwxr-xr-x   6 mn    mn          4096 2008-04-10 13:17 amarok-1.4.9.1
drwxr-xr-x   5   501     501     4096 2007-09-16 02:11 Archive-Tar-1.36
drwxr-xr-x   5 mn    mn          4096 2009-02-24 14:45 Art
drwxr-xr-x   3 mn    mn          4096 2009-03-13 16:29 .audacity1.3-mn
drwxr-xr-x   5 mn    mn          4096 2009-02-25 15:01 .audacity-data
drwxrwxrwx  27 mn       1027     4096 2007-12-17 07:59 avahi-0.6.22
drwxr-xr-x   5   400     401     4096 2007-07-07 04:05 awstats-6.7
-rw-------   1 mn    mn         14426 2009-03-14 16:24 .bash_history
-rw-r--r--   1 mn    mn           220 2008-07-19 09:55 .bash_logout
-rw-r--r--   1 mn    mn          2928 2008-07-19 09:55 .bashrc
-rw-r--r--   1 mn    mn        419515 2009-03-02 16:05 Bays in summer 034.jpg
drwxr-sr-x   9  2501 mn          4096 2008-07-29 12:48 bind9-9.4.2.dfsg.P2
-rw-r--r--   1 mn    mn        295149 2009-02-23 16:54 BlueMoon.jpg
-rw-r--r--   1 mn    mn           383 2009-02-06 13:35 .BOINC Manager
drwxr-xr-x   3 mn    mn          4096 2008-07-19 10:00 .cache
drwx------   4 mn    mn          4096 2009-03-01 10:52 Capsule
-rw-r--r--   1 mn    mn        188416 2008-08-03 18:28 Cetasikas.mdb
-rw-r--r--   1 mn    mn         20751 2008-08-10 15:58 Cetasikas.ods
-rw-r--r--   1 mn    mn         27763 2008-08-10 11:02 CetasikasPali.odt
-rw-r--r--   1 mn    mn        114746 2008-08-10 11:04 CetasikasPali.pdf
-rwxrwxrwx   1 mn    mn         41472 2008-08-02 15:53 Cetasikas.xls
-rw-r--r--   1 mn    mn        212894 2008-12-14 19:51 Christ vs Klaus No 1.jpg
-rw-r--r--   1 mn    mn          2351 2009-02-06 10:22 client_state_prev.xml
-rw-r--r--   1 mn    mn          2295 2009-02-06 12:34 client_state.xml
drwx------   3 mn    mn          4096 2008-07-19 10:29 .compiz
drwxrwxrwx   8 mn    mn          4096 2008-12-15 17:20 compiz-fusion-plugins-main-0.7.4
drwxr-xr-x   9 mn    mn          4096 2008-08-28 15:33 .config
-rw-r--r--   1 mn    mn        143173 2008-08-03 21:30 Copy of Worker Men Painting 003.jpg
drwxrwxr-x  28   501 root        4096 2008-04-01 14:59 cups-1.3.7
drwxrwxrwx   8 mn    mn          4096 2008-01-28 09:29 curl-7.18.0
drwxrwxrwx   3 mn    mn          4096 2007-07-13 01:30 dash-0.5.4
drwx------   3 root  root        4096 2009-01-09 09:48 .dbus
drwxrwxrwx   7   500     500     4096 2008-02-26 10:36 dbus-1.1.20
drwxr-xr-x   2 mn    mn         12288 2009-03-14 16:02 Desktop
-rw-r--r--   1 mn    mn          8954 2008-07-24 21:08 Dhammapada 290.odt
-rw-------   1 mn    mn            28 2009-03-14 13:09 .dmrc
drwxr-xr-x   8   500 users       4096 2008-02-12 12:36 dnsmasq-2.41.orig
drwxr-xr-x   3 mn    mn          4096 2009-02-02 09:38 Documents
drwxr-xr-x   3 mn    mn          4096 2009-02-18 12:19 eaglemount
drwxr-xr-x  12   680 users       4096 2006-08-26 06:09 ekg-1.7rc2
drwxr-xr-x  14 root  root        4096 2008-11-05 10:57 enscript-1.6.4
drwxr-xr-x   5 mn    mn          4096 2008-06-14 14:05 entertainer-0.1
-rw-------   1 mn    mn            16 2008-07-19 09:59 .esd_auth
lrwxrwxrwx   1 mn    mn            26 2008-07-19 09:55 Examples -> /usr/share/example-content
drwxr-xr-x   9 mn    mn          4096 2008-01-16 00:14 exiv2-0.16.orig
drwxr-xr-x  10 mn    users       4096 2007-03-07 05:37 ffmpeg-0.cvs20070307
drwxr-xr-x  13 root  root        4096 2009-03-05 14:35 firefox
drwxr-xr-x  13 mn    mn          4096 2009-03-05 14:35 firefox (2)
drwxr-xr-x   2 mn    mn          4096 2008-11-12 11:23 firefox-2.0.0.18+nobinonly
drwxr-xr-x   2   501 mn          4096 2008-07-09 12:31 firefox-3.0-3.0.1+build1+nobinonly
drwxr-xr-x   2 mn        500     4096 2008-09-17 08:32 firefox-3.0-3.0.2+build6+nobinonly
drwxr-xr-x   2   501 mn          4096 2008-09-25 02:44 firefox-3.0-3.0.3+build1+nobinonly
drwxr-xr-x   2 mn    mn          4096 2008-11-12 07:00 firefox-3.0-3.0.4+nobinonly
drwxr-xr-x   2   501 mn          4096 2008-12-16 07:26 firefox-3.0-3.0.5+nobinonly
drwxr-xr-x   2 mn    mn          4096 2009-02-05 00:53 firefox-3.0-3.0.6+nobinonly
drwxr-xr-x   2   501 mn          4096 2009-03-04 08:28 firefox-3.0-3.0.7+nobinonly
-rw-r--r--   1 mn    mn       9763335 2009-03-14 13:02 firefox-3.1b3.tar.bz2
drwxr-xr-x   2 mn    mn          4096 2009-02-06 13:31 .fontconfig
drwxr-xr-x   2 mn    mn          4096 2009-02-06 13:30 .fonts
drwx------   2 mn    mn          4096 2008-10-08 19:10 .fr-gAMYZq
drwx------   2 mn    mn          4096 2008-10-08 19:09 .fr-Kij8j6
drwx------   5 mn    mn          4096 2009-03-14 13:09 .gconf
drwx------   2 mn    mn          4096 2009-03-14 16:25 .gconfd
drwxr-xr-x  22 mn    mn          4096 2009-03-14 12:36 .gimp-2.4
drwxrwxr-x  15 root  root       12288 2008-02-23 12:43 git-1.5.4.3
-rw-r-----   1 mn    mn             0 2009-03-14 12:08 .gksu.lock
drwx------  16 mn    mn          4096 2009-03-14 13:07 .gnome2
drwx------   2 mn    mn          4096 2008-07-19 09:59 .gnome2_private
drwx------   2 mn    mn          4096 2009-03-14 13:09 .gnupg
drwxrwxrwx  14 root  root        4096 2007-11-16 06:52 gnutls-2.0.4
drwxr-xr-x   2 mn    mn          4096 2008-09-14 18:05 .gpilotd
-rw-r--r--   1 mn    mn             4 2008-09-14 18:05 .gpilotd.pid
drwxr-xr-x   2 mn    mn          4096 2009-02-06 16:05 .gstreamer-0.10
-rw-r--r--   1 mn    mn           125 2009-03-14 13:11 .gtk-bookmarks
-rw-------   1 mn    mn            32 2009-02-06 10:22 gui_rpc_auth.cfg
dr-x------   2 mn    mn             0 2009-03-14 13:09 .gvfs
drwxr-xr-x   2 mn    mn          4096 2008-07-20 13:21 .helix
drwxrwxrwx  18 mn    mn          4096 2008-02-08 18:08 hplip-2.8.2
-rw-r--r--   1 mn    mn         57741 2009-01-12 19:57 hs_err_pid6215.log
-rw-r--r--   1 mn    mn           204 2009-01-26 13:32 hsqlprefs.dat
drwxr-xr-x  11   501 staff       4096 2008-01-10 08:54 httpd-2.2.8
-rw-------   1 mn    mn          7183 2009-03-14 13:09 .ICEauthority
-rw-------   1 mn    mn          2006 2008-10-08 14:26 .ICEauthority.before_restore_2008-10-08_14.28.49.320392
drwxr-xr-x   2 mn    mn          4096 2008-07-19 10:12 .icons
drwxr-sr-x   5 mn    mn          4096 2007-11-24 18:28 imlib2-1.4.0.orig
-rw-r--r--   1 mn    mn          1752 2008-07-21 11:35 index.html
drwxr-xr-x   2   501 users       4096 2008-03-24 19:02 install_flash_player_9_linux
-rw-r--r--   1 mn    mn           159 2008-07-21 12:10 Install w32codecs
drwxrwxrwx   4   500     500     4096 2007-04-06 02:07 ipsec-tools-0.6.7
drwxr-xr-x   3 mn    mn          4096 2009-01-16 12:37 .java
-rw-r--r--   1 mn    mn       2890855 2009-03-02 15:51 June'07 005.jpg
drwx------   4 mn    mn          4096 2008-11-24 18:28 .kde
drwxr-xr-x  46 mn    mn          4096 2008-08-20 08:25 kdepim-3.5.10
drwxr-xr-x   2 mn    mn          4096 2009-01-27 19:35 Kerouac
drwxr-xr-x   9 mn    mn          4096 2008-01-27 04:21 ktorrent-2.2.5
-rw-r--r--   1 root  root       40728 2008-07-21 15:19 lanmap.png
drwxr-xr-x   5 mn    mn          4096 2008-08-18 13:56 lbm
drwxrwxrwx  15  1003     513     4096 2006-12-13 03:39 lcms-1.16
drwxr-xr-x   5  1004 libuuid     4096 2006-12-07 17:21 libpng-1.2.15beta5
drwxrwxrwx  14 50138      69     4096 2007-12-17 15:44 libvirt-0.4.0
drwxr-xr-x  11 mn    mn          4096 2007-07-25 09:46 libvorbis-1.2.0
drwxr-xr-x  11 mn    mn          4096 2008-01-19 08:14 libxml2-2.6.31
drwxrwxrwx  11 50138      69     4096 2007-08-23 08:24 libxslt-1.1.22
drwxr-xr-x   4 mn    mn          4096 2009-03-07 13:20 LimeWire
drwxr-xr-x   8 mn    mn          4096 2009-03-10 19:46 .limewire
drwxrwxr-x  20 root  root        4096 2008-02-10 21:51 linux-2.6.24.2
drwxrwxr-x  15 mn    mn          4096 2008-07-10 16:05 linux-restricted-modules-2.6.24-2.6.24.14
-rw-r--r--   1 mn    mn         77349 2009-01-05 20:26 LittleMatchGirl
drwxr-xr-x   3 mn    mn          4096 2008-07-19 10:00 .local
-rw-r--r--   1 mn    mn             0 2009-02-06 10:22 lockfile
drwxr-xr-x   5 mn    mn          4096 2008-11-06 00:41 lum
drwx------   3 mn    mn          4096 2008-07-19 17:06 .macromedia
-rw-r--r--   1 mn    mn          3146 2008-12-29 10:14 .mailcap
drwxr-xr-x   3 mn    mn          4096 2008-11-25 13:31 .mcop
-rw-------   1 mn    mn            31 2009-03-07 17:33 .mcoprc
drwx------   3 mn    mn          4096 2008-07-19 11:59 .metacity
drwxr-xr-x   2 mn    mn          4096 2008-11-15 14:36 .mhwaveedit
drwxr-xr-x  53 mn    mn          4096 2008-06-04 11:33 midbrowser-0.3.0rc1a
-rw-r--r--   1 mn    mn          6399 2008-08-01 11:30 mn avatar.gif
drwxrwxr-x   7 guest guest       4096 2007-05-12 15:28 moin-1.5.8
drwxr-xr-x  33 root  root        4096 2007-07-08 07:18 moodle
drwx------   5 mn    mn          4096 2008-07-19 17:06 .mozilla
-rw-r--r--   1 mn    mn        885564 2009-02-19 13:58 mozilla.ps
drwx------   3 mn    mn          4096 2008-07-19 15:04 .mozilla-thunderbird
drwxr-xr-x   3 root  root        4096 2008-07-25 17:32 mozilla-thunderbird-1.5.0.13+1.5.0.15~prepatch080614d
drwxr-xr-x   2 mn    mn          4096 2009-01-31 22:19 .mplayer
drwxr-xr-x   2 mn    mn          4096 2009-03-05 18:05 Music
drwxrwxr-x  11   501     501     4096 2008-03-12 07:07 nagios-2.11
drwxr-sr-x  12   802     900     4096 2007-11-01 15:01 nasm-0.99.06-20071101
drwxr-xr-x   3 mn    mn         12288 2009-03-14 13:07 .nautilus
drwxr-sr-x  15 mn    staff       4096 2007-08-02 05:42 net-snmp-5.4.1
drwxr-xr-x   7   501 mn          4096 2008-03-07 02:31 network-manager-applet-0.6.6
drwxr-xr-x   2 mn    mn          4096 2008-09-01 17:21 .new
-rw-r--r--   1 mn    mn          2924 2008-08-03 18:28 New Database.odb
drwxr-xr-x   7  3606    3606     4096 2008-03-14 10:44 nfs-utils-1.1.2
drwxrwxr-x  21  1012    2000     4096 2007-10-11 01:32 ntp-4.2.4p4
drwx------   3 mn    mn          4096 2009-03-04 13:11 .openoffice.org2
drwxr-xr-x   3 mn    mn          4096 2008-05-30 03:52 openoffice.org-2.4.1
drwxr-xr-x  22 root  root        4096 2009-01-07 14:43 openssl-0.9.8g
drwx------   4 mn    mn          4096 2009-02-02 18:40 P&#257;&#7735;i
-rwx------   1 mn    mn        912502 2008-07-19 10:24 palidict.zip
-rw-rw-rw-   1 mn    mn       2715652 2000-07-07 14:00 Pali English Dictionary 1.pwa
-rwx------   1 mn    mn        146489 2008-07-19 10:24 Paliwords 4.0.zip
-rwxrwxrwx   1 mn    mn        311296 2008-07-22 09:44 paliwords.exe
drwxr-xr-x   4 mn    root        4096 2007-12-28 21:43 pam-krb5-3.10
drwx------   2 mn    mn          4096 2008-12-03 16:43 PDF
drwxr-xr-x   2 mn    mn          4096 2008-08-10 10:26 .pdfedit
drwxr-xr-x  31  1013    1013    12288 2006-01-31 15:40 perl-5.8.8
drwxr-xr-x  14 rose  rose        4096 2007-08-29 16:39 php-5.2.4
drwxr-xr-x   7 mn    mn          4096 2009-03-12 17:56 Pictures
drwxrwxrwx   9   500     500     4096 2008-03-31 10:23 pidgin-2.4.1
drwxr-xr-x   4 mn    mn          4096 2009-03-05 10:44 Politics
drwxrwxrwx  12 mn    mn          4096 2008-01-25 14:12 poppler-0.6.4
drwxr-xr-x  16 guest root        4096 2008-01-23 17:50 postfix-2.5.1
-rw-r--r--   1 mn    mn           586 2008-07-19 09:55 .profile
drwxr-xr-x   2 mn    mn          4096 2008-07-19 09:59 Public
drwxr-xr-x   2 mn    mn          4096 2008-10-08 14:29 .pulse
-rw-------   1 mn    mn           256 2008-07-19 09:59 .pulse-cookie
drwx------   5 mn    mn          4096 2008-11-19 22:08 .purple
drwxr-sr-x  11 mn    mn          4096 2004-08-14 03:49 pycrypto-2.0
drwxr-xr-x  18 mn    mn          4096 2008-02-21 03:55 python2.5-2.5.2
drwxr-xr-x   2 mn    mn          4096 2009-03-07 17:33 .qt
drwxr-xr-x   4 root  root        4096 2008-09-19 10:28 rdesktop-1.5.0
-rwx------   1 root  root     7170068 2006-01-24 00:05 ReaderLinux
-rw-------   1 mn    mn         14398 2009-02-19 14:00 .recently-used
-rw-r--r--   1 mn    mn         36721 2009-03-14 16:02 .recently-used.xbel
-rw-r--r--   1 mn    mn          3099 2008-10-08 14:24 .recently-used.xbel.before_restore_2008-10-08_14.28.49.320392
-rw-r--r--   1 mn    mn           237 2009-03-14 11:24 .registry
drwxr-xr-x  17 10347   10347     4096 2007-10-03 19:54 ruby-1.8.6-p111
drwxrwxr-x   4 mn    mn          4096 2002-05-17 07:03 rv9
drwxr-xr-x   3 mn    mn          4096 2008-12-07 11:31 .scribus
drwxrwxr-x  10 mn    mn          4096 2007-10-28 11:19 shadow-4.0.18.2
-rwxr-xr-x   1 mn    admin       1344 2008-05-13 05:32 shortcut-install
-rwxr-xr-x   1 mn    admin       1303 2008-05-13 05:32 shortcut-uninstall
drwx------   3 mn    mn          4096 2009-03-14 16:23 .Skype
drwx------   2 mn    mn          4096 2008-07-19 09:59 .ssh
drwxr-xr-x   2 mn    mn          4096 2009-03-03 17:50 .stellarium
drwxr-xr-x  15 root  root        4096 2009-03-03 17:19 stellarium-0.10.1
drwxr-xr-x   4 root  root        4096 2009-02-18 12:17 sudo-1.6.9p10
-rw-r--r--   1 mn    mn             0 2008-07-19 10:02 .sudo_as_admin_successful
drwxr-xr-x   2 mn    mn          4096 2008-07-19 09:59 Templates
drwxr-xr-x   2 mn    mn          4096 2008-07-19 10:12 .themes
drwx------   5 mn    mn          4096 2008-07-21 07:16 .thumbnails
drwxr-xr-x  13 root  root        4096 2008-04-21 09:33 thunderbird
drwxr-xr-x   2 root  root        4096 2009-01-07 15:22 thunderbird-2.0.0.19+nobinonly
drwxr-xr-x   2 root  root        4096 2008-11-25 19:02 thunderbird.gutsy
drwxr-xr-x   2 mn    mn          4096 2008-09-03 12:40 tiff-3.8.2
-rw-r--r--   1 mn    mn             0 2009-02-06 10:22 time_stats_log
drwxr-xr-x   5 mn    mn          4096 2008-08-02 19:20 .transmission
-rw-r--r--   1 mn    mn          4944 2008-12-06 17:24 Triumphant Plutocracy.abw
-rw-r--r--   1 mn    mn           503 2008-12-28 11:56 Triumphant Plutrocacy.text
drwxr-xr-x   5 mn    mn          4096 2008-05-07 03:40 ubuntu-tweak-0.3.1.orig
-rw-------   1 mn    mn       9424837 2008-12-12 17:44 Underdog.flv
-rw-r--r--   1 mn    mn      21325824 2008-12-13 14:28 Underdog.mpeg
drwxr-xr-x   2 mn    mn          4096 2008-07-19 11:26 .update-manager-core
drwx------   2 mn    mn          4096 2008-07-21 12:05 .update-notifier
drwxr-xr-x   2 mn    mn          4096 2008-12-31 07:43 Videos
drwxr-xr-x   3 root  root        4096 2009-01-28 17:40 vim-7.1
drwxrwxrwx   6 mn    mn          4096 2008-04-07 06:13 vinagre-0.5.1
drwxr-xr-x   2 mn    mn          4096 2009-03-13 15:07 .wapi
-rw-------   1 mn    mn       7482778 2008-12-28 22:17 Who Owns You.flv
drwxr-xr-x   4 mn    mn          4096 2009-03-07 15:20 .wine
-rw-------   1 mn    mn           244 2009-03-14 13:09 .Xauthority
-rw-------   1 mn    mn           121 2008-10-08 14:26 .Xauthority.before_restore_2008-10-08_14.28.49.320392
drwx------   4 mn    mn          4096 2008-12-24 13:14 .xchat2
drwxrwxrwx  10 mn    mn          4096 2008-03-30 07:03 xine-lib-1.1.11.1
-rw-r--r--   1 mn    mn          7156 2009-03-14 16:21 .xsession-errors
-rw-r--r--   1 mn    mn         22084 2008-10-08 14:32 .xsession-errors.before_restore_2008-10-08_14.28.49.320392
drwxr-xr-x   6 guest users       4096 2007-08-12 16:29 xterm-229
drwxr-xr-x   3   501 mn          4096 2008-07-09 12:27 xulrunner-1.9-1.9.0.1+build1+nobinonly
drwxr-xr-x   3 mn        500     4096 2008-09-17 08:19 xulrunner-1.9-1.9.0.2+build6+nobinonly
drwxr-xr-x   3 root  root        4096 2008-09-24 18:41 xulrunner-1.9-1.9.0.3+build1+nobinonly
drwxr-xr-x   3 mn    mn          4096 2008-11-12 08:00 xulrunner-1.9-1.9.0.4+nobinonly
drwxr-xr-x   3   501 mn          4096 2008-12-16 08:18 xulrunner-1.9-1.9.0.5+nobinonly
drwxr-xr-x   3 mn    mn          4096 2009-02-05 01:39 xulrunner-1.9-1.9.0.6+nobinonly
drwxr-xr-x   3   501 mn          4096 2009-03-04 09:06 xulrunner-1.9-1.9.0.7+nobinonly
-rw-r--r--   1 mn    mn         20971 2009-01-08 17:20 ya.aup
-rw-r--r--   1 mn    mn         20969 2008-11-16 18:35 ya.aup~
drwxrwxr-x   3 mn    mn          4096 2008-11-16 18:35 ya_data
drwxrwxrwx   7 11834 users       4096 2008-04-07 15:05 yelp-2.22.1
-rw-r--r--   1 mn    mn         42821 2008-08-13 15:10 Young Guns.doc

---

### Post by taurus on 2009-03-14
Try these.

```
mv firefox-3.1b3.tar.bz2 Desktop
cd Desktop
tar xvjf firefox-3.1b3.tar.bz2
cd firefox
./firefox
```
What version of firefox is running right now?

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> Try these.

```
mv firefox-3.1b3.tar.bz2 Desktop
cd Desktop
tar xvjf firefox-3.1b3.tar.bz2
cd firefox
./firefox
```
What version of firefox is running right now?

Done--still opening 3.0.7.  I suppose this problem has to do with all these extra firefox files?  Can you advise me as to how to determine which I can delete without breaking anything?  I could stand to risk losing my bookmarks and can't think of any other data I'd lose, off-hand.

---

### Post by taurus on 2009-03-14
All your personal settings should be in ~/.mozilla/firefox.  Personally, I would remove all of them.  Then, unpack the new version (and only version), firefox-3.1b3.tar.bz2, and try to run it again.  

By the way, which release are you running and did you install Ubuntu on it own partition?

```
lsb_release -a
sudo fdisk -l
df -h
```

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> All your personal settings should be in ~/.mozilla/firefox.  Personally, I would remove all of them.  Then, unpack the new version (and only version), firefox-3.1b3.tar.bz2, and try to run it again.  

will do--

By the way, which release are you running and did you install Ubuntu on it own partition?

```
lsb_release -a
sudo fdisk -l
df -h
```

mn@mn-desktop:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:core-3.2-ia32:core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-3.2-noarch:cxx-2.0-ia32:cxx-3.0-ia32:cxx-3.1-ia32:cxx-3.2-ia32:cxx-2.0-noarch:cxx-3.0-noarch:cxx-3.1-noarch:cxx-3.2-noarch:desktop-3.1-ia32:desktop-3.2-ia32:desktop-3.1-noarch:desktop-3.2-noarch:graphics-2.0-ia32:graphics-3.0-ia32:graphics-3.1-ia32:graphics-3.2-ia32:graphics-2.0-noarch:graphics-3.0-noarch:graphics-3.1-noarch:graphics-3.2-noarch:languages-3.2-ia32:languages-3.2-noarch:multimedia-3.2-ia32:multimedia-3.2-noarch:printing-3.2-ia32:printing-3.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
mn@mn-desktop:~$ sudo fdisk -l
[sudo] password for mn: 

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58514e3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4686    37640263+  83  Linux
/dev/sda2            4687        4870     1477980    5  Extended
/dev/sda5            4687        4870     1477948+  82  Linux swap / Solaris

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> All your personal settings should be in ~/.mozilla/firefox.  Personally, I would remove all of them.  Then, unpack the new version (and only version), firefox-3.1b3.tar.bz2, and try to run it again.  

By the way, which release are you running and did you install Ubuntu on it own partition?

```
lsb_release -a
sudo fdisk -l
df -h
```

I removed all of them, ran:

mv firefox-3.1b3.tar.bz2 Desktop
cd Desktop
tar xvjf firefox-3.1b3.tar.bz2
cd firefox
./firefox

and got 3.0.7 again.  Baffling...

---

### Post by taurus on 2009-03-14
Do you already have firefox installed on your machine?

```
whereis firefox
```

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> Do you already have firefox installed on your machine?

```
whereis firefox
```

mn@mn-desktop:~$ whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /usr/share/firefox
mn@mn-desktop:~$

---

### Post by taurus on 2009-03-14
See which version is this one?

```
/usr/bin/firefox
```

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> see which version is this one?

```
/usr/bin/firefox
```

3.0.7

---

### Post by taurus on 2009-03-14
Can you remove it from your machine with either add/remove or synaptic?  Then, run the one that you've unpacked and see what happens.

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> Can you remove it from your machine with either add/remove or synaptic?  Then, run the one that you've unpacked and see what happens.

Bravo, Taurus--that seems to've done the trick.  I'm writing to you now from Firefox/3.1b3.  I could only open it, though, from terminal:

mn@mn-desktop:~$ cd firefox
mn@mn-desktop:~/firefox$ ./firefox

And it doesn't appear under applications > internet.  I'd like to be able to place a link to it in Gnome panel--any tips?

Thanks a million for all your patience and perseverance.  I guess, ultimately, the answer is simply to remove all other Firefox versions completely before installing 3.1b3.

mike

---

### Post by taurus on 2009-03-14
You can create a launcher on the top panel.  Place a mouse cursor on the top panel and click the right button -> Add to Panel -> Custom Application Launcher -> Add 

Name:  Firefox 3.1b3
Command:  ~/firefox/firefox
 
then OK.  Now, you just have to click on the icon to run firefox.

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> You can create a launcher on the top panel.  Place a mouse cursor on the top panel and click the right button -> Add to Panel -> Custom Application Launcher -> Add 

Name:  Firefox 3.1b3
Command:  ~/firefox/firefox
 
then OK.  Now, you just have to click on the icon to run firefox.

Taurus, yer a prince.  I'd figured this out once before for a Wine app, but assumed Firefox would be accessible more conventionally.  Thanks again for everything!

---

### Post by sgosnell on 2009-03-14
That's the problem with doing things this way - Firefox 3.1 beta isn't installed, it's just sitting in your home directory.  That's fine for just trying it out, but it has side effects as you've discovered.  The firefox directory is not in the path, so the system has no idea it's there.

---

### Post by mlnease on 2009-03-14
> **sgosnell said:**
> That's the problem with doing things this way - Firefox 3.1 beta isn't installed, it's just sitting in your home directory.  That's fine for just trying it out, but it has side effects as you've discovered.  The firefox directory is not in the path, so the system has no idea it's there.

I see--do you have time to tell me how to actually install it?

p.s.  Thanks for your interest, sgosnell--it took me a minute to realize you were a new respondent.

---

### Post by taurus on 2009-03-14
If you want to add that new firefox to your path, just edit ~/.bashrc

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:~/firefox
export PATH
```
Save it and then run

```
source ~/.bashrc
```
~/firefox is now in your path.

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> If you want to add that new firefox to your path, just edit ~/.bashrc

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:~/firefox
export PATH
```
Save it and then run

```
source ~/.bashrc
```
~/firefox is now in your path.

OK, Taurus, done--thanks again.  Er--I don't see any difference?  Sorry to be obtuse.

---

### Post by taurus on 2009-03-14
It only adds ~/firefox to your PATH so you can run it anywhere you want without typing in the whole path.  If you want it to appear on the Applications -> Internet, look in System -> Preferences -> Main Menu.

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> It only adds ~/firefox to your PATH so you can run it anywhere you want without typing in the whole path.  If you want it to appear on the Applications -> Internet, look in System -> Preferences -> Main Menu.

OK, here's what I got--thanks yet again for your patience--

---

### Post by taurus on 2009-03-14
Click Internet on the left window.  Then, **+ Ne_w_ Item**.  I think you know how to fill out those fields now.

---

### Post by mlnease on 2009-03-14
> **taurus said:**
> Click Internet on the left window.  Then, **+ Ne_w_ Item**.  I think you know how to fill out those fields now.

Yep.  Got it. Thanks.  Note the tiny brain.

---

