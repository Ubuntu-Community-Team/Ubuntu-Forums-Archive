---
title: "Wacom, HAL and right click and more....."
date: 2009-05-20
forum: Hardware
---

### Post by ragtag on 2009-05-20
For 8.10 I used xorg.conf for the Wacom on my TabletPC, as HAL wasn't working corerctly. Now that I've upgraded, HAL almost worked out of the box, including pressure in GIMP. :)  But there are a few problems.

I can't get right clicking to work at all, which I really need as I use it with EasyStroke to do gesture control. Is there a way to configure this in HAL?

 And, I don't know how to rotate the Wacom. I used to use the command below, but now I get the following error:

```
xsetwacom set "stylus" Rotate CW
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'
```

This, of xourse, makes sense as I'm using HAL. But what's the HAL way of rotating the Wacom, preferably interactively. I have a script I use to toggle the screen and tablet rotation together that used to work great.

I tried uncommenting the wacom xorg.conf lines, but then the pen just stopped working. Running wacdump on /dev/input/wacom returns:

```

WacomOpenTablet: Connection timed out

```

So how do I get the right click (side button) to work with HAL

---

### Post by ragtag on 2009-05-20
Figured out half of this myself, maybe I posted a bit too soon. I added a file called /etc/hal/fdi/policy/custom_wacom.fdi that looks like this.

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">25,0,100,75</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">25,0,100,75</merge>
      </match>
    </match>
  </device>

</deviceinfo>

```

The main difference in mine to the one posted here [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi) is that TPCButton is turned off, and the lines containing Button2. They are probably not needed for the eraser, but I just left them in there. :)  My pressure curve is different from the default, so only include that if you want a softer touch.

Now...all I need to figure out is how to rotate the wacom interactively. I assume I can edit that file with the rotate option, but I want to do it from a script so I can have a button that rotates the screen and wacom together. Any ideas?

---

### Post by Favux on 2009-05-20
Hi ragtag,

What tablet pc do you have?

If your rotate script (xsetwacom commands) isn't working then wacomcpl probably isn't either.  In a terminal does:
```
xsetwacom list
```
show anything with your new .fdi?  This will show you how HAL is returning the device names:
```
xinput --list
```

If xsetwacom list is blank then see Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by ragtag on 2009-05-21
Thanks for the pointers. I managed to figure it out. xinput --list returned the name of the wacom as "Wacom Serial Tablet PC Pen Tablet/Digitizer", so it was a simple case of replacing "stylus" in my script with this. Now my rotate script looks like this.

```

    rotation=`xrandr -q | grep "LVDS" | awk '{print $4}'`
    if [ "$rotation" = "(normal" ]; then
        xrandr -o right
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate CW
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" Rotate CW
    else
        xrandr -o normal
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate NONE
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" Rotate NONE
    fi

```

This script toggles the screen and tablet rotation on my HP TC4400.

:)

---

### Post by Favux on 2009-05-21
Hi ragtag,

Good job getting rotation back.  If it goes away again you'll know they updated something, probably the .fdi.

---

### Post by ragtag on 2009-05-22
There is a minor bug with this solution (that actually also happens on WindowsXP in different drawing applications). If I have the GIMP open when I rotate the screen, it maps incorrectly within the GIMP window afterwards. This is simply fixed by restarting GIMP after you rotate the screen, so it's not really a problem. :)

Thanks for the help, the xinput --list was what solved it for me. :)

---

### Post by sarah.fauzia on 2009-05-23
> **ragtag said:**
> Thanks for the pointers. I managed to figure it out. xinput --list returned the name of the wacom as "Wacom Serial Tablet PC Pen Tablet/Digitizer", so it was a simple case of replacing "stylus" in my script with this. Now my rotate script looks like this.

```

    rotation=`xrandr -q | grep "LVDS" | awk '{print $4}'`
    if [ "$rotation" = "(normal" ]; then
        xrandr -o right
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate CW
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" Rotate CW
    else
        xrandr -o normal
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate NONE
        xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" Rotate NONE
    fi

```

This script toggles the screen and tablet rotation on my HP TC4400.

:)

Will this work for the touchscreen as well, or only the stylus? I never had to calibrate touch for different rotations, before.

Output of my xinput --list

```

xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ThinkPad Extra Buttons"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PnP Device (WACf008)"	id=3	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"PnP Device (WACf008) touch"	id=4	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 50
		Max_value is 931
		Resolution is 106
	Axis 1 :
		Min_value is 80
		Max_value is 953
		Resolution is 141
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"PnP Device (WACf008) eraser"	id=5	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"AT Translated Set 2 keyboard"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"TPPS/2 IBM TrackPoint"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Video Bus"	id=9	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

And my rotate script (unmodified):

```

#!/usr/bin/python

import os, sys, re

  # All allowed rotations
rotations = ['normal', 'right', 'inverted', 'left']

  # Keyboard scan codes for arrow keys
scanCodes = {'up': 0x71, 'dn': 0x6f, 'lt': 0x6e, 'rt': 0x6d}

  # Keycodes to use for each rotation
  # 104 = pgup, 109 = pgdn, 105 = left, 106 = right, 103 = up, 108 = down
keyCodes = {
            'normal':   {'up': 103, 'dn': 108, 'lt': 105, 'rt': 106},
            'right':    {'up': 105, 'dn': 106, 'lt': 108, 'rt': 103},
            'inverted': {'up': 108, 'dn': 103, 'lt': 106, 'rt': 105},
            'left':     {'up': 106, 'dn': 105, 'lt': 103, 'rt': 108}
          }

  # Rotations to pick from when no specific rotation is given
preferredRotations = rotations

  # Rotation to use when switched to tablet mode
tabletMode = "right"
  
  # Tells the program to stay open when in tablet mode and 
  # rotate using the orientation sensor
tabletAutoRotate = True
  
  # Rotation to use when switched to normal laptop mode
laptopMode = "normal"


## If a local xsetwacom is installed, it should probably take precedent (?)
if os.path.isfile('/usr/local/bin/xsetwacom'):
  xsetwacom = '/usr/local/bin/xsetwacom'
elif os.path.isfile('/usr/bin/xsetwacom'):
  xsetwacom = '/usr/bin/xsetwacom'
else:
  ## If it's not one of those two, just hope it's in the path somewhere.
  xsetwacom = 'xsetwacom'

xrandr = '/usr/bin/xrandr'



def main():
  setEnv()
  
    # list of wacom devices to be rotated
  devices = listDevices()
  
  if len(sys.argv) < 2:     # No rotation specified, just go to the next one in the preferred list
    cr = getCurrentRotation()
    if cr in preferredRotations:
      nextIndex = (preferredRotations.index(cr) + 1) % len(preferredRotations)
    else:
      nextIndex = 0
    next = preferredRotations[nextIndex]
  else:
    next = sys.argv[1]
    if not next in rotations:
      if next == "tablet":
        next = tabletMode
      elif next == "laptop":
        next = laptopMode
      else:
        sys.stderr.write("Rotation \"%s\" not allowed (pick from %s, tablet, laptop)\n" % (next, ', '.join(rotations)))
        sys.exit(-1)
  setRotation(next, devices)



def runCmd(cmd):
  f = os.popen(cmd)
  l = f.readlines()
  f.close()
  return l

def getCurrentRotation():
  #setEnv()
  try:
    rrv = randrVersion()
    if rrv < '1.2':
      l = [s for s in runCmd(xrandr) if re.match('Current rotation', s)]
      r = re.sub('Current rotation - ', '', l[0])
      return r.strip()
    elif rrv >= '1.2':
      l = runCmd(xrandr) #"%s | grep 'LVDS connected' | gawk '{print $4}' | sed -e 's/(//'" % xrandr)
      l = [x for x in l if re.search(r'(LVDS|default) connected', x)][0]
      l = l.split(' ')[3]
      l = re.sub(r'\(', '', l)
      
      return l.strip()
  except:
    sys.stderr.write("Can not determine current rotation, bailing out :(")
    sys.exit(-1)

def setRotation(o, devices):
  #setEnv()
  runCmd("%s --output LVDS --rotate %s" % (xrandr, o))
  wacomRots = {'normal': '0', 'left': '2', 'right': '1', 'inverted': '3'}
  for d in devices:
    runCmd("%s set %s Rotate %s" % (xsetwacom, d, wacomRots[o]))
  setKeymap(o)

def setEnv():
  if os.environ.has_key('DISPLAY'):
    return  # DISPLAY is already set, don't mess with it.
  
  if os.system('pidof kdm > /dev/null') == 0:
    kdmsts = '/var/lib/kdm/kdmsts'
    if os.access(kdmsts, os.R_OK):
      kdmdata = open(kdmsts).readlines()
      userline = [s for s in kdmdata if re.match(r':0=', s)][0]
      user = re.sub(r':0=', '', userline).strip()
      os.environ['DISPLAY'] = ':0.0'
      os.environ['XAUTHORITY'] = '/home/%s/.Xauthority' % user
  elif os.system('pidof gdm > /dev/null') == 0:
    os.environ['DISPLAY'] = ':0.0'
    os.environ['XAUTHORITY'] = '/var/lib/gdm/:0.Xauth'
  
def setKeymap(o):
  for sc in scanCodes.keys():
    os.system('sudo setkeycodes %x %d' % (scanCodes[sc], keyCodes[o][sc]))


def randrVersion():
  #setEnv()
  xrv = runCmd('%s -v' % xrandr)[0]
  xrv = re.sub(r'.*version ', '', xrv)
  return xrv.strip()

def listDevices():
  #setEnv()
  dev = runCmd("%s list dev | awk {'print $1'}" % xsetwacom)

  dev = map(lambda s: s.strip(), dev)
  return dev
   
main()

```

My wacom fdi file (/etc/hal/fdi/policy/10-wacom.fdi)
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
	<merge key="input.x11_options.Button2" type="string">3</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
	<merge key="input.x11_options.Button1" type="string">2</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="touch">
        <merge key="input.x11_options.BottomY" type="string">953</merge>
        <merge key="input.x11_options.BottomX" type="string">931</merge>
        <merge key="input.x11_options.TopY" type="string">80</merge>
        <merge key="input.x11_options.TopX" type="string">50</merge>
      </match>
    </match>
  </device>

</deviceinfo>

```

My tablet is a Lenovo X61t.

---

### Post by Favux on 2009-05-23
Hi sarah.fauzia,

New tablet?  Anyway rec had a X200t with the same identifier "PnP Device (WACf008 )" so the two tablets must share the same digitizer.  The xsetwacom command will work for touch too if you use the identifier for it which is "PnP Device (WACf008 ) touch".

You might want to consider rec's script.  In Jaunty Users (near the top) 3 and 3a apply to you:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Did you do that rotation script?  That has to be the most complicated I've seen.  Mine are considerably simpler:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

---

### Post by sarah.fauzia on 2009-05-23
No, I found the script online, actually at the Ubuntu forums ([link](http://ubuntuforums.org/showthread.php?t=604896)). I like how it manages the NaviDial so that the keys rotate appropriately, just like they would in Windows. It also manages automatic rotation if you're using the hdaps kernel module, but I personally don't care for automatic rotation (usually is more trouble than it's worth).

---

### Post by Favux on 2009-05-23
Hi sarah.fauzia,

Well I'm not knocking it.  Maybe the word I was looking for was intricate.

As far as automatic rotation goes, we've only just finally figured out the module, HP-WMI.

---

### Post by sarah.fauzia on 2009-05-23
Rec's script works perfectly. Thanks for recommending it! I'm using ArchLinux (I used to use Ubuntu--it introduced me to Linux, and I joined these forums the same day), and I only needed to make two changes for it to work. I'll post it at that thread as well to help other users:

1. Save the wacom-names script in /etc/rc.d
2. Edit your rc.conf and add wacom-names to the daemons line. Make sure that HAL is not set as a background process, lest wacom-names run before HAL.
It'll need to run every boot if you use a script like mine that makes it impossible to edit.

---

