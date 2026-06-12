---
title: "LCDd works fine if restarted AFTER Myth is running...help"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by marvin1969 on 2008-02-17
All,
    I am running Mythbuntu 7.04 on an AMD-64 in a Silverstone case with VFD.  I have the VFD working fine with Myth; however, if the box restarts, the VFD works oddly.  No clock displayed and only the top line of the 2-line display works.  Second line may be blank, or garbage characters or blocks.  If I restart LCDd (remotely or locally), it works flawlessly (clock displays, menu and submenus display while navigating, etc.)  Also, when I go to watch TV, it displays the info, but usually only on the first line, and eventually it always munges the display in the VFD until I restart it.

    Any suggestions?  My LCDd.conf is attached.

Thanks for any assistance.

/etc/LCDd.conf
```

# LCDd.conf -- configuration file for the LCDproc server daemon LCDd
#
# This file contains the configuration for the LCDd server.
# 
# The format is ini-file-like. It is divided into sections that start at
# markers that look like [section]. Comments are all line-based comments,
# and are lines that start with '#' or ';'.
#
# The server has a 'central' section named [server]. For the menu there is
# a section called [menu]. Further each driver has a section which
# defines how the driver acts.
#
# The drivers are activated by specifiying them in a driver= line in the
# server section, like:
#
#   Driver=curses
#
# This tells LCDd to use the curses driver.
# The first driver that is loaded and is capable of output defines the
# size of the display. The default driver to use is curses.
# If the driver is specified using the -d <driver> command line option,
# the Driver= options in the config file are ignored.
#
# The drivers read their own options from the respective sections.



## Server section with all kinds of settings for the LCDd server ##
[server]

# Tells the server to load the given drivers. Multiple lines can be given.
# The name of the driver is case sensitive and determines the section
# where to look for further configuration options of the specific driver
# as well as the name of the dynamic driver module to load at runtime.
# The latter one can be changed by giving af File= directive in the
# driver specific section.
#
# The following drivers are supported:
#   bayrad, CFontz, CFontz633, CFontzPacket, curses, CwLnx, ea65, 
#   EyeboxOne, g15, glcdlib, glk, hd44780, icp_a106, imon, IOWarrior,
#   irman, joy, lb216, lcdm001, lcterm, lirc, MD8800, ms6931, mtc_s16209x,
#   MtxOrb, NoritakeVFD, picolcd, pyramid, sed1330, sed1520, serialPOS,
#   serialVFD, sli, stv5730, svga, t6963, text, tyan, ula200, xosd
#Driver=curses
Driver=hd44780
#Driver=imon

# Tells the driver to bind to the given interface
Bind=127.0.0.1

# Listen on this specified port; defaults to 13666.
Port=13666

# Sets the reporting level; defaults to 2 (warnings and errors only).
#ReportLevel=3
ReportLevel=3

# Should we report to syslog instead of stderr ? Default: no
ReportToSyslog=yes

# Sets the default time in seconds to displays a screen.
WaitTime=5

# User to run as.  LCDd will drop its root priviledges,
# if any, and run as this user instead.
User=nobody

# If yes, the the serverscreen will be rotated as a usual info screen. If no,
# it will be a background screen, only visible when no other screens are
# active.
ServerScreen=no

# The server will stay in the foreground if set to true.
#Foreground=no

# Where can we find the driver modules ?
# IMPORTANT: Make sure to change this setting to reflect your
#            specific setup! Otherwise LCDd won't be able to find
#            the driver modules and will thus not be able to
#            function properly.
# NOTE: Always place a slash as last character !
DriverPath=/usr/lib/lcdproc/

# GoodBye message: each entry represents a display line; default: builtin
#GoodBye="Thanks for using"
#GoodBye="   LCDproc!"
Hello="Starting display"
Hello=" using LCDproc"
GoodBye="    Good-Bye    "
GoodBye="Have a nice day!"

# The "...Key=" lines define what the server does with keypresses that
# don't go to any client.
# These are the defaults:
ToggleRotateKey=Enter
PrevScreenKey=Left
NextScreenKey=Right
#ScrollUpKey=Up
#ScrollDownKey=Down

# If you have only 4 keys, you can choose to use this:
#ToggleRotateKey=Enter
#PrevScreenKey=Up
#NextScreenKey=Down

# If you have only 3 keys, you can choose to use this:
#ToggleRotateKey=Enter
#PrevScreenKey=Up



## The menu section. The menu is an internal LCDproc client. ##
[menu]
# You can configure what keys the menu should use. Note that the MenuKey
# will be reserved exclusively, the others work in shared mode.

# The following works excellent with 4 keys or more.
MenuKey=Escape
EnterKey=Enter
UpKey=Up
DownKey=Down
# If you have 6 keys you may define these as well
#LeftKey=Left
#RightKey=Right

# If you have only 3 keys, you could use something like this:
#MenuKey=Escape
#EnterKey=Enter
#DownKey=Down


### Driver sections are below this line, in alphabetical order  ###
## Hitachi HD44780 driver ##
[hd44780]

# Select what type of connection. See documentation for types.
#ConnectionType=4bit
ConnectionType=winamp

# Port where the LPT is. Usual values are 0x278, 0x378 and 0x3BC
Port=0x378

# Device of the serial interface (default is /dev/lcd)
#Device=/dev/ttyS0

# Bitrate of the serial port (0 for interface default)
Speed=0

# If you have a keypad connected.
# You may also need to configure the keypad layout further on in this file.
Keypad=no

# set the initial contrast (for bwctusb only) [default: 0; legal: 0 - 1000]
Contrast=0

# If you have a switchable backlight.
#Backlight=no
Backlight=yes

# If you have the additional output port ("bargraph") and you want to
# be able to control it with the lcdproc OUTPUT command
OutputPort=no

# Specifies if the last line is pixel addressable or it controls an
# underline effect. [default: true (= pixel addressable); legal: yes, no]
#Lastline=true

# Specifies the size of the LCD.
# In case of multiple combined displays, this should be the total size.
#Size=20x4
Size=16x2

# For multiple combined displays: how many lines does each display have.
# Vspan=2,2 means both displays have 2 lines.
#vspan=2,2

# If you have an HD66712, a KS0073 or an other 'almost HD44780-compatible',
# set this flag to get into extended mode (4-line linear).
# This flag is NOT the old obsolete Extended option.
#ExtendedMode=yes

# Character map to to map ISO-8859-1 to the LCD's character set
# [default: hd44780_default; legal: hd44780_default, ea_ks0073, sed1278f_0b ]
Charmap=hd44780_default

# If your display is slow and cannot keep up with the flow of data from
# LCDd, garbage can appear on the LCDd. Set this delay factor to 2 or 4
# to increase the delays. Default: 1.
#DelayMult=2

# Some displays (e.g. vdr-wakeup) need a message from the driver to that it
# is still alive. When set to a value bigger then null the character in the
# upper left corner is updated every <KeepAliveDisplay> seconds. Default: 0.
#KeepAliveDisplay=0
KeepAliveDisplay=1

# If you experience occasional garbage on your display you can use this
# option as workaround. If set to a value bigger than null it forces a
# full screen refresh <RefreshDiplay> seconds. Default: 0.
#RefreshDisplay=5

# You can reduce the inserted delays by setting this to false.
# On fast PCs it is possible your LCD does not respond correctly.
# Default: true.
DelayBus=true

# If you have a keypad you can assign keystrings to the keys.
# See documentation for used terms and how to wire it.
# For example to give directly connected key 4 the string "Enter", use:
#   KeyDirect_4=Enter
# For matrix keys use the X and Y coordinates of the key:
#   KeyMatrix_1_3=Enter
KeyMatrix_4_1=Enter
KeyMatrix_4_2=Up
KeyMatrix_4_3=Down
KeyMatrix_4_4=Escape

# EOF

```

---

### Post by marvin1969 on 2008-02-23
Just an update.  I got this working by changing the LDCd starts from S60LCDd to S99LCDd  in the rcX.d directories.  LCD works fine now.

---

