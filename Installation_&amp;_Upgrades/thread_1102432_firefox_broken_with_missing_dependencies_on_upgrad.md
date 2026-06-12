---
title: "firefox broken with missing dependencies on upgrade"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by ami_nakata on 2009-03-21
RESOLVED: I downloaded firefox directly from the mozilla
web site and installed that, without using synaptic. 
Everything works properly again.  Weird.

- -

Firefox worked fine until I intalled the latest official
upgrade to Hardy Heron/8.04LTS today via Synaptic. 
( 20 March 2009 ) I was watching a video on [www.fancast.com](www.fancast.com), 
all was working just fine.

Then I noticed the "upgrades available" notification icon 
in the upper right corner of my gnome/ubuntu screen.  So I 
stopped the video in mid-show, exited firefox, and completed 
the upgrade process. 

I rebooted, then restarted firefox (now at ver 3.0.7). It 
allowed me to do most things, including watching youtube 
videos. But when I tried to play the video I had been 
watching on [www.fancast.com](www.fancast.com) it wouldn't play. The site 
attempted to load the actual video indefinitely, i.e. it 
never played, just said "loading", "loading", ad nauseum.
Same result for any other video I tried to play on fancast.

Firefox error log reports:

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.7/components/pyabout.py
Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.7/components/libpyloader.so

Warning: Error in parsing value for property 'cursor'. Declaration dropped.
Source File: [http://www.fancast.com/static-19052/css/base.css](http://www.fancast.com/static-19052/css/base.css)
Line: 28

Warning: Unknown property 'resize'. Declaration dropped.
Source File: [http://www.fancast.com/static-19052/css/base.css](http://www.fancast.com/static-19052/css/base.css)
Line: 41

... and a raft of similar errors re this base.css file.

I looked around the web and found information that would seem
to confirm that the just-released "update packages" I installed have
some missing dependencies re Firefox. I've included a detailed list
about this, following. 

Do I just need to wait for a "fix for the fix" to be released, or 
is there something I can do on my own? Or should this be entered 
into launchpad as a bug? Thanks in advance for your help; 
documentation follows:

Based on info which [http://forums.mozillazine.org/viewtopic.php?f=19&t=787565](http://forums.mozillazine.org/viewtopic.php?f=19&t=787565) led me to,
I ran the following command from a terminal window:

ami@austen:~$ cd /usr/lib/xulrunner-1.9.0.7/components
ami@austen:~$ /usr/lib/firefox-3.0.7/run-mozilla.sh `which ldd` -r ./libpyloader.so

( or, all together: /usr/lib/firefox-3.0.7/run-mozilla.sh `which ldd` -r /usr/lib/xulrunner-1.9.0.7/components/libpyloader.so )

both of which result in this output, which indicate MISSING DEPENDENCIES, and thus (?) a problem in the build.

- - terminal window results begin --

ami@austen:~$ /usr/lib/firefox-3.0.7/run-mozilla.sh `which ldd` -r /usr/lib/xulrunner-1.9.0.7/components/libpyloader.so
 linux-gate.so.1 => (0xb7f46000)
 libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f1d000)
 libxpcom.so => not found
 libxul.so => not found
 libplds4.so.0d => /usr/lib/libplds4.so.0d (0xb7f19000)
 libplc4.so.0d => /usr/lib/libplc4.so.0d (0xb7f15000)
 libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0xb7ee2000)
 libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ede000)
 libpython2.5.so.1.0 => /usr/lib/libpython2.5.so.1.0 (0xb7da8000)
 libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7da4000)
 libpyxpcom.so => not found
 libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7cb1000)
 libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c8c000)
 libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7c80000)
 libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b31000)
 /lib/ld-linux.so.2 (0xb7f47000)
undefined symbol: _ZN14Py_nsISupports21PyObjectFromInterfaceEP11nsISupportsRK4nsIDii (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z16PyXPCOM_LogErrorPKcz (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _ZN14Py_nsISupports21InterfaceFromPyObjectEP7_objectRK4nsIDPP11nsISupportsii (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z24PyXPCOM_MakePendingCallsv (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z31PyXPCOM_EnsurePythonEnvironmentv (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z34PyXPCOM_SetCOMErrorFromPyExceptionv (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
ami@austen:~$

- - terminal window results end - -

Note the mozillazine forum entry referenced above pointed to this URL:

[https://developer.mozilla.org/en/Troubleshooting_XPCOM_components_registration#Linux-specific_hints](https://developer.mozilla.org/en/Troubleshooting_XPCOM_components_registration#Linux-specific_hints)

which provided the following info ( in an "article" (page) entitled: Troubleshooting XPCOM components registration )

 Linux-specific hints

(1) Check if you have missing dependent libraries:

 From your Firefox (/XULRunner) install directory,
 run "./run-mozilla.sh `which ldd` -r path/to/your/component.so".

 There should be no "not found" entries and no undefined symbols.
 (The -r switch from GNU ldd lists function relocations; adjust
 as suitable for your version)

(2) Use strace to see if Firefox is trying to load your components.

(3) Pass the -Wl,-z,defs flag to gcc when linking your component.

 This will ensure that undefined symbols show an error at link time
 instead of failing at run time.

Finally, this link may also be helpful for any real programmer trying to understand or resolve the problem:

[http://forums.mozillazine.org/viewtopic.php?f=27&t=770085](http://forums.mozillazine.org/viewtopic.php?f=27&t=770085)

---

