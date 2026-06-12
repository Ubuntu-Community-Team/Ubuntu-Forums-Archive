---
title: "[SOLVED] ldconfig problem"
date: 2008-09-01
forum: General Help
---

### Post by onurphp on 2008-09-01
Kubuntu - Linux exit 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

i deleted my /usr/lib/libmysql* files manually.
And i get them another computer with other libs.
and i have got this error when i execute "ldconfig" command

how can i solve that problem ? ( i lookup mini-solution )

Output of "ldconfig" command:
[http://pastebin.ca/1188498](http://pastebin.ca/1188498)

Regards,

---

### Post by onurphp on 2008-09-01
[PHP]<?php

$lines	= file('a.txt');

foreach($lines as $line)
{
	if(trim($line) == "") continue; 
	preg_match('#ldconfig.real: (.*?) is not a symbolic link#',$line,$matches);
	$command[]	= 'mv '.trim($matches[1]).' '.trim($matches[1]).'.modified && ln -s '.trim($matches[1]).'.modified '.trim($matches[1]);
}
print join('<br>',$command);
?>[/PHP]


```
mv /usr/lib/libgnomekbdui.so.2 /usr/lib/libgnomekbdui.so.2.modified && ln -s /usr/lib/libgnomekbdui.so.2.modified /usr/lib/libgnomekbdui.so.2
mv /usr/lib/libedata-book-1.2.so.2 /usr/lib/libedata-book-1.2.so.2.modified && ln -s /usr/lib/libedata-book-1.2.so.2.modified /usr/lib/libedata-book-1.2.so.2
mv /usr/lib/libgvfscommon.so.0 /usr/lib/libgvfscommon.so.0.modified && ln -s /usr/lib/libgvfscommon.so.0.modified /usr/lib/libgvfscommon.so.0
mv /usr/lib/libgnome-window-settings.so.1 /usr/lib/libgnome-window-settings.so.1.modified && ln -s /usr/lib/libgnome-window-settings.so.1.modified /usr/lib/libgnome-window-settings.so.1
mv /usr/lib/libsndfile.so.1 /usr/lib/libsndfile.so.1.modified && ln -s /usr/lib/libsndfile.so.1.modified /usr/lib/libsndfile.so.1
mv /usr/lib/libnm_glib.so.0 /usr/lib/libnm_glib.so.0.modified && ln -s /usr/lib/libnm_glib.so.0.modified /usr/lib/libnm_glib.so.0
mv /usr/lib/libpulse-browse.so.0 /usr/lib/libpulse-browse.so.0.modified && ln -s /usr/lib/libpulse-browse.so.0.modified /usr/lib/libpulse-browse.so.0
mv /usr/lib/libespeak.so.1 /usr/lib/libespeak.so.1.modified && ln -s /usr/lib/libespeak.so.1.modified /usr/lib/libespeak.so.1
mv /usr/lib/libalut.so.0 /usr/lib/libalut.so.0.modified && ln -s /usr/lib/libalut.so.0.modified /usr/lib/libalut.so.0
mv /usr/lib/libgpilotd.so.2 /usr/lib/libgpilotd.so.2.modified && ln -s /usr/lib/libgpilotd.so.2.modified /usr/lib/libgpilotd.so.2
mv /usr/lib/libgnomekbd.so.2 /usr/lib/libgnomekbd.so.2.modified && ln -s /usr/lib/libgnomekbd.so.2.modified /usr/lib/libgnomekbd.so.2
mv /usr/lib/libgdict-1.0.so.5 /usr/lib/libgdict-1.0.so.5.modified && ln -s /usr/lib/libgdict-1.0.so.5.modified /usr/lib/libgdict-1.0.so.5
mv /usr/lib/librarian.so.0 /usr/lib/librarian.so.0.modified && ln -s /usr/lib/librarian.so.0.modified /usr/lib/librarian.so.0
mv /usr/lib/libebook-1.2.so.9 /usr/lib/libebook-1.2.so.9.modified && ln -s /usr/lib/libebook-1.2.so.9.modified /usr/lib/libebook-1.2.so.9
mv /usr/lib/libedataserverui-1.2.so.8 /usr/lib/libedataserverui-1.2.so.8.modified && ln -s /usr/lib/libedataserverui-1.2.so.8.modified /usr/lib/libedataserverui-1.2.so.8
mv /usr/lib/libpolkit-gnome.so.0 /usr/lib/libpolkit-gnome.so.0.modified && ln -s /usr/lib/libpolkit-gnome.so.0.modified /usr/lib/libpolkit-gnome.so.0
mv /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.7.modified && ln -s /usr/lib/libgtop-2.0.so.7.modified /usr/lib/libgtop-2.0.so.7
mv /usr/lib/libmono.so.0 /usr/lib/libmono.so.0.modified && ln -s /usr/lib/libmono.so.0.modified /usr/lib/libmono.so.0
mv /usr/lib/libgtk-vnc-1.0.so.0 /usr/lib/libgtk-vnc-1.0.so.0.modified && ln -s /usr/lib/libgtk-vnc-1.0.so.0.modified /usr/lib/libgtk-vnc-1.0.so.0
mv /usr/lib/libotr.so.2 /usr/lib/libotr.so.2.modified && ln -s /usr/lib/libotr.so.2.modified /usr/lib/libotr.so.2
mv /usr/lib/libgnome-mag.so.2 /usr/lib/libgnome-mag.so.2.modified && ln -s /usr/lib/libgnome-mag.so.2.modified /usr/lib/libgnome-mag.so.2
mv /usr/lib/libdns.so.35 /usr/lib/libdns.so.35.modified && ln -s /usr/lib/libdns.so.35.modified /usr/lib/libdns.so.35
mv /usr/lib/libpanel-applet-2.so.0 /usr/lib/libpanel-applet-2.so.0.modified && ln -s /usr/lib/libpanel-applet-2.so.0.modified /usr/lib/libpanel-applet-2.so.0
mv /usr/lib/libgtksourceview-1.0.so.0 /usr/lib/libgtksourceview-1.0.so.0.modified && ln -s /usr/lib/libgtksourceview-1.0.so.0.modified /usr/lib/libgtksourceview-1.0.so.0
mv /usr/lib/libgnome-desktop-2.so.2 /usr/lib/libgnome-desktop-2.so.2.modified && ln -s /usr/lib/libgnome-desktop-2.so.2.modified /usr/lib/libgnome-desktop-2.so.2
mv /usr/lib/libggzcore.so.9 /usr/lib/libggzcore.so.9.modified && ln -s /usr/lib/libggzcore.so.9.modified /usr/lib/libggzcore.so.9
mv /usr/lib/libpurple.so.0 /usr/lib/libpurple.so.0.modified && ln -s /usr/lib/libpurple.so.0.modified /usr/lib/libpurple.so.0
mv /usr/lib/libcdio_cdda.so.0 /usr/lib/libcdio_cdda.so.0.modified && ln -s /usr/lib/libcdio_cdda.so.0.modified /usr/lib/libcdio_cdda.so.0
mv /usr/lib/libgtkhtml-3.14.so.19 /usr/lib/libgtkhtml-3.14.so.19.modified && ln -s /usr/lib/libgtkhtml-3.14.so.19.modified /usr/lib/libgtkhtml-3.14.so.19
mv /usr/lib/libavahi-ui.so.0 /usr/lib/libavahi-ui.so.0.modified && ln -s /usr/lib/libavahi-ui.so.0.modified /usr/lib/libavahi-ui.so.0
mv /usr/lib/libportaudio.so.0 /usr/lib/libportaudio.so.0.modified && ln -s /usr/lib/libportaudio.so.0.modified /usr/lib/libportaudio.so.0
mv /usr/lib/libmono-profiler-aot.so.0 /usr/lib/libmono-profiler-aot.so.0.modified && ln -s /usr/lib/libmono-profiler-aot.so.0.modified /usr/lib/libmono-profiler-aot.so.0
mv /usr/lib/libexchange-storage-1.2.so.3 /usr/lib/libexchange-storage-1.2.so.3.modified && ln -s /usr/lib/libexchange-storage-1.2.so.3.modified /usr/lib/libexchange-storage-1.2.so.3
mv /usr/lib/libeel-2.so.2 /usr/lib/libeel-2.so.2.modified && ln -s /usr/lib/libeel-2.so.2.modified /usr/lib/libeel-2.so.2
mv /usr/lib/libkpathsea.so.4 /usr/lib/libkpathsea.so.4.modified && ln -s /usr/lib/libkpathsea.so.4.modified /usr/lib/libkpathsea.so.4
mv /usr/lib/libmetacity-private.so.0 /usr/lib/libmetacity-private.so.0.modified && ln -s /usr/lib/libmetacity-private.so.0.modified /usr/lib/libmetacity-private.so.0
mv /usr/lib/libgpilotdconduit.so.2 /usr/lib/libgpilotdconduit.so.2.modified && ln -s /usr/lib/libgpilotdconduit.so.2.modified /usr/lib/libgpilotdconduit.so.2
mv /usr/lib/libenchant.so.1 /usr/lib/libenchant.so.1.modified && ln -s /usr/lib/libenchant.so.1.modified /usr/lib/libenchant.so.1
mv /usr/lib/libegroupwise-1.2.so.13 /usr/lib/libegroupwise-1.2.so.13.modified && ln -s /usr/lib/libegroupwise-1.2.so.13.modified /usr/lib/libegroupwise-1.2.so.13
mv /usr/lib/libguilereadline-v-12.so.12 /usr/lib/libguilereadline-v-12.so.12.modified && ln -s /usr/lib/libguilereadline-v-12.so.12.modified /usr/lib/libguilereadline-v-12.so.12
mv /usr/lib/libgnome-menu.so.2 /usr/lib/libgnome-menu.so.2.modified && ln -s /usr/lib/libgnome-menu.so.2.modified /usr/lib/libgnome-menu.so.2
mv /usr/lib/libevbackend.so.0 /usr/lib/libevbackend.so.0.modified && ln -s /usr/lib/libevbackend.so.0.modified /usr/lib/libevbackend.so.0
mv /usr/lib/libarchive.so.2 /usr/lib/libarchive.so.2.modified && ln -s /usr/lib/libarchive.so.2.modified /usr/lib/libarchive.so.2
mv /usr/lib/liblpint-bonobo.so.0 /usr/lib/liblpint-bonobo.so.0.modified && ln -s /usr/lib/liblpint-bonobo.so.0.modified /usr/lib/liblpint-bonobo.so.0
mv /usr/lib/libcryptui.so.0 /usr/lib/libcryptui.so.0.modified && ln -s /usr/lib/libcryptui.so.0.modified /usr/lib/libcryptui.so.0
mv /usr/lib/libbeagle.so.1 /usr/lib/libbeagle.so.1.modified && ln -s /usr/lib/libbeagle.so.1.modified /usr/lib/libbeagle.so.1
mv /usr/lib/libpisock.so.9 /usr/lib/libpisock.so.9.modified && ln -s /usr/lib/libpisock.so.9.modified /usr/lib/libpisock.so.9
mv /usr/lib/libloginhelper.so.0 /usr/lib/libloginhelper.so.0.modified && ln -s /usr/lib/libloginhelper.so.0.modified /usr/lib/libloginhelper.so.0
mv /usr/lib/libgweather.so.1 /usr/lib/libgweather.so.1.modified && ln -s /usr/lib/libgweather.so.1.modified /usr/lib/libgweather.so.1
mv /usr/lib/libcdio_paranoia.so.0 /usr/lib/libcdio_paranoia.so.0.modified && ln -s /usr/lib/libcdio_paranoia.so.0.modified /usr/lib/libcdio_paranoia.so.0
mv /usr/lib/libgtkspell.so.0 /usr/lib/libgtkspell.so.0.modified && ln -s /usr/lib/libgtkspell.so.0.modified /usr/lib/libgtkspell.so.0
mv /usr/lib/libgdata-google-1.2.so.1 /usr/lib/libgdata-google-1.2.so.1.modified && ln -s /usr/lib/libgdata-google-1.2.so.1.modified /usr/lib/libgdata-google-1.2.so.1
mv /usr/lib/libguile-ltdl.so.1 /usr/lib/libguile-ltdl.so.1.modified && ln -s /usr/lib/libguile-ltdl.so.1.modified /usr/lib/libguile-ltdl.so.1
mv /usr/lib/libgnome-media-profiles.so.0 /usr/lib/libgnome-media-profiles.so.0.modified && ln -s /usr/lib/libgnome-media-profiles.so.0.modified /usr/lib/libgnome-media-profiles.so.0
mv /usr/lib/libpulsecore.so.5 /usr/lib/libpulsecore.so.5.modified && ln -s /usr/lib/libpulsecore.so.5.modified /usr/lib/libpulsecore.so.5
mv /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-2.0.so.0.modified && ln -s /usr/lib/libgtksourceview-2.0.so.0.modified /usr/lib/libgtksourceview-2.0.so.0
mv /usr/lib/libsoup-2.4.so.1 /usr/lib/libsoup-2.4.so.1.modified && ln -s /usr/lib/libsoup-2.4.so.1.modified /usr/lib/libsoup-2.4.so.1
mv /usr/lib/libggz.so.2 /usr/lib/libggz.so.2.modified && ln -s /usr/lib/libggz.so.2.modified /usr/lib/libggz.so.2
mv /usr/lib/libscrollkeeper.so.0 /usr/lib/libscrollkeeper.so.0.modified && ln -s /usr/lib/libscrollkeeper.so.0.modified /usr/lib/libscrollkeeper.so.0
mv /usr/lib/libgnomespeech.so.7 /usr/lib/libgnomespeech.so.7.modified && ln -s /usr/lib/libgnomespeech.so.7.modified /usr/lib/libgnomespeech.so.7
mv /usr/lib/libtrackerclient.so.0 /usr/lib/libtrackerclient.so.0.modified && ln -s /usr/lib/libtrackerclient.so.0.modified /usr/lib/libtrackerclient.so.0
mv /usr/lib/liboobs-1.so.4 /usr/lib/liboobs-1.so.4.modified && ln -s /usr/lib/liboobs-1.so.4.modified /usr/lib/liboobs-1.so.4
mv /usr/lib/libecal-1.2.so.7 /usr/lib/libecal-1.2.so.7.modified && ln -s /usr/lib/libecal-1.2.so.7.modified /usr/lib/libecal-1.2.so.7
mv /usr/lib/libgksu2.so.0 /usr/lib/libgksu2.so.0.modified && ln -s /usr/lib/libgksu2.so.0.modified /usr/lib/libgksu2.so.0
mv /usr/lib/libmono-profiler-cov.so.0 /usr/lib/libmono-profiler-cov.so.0.modified && ln -s /usr/lib/libmono-profiler-cov.so.0.modified /usr/lib/libmono-profiler-cov.so.0
mv /usr/lib/libqthreads.so.12 /usr/lib/libqthreads.so.12.modified && ln -s /usr/lib/libqthreads.so.12.modified /usr/lib/libqthreads.so.12
mv /usr/lib/libdmx.so.1 /usr/lib/libdmx.so.1.modified && ln -s /usr/lib/libdmx.so.1.modified /usr/lib/libdmx.so.1
mv /usr/lib/libmysqlclient.so.15 /usr/lib/libmysqlclient.so.15.modified && ln -s /usr/lib/libmysqlclient.so.15.modified /usr/lib/libmysqlclient.so.15
mv /usr/lib/libguile-srfi-srfi-4-v-1.so.1 /usr/lib/libguile-srfi-srfi-4-v-1.so.1.modified && ln -s /usr/lib/libguile-srfi-srfi-4-v-1.so.1.modified /usr/lib/libguile-srfi-srfi-4-v-1.so.1
mv /usr/lib/libsqlite.so.0 /usr/lib/libsqlite.so.0.modified && ln -s /usr/lib/libsqlite.so.0.modified /usr/lib/libsqlite.so.0
mv /usr/lib/libnotify.so.1 /usr/lib/libnotify.so.1.modified && ln -s /usr/lib/libnotify.so.1.modified /usr/lib/libnotify.so.1
mv /usr/lib/libsexy.so.2 /usr/lib/libsexy.so.2.modified && ln -s /usr/lib/libsexy.so.2.modified /usr/lib/libsexy.so.2
mv /usr/lib/libgmime-2.0.so.2 /usr/lib/libgmime-2.0.so.2.modified && ln -s /usr/lib/libgmime-2.0.so.2.modified /usr/lib/libgmime-2.0.so.2
mv /usr/lib/libcspi.so.0 /usr/lib/libcspi.so.0.modified && ln -s /usr/lib/libcspi.so.0.modified /usr/lib/libcspi.so.0
mv /usr/lib/libscim-gtkutils-1.0.so.8 /usr/lib/libscim-gtkutils-1.0.so.8.modified && ln -s /usr/lib/libscim-gtkutils-1.0.so.8.modified /usr/lib/libscim-gtkutils-1.0.so.8
mv /usr/lib/libpurple-client.so.0 /usr/lib/libpurple-client.so.0.modified && ln -s /usr/lib/libpurple-client.so.0.modified /usr/lib/libpurple-client.so.0
mv /usr/lib/libtracker-gtk.so.0 /usr/lib/libtracker-gtk.so.0.modified && ln -s /usr/lib/libtracker-gtk.so.0.modified /usr/lib/libtracker-gtk.so.0
mv /usr/lib/libGLEW.so.1.5 /usr/lib/libGLEW.so.1.5.modified && ln -s /usr/lib/libGLEW.so.1.5.modified /usr/lib/libGLEW.so.1.5
mv /usr/lib/libgpilotdcm.so.2 /usr/lib/libgpilotdcm.so.2.modified && ln -s /usr/lib/libgpilotdcm.so.2.modified /usr/lib/libgpilotdcm.so.2
mv /usr/lib/libnautilus-burn.so.4 /usr/lib/libnautilus-burn.so.4.modified && ln -s /usr/lib/libnautilus-burn.so.4.modified /usr/lib/libnautilus-burn.so.4
mv /usr/lib/libexempi.so.3 /usr/lib/libexempi.so.3.modified && ln -s /usr/lib/libexempi.so.3.modified /usr/lib/libexempi.so.3
mv /usr/lib/libspi.so.0 /usr/lib/libspi.so.0.modified && ln -s /usr/lib/libspi.so.0.modified /usr/lib/libspi.so.0
mv /usr/lib/libggzmod.so.4 /usr/lib/libggzmod.so.4.modified && ln -s /usr/lib/libggzmod.so.4.modified /usr/lib/libggzmod.so.4
mv /usr/lib/libedata-cal-1.2.so.6 /usr/lib/libedata-cal-1.2.so.6.modified && ln -s /usr/lib/libedata-cal-1.2.so.6.modified /usr/lib/libedata-cal-1.2.so.6
mv /usr/lib/libguile-srfi-srfi-13-14-v-1.so.1 /usr/lib/libguile-srfi-srfi-13-14-v-1.so.1.modified && ln -s /usr/lib/libguile-srfi-srfi-13-14-v-1.so.1.modified /usr/lib/libguile-srfi-srfi-13-14-v-1.so.1
mv /usr/lib/libopal.so.2.2 /usr/lib/libopal.so.2.2.modified && ln -s /usr/lib/libopal.so.2.2.modified /usr/lib/libopal.so.2.2
mv /usr/lib/libgucharmap.so.6 /usr/lib/libgucharmap.so.6.modified && ln -s /usr/lib/libgucharmap.so.6.modified /usr/lib/libgucharmap.so.6
mv /usr/lib/libseahorse.so.0 /usr/lib/libseahorse.so.0.modified && ln -s /usr/lib/libseahorse.so.0.modified /usr/lib/libseahorse.so.0
mv /usr/lib/librhythmbox-core.so.0 /usr/lib/librhythmbox-core.so.0.modified && ln -s /usr/lib/librhythmbox-core.so.0.modified /usr/lib/librhythmbox-core.so.0
mv /usr/lib/libgdata-1.2.so.1 /usr/lib/libgdata-1.2.so.1.modified && ln -s /usr/lib/libgdata-1.2.so.1.modified /usr/lib/libgdata-1.2.so.1
mv /usr/lib/libpisync.so.1 /usr/lib/libpisync.so.1.modified && ln -s /usr/lib/libpisync.so.1.modified /usr/lib/libpisync.so.1
```

---

