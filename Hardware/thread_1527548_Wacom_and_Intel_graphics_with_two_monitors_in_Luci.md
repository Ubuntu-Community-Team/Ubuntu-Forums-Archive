---
title: "Wacom and Intel graphics with two monitors in Lucid"
date: 2010-07-09
forum: Hardware
---

### Post by chh on 2010-07-09
Hello,

I have a Lenovo Thinkpad X201 Tablet with intel graphics (i965) and 64bit Ubuntu 10.04. When using a second monitor to extend the desktop, the wacom is not restricted to one monitor but stretched over both, i.e., when I point somewhere on the internal touchscreen, the cursor is not moved to the correct position on the internal monitor, but the position is mapped to the corresponding relative position of the overall desktop.

I know there are already some related threads, but none of them seemed  to help me: 
of course xsetwacom has the "TwinView" setting, but this doesn't seem to work for me since the intel graphics does not seem to support twinview (only xinerama).

I also noticed that xsetwacom can set the "TwinView" option to "xinerama", but I get
```
$ xsetwacom set "Serial Wacom Tablet" TwinView xinerama
Usage: xsetwacom rotate <device name> [NONE | CW | CCW | HALF]
```However, xsetwacom does not accept the command "rotate".

Any suggestions would be appreciated.

Chris

---

### Post by trickylogician on 2011-01-07
Having the same issue on a ThinkPad x60 tablet with intel graphics and dual monitors. Maybe someone will respond, now that it is a new year.

---

### Post by Favux on 2011-01-07
Hi trickylogician,

It depends on a lot of variables.  See the [Wacom Multi-monitor HOW TO]("http://ubuntuforums.org/showthread.php?t=1656089").

---

### Post by chh on 2011-01-07
Hi,
I have not yet had time to read through the howto that Favux has posted, so maybe what I post now is more or less equivalent, but here is the solution that I finally came up with. I have been using it for months on lucid with gnome, and it works like a charm.

Create a file called updatewacom, insert the following code, give execute permission and copy it somewhere in the path. This scripts adapts the wacom to the current display settings and works with dual head, arbitrary resolutions, and arbitrary display rotation.

```
#!/bin/bash
# Update Wacom
# (c) 2010 chh (toxic at freenet dot de)
# Sep 7th, 2010

# read desktop resolution
desksol=`xrandr | grep Screen\ 0 | sed "s/.*current \([0-9]*\)\ x\ \([0-9]*\).*/\1x\2/g"`
desksolX=`echo $desksol | cut -d "x" -f1`
desksolY=`echo $desksol | cut -d "x" -f2`
# read info of internal monitor
randrinfo=`xrandr | grep LVDS1`
# extract rotation and replace it with the keywords used by setxwacom
rinfo=`echo $randrinfo | cut -d " " -f4 | sed 's/right/CW/' | sed 's/left/CCW/' | sed 's/inverted/HALF/' | sed 's/.normal/NONE/'`
# extract resolution and offset
sinfo=`echo $randrinfo | cut -d " " -f3`
# extract resolution of internal monitor
resol=`echo $sinfo | cut -d "+" -f1`
resolX=`echo $resol | cut -d "x" -f1`
resolY=`echo $resol | cut -d "x" -f2`
# extract/compute offset above and below the internal monitor
offX=`echo $sinfo | cut -d "+" -f2`
offY=`echo $sinfo | cut -d "+" -f3`
botoffX=`echo $desksolX-$offX-$resolX | bc`
botoffY=`echo $desksolY-$offY-$resolY | bc`

# possibly, the input devices are called differently on another system
for pad in "Serial Wacom Tablet" "Serial Wacom Tablet eraser" "Serial Wacom Tablet touch"
do
    # rotate the input decive
    xsetwacom set "$pad" Rotate $rinfo
    # reset calibration to default values
    xsetwacom set "$pad" xyDefault 1
    # read the resolution of the input device
    padX=`xsetwacom get "$pad" BottomX`
    padY=`xsetwacom get "$pad" BottomY`

    # compute the coordinates needed to calibrate the input device
    toppadX=`echo $padX*$offX/$resolX | bc`
    toppadY=`echo $padY*$offY/$resolY | bc`
    botpadX=`echo $padX*$desksolX/$resolX-$toppadX | bc`
    botpadY=`echo $padY*$desksolY/$resolY-$toppadY | bc`
    
    # calibrate the input device
    xsetwacom set "$pad" TopX -$toppadX
    xsetwacom set "$pad" TopY -$toppadY
    xsetwacom set "$pad" BottomX $botpadX
    xsetwacom set "$pad" BottomY $botpadY
done

# Optional: set pen button to right click
# xsetwacom set "Serial Wacom Tablet" Button2 3

```now create another executable script called updatewacom_eventhandler.py, insert the following code, and add the script to the gnome startup applications (preferences, startup applications). This script is an event handler and will call the updatewacom script whenever the display settings are changed.
```

#!/usr/bin/python
#
# Event Handler for Update Wacom
# (c) 2010 chh (toxic at freenet dot de)
# Sep 7th, 2010
# 
# based on python-xlib's xrandr example:
#
# examples/xrandr.py -- demonstrate the RandR extension
#
#    Copyright (C) 2009 David H. Bronke <whitelynx@gmail.com>
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

import sys, os

# Change path so we find Xlib
sys.path.insert(1, os.path.join(sys.path[0], '..'))

from Xlib import X, display, Xutil
from Xlib.ext import randr

# Application window (only one)
class Window:
    def __init__(self, display):
        self.d = display

        # Check for extension
        if not self.d.has_extension('RANDR'):
            sys.stderr.write('%s: server does not have the RANDR extension\n'
                             % sys.argv[0])
            print self.d.query_extension('RANDR')
            sys.stderr.write("\n".join(self.d.list_extensions()))
            if self.d.query_extension('RANDR') is None:
                sys.exit(1)

        # Grab the current screen
        self.screen = self.d.screen()

        self.window = self.screen.root.create_window(
            50, 50, 300, 200, 2,
            self.screen.root_depth,
            X.InputOutput,
            X.CopyFromParent,

            # special attribute values
            background_pixel = self.screen.white_pixel,
            event_mask = (X.ExposureMask |
                          X.StructureNotifyMask |
                          X.ButtonPressMask |
                          X.ButtonReleaseMask |
                          X.Button1MotionMask),
            colormap = X.CopyFromParent,
            )

        self.gc = self.window.create_gc(
            foreground = self.screen.black_pixel,
            background = self.screen.white_pixel,
            )

        # Set some WM info

        self.WM_DELETE_WINDOW = self.d.intern_atom('WM_DELETE_WINDOW')
        self.WM_PROTOCOLS = self.d.intern_atom('WM_PROTOCOLS')

        self.window.set_wm_name('Xlib example: xrandr.py')
        self.window.set_wm_icon_name('xrandr.py')
        self.window.set_wm_class('xrandr', 'XlibExample')

        self.window.set_wm_protocols([self.WM_DELETE_WINDOW])
        self.window.set_wm_hints(flags = Xutil.StateHint,
                                 initial_state = Xutil.NormalState)

        self.window.set_wm_normal_hints(flags = (Xutil.PPosition | Xutil.PSize
                                                 | Xutil.PMinSize),
                                        min_width = 20,
                                        min_height = 20)

        # Mapping the window would make it visible
        #self.window.map()

        # Enable all RandR events.
        self.window.xrandr_select_input(
            randr.RRScreenChangeNotifyMask
            | randr.RRCrtcChangeNotifyMask
            | randr.RROutputChangeNotifyMask
            | randr.RROutputPropertyNotifyMask
            )

        resources = self.window.xrandr_get_screen_resources()._data
        
        os.system('updatewacom')

    # Main loop, handling events
    def loop(self):
        current = None
        while 1:
            e = self.d.next_event()

            # Window has been destroyed, quit
            if e.type == X.DestroyNotify:
                sys.exit(0)

            # Screen information has changed
            elif e.type == self.d.extension_event.ScreenChangeNotify:
                os.system('updatewacom')

            # Somebody wants to tell us something
            elif e.type == X.ClientMessage:
                if e.client_type == self.WM_PROTOCOLS:
                    fmt, data = e.data
                    if fmt == 32 and data[0] == self.WM_DELETE_WINDOW:
                        sys.exit(0)

if __name__ == '__main__':
    Window(display.Display()).loop()

```that's all folks. have fun with it
best, 
chris

---

