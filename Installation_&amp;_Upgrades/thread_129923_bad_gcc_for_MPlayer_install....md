---
title: "bad gcc for MPlayer install..."
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by dantheman on 2006-02-15
here is the problem I'm having...
```
dan@cleardan:~/Desktop/MPlayer-1.0pre7try2$ ./configure
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.2, bad
Checking for gcc version ... 4.0.2, bad
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... not found
Checking for gcc-3.2 version ... not found
Checking for gcc-3.1 version ... not found
Checking for gcc3 version ... not found
Checking for gcc-3.0 version ... not found
Checking for cc version ... 4.0.2, bad

*** Please downgrade/upgrade C compiler to version gcc-2.95.x or gcc-3.x! ***

You are not using a supported compiler. We do not have the time to make sure
everything works with compilers other than the ones we use.  Use either the
same compiler as we do, or use --disable-gcc-checking but DO *NOT* REPORT BUGS
unless you can reproduce them after recompiling with a 2.95.x or 3.x version!

Note for gcc 2.96 users: Some versions of this compiler are known to miscompile
mplayer and lame (which is used for mencoder).  If you get compile errors,
first upgrade to the latest 2.96 release (minimum 2.96-85) and try again.
If the problem still exists, try with gcc 3.x (or 2.95.x) *BEFORE* reporting
bugs!

        GCC 2.96 IS NOT AND WILL NOT BE SUPPORTED BY US !

    *** For details please read DOCS/HTML/en/users-vs-dev.html ***


Error: Bad gcc version

Check "configure.log" if you do not understand why it failed.
dan@cleardan:~/Desktop/MPlayer-1.0pre7try2$
```

Is there a way I can rollback the version just for the install and then "upgrade" after it's done? 

-dan-

---

### Post by public_void on 2006-02-15
Try
```
sudo apt-get install mplayer-386
```

To see how to setup the plugin in Firefox see [here]("http://ubuntuguide.org/#mplayer").

---

### Post by dantheman on 2006-02-15
[QUOTE=public_void]```
sudo apt-get install mplayer-386
```[/QUOTE]
Didn't work...
```
dan@cleardan:~$ sudo apt-get install mplayer-386
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386
dan@cleardan:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer
dan@cleardan:~$
```

...?

---

### Post by dantheman on 2006-02-15
```
Starting playback...
VDec: vo config request - 480 x 320 (preferred csp: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.

FATAL: Could not initialize video filters (-vf) or video output (-vo).

Can't restore text mode: Invalid argument

Exiting... (End of file)
```

It's installed now... I got a version of gcc3.4 from [http://packages.ubuntu.com](http://packages.ubuntu.com) and now after proper install, it's giving me this error... ?

---

### Post by dantheman on 2006-02-15
It gives me the error independent of the source (.wmv, .avi, .mpg, etc). I tried re-compling it, but that didn't do anything to fix the problem.

---

### Post by dantheman on 2006-03-08
I found a solution to this problem... 

install VLC instead

---

