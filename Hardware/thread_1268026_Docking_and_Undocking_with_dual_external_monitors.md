---
title: "Docking and Undocking with dual external monitors"
date: 2009-09-16
forum: Hardware
---

### Post by FiredIce on 2009-09-16
Hi,

I've got a Dell Latitude docked in a docking station, attached to the docking station are two external monitors.

I've used a mix of nvidia-settings and manual cranking to get the external displays set up as I want them. The manual cranking was to rotate one of the displays so that it's in portrait mode.

Is it possible to undock the laptop and have it switch back to the laptop screen. Then when the laptop is redocked have it remember the original configuration and use the external screens? I'm happy to accept that I may need to restart X; effectivly log out and back in again, but it'd be nice to not have to do that or copy different versions of /etc/X11/xorg.conf about.

Any ideas welcomed!

:-)

---

### Post by kai5263499 on 2009-10-07
Bump. 

I am interested in a seamless solution to this problem too. Currently I have to manually go in and reset my displays to the laptop's screen (and vice versa when I dock it in the morning).

---

### Post by Hypnoz on 2009-10-14
I also would like to bump the laptop docking issue.

1) Laptop lid closed, in suspend
2) Plug into docking station
3) Press power button with lid still closed
4) Display SHOULD come up on external display

Very frustrating to have to restart my desktop session and lose all my windows to connect to a docking station.

---

### Post by julrich on 2009-11-16
I'm also in need of some info on this. 

Right now, I can make it work with the docking station, but it seems I need to run the nvidia-settings every time to get my external monitors working.

Is there a way to make this seamless?

---

### Post by SmokeyMaverick on 2009-11-17
Bump.

I'd like to see what the community has on this as well.  Going to jump into Ubuntu with a new Dell laptop this coming month, and I really would like to do dual monitors.  If I really have to, I'd just use laptop monitor and one shared external monitor hooked up to the docking station.

Thanks all!

---

### Post by julrich on 2009-11-17
The best thing I've come up with so far is to modify the gdm config to test for the presence of my external monitors, and then apply the correct xorg.conf based on it's findings.  It will require an x restart with docking/undocking, but I can't dig up anything else.

---

### Post by jbondjr on 2009-12-26
Bump.

I just got a dell and was interested in running the same setup.  I am taking it that, as of now,  every time I want to dock/undock I have to log out and log back in?

Is this a problem for people running ubuntu inside Windows (possible option for me if this doesn't work natively)?

---

### Post by julrich on 2009-12-28
I got it pretty close using hal events (halevt) and disper / auto-disper.

The laptop needs to be awake, and you need to be logged in when changing dock state. There's got to be a way to trigger the script during other events (on boot, on wake, etc..) to make it seamless, but I'm satisfied for now.

Works good for me!

---

### Post by calimocho on 2010-02-01
I also have the same setup as the O.P. (including NVidia and dual external monitors, one I'd like in portrait.)  

I too would like to see the ability to dock and undock with as few hand-machinations as possible.

---

### Post by Manslen on 2010-08-03
> **julrich said:**
> I got it pretty close using hal events (halevt) and disper / auto-disper.

The laptop needs to be awake, and you need to be logged in when changing dock state. There's got to be a way to trigger the script during other events (on boot, on wake, etc..) to make it seamless, but I'm satisfied for now.

Works good for me!

Could you post your configuration?

---

### Post by julrich on 2010-08-03
Sorry, I had to go back to windows :(

---

### Post by SmokeyMaverick on 2010-08-03
I got it with auto-disper and cli.py (found it somewhere online).

I have a short cut to the command:  "./cli.py -e" which auto detects if a 2nd monitor is attached to the laptop and configures it accordingly.  Like others have said - this works for me.  I'll copy and paste the cli.py script below.

Good luck!
[INDENT]
#!/usr/bin/env python
###############################################################################
# cli.py - command-line front-end for disper
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#        
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)
# By using, editing and/or distributing this software you agree to
# the terms and conditions of this license.

import sys
import logging
import optparse

import switcher

# program name and version
progname = 'disper'
progver = '0.2.3'

def add_option(obj, *args, **kwargs):
    '''portable optarg add_option function that implements the append_const
    action for Python versions below 2.5; has an extra first argument as
    the object on which add_option should be called.'''
    if sys.hexversion < 0x020500f0 and 'action' in kwargs and \
            kwargs['action'] == 'append_const':
        # after: [http://permalink.gmane.org/gmane.comp.python.optik.user/284](http://permalink.gmane.org/gmane.comp.python.optik.user/284)
        def append_const_cb(const):
            def cb(opt, opt_str, value, parser):
                if not getattr(parser.values, opt.dest):
                    setattr(parser.values, opt.dest, list())
                getattr(parser.values, opt.dest).append(const)
            return cb
        kwargs['action'] = 'callback'
        kwargs['callback'] = append_const_cb(kwargs['const'])
        del kwargs['const']
    return obj.add_option(*args, **kwargs)

def main():
    '''main program entry point'''
    # Python 2.3 doesn't support arguments to basicConfig()
    try: logging.basicConfig(format='%(message)s')
    except: logging.basicConfig()
    logging.getLogger().setLevel(logging.WARNING)
    ### option defitions
    usage = "usage: %prog [options] (-l|-s|-c|-e|-p|-i)"
    version = ' '.join(map(str, [progname, progver]))
    parser = optparse.OptionParser(usage=usage, version=version)

    add_option(parser, '-v', '--verbose', action='store_const', dest='debug', const=logging.INFO,
        help='show what\'s happening')
    add_option(parser, '-q', '--quiet', action='store_const', dest='debug', const=logging.ERROR,
        help='be quiet and only show errors')
    add_option(parser, '-r', '--resolution', dest='resolution',  
        help='set resolution, e.g. "800x600", or "auto" to detect the highest common '+
             'resolution. For extend it is possible to enter a single resolution for '+
             'all displays, or a comma-separated list of resolutions (one for each '+
             'display), or "max" to use the maximum resolution for each device. Beware '+
             'that many displays advertise resolutions they can not fully show, so '+
             '"max" is not advised.')
    add_option(parser, '-d', '--displays', dest='displays',
        help='comma-separated list of displays to operate on, or "auto" to detect')
    add_option(parser, '-t', '--direction', dest='direction',
        choices=['left','right','top','bottom'],
        help='where to extend displays: "left", "right", "top", or "bottom"')
    add_option(parser, '', '--scaling', dest='scaling',
        choices=['default','native','scaled','centered','aspect-scaled'],
        help='flat-panel scaling mode: "default", "native", "scaled", "centered", or "aspect-scaled"')

    group = optparse.OptionGroup(parser, 'Actions',
        'Select exactly one of the following actions')
    add_option(group, '-l', '--list', action='append_const', const='list', dest='actions',
        help='list the attached displays')
    add_option(group, '-s', '--single', action='append_const', const='single', dest='actions',
        help='only enable the primary display')
    add_option(group, '-S', '--secondary', action='append_const', const='secondary', dest='actions',
        help='only enable the secondary display')
    add_option(group, '-c', '--clone', action='append_const', const='clone', dest='actions',
        help='clone displays')
    add_option(group, '-e', '--extend', action='append_const', const='extend', dest='actions',
        help='extend displays')
    add_option(group, '-p', '--export', action='append_const', const='export', dest='actions',
        help='export current settings to standard output')
    add_option(group, '-i', '--import', action='append_const', const='import', dest='actions',
        help='import current settings from standard input')
    parser.add_option_group(group)

    (options, args) = parser.parse_args()
    # need exactly one action
    if not options.actions: options.actions = []
    if len(options.actions) == 0:
        logging.info('no action specified')
        # show help if no action specified
        parser.print_help()
        sys.exit(0)
    elif len(options.actions) > 1:
        parser.error('conflicting actions, please specify exactly one action: '
                     +', '.join(options.actions))
        sys.exit(2)

    if 'import' in options.actions or 'export' in options.actions:
        if options.resolution:
            logging.warning('specified resolution ignored for %s'%options.actions[0])
        if options.displays:
            logging.warning('specified displays ignored for %s'%options.actions[0])

    # apply defaults here to be able to detect if they were set explicitly or not
    if not options.direction: options.direction = "right"
    if not options.resolution: options.resolution = "auto"
    if not options.displays: options.displays = "auto"
    if not options.scaling: options.scaling = "default"
    if not options.debug: options.debug = logging.WARNING
    logging.getLogger().setLevel(options.debug)

    ### autodetect and apply options
    sw = switcher.Switcher()

    # determine displays involved
    if 'single' in options.actions:
        if options.displays == 'auto':
            options.displays = sw.get_primary_display()
        elif options.displays != [sw.get_primary_display()]:
            logging.warning('cloning specified displays instead of selecting primary display only')
        options.actions = ['clone']
    elif 'secondary' in options.actions:
        primary = sw.get_primary_display()
        if options.displays == 'auto':
            try:
                options.displays = [x for x in sw.get_displays() if x != primary][0]
            except IndexError:
                logging.critical('No secondary display found')
        elif options.displays == [primary]:
            logging.warning('selecting the primary display for secondary display')
        options.actions = ['clone']
        
    if options.displays == 'auto':
        options.displays = sw.get_displays()
        logging.info('auto-detected displays: '+', '.join(options.displays))
    else:
        options.displays = map(lambda x: x.strip(), options.displays.split(','))
        logging.info('using specified displays: '+', '.join(options.displays))

    ### execute action
    if 'list' in options.actions:
        # list displays with resolutions
        for disp in options.displays:
            res = sw.get_resolutions_display(disp)
            res.sort()
            print 'display %s: %s'%(disp, sw.get_display_name(disp))
            print ' resolutions: '+str(res)

    elif 'clone' in options.actions:
        # determine resolution
        resolution = options.resolution
        if resolution == 'auto':
            res = sw.get_resolutions(options.displays).common()
            if len(res)==0:
                logging.critical('displays share no common resolution')
                sys.exit(1)
            resolution = sorted(res)[-1]
        else:
            resolution = switcher.Resolution(resolution)
        # and switch
        sw.switch_clone(options.displays, resolution)
        # and apply scaling options if requested
        sw.set_scaling(options.displays, options.scaling)

    elif 'extend' in options.actions:
        # TODO rework this to code reorganisation
        # determine resolutions
        resolution = options.resolution
        if resolution == 'max':     # max resolution for each
            # override auto-detection weights and get highest resolution
            ress = sw.get_resolutions(options.displays)
            for rl in ress.values():
                for r in rl: r.weight = 0
            ress = ress.select()
            logging.info('maximum resolutions for displays: '+str(ress))
        elif resolution == 'auto':  # use preferred resolution for each
            ress = sw.get_resolutions(options.displays).select()
            logging.info('preferred resolutions for displays: '+str(ress))
        else:                       # list of resolutions specified
            ress = switcher.ResolutionSelection(resolution, options.displays)
            if len(ress)==1:
                ress = ress * len(options.displays)
            elif len(ress) != len(options.displays):
                logging.critical('resolution: must specify either "auto", "max", a single value, or one for each display')
                sys.exit(2)
            logging.info('selected resolutions for displays: '+str(ress))
        # and switch
        sw.switch_extend(options.displays, options.direction, ress)
        # and apply scaling options if requested
        sw.set_scaling(options.displays, options.scaling)
        
    elif 'export' in options.actions:
        print sw.export_config()

    elif 'import' in options.actions:
        sw.import_config('\n'.join(sys.stdin))

    else:
        logging.critical('program error, unrecognised action: '+', '.join(options.actions))
        sys.exit(2)

if __name__ == "__main__":
    main()

# vim:ts=4:sw=4:expandtab:
[/INDENT]

---

### Post by danny11 on 2010-08-03
Generally, laptops can be docked and undocked hot, cold or standby, depending on the system capabilities. In a cold dock or undock, you completely shuts down the computer before docking/undocking. Whereas, in a hot dock or undock, the computer remains running when docked/undocked. An intermediate style used in some designs allows the computer to be docked/undocked while powered on, but requires that it be placed into a sleep mode prior to docking/undocking.


_______________________________________
For connecting to remote desktop of another computer (via internet or network) and controls.  Also connecting to VNCServer through Repeater or directly to VNCServer and a lot of other configuration options. For more details [VNCServer ](http://www.abtollc.com/VNCViewer.aspx /)

---

