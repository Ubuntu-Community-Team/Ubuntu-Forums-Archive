---
title: "E: ttf-mathematica4.1: subprocess pre-removal script returned error exit status 1"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by purrcy on 2009-01-02
I tried to install ttf-mathematica4.1 and it is corrupted.  I get error codes whenever I try to use apt-get or synaptic.  I've tried everything but the right thing to get rid of it, but it's still there.

How do I get rid of this package?

---

### Post by Partyboi2 on 2009-01-02
Open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get -f install
sudo apt-get remove  ttf-mathematica4.1
``` and post the outputs back here.

---

### Post by purrcy on 2009-01-03
Sorry.  That didn't work.

---

### Post by mithbuntu on 2009-03-24
I'm having this problem right now and it is stopping me from repairing my system.  Any updates?

I upgraded to 8.10 and went to the SPM to install new software.  One of the packages I accidentally installed was 'scrollkeeper'.  When I rebooted, I was dumped to the root terminal after I logged in through the shell rather than the gui.

I thought there may have been a problem when I noticed ubuntu-deskop / gnome-desktop-environment were marked for uninstallation, but I figured I was just replacing them with something else. I didn't think the SPM would allow me to kill off the gui so easily.

I tried sudo apt-get install ubuntu-desktop/ sudo apt-get install gnome-desktop-environment/ sudo apt-get remove scrollkeeper which all led me to the problem with ttf-mathematica4.1 erroring out.

So I then I tried sudo apt-get remove ttf-mathematica4.1 and then I get all sorts of weird error messages.

All I want to know is how can I repair my gui? Please don't tell me I need to reinstall ubuntu.

the error i see is:
```



Binary package hint: ttf-mathematica4.1

Selecting previously deselected package ttf-mathematica4.1.
(Reading database ... 160253 files and directories currently installed.)
Preparing to replace ttf-mathematica4.1 4 (using .../ttf-mathematica4.1_4_all.deb) ...
The license has already been accepted
Unpacking replacement ttf-mathematica4.1 ...
Setting up ttf-mathematica4.1 (4) ...
--2008-11-18 15:27:39-- http://support.wolfram.com/mathematica/systems/windows/general/files/MathFonts_TrueType_41.exe
Resolving support.wolfram.com... 140.177.205.40
Connecting to support.wolfram.com|140.177.205.40|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://support.wolfram.com/index.en.html [following]
--2008-11-18 15:27:40-- http://support.wolfram.com/index.en.html
Connecting to support.wolfram.com|140.177.205.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `./index.en.html'

    [<=> ] 0 --.-K/s [ <=> ] 4 017 19,2K/s [ <=> ] 9 777 23,4K/s [ <=> ] 19 186 34,1K/s in 0,5s

2008-11-18 15:27:41 (34,1 KB/s) - `./index.en.html' saved [19186]

checking MathFonts_TrueType_41.exe
Downloaded file looks corrupted!
dpkg: error processing ttf-mathematica4.1 (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mathematica4.1

```

---

### Post by Partyboi2 on 2009-03-25
> **mithbuntu said:**
> I'm having this problem right now and it is stopping me from repairing my system.  Any updates?

I upgraded to 8.10 and went to the SPM to install new software.  One of the packages I accidentally installed was 'scrollkeeper'.  When I rebooted, I was dumped to the root terminal after I logged in through the shell rather than the gui.

I thought there may have been a problem when I noticed ubuntu-deskop / gnome-desktop-environment were marked for uninstallation, but I figured I was just replacing them with something else. I didn't think the SPM would allow me to kill off the gui so easily.

I tried sudo apt-get install ubuntu-desktop/ sudo apt-get install gnome-desktop-environment/ sudo apt-get remove scrollkeeper which all led me to the problem with ttf-mathematica4.1 erroring out.

So I then I tried sudo apt-get remove ttf-mathematica4.1 and then I get all sorts of weird error messages.

All I want to know is how can I repair my gui? Please don't tell me I need to reinstall ubuntu.

the error i see is:
```



Binary package hint: ttf-mathematica4.1

Selecting previously deselected package ttf-mathematica4.1.
(Reading database ... 160253 files and directories currently installed.)
Preparing to replace ttf-mathematica4.1 4 (using .../ttf-mathematica4.1_4_all.deb) ...
The license has already been accepted
Unpacking replacement ttf-mathematica4.1 ...
Setting up ttf-mathematica4.1 (4) ...
--2008-11-18 15:27:39-- http://support.wolfram.com/mathematica/systems/windows/general/files/MathFonts_TrueType_41.exe
Resolving support.wolfram.com... 140.177.205.40
Connecting to support.wolfram.com|140.177.205.40|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://support.wolfram.com/index.en.html [following]
--2008-11-18 15:27:40-- http://support.wolfram.com/index.en.html
Connecting to support.wolfram.com|140.177.205.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `./index.en.html'

    [<=> ] 0 --.-K/s [ <=> ] 4 017 19,2K/s [ <=> ] 9 777 23,4K/s [ <=> ] 19 186 34,1K/s in 0,5s

2008-11-18 15:27:41 (34,1 KB/s) - `./index.en.html' saved [19186]

checking MathFonts_TrueType_41.exe
Downloaded file looks corrupted!
dpkg: error processing ttf-mathematica4.1 (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mathematica4.1

```
There is a bug report [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ttf-mathematica4.1/+bug/299427") with a couple of possible solutions. Hope one of them works for you. :)

---

