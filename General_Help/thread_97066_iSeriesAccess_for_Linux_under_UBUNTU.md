---
title: "iSeriesAccess for Linux under UBUNTU"
date: 2005-11-30
forum: General Help
---

### Post by elvisd on 2005-11-30
Hi all,
I'm trying to install iSeries Access for Linux.
I've downloaded the installation rpm file from ibm and converted to deb using alien.
```
sudo alien -d --scripts iSeriesAccess-5.2.0-1.10.i386.rpm
```
then
```
sudo dpkg -i iseriesaccess_5.2.0-2.1_i386.deb
```

Linked the  libXm.so.3 in /lib and in/opt/ibm/iseriesaccess/lib using (found in some post elsewhere...)
```
sudo ln -s /usr/X11R6/lib/libXm.so.3 /lib
sudo ln -s /usr/X11R6/lib/libXm.so.3 lib
```

then I make an ldd of /opt/ibm/iSeriesAccess/bin/ibm5250 and gave me:
```

 linux-gate.so.1 =>  (0xffffe000)
        libXm.so.3 => /lib/libXm.so.3 (0xb7d79000)
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7d64000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7d15000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7d0e000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7cf5000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c35000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb7c2e000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c21000)
        libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7c0b000)
        libcwbcore.so => /usr/lib/libcwbcore.so (0xb7b1b000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7a61000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7a3f000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7a34000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7906000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7902000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb78ff000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb78fb000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb78e9000)
        /lib/ld-linux.so.2 (0xb7fb4000)


```

finally... 
when I launch the ibm5250 program return me this error:
```

5250: [ INFORMATIONAL ]: Build Date: 13 July 2005 (1.10).
*** glibc detected *** free(): invalid next size (fast): 0x0838e560 ***
Aborted

```

Can someone help me in this issue?
Thank you very much

Best regards

elvisd

---

### Post by elvisd on 2005-12-20
Just for info: this problem isn't solved yet.
Till then... I have downloaded and installed tn5250j and works so fine...:smile: 

Best regards

elvisd

---

### Post by foodcoman on 2006-01-19
I have the same problem also and just settled for the 5250 client which works, but is not as familiar.  Help would be greatly appreciate on this one.

---

### Post by elvisd on 2006-02-07
I have downloaded iSeriesAccess-5.2.0-1.8.i386.rpm and alien'd to create a .deb, installation was successfull, but now when I launch the application I see the login, I enter my data press ok and receive (in the console) the following message:

```
5250: [ INFORMATIONAL ]: Build Date: 28 January 2005 (1.8).
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ INFORMATIONAL ]:
        ***** -b&h-lucidatypewriter-medium-r-normal-sans-0-* scalable fonts are unavailable. *****
        ***** Using fixed fonts if you want to use scaleable fonts, check the font FAQ and   *****
        ***** edit your /etc/X11/XF86Config or /etc/X11/fs/config file.    *****
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
Segmentation fault
```

I think that the error message is explicit... but I don't understand what should I do... Sorry and thanx

Best regards

elvisd

---

### Post by elvisd on 2006-02-07
Found on ibm website, how to apply to Ubuntu? ([http://www-03.ibm.com/servers/eserver/iseries/access/linux/guide/#known1](http://www-03.ibm.com/servers/eserver/iseries/access/linux/guide/#known1))

Emulator will not start, font error indicated.

The emulator uses scalable 75 and 100 DPI fonts. If scalable fonts are not found an attempt to use a fixed font is made. Even if a fixed font is found and used, for proper full screen and size support, the X server should be configured to use scalable fonts.

The error returned should look similar too:

    "*****Check your /etc/X11/XF86Config file*****
    -b&h-lucidatypewriter-medium-r-normal-sans-0-* scalable fonts are not available.
    *****Using fixed fonts******.

Or

    Check your /etc/X11/XF86Config file.
    -b&h-lucidatypewriter-medium-r-normal-sans-* fixed and scalable fonts are not available. Session not starting.

For either of the above messages, 75 and 100 dpi fonts need to be made available. The default font server is configured usually in one of the following two ways:

1. The "XFree86Config" File

The global XFree86 config file "XF86Config" or "XF86Config-4" is located in the /etc or /etc/X11 directories. The user may also have ".XF86Config" or ".XF86Config-4" (user config version) in his home directory.

If the following is in the XF86Config, the font server is configured here and is not configured to use 75 and 100 dpi scaled fonts.
    FontPath "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
    FontPath "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"

To enable 75 and 100 dpi scalable fonts, change the above two lines to look like this:
    FontPath "/usr/X11R6/lib/X11/fonts/75dpi"
    FontPath "/usr/X11R6/lib/X11/fonts/100dpi"

2. Font server (xfs) "config" file

If the XF86Config file contains a single line similar to the following, then look for the file "config" in /etc/X11/fs directory:
    FontPath "unix/:7100"

Similar to the steps above find the lines and remove the ":unscaled" from the lines for 75 and 100 dpi fonts.

For example change:
catalogue = /usr/X11R6/lib/X11/fonts/korean,
    /usr/X11R6/lib/X11/fonts/misc:unscaled,
    /usr/X11R6/lib/X11/fonts/75dpi:unscaled,
    /usr/X11R6/lib/X11/fonts/100dpi:unscaled,

to look like this:
catalogue = /usr/X11R6/lib/X11/fonts/korean,
    /usr/X11R6/lib/X11/fonts/misc:unscaled,
    /usr/X11R6/lib/X11/fonts/75dpi,
    /usr/X11R6/lib/X11/fonts/100dpi,

Then restart the X server.

For more help or information read the man pages for X(7x), xfs(1x) and XF86Config(5x) or the Linux Font, Font Server or XFree86 HowTo's.

Troubleshooting font problems.

To troubleshoot font problems use the following XFree86 utilities:

   xfd -fn "fontname" - To try and display the font

   xlsfonts - To get a list of all available fonts from the font server
   xlsfonts -fn pattern - To get a list of pattern available fonts from the font server

---

### Post by elvisd on 2006-02-07
I have edited the xorg.conf removing the ':unscaled' to both 75 and 100... now I have this error:

5250: [ INFORMATIONAL ]: Build Date: 28 January 2005 ( 1 . 8 )
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r- normal-*-24-*-*-*-m-*" to type FontSet.

What is this error now?

---

### Post by sirnigel on 2006-02-28
I have the IBM5250 terminal emulator running on Ubuntu 5.10.  After installing Umbuntu 5.10 I used EasyUbuntu to install, "Repository list, Main, Universe, Multiverse, and PLF" and "Fonts: Install Microsoft and other nice fonts."

Here's how I installed IBM5250:

Download iSeriesAccess-5.2.0-1.10.i386.rpm from IBM.

	$ sudo alien -i iSeriesAccess-5.2.0-1.10.i386.rpm 

	$ sudo apt-get install libmotif3

	$ sudo apt-get install libxaw6

I'm not sure whether libmotif3 or libxaw6 provides libXm.so.3 so I installed them both.

	$ sudo ln -s /usr/X11R6/lib/libXm.so.3.0.2 /usr/lib/libXm.so.3

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/	libcwbcore.so

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbc.so /usr/lib/libcwbodbc.so

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbcs.so /usr/lib/libcwbodbcs.so

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbrc.so /usr/lib/libcwbrc.so

	$ echo $LANG
en_US.UTF-8

IBM5250 expects something other than en_US.UTF-8, so run this to start.

	$ /opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_us

IBM5250 starts and runs fine.  I did not run setup5250 first.

---

### Post by n8bounds on 2006-04-27
Most of that worked (reading your commands taught me how to make links, which I needed a few more of, but the terminal output gave easily understood errors which helped) but I also needed this:

code:
sudo apt-get install libstdc++5

---

### Post by n8bounds on 2007-02-25
This one should actually work:

[http://ubuntuforums.org/showthread.php?t=368894](http://ubuntuforums.org/showthread.php?t=368894)

---

### Post by djearwig on 2007-03-02
I'm having the same problem as elvisd.  Followed siringel's instuctions with no problems until I ran the 5250 session.  I have tried to install the MS Tru Type fonts with the commnad: #apt-get install msttcorefonts -y.  I get an error that says: "dpkg: error processing msttcorefonts (--configure)"
I'd like to get this running and break my company free of M$ so any help would be greatly appreciated.

---

### Post by royg on 2007-08-29
Hi there guys, 

this worked perfectly for me, use "alien" instead of rpm to install the the iseries*.rpm 

Thanks so much for the help, what was missing for me was libmotif3 and libxaw6, just libmotif3 wouldn't work either.

cheers
royg
> **sirnigel said:**
> I have the IBM5250 terminal emulator running on Ubuntu 5.10.  After installing Umbuntu 5.10 I used EasyUbuntu to install, "Repository list, Main, Universe, Multiverse, and PLF" and "Fonts: Install Microsoft and other nice fonts."

Here's how I installed IBM5250:

Download iSeriesAccess-5.2.0-1.10.i386.rpm from IBM.

	$ sudo alien -i iSeriesAccess-5.2.0-1.10.i386.rpm 

	$ sudo apt-get install libmotif3

	$ sudo apt-get install libxaw6

I'm not sure whether libmotif3 or libxaw6 provides libXm.so.3 so I installed them both.

	$ sudo ln -s /usr/X11R6/lib/libXm.so.3.0.2 /usr/lib/libXm.so.3

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/	libcwbcore.so

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbc.so /usr/lib/libcwbodbc.so

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbcs.so /usr/lib/libcwbodbcs.so

	$ sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbrc.so /usr/lib/libcwbrc.so

	$ echo $LANG
en_US.UTF-8

IBM5250 expects something other than en_US.UTF-8, so run this to start.

	$ /opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_us

IBM5250 starts and runs fine.  I did not run setup5250 first.

---

