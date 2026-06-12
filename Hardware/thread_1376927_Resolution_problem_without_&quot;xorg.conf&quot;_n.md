---
title: "Resolution problem without &quot;xorg.conf&quot; nor &quot;dpkg --configure -a&quot;"
date: 2010-01-09
forum: Hardware
---

### Post by iperetta on 2010-01-09
Hi, there

I'm a beginner with Linux, but I could find myself several times by now. I recently have installed Ubuntu 9.10.  The fact is, it hasn't recognized my monitor (a Philips 105E) and it get me stuck with 800x600 unknown monitor. When I try to solve my resolution problem, first I've looked for "xorg.conf" file:

```
igor@RatZ:/etc/X11$ ls /etc/X11/
app-defaults             fonts    xinit       Xsession          XvMCConfig
cursors                  rgb.txt  xkb         Xsession.d        Xwrapper.config
default-display-manager  X        Xresources  Xsession.options
```And I didn't find it. Next, I've tried "sudo dpkg --configure -a":

```
igor@RatZ:/etc/X11$ sudo dpkg --configure -a
[sudo] password for igor: 
igor@RatZ:/etc/X11$
```And nothing's happen. Then, I've tried to find out what Ubuntu has detected:

```
igor@RatZ:/etc/X11$ lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
igor@RatZ:/etc/X11$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9
```So, what I got to do or what do I need to update/install to solve my resolution problem?  

Thank you for support!

---

### Post by iperetta on 2010-01-09
Uff! Finally!

I was really hard to understand how to do it, but I did, thanks to [http://ubuntuforums.org/showthread.php?t=1313280&highlight=Resolution+problem](http://ubuntuforums.org/showthread.php?t=1313280&highlight=Resolution+problem).

To make it short (take note because it will change to terminal mode, you'll loose desktop):

Start a terminal. Enter with

```
sudo service gdm stop
```It'll ask for user and pwd

```
sudo Xorg -configure
```It'll create a xorg.conf.new in /home/yourself

```
sudo service gdm start
```Now, start a terminal. Enter with:

```
sudo mv /home/yourself/xorg.conf.new /etc/X11/xorg.conf
sudo gedit /etc/X11/xorg.conf
```Inside the file, search for << Section "Monitor" >> and make it closer to:

```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync *AA*-*BB*
        VertRefresh *CC*-*DD*
        #UseModes     "Modes0" #monitor0usemodes
        Option      "PreferredMode" "1024x768"
EndSection
```Where AA-BB and CC-DD are based on your monitor manual (mine, I found in the manual under Technical Specifications/  Scanning/ Horizontal scanning & Horizontal scanning).

In the same file, search for << Section "Screen" >> and make it closer to:

```
Section "Screen"
       Identifier "Screen0"
       Device     "Card0"
       Monitor    "Monitor0"
       DefaultDepth 24
            # (...)
       Subsection "Display"
       Depth       24
       Modes       "1024x768"
       EndSubsection
EndSection
```Then, do it again:

```
sudo service gdm stop
```It'll drop you from gnome desktop.
```
sudo service gdm start
```It'll jump you again, this time with 1024x768 resolution.

Hope this one could find more troubled heart users to help with.

Thanks!

---

