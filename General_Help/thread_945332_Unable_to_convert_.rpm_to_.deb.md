---
title: "Unable to convert .rpm to .deb"
date: 2008-10-12
forum: General Help
---

### Post by Fatfool on 2008-10-12
yep using alien which gives this log:

```
jeffery@Roomcomp:~/Desktop$ sudo alien --scripts -k VirtualForbiddenCity.rpm
Package build failed. Here's the log:
d





 h_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - VFC 5.3 QA release
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/virtualforbiddencity
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: couldn't find library libnss3.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so shouldn't be linked with libpthread.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libxpcom.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libxul.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libpthread.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libstdc++.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libgcc_s.so.1 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libxpcom.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libxul.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libpthread.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgtk-x11-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgdk-x11-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libatk-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgdk_pixbuf-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libpangocairo-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libpango-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libcairo.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgmodule-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgcc_s.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libvorbis.so.0 needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/vfc.bin (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - VFC 5.3 QA release
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: VirtualForbiddenCity-6.0: No such file or directory
jeffery@Roomcomp:~/Desktop$ sudo rm -Rf VirtualForbiddenCity-6.0
jeffery@Roomcomp:~/Desktop$ sudo alien --scripts -i VirtualForbiddenCity.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - VFC 5.3 QA release
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/virtualforbiddencity
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: couldn't find library libnss3.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/libssl3.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/libmozjs.so shouldn't be linked with libpthread.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libxpcom.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libxul.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libpthread.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libstdc++.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/plugins/libunixprintplugin.so shouldn't be linked with libgcc_s.so.1 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libxpcom.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libxul.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplds4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libplc4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnspr4.so needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libpthread.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgtk-x11-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgdk-x11-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libatk-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgdk_pixbuf-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libpangocairo-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libpango-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libcairo.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgmodule-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/virtualforbiddencity/opt/VirtualForbiddenCity/components/libsystem-pref.so shouldn't be linked with libgcc_s.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libvorbis.so.0 needed by debian/virtualforbiddencity/opt/VirtualForbiddenCity/vfc.bin (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - VFC 5.3 QA release
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: VirtualForbiddenCity-6.0: No such file or directory
jeffery@Roomcomp:~/Desktop$ 


```

hmm. so it can't be converted? looks like it won't work on 64 bit ubuntu either.

I've tried -i, -k, with '--scripts' and without and it still doesn't work.

this is the link to the rpm file:
[http://www.virtualforbiddencity.org/VirtualForbiddenCity.rpm](http://www.virtualforbiddencity.org/VirtualForbiddenCity.rpm)

unfortunately, I won't be able to reply for a week though. :(

---

### Post by exploder on 2008-10-12
The link you provided completely locked up my browser! What package are you trying to convert? Maybe I can help you find a deb package that is already built.

---

### Post by Fatfool on 2008-10-12
> **exploder said:**
> The link you provided completely locked up my browser! What package are you trying to convert? Maybe I can help you find a deb package that is already built.
[http://www.virtualforbiddencity.org/FCBSTWeb/web/index.html](http://www.virtualforbiddencity.org/FCBSTWeb/web/index.html)

this is the main page.

its apparently a tour of the forbidden city which has a RPM file for linux.

I'm using Firefox and its fine though.......

I can't seem to find any .deb package for it

edit: ok i'll just leave this thread here. I'll only be back on saturday or so lol.

---

### Post by benjamin_linux on 2008-11-27
I don't know if you finally work it out, or if not what could be the problem, because

```
seretur@dendro:~$ sudo alien -k --scripts VirtualForbiddenCity.rpm
virtualforbiddencity_6.0-1_i386.deb generated
seretur@dendro:~$
```

Anyway, i installed the .deb and when i try to run the tour i got an error message "trying to run the proccess 'vfc' (access denied)", i tried to run it on the terminal and same result

```
seretur@dendro:~$ vfc
bash: /usr/bin/vfc: Permiso denegado
seretur@dendro:~$
```

The first time i tried without --scripts and it only created a folder with all the info, and when i try to delete it i got the same result, i logged in as root and can't do it either and , it said when i checked the folder and file permissions it said i can't change then because "i'm not the propietary"... i trully don't mind if the tour doesn't work, how the hell can i erase it!?

Any ideas, please?

---

