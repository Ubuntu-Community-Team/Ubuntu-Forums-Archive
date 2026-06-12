---
title: "Canon Pixma MG6150 &quot;cannot load library&quot; error"
date: 2014-05-21
forum: Hardware
---

### Post by foxy123 on 2014-05-21
I am trying to make the above printer work on the Asus U36J laptop running on Trusty (14.04). First I had a problem with installing the drivers. It required tiff4 library absent in Trusty. Searching the forum I found a link to the library from the previous Ubuntu version. After installing it I was able to install the drivers. But now it does not print. It printed fine on 12.04 before the upgrade and it works on my other Asus and HP laptops but not on this one. The error in cups just says "cannot load library".

This is an extract from /var/log/cups/error_log just in case:
```
D [21/May/2014:23:01:01 +0100] [Job 37] Gutenprint: 5.2.10-pre2 Starting
D [21/May/2014:23:01:01 +0100] [Job 37] Gutenprint: command line: Canon-MG6100 '37' 'alex' 'Test Page' '1' <args>
D [21/May/2014:23:01:01 +0100] [Job 37] Gutenprint: using PPD file /etc/cups/ppd/Canon-MG6100.ppd
D [21/May/2014:23:01:01 +0100] cupsd is not idle any more, canceling shutdown.
E [21/May/2014:23:01:01 +0100] [Job 37] cannot load library
D [21/May/2014:23:01:01 +0100] cupsdMarkDirty(---J-)
D [21/May/2014:23:01:01 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [21/May/2014:23:01:01 +0100] cupsdMarkDirty(---J-)
D [21/May/2014:23:01:01 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [21/May/2014:23:01:01 +0100] [Job 37] Set job-printer-state-message to "cannot load library", current level=ERROR
D [21/May/2014:23:01:01 +0100] cupsdMarkDirty(----S)
```

Any help will be appreciated.

---

### Post by foxy123 on 2014-05-22
I have tried using Michael Gruz's PPA but got also an error, something about not able to specify a model number or something like that.

---

### Post by pdc on 2014-05-23
can I suggest we attempt to install the drivers that Canon supply for your printer? They supply debian packages; and Ubuntu uses debian packages

so if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100301802.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100301802.html) and click to Download; and if you select SAVE when asked what you want to do; by default, the file you will download cnijfilter-mg6100series-3.40-1-deb.tar.gz will end up in your Downloads directory

so if I give the commands in red; and if you copy and paste them into the terminal: I suggest using the top line of the terminal: and use the mouse: ie start at File; along to Edit and down to Paste ........ (and hit the enter key after each paste ..)

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg6100series-3.40-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg6100series-3.40-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

you will be asked if you have usb or wireless; I assume you are usb ?

that should get the printer driver installed; Canon supply scangearmp to run the scanner and you can get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100303102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100303102.html) and install in the same structure as for the printer driver

to initially run the scanner, the command is > [COLOR="#FF0000"]scangearmp[/COLOR] and then you create a launcher ..........to launch it ..........

I hope this helps

---

### Post by foxy123 on 2014-05-23
Thanks a lot for the reply. Actually I did install the provided drivers and everything worked fine on 12.04. It is only after the upgrade to 14.04 I have started getting this error. The driver is installed fine and scanning works but not printing. It is wifi printer by the way.

---

