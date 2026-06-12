---
title: "firefox keeps shutting off.."
date: 2008-12-02
forum: General Help
---

### Post by EnzoRacing on 2008-12-02
Lately i'll be browsing around and firefox will just shut off.

Anyone have any ideas why?

---

### Post by taurus on 2008-12-02
Try running firefox from a terminal to see what's the error message is.

Applications -> Accessories -> Terminal
```
firefox
```

---

### Post by mkvnmtr on 2008-12-02
I recently had my firefox go to 100% cpu usage and stay there for a long time. Sometimes it would freeze. On Htop I could never see why. No errors either. I finally uninstalled AdBlock and the problem went away. I think I added too many block lists. You could try uninstalling your add-ons one at a time to see if the problem is there.

---

### Post by EnzoRacing on 2008-12-02
okay so i ran it thru terminal and it finally shut off again..

It says segmentation fault in terminal..

---

### Post by taurus on 2008-12-02
Which release are you running?  Is it 32bit or 64bit?  Which version of firefox do you have?  Does the shut off happen randomly, not at a specific site?

---

### Post by gibbylinks on 2008-12-02
I have the same fault. I can get it to re-occur on Comets website by doing a search

See below

 firefox
NS_PluginInitialize call ---------------------------------------------------
xEmbed supported in this browser
GTK2 supported in this browser
NOTE: NPAPI plugin set GNASHRC to /usr/etc/gnashpluginrc:/home/gibbylinks/.gnashpluginrc
PARAM: style = visibility: visible;
PARAM: id = homepage_top
PARAM: data = /comet/ev2/content/pages/homepage/homepage.swf
PARAM: type = application/x-shockwave-flash
PARAM: width = 100%
PARAM: height = 280
PARAM: SRC = /comet/ev2/content/pages/homepage/homepage.swf
PARAM: PARAM = 
PARAM: menu = false
PARAM: wmode = transparent
PARAM: flashvars = startingTab=1&loadTab3=/comet/ev2/content/pages/homepage/christmas-cracker.swf
NewStream: The full URL is [http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf](http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf)
Closed 63 files.
Starting process: /usr/bin/gtk-gnash -x 67112073 -j 1239 -k 280 -u [http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf](http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf) -F 68 -U [http://www.comet.co.uk/shopcomet/homePage.do?zone_id=13](http://www.comet.co.uk/shopcomet/homePage.do?zone_id=13) -P PARAM= -P SRC=/comet/ev2/content/pages/homepage/homepage.swf -P data=/comet/ev2/content/pages/homepage/homepage.swf -P flashvars=startingTab=1&loadTab3=/comet/ev2/content/pages/homepage/christmas-cracker.swf -P height=280 -P id=homepage_top -P menu=false -P style=visibility: visible; -P type=application/x-shockwave-flash -P width=100% -P wmode=transparent - 
Forked successfully, child process PID is 23015
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/gibbylinks/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/gibbylinks/.gnashpluginrc
NewStream: The full URL is [http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf](http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf)
Closed 65 files.
Starting process: /usr/bin/gtk-gnash -x 67112073 -j 1239 -k 280 -u [http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf](http://www.comet.co.uk/comet/ev2/content/pages/homepage/homepage.swf) -F 70 -U [http://www.comet.co.uk/shopcomet/homePage.do?zone_id=13](http://www.comet.co.uk/shopcomet/homePage.do?zone_id=13) -P PARAM= -P SRC=/comet/ev2/content/pages/homepage/homepage.swf -P data=/comet/ev2/content/pages/homepage/homepage.swf -P flashvars=startingTab=1&loadTab3=/comet/ev2/content/pages/homepage/christmas-cracker.swf -P height=280 -P id=homepage_top -P menu=false -P style=visibility: visible; -P type=application/x-shockwave-flash -P width=100% -P wmode=transparent - 
RcInitFile: couldn't open file: Forked successfully, child process PID is 23017
/usr/etc/gnashrc
RcInitFile: couldn't open file: /home/gibbylinks/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/gibbylinks/.gnashpluginrc

(gtk-gnash:23017): Gdk-WARNING **: GdkWindow 0x440001e unexpectedly destroyed

(gtk-gnash:23017): Gdk-WARNING **: GdkWindow 0x4400003 unexpectedly destroyed
The program 'gtk-gnash' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 184 error_code 9 request_code 148 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Shutting down
Child process exited with status 15
plugin instance destruction
shutting down input chan 0xa6d7448
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Segmentation fault

I'm running 8.10 with Firefox 3.04

---

