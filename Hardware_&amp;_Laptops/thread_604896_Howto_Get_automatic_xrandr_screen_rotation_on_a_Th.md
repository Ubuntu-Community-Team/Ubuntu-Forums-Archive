---
title: "Howto: Get automatic xrandr screen rotation on a Thinkpad X61 tablet/Intel 965"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by tlawson on 2007-11-06
This is a short guide to getting automatic screen rotation working on a Thinkpad X61 tablet, in the hopes of saving others some time.  Most of the information is generic and could conceivably apply to other machines, and I'll try to indicate how to get that set up.

I'm going to assume that you mostly have your tablet set up, have the pen working, have hdparm -B 254 set, etc etc.

I owe a lot of this to others, particularly [http://luke.no-ip.org/x60tablet/]("http://luke.no-ip.org/x60tablet/") for the basic setup and the person who wrote [bug report 147783]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/147783"), which lists the DRI fix.


Step 1: Remove conflicts.

Edit the file /etc/X11/xorg.conf and add the following line to the "Device" section:

```
Option		"DRI"		"false"

```

This disables 3D acceleration.  If you have an Intel 965 graphics controller and don't set this option, your screen will probably not redraw properly after rotation.  Due to poor rotation support on most video cards, this bug is apparently not a priority at current, which is annoying if you want to use a tablet.

If you have the package xserver-xgl installed, uninstall it.

Now restart X using ctrl-alt-backspace.


Step 2: Add a rotation script.

First we'll install a script that does the screen rotation for us.  The following script is taken almost directly from [http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/) - the only alteration is that I changed to to always apply to the LVDS device.

Add the following lines to /etc/rc.local before the "exit 0" line:

```
setkeycodes 6f 108 
setkeycodes 71 103 
setkeycodes 6e 105 
setkeycodes 6d 106 

```

Create a file /usr/local/bin/rotate with the following content:

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

Then set permissions on this file to 755.

Run visudo and add the following line to the bottom:

```
%admin ALL=NOPASSWD: /usr/bin/setkeycodes
```

This allows the setkeycodes command to be run from within the script.

You should now be able to type "rotate tablet" and "rotate laptop" from a command prompt to turn the screen at will.  This script also adjust the arrow keypad on the side of the tablet so that the directions correspond to screen directions and sets the tablet pen to move correctly.


Step 3: Set up automatic rotation.

We're now going to set up some scripts and events to automatically handle swivelling of the screen.  Parts of this solution is not ideal, but I don't know a better one at this point because I don't know how to poll the hardware for the current state.

Create a directory /etc/autorotate and a file /etc/autorotate/lastrotation with just the single line

```
laptop
```

Change permissions on this file to 666.

Create a file /usr/local/bin/autorotate with the following content:

```
#!/bin/sh

/usr/local/bin/rotate `cat /etc/autorotate/lastrotation`
```

Change permissions on this file to 755.

Create a file /usr/local/bin/setrotation with the following content:

```
#!/bin/sh

echo $1 > /etc/autorotate/lastrotation
/usr/local/bin/autorotate
```

Change permissions on this file to 755.
Create a file /etc/acpi/events/swivel-up with the following content:

```
# called when tablet screen swivels up (into laptop mode)
event=ibm/hotkey HKEY 00000080 0000500a
action=/usr/local/bin/setrotation laptop
```

Create a file /etc/acpi/events/swivel-down with the following content:

```
# called when tablet screen swivels down (into tablet mode)
event=ibm/hotkey HKEY 00000080 00005009
action=/usr/local/bin/setrotation tablet
```

These are specific to the X61 (and X60, at least) tablet.  If you want to do it on another machine, try checking the end of the file /var/log/acpid after swivelling the tablet screen to try and find the appropriate keycodes.

Reboot your system.  Your screen should now automatically turn when you swivel the laptop into tablet mode and back.  If you mess around with the rotation, you should now automatically be able to return it to the correct setting by typing "autorotate".


Step 4: Get the login screen to start in the correct video mode.

One significant annoyance for me was that after logging out, the screen would revert to laptop mode.  Here is an (optional) bit of setup you can do to get a nice login screen in gdm; I don't know the corresponding thing to do in KDE or any other desktop managers.

Go to System > Administration > Login Window and click the "local" tab.  Set the style to "plain" or "plain with face browser".

Edit the file /etc/gdm/Init/Default and add the following lines at the bottom, just before "exit 0":

```
/usr/local/bin/autorotate
onboard&
```

This starts up the screen in the correct rotation with an onscreen keyboard (onboard; try xvkbd if you don't like that) so that you can login with a tablet pen.

If the default setting for onboard is in your way, you can do the following.  Edit the file /usr/share/onboard/sok.py and add the following around line 100 (I inserted it around line 101):

```
	    self.window.do_set_gravity(gtk.gdk.GRAVITY_SOUTH_EAST)
```

Python is sensitive to indenting, so make sure it's indented the same amount as the surrounding code.  Then edit the file /usr/share/onboard/KbdWindow.py and replace lines 21-25 with the following:

```
#		if x and y:
#			self.set_default_size(x,y)
#		else:
		self.set_default_size(600,180)
		#self.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)
```

You can change 600 and 180 to whatever dimensions please you.  Again, indentation is important.


Final thoughts.

Obviously it would be much better to poll the hardware for the current tablet state rather than this hackwork of writing a script to store the last state.  I have no idea how to do this.

The login window doesn't like it if you rotate the tablet; it doesn't redraw to different dimensions.  I don't know if this is solvable for me.

---

### Post by haplo_09 on 2007-11-06
Did you get artifacts, after you rotate laptop into tablet mode? 
Will intel i810 driver work with i965 card?

---

### Post by tlawson on 2007-11-06
I used to get artifacts; the Option "DRI" "false" in xorg.conf removed those for me.

---

### Post by haplo_09 on 2007-11-06
> **tlawson said:**
> I used to get artifacts; the Option "DRI" "false" in xorg.conf removed those for me.

thanks

Also,  I have fujitsu t4220, do you have any ideas how can identify response from tablet sensor after you rotate screen into tablet mode.?

---

### Post by tlawson on 2007-11-06
type tail /var/log/acpid
then try swivelling the screen to a new position and then type it again
on my system, I'll see a new entry after I do this that says 

received event ibm/hotkey HKEY 00000080 00005009

(for swivelling the screen up)  hopefully on your system you'll see a similar message but probably with a different number.

---

### Post by haplo_09 on 2007-11-06
Nope, no response. Is there any other way to identify signal from sensor

---

### Post by tlawson on 2007-11-07
that I don't know.  I don't know enough about hardware to begin to know where to look.  anyone know a starting point?

---

### Post by corte123 on 2007-11-24
hi i have an thinkpad x60 tablet ,i went through your guide with no problems , but i cant get the pen to move right any help on fixing the pen , left an right movements are up an down on my thinkpad :(

---

### Post by corte123 on 2007-11-24
forget that list post ,i didnt have wacom tools installed :)

---

### Post by HanaD on 2008-03-17
Thank you for this helpful code for rotation,
but i am facing one problem,
after doing all what was written on this forum,

i got screen rotation working,
but in tablet mode, the pen behaves erratic, for eg, if i try to point th ecursor to right hand corner down, it points on the left and so on....

can you please help me figure whats wrong.

I am using X61tablet.

Regads,
Hana

---

### Post by pirata_loco on 2008-04-07
Hi,
i have the x60t and i'm trying to get work the rotation key, but it doesn't.
Does someone get worked it?
saludo

---

### Post by tlawson on 2008-05-09
> **HanaD said:**
> Thank you for this helpful code for rotation,
but i am facing one problem,
after doing all what was written on this forum,

i got screen rotation working,
but in tablet mode, the pen behaves erratic, for eg, if i try to point th ecursor to right hand corner down, it points on the left and so on....


It sounds like you don't have wacom-tools installed, like the previous poster mentioned.  Try:

```
sudo apt-get install wacom-tools
```

and try again to see if that helps?

---

### Post by pibach on 2008-06-04
also rotate the digitizer:
 xsetwacom set stylus Rotate ccw

---

### Post by krueschan on 2008-07-15
> **pirata_loco said:**
> i have the x60t and i'm trying to get work the rotation key, but it doesn't.
Does someone get worked it?
If you use metacity (which you do by default in Ubuntu) you can map any command to any key combination. Enter (as 'yourself' not as root (or via sudo) as the root user has her own set of settings)

```
gconf-editor /apps/metacity/keybinding_commands
```
and enter the command 'rotate' (which has been created if you followed the very helpful steps described by tlawson to at least the first part of Step 3 (creating the file /etc/autorotate/lastrotation) as value for any of the empty 'command_xx' keys.

Change (on the left pane) to 'global_keybindings' and enter the keycode for the rotate key as value for the key 'run_command_xx' where xx is the same number as in the previous step. 


The keycode is 0xdb for my X61 and [http://www.thinkwiki.org/wiki/Tablet_Hardware_Buttons](http://www.thinkwiki.org/wiki/Tablet_Hardware_Buttons) has a list for other models.

After closing gconf-editor the rotation should work instantly without the need to restart.

It worked for me that way. Good luck.

Oh. By the way, I am talking about Ubuntu 8.04; I don't know where to map keys in other Ubuntu versions...

---
P.S. if it doesn't work. first find out if the 'rotate' command does what it is supposed to be by entering it without any arguments in a terminal window and checking if it rotates the screen as you expect the rotate button to (after calling the command 4 times you should have your screen in 'laptop mode' again. If it does, something went wrong with you keybinding. Try to bind the rotate command to some other key combination first by entering, for example, '<Control>r' in the 'run_command_xx' key in 'global_keybindings' and check if <Control>r calls the program.

---

