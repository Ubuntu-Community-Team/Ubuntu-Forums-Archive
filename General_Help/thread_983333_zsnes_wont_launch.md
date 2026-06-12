---
title: "zsnes wont launch"
date: 2008-11-15
forum: General Help
---

### Post by billc123 on 2008-11-15
Hello-
 I upgraded from 8.04 to 8.10 of Ubuntu, and now zsnes wont launch. It worked perfect before I upgraded though. Im using a Dell Inspiron 1525 Laptop. When launching from the desktop nothing happens. I tried uninstalling, deleting the .zsnes folder, and reinstalling through add/remove option, but the same thing happens. I don't have the mcop error though. Through the terminal I have this...




bill@Archimedes:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7db6558]
/lib/tls/i686/cmov/libc.so.6[0xb7db4680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 1638417    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 1638417    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 1638417    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
08935000-0897e000 rw-p 08935000 00:00 0          [heap]
b6d84000-b78b3000 rw-p b6d84000 00:00 0 
b78b3000-b7900000 r-xp 00000000 08:01 1639770    /usr/lib/libXt.so.6.0.0
b7900000-b7904000 rw-p 0004c000 08:01 1639770    /usr/lib/libXt.so.6.0.0
b7904000-b791a000 r-xp 00000000 08:01 1638889    /usr/lib/libaudio.so.2.4
b791a000-b791b000 r--p 00015000 08:01 1638889    /usr/lib/libaudio.so.2.4
b791b000-b791c000 rw-p 00016000 08:01 1638889    /usr/lib/libaudio.so.2.4
b792c000-b794e000 r-xp 00000000 08:01 1639811    /usr/lib/libaudiofile.so.0.0.2
b794e000-b7951000 rw-p 00021000 08:01 1639811    /usr/lib/libaudiofile.so.0.0.2
b7959000-b795c000 r-xp 00000000 08:01 1647588    /usr/lib/ao/plugins-2/libalsa09.so
b795c000-b795e000 rw-p 00002000 08:01 1647588    /usr/lib/ao/plugins-2/libalsa09.so
b795e000-b795f000 r-xp 00000000 08:01 1466372    /usr/lib/ao/plugins-2/libnas.so
b795f000-b7961000 rw-p 00000000 08:01 1466372    /usr/lib/ao/plugins-2/libnas.so
b7961000-b7964000 r-xp 00000000 08:01 2113578    /lib/libcap.so.1.10
b7964000-b7965000 rw-p 00002000 08:01 2113578    /lib/libcap.so.1.10
b7965000-b797a000 r-xp 00000000 08:01 1639693    /usr/lib/libICE.so.6.3.0
b797a000-b797b000 rw-p 00014000 08:01 1639693    /usr/lib/libICE.so.6.3.0
b797b000-b797d000 rw-p b797b000 00:00 0 
b797d000-b79cb000 r-xp 00000000 08:01 1640916    /usr/lib/libpulse.so.0.4.1
b79cb000-b79cc000 r--p 0004d000 08:01 1640916    /usr/lib/libpulse.so.0.4.1
b79cc000-b79cd000 rw-p 0004e000 08:01 1640916    /usr/lib/libpulse.so.0.4.1
b79cd000-b79d9000 r-xp 00000000 08:01 1640918    /usr/lib/libpulse-simple.so.0.0.1
b79d9000-b79da000 r--p 0000b000 08:01 1640918    /usr/lib/libpulse-simple.so.0.0.1
b79da000-b79db000 rw-p 0000c000 08:01 1640918    /usr/lib/libpulse-simple.so.0.0.1
b79db000-b79dc000 rw-p b79db000 00:00 0 
b79dc000-b79e5000 r-xp 00000000 08:01 1638428    /usr/lib/libesd.so.0.2.39
b79e5000-b79e6000 r--p 00008000 08:01 1638428    /usr/lib/libesd.so.0.2.39
b79e6000-b79e7000 rw-p 00009000 08:01 1638428    /usr/lib/libesd.so.0.2.39
b79e7000-b79e9000 r-xp 00000000 08:01 1466373    /usr/lib/ao/plugins-2/liboss.so
b79e9000-b79eb000 rw-p 00001000 08:01 1466373    /usr/lib/ao/plugins-2/liboss.so
b79eb000-b79f5000 r-xp 00000000 08:01 2130990    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b79f5000-b79f6000 r--p 00009000 08:01 2130990    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b79f6000-b79f7000 rw-p 0000a000 08:01 2130990    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b79f7000-b7a00000 r-xp 00000000 08:01 2130994    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7a00000-b7a01000 r--p 00008000 08:01 2130994    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7a01000-b7a02000 rw-p 00009000 08:01 2130994    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7a02000-b7a17000 r-xp 00000000 08:01 2130984    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7a17000-b7a18000 r--p 00014000 08:01 2130984    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7a18000-b7a19000 rw-p 00015000 08:01 2130984    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7a19000-b7a1b000 rw-p b7a19000 00:00 0 
b7a1b000-b7a22000 r-xp 00000000 08:01 2130986    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7a22000-b7a23000 r--p 00006000 08:01 2130986    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7a23000-b7a24000 rw-p 00007000 08:01 2130986    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7a24000-b7a26000 rw-p b7a24000 00:00 0 
b7a26000-b7a2a000 r-xp 00000000 08:01 1638665    /usr/lib/libXdmcp.so.6.0.0
b7a2a000-b7a2b000 rw-p 00003000 08:01 1638665    /usr/lib/libXdmcp.so.6.0.0
b7a2b000-b7a42000 r-xp 00000000 08:01 1639339    /usr/lib/libxcb.so.1.0.0
b7a42000-b7a43000 r--p 00016000 08:01 1639339    /usr/lib/libxcb.so.1.0.0
b7a43000-b7a44000 rw-p 00017000 08:01 1639339    /usr/lib/libxcb.so.1.0.0
b7a44000-b7a45000 r-xp 00000000 08:01 1639358    /usr/lib/libxcb-xlib.so.0.0.0
b7a45000-b7a46000 r--p 00000000 08:01 1639358    /usr/lib/libxcb-xlib.so.0.0.0
b7a46000-b7a47000 rw-p 00001000 08:01 1639358    /usr/lib/libxcb-xlib.so.0.0.0
b7a47000-b7a48000 rw-p b7a47000 00:00 0 
b7a48000-b7a4a000 r-xp 00000000 08:01 1638663    /usr/lib/libXau.so.6.0.0
b7a4a000-b7a4b000 rw-p 00001000 08:01 1638663    /usr/lib/libXau.so.6.0.0
b7a4b000-b7b36000 r-xp 00000000 08:01 1639365    /usr/lib/libX11.so.6.2.0
b7b36000-b7b37000 r--p 000ea000 08:01 1639365    /usr/lib/libX11.so.6.2.0
b7b37000-b7b39000 rw-p 000eb000 08:01 1639365    /usr/lib/libX11.so.6.2.0
b7b39000-b7b3a000 rw-p b7b39000 00:00 0 
b7b3a000-b7b41000 r-xp 00000000 08:01 2131004    /lib/tls/i686/cmov/librt-2.8.90.so
b7b41000-b7b42000 r--p 00007000 08:01 2131004    /lib/tls/i686/cmov/librt-2.8.90.so
b7b42000-b7b43000 rw-p 00008000 08:01 2131004    /lib/tls/i686/cmov/librt-2.8.90.so
b7b43000-b7b50000 r-xp 00000000 08:01 1639737    /usr/lib/libXext.so.6.4.0
b7b50000-b7b52000 rw-p 0000c000 08:01 1639737    /usr/lib/libXext.so.6.4.0
b7b52000-b7b65000 r-xp 00000000 08:01 1640793    /usr/lib/libdirect-1.0.so.0.1.0
b7b65000-b7b66000 r--p 00012000 08:01 1640793    /usr/lib/libdirect-1.0.so.0.1.0
b7b66000-b7b67000 rw-p 00013000 08:01 1640793    /usr/lib/libdirect-1.0.so.0.1.0
b7b67000-b7b6e000 r-xp 00000000 08:01 1640795    /usr/lib/libfusion-1.0.so.0.1.0
b7b6e000-b7b6f000 r--p 00006000 08:01 1640795    /usr/lib/libfusion-1.0.so.0.1.0
b7b6f000-b7b70000 rw-p 00007000 08:01 1640795    /usr/lib/libfusion-1.0.so.0.1.0
b7b70000-b7b71000 rw-p b7b70000 00:00 0 
b7b71000-b7bd5000 r-xp 00000000 08:01 1640794    /usr/lib/libdirectfb-1.0.so.0.1.0
b7bd5000-b7bd6000 r--p 00063000 08:01 1640794    /usr/lib/libdirectfb-1.0.so.0.1.0
b7bd6000-b7bd7000 rw-p 00064000 08:01 1640794    /usr/lib/libdirectfb-1.0.so.0.1.0
b7bd7000-b7bd9000 r-xp 00000000 08:01 2130978    /lib/tls/i686/cmov/libdl-2.8.90.so
b7bd9000-b7bda000 r--p 00001000 08:01 2130978    /lib/tls/i686/cmov/libdl-2.8.90.so
b7bda000-b7bdb000 rw-p 00002000 08:01 2130978    /lib/tls/i686/cmov/libdl-2.8.90.so
b7bdb000-b7c9e000 r-xp 00000000 08:01 1640122    /usr/lib/libasound.so.2.0.0
b7c9e000-b7ca0000 r--p 000c2000 08:01 1640122    /usr/lib/libasound.so.2.0.0
b7ca0000-b7ca3000 rw-p 000c4000 08:01 1640122    /usr/lib/libasound.so.2.0.0
b7ca3000-b7cb8000 r-xp 00000000 08:01 2131000    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7cb8000-b7cb9000 r--p 00014000 08:01 2131000    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7cb9000-b7cba000 rw-p 00015000 08:01 2131000    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7cba000-b7cbc000 rw-p b7cba000 00:00 0 
b7cbc000-b7e14000 r-xp 00000000 08:01 2130972    /lib/tls/i686/cmov/libc-2.8.90.so
b7e14000-b7e16000 r--p 00158000 08:01 2130972    /lib/tls/i686/cmov/libc-2.8.90.so
b7e16000-b7e17000 rw-p 0015a000 08:01 2130972    /lib/tls/i686/cmov/libc-2.8.90.so
b7e17000-b7e1b000 rw-p b7e17000 00:00 0 
b7e1b000-b7e28000 r-xp 00000000 08:01 2113670    /lib/libgcc_s.so.1
b7e28000-b7e29000 r--p 0000c000 08:01 2113670    /lib/libgcc_s.so.1
b7e29000-b7e2a000 rw-p 0000d000 08:01 2113670    /lib/libgcc_s.so.1
b7e2a000-b7e4e000 r-xp 00000000 08:01 2130980    /lib/tls/i686/cmov/libm-2.8.90.so
b7e4e000-b7e4f000 r--p 00023000 08:01 2130980    /lib/tls/i686/cmov/libm-2.8.90.so
b7e4f000-b7e50000 rw-p 00024000 08:01 2130980    /lib/tls/i686/cmov/libm-2.8.90.so
b7e50000-b7f33000 r-xp 00000000 08:01 1639714    /usr/lib/libstdc++.so.6.0.10
b7f33000-b7f34000 ---p 000e3000 08:01 1639714    /usr/lib/libstdc++.so.6.0.10
b7f34000-b7f38000 r--p 000e3000 08:01 1639714    /usr/lib/libstdc++.so.6.0.10
b7f38000-b7f39000 rw-p 000e7000 08:01 1639714    /usr/lib/libstdc++.so.6.0.10
b7f39000-b7f3f000 rw-p b7f39000 00:00 0 
b7f3f000-b7fb5000 r-xp 00000000 08:01 1640813    /usr/lib/libGL.so.1.2
b7fb5000-b7fb7000 rw-p 00075000 08:01 1640813    /usr/lib/libGL.so.1.2
b7fb7000-b7fbb000 rw-p b7fb7000 00:00 0 
b7fbb000-b7fbe000 r-xp 00000000 08:01 1638511    /usr/lib/libao.so.2.1.3
b7fbe000-b7fc0000 rw-p 00003000 08:01 1638511    /usr/lib/libao.so.2.1.3
b7fc0000-b7fe4000 r-xp 00000000 08:01 1639356    /usr/lib/libpng12.so.0.27.0
b7fe4000-b7fe6000 rw-p 000230Aborted

---

### Post by billc123 on 2008-11-15
this is my video card also...

bill@Archimedes:~/Desktop$ su -c "lspci | grep VGA"
Password: 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by dfreer on 2008-11-16
This issue has come up multiple times already... you need to download a ZSNES binary that was NOT compiled using Ubuntu Intrepid's GCC 4.3.2, as it produces the error you see above.

---

### Post by billc123 on 2008-11-16
ok thanks. Do you know of a link where I could get it?

---

### Post by dfreer on 2008-11-16
This binary should work, I compiled with --enable-libao --enable-release force_arch=i586, so it should work for everyone. If it doesn't, try running **ldd** on it and make sure you have all the dependencies you need.

---

### Post by billc123 on 2008-11-16
thanks my friend.  Sorry if this is a dumb question, but i am still pretty new to linux.  I extracted it to my desktop, but when i click on it, it says "Could not display /home/bill/desktop/zsnes. there is no application installed for this file type." 
What is "ld"?

---

### Post by dfreer on 2008-11-17
```
cd ~/Desktop/
**ldd** ./zsnes
```
That should show the list of all shared libraries that ZSNES requires to run. 
EDITED: Because I am a silly bear :p
**[http://www.computerhope.com/unix/uldd.htm](http://www.computerhope.com/unix/uldd.htm)**

```
cd ~/Desktop
ls -l ./zsnes
```
The output should look something like this:
```
$ ls -l zsnes
-rwxr-xr-x 1 cssgamer cssgamer 10644 2008-11-16 22:50 zsnes

```
The important thing to note here, is that on the left side, ZSNES has e**x**cutable permissions, which allows it to run. If it does not have executable permissions, that might be why you are unable to click on it and launch it.

Finally, just enter the following:
```
cd ~/Desktop
./zsnes
```
If it gives you an error, copy and paste it here and I'll see what I can do :D

I would normally have just given you a .deb package so you could install zsnes like a .exe on windows, but alas I still need to create some for intrepid.

---

### Post by billc123 on 2008-11-17
thanks. so this is what happened...

bill@Archimedes:~$ cd ~/Desktop
bill@Archimedes:~/Desktop$ ld ./zsnes
ld: error in ./zsnes(.eh_frame); no .eh_frame_hdr table will be created.
ld: warning: cannot find entry symbol _start; defaulting to 000000000804d340
bill@Archimedes:~/Desktop$ 


I think that error may be because the ./zsnes folder is located at /home/bill and not at /home/bill/desktop  Maybe i should try it from the bill folder and see what happens.

You are right about no 'X' on the permissions though. Here is what i got for a ls -l command...

bill@Archimedes:~/Desktop$ ls -l zsnes
-rw-r--r-- 1 bill bill 3132512 2008-10-30 02:58 zsnes

so maybe i just need to give it x on permissions?

---

### Post by dfreer on 2008-11-17
A little confused myself, I only uploaded the binary to you, and yet you say there is a zsnes folder in your /home/bill/? Perhaps you are talking about the user preferences folder for ZSNES, it would be located at /home/bill/.zsnes/, and it stores all your settings, saved games, states etc.

To make a binary executable, you can use chmod:
```
chmod +x ~/Desktop/zsnes
```

That would explain why you wouldn't be able to launch ZSNES.

As for the whole ld thing, I completely screwed up there, my bad :( The correct command is **ldd**, not ld. The link I posted earlier is also wrong, I have no idea what I was thinking when I made those posts. Here's the results of running ldd on zsnes in Debian Lenny 64-bit:
```
$ ldd ./zsnes
        linux-gate.so.1 =>  (0xf7eee000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7ec8000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7e17000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf7df4000)
        libncurses.so.5 => /lib32/libncurses.so.5 (0xf7dc2000)
        **libao.so.2 => not found**
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7d5e000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7c70000)
        libm.so.6 => /lib32/libm.so.6 (0xf7c4c000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7c3f000)
        libc.so.6 => /lib32/libc.so.6 (0xf7aec000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ad5000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7a12000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7a0e000)
        libdirectfb-1.0.so.0 => /usr/lib32/libdirectfb-1.0.so.0 (0xf79aa000)
        libfusion-1.0.so.0 => /usr/lib32/libfusion-1.0.so.0 (0xf79a2000)
        libdirect-1.0.so.0 => /usr/lib32/libdirect-1.0.so.0 (0xf798e000)
        libvga.so.1 => /usr/lib32/libvga.so.1 (0xf792d000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf783e000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7830000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf782b000)
        libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf7827000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf7822000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0xf781a000)
        /lib/ld-linux.so.2 (0xf7eef000)
        librt.so.1 => /lib32/librt.so.1 (0xf7811000)
        libx86.so.1 => /lib32/libx86.so.1 (0xf780e000)
        libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf780b000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf77f3000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf77f0000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf77eb000)
```
Note that how in this case, I am missing the library highlighted in bold, which can be fixed on a 32-bit system with:
```
sudo apt-get install libao2
```

---

### Post by billc123 on 2008-11-17
It is working normally now. :)

  As soon as I did the chmod command to make it executable, it was back to normal. 

  Also, yes, the .zsnes folder was the one that holds all the settings etc. It was still there from before when I installed it via the add\remove software option. It creates the folder automatically from the repository. I found an desktop icon on the internet that looks cool too. :)

Thank you so much for your help!

---

### Post by billc123 on 2008-12-04
just to let people know- I also tried this on opensuse 11, and it even works perfectly on that also.
\\:D/

---

