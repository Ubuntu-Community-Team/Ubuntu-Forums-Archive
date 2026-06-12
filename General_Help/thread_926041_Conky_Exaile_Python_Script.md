---
title: "Conky Exaile Python Script"
date: 2008-09-21
forum: General Help
---

### Post by kaivalagi on 2008-09-21
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE=3][COLOR=Blue]Intro[/COLOR][/SIZE]_**

This is a simple script to display what is current playing in Exaile. The script talks to Exaile using dbus, the same way the Exaile command line output options work but allowing more options and templates...

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conky<scriptname>/

**_[SIZE=3][COLOR=Blue]Basic Install[/COLOR][/SIZE]_**

**[COLOR=Blue]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the script: 

```
sudo apt-get update && sudo apt-get install conkyexaile

```

**[COLOR=Blue]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyExaile script to point to the correct location where conkyExaile.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

You can get the current help options at any time by running (change the path as necessary):

```

conkyExaile -h

```or

```

conkyExaile --help

``````
Usage: conkyExaile [options]
Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        define a template file to generate output in one call.
                        A displayable item in the file is in the form
                        [--datatype=TI]. The following are possible options
                        within each item: --datatype,--ratingchar. Note that
                        the short forms of the options are not currently
                        supported! None of these options are applicable at
                        command line when using templates.
  -d DATATYPE, --datatype=DATATYPE
                        [default: TI] The data type options are: ST (status),
                        CA (coverart), TI (title), AL (album), AR (artist), GE
                        (genre), YR (year), TN (track number), FN (file name),
                        BR (bitrate), LE (length), PP (current position in
                        percent), PT (current position in time), VO (volume),
                        RT (rating). Not applicable at command line when using
                        templates.
  -r CHAR, --ratingchar=CHAR
                        [default: *] The output character for the ratings
                        scale. Command line option overridden if used in
                        templates.
  -s TEXT, --statustext=TEXT
                        [default: Playing,Paused,Stopped] The text must be
                        comma delimited in the form 'A,B,C'. Command line
                        option overridden if used in templates.
  -n, --nounknownoutput
                        Turn off unknown output such as "Unknown" for title
                        and "0:00" for length. Command line option overridden
                        if used in templates.
  -S, --secondsoutput   Force all position and length output to be in seconds
                        only.
  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

**_[SIZE=3][COLOR=Blue]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkyexaile"]https://code.launchpad.net/~conky-companions/+junk/conkyexaile
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by Steve Fisher on 2008-09-21
This is nice. I have a problem when there is nothing playing. It will just display "Unknown", which isn't really very nice. Is there a way of making it display nothing at all if Exaile is running?

---

### Post by Steve Fisher on 2008-09-21
Also I get this when I close Exaile
```
File "/usr/share/conkyexaile/conkyExaile.py", line 270, in <module>
    conkyexaile.outputData()
  File "/usr/share/conkyexaile/conkyExaile.py", line 241, in outputData
    print output.encode("utf-8")
AttributeError: 'NoneType' object has no attribute 'encode'

```

---

### Post by kaivalagi on 2008-09-21
Okay, I'm going to start updating the script.

I like having the unknown output, so I think I'll add an option to switch output on or off when no data is available

I've also found out why the script throws a wobbly when exaile isn't running

Give me a day or so... edit: hour or so..

---

### Post by kaivalagi on 2008-09-21
[COLOR="SeaGreen"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

Added --nounknownoutput option to turn off "Unknown" and "0:00" as default output for the unknown. This works in both normal and template modes :)

The script will handle no Exaile running and stopped tracks much nicer too.

The files in the first post have been updated, and the new package is available via apt.

---

### Post by kaivalagi on 2008-09-23
[COLOR="DarkRed"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I've updated the script to only call the dbus data retirevial once and reuse the data through template output. Also updated slightly to cope better with unknown output.

The files in the first post have been updated, and the new package is available via apt.

Note: this is now an equivalent script for Rhythmbox, see my sig for the link :)

---

### Post by loomsen on 2008-09-24
Thank you very much, Sir :)

---

### Post by kaivalagi on 2008-09-25
[COLOR="Blue"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I've updated the script as follows:

[LIST]
[*]Updated to handle when no music is playing, no unnecessary dbus calls will be made
[*]Updated rating output generation to use ljust string function
[/LIST]

The first post attachments have been updated, and the apt package is available

---

### Post by billgoldberg on 2008-09-25
Why not just use this in .conkyrc itself?

```
${execi 10 exaile --get-title} - ${execi 10 exaile --get-artist}
```

---

### Post by loomsen on 2008-09-25
Because this will start exaile even if its not running? Just to state obvious...

---

### Post by kaivalagi on 2008-09-26
> **billgoldberg said:**
> Why not just use this in .conkyrc itself?

```
${execi 10 exaile --get-title} - ${execi 10 exaile --get-artist}
```

Of the top of my head, my script can do the following that the Exaile command line can't:

[LIST]
[*]run without starting exaile
[*]provide current position in track from percent and length
[*]allow for rating output as "***" or "~~~" etc
[*]allow one exec call to display all details you want from a template
[*]give the ability to display things as unknown when they are unknown
[*]provide a framework to add more functionality to conky to suit conky at a later stage :)
[/LIST]

I get your point, but this was an easy task and it does have a couple of benefits...

I have also used the same methodology for Rhythmbox where you could argue the same thing can be done with rhythmbox-client, but again the script can provide percent and template functions for example, as well as (in the case of rhythmbox) breakdown the details of a song into title/album/artist etc etc

---

### Post by jryprt on 2008-09-26
Will this work on 7.10 gutsy gibbson?

---

### Post by kaivalagi on 2008-09-26
> **jryprt said:**
> Will this work on 7.10 gutsy gibbson?

Should do, the only dependency is on python and exaile...I think exaile would have had dbus functions right from the start.

Give it a try, if it doesn't install then no loss, if it does install and doesn't work then uninstall it. 

I know from when I was running Gutsy before now, I successfully used hardy based 3rd party repo's okay...not sure on my one though as no one has ever tried as far as I am aware...

Let me know how you get on!

---

### Post by jryprt on 2008-09-26
> **kaivalagi said:**
> Should do, the only dependency is on python and exaile...I think exaile would have had dbus functions right from the start.

Give it a try, if it doesn't install then no loss, if it does install and doesn't work then uninstall it. 

I know from when I was running Gutsy before now, I successfully used hardy based 3rd party repo's okay...not sure on my one though as no one has ever tried as far as I am aware...

Let me know how you get on!

I get this at the end in the terminal

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  conkyexaile: Depends: python-central (>= 0.6.7) but 0.5.15ubuntu2 is to be installed
E: Broken packages

```

---

### Post by kaivalagi on 2008-09-27
> **jryprt said:**
> I get this at the end in the terminal

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  conkyexaile: Depends: python-central (>= 0.6.7) but 0.5.15ubuntu2 is to be installed
E: Broken packages

```

That was unexpected :(

Python central is used for the install process, in this case you'll have no choice but to install the script manually using the tarball from the first post.

If you extract the tarball to a location of you choice in your home folder (e.g. /home/user/scripts/), you can then use it in conky with a line like this:

```
${exec python /home/user/scripts/conkyExaile.py ...options...}
```

Any particular reason that you haven't upgraded to 8.10?

---

### Post by kaivalagi on 2008-10-04
[COLOR="DarkGreen"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

The script has been updated and is available in the first post and via apt, the changes are as follows:

[LIST]
[*]Updated script to now use "[" and "]" as template brackets rather than "{" and "}" so that the execp/execpi conky command can be used, this enables the use of $font, $color options in the template which conky will then make adjustments for in the output!
[*]Updated example files to use new template functionality with execpi in conky
[*]Updated README for usage changes
[/LIST]

Note the change to template requirements...

Have fun

---

### Post by riizu on 2008-10-04
Hey I tried it, but I get this error.

```
ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 643, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/var/lib/python-support/python2.5/dbus/service.py", line 244, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: get_volume is not a valid method of interface org.exaile.DBusInterface

```

I have this line in my .conkyrc

```
${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}
```

PS I have the newest version of Ubuntu.

---

### Post by kaivalagi on 2008-10-04
> **riizu said:**
> Hey I tried it, but I get this error.

```
ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 643, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/var/lib/python-support/python2.5/dbus/service.py", line 244, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: get_volume is not a valid method of interface org.exaile.DBusInterface

```

I have this line in my .conkyrc

```
${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}
```

PS I have the newest version of Ubuntu.

Do you get any useful output from the script?

All the errors look alien to me, I haven't seen any of them before....

As much info as possible please! What version of Exaile etc...

---

### Post by kaivalagi on 2008-11-02
[COLOR="Green"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've published a new package labelled for Intrepid, starting at version 2.0.

The first post has been updated, and the package is available via apt.

To use the new intrepid "labelled" packages via apt, changes to your sources.list are needed. This:

```
deb http://ppa.launchpad.net/m-buck/ubuntu hardy main
deb-src http://ppa.launchpad.net/m-buck/ubuntu hardy main
```

Needs to become this:

```
deb http://ppa.launchpad.net/m-buck/ubuntu intrepid main
deb-src http://ppa.launchpad.net/m-buck/ubuntu intrepid main
```

Currently either hardy or intrepid packages will work with either version of ubuntu.

However going forwards there are no guarantees that packages will continue to work with hardy, development may introduce intrepid specific dependencies. All future revisions will only be available for intrepid.

---

### Post by kaivalagi on 2008-11-10
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Added --errorlog and --infolog options to log data to a file, removed --enableerrors option as unnecessary
[*]Refactored and tidied up
[*]Updated README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by ddnev45 on 2008-11-14
> **riizu said:**
> Hey I tried it, but I get this error.

```
ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 643, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/var/lib/python-support/python2.5/dbus/service.py", line 244, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: get_volume is not a valid method of interface org.exaile.DBusInterface

```

I have this line in my .conkyrc

```
${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}
```

PS I have the newest version of Ubuntu.

I get a similar error:

```
[AMD-64] ~/.conkyscripts $ conky -c ConkyExaile
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (1a6) is root window
Conky: window type - override
Conky: drawing to created window (1a00001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 103, in getOutputText
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-92gFCnxAkD: Connection refused
ERROR: Unknown error when calling getOutputText:org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-92gFCnxAkD: Connection refused
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 103, in getOutputText
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-5PhYayzRrx: Connection refused

```

If I run the conkyexaile script as root, it will start, but not detect the CD.

Exaile 0.2.14
Ubuntu 8.04.
Openbox.

The script runs just fine on my laptop.

---

### Post by kaivalagi on 2008-11-14
> **ddnev45 said:**
> I get a similar error:

```
[AMD-64] ~/.conkyscripts $ conky -c ConkyExaile
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (1a6) is root window
Conky: window type - override
Conky: drawing to created window (1a00001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 103, in getOutputText
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-92gFCnxAkD: Connection refused
ERROR: Unknown error when calling getOutputText:org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-92gFCnxAkD: Connection refused
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 103, in getOutputText
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-5PhYayzRrx: Connection refused

```

If I run the conkyexaile script as root, it will start, but not detect the CD.

Exaile 0.2.14
Ubuntu 8.04.
Openbox.

The script runs just fine on my laptop.

Have you tried running a newer exaile version? Update from the exaile dev repo maybe?

Add this to the bottom of /etc/apt/sources.list (swap intrepid for hardy if that's the case):

```
deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main
```

Run:

```
sudo apt-get update && sudo apt-get upgrade

```

We know the script works, it looks to me like something related to dbus, either exaile specific or system specific.

Let me know how you get on with the above

---

### Post by ddnev45 on 2008-11-14
Tried the upgrade route, but I see on the exaile site that I can use the development releases. Will try that after work tonight if I have time.

Right now, I'm leaning toward something system specific. The desktop (non-working) is a self-built, AMD 64-bit chip; the laptop is a Compaq AMD 32-bit chip. That would be the main difference.

---

### Post by ddnev45 on 2008-11-14
> **ddnev45 said:**
> Tried the upgrade route, but I see on the exaile site that I can use the development releases. Will try that after work tonight if I have time.

Right now, I'm leaning toward something system specific. The desktop (non-working) is a self-built, AMD 64-bit chip; the laptop is a Compaq AMD 32-bit chip. That would be the main difference.

Upgrade to the development release of exaile failed -- exaile wouldn't play a CD; but the conkyexaile script was working in Gnome.

However, after going back to a stable/working version of exaile, it would appear to be a non-gnome issue with my system. Fvwm yields the same results as Openbox.

---

### Post by kaivalagi on 2008-11-15
I don't know what can be done here

Try re-installing dbus and python-dbus, just in case...

This might take some effort, but could you run a live cd on the PC, once booted up, install conky from the repo, and the script from the deb file, and try it out.....I

---

### Post by akahige on 2008-11-17
Thanks for developing such a cool script!

One of the things that I like the most is how if you're using the template file, you don't have to restart Conky to test experimental layouts.

Having worked out a template that I like, I'm wondering if you're planning on adding variables to display file name and track number...?

Cheers!

---

### Post by kaivalagi on 2008-11-17
> **akahige said:**
> Thanks for developing such a cool script!

One of the things that I like the most is how if you're using the template file, you don't have to restart Conky to test experimental layouts.

Having worked out a template that I like, I'm wondering if you're planning on adding variables to display file name and track number...?

Cheers!

Can do

Can you think of any other details you'll want, I can then introduce them all in one go

---

### Post by akahige on 2008-11-17
> **kaivalagi said:**
> Can do

Can you think of any other details you'll want, I can then introduce them all in one go

Awesome! Thanks!

I gave that a bit of a think and came up with the following...

Support for the rest of the major tag elements would be nice.
• file name (w. an option to display the full path)
• track number
• genre
• year

Is there a way to display info about the running playlist? Current position, total number of tracks, and playlist name could be useful.

A player status message would be very nice. It could indicate playing, paused, or stopped -- and if there was a way for the user to set custom labels for each status...

I'm not sure how you'd implement this, but it would be highly cool -- for people using the external template -- if Exaile is closed, the template output is suppressed. That will allow the Conky layout to collapse, instead of displaying a bunch of "unknown" tags. (Or at least it will appear collapsed if the conkyExaile template is the very last thing Conky displays.)

Would it be possible to suppress/collapse blank elements? It would certainly be an elegant way of getting rid of "unknown" messages for tags that aren't present.


According to [this post](http://ubuntuforums.org/showthread.php?p=6077023), Conky now supports scrolling text marquees, so displaying long or complicated strings of info (e.g. a file path and title) should be fairly elegant.

I filed a backport request to get conky 1.6.1 (ships with Intrepid) moved into the Hardy repo.

Any thoughts...?

---

### Post by kaivalagi on 2008-11-17
Lot's of thoughts :)

> **akahige said:**
> Support for the rest of the major tag elements would be nice.
&#8226; file name (w. an option to display the full path)
&#8226; track number
&#8226; genre
&#8226; year


That shouldn't be a problem, I'll do it for both exaile and rhythmbox scripts

[COLOR="Blue"]Edit: All possible with the exception of the full path to the file...
[/COLOR]
> **akahige said:**
> 
Is there a way to display info about the running playlist? Current position, total number of tracks, and playlist name could be useful.


Not sure, dont think so, as the playlist is not something exaile exposes via dbus...I think. Unlikely to happen this one.

[COLOR="Blue"]Edit: Not possible[/COLOR]

> **akahige said:**
> 
A player status message would be very nice. It could indicate playing, paused, or stopped -- and if there was a way for the user to set custom labels for each status...


Again, not sure whether the dbus interface provides for this, I'll take a look. Limited documentation on the whole thing though...it would be a nice feature though, especially if you could use a font for play, pause and stop symbols :)

[COLOR="Blue"]Edit: status is retrievable, I'll add a statustext option too...set it like --statustext=Playing,Paused,Stopped using a comma delimited list[/COLOR]

> **akahige said:**
> 
I'm not sure how you'd implement this, but it would be highly cool -- for people using the external template -- if Exaile is closed, the template output is suppressed. That will allow the Conky layout to collapse, instead of displaying a bunch of "unknown" tags. (Or at least it will appear collapsed if the conkyExaile template is the very last thing Conky displays.)


you should be able to handle this in conky, using:

```
${if_running exaile}

...conky execs...

${endif}
```

[COLOR="Blue"]Edit: works for me with rhythmbox...[/COLOR]

> **akahige said:**
> 
Would it be possible to suppress/collapse blank elements? It would certainly be an elegant way of getting rid of "unknown" messages for tags that aren't present.

That it not possible to cover all scenarios, as any surrounding text put into the template would also need removing, and I have no way of knowing what that is...

[COLOR="Blue"]Edit: Not doing it[/COLOR]

> **akahige said:**
> 
According to [this post](http://ubuntuforums.org/showthread.php?p=6077023), Conky now supports scrolling text marquees, so displaying long or complicated strings of info (e.g. a file path and title) should be fairly elegant.

I haven't tried the scrolling feature, but I would suspect you can put the necessary commands into the template, let us know how you get on.

> **akahige said:**
> 
I filed a backport request to get conky 1.6.1 (ships with Intrepid) moved into the Hardy repo.


The backport would be nice, but compiling conky isn't hard...take a look here:

[http://ubuntuforums.org/showthread.php?t=706736](http://ubuntuforums.org/showthread.php?t=706736)

It's for an older version and for enabling specific functionality but you'll get the jist from it...just don't provide options to the /configure call.

You won't see any of this development happen for a while, I am busy with another project right now. When I get a chance I'll have a stab at it all though.

Chimo

---

### Post by akahige on 2008-11-17
> **kaivalagi said:**
> Lot's of thoughts :)
Well, I tried to think of things that other people might find useful.


[QUOTE=kaivalagi]Again, not sure whether the dbus interface provides for this, I'll take a look. Limited documentation on the whole thing though...it would be a nice feature though, especially if you could use a font for play, pause and stop symbols :)[/quote]
That would be pretty sweet!


[QUOTE=kaivalagi]you should be able to handle this in conky, using:

```
$if_running exaile

...conky execs...

$endif
```[/quote]

I must be missing something about how if_running works.

In trying this:

```
${if_running exaile}
${execp conkyExaile --template=/home/michael/.conkyExaile.template}
${endif}
```
I get nothing at all -- the template doesn't load. From what I've read, it should work, but...

And even if it was working, because it's called from conkyrc, would it dynamically come and go if you were opening and closing Exaile? Or would you have to restart conky?


[QUOTE=kaivalagi][quote=akahige]Would it be possible to suppress/collapse blank elements? It would certainly be an elegant way of getting rid of "unknown" messages for tags that aren't present.[/quote]That it not possible to cover all scenarios, as any surrounding text put into the template would also need removing, and I have no way of knowing what that is...[/quote]
That's a good point. But if there wasn't any surrounding text, it could work, right?


[QUOTE=kaivalagi]I haven't tried the scrolling feature, but I would suspect you can put the necessary commands into the template, let us know how you get on.[/quote]
I'll do that. The obvious test would be a file name with path (on a network share), but since conkyExaile doesn't support that yet (and I'm still running conky 1.5.1), I'll have to hold off for awhile.


[QUOTE=kaivalagi]You won't see any of this development happen for a while, I am busy with another project right now. When I get a chance I'll have a stab at it all though.

Chimo[/QUOTE]

Thanks for considering my suggestions. I can't wait to see what you come up with.

---

### Post by kaivalagi on 2008-11-17
> **akahige said:**
> 
Thanks for considering my suggestions. I can't wait to see what you come up with.

No worries

I've edited the above post from myself with details after doing a little digging...

---

### Post by akahige on 2008-11-17
You don't happen to have any ideas about the if_running issue do you?

If I pull of the surrounding IF arguments, the template loads just fine, but if they're there (as in the above post), the execp argument is ignored.

---

### Post by kaivalagi on 2008-11-17
> **akahige said:**
> You don't happen to have any ideas about the if_running issue do you?

If I pull of the surrounding IF arguments, the template loads just fine, but if they're there (as in the above post), the execp argument is ignored.

if you are running exaile and you do this, do you find it listed?

```
ps -C exaile
```

I get:

```
  PID TTY          TIME CMD
12536 ?        00:00:09 exaile

```

You could try asking on the main conkyrc thread...[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by akahige on 2008-11-17
> **kaivalagi said:**
> if you are running exaile and you do this, do you find it listed?

```
ps -C exaile
```
Yep. That's what makes it so odd.


[QUOTE=kaivalagi]You could try asking on the main conkyrc thread...[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)[/QUOTE]
I'll do that.

---

### Post by kaivalagi on 2008-11-19
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Now loading the template file in unicode mode to allow for the extended character set
[*]Added datatypes: ST (status), GE (genre), YR (year), TN (track number), FN (file name)
[*]Added --statustext option to allow overridding of the standard status text
[*]Updated README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by akahige on 2008-11-20
TOTALLY awesome!

Thanks for all your hard work.

---

### Post by kaivalagi on 2008-11-20
> **akahige said:**
> TOTALLY awesome!

Thanks for all your hard work.

My pleasure, no more changes for some time now...

---

### Post by akahige on 2008-11-20
Having upgraded to the new version of conkyExaile, I've watched conky start consuming an astronomical amount of CPU resources. If conkyExaile isn't running, everything calms down (so my compiled-from-source conky 1.6.1 upgrade doesn't seem to be at fault).

This is the template file I'm using, in case there's anything in there that might help troubleshoot this.

```
${voffset 4}${color4}${font Verdana:size=12}Now ${exec conkyExaile --statustext=Playing,Paused,Stopped --d=ST}:$font ${alignr}${color7}${exec conkyExaile --datatype=PT} ${color8}of${color7} ${exec conkyExaile --datatype=LE}$font
${offset 20}${voffset -2}${color8}${font Verdana:size=10}Title${goto 76}: ${goto 92}${color2}${font Verdana:size=12}${exec conkyExaile -n --d=TI}$font
${offset 20}${voffset -3}${color8}${font Verdana:size=10}Artist${goto 76}: ${goto 92}${color2}${font Verdana:size=12}${exec conkyExaile -n --d=AR}$font
${offset 20}${voffset -3}${color8}${font Verdana:size=10}Album${goto 76}: ${goto 92}${color2}${font Verdana:size=12}${exec conkyExaile -n --d=AL}$font
${offset 82}${color2}${execibar 1 conkyExaile -n --d=PP}
${offset 82}${voffset -6}${color8}${font Consolas-11}${scroll 42 Track No.: ${exec conkyExaile -n --datatype=TN} ... ${exec conkyExaile -n --d=FN}}$font

```

I tried cutting elements out of the template to see if anything in specific might be causing this, but that didn't seem to help.

Have you gotten reports of anything similar...? Got any idea what might be causing this?

---

### Post by kaivalagi on 2008-11-21
> **akahige said:**
> Got any idea what might be causing this?

You are running several instances of the script, there is no need to do that.

Take a look at the example files that come with the install, you'll find them here "/usr/share/conkyexaile/example"

In the conkyrc there is this **execp** call using a template:
```

${color1}${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}

```

And the template has all the conky options you might want for layout, as the execp/execpi allows for this:
```
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
```

Doing things this way means only one instance of the scriptis required  for exaile output

Hope that helps

---

### Post by akahige on 2008-11-21
> **kaivalagi said:**
> You are running several instances of the script, there is no need to do that.

...

Doing things this way means only one instance of the script is required  for exaile output

Hope that helps

Helped quite a bit, actually. I'd skimmed the updated readme, but didn't quite get that this was a new and necessary way of doing things, and not just an improved and compact one.

The one thing that I can't seem to grok -- and this wasn't real clear in the previous version, even though I got it to work -- is the way in which the custom status text is called. Where does it go?

I'm using this (or trying to):
```
Now [--datatype=ST --statustext=Playing,Paused,Stopped]:
```
...but it's not being read. Also tried it in front of the datatype (where it was in the initial incarnation that worked with the previous version), but it didn't work there, either.

---

### Post by kaivalagi on 2008-11-21
> **akahige said:**
> Helped quite a bit, actually. I'd skimmed the updated readme, but didn't quite get that this was a new and necessary way of doing things, and not just an improved and compact one.

The one thing that I can't seem to grok -- and this wasn't real clear in the previous version, even though I got it to work -- is the way in which the custom status text is called. Where does it go?

I'm using this (or trying to):
```
Now [--datatype=ST --statustext=Playing,Paused,Stopped]:
```
...but it's not being read. Also tried it in front of the datatype (where it was in the initial incarnation that worked with the previous version), but it didn't work there, either.

If you're not concerned about CPU usage then running what you had before is fine, however using a template means everything will gather via a single dbus call and get output, so CPU usage should go down.

I'll take a look when I get home, maybe I've missed the --statustext setting out of the template functionality, so it's not getting picked up?

---

### Post by akahige on 2008-11-21
> **kaivalagi said:**
> If you're not concerned about CPU usage then running what you had before is fine, however using a template means everything will gather via a single dbus call and get output, so CPU usage should go down.
I'm not on the world's fastest system, so obviously, I'd like things as optimal as they can be -- or at least not horribly wasteful. :)

I didn't know about the template being a single dbus call. Now that you say it, it makes perfect sense. Of course, I also missed the part in the readme where you said that the short variable names aren't supported yet.


> **kaivalagi said:**
> I'll take a look when I get home, maybe I've missed the --statustext setting out of the template functionality, so it's not getting picked up?
Well... If you can't see a problem with the data format that I'm using, then that should help eliminate my implementation as the part of the problem.

Looking forward to seeing what you discover...

---

### Post by kaivalagi on 2008-11-21
> **akahige said:**
> I'm not on the world's fastest system, so obviously, I'd like things as optimal as they can be -- or at least not horribly wasteful. :)

I didn't know about the template being a single dbus call. Now that you say it, it makes perfect sense. Of course, I also missed the part in the readme where you said that the short variable names aren't supported yet.



Well... If you can't see a problem with the data format that I'm using, then that should help eliminate my implementation as the part of the problem.

Looking forward to seeing what you discover...

I have updated the script (locally) to accept the statustext from command line options or from the template now...

Thinking about it though, **there is no reason why you shouldn't just set the statustext option up in the main exec call instead**....it's not like you'll want 2 statuses in the same output with different text is it? At least not yet :)

On this basis I am not going to go through the hassle of releasing the changes just yet, I'll wait until there are enough of them to warrant it....or when my other project is finished first ;)

---

### Post by akahige on 2008-11-21
> **kaivalagi said:**
> I have updated the script (locally) to accept the statustext from command line options or from the template now...

Thinking about it though, **there is no reason why you shouldn't just set the statustext option up in the main exec call instead**....
You know... I almost tried that, but I was running short on time, and I figured that if it was an option, you'd have mentioned it.  Sigh...  :)


> **kaivalagi said:**
> it's not like you'll want 2 statuses in the same output with different text is it? At least not yet :)
Ooh... multiple statuses... that could be fun... Although, I'll have to devote some thought to what the actual benefit would be. Sounds like you have something spiffy and evil in mind...


> **kaivalagi said:**
> On this basis I am not going to go through the hassle of releasing the changes just yet, I'll wait until there are enough of them to warrant it....or when my other project is finished first ;)
That sounds totally reasonable. Except for the mention of the mysterious "other project". That's just cruel. At this rate, you should just call the phantom python monitor "Area 51". Whatever it is... I'm looking forward to seeing it in action.

---

### Post by ddnev45 on 2008-11-23
> **kaivalagi said:**
> I don't know what can be done here

Try re-installing dbus and python-dbus, just in case...

This might take some effort, but could you run a live cd on the PC, once booted up, install conky from the repo, and the script from the deb file, and try it out.....I

Had a partial system crash and did a clean install of xubuntu 8.10; exaile and forecast scripts working just fine now.

Thanks for putting in all the time with these scripts.

---

### Post by kaivalagi on 2008-11-23
> **ddnev45 said:**
> Had a partial system crash and did a clean install of xubuntu 8.10; exaile and forecast scripts working just fine now.

Thanks for putting in all the time with these scripts.

My pleasure...

It's an addiction of sorts, much like messing with conky settings :)

---

### Post by x0x on 2008-11-28
Thanks for this great script :D

-------------------------------------


i solved the problem for $if_running..


check what is your "ps aux | grep exaile" looks like

if your ps reply like this.. you will have to rename the process name
```
c0re     30372  9.5  5.3 158036 55312 ?        Sl   02:41   0:51 python /usr/lib/exaile/exaile.py
```


here is the 13 steps HowTO:

step 1. download the attachment file.
step 2. save it
step 3. extract it; tar xzf PyInline-0.03.tar.gz
step 4. cd PyInline-0.03
step 5. chmod +x setup.py
step 6. sudo ./setup.py install
step 7. sudo gedit /usr/lib/exaile/exaile.py
step 8. find import sys
step 9. add after
```
import dl
import PyInline
import time
libc = dl.open('/lib/libc.so.6')
if libc != 0 : libc.call('prctl', 15, 'exaile\0', 0, 0, 0)
else : print ('prctl not called')

m = PyInline.build(code=r"""
    #include <Python.h>
    #include <stdio.h>
    #include <string.h>

    void set_argv(char *str){
        int argc;
        char **argv;
        Py_GetArgcArgv(&argc, &argv);
        strncpy(argv[0], str , strlen(str));
        memset(&argv[0][strlen(str)], '\0', strlen(&argv[0][strlen(str)]));
    }
    """, language="C")

m.set_argv('exaile')

```

step 10. save the file.
step 11. run exaile
step 12. its should be working now :D
step 13. have fun

---

### Post by kaivalagi on 2008-11-28
Holy crap, that's a lot you have to go through to sort it, well done on figuring it out!

I am using exaile from the dev repo's and don't have the problem, could it be that version has been updated to work better?

---

### Post by x0x on 2008-11-29
> **kaivalagi said:**
> Holy crap, that's a lot you have to go through to sort it, well done on figuring it out!

I am using exaile from the dev repo's and don't have the problem, could it be that version has been updated to work better?

i am sorry. my english isnt well.. so explain it clearly.:(

EDIT: i mean what you meant by "could it be that version has been updated to work better"

---

### Post by kaivalagi on 2008-11-29
> **x0x said:**
> i am sorry. my english isnt well.. so explain it clearly.:(

EDIT: i mean what you meant by "could it be that version has been updated to work better"

I've installed exaile using this apt source in /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main
```

You could try installing a newer version of exaile from this repo, it may well work fine without any modifications.

---

### Post by x0x on 2008-11-29
umm. do i need to compile it?

---

### Post by kaivalagi on 2008-11-29
> **x0x said:**
> umm. do i need to compile it?

Nope, just add the line to the bottom of your sources.list and update the app through synaptic/apt-get...

If you need help on that, I suggest you read a little more in the forums...

---

### Post by x0x on 2008-11-29
i installed exaile with that repos...

---

### Post by kaivalagi on 2008-11-30
> **x0x said:**
> i installed exaile with that repos...

Does the "$is_running exaile" conky variable now work for you?

---

### Post by akahige on 2008-11-30
Not sure if this is a conkyExaile problem or not, but I know I'll get a swift and authoritative answer, so here goes...

I just took the plunge and upgraded from Hardy to Intrepid, and am sorting out the requisite bugs, glitches, and snafus...

Running conky 1.6.1 + exaile 0.2.14 + conkyExaile 2.02 (which should be all the most current versions from the repos)... The cE template works just fine, there's just one little hitch: when I'm playing a playlist that's set to repeat, it plays just fine through to the end, but when it cycles back around to the first track, the entire template disappears, and does not reappear until it hits track 2 (or if I force it to a different track).

Got any thoughts? Is there anything I can check?


In other news, now that I'm running the most current versions of everything, I tried the ${if_running exaile} thing again, based on the last few comments in the thread, and it still doesn't work for me.

---

### Post by kaivalagi on 2008-11-30
> **akahige said:**
> Not sure if this is a conkyExaile problem or not, but I know I'll get a swift and authoritative answer, so here goes...

I just took the plunge and upgraded from Hardy to Intrepid, and am sorting out the requisite bugs, glitches, and snafus...

Running conky 1.6.1 + exaile 0.2.14 + conkyExaile 2.02 (which should be all the most current versions from the repos)... The cE template works just fine, there's just one little hitch: when I'm playing a playlist that's set to repeat, it plays just fine through to the end, but when it cycles back around to the first track, the entire template disappears, and does not reappear until it hits track 2 (or if I force it to a different track).

Got any thoughts? Is there anything I can check?


In other news, now that I'm running the most current versions of everything, I tried the ${if_running exaile} thing again, based on the last few comments in the thread, and it still doesn't work for me.

That's a new one on me

Setup the same scenario again, but this time use the --errorlogfile option to log all errors to a file...e.g.

```
${execp conkyExaile ...original options... --errorlogfile=/tmp/conkyExaile.log}
```

Post the log file contents if they seem even slightly relevant

I think it may have something to do with the dbus api hooks in the script getting messed up on looping back to the start of the playlist....maybe....

If I can see the error message, it might help me identify what to do to the script to handle the event

I am using exaile from the dev repo's, this may also cure it? If you want to try that add the dev ppa to the bottom of your /etc/apt/sources.list file and upgrade the install. e.g.

[LIST]
[*]edit the sources.list file:
```
gksudo gedit /etc/apt/sources.list
```
[*]Add this to the bottom for the file and save
```
deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main
```
[*]run the following to upgrade
```
sudo apt-get update && sudo apt-get upgrade
```
[/LIST]

Hope that helps

---

### Post by akahige on 2008-11-30
> **kaivalagi said:**
> That's a new one on me

Setup the same scenario again, but this time use the --errorlogfile option to log all errors to a file...e.g.

```
${execp conkyExaile ...original options... --errorlogfile=/tmp/conkyExaile.log}
```

Post the log file contents if they seem even slightly relevant
Done as requested. No log file was created, so I'm guessing that this occurrence isn't being seen as an error.
 

> **kaivalagi said:**
> I am using exaile from the dev repo's, this may also cure it?
Doubtful. I'm running that version, too.  :)

---

### Post by kaivalagi on 2008-11-30
> **akahige said:**
> Done as requested. No log file was created, so I'm guessing that this occurrence isn't being seen as an error.
 


Doubtful. I'm running that version, too.  :)

Can you try using the --infologfile option instead, just in case I messed up and am logging text useful to this error as "info"

The trouble with this sort of issue is that it's REALLY hard to reproduce, it is most likely something to do with the timing of data retrieval...

---

### Post by akahige on 2008-11-30
> **kaivalagi said:**
> Can you try using the --infologfile option instead, just in case I messed up and am logging text useful to this error as "info"
Using infologfile instead of errorlogfile resulted in the template not working at all (except for the progress bar).

Here's the exact line used, in case I'm doing something hideously stupid:
```
${execp conkyExaile --template=/home/user/.conkyExaile.template  --statustext=Playing,Paused,Stopped --infologfile=/home/user/conkyExaile.log}
```


> **kaivalagi said:**
> The trouble with this sort of issue is that it's REALLY hard to reproduce, it is most likely something to do with the timing of data retrieval...
I completely understand. I don't mind doing whatever I can to help get it sorted.

---

### Post by kaivalagi on 2008-11-30
> **akahige said:**
> Using infologfile instead of errorlogfile resulted in the template not working at all (except for the progress bar).

Here's the exact line used, in case I'm doing something hideously stupid:
```
${execp conkyExaile --template=/home/user/.conkyExaile.template  --statustext=Playing,Paused,Stopped --infologfile=/home/user/conkyExaile.log}
```

I completely understand. I don't mind doing whatever I can to help get it sorted.

I'll take a look at the error handling in more detail later on, maybe there is something I can do w.r.t that

Can you live with it for now?

---

### Post by akahige on 2008-11-30
> **kaivalagi said:**
> Can you live with it for now?
Sure. No worries!

Hope I didn't sound like I was complaining. If there's anything I can do to help troubleshoot or test, just let me know.

---

### Post by kaivalagi on 2008-12-01
> **akahige said:**
> Sure. No worries!

Hope I didn't sound like I was complaining. If there's anything I can do to help troubleshoot or test, just let me know.

No it's okay, you have an issue you want to get to the bottom of, I understand....

When I get more time I shall try to reproduce with error catching everywhere in code...if I can't make it happen then I'll ask you to try a few things

---

### Post by x0x on 2008-12-05
no its still not working :p

---

### Post by kaivalagi on 2008-12-05
> **x0x said:**
> no its still not working :p

What do you get when you run:

```
ps -C exaile -f

```

---

### Post by x0x on 2008-12-11
UID        PID  PPID  C STIME TTY          TIME CMD
c0re     21688     1  8 23:35 ?        00:00:22 python /usr/lib/exaile/exaile.py

---

### Post by kaivalagi on 2008-12-11
> **x0x said:**
> UID        PID  PPID  C STIME TTY          TIME CMD
c0re     21688     1  8 23:35 ?        00:00:22 python /usr/lib/exaile/exaile.py

I get the same (I was expecting different :) should have checked at this end first...):

```
UID        PID  PPID  C STIME TTY          TIME CMD
mark      4390     1  7 18:03 ?        00:00:00 python /usr/lib/exaile/exaile.py

```

But if I run "ps -C exaile" I get:

```
  PID TTY          TIME CMD
 4390 ?        00:00:00 **exaile**

```

which is probably why if_running works for me.

I am running exaile v.0.2.14

.................?

---

### Post by x0x on 2008-12-11
look what i have found... easy way to change exaile's process name :p
[http://code.google.com/p/procname/](http://code.google.com/p/procname/)

---

### Post by akahige on 2008-12-11
> **kaivalagi said:**
> I get the same (I was expecting different :) should have checked at this end first...):

```
UID        PID  PPID  C STIME TTY          TIME CMD
mark      4390     1  7 18:03 ?        00:00:00 python /usr/lib/exaile/exaile.py

```

But if I run "ps -C exaile" I get:

```
  PID TTY          TIME CMD
 4390 ?        00:00:00 **exaile**

```

which is probably why if_running works for me.

I am running exaile v.0.2.14

.................?
Yes, but I get the exact same ps output as you do, I'm running the exact same version of Exaile as you are, and it doesn't work for me.

Not that I wouldn't be delighted to have $if_running work as advertised (or as I think it should), but I've got a snazzy work around for my issue, thanks to the folks over on #conky, but I still don't understand why we'd all get different results from the exact same thing.

I'm running conky 1.6.1, from the Intrepid repos.



In other news, I've noticed an interesting "glitch" in the interaction between exaile and conkyExaile. I don't think that it has anything to do with conkyExaile, but in case it does, I wanted to mention it...

I've noticed that when exaile is left paused for extended periods of time -- like overnight -- the track info displayed in conky will disappear (i.e. go blank). If I open exaile and look at the UI, it still shows the paused track sitting there, so I'm guessing that somehow, the communication stream (DBUS?) between exaile and conky is hiccuping.

Does this sound right? Ever see it before?

---

### Post by kaivalagi on 2008-12-11
> **akahige said:**
> Yes, but I get the exact same ps output as you do, I'm running the exact same version of Exaile as you are, and it doesn't work for me.

Not that I wouldn't be delighted to have $if_running work as advertised (or as I think it should), but I've got a snazzy work around for my issue, thanks to the folks over on #conky, but I still don't understand why we'd all get different results from the exact same thing.

I'm running conky 1.6.1, from the Intrepid repos.



In other news, I've noticed an interesting "glitch" in the interaction between exaile and conkyExaile. I don't think that it has anything to do with conkyExaile, but in case it does, I wanted to mention it...

I've noticed that when exaile is left paused for extended periods of time -- like overnight -- the track info displayed in conky will disappear (i.e. go blank). If I open exaile and look at the UI, it still shows the paused track sitting there, so I'm guessing that somehow, the communication stream (DBUS?) between exaile and conky is hiccuping.

Does this sound right? Ever see it before?

I can't figure out the if_running issue, makes no sense to why why it's not working for you.

mmmmm, that overnight glitch certainly points towards dbus...

In the morning when you see this behaviour, what happens is you stop and start conky again, do you see the correct info again?

---

### Post by kaivalagi on 2008-12-11
> **x0x said:**
> look what i have found... easy way to change exaile's process name :p
[http://code.google.com/p/procname/](http://code.google.com/p/procname/)

Just needs to be put into the exaile code....

---

### Post by akahige on 2008-12-11
> **kaivalagi said:**
> I can't figure out the if_running issue, makes no sense to why why it's not working for you.
Me, neither. In case you're interested, the workaround from the guys on #conky is at the bottom of this post. Maybe it will be useful for other people cruising this thread.



> **kaivalagi said:**
> mmmmm, that overnight glitch certainly points towards dbus...

In the morning when you see this behaviour, what happens is you stop and start conky again, do you see the correct info again?
I don't know. I never tried that -- but I will, the next time it happens.

The info comes back as soon as I unpause exaile though. And if my toolbar button addon also communicates through dbus, then that's the culprit because when the conky display is blank, the button loses its status.



Here's the process workaround:

> 
Thanks to lostfayth over on the conky IRC channel, there's a working solution to the show/hide issue.

Here's how it works...

Put this in your conkyexaile template:
```
${if_existing /home/username/.exaile.pid}
your conkyexaile template
${endif}
```

Do not abbreviate the path to your home directory by using "~/" ... conky doesn't like that.


Next, create a bash script file with this contents:
```
#!/bin/bash
PID=`pgrep exaile`

if [[ $PID != '' ]]; then
	echo $PID > ~/.exaile.pid
else
	if [ -e ~/.exaile.pid ]; then
		 rm ~/.exaile.pid
	fi
fi

```

Do not name the bash script anything with "exaile" in the name or the script will pick that up and not work. I called mine ".conky_is_it_running".

The script checks to see if exaile is running and creates a file that conkyrc checks through the $if_existing variable. If exaile isn't running, then the file is deleted.


Finally, add an entry to crontab to call the is_it_running script:
```
* * * * * ~/.conky_is_it_running
```
There's no way to make crontab do something more frequently than every minute, so there can be a bit of a lag (depending on where you fall in the cron cycle), but it works!


---

### Post by kaivalagi on 2008-12-14
New app added to my PPA, new thread on this can be found through the apps link in my sig below...

---

### Post by kaivalagi on 2008-12-31
[COLOR="Green"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

New script available with the following changes:

[LIST]
[*]Unrated rating now outputs nothing
[*]Fixed statustext to work inside template now
[/LIST]

The first post has been updated and the apt package will be available shortly

Cheers

---

### Post by stepper on 2009-01-03
To show details of Exaile on conky only when playing music, I did the following:

1. Created a dummy file called /home/user/playing and wrote 'Playing' without quotes and saved

2. In my conkyrc I typed the following:
     [SIZE="3"]${exec conkyExaile -t /usr/share/conkyexaile/example/conkyExaile.template | grep "Status" |cut -c26- > /home/stepper/status}
${if_empty ${exec diff /home/stepper/playing /home/stepper/status}}
${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}
${endif}[/SIZE]

3. If the results of the diff command is zero/empty then conky displays Exaile info. 

I know its dirty but it works it still needs tweaking to show when stopped as well. I failed terribly with the script posted above for two days.

---

### Post by kaivalagi on 2009-01-03
Nicely done!

I still don't know why I don't have this awkward issue, I can simply use the "$if_running exaile" option instead...

All I am running is exaile from the exaile dev repo...v. 0.2.14

---

### Post by Tick-Tock on 2009-01-06
Hi. I'm dealing with the if_running problem, but it's not so important for now, 'cause i've another thing to fix: when i'm listening to "Böhse Onkelz" i receive this error:

```
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 445, in <module>
    main()
  File "/usr/share/conkyexaile/conkyExaile.py", line 442, in main
    exaileinfo.writeOutput()
  File "/usr/share/conkyexaile/conkyExaile.py", line 395, in writeOutput
    print output.encode("utf-8")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 1: ordinal not in range(128)

```

and there isn't an output for the artist. There is a way to fix it that isn't change the name in the properties of the mp3?

---

### Post by kaivalagi on 2009-01-06
Well I can reproduce the problem, and I can fix it so it works at the command line, but if run in conky it outputs gibberish

See attached

When I get some more time I'll do some research...

If you want the .py file for now I have attached that in a tarball too...

---

### Post by Tick-Tock on 2009-01-06
Ok, it works. Isn't very beautiful to see the name in that way, but it's better than see nothing. Thank you.

p.s.
If you can do a similar work to the other letters... like Ë, Ä, Ï, Ü... when you have some time to spend to, of course ;)

---

### Post by kaivalagi on 2009-01-06
> **Tick-Tock said:**
> Ok, it works. Isn't very beautiful to see the name in that way, but it's better than see nothing. Thank you.

p.s.
If you can do a similar work to the other letters... like Ë, Ä, Ï, Ü... when you have some time to spend to, of course ;)

It should work for all of those characters, they are all unicode and the fix was generic

I really dont know why conky is making that happen though...in my other app (see sig) all works fine.

I need to absorb some unicode material I think :)

Glad it "sort of" works

---

### Post by Tick-Tock on 2009-01-07
> **akahige said:**
> Here's the process workaround:

I, it's me. Again:rolleyes:

I followed the instructions in this post, and it works, but i see that now the cpu's are working on 100% or near, suddendly when i edited the /etc/crontab file (maybe i edited it bad? :confused:).

Suggestion?

EDIT

Sorry, my bad: the cpu was occupied by another process that i didn't close well.
The script works, even if it's quite laggy (30 second in medium case I think). I've not understood well ho works the script made by stepper... it's better?

---

### Post by kaivalagi on 2009-01-07
> **Tick-Tock said:**
> I, it's me. Again:rolleyes:

I followed the instructions in this post, and it works, but i see that now the cpu's are working on 100% or near, suddendly when i edited the /etc/crontab file (maybe i edited it bad? :confused:).

Suggestion?

EDIT

Sorry, my bad: the cpu was occupied by another process that i didn't close well.
The script works, even if it's quite laggy (30 second in medium case I think). I've not understood well ho works the script made by stepper... it's better?

Are you solely talking about scripts for handling the exaile process for conky to work with a is_running option?

If so I really don't know anything, works by default for me, can you help akahige?

---

### Post by akahige on 2009-01-07
> **Tick-Tock said:**
> I, it's me. Again:rolleyes:

EDIT

Sorry, my bad: the cpu was occupied by another process that i didn't close well.
The script works, even if it's quite laggy (30 second in medium case I think). I've not understood well ho works the script made by stepper... it's better?

I have no idea about stepper's script. Seems like you should either use his script or mine. So far as mine goes... I didn't write it, I basically threw myself on the mercy of the good folks over on the conky channel and they helped by doing the heavy lifting and working out what I couldn't.

Having said that, it sounds like now that you identified the CPU issue as having nothing to do with conky, exaile, conkyexaile, or the script, the issue is that the Is It Running script is "laggy". It sounds to me as if it's working as advertised.

The short answer is "of course it's going to be laggy" since crontab WILL NOT do any action more frequently than every one minute. Therefore, depending on where your action of starting or stopping exaile (or whatever you mod the script to do) falls in that cycle, conky could respond instantaneously... or it could take up to a minute... or it could be anywhere in between.

My presumption is that crontab activity is synced to the system clock and if that's true, you should be able to start and stop exaile at different times and see how the script reacts. That, however, is just a guess. I didn't bother to do any research to see how it works.

Does any of this in any way help...? (Or even make sense?)

---

### Post by stepper on 2009-01-08
Ok, lets clear something here!

I did not create a script but only created a file called 'playing' in my home folder which just contains the words 'Playing'.
Then I typed commands in my conkyrc that instructs conky to create a file called 'status' in my home folder, and compare the files by using the 'diff' command. If the file contents are the same the results will be empty (or no output) then conky shows the exaile info based on your template.

I'm not sure if Tick-Tock is trying to use both methods at the same time.
I went this route because I had a problem with crontab.

---

### Post by akahige on 2009-01-08
stepper:

I'm not really sure if your comment was aimed at something I said, but in reading over your last couple of posts, I'm not entirely clear on what your script does vs. what mine does. You mentioned that you went the route that you did with your script because crontab didn't work for you. If I'm understanding correctly, we may be talking across purposes here. The conky status display I'm using is due to the conkyexaile script.

The only thing that my script does is completely hide the conkyexaile template if exaile isn't running.

---

### Post by Tick-Tock on 2009-01-08
> **akahige said:**
> I have no idea about stepper's script. Seems like you should either use his script or mine. So far as mine goes... I didn't write it, I basically threw myself on the mercy of the good folks over on the conky channel and they helped by doing the heavy lifting and working out what I couldn't.

Having said that, it sounds like now that you identified the CPU issue as having nothing to do with conky, exaile, conkyexaile, or the script, the issue is that the Is It Running script is "laggy". It sounds to me as if it's working as advertised.

The short answer is "of course it's going to be laggy" since crontab WILL NOT do any action more frequently than every one minute. Therefore, depending on where your action of starting or stopping exaile (or whatever you mod the script to do) falls in that cycle, conky could respond instantaneously... or it could take up to a minute... or it could be anywhere in between.

My presumption is that crontab activity is synced to the system clock and if that's true, you should be able to start and stop exaile at different times and see how the script reacts. That, however, is just a guess. I didn't bother to do any research to see how it works.

Does any of this in any way help...? (Or even make sense?)

Hi. I understood that the script that you posted is obviously laggy, after some experiments it seems that is as you said, crontab works when the minute changes. What I asked is a little explanation about the script posted by stepper 'cause I would better understand how it works, to compare the two scripts.
It's not my intention to injure anyone, or make comparison between the poster... i'm sorry but my english is poor and probably I made some mistakes writing that would be misinterpreted by my fault...

> **stepper said:**
> Ok, lets clear something here!

I did not create a script but only created a file called 'playing' in my home folder which just contains the words 'Playing'.
Then I typed commands in my conkyrc that instructs conky to create a file called 'status' in my home folder, and compare the files by using the 'diff' command. If the file contents are the same the results will be empty (or no output) then conky shows the exaile info based on your template.

I'm not sure if Tick-Tock is trying to use both methods at the same time.
I went this route because I had a problem with crontab.

Actually I'm using the method with crontab, but I would try both, that's why I asked you to explain the functioning of it.

---

### Post by stepper on 2009-01-08
> **akahige said:**
> stepper:

I'm not really sure if your comment was aimed at something I said, but in reading over your last couple of posts, I'm not entirely clear on what your script does vs. what mine does. You mentioned that you went the route that you did with your script because crontab didn't work for you. If I'm understanding correctly, we may be talking across purposes here. The conky status display I'm using is due to the conkyexaile script.

The only thing that my script does is completely hide the conkyexaile template if exaile isn't running.

My comments were not aimed at anyone per se, I was just trying to explain what I did to show info in conky. Maybe it came out wrong, for that: apologies.

> **Tick-Tock said:**
> Hi. I understood that the script that you posted is obviously laggy, after some experiments it seems that is as you said, crontab works when the minute changes. What I asked is a little explanation about the script posted by stepper 'cause I would better understand how it works, to compare the two scripts.
It's not my intention to injure anyone, or make comparison between the poster... i'm sorry but my english is poor and probably I made some mistakes writing that would be misinterpreted by my fault...



Actually I'm using the method with crontab, but I would try both, that's why I asked you to explain the functioning of it.

Tick-Tock:

Here is the procedure to my method:

1.Create a file called 'playing' in your home folder 
```
gedit ~/playing
```
2. type *Playing* in the file and save.
3.Edit your .conkyrc and type in the following:
> ${exec conkyExaile -t /usr/share/conkyexaile/example/conkyExaile.template | grep "Status" |cut -c26- > ~/status}
${if_empty ${exec diff ~/playing ~/status}}
${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}
${endif}
The first command in conkyrc tells conky to create a file called status and put in the status of exaile: 'Unknown, Playing or Stopped' in that file ~/status.
The *diff* command compares the two files ~/playing and ~/status and if they are the same it means difference is zero or none, then the exaile info is shown in conky as explained by the $if_empty variable [here]("http://conky.sourceforge.net/variables.html"). 
Hope it makes sense...

---

### Post by Tick-Tock on 2009-01-08
> **stepper said:**
> Here is the procedure to my method:

1.Create a file called 'playing' in your home folder 
```
gedit ~/playing
```
2. type *Playing* in the file and save.
3.Edit your .conkyrc and type in the following:

The first command in conkyrc tells conky to create a file called status and put in the status of exaile: 'Unknown, Playing or Stopped' in that file ~/status.
The *diff* command compares the two files ~/playing and ~/status and if they are the same it means difference is zero or none, then the exaile info is shown in conky as explained by the $if_empty variable [here]("http://conky.sourceforge.net/variables.html"). 
Hope it makes sense...

Ok, I think I've understood. At the first time i tried to change the template because I don't like too much the one in /example/ and I retrieve an error. Tried even with if/else, changing the status file and the grep command etc, instead the better and simplier way is to create another template and add it in the third line like this:

```
${exec conkyExaile -t /usr/share/conkyexaile/example/conkyExaile.template | grep "Status" |cut -c26- > ~/status}
${if_empty ${exec diff ~/playing ~/status}}
${execp conkyExaile --template=/usr/share/conkyexaile/myConkyExaile.template}
${endif} 
```

Now it works properly and without lag, tjanks to all :D

@ kaivalagi

I don't know why, but I notice that now the problem with the umlaut is well fixed: "Böhse Onkelz" in exaile become "Böhse Onkelz" in conky without any problem. I think it's probably because i use "execp" instead of "exec" in the code, but i'm not sure...

---

### Post by kaivalagi on 2009-01-08
> **Tick-Tock said:**
> 
@ kaivalagi

I don't know why, but I notice that now the problem with the umlaut is well fixed: "Böhse Onkelz" in exaile become "Böhse Onkelz" in conky without any problem. I think it's probably because i use "execp" instead of "exec" in the code, but i'm not sure...

So you mean it's fixed with the latest script I gave you or with the current live version available via apt?

This confirms either way that conky plays a significant part in screwing with unicode text support...

---

### Post by kaivalagi on 2009-01-10
**[COLOR="Red"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Fixed the script to handle unicode output better (I hope)

The first post has been updated and the apt package should be available soon

---

### Post by Tick-Tock on 2009-01-10
> **kaivalagi said:**
> So you mean it's fixed with the latest script I gave you or with the current live version available via apt?

This confirms either way that conky plays a significant part in screwing with unicode text support...

I don't know if it works thanks to the new .py you gave me o why i use the execp command instead of exec...

---

### Post by kaivalagi on 2009-01-10
> **Tick-Tock said:**
> I don't know if it works thanks to the new .py you gave me o why i use the execp command instead of exec...

No worries, we have the same issues with the rhythmbox script too, that worked out okay...so whats good for one if good for another (I hope) :)

---

### Post by kaivalagi on 2009-02-02
**[COLOR="Red"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

New instructions on setting up the repository in your system have been added to the first post, as follows

[COLOR="Red"]**Remove any existing /etc/apt/sources.list entry before or after doing this!**[/COLOR]

1) Create the necessary list file for access to the repository by running this:

```
sudo wget -q http://www.kaivalagi.com/m-buck-ppa.list -O /etc/apt/sources.list.d/m-buck-ppa.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/m-buck-ppa-key.gpg -O- | sudo apt-key add -
```

---

### Post by pfeoora on 2009-02-17
> **x0x said:**
> 
step 1. download the attachment file.
step 2. save it
step 3. extract it; tar xzf PyInline-0.03.tar.gz
step 4. cd PyInline-0.03
step 5. chmod +x setup.py
step 6. sudo ./setup.py install
step 7. sudo gedit /usr/lib/exaile/exaile.py
step 8. find import sys
step 9. add after
```
import dl
import PyInline
import time
libc = dl.open('/lib/libc.so.6')
if libc != 0 : libc.call('prctl', 15, 'exaile\0', 0, 0, 0)
else : print ('prctl not called')

m = PyInline.build(code=r"""
    #include <Python.h>
    #include <stdio.h>
    #include <string.h>

    void set_argv(char *str){
        int argc;
        char **argv;
        Py_GetArgcArgv(&argc, &argv);
        strncpy(argv[0], str , strlen(str));
        memset(&argv[0][strlen(str)], '\0', strlen(&argv[0][strlen(str)]));
    }
    """, language="C")

m.set_argv('exaile')

```

step 10. save the file.
step 11. run exaile


Doesn't work for me. Get this error message:

```

Couldn't create build directory _PyInline_edbd2b2165da1a06c01d11721c556823
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 37, in <module>
    """, language="C")
  File "/usr/lib/python2.5/site-packages/PyInline/__init__.py", line 38, in build
    return b.build()
  File "/usr/lib/python2.5/site-packages/PyInline/C.py", line 44, in build
    self._writeModule()
  File "/usr/lib/python2.5/site-packages/PyInline/C.py", line 156, in _writeModule
    raise BuildError("Couldn't open source file for writing: %s" % e)
PyInline.BuildError: Couldn't open source file for writing: [Errno 2] No such file or directory: '_PyInline_edbd2b2165da1a06c01d11721c556823/_PyInline_edbd2b2165da1a06c01d11721c556823.c'

```

Any ideas? Trying to get ${if_running} to work like crazy but nothing seems to work :(

---

### Post by Vandrerol on 2009-02-18
> Any ideas? Trying to get ${if_running} to work like crazy but nothing seems to work 

Hey there. I've been wrestling all day with both conkyExaile and {if_running}. About three hours later (I'm still new to this whole linux thing...), I have figured a very crude work-around.

For some reason if_running isn't working with exaile, so I tried using if_existing instead. Turns out exaile creates a file when it's playing and deletes it when you exit, so all you need to do is check for that file.

My conkyrc ends up looking like this
```
${if_existing /home/user/.exaile/music.db-journal}
```

I'm sure I'm doing something really dumb, but it works...

---

### Post by kaivalagi on 2009-02-19
Nice find!

---

### Post by pfeoora on 2009-02-21
> **Vandrerol said:**
> 
My conkyrc ends up looking like this
```
${if_existing /home/user/.exaile/music.db-journal}
```

I'm sure I'm doing something really dumb, but it works...

Wow, thanks! Works like a charm \\:D/ :-D

---

### Post by mayacreator on 2009-03-25
Hi, guys I`ve just installed conkyexaile-2.04 and when I run conky with this
```
${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}
```

I see on screen something like this
Status:Unknown
Artist:Unknown
Album:Unknown
...etc

What I do wrong?
Exaile is running

---

### Post by kaivalagi on 2009-03-25
> **mayacreator said:**
> Hi, guys I`ve just installed conkyexaile-2.04 and when I run conky with this
```
${execp conkyExaile --template=/usr/share/conkyexaile/example/conkyExaile.template}
```

I see on screen something like this
Status:Unknown
Artist:Unknown
Album:Unknown
...etc

What I do wrong?
Exaile is running

Playing mp3's? or internet radio etc???

I'll take a look at the weekend, I'm away from home on training at the mo

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Green"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

**PPA Location Changes**

I have created new PPA's on launchpad to sub-divide all my scripts into their own categories. As such the installation steps for conky scripts have changed, which have been updated on the first post.

You should all change the repository details using the first post steps to get new updates, no new updates will be applied to the old archive location going forwards.

By all means leave the old settings in place too, but these will not help you much.

**Jaunty Package Support**

I have created equivalent packages for Jaunty Jackalope in my PPA's now. They are identical to the intrepid packages but sit under a jaunty location. In my limited testing they all seem to work fine. Again the first post has been updated to describe the setup steps.

Chimo!

---

### Post by Judgegeo on 2009-04-25
Any help would be appreciated

```
ERROR: Error loading template file: [Errno 2] No such file or directory: 'usr/share/conkyexaile/example/conkyExaile.template'
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 445, in <module>
    main()
  File "/usr/share/conkyexaile/conkyExaile.py", line 442, in main
    exaileinfo.writeOutput()
  File "/usr/share/conkyexaile/conkyExaile.py", line 395, in writeOutput
    print output.encode("utf-8")
UnboundLocalError: local variable 'output' referenced before assignment
```

template:
```
Artist: [--datatype=AR]
Title: [--datatype=TI]
Album: [--datatype=AL]
```

---

### Post by kaivalagi on 2009-04-26
> **Judgegeo said:**
> Any help would be appreciated

```
**[COLOR="Red"]ERROR: Error loading template file: [Errno 2] No such file or directory: 'usr/share/conkyexaile/example/conkyExaile.template'[/COLOR]**
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 445, in <module>
    main()
  File "/usr/share/conkyexaile/conkyExaile.py", line 442, in main
    exaileinfo.writeOutput()
  File "/usr/share/conkyexaile/conkyExaile.py", line 395, in writeOutput
    print output.encode("utf-8")
UnboundLocalError: local variable 'output' referenced before assignment
```


The answer really is in the error message, the example template you are pointing to with the command line options isn't there...

---

### Post by Judgegeo on 2009-04-26
> **kaivalagi said:**
> The answer really is in the error message, the example template you are pointing to with the command line options isn't there...

Thats the thing that confuses me, it IS there. I've checked and double checked, deleted the file, made a new one, still I get the same error.

---

### Post by kaivalagi on 2009-04-27
> **Judgegeo said:**
> Thats the thing that confuses me, it IS there. I've checked and double checked, deleted the file, made a new one, still I get the same error.

Missing "/" at the start of the path?

"usr/share/conkyexaile/example/conkyExaile.template" should be "/usr/share/conkyexaile/example/conkyExaile.template" otherwise the script may try loading the file from a usr sub-folder somewhere...

---

### Post by Judgegeo on 2009-04-27
> **kaivalagi said:**
> Missing "/" at the start of the path?

"usr/share/conkyexaile/example/conkyExaile.template" should be "/usr/share/conkyexaile/example/conkyExaile.template" otherwise the script may try loading the file from a usr sub-folder somewhere...

You sir, are a gentleman and a squire. I never once picked up on that! Even though the other 3 scripts of yours I run have the "/", haha. 

THANK YOU :3.

---

### Post by Sarai the Geek on 2009-07-21
Can this script produce a progress bar? I don't see it in the template or options but it's mentioned once in this thread, so it's possible I'm being totally dense...?

---

### Post by kaivalagi on 2009-07-22
> **Sarai the Geek said:**
> Can this script produce a progress bar? I don't see it in the template or options but it's mentioned once in this thread, so it's possible I'm being totally dense...?

The script can produce a percentage value for progress, which can be used along with the execibar function, e.g.:

${execibar 1 conkyExaile --datatype=PC}

Take a look at the conky documentation pages for more info on it if you get stuck, it should be simple enough though

Cheers

---

### Post by kaivalagi on 2009-07-26
**[COLOR=DarkRed][SIZE=4]UPDATE[/SIZE][/COLOR]**
 
 I have added cover art support to the script, now cover art image filepaths can be found by using the --datatype=CA option. This option will be useful to anyone using the $image function now available with conky v1.7.1+
  
Package changes can be seen here:  [URL="https://launchpad.net/%7Em-buck/+archive/conky/+files/conkyexaile_2.05_source.changes"]https://launchpad.net/~m-buck/+archive/conky/+files/conkyexaile_2.05_source.changes
[/URL]  
 The apt packages should be available shortly, the first post has the new packages attached also
 
 Chimo

[COLOR=DarkSlateGray]Edit: I forgot to update the README and the help output to detail the CA datatype availability...this will be updated in the next release whenever that is...[/COLOR]

---

### Post by fooey on 2009-08-08
awesome. kaivalagi, thanks for all your hard work! =D>

---

### Post by maximalistic on 2009-08-17
does this work with the dev version of exaile? i cant get any info out of it!?

---

### Post by kaivalagi on 2009-08-17
> **maximalistic said:**
> does this work with the dev version of exaile? i cant get any info out of it!?

I'm running version 0.2.14 of Exaile and have it working, I am using this repo:

```
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu jaunty main

```

---

### Post by maximalistic on 2009-08-18
> **kaivalagi said:**
> I'm running version 0.2.14 of Exaile and have it working, I am using this repo:

```
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu jaunty main

```

im using that repo and exaile says its version 0.2.999.1 but it really is 0.3b1

---

### Post by puma303 on 2009-08-27
hi, the new release of exaile (0.3) don't work whit conkyExaile any help?

---

### Post by qweru on 2009-09-06
is there a way to set max length like in your banshee script??

---

### Post by Xsoldier2000 on 2009-09-23
I've just switched from flaky Rhythmbox to Exaile 3.0.1 and nothing I do can get conky to display anything about Exaile.

I tried the "${if_existing /home/user/.exaile/music.db-journal}" (nothing displays)

also:   got rid of the ${if_running exaile} and ${endif}  leaving  ${execp conkyExaile --template=/home/rich/.conky/conkyExaile.template}  result: the template loaded with UNKNOWN for everything.

also:  tried putting $colors in front of $if_running exaile}   result: nothing loaded.

also: tried just running your included example.template using ```
conky -c /usr/share/conkyexaile/example/conkyrc &
```  result: loaded the example with UNKNOWN for everything.

... and yes, I am absolutely sure exaile is running the whole time.

Any help?

---

### Post by kaivalagi on 2009-09-23
> **puma303 said:**
> hi, the new release of exaile (0.3) don't work whit conkyExaile any help?

> **Xsoldier2000 said:**
> I've just switched from flaky Rhythmbox to Exaile 3.0.1 and nothing I do can get conky to display anything about Exaile.

I actually still prefer Rhythmbox, it has a better interface as far as I am concerned. It's a shame there is no real active development carrying on with it...I suspect Banshee will replace Rhythmbox as the default Ubuntu player at some point.

**_The Issue_**

It looks like the Exaile team have re-written the dbus interface for their app, as a result the script no longer works because it can't get a hold of any music data.

The conkyExaile script will need a rewrite to work with the new dbus service and it's alternative exposed methods...I'll see what I can fathom out in the short term, but I suspect it will not be a simple change.

[COLOR="Blue"]Edit: Fix on it's way, although I can't get coverart to work and there is zero documentation on the GetTrackAttr method and what attribute names are supported :([/COLOR]

---

### Post by kaivalagi on 2009-09-23
> **qweru said:**
> is there a way to set max length like in your banshee script??

I'll do another build with this option added, it was missed from the script after being first implemented in the Banshee one, it is in the Rhythmbox script though...shouldn't take much effort.

---

### Post by kaivalagi on 2009-09-23
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

The script has had the following changes made:

[LIST]
[*]Updated to use the new exaile dbus service, currently coverart not working...
[*]Added --maxlength option already available with Rhythmbox and Banshee scripts
[/LIST]

Package changes can be seen here:  [URL="https://launchpad.net/%7Em-buck/+archive/conky/+files/conkyexaile_2.06_source.changes"]https://launchpad.net/~m-buck/+archive/conky/+files/conkyexaile_2.06_source.changes
[/URL]And here: [URL="https://launchpad.net/%7Em-buck/+archive/conky/+files/conkyexaile_2.07_source.changes"]https://launchpad.net/~m-buck/+archive/conky/+files/conkyexaile_2.07_source.changes
[/URL]

I release 2 versions one after the other, in quick succession...(I messed up :) )

The apt packages should be available shortly, the first post has the new packages attached also but they will probably only work with Jaunty

[COLOR="DimGray"]Note: I forgot to update readme so details on the maxlength option are not present, but this can be looked up using conkyExaile -h in a terminal
[/COLOR]
Chimo

[COLOR="Blue"]Edit: There was a request made to expose coverart via dbus, it will be introduced in a future release: [https://bugs.launchpad.net/exaile/+bug/434787](https://bugs.launchpad.net/exaile/+bug/434787)[/COLOR]

---

### Post by Xsoldier2000 on 2009-09-24
Thank you so muck for all your hard work. I agree with you about rhythmbox eing better, and with the cover art plugin, it make a better visual on the desktop. (With being able to control the player from the cover art; ie. play pause next and previous)

But sometimes, hitting play the player just hangs...it'll say it's playing, but it's not. Just weird stuff, and I've never had that with Exaile. Now with your hard work, I can enjoy exaile.

Thank you so much for all your time spent with updates and such.

:guitar:    \../,  you rock   ,\../

---

### Post by kaivalagi on 2009-09-25
> **Xsoldier2000 said:**
> Thank you so muck for all your hard work. I agree with you about rhythmbox eing better, and with the cover art plugin, it make a better visual on the desktop. (With being able to control the player from the cover art; ie. play pause next and previous)

But sometimes, hitting play the player just hangs...it'll say it's playing, but it's not. Just weird stuff, and I've never had that with Exaile. Now with your hard work, I can enjoy exaile.

Thank you so much for all your time spent with updates and such.

:guitar:    \../,  you rock   ,\../

My pleasure, just gonna have to wait on the cover art support to be introduced to the api now...3.1 will have it I think, whenever that comes out.

---

### Post by kaivalagi on 2009-10-17
Quick heads up, a patch has been posted for a dbus call to retreive cover art, it is detailed against the bug here: [https://bugs.launchpad.net/exaile/+bug/434787](https://bugs.launchpad.net/exaile/+bug/434787)

I have updated my exaile source locally and have the gtk-desktop-info app working with it too, just waiting for it to actually be released into a new revision of exaile then I'll publish a new package with the cover art fix...

Edit: the image returned is only 64x64 pixels :( I've asked if something better could be achieved, like in older versions...

Edit2: My bad, the cover art was 64x64 cause of where it came from, better quality art if returned to exaile will be provided via the dbus method. The fix has been commited, it should appear in the next Exaile release.

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by kaivalagi on 2010-01-09
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```
Then follow the modified first post instructions for the scripts
[/COLOR]

---

### Post by GSF1200S on 2010-03-10
Well, conky colors works great for me, except for this. I have python-dbus and obviously dbus installed. Im running the latest development release of exaile having updated it from bzr yesterday.

However, whenever I open conky OR I run conkyExaile from the terminal I get this error:

```
ERROR: Issue calling the dbus service:invalid literal for float(): None
Unknown
```

I have absolutely no idea where to go here. Any ideas?

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Well, conky colors works great for me, except for this. I have python-dbus and obviously dbus installed. Im running the latest development release of exaile having updated it from bzr yesterday.

However, whenever I open conky OR I run conkyExaile from the terminal I get this error:

```
ERROR: Issue calling the dbus service:invalid literal for float(): None
Unknown
```

I have absolutely no idea where to go here. Any ideas?

Something is being passed in as "nothing" when calling the dbus service for exaile I think

Can you give me an example of what you are trying to do, ie.r the terminal command you used to get the error?

I can't promise anything cause I am running Arch not Ubuntu and dont use exaile anymore, but we shall see. I have exaile v0.3.0.2 installed so I'll be testing with that once I know what you are trying to do, what version are you running?

[COLOR="Blue"]Edit: seems to fail with that error when nothing is playing, if playing something then no error and  the correct output...same for you?
[/COLOR]

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Something is being passed in as "nothing" when calling the dbus service for exaile I think

Can you give me an example of what you are trying to do, ie.r the terminal command you used to get the error?

I can't promise anything cause I am running Arch not Ubuntu and dont use exaile anymore, but we shall see. I have exaile v0.3.0.2 installed so I'll be testing with that once I know what you are trying to do, what version are you running?

[COLOR="Blue"]Edit: seems to fail with that error when nothing is playing, if playing something then no error and  the current output...same for you?[/COLOR]

I open a terminal and put in:
```
conkyExaile -s -m
```
and I return the following error message:
```
ERROR: Issue calling the dbus service:invalid literal for float(): None
Unknown
```
I figured that the script is probably meant to be run through conky, so I created a conkyrc with --exaile as one of the options.

If I close Exaile, and then execute Conky in a terminal, I get NO error message. Once I open Exaile, Conky's terminal spits out this same error over and over again (this is BEFORE I start playing a song):
```
ERROR: Issue calling the dbus service:empty string for float()
```

Once I start playing a song, I get the same error message as I did when inputing the above terminal command:
```
ERROR: Issue calling the dbus service:invalid literal for float(): None
```
Note the absence of "Unknown"

Im running Xubuntu 9.10 64bit, Exaile 3.1b+ rev 2884 (from bzr), with repo versions of python-dbus and dbus.

---

### Post by kaivalagi on 2010-03-10
Not quite the same as I'm seeing with my version but hopefully the fix in the attached file will help. I think it's something to do with not handling null values properly when nothing is available from exaile for whatever reason. Could be the song has no tag info too? Give it a go and let me know...

[COLOR="Blue"]Edit: just installed exaile from bzr (3.1b+) and I have the same error, I can debug it now :) I'll see what I can come up with...
[/COLOR]

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Not quite the same as I'm seeing with my version but hopefully the fix in the attached file will help. I think it's something to do with not handling null values properly when nothing is available from exaile for whatever reason. Could be the song has no tag info too? Give it a go and let me know...

Cheers

I really appreciate the help:) Unfortunately, that file did not fix the issue (replaced it as per your suggestion). It does exactly the same thing as before. I ensured that my song choices had tag data.

Maybe someone who has had this issue will chime in with an idea. Its almost impossible for you to find a solution for something like this when you cant duplicate the issue yourself.. Thanks again :)

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Not quite the same as I'm seeing with my version but hopefully the fix in the attached file will help. I think it's something to do with not handling null values properly when nothing is available from exaile for whatever reason. Could be the song has no tag info too? Give it a go and let me know...

[COLOR="Blue"]Edit: just installed exaile from bzr (3.1b+) and I have the same error, I can debug it now :) I'll see what I can come up with...
[/COLOR]

Hah! Beat me to it.. I was going to go back to 3.0.2 just to see if the script worked :)

*EDIT* If you find something that might need a change in Exaile itself, you could let them know in the #exaile channel (freenode), or simply let me know here and ill drop in there. I dont know if theyll be able to incorporate anything, but they are good devs...

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Hah! Beat me to it.. I was going to go back to 3.0.2 just to see if the script worked :)

The newer version of the script attached above would work with the older exaile I think, but I'm almost there with fixing for the newest version of exaile now (without breaking older versions...) so another 10 mins and they'll be a new attachment to test out :)

> **GSF1200S said:**
> *EDIT* If you find something that might need a change in Exaile itself, you could let them know in the #exaile channel (freenode), or simply let me know here and ill drop in there. I dont know if theyll be able to incorporate anything, but they are good devs...

Been there and done that already for cover art issues in the past, it was already in progress but new changes take their time to arrive. The 3.1b+ release for example has a GetCoverData method available in the dbus service now which should provide image data, but it is currently broken (bzr for you). Next proper release should be a good one I hope...

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> The newer version of the script attached above would work with the older exaile I think, but I'm almost there with fixing for the newest version of exaile now (without breaking older versions...) so another 10 mins and they'll be a new attachment to test out :)

Cool.. Ill be here. Yeah, I was just thinking maybe it was something borked on my system specifically, so I was just going to make sure..

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Cool.. Ill be here. Yeah, I was just thinking maybe it was something borked on my system specifically, so I was just going to make sure..

Give this fix a go...let me know how it goes and if all is well I'll try and arrange a new package in the ppa for it...

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Give this fix a go...let me know how it goes and if all is well I'll try and arrange a new package in the ppa for it...

Hmmm man.. I still have the same error. For that matter, the error is exactly the same if a conkyExaile.py isnt even IN /usr/share/conkyexaile.

What revision number are you running (bzr revno   in the folder where you extract from the tarball fetched by bzr)? Im running 3.1b+ rev. 2884. Im attaching my .conkyrc, although I know that will probably not help.

Conky-all installed in repos, and the source from the following link for conky-colors itself:
[http://gnome-look.org/content/show.php/CONKY-colors?content=92328]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328")

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Hmmm man.. I still have the same error. For that matter, the error is exactly the same if a conkyExaile.py isnt even IN /usr/share.

What revision number are you running (bzr revno   in the folder where you extract from the tarball fetched by bzr)? Im running 3.1b+ rev. 2884. Im attaching my .conkyrc, although I know that will probably not help.

Conky-all installed in repos, and the source from the following link for conky-colors itself:
[http://gnome-look.org/content/show.php/CONKY-colors?content=92328]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328")

Are you sure you placed the new file in the right place? /usr/share/conkyexaile/ right?

I am running rev 2660, so not as new as yours. I think you've got either an exaile which all dbus commands have changed for or it's just plain broke w.r.t. dbus right now...I'll try and get a newer version installed...

edit: working for 2885-1 - I asked for 2884 and got this:
==> Finished making: exaile-bzr 2885-1 x86_64 (Wed Mar 10 15:34:13 GMT 2010)

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Are you sure you placed the new file in the right place? /usr/share/conkyexaile/ right?

I am running rev 2660, so not as new as yours. I think you've got either an exaile which all dbus commands have changed for or it's just plain broke w.r.t. dbus right now...I'll try and get a newer version installed...

Yes, I forgot to add /conkyexaile when I wrote that last post, but I replaced the conkyExaile.py at /usr/share/conkyexaile/conkyExaile.py.

I think I still have the tarball (for exaile rev. 2884) as I just installed it yesterday; Ill check and post it as an attachment if possible. I dont know if they rolled back to 2660 or what. Perhaps you just need to update bzr.

They managed to fix a CPU leak and a crash associated with the lyrics viewer pane in 2884, so thats why Im running it now.. 2660 still had those issues..

**EDIT** Ok, ill try and update to 2885-1. These guys fly on releases- I was just in the #exaile channel with them less than 12 hours ago when they dropped out 2884! Ill post back.

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Yes, I forgot to add /conkyexaile when I wrote that last post, but I replaced the conkyExaile.py at /usr/share/conkyexaile/conkyExaile.py.

I think I still have the tarball (for exaile rev. 2884) as I just installed it yesterday; Ill check and post it as an attachment if possible. I dont know if they rolled back to 2660 or what. Perhaps you just need to update bzr.

They managed to fix a CPU leak and a crash associated with the lyrics viewer pane in 2884, so thats why Im running it now.. 2660 still had those issues..

I'm using Arch so bzr based installs for exaile are found in pre made PKGBUILD files which dictate the revision internally. To get 2885 I edited the PKGBUILD before pulling down the source so I got the latest instead.

Still works for me with 2885-1...

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Are you sure you placed the new file in the right place? /usr/share/conkyexaile/ right?

I am running rev 2660, so not as new as yours. I think you've got either an exaile which all dbus commands have changed for or it's just plain broke w.r.t. dbus right now...I'll try and get a newer version installed...

edit: working for 2885-1 - I asked for 2884 and got this:
==> Finished making: exaile-bzr 2885-1 x86_64 (Wed Mar 10 15:34:13 GMT 2010)

Well, I bzr checkout lp:exaile and I get rev 2885. Im not exactly sure how you are getting the 2885-1. So, make and make install as root, and Conky still spits out that error in the terminal, with unknown in all fields of conky (relating to exaile). I dont know whats going on- its working for you.. It has to be my system somehow. Any last ideas of things to re-install/reconfigure that could cause this? I really appreciate the help and im sure you got alot of other peoples (potential) issues fixed.. :)

**EDIT** Makes sense. Ill try all this out on Arch once I get around to figuring out whats wrong with my / filesystem (may end up having to reinstall- ext4 has not been good to me so far). Never used bzr with Arch..

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Well, I bzr checkout lp:exaile and I get rev 2885. Im not exactly sure how you are getting the 2885-1. So, make and make install as root, and Conky still spits out that error in the terminal, with unknown in all fields of conky (relating to exaile). I dont know whats going on- its working for you.. It has to be my system somehow. Any last ideas of things to re-install/reconfigure that could cause this? I really appreciate the help and im sure you got alot of other peoples (potential) issues fixed.. :)

**EDIT** Makes sense. Ill try all this out on Arch once I get around to figuring out whats wrong with my / filesystem (may end up having to reinstall- ext4 has not been good to me so far). Never used bzr with Arch..

Lose all other OS's and stick with Arch alone, you know it makes sense!
The install is from the AUR so you need a tool not available in the core repos, either yaourt/packer/bauerbill will do it. TO install you would run "yaourt -S exaile-bzr" for example, then when prompted for PKGBUILD edit choice yes, and change the revision value towards to top of the file, then continue the install

Another option is to install d-feet and see what is there for dbus, this tool lets you see what dbus services are up on your system and you can explore them too. The attached screenshot if what I see when looking at dbus for exaile (2885). It would be interesting to see what happens if you invoke a method from that tool rather than through the script...try IsPlaying and GetRating as they are simple method calls without the need for input.

btw, the 1 from 2885-1 is an internal release number, nothing to do with the revision of the bzr branch

I wont release a script until I know it atleast works for one other person first :) I want to see this working as much as you do :)
I'm happy to help, I am currently unemployed so don't have too much on for now...still looking for the next contract

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Lose all other OS's and stick with Arch alone, you know it makes sense!
The install is from the AUR so you need a tool not available in the core repos, either yaourt/packer/bauerbill will do it. TO install you would run "yaourt -S exaile-bzr" for example, then when prompted for PKGBUILD edit choice yes, and change the revision value towards to top of the file, then continue the install

Another option is to install d-feet and see what is there for dbus, this tool lets you see what dbus services are up on your system and you can explore them too. The attached screenshot if what I see when looking at dbus for exaile (2885). It would be interesting to see what happens if you invoke a method from that tool rather than through the script...try IsPlaying and GetRating as they are simple method calls without the need for input.

btw, the 1 from 2885-1 is an internal release number, nothing to do with the revision of the bzr branch

I wont release a script until I know it atleast works for one other person first :) I want to see this working as much as you do :)

I think we have stepped past my level of understanding, haha. I grabbed D-Feet and took a screenie of exailes portion. I double clicked on GetTrackAttr, but I dont have any idea what to use for parameters. I did just hit execute and got back:
```
'More items found in D-Bus signature than in Python arguments'
```
Ive attached a screenie of the D-Feet window for comparison, but to me it looks pretty much the same as yours. Im stumped..

**EDIT** Yeah, I need to get back to Arch. Been a few weeks now, but as a college student going through midterms I dont really have the time to go through filesystem surgery (nor the expertise honestly). Granted, I have spent X hours messing with conky, so I suppose I should get my priorities straight. I need to stick with ext3 or maybe jfs and just reinstall..

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> I think we have stepped past my level of understanding, haha. I grabbed D-Feet and took a screenie of exailes portion. I double clicked on GetTrackAttr, but I dont have any idea what to use for parameters. I did just hit execute and got back:
```
'More items found in D-Bus signature than in Python arguments'
```
Ive attached a screenie of the D-Feet window for comparison, but to me it looks pretty much the same as yours. Im stumped..

**EDIT** Yeah, I need to get back to Arch. Been a few weeks now, but as a college student going through midterms I dont really have the time to go through filesystem surgery (nor the expertise honestly). Granted, I have spent X hours messing with conky, so I suppose I should get my priorities straight. I need to stick with ext3 or maybe jfs and just reinstall..

Trust me, you might spend more time upfront getting Arch running how you'd like, but once there the rolling releases take away any nasty rubbish every 6 months...that's reason I left Ubuntu, too many bad things happen when the big 6 monthly update comes along. As a developer I really need newer versions so can't stay where I am but can't justify the crap I used to go through every 6 months...

You would pick the trackattr function, it needs parameters :) Try double clicking on IsPlaying and GetRating, just click execute with anything else input and you should see something come back in the bottom part of the dialog which makes sense...the fact that we can access the dbus service through d-feet is a good thing though.

I'll get you debugging the script next so we can really find out what is wrong ;)

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Trust me, you might spend more time upfront getting Arch running how you'd like, but once there the rolling releases take away any nasty rubbish every 6 months...that's reason I left Ubuntu, too many bad things happen when the big 6 monthly update comes along. As a developer I really need newer versions so can't stay where I am but can't justify the crap I used to go through every 6 months...

You would pick the trackattr function, it needs parameters :) Try double clicking on IsPlaying and GetRating, just click execute with anything else input and you should see something come back in the bottom part of the dialog which makes sense...the fact that we can access the dbus service through d-feet is a good thing though.

I'll get you debugging the script next so we can really find out what is wrong ;)

Alright, lets get to it. I did get dbus output for progress and percent complete, etc.. (IsPlaying returned a 0 for some reason though). I know that Exaile is fine with dbus- Its communicating with Pidgin just fine (just found that out).

---

### Post by trueplay on 2010-03-10
How often do we need to be updating everything?

---

### Post by kaivalagi on 2010-03-10
> **trueplay said:**
> How often do we need to be updating everything?

Your call ;) I guess it really depends on how "in the know" you are with everything.

The last few posts are around a bzr based exaile, which you could class as Alpha/Beta...it's a development release, but does give good hints on what to expect with a future standard release.

If not sure then stick to the norm and you'll be fine, only if there are things not working for you should you think about updating from source code etc.

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Alright, lets get to it. I did get dbus output for progress and percent complete, etc.. (IsPlaying returned a 0 for some reason though). I know that Exaile is fine with dbus- Its communicating with Pidgin just fine (just found that out).

If you want to debug then it will take some serious background reading and a lot of setup. You'll need to get Eclipse installed and add the pydev plugin for starters. Then pull down the source, and run it through in debug mode of eclipse to see what is breaking things...

The alternative is if I put print statements throughout the py file that indicate where exactly the error is happening...I know what section of code it happens in already.

Option 2?

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> If you want to debug then it will take some serious background reading and a lot of setup. You'll need to get Eclipse installed and add the pydev plugin for starters. Then pull down the source, and run it through in debug mode of eclipse to see what is breaking things...

The alternative is if I put print statements throughout the py file that indicate where exactly the error is happening...I know what section of code it happens in already.

Option 2?

Sounds find to me. You mean that I will get print statements in the terminal when I run conkyExaile? Im assuming so.. I will do number 1 actually, as coincidentally im trying to learn python myself, so it would be good help. But for now, we can go route 2. Not enough time in the day, at least for me...

Actually, if its going to be a PITA for you, we can do option 1. No need to waste a ton of your time.. I will be crashing soon, so option 1 will most likely take place tonight.

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Sounds find to me. You mean that I will get print statements in the terminal when I run conkyExaile? Im assuming so.. I will do number 1 actually, as coincidentally im trying to learn python myself, so it would be a good help. But for now, we can go route 2. Not enough time in the day, at least for me...

Modified py file attached, yes it will just print keywords as it goes through the logic, when the error occurs we'll know which part of the code caused it...maybe if it comes to that I can put further checks and more data output to then see what on earth is up

By all means get eclipse and pydev setup locally, and bring down the source from lp...then I can help out (time permitting for both of us of course). Python is really straight forward, if you've done any sort of development of code/scripts etc then it will be a doddle.

BTW, just waiting for my provisional motorbike license, so I can start the arduous task of getting the license (bloody hard in the UK). I'll be jumping on a Kawa 250R Ninja once through that hell, I could get on something like your nickname but I think I'll be taking it a step at a time :)

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Modified py file attached, yes it will just print keywords as it goes through the logic, when the error occurs we'll know which part of the code caused it...maybe if it comes to that I can put further checks and more data output to then see what on earth is up

By all means get eclipse and pydev setup locally, and bring down the source from lp...then I can help out (time permitting for both of us of course). Python is really straight forward, if you've done any sort of development of code/scripts etc then it will be a doddle.

BTW, just waiting for my provisional motorbike license, so I can start the arduous task of getting the license (bloody hard in the UK). I'll be jumping on a Kawa 250R Ninja once through that hell, I could get on something like your nickname but I think I'll be taking it a step at a time :)

Interesting note:
```
[poeticrpm@geekdom ~]$ conkyExaile -r -s
*** test for dbus service
*** remote object 1
*** remote object 2
*** isplaying and get status
*** coverart retrieval
*** cover art manip
*** title
*** album
*** artist
*** genre
*** date
*** tracknumber
*** filename
*** length
*** length manip
*** current pos per
*** current pos
*** volume
Un-United Kingdom (Fuzz Townshend Mix)

```
Thats the name of the song Im playing, but conky's terminal is still, as it has been from the start, returning:
```
ERROR: Issue calling the dbus service:invalid literal for float(): None
```
It seems to me that Exaile is fine on dbus, and conkyExaile is working, as it is obviously printing the song title playing in Exaile. Are you sure this is an issue with your script?

**EDIT** Ive been riding a while, and that bike still threatens my life at times. A 250 is a great bike, even beyond the whole "starter" aspect. You will likely be a better rider than most the guys who jump on literbikes right out of the gate.. Be careful out there! I dont know about the UK, but the drivers here in the US do NOT see motorcyclists (better in Florida than California in that respect though).

**EDIT2** Haha, I realized what a coincidence my song above was. I dont suppose you like Pitchshifter?

---

### Post by GSF1200S on 2010-03-10
**Delete**

---

### Post by kaivalagi on 2010-03-10
> **GSF1200S said:**
> Interesting note:
```
[poeticrpm@geekdom ~]$ conkyExaile -r -s
*** test for dbus service
*** remote object 1
*** remote object 2
*** isplaying and get status
*** coverart retrieval
*** cover art manip
*** title
*** album
*** artist
*** genre
*** date
*** tracknumber
*** filename
*** length
*** length manip
*** current pos per
*** current pos
*** volume
Un-United Kingdom (Fuzz Townshend Mix)

```
Thats the name of the song Im playing, but conky's terminal is still, as it has been from the start, returning:
```
ERROR: Issue calling the dbus service:invalid literal for float(): None
```
It seems to me that Exaile is fine on dbus, and conkyExaile is working, as it is obviously printing the song title playing in Exaile. Are you sure this is an issue with your script?

**EDIT** Ive been riding a while, and that bike still threatens my life at times. A 250 is a great bike, even beyond the whole "starter" aspect. You will likely be a better rider than most the guys who jump on literbikes right out of the gate.. Be careful out there! I dont know about the UK, but the drivers here in the US do NOT see motorcyclists (better in Florida than California in that respect though).

**EDIT2** Haha, I realized what a coincidence my song above was. I dont suppose you like Pitchshifter?

Definitely not Exaile and conkyExaile, looks like something with Conky...are you sure you're calling the same script from your conkyrc? Just checking...

No way will I jump on a big bike, and yes people in the UK don't see bikes either! I will have a bright green bike with matching bash hat and fluorescent jacket! But I'll still get bloody hit! To be fair I plan on travelling most of my time on motorways which should keep the risk down a lot. But, yes, I will be extra extra cautious - expecting everyone to hit me! I plan on a bike no bigger than 600cc long term, another Ninja me thinks...but who knows what's out there in a couple of years screaming for me to buy it :)

---

### Post by GSF1200S on 2010-03-10
> **kaivalagi said:**
> Definitely not Exaile and conkyExaile, looks like something with Conky...are you sure you're calling the same script from your conkyrc? Just checking...

No way will I jump on a big bike, and yes people in the UK don't see bikes either! I will have a bright green bike with matching bash hat and fluorescent jacket! But I'll still get bloody hit! To be fair I plan on travelling most of my time on motorways which should keep the risk down a lot. But, yes, I will be extra extra cautious - expecting everyone to hit me! I plan on a bike no bigger than 600cc long term, another Ninja me thinks...but who knows what's out there in a couple of years screaming for me to buy it :)

I have good news! I now have it working, kind of! The status always says playing (even if I pause), however it correctly reflects stopped. It doesnt import album art (not a dealbreaker) either. Also, the time always shows 0:00 for the total song length. Honestly, I wouldnt mind removing the time and status- mainly interested in the song and album art. I accomplished this by modifying my conkyrc exaile line to:
```
conkyExaile -t ~/.conkycolors/templates/conkyPlayer.template
```
Prior to this change, it was attempting to call a conkyexaile executable in ~/.conkycolors/bin/ and THEN call this template.

Also, I went back to the version of conkyExaile.py you sent me approximately 2 times ago (the one before the one prior to the annotated one you sent), and it did NOT work. Updating to the one directly before the annotated one fixed the issues for me. This is good because I feel like I didnt completely waste your time ;)

I still get that error message, but at least it works now.

I say go ahead and role out a new release :) Included a screenshot so you can see what I mean about the time issue..

Thanks, and let me know if you need any more testing from me. :)

**EDIT** Haha, a 600cc ninja is still a VERY powerful bike, so youll have to be careful when you end up on one (and you will :) you cannot prevent such purchases ;)) Thats really good about the coloring- alot of people want black and "cool" looking. I have a black and white leather jacket thats very easy to see at night, along with a fluorescent vest if Im taking long trips. As you probably know, there are three big things to look out for:
1) People making a right turn in front of you (left turn for here in the US) without seeing you. Of motorcycle wrecks with a car, this is almost 70% of the fatalities in the US.
2) Getting rear-ended
3) Single vehicle wreck (pushing it too hard and going low-side/high-side/off the road)
Im not familiar with England, but if im aware correctly you have more turnabouts as opposed to lights, which for motorcycles is very good. Sounds like you'll be fine though- you have a good attitude! :)

---

### Post by GSF1200S on 2010-03-11
Heres what it looks like (finally). It doesnt really matter that I cannot import the album art- I just use Exaile's Desktop Cover plugin and put it right below conky. Thanks again :)

---

### Post by kaivalagi on 2010-03-11
> **GSF1200S said:**
> Heres what it looks like (finally). It doesnt really matter that I cannot import the album art- I just use Exaile's Desktop Cover plugin and put it right below conky. Thanks again :)

Cool, and no probs, I'll check the total length value...

The cover art is something I'd like to see work but the dbus side of things fails for this (try it in d-feet)

Yeah, the dreaded right turn in front of you. Believe it or not by I've had that happen to me when on my bicycle at 20mph! I went sideways like in speedway which saved me but I don't think that would be safe on a motorbike :) Not an easy situation to avoid I guess, especially if it's last minute stuff...

Edit: BR (bitrate) datatype added too, hopefully a new package should turn up soon, I have to ask mobilediesel to build and deploy it as I don't run Ubuntu any more...

---

### Post by kaivalagi on 2010-03-11
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

The script has had changes made for compatibility to v3.1b+ of Exaile and now supports a new datatype BR or bitrate

Changes can been seen here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.09_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.09_source.changes)

The package updates are now available and the first post has been updated

Cheers

---

### Post by GSF1200S on 2010-03-17
> **kaivalagi said:**
> **[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

The script has had changes made for compatibility to v3.1b+ of Exaile and now supports a new datatype BR or bitrate

Changes can been seen here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.09_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.09_source.changes)

The package updates are now available and the first post has been updated

Cheers

I was recently talking with the Exaile devs about some issues occurring as a result of using this script. You had fixed the script and it was working fine, but as a result of how it worked, dbus was spitting a TON of input errors out. The issue was so extreme that exaile.log and ~/.xsession-errors where growing MB's by the second with dbus errors. The dev determined that part of the issue was the manner in which Exaile was functioning. This of course wasnt good as it was doing write operations constantly while conky utilized this script. In the latest revision (bzr revno 2918 ), theyve changed the way that Exaile handles such things. Im not really familiar with all the terminology, so I will show you what the dev had to say as well as the patch he had me try with rev. 2917 before he patched and released 2918.  

```
 you might mention that its now a Dbus ByteArray that's being returned, though he should be able to tell that from the patch
```
and the patch:
```
=== modified file 'xl/xldbus.py'
--- xl/xldbus.py	2010-03-02 09:32:45 +0000
+++ xl/xldbus.py	2010-03-17 00:42:39 +0000
@@ -426,7 +426,7 @@
         """
         self.exaile.gui.main.toggle_visible()
 
-    @dbus.service.method('org.exaile.Exaile')
+    @dbus.service.method('org.exaile.Exaile', None, 'ay')
     def GetCoverData(self):
         """
             Returns the data of the cover image of the playing track, or

```

While the issue on Exaile is now fixed, the script still spits out massive amounts of errors with any song that HAS ALBUM ART. Whats interesting is, even though my conkyPlayer.template and .conkyrc has no datatype trying to fetch cover art (I use exaile's DesktopCover extension instead), the dbus errors only start flying when the song has album art. I can make dbus calls all day with your script as well as Exaile's built in command line options and I have no issue so long as the song has no cover art. Conky spits out no errors that I can see.

---

### Post by kaivalagi on 2010-03-17
> **GSF1200S said:**
> I was recently talking with the Exaile devs about some issues occurring as a result of using this script. You had fixed the script and it was working fine, but as a result of how it worked, dbus was spitting a TON of input errors out. The issue was so extreme that exaile.log and ~/.xsession-errors where growing MB's by the second with dbus errors. The dev determined that part of the issue was the manner in which Exaile was functioning. This of course wasnt good as it was doing write operations constantly while conky utilized this script. In the latest revision (bzr revno 2918 ), theyve changed the way that Exaile handles such things. Im not really familiar with all the terminology, so I will show you what the dev had to say as well as the patch he had me try with rev. 2917 before he patched and released 2918.  

```
 you might mention that its now a Dbus ByteArray that's being returned, though he should be able to tell that from the patch
```
and the patch:
```
=== modified file 'xl/xldbus.py'
--- xl/xldbus.py	2010-03-02 09:32:45 +0000
+++ xl/xldbus.py	2010-03-17 00:42:39 +0000
@@ -426,7 +426,7 @@
         """
         self.exaile.gui.main.toggle_visible()
 
-    @dbus.service.method('org.exaile.Exaile')
+    @dbus.service.method('org.exaile.Exaile', None, 'ay')
     def GetCoverData(self):
         """
             Returns the data of the cover image of the playing track, or

```

While the issue on Exaile is now fixed, the script still spits out massive amounts of errors with any song that HAS ALBUM ART. Whats interesting is, even though my conkyPlayer.template and .conkyrc has no datatype trying to fetch cover art (I use exaile's DesktopCover extension instead), the dbus errors only start flying when the song has album art. I can make dbus calls all day with your script as well as Exaile's built in command line options and I have no issue so long as the song has no cover art. Conky spits out no errors that I can see.

Looks like the cover art returned is the actual image data rather than a file path, sorry didn't realise...I'll need to correct for that. I'm busy busy busy right now with sorting out a new job and other projects so may be a little way off from a fix...for now don't use --datatype=CA anywhere and that should sort it I think (?)

Edit: installed exaile rev. 2918 and it has an error, I reverted to 2912 (0.3.1) and still got errors on startup...gonna have to leave this for today me thinks. I have spent this after learning how to program PIC devices and am done for the day :)

---

### Post by GSF1200S on 2010-03-17
> **kaivalagi said:**
> Looks like the cover art returned is the actual image data rather than a file path, sorry didn't realise...I'll need to correct for that. I'm busy busy busy right now with sorting out a new job and other projects so may be a little way off from a fix...for now don't use --datatype=CA anywhere and that should sort it I think (?)

Well thats the interesting part- I dont have any --datatype=CA in my conkyrc or in the template. Also, if you run exaile on a song with album art and pass ANY command from conkyExaile through the command line (-d PP for instance), it will still spit out all that code (which as you said appears to be image data). I would think that asking for the percent progress would have nothing to do with it, yet it seems to. However, passing a command to Exaile via its built in mechanisms returns no errors.

So, in summary: run exaile, and pass a conkyExaile command (ANY command) and you will get that output in exaile.log, .xsession-errors, and in the terminal. However, once again, if the song doesnt have album art, no errors will be spit out when invoking a conkyExaile command. I have double and triple checked this.

Yeah, we all have things to do man.. no rush. Just thought you would like to know :)

---

### Post by kaivalagi on 2010-03-17
> **GSF1200S said:**
> Well thats the interesting part- I dont have any --datatype=CA in my conkyrc or in the template. Also, if you run exaile on a song with album art and pass ANY command from conkyExaile through the command line (-d PP for instance), it will still spit out all that code (which as you said appears to be image data). I would think that asking for the percent progress would have nothing to do with it, yet it seems to. However, passing a command to Exaile via its built in mechanisms returns no errors.

So, in summary: run exaile, and pass a conkyExaile command (ANY command) and you will get that output in exaile.log, .xsession-errors, and in the terminal. However, once again, if the song doesnt have album art, no errors will be spit out when invoking a conkyExaile command. I have double and triple checked this.

Yeah, we all have things to do man.. no rush. Just thought you would like to know :)

I see, an exaile based issue then maybe, caused when the script connects to exailes dbus service at a guess...I'll double check my script soon and see if anything there could cause it but I doubt it.

The error I am getting from exaile (rev 2921/2918/2912) is this:

```
INFO    : Loading main window...
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 52, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 49, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 84, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 206, in __init
    self.gui = xlgui.Main(self)
  File "/usr/lib/exaile/xlgui/__init__.py", line 99, in __init__
    exaile.collection, exaile.player, exaile.queue, exaile.covers)
  File "/usr/lib/exaile/xlgui/main.py", line 389, in __init__
    self._setup_widgets()
  File "/usr/lib/exaile/xlgui/main.py", line 598, in _setup_widgets
    self.builder.get_object('volume_control')
  File "/usr/lib/exaile/xlgui/guiutil.py", line 431, in __init__
    builder.add_from_file(xdg.get_data_path('ui/widgets/volume_control.ui'))
TypeError: Gtk.Builder.add_from_file() argument 1 must be string, not None

```

---

### Post by MaDxCrEaM on 2010-03-26
so am I correct saying conkyExaile doesn't work with Version 0.3.1.0? I'm using a conky config, and all it basically reads is the time of the song, nothing else is displaying.

---

### Post by kaivalagi on 2010-03-26
> **MaDxCrEaM said:**
> so am I correct saying conkyExaile doesn't work with Version 0.3.1.0? I'm using a conky config, and all it basically reads is the time of the song, nothing else is displaying.

You got it...Exaile code surrounding the dbus functions (used to determine what's going on with the player) have been changing a lot lately and to be honest I am fed up with trying to maintain the script to work with it.

I might take another look in a month or so when maybe things may have settled with the development...but no promises.

By all means if anyone who can develop with Python wants to put some time in instead of me they can go right ahead and post updates to the script in this thread...

---

### Post by GSF1200S on 2010-03-28
> **kaivalagi said:**
> You got it...Exaile code surrounding the dbus functions (used to determine what's going on with the player) have been changing a lot lately and to be honest I am fed up with trying to maintain the script to work with it.

I might take another look in a month or so when maybe things may have settled with the development...but no promises.

By all means if anyone who can develop with Python wants to put some time in instead of me they can go right ahead and post updates to the script in this thread...

I installed the latest bzr version of your script along with the latest bzr of Exaile (rev. 2962) and everything works well. I still get alot of spitout in the terminal and swelling logs, but I just made a script to delete .xsession-errors and exaile logs every so often.. prior to installing the bzr I was getting errors with the latest exaile version.

Keeping up with bzr releases is good stuff :) intentional or not. Cheers..

---

### Post by kaivalagi on 2010-03-28
> **GSF1200S said:**
> I installed the latest bzr version of your script along with the latest bzr of Exaile (rev. 2962) and everything works well. I still get alot of spitout in the terminal and swelling logs, but I just made a script to delete .xsession-errors and exaile logs every so often.. prior to installing the bzr I was getting errors with the latest exaile version.

Keeping up with bzr releases is good stuff :) intentional or not. Cheers..

So whatever was wrong with Exaile has now been fixed, hooray!

That's for letting me know

---

### Post by 98acura on 2010-04-24
Your information for Lucid doesnt work.
You have:

```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conky**forecast**-lucid.list -O /etc/apt/sources.list.d/conkyhardcore-lucid.list
```

Which should be:

```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conky**hardcore**-lucid.list -O /etc/apt/sources.list.d/conkyhardcore-lucid.list
```

---

### Post by kaivalagi on 2010-04-24
> **98acura said:**
> Your information for Lucid doesnt work.
You have:

```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conky**forecast**-lucid.list -O /etc/apt/sources.list.d/conkyhardcore-lucid.list
```

Which should be:

```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conky**hardcore**-lucid.list -O /etc/apt/sources.list.d/conkyhardcore-lucid.list
```

Thanks for the heads up, changed :)

---

### Post by mayacreator on 2010-05-12
Unfortunately it does not work with Exaile 0.3.1.1 :( Could you please fix it?

---

### Post by kaivalagi on 2010-05-12
> **mayacreator said:**
> Unfortunately it does not work with Exaile 0.3.1.1 :( Could you please fix it?

I might take a look at the weekend if I get a chance, see my frustrations with this script and the changes needed all the time 6 posts up ^^^^^^

---

### Post by AlejandroDelLoco on 2010-05-17
I'm having Issues with 3.1.1 myself - same dbus array problems? Here's the output I get in my xsession-errors and running conky:

```
ERROR: Issue calling the dbus service:'dbus.Array' object has no attribute 'find'
```

---

### Post by lautarop on 2010-05-19
dang, me too :(

---

### Post by kaivalagi on 2010-05-19
I can't say when I'll look at it....I'm just too busy.

If someone else wants to look at the problem, fix it and pass on the fix I'm not stopping them...

The problems will be due to changes in the Exaile DBUS methods and what they are returning now compared to before. Quickly debugging the script would highlight the problems, try using eclipse with the pydev plugin for this...and d-feet to show DBUS methods available.

---

### Post by carbolymer on 2010-06-06
Where can i get conky exaile for exaile 0.3.0.1 ? In repo there's only the newest one. -.-

---

### Post by kaivalagi on 2010-06-06
> **carbolymer said:**
> Where can i get conky exaile for exaile 0.3.0.1 ? In repo there's only the newest one. -.-

Sorry, that's not going to happen...exaile keep changing the process and I will not be supporting every variation of it, it's just ridiculous...

However......you may be lucky using my old personal repo here: [https://launchpad.net/~m-buck/+archive/conky](https://launchpad.net/~m-buck/+archive/conky)
It hosts version 2.07 of the script rather than 2.09...I couldn't tell you if it's suitable or not but it may be worth a go. This will not be updated, all new versions go to the documented repo now. To use this repo you would need to remove the other one, otherwise newer versions will supersede older ones.

---

### Post by YUMESUKI on 2010-07-24
Thanks for this.... I am still trying to get it to work properly

---

### Post by grzegorl on 2010-08-16
try this one

---

### Post by RubyApple on 2010-08-17
Could anyone tell me which version of Exaile work with the current version of this script? Thanks. : D

---

### Post by kaivalagi on 2010-08-18
Working for v.0.3.1.99

---

### Post by ReZeeR on 2010-08-22
This error 
  > ERROR: Issue calling the dbus service:'dbus.Array' object has no attribute 'find' comes up whenever a song starts playing that has a know album.... If the song doesn't have a known album then everything  is fine..... A bit weird ?

---

### Post by kaivalagi on 2010-08-22
> **ReZeeR said:**
> This error 
   comes up whenever a song starts playing that has a know album.... If the song doesn't have a known album then everything  is fine..... A bit weird ?

I think it might be related to coverart retrieval in the script...

I'm looking now, I think I am trying to search the coverart data for a string when it is a byte array...

edit: Although the coverart functions via dbus don't work with exaile (internal problems that prevents script doing anything wrong anyway) it wouldn't lead to the problem you have. Unless of course you have a newer version of exaile that brings back cover art data unlike mine...what version are you running?

edit2: installed exaile revision 3720 from bazaar repo and I can reproduce the same error, coverart is the issue...looking into it

edit3: fixed the problem and cover art will now work...I'm packaging a script, I'll post an update when available :)

edit4: As the build is some way off find the 2 main .py files attached

---

### Post by kaivalagi on 2010-08-22
**[COLOR=DarkOrange][SIZE=4]UPDATE[/SIZE][/COLOR]**

The script has had changes as follows:
[LIST]
[*] Fixed cover art functions, working with the latest exaile version from bazaar (0.3.3.0-dev)
[*] Added conkyExaile-GetCoverArt script for on track change updates to /tmp/exaile-coverart.jpg
[/LIST]

Changes can been seen here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.11_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.11_source.changes)

The package updates should be available soon once launchpad has built them (currently 5hrs before build will happen :()

Cheers

---

### Post by ReZeeR on 2010-08-22
Works perfectly, thank you !
[IMG]http://img682.imageshack.us/img682/9449/25067691.jpg[/IMG]

---

### Post by kaivalagi on 2010-08-22
Good stuff :)

The package has just completed being built, just waiting on the package being published for download via the ppa, give it 10 minutes or so and it will turn up in an upgrade

---

### Post by kaivalagi on 2010-08-30
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Changes as follows:
[LIST]
[*]Added --secondsoutput / -S option to output time in seconds
[/LIST]
 
Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.12_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.12_source.changes)

The apt packages should be available shortly

Cheers

---

### Post by statmonkey on 2010-08-31
As always never forget that I am idiot.  Problem resolved on restart.  Duh!  Thanks for all your work, this is fantastic stuff.

---

### Post by VastOne on 2010-09-16
I have read all through this and I am sorry if I missed it, but was the issue with Pause not working resolved?  From the template Playing and Stopped works, but pausing Exaile still shows it as Playing.

Also, BR from the template shows a 320 BR song (showing correctly in Exaile) as a 312k/s in the Conky display...

Again I apologize if I have missed this.

---

### Post by kaivalagi on 2010-09-17
> **VastOne said:**
> I have read all through this and I am sorry if I missed it, but was the issue with Pause not working resolved?  From the template Playing and Stopped works, but pausing Exaile still shows it as Playing.

Also, BR from the template shows a 320 BR song (showing correctly in Exaile) as a 312k/s in the Conky display...

Again I apologize if I have missed this.

No pause in status:
```
                        # grab the data for use
                        if iface.IsPlaying() == True:
                            status = self.getStatusText("playing", statustext)
                        else:
                            status = self.getStatusText("stopped", statustext)
```

Bitrate is very straight forward, so I am not responsible for any deviations...:
```
                        bitrate = iface.GetTrackAttr("__bitrate")
                        if self.isNumeric(bitrate):
                            bitrate = str(int(bitrate)/1024)+"k/s"
```

Just used your template from guayadeque I assume ;)

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)
[*]Updated to provide a custom path for cover art output. The file where coverart gets copied to when using the --datatype=CA option is determined by the -c/--coverartpath option, the default is /tmp/cover.
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.13_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.13_source.changes)

The apt packages should be available soon

Cheers

**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by kaivalagi on 2010-11-21
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to dynamically call the available python exec as /usr/bin/python is linked to Python 3 (Arch) or will be at some point (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.14_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.14_source.changes)

The apt packages should be available soon

---

### Post by VastOne on 2010-11-23
> **kaivalagi said:**
> No pause in status:
```
                        # grab the data for use
                        if iface.IsPlaying() == True:
                            status = self.getStatusText("playing", statustext)
                        else:
                            status = self.getStatusText("stopped", statustext)
```

Bitrate is very straight forward, so I am not responsible for any deviations...:
```
                        bitrate = iface.GetTrackAttr("__bitrate")
                        if self.isNumeric(bitrate):
                            bitrate = str(int(bitrate)/1024)+"k/s"
```

Just used your template from guayadeque I assume ;)

Yes - The fool in me got to me!

Never mind this question... I saw the script for the /tmp//exaile-coverart.jpg and get it now

Thanks K!

---

### Post by VastOne on 2010-11-23
deleted

Updating to 0.3.3.0-dev solved the problem


Thanks

Hey Mark

I am stumped...  I have tried -n -f 0 and the obvious of imlib_cache_size 0 in calling the image in Exaile Conky and none of these are working. 

Running the script from the command line shows no issues, it is doing as it should

Unlike the Guayadeque script which replaces one to one, the Exaile script keeps all the files in the tmp directory and creates a new image file on each change.  For whatever reason, there seems to be a cache somewhere because once a song is locked in on an image, it stays there for good, even though it is not the correct image imbedded in the file

Appreciate any insight you may have

Thanks

I am discovering that Exaile treats the first image it finds and keeps it for every song in that directory it comes from even though it is not written to that directory.  I have gone through every setting I can find and will now report it as a bug

It happens in using both the conkyExaile.py and the ${image [--datatype=CA] -p 2,169 -s 365x375 -n -f 1} in the template.

I am going to report a bug on it at Exaile-dev

---

### Post by VastOne on 2010-11-27
K, 

I have a Python question related to trying to figure this Exaile issue out.

I notice in all your directories, there is a .pyc file that accompanies every .py file with the same name.  I realize it is a bytecode file but need to know what is the function of these files?

The issue I am having with Exaile can be resolved in the cover.py file within the ~/exaile/xl directory by changing the (use_cache = True/False) variable.  In this directory, there is a cover.py, cover.pyc and cover.pyo

I have made the changes to the main cover.py but nothing happens which leads me to believe I need to run something additional (recompile?) in order for the changes to take effect.   

The Exaile developers seem to think that everyone has identical file structures (artist/album/cover.jpg) and create a cache.db in ~.local/share/exaile/covers file that keeps the first played image and uses it for every song played within that directory. This totally circumvents anything your conkyExaile.py and conkyExaile-GetCoverart.py does, which is just plain wrong..

Your wisdom on this will help me a lot and will be greatly appreciated.

Thanks,

VastOne

---

### Post by kaivalagi on 2010-11-28
> **VastOne said:**
> I have a Python question related to trying to figure this Exaile issue out.
No probs - Sorry I didn't pick up on your previous post as you edited an existing post so the thread didn't prompt to attention...

> **VastOne said:**
> I notice in all your directories, there is a .pyc file that accompanies every .py file with the same name.  I realize it is a bytecode file but need to know what is the function of these files?
Nothing to do with me, it's a standard python thing. When a .py file is first executed the .pyc is created and reused if suitable again and again, the c stands for compiled I think

> **VastOne said:**
> The issue I am having with Exaile can be resolved in the cover.py file within the ~/exaile/xl directory by changing the (use_cache = True/False) variable.  In this directory, there is a cover.py, cover.pyc and cover.pyo

I have made the changes to the main cover.py but nothing happens which leads me to believe I need to run something additional (recompile?) in order for the changes to take effect.

Try deleting or renaming the .pyc file, although a change to source should mean it gets used :confused:  

> **VastOne said:**
> The Exaile developers seem to think that everyone has identical file structures (artist/album/cover.jpg) and create a cache.db in ~.local/share/exaile/covers file that keeps the first played image and uses it for every song played within that directory. This totally circumvents anything your conkyExaile.py and conkyExaile-GetCoverart.py does, which is just plain wrong..

Mmmmm, I would assume that the coverart remains the same if the song files played all come from the same directory...but there are circumstances where images are in tags that would mean this is no so (I don't think I have such issues with my music though)

> **VastOne said:**
> Your wisdom on this will help me a lot and will be greatly appreciated.
All I can suggest to removing the .pyc file for cover.py and try again...maybe also put print statements in so you can see what is going on in the command line (assuming t=you start exaile from there)

---

### Post by VastOne on 2010-11-28
> **kaivalagi said:**
> No probs - Sorry I didn't pick up on your previous post as you edited an existing post so the thread didn't prompt to attention...


Mmmmm, I would assume that the coverart remains the same if the song files played all come from the same directory...but there are circumstances where images are in tags that would mean this is no so (I don't think I have such issues with my music though)



No worries!  That is the difference for me, I have over a thousand songs in one directory in my setup.  I do not care about per album setup, mine is more genre based in it's file structure and I do have all the art in a per song embedded tag basis.  A lot of these are the same, say if I have 25 instances of the band Tears for Fears, all 25 of those would have the same embedded file.

I ran Exaile from terminal and it gives no indication as to what is going on other than playing the song.  I will keep after the developers on how to make the changes I need.

Thanks for your help..

---

### Post by VastOne on 2010-11-29
I have figured this one out and will submit this information for anyone else who wants the same thing I was after, to have each individual song use it's embedded tag and not the covers.db cache method.

covers.py is written to /usr/loca/lib/exaile/xl once Exaile is installed.

In covers.py is a line 
```

    def add(self, data):

        """
            Adds an entry to the cache.  Returns a key that can be used
            to retrieve the data from the cache.

            :param data: The data to store, as a bytestring.
        """
```

I made this line

```
    def add(self):
```

and now no data is written to the covers.db which was my objective.

Now every file played uses it's own embedded image and K's scripts work as they should.

---

### Post by kaivalagi on 2010-11-30
> **VastOne said:**
> Now every file played uses it's own embedded image and K's scripts work as they should.
Good catch

How about changing the order in which the getcover script checks/gets images, so the tag contents are used first if found? I'll look to see if I could setup a option flag at the top of the file or something like that..

---

### Post by VastOne on 2010-11-30
> **kaivalagi said:**
> How about I change the order in which the getcover script checks for images, so the tag contents are looked at first?

That would be great K, but I am not sure if it would help (of course I am speaking with limited knowledge)

In testing through all of this it seems to me that the covers.db and covers.py supersede everything else... But you are the master and I am game to test anything you want to do...

---

### Post by VastOne on 2010-11-30
> **kaivalagi said:**
> Good catch

How about changing the order in which the getcover script checks/gets images, so the tag contents are used first if found? I'll look to see if I could setup a option flag at the top of the file or something like that...

Now that I see your changes...

This sounds like the perfect solution...

---

### Post by kaivalagi on 2010-11-30
The attached is the default but for you just change the line:

```
    use_tag_image_only = False
```

to be:

```
    use_tag_image_only = True
```

Not tested but it should work, it just bypasses the getting of cover art file paths so forces tag image usage

---

### Post by VastOne on 2010-11-30
> **kaivalagi said:**
> The attached is the default but for you just change the line:

```
    use_tag_image_only = False
```

to be:

```
    use_tag_image_only = True
```

Not tested but it should work, it just bypasses the getting of cover art file paths so forces tag image usage

Worked perfectly!  I changed back the covers.py to it's original and used these changes and now Exaile is doing what it should be, or at least what I want it to do.

As always, I appreciate your help.

Thank you!

---

### Post by kaivalagi on 2010-11-30
No worries, just remember to adjust the flag on each update :) I could put the flag into a gconf setting or a file but it's a lot of complication for one reason

I'll get the changes into the next package that gets released, if there isn't a good enough reason remind me by the new year to rollout the new script regardless ;)

---

### Post by VastOne on 2010-12-04
K,

Would you know how to get a call for datatype=BR to stop displaying the trailing k/s and just have the number?

It does not do it in Guayadeque but is there in Exaile

Thanks...

---

### Post by kaivalagi on 2010-12-04
Turns out all scripts except the Guayadeque one append "k/s" on the end, if you want to remove it then where's the offending text in red within the exaile script:

```
                        bitrate = iface.GetTrackAttr("__bitrate")
                        if self.isNumeric(bitrate):
                            bitrate = str(int(bitrate)/1024)**[COLOR="Red"]+"k/s"[/COLOR]**
```

I'll not be adding an option to hide/show it I don't think, it's a lot of trouble to go to foe something so trivial, I think the default behaviour is fine TBH

You could remove the text using a "sed" or "replace" command piped on the end of the execi/execpi call if you want to remove it without editing the script

---

### Post by VastOne on 2010-12-04
> **kaivalagi said:**
> Turns out all scripts except the Guayadeque one append "k/s" on the end, if you want to remove it then where's the offending text in red within the exaile script:

```
                        bitrate = iface.GetTrackAttr("__bitrate")
                        if self.isNumeric(bitrate):
                            bitrate = str(int(bitrate)/1024)**[COLOR="Red"]+"k/s"[/COLOR]**
```

I'll not be adding an option to hide/show it I don't think, it's a lot of trouble to go to foe something so trivial, I think the default behaviour is fine TBH

You could remove the text using a "sed" or "replace" command piped on the end of the execi/execpi call if you want to remove it without editing the script

Not one but two solutions...Impressive!

Thanks K!

---

### Post by kaivalagi on 2010-12-09
> **zyghom said:**
> hi Kaivalgi

for the script with Exaile I get continuous errors:

```
SyntaxError: invalid syntax
  File "/home/papio/.conky/scripts/conkyExaile.py", line 46
    self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=TI]. The following are possible options within each item: --datatype,--ratingchar. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
```
 
what is the problem ?

You are running python3...the script works with python2

Run this in the command line:
```
python --version
```

If that is 2.something then run this and post the results:
```
cat /usr/bin/conkyExaile
```

---

### Post by zyghom on 2010-12-09
hi Kaivalgi

for the script with Exaile I get continuous errors:

```
SyntaxError: invalid syntax
  File "/home/papio/.conky/scripts/conkyExaile.py", line 46
    self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=TI]. The following are possible options within each item: --datatype,--ratingchar. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
```

what is the problem ?

---

### Post by kaivalagi on 2010-12-09
> **zyghom said:**
> what is the problem ?
posted response above...

---

### Post by zyghom on 2010-12-09
> **kaivalagi said:**
> posted response above...



```
09:36:03 papio@baboonsony:~$ python --version
Python 3.1.3
09:36:37 papio@baboonsony:~$ 
```

---

### Post by kaivalagi on 2010-12-09
> **zyghom said:**
> ```
09:36:03 papio@baboonsony:~$ python --version
Python 3.1.3
09:36:37 papio@baboonsony:~$ 
```

There's your problem, what is the conkyExaile script contents like?
e.g. run "cat /usr/bin/conkyExaile" and post results, the script should handle this issue unless you haven't updated? How did you install the script?


The latest version of conkyExaile, version 2.14, has this for the /usr/bin script which should handle if /usr/bin/python is linked to python3 as in your case:
```

#! /bin/sh
cd /usr/share/conkyexaile/

pythoncmd="/usr/share/conkyexaile/conkyExaile.py $@"

if [ -f /usr/bin/python2 ]; then
	cmd="/usr/bin/python2 $pythoncmd"
elif [ -f /usr/bin/python2.7 ] ; then
	cmd="/usr/bin/python2.7 $pythoncmd"
elif [ -f /usr/bin/python2.6 ] ; then
	cmd="/usr/bin/python2.6 $pythoncmd"
else
	# here's hoping!
	cmd="/usr/bin/python $pythoncmd"
fi

exec $cmd

```

---

### Post by zyghom on 2010-12-09
actually I'm using this:

[http://gnome-look.org/content/show.php/conky~meet~faenza?content=133086](http://gnome-look.org/content/show.php/conky~meet~faenza?content=133086)

---

### Post by kaivalagi on 2010-12-09
> **zyghom said:**
> actually I'm using this:

[http://gnome-look.org/content/show.php/conky~meet~faenza?content=133086](http://gnome-look.org/content/show.php/conky~meet~faenza?content=133086)

reinstall the script using the instructions in the first post of this thread...

Unfortunately the authors of these packs do not know how to handle deb packages etc and so you have these issues, they should script the install from the repo in thier packages rather than included the scripts themselves...otherwise you get out of date packages easily...it really pees me off to be honest...

---

### Post by zyghom on 2010-12-09
I installed conkyexaile-bzr and ran as in README:

```
09:50:00 papio@baboonsony:~$ conky -c /usr/share/conkyexaile/example/conkyrc
Conky: /usr/share/conkyexaile/example/conkyrc: 47: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (100002b) is subwindow of root window (a9)
Conky: window type - override
Conky: drawing to created window (0x5e00001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 10, in <module>
    from PIL import Image
ImportError: No module named PIL
```

---

### Post by kaivalagi on 2010-12-09
> **zyghom said:**
> I installed conkyexaile-bzr and ran as in README:

```
09:50:00 papio@baboonsony:~$ conky -c /usr/share/conkyexaile/example/conkyrc
Conky: /usr/share/conkyexaile/example/conkyrc: 47: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (100002b) is subwindow of root window (a9)
Conky: window type - override
Conky: drawing to created window (0x5e00001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile.py", line 10, in <module>
    from PIL import Image
ImportError: No module named PIL
```

You running Arch?

PIL / "python-imaging" needs installing...you've gotten further as the script is starting now

Once you get that running you'll need to mess with the other download you did so it can run the script now it is in a different location

---

### Post by zyghom on 2010-12-09
> **kaivalagi said:**
> You running Arch?

PIL / "python-imaging" needs installing...you've gotten further as the script is starting now

Once you get that running you'll need to mess with the other download you did so it can run the script now it is in a different location


yes, Archlinux
after installation of imaging it is OK now - thank you

btw the whole package from gnome site was very nice, otherwise in Arch there are only single packages...

---

### Post by kaivalagi on 2010-12-09
> **zyghom said:**
> yes, Archlinux
after installation of imaging it is OK now - thank you

btw the whole package from gnome site was very nice, otherwise in Arch there are only single packages...

No problems, it is advised to install my scripts from the AUR so if things change you get the benefit, in this case you missed out on the fix to the /usr/bin/conkyExaile bash script to manage the execution of the script via python2. Since python3 was made the norm in Arch i.e. sym linked to /usr/bin/python lots of python2 scripts have been failing

I currently have my sym links changed so lots still works e.g.:
```
~]$ ls /usr/bin/python
lrwxrwxrwx 1 root root 7 Dec  4 16:32 /usr/bin/python -> python2
```

For the default install (and your system) it will be pointing to python3...

Have fun :)

---

### Post by kaivalagi on 2010-12-11
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added use_tag_image_only flag to the GetCover script, if set to true (false by default) only tag images will get used for cover art output
[*]Updated main script to only actually copy over found cover art when --datatype=CA is requested
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.15_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.15_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2010-12-12
**[COLOR=Orange][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Fixed bug with GetCover script due to the tag image flag that was added
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.16_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyexaile_2.16_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2010-12-14
**[COLOR="Red"][SIZE="3"]IMPORTANT NEWS[/SIZE][/COLOR]**

All the script packages have now been copied into the **Conky Companions PPA**. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this: 

```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*

```
Then follow the modified first post instructions for the scripts

[COLOR="Red"]**Script updates will only be published through this new ppa going forwards**[/COLOR]

---

### Post by Sporktacular on 2011-01-14
Hey, loving this so far :)

Unfortunately, I can't seem to get the cover art feature working. I apologise if this has already been fixed before, but I couldn't find anything.
conkyExaile -d CA just returns a newline and conkyExaile-GetCoverart returns a host of errors when the track changes.

```
jonno@capricorn ~/bin/conkyexaile $ ./conkyExaile -d CA

jonno@capricorn ~/bin/conkyexaile $ ./conkyExaile-GetCoverart 
conkyExaile-GetCoverart - Cover art will be copied to '/tmp/exaile-coverart.jpg'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...
Traceback (most recent call last):
  File "/home/jonno/bin/conkyexaile/conkyExaile-GetCoverart.py", line 97, in getCoverartPath
    imgString = "".join(chr(byte) for byte in self.iface.GetCoverData())
  File "/usr/lib64/python2.6/site-packages/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib64/python2.6/site-packages/dbus/connection.py", line 622, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Python.NameError: Traceback (most recent call last):
  File "/usr/lib64/python2.6/site-packages/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib64/exaile/xl/xldbus.py", line 489, in GetCoverData
    cover = covers.MANAGER.get_cover(player.PLAYER.current)
NameError: global name 'player' is not defined

** Track Changed: No cover art images known, Checking for embedded images in audio file...
*** Error: Begin
Traceback (most recent call last):
  File "/home/jonno/bin/conkyexaile/conkyExaile-GetCoverart.py", line 70, in OnTrackChange
    if len(self.getCoverartImage(self.COVERART_DESTINATION)) > 0:
  File "/home/jonno/bin/conkyexaile/conkyExaile-GetCoverart.py", line 110, in getCoverartImage
    if "location" in self.props:
AttributeError: Exaile_GetCoverart instance has no attribute 'props'
*** Error: End
* Listening: waiting for a track change...

```I'm using Gentoo (so I'm no stranger to things not working, at least ;)) so I had to set up from the tgz. I'm not sure if I messed something up on install; I just extracted, changed the paths in the scripts and installed anything that Python moaned about not having.

Oh, and...
```
jonno@capricorn ~/bin/conkyexaile $ python --version
Python 2.6.6

```Thanks for your work so far, if this is a genuine bug and not just my being stupid, I'll do what I can to help :)

---

### Post by kaivalagi on 2011-01-14
Hi Sporktacular

Could you tell me what version of the script and exaile you are running, I am running conkyExaile v.2.16 and Exaile v0.3.3.0-dev. Also do you actually have Exaile running when you use the script? It just looks like the services required are not available to connect to...

If I recall cover art retrieval wasn't running until this version as it only now has the coverart methods provided but I can't quite remember exactly.

I've attached a screenshot of d-feet showing the service interfaces in my version for reference (GetCoverArt is the method required). Might be an idea to install d-feet on your system and see if you see the same interfaces available for exaile, they are needed by the script.

Either method is working for me:

```
[user@system ~]$ **conkyExaile --datatype=CA**
/tmp/cover
 [user@system ~]$ **conkyExaile-GetCoverart**
conkyExaile-GetCoverart - Cover art will be copied to '/tmp/exaile-coverart.jpg'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...
** Track changed: Copying '/tmp/exaile-2630187a-1fed-11e0-9c1b-001a927d44a5.jpg' to '/tmp/exaile-coverart.jpg'
* Listening: waiting for a track change...

```

Although I've noticed the file naming isn't in line between the 2 methods...it needs to ideally be /tmp/cover in the getcover scripts too...

Anyway, let me know more details on versions and we'll take it from there

---

### Post by crownedzero on 2011-01-14
Trying to get album art displayed as well. My first issue was in regards to a python dependency for id tags so I installed the pythoneye3d package. However I'm still not getting the desired results. Here's the terminal display:
```

crownedzero@mobil:~$ conkyExaile --datatype=CA

crownedzero@mobil:~$ conkyExaile-GetCoverart
conkyExaile-GetCoverart - Cover art will be copied to '/tmp/exaile-coverart.jpg'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile-GetCoverart.py", line 97, in getCoverartPath
    imgString = "".join(chr(byte) for byte in self.iface.GetCoverData())
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Python.NameError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/exaile/xl/xldbus.py", line 489, in GetCoverData
    cover = covers.MANAGER.get_cover(player.PLAYER.current)
NameError: global name 'player' is not defined

** Track Changed: No cover art images known, Checking for embedded images in audio file...
*** Error: Begin
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile-GetCoverart.py", line 70, in OnTrackChange
    if len(self.getCoverartImage(self.COVERART_DESTINATION)) > 0:
  File "/usr/share/conkyexaile/conkyExaile-GetCoverart.py", line 110, in getCoverartImage
    if "location" in self.props:
AttributeError: Exaile_GetCoverart instance has no attribute 'props'
*** Error: End
* Listening: waiting for a track change...

```

This first call for a datatype results in a newline whereas the getcoverart appears to work until there is a track change in which I receive errors.

```

crownedzero@mobil:~$ conkyExaile --datatype=TI --verbose
*** INITIAL OPTIONS:
    datatype: TI
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:TI
11 - Rap Phenomenon Feat. Method Man & Redman

```
This appears to be working.

python -V returns 2.6.6
conkyExaile -V returns 2.16
exaile 0.3.2.0-0ubuntu3

Not sure if there's anymore info I can provide on this. Thanks for any responses.

---

### Post by Sporktacular on 2011-01-14
I'm running exaile when I start the script, and if I understand D-Feet correctly, I've managed to find the same thing that you're showing?

My conkyExaile is v2.16 (actually says v.2.16 but I figured that's what it meant :P)
exaile itself is 3.2.0, which is the latest on Gentoo's Portage. I can try compiling the version you use to see if that's the issue? My Linux knowledge is pretty rudimentary so I'm sorry I can't help more.

---

### Post by VastOne on 2011-01-14
For me, to get everything in the scripts to work the way I wanted them to, I had to move up to Exaile 0.3.3.0-dev version.

---

### Post by kaivalagi on 2011-01-14
double post

---

### Post by kaivalagi on 2011-01-14
> **VastOne said:**
> For me, to get everything in the scripts to work the way I wanted them to, I had to move up to Exaile 0.3.3.0-dev version.

If I recall (maybe you can help here VastOne as my memory has walked out on me recently...) didn't we have discussions on this same issue with the older versions before and came to the conclusion that v0.3.2.x just didn't provide cover art info correctly? I just can't remember if it was this or one of the other many music player scripts :D

I think the simple answer anyway if for all those wanting cover art support with this script to get 0.3.3.x installed on your distro's or just wait until 3.3.x is stable and not a dev version...it's working for me and VastOne on different distros (me on Arch, VastOne on a Debian derivative, #! or Ubuntu?)

---

### Post by VastOne on 2011-01-14
> **kaivalagi said:**
> If I recall (maybe you can help here VastOne as my memory has walked out on me recently...) didn't we have discussions on this same issue with the older versions before and came to the conclusion that v0.3.2.x just didn't provide cover art info correctly? I just can't remember if it was this or one of the other many music player scripts :D

I think the simple answer anyway if for all those wanting cover art support with this script to get 0.3.3.x installed on your distro's or just wait until 3.3.x is stable and not a dev version...it's working for me and VastOne on different distros (me on Arch, VastOne on a Debian derivative, #! or Ubuntu?)

I am on Ubuntu and you are correct K, we did determine that the 0.3.3.0-dev was the only version that we got to work correctly and still is the only version that works.  My memory is in the same boat as yours but this on I am crystal clear on

I see by your double post that you are having some of the same issues I am in responding..  Severe lag time once you hit submit..

---

### Post by kaivalagi on 2011-01-14
> **VastOne said:**
> I am on Ubuntu and you are correct K, we did determine that the 0.3.3.0-dev was the only version that we got to work correctly and still is the only version that works.  My memory is in the same boat as yours but this on I am crystal clear on

I see by your double post that you are having some of the same issues I am in responding..  Severe lag time once you hit submit..

That's good to know, I hate having vague memories of some things...good to know there was a reason there was something niggling me in the back of my mind and I am not mad (yet)

And yep, the forum is playing up a little, a lot slower than other sites right now...these VBulletin sites can be rather poor performing but I guess there will be tons of activity...lots of newbie users coming onboard all the time it seems...

---

### Post by VastOne on 2011-01-15
K,

I am getting the following now with the Exaile_GetCoverart


*** Error: Begin
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile-GetCoverart.py", line 70, in OnTrackChange
    if len(self.getCoverartImage(self.COVERART_DESTINATION)) > 0:
  File "/usr/share/conkyexaile/conkyExaile-GetCoverart.py", line 110, in getCoverartImage
    if "location" in self.props:
AttributeError: Exaile_GetCoverart instance has no attribute 'props'
*** Error: End

This is not happening with art work embedded in the files, only on files where there is a jpg in the directory.

Thanks

---

### Post by VastOne on 2011-01-15
dupe

---

### Post by kaivalagi on 2011-01-15
> **VastOne said:**
> K,

I am getting the following now with the Exaile_GetCoverart


*** Error: Begin
Traceback (most recent call last):
  File "/usr/share/conkyexaile/conkyExaile-GetCoverart.py", line 70, in OnTrackChange
    if len(self.getCoverartImage(self.COVERART_DESTINATION)) > 0:
  File "/usr/share/conkyexaile/conkyExaile-GetCoverart.py", line 110, in getCoverartImage
    if "location" in self.props:
AttributeError: Exaile_GetCoverart instance has no attribute 'props'
*** Error: End

This is not happening with art work embedded in the files, only on files where there is a jpg in the directory.

Thanks

Definately wrong, must of got copied from one of the other player scripts by mistake, however looking at it further and there is no means that I can see of getting the file location via the d-bus methods...I can't find a "filename" or "location" attrib etc available to request data from and therefore can't tell the script to search for images in the id3 tags as I can't tell it what the file is...

I've updated the script and attached based on the way it ought to work

Basically this:
```
        # get file apth
        if "location" in self.props:
            location = self.props["location"]
```

has become this:
```
        # get file path
        location = self.iface.GetTrackAttr("filename")
```

---

### Post by Sporktacular on 2011-01-16
I finally got around to downloading 3.3.0-dev and my coverart seems to be working great with that so far.

I'm not sure if this is mentioned anywhere else, but I had to add ```
imlib_cache_size 0
``` to my .conkyrc to get conky to update the image. Might be something to do with my actual template line ```
${image /tmp/exaile-coverart.jpg -s 150x150 -p 40,910}
``` as I wasn't entirely sure how it was supposed to be used.

I'll keep it up for a while and see if I find any problems, although it's a grim reminder of how messy some of the coverart in my collection is :)

Edit:
Upgraded to your new script and it seems to have broken things:
```

* Listening: waiting for a track change...
** Track Changed: No cover art images known, Checking for embedded images in audio file...
**                No image found.
* Listening: waiting for a track change...
** Track Changed: No cover art images known, Checking for embedded images in audio file...
**                No image found.
* Listening: waiting for a track change...
** Track Changed: No cover art images known, Checking for embedded images in audio file...
**                No image found.
* Listening: waiting for a track change...
** Track Changed: No cover art images known, Checking for embedded images in audio file...
**                No image found.
* Listening: waiting for a track change...

```
That's every time I change track, not constant.
The popups seem to be showing the art for the tracks just fine. I'm not positive which of my songs use embedded art and which don't, since WMP decided to throw image files everywhere anyway, but I skipped through enough songs to be fairly sure neither method works for me.

I'll play about with it a little more if I can get 3.3.0 to enqueue songs properly.

---

### Post by VastOne on 2011-01-16
> **Sporktacular said:**
> I finally got around to downloading 3.3.0-dev and my coverart seems to be working great with that so far.

I'm not sure if this is mentioned anywhere else, but I had to add ```
imlib_cache_size 0
``` to my .conkyrc to get conky to update the image. Might be something to do with my actual template line ```
${image /tmp/exaile-coverart.jpg -s 150x150 -p 40,910}
``` as I wasn't entirely sure how it was supposed to be used.

I'll keep it up for a while and see if I find any problems, although it's a grim reminder of how messy some of the coverart in my collection is :)

Good catch on the imlib_cache_size, that is documented through most of K's scripts on each of the different players here.

Your template line looks good... 

You can read through most of these players here in K's scripts as each have basically the same input as the others, so you could be reading something or a Conky setup from Clementine and make it work just as easily with Exaile by putting in the correct paths.

Glad you got it going!

---

### Post by Sporktacular on 2011-01-16
Aha, I didn't realise he'd written so many! I'll take a look through before I start wandering blindly next time ;)

I got it working again by changing use_tag_image_only to False again in conkyExaile-GetCoverart.py, and noticed that the image destination had changed too while I was at it. 

I seem to have fixed it anyways by changing
```

location = self.iface.GetTrackAttr("filename")

```to
```

location = self.iface.GetTrackAttr("__loc")

```after digging around in Exaile a bit. Sorry if this is counter-productive, I'm not much of a programmer but it worked for me.

I've got it working at least part of the time in 3.2.0 with that, so I'm happy enough. Going to throw some ugly hack together to grab jpgs from the file path and hopefully that'll do me until 3.3.0's in Gentoo :P

---

### Post by VastOne on 2011-01-16
> **Sporktacular said:**
> Aha, I didn't realise he'd written so many! I'll take a look through before I start wandering blindly next time ;)

I got it working again by changing use_tag_image_only to False again in conkyExaile-GetCoverart.py, and noticed that the image destination had changed too while I was at it. 

I seem to have fixed it anyways by changing
```

location = self.iface.GetTrackAttr("filename")

```
to
```

location = self.iface.GetTrackAttr("__loc")

```
after digging around in Exaile a bit. Sorry if this is counter-productive, I'm not much of a programmer but it worked for me.

I seem to only be able to get embedded art to work with the current GetCover script, if there is a cover.jpg (pr any other) I get the "no cover art images known", Checking for embedded, No Image found

FYI, d-feet dbus dbugger tool is a pretty awesome one to have in looking directly into the bus sessions to see what is going on..

Just check synaptic for d-feet

Terry

---

### Post by kaivalagi on 2011-01-16
> **Sporktacular said:**
> I seem to have fixed it anyways by changing
```

location = self.iface.GetTrackAttr("filename")

```to
```

location = self.iface.GetTrackAttr("__loc")

```after digging around in Exaile a bit. Sorry if this is counter-productive, I'm not much of a programmer but it worked for me.

Thanks for that' I'll update the package with these changes when I get a chance...I looked and looked, which .py was the __loc in?

---

### Post by Sporktacular on 2011-01-16
D-Feet is how I hunted it down. kaivalagi advised me to install it earlier :)

At least for me, when I use GetTrackAttr("filename") I get an empty string back on 3.3.0 and a None on 3.2.0, but using GetTrackAttr("__loc") I get the full file path as a URI on both. Perhaps I'm not using it properly? I have zero experience with DBus.

I've hacked something together to grab JPGs from the folders which works some of the time for 3.2.0. I'll upload it if you like but it's ugly and hackish. I made it return a blank transparent PNG if everything fails so I at least don't get the last album's coverart.

On the other hand, it works pretty much perfectly out of the box for me when I use 3.3.0 so I may be missing the whole issue.

Edit:
I found __loc in trax/track.py under __register() and decided to try it out in DFeet.

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

