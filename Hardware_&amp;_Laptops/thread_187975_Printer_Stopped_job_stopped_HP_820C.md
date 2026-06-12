---
title: "Printer Stopped: job stopped HP 820C"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by sedona on 2006-06-03
Requesting Help Please for *Printer Stopped: job stopped*
Clicking *Resume Jobs* has no effect. 
Have installed and re-installed HP Deskjet 820C, working
fine under that other OS that I don't want to use any more.
Also re-installed cupsys, and restarted same. 
Worked great initial Ubuntu install months ago but long prior
to upgrade to 6.06 the Ubuntu printing quit, works in XP.
Everything working great on Ubuntu 6.06 everything except HP.
Tried typing in term: fg %1 and still no reaction from
printer that works fine in XP.  Loving Linux, except for HP.
Welcome  suggestions, never posted before, so hate looking
stupid and wasting others time, but am out of resources. Thanks

---

### Post by klytu on 2006-06-23
Try this:
sudo gedit /etc/pnm2ppa.conf

In the section beginning with version, change from this:

version
#version 710 # 710, 712, 722 also acceptable
#version 820
#version 1000
sudo gedit /etc/pnm2ppa.conf

to this:

version 820

Save change and try to print. This worked for me with my HP722C.

---

### Post by sedona on 2006-07-09
Thank you for sharing with me this suggestion. 
This is my first *Reply* ever to any Thread, so further suggestions - style, content - are welcome.

After typing in terminal, sudo gedit /etc/pnm2ppa.conf then, The reaction was a flurry of error messages that I have never seen in Unbuntu in over a year of use, so I am encouraged that you have me working on the right section.  Whoow, just found error messages - copied below.
Can you suggest other area's to tweak that are indicated by these system reactions? 

sudo gedit /etc/pnm2ppa.conf
Password:
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:5963): WARNING **: Could not load python module modelines


** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5963): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed


Whew, and I thought everything is fine except just my printer.
Like you suggested, everything is commented# out except:

version  710
#version  720	# 710, 712, 722 also acceptable
version  710
#version 1000

log_info 1               # <= COMMENT THIS OUT TO GET THE NEW DEFAULT BEHAVIOR!


So, I will do as you suggested and comment out #verstion 710, and add version 820. 

Entire file is copied immediately below:
# Sample configuration file 
#
# This file will be automatically read upon startup if it is placed in
# /etc/pnm2ppa.conf
#
# uncomment entries by removing "#" to activate them.
#
#-----------set the printer model---------------------------
# The printer model will normally  be set by a -v <model> command
# line argument.   Otherwise, if not set in the configuration file
# it defaults to the 710/720 series.   Remove/comment out the line
# "version 0" below to get the default choice.
# 
# If there is more than one "version" entry activated, the last one
# will be used.   The printer version can also be set with the command line
# option e.g., "-v 720".

version  710
#version  720	# 710, 712, 722 also acceptable
version  710
#version 1000

#--------control system log messages from pnm2ppa-------------------
# pnm2ppa issues progress and error messages to the system log (syslog).
# For security reasons, no  input from the user is ever sent to the syslog.
# The setting "silent 1" suppresses messages to the syslog.   The
# setting "verbose 1"  sends messages to the standard error stream (stderr)
# in addition to the syslog. (Note: if pnm2ppa was compiled with the
# -D__NO_SYSLOG__ option (e.g., for BeOS),  syslog messages are
# diverted to stderr; use "silent 1" to suppress them.)

#silent 1
#verbose 1

# (NEW FEATURE:)
# standard informational messages ( when a job starts, when each page
# prints, job finished, etc.) will not be recorded in the System Log,
# unless explicitly activated here with the "log_info 1" keyword.
# (i.e., "log_info 0" is the default.)
# (Informational messages will still always be sent  to stderr in "verbose" 
# mode, even if log_info is not set.)

log_info 1               # <= COMMENT THIS OUT TO GET THE NEW DEFAULT BEHAVIOR!

# Note: the "silent 1" and "log_info" keywords are only accepted from the 
# system configuration  file (/etc/pnm2ppa.conf), and not from configuration 
# files specified  by users with the pnm2ppa option "-f".

#---------set the margins of the printed page-------------------
# Margins: these are distances from the edges of the paper in
# "dots" ( 600 dots = 1 inch = 2.54 cm).   
# Nothing outside these margins will be printed. 
# Default values are give below;  uncomment  and change, if necessary. 
# (Older versions of pnm2ppa required larger left and right margins to avoid 
# printer failure with  "flashing lights", but this  problem is believed to 
# be solved)

#topmargin      10 
#bottommargin   150
#leftmargin     10
#rightmargin    10

#----------center the printer output on the paper-------------------
# Offsets: these are adjustments for centering the print correctly on the
# paper.   Units are dots (1/600 inch).   Add a positive number of dots to
# xoff to move the printed image  to the  right, relative to the paper.
# add to yoff to move it  down.   The helper program calibrate_ppa prints
# a test page to  check the offsets (see CALIBRATON.txt):
# usage: "calibrate_ppa --center | pnm2ppa --bw  - - | lpr -l
# Default values are:

#xoffset   160
#yoffset    50

#------------align the  black and color ink cartridges--------
# Color Offsets: these control alignment between the black  ink
# and color ink print cartridges.   This changes a little  whenever  you  
# replace an ink cartridge, so the default values are just approximate.
#
# Use "calibrate_ppa --align  | pnm2ppa --fd - - | lpr -l "
# to print a test page to help you adjust the color offsets.
#
# The first line checks horizontal alignment ColOffsX,: 
# The second line checks vertical alignment ColOffsY,: 
# The alignment  is correct if alignment patterns "0" is best.   
# If a diffent alignment pattern is best, add or subtract the  + or
# - value shown below it to ColOffsX or ColOffSy.
# 
# See CALIBRATION.txt for more details.
# Use "calibrate_ppa --test  | pnm2ppa --fd - - | lpr -l " to check your
# new settings.

#ColOffsX	0
#ColOffsY	0

#---------------"shearing" corrections-------------------------------------
# shearing correction (for bidirectional printing modes)
# if there is a horizontal offset between right-to-left and left-to-right
# sweeps of the print head, adjust these in units of 1"/600 (1 dot). 
# There are separate corrections colorshear and blackshear for the 
# color and black  print heads.  The third and fourth lines of the
# alignment test page (see above) tests these.   
# The setting is correct when alignments "0" are correct.
# The (positive or negative) number shown under the best-aligned shearing 
# alignment pattern tells you how much to change the colorshar or blackshear
# value by.   (For, example, if you print the calibration page with 
# "colorshear 0" (the default value) and the best pattern is labelled "-2", 
# uncomment the "colorshear" value below and set it equal to -2.)

#colorshear    0
#blackshear    0

#-------------blackness control-----------------------------
# this controls the density of black ink used. 
# valid blackness choices are 1 2 3 4; controls the
# density of black ink used: 1 (least ink), 2 (default), 4 (most).
# 0 = no black ink.   This affects black ink bordered by whitespace
# only  (e.g. text, but not black in color images)

#blackness 2   

#------------Color correct curve Gamma parameters-------------------------
# Gamma color correction values for Red, Green and Blue:
# (Note: a more effective method of color correction is to use
# a calibration file /etc/pnm2ppa.gamma, in which case these
# Gamma values will not be used.  See COLOR.html or COLOR.txt) 
# The pnm2ppa option --noGamma suppresses color correction.

# The  standard Gamma  enhancement  curve is 
# gEnh(i) = (int) ( pow ( (double) i / 256, Gamma ) * 256 ) 
# (i.e., 256 times ( i*(1.0/256)) to the power Gamma ),
# where (int) i is the ppm color intensity, in the range 0 - 255.
# positive values of Gamma enhance  (increase the intensity of)
# the corresponding color.   Gamma = 1.0 corresponds to no
# color correction, gEnh[i] = i.

# You can specify Gamma values as a decimal number for each primary color

#GammaR 1.0      # red enhancement
#GammaG 1.0      # green enhancement
#GammaB 1.0      # blue enhancement

# For use with the printed output of "pnm2ppa -g ",
# you can also specify Gamma values using the integer GammaIdx,
# which gives Gamma = 1.0 - 0.033 * GammaIdx :

#RedGammaIdx	0     
#GreenGammaIdx	0
#BlueGammaIdx	0

# Default papersize (only used for printing the color calibration
# test page with pnm2ppa -g).  
# Valid choices are: a4, letter, legal:

#papersize letter    # this is the default  
#papersize legal
#papersize a4

#-----------suppress bidirectional printing---------------------

# by default the printing sweeps are now bidirectional (unimode 0);
# to make  unidirectional printing (left-to-right) the default behavior,
# (unimode 1) uncomment the next line .  (The command line options --uni 
# and --bi override the default behavior).  You might wish to print 
# unidirectionally to avoid shearing effects in high-quality
# color images, for example)

#unimode 1

#------------switch off (color) data compression------------------
# Previously, data compression of color data sent to the printer
# was not enabled.    It is now enabled by default, but has only
# been tested on HP71x/72xC models.   Uncomment and set "compression 0"
# to disable color data compression  if necessary.

#compression 1

#=====================================================================
# the following are switches for debugging purposes only:
# set their values to 0 to switch off the corresponding ink type:

#black_ink 1
#color_ink 1
#cyan_ink 1
#magenta_ink 1
#yellow_ink 1

---

### Post by klytu on 2006-07-30
Are you using Ubuntu (gnome desktop) or Kubuntu (KDE desktop)? The steps below assume you are working with Ubuntu and the default gnome desktop. (I have used KDE before, but I don't have Kubuntu set up). 

First thing you might want to try is checking for broken packages. Type in a terminal window:

```
gksudo synaptic
```

Enter your password when prompted. Click the Custom button on the bottom left corner, then highlight Broken. This should show any packages you have installed that are messed up. (There is a way to do all this from the command line, but I don't remember it.) You should reinstall any of these broken packages. This might take care of the error messages you are receiving from gedit. 

You can access your Printing Manager from a command line with:

```
gnome-cups-manager
```

From the info you posted about editing /etc/pnm2ppa.conf, I couldn't see your updated file showing the line with version 820. What happens when you try printing after making that change (and of course saving the corrected file before printing)?

About replying to messages, there are a LOT of formatting tools built-in. When you reply try hovering your mouse over the various icons in the message box. The quote and code tags are particularly useful. First type a bit of text, highlight it by dragging the mouse over it, and then click on either the quote or code icons and you will notice html tags wrapped around what you type. When you Preview Post you can see the effect before posting. Then you can go change things or try something else out and Preview Post again or Submit Reply when you are satisfied with all your changes.

---

### Post by sedona on 2006-08-17
> **klytu said:**
> Are you using Ubuntu (gnome desktop) or Kubuntu (KDE desktop)? The steps below assume you are working with Ubuntu and the default gnome desktop. (I have used KDE before, but I don't have Kubuntu set up). 

First thing you might want to try is checking for broken packages. Type in a terminal window:

```
gksudo synaptic
```

Enter your password when prompted. Click the Custom button on the bottom left corner, then highlight Broken. This should show any packages you have installed that are messed up. (There is a way to do all this from the command line, but I don't remember it.) You should reinstall any of these broken packages. This might take care of the error messages you are receiving from gedit. 

You can access your Printing Manager from a command line with:

```
gnome-cups-manager
```

From the info you posted about editing /etc/pnm2ppa.conf, I couldn't see your updated file showing the line with version 820. What happens when you try printing after making that change (and of course saving the corrected file before printing)? 

REPLY 17Aug06:
Thank you very much for the suggestions which gives me things to check.
I am running *gnome* desktop.

Checked for **broken** pkg's and *zero/none* broken per gksudo synaptic (Thank you, I didn't know about that feature).

Tried sudo: gnome-cups-manager: command not found
Ummmm, command not found does not sound good, am searching for help on that.

Below is copy of pertinate part of updated /etc/pnm2ppa.conf showing HP820: 
#version  710
#version  720	
# 710, 712, 722 also acceptable
#version  710
#version 1000
**version 820**

What happens now after making that change to /etc/pnm2ppa.conf is still nothing happens when click on print. No different result. I think I have a more basic problem which is getting Printer configuration Tool installed.

I will research why I am unable to access Printing Manager from a command line using ```
gnome-cups-manager
``` -- that seems to be an initial necessary step.

At this point it seems to me that I need to *install* HP820, and then any configuring that is necessary. Not having my Printer Configuration Tool seems to be the basic challenge at this point. I am going to continue researching this, I am inspired by these ideas of areas to check in my ubuntu. Thank you for the suggestions!

Ubuntu 6.06 Gnome Desktop | AMD Athlon 1800+ (1.5 GHz) | Maxtor 60 Gb HD | RAM 512 Mb PC 3200 | Asus A8V-E deluxe | Sony CD-RW | HP Deskjet 820Cse | still dualboot Ubuntu 6.06 32 bit & Windows XP Sp2 only because HP820 printer not yet configured correct in Ubuntu - which is my remaining challenge to exclusively be using Ubuntu.

---

### Post by klytu on 2006-08-17
Try this:

```
sudo aptitude update
```

and then this:

```
sudo aptitude install gnome-cups-manager
```

when that completes, try installing your printer again.

---

### Post by sedona on 2006-08-17
> **klytu said:**
> Try this:

```
sudo aptitude update
```

and then this:

```
sudo aptitude install gnome-cups-manager
```

when that completes, try installing your printer again.

[SIZE="3"]Reply:  [SIZE="4"]**Y E S !**[/SIZE]  =D> 
Printed in Firefox and text editor, but not in OO, so next will go see if restarting OO helps or if there is a configuration.
Thank you Klytu very much! I am extremely grateful. Now I can work in Ubuntu and not boot XP.[/SIZE] I am thrilled! Thank you.

---

### Post by sedona on 2006-08-17
> **klytu said:**
> Try this:

```
sudo aptitude update
```

and then this:

```
sudo aptitude install gnome-cups-manager
```

when that completes, try installing your printer again.

Reply:  And YES! restarting OO and it prints fine there as well.
Move over Clint Eastwood, YOU just made my day!
Thank you again very much.

---

