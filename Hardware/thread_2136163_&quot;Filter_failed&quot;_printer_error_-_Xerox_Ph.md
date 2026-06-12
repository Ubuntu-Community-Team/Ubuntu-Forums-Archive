---
title: "&quot;Filter failed&quot; printer error - Xerox Phaser 3010 on Ubuntu/Kubuntu 12.10"
date: 2013-04-16
forum: Hardware
---

### Post by jankillian on 2013-04-16
[LIST=1]
[*]installed xerox phaser 3010/3040 deb package from [http://www.support.xerox.com/support/phaser-3010/file-download/enza.html?operatingSystem=linux&contentId=118987](http://www.support.xerox.com/support/phaser-3010/file-download/enza.html?operatingSystem=linux&contentId=118987)
[*]added the printer in CUPS
[*]enabled CUPS debug: ```
sudo cupsctl LogLevel=debug2
```
[*]tried to print a test page from CUPS (repeated later using a simple Google Document with the same result)
[*]printer changed its status to "busy - processing page 1" and within second changed again to "inactive - processing page 1"
[*]the status message in printer job queue is "Filter failed"
[*]the full /var/log/cups/error_log is at [http://pastebin.com/GqwbTZ0L](http://pastebin.com/GqwbTZ0L), selected fails:
[/LIST]

[LIST]
[*][SIZE=2][FONT=arial][&#8203;]("http://pastebin.com/GqwbTZ0L")[COLOR=#000000]D [16/Apr/2013:20:46:27 +0200] DeleteDevice failed: org.freedesktop.DBus.Error.InvalidArgs:Type of message, `(s)', does not match expected type `(o)'[/COLOR][/FONT][/SIZE]
[*][SIZE=2][FONT=arial][COLOR=#000000]CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Xerox_Phaser_3010' already exists[/COLOR][/FONT][/SIZE]
[*][SIZE=2][FONT=arial]D [16/Apr/2013:20:46:35 +0200] [Job 189] Failed to send: org.freedesktop.ColorManager.Failed:device id 'Xerox_Phaser_3010' does not exists[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]D [16/Apr/2013:20:46:35 +0200] [Job 189] Failed to get profile filename![/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial]&#8203;
Any ideas what the cause and solution might be?
[/FONT][/SIZE]

---

### Post by gridcube on 2013-04-17
I have this exact same problem on a Xerox Phaser 3040 that share the same drivers.

I'm using Xubuntu 12.10

so I think we share the same CUPS version and all.  :( ill give more information later but i didnt want you to feel alone in this conundrum

---

### Post by gridcube on 2013-04-17
jankillian, i've found this thread: 

[http://forum.support.xerox.com/t5/Printing/Phaser-6010-driver-Linux-64-bits/td-p/5244/page/2](http://forum.support.xerox.com/t5/Printing/Phaser-6010-driver-Linux-64-bits/td-p/5244/page/2)

it suggest a few workarounds to test, will report once i've tested them to see if one works.

---

### Post by gridcube on 2013-04-17
:D YEAH! success!

jankillian, i've succeded in installing the printer, i followed all the instructions to get it to work so i dont know wich ones did the trick, firts i tried the last suggestion, for debian, but as the multiarch comes by default in ubuntu it worked, sort of,

> 1.: Enable multiarch support on your Debian: [http://wiki.debian.org/Multiarch/Implementation#Using_multiarch](http://wiki.debian.org/Multiarch/Implementation#Using_multiarch)

2.: Install the 32 bits driver deb-package

3.: In CUPS you can add the printer now but it will not work so far. After trying to print something you can find something like

D [14/Mar/2013:21:31:41 +0100] [Job 39] Dell_1250c: error while loading shared libraries: libcupsimage.so.2: cannot open shared object file: No such file or directory

in /var/log/cups/error_log

4.: But this message is a pretty good help: apt-get install libcupsimage2:i386 will install the missing 32 bits library

5.: After restarting CUPS with /etc/init.d/cups restart I was able to use the printer without any problem

 

that took away the "filter failed" error log, but i still couldnt print.

then i tried this,

> However, based on the above posts I may have a workaround for Linux Mint 13 or similar Ubuntu based distributions:

1) Make sure ia32-libs is installed (sudo apt-get install -y ia32-libs)

2) go ahead and download the 32-bit *.deb from the Xerox support site

3) Install the 32-bit deb using gdebi package installer (I just right clicked on the *.deb and installed)

4) Open nautilus and navigate to /usr/share/ppd/Xerox and find the Xerox_Phaser_6010n.ppd.gz file

5) copy this file and move it to a directory you own (~/Desktop) for example

6) extract the contents of the gz, out will come Xerox_Phaser_6010N.ppd

7) Open a terminal and use system-config-printer

8) Add the printer, I have it connected to my router with a reserved DHCP IP address so I use
the appsockert/JetDirect option. In my case the resulting Device URI is socket://192.168.0.127:9100 (modify for your IP settings)

9) When asked for the driver ppd, select "Provide the ppd file" and browse to the extracted Xerox_Phaser_6010N.ppd from a folder you have permissions. This should be successful, trying to add it for me directly from /usr/share/ppd/Xerox resulted in a cups error on add, probably due to lack of permissions on usr/share/...)

still no luck, the printer accepted the job, and tooked it away of the queue, but it printed nothing.


finally i did this;
>     sudo nautilus ~ /* creates a root filemanager in your home directory */
    create an empty directory
    download and extract the .deb package
    extract the contents of the .deb package /* in root nautilus (remember the sudo), right click/extract here.  If you double click, it tries to install and complains about being the wrong architecture */
    manually copy the contents from under /usr to their respective locations creating any missing directories as you go.  You can ignore the /DEBIAN directory.
    Reboot /* don't know if this is necessary, but I've been trained by years of using windows :-) */
    Add the printer through cups

I did not reboot however, what i did differently, after removing the printer was add it from the CUPS not the printer installer.


:D NOW THE PRINTER WORKS AND IM HAPPY

---

### Post by jankillian on 2013-04-18
Hello @gridcube, thanks for your effort, this seems promising! I recall to see the missing lib in logs. Will try that as soon as I get to the printer. Many thanks!

---

### Post by jankillian on 2013-04-18
Woohoo, you are the hacker @gridcube!

It helped:

```

sudo apt-get install -y ia32-libs

ar p xerox-phaser-3010-3040_1.0-28_i386.deb data.tar.gz | sudo tar -xzf - --keep-newer-files --no-overwrite-dir -v -C / ./usr

sudo restart cups
```

[LIST=1]
[*]now go to the printer settings
[*]remove the old phaser printer, if any
[*]turn on the printer
[*]it should be autodetected and automatically added
[*]print a test page
[/LIST]

Many thanks! :)

---

