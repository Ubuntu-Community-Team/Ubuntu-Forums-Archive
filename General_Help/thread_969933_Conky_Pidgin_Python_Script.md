---
title: "Conky Pidgin Python Script"
date: 2008-11-03
forum: General Help
---

### Post by kaivalagi on 2008-11-03
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE="3"][COLOR="Blue"]Intro[/COLOR][/SIZE]_**

This is a simple script to display buddy info from Pidgin. The script talks to Pidgin using dbus and allows templates...

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conky<scriptname>/

**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the script: 

```
sudo apt-get update && sudo apt-get install conkypidgin

```

**[COLOR="Blue"]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyPidgin script to point to the correct location where conkyPidgin.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE="3"][COLOR="Blue"]Usage Help[/COLOR][/SIZE]_**

To use the script in conky in it's simplist form, you'll need an exec statement like this:

```
${execi 60 conkyPidgin}
```

To use a template for custom output, I suggest you read the README attached, and take a look at the example conkyrc and template files that are installed to "/usr/share/conkypidgin/example".

You can get the current help options at any time by running:

```

conkyPidgin -h

```

or

```

conkyPidgin --help

```

```
Usage: conkyPidgin [options]
Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        Template file determining the format for each buddy's
                        data or account info. Use the following placeholders
                        for default buddy output: [name], [alias], [group],
                        [status], [status_message]. If outputting an account
                        listing use these placeholders: [name], [protocol],
                        [status]
  -L, --accountlisting  Show account listing with status rather than buddies
  -o, --onlineonly      Only show online buddies. If outputting account
                        listings this option limits it to enabled only.
  -a, --availableonly   Only show available buddies. If outputting account
                        listings this option limits it to enabled only.
  -f, --offlineonly     Only show offline buddies. If outputting account
                        listings this option limits it to disabled only.
  -i LIST, --ignorelist=LIST
                        A comma delimited list of groups to ignore. Partial
                        text matches on group will be ignored if found
  -I LIST, --includelist=LIST
                        A comma delimited list of groups to include. Partial
                        text matches on group will be included if found. The
                        ignorelist, if used, takes precedence. if this list is
                        omitted all groups will be included unless ignored.
  -C TEXT, --chattingtext=TEXT
                        [default: Chatting] Text to use for chatting status
                        output
  -A TEXT, --availabletext=TEXT
                        [default: Available] Text to use for available status
                        output
  -U TEXT, --unavailabletext=TEXT
                        [default: Unavailable] Text to use for unavailable
                        status output
  -N TEXT, --invisibletext=TEXT
                        [default: Invisible] Text to use for invisible status
                        output
  -W TEXT, --awaytext=TEXT
                        [default: Away] Text to use for away status output
  -M TEXT, --mobiletext=TEXT
                        [default: Mobile] Text to use for mobile status output
  -F TEXT, --offlinetext=TEXT
                        [default: Offline] Text to use for offline status
                        output
  -l NUMBER, --limit=NUMBER
                        [default: 0] Set a limit to the number of buddies
                        displayed, by default no limitation is made
  -s, --sortbylogactivity
                        If used the list is sorted by most recent activity
                        first, this is useful when limiting the list size with
                        the limit option
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

**_[SIZE="3"][COLOR="Blue"]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkypidgin"]https://code.launchpad.net/~conky-companions/+junk/conkypidgin
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by abrussak on 2008-11-03
I looked at your repos and saw no pidgin version for hardy...are you going to write one? :) Cause that would be awesome :)

---

### Post by kaivalagi on 2008-11-03
> **abrussak said:**
> I looked at your repos and saw no pidgin version for hardy...are you going to write one? :) Cause that would be awesome :)

Nope, all intrepid from now on in...

If you follow the instructions it will work in hardy though ;)

I just labelled every up as intrepid because there may be code I develop that won't work in hardy anymore....for now though all my scripts are fine in hardy. They are python based so should be fine for some time (until hardy is well out of date, i.e. python 2.5 is obsolete)

---

### Post by abrussak on 2008-11-03
If a buddy has an away message, I see the HTML code.

---

### Post by cl0ckwork on 2008-11-04
conky is just so useful :guitar:

---

### Post by loomsen on 2008-11-04
Oh nice, that's what I supposed to do the next few days^^

Now that saves me a lot of time, thx buddy :)

---

### Post by kaivalagi on 2008-11-04
> **abrussak said:**
> If a buddy has an away message, I see the HTML code.

I'll take a look, just need to strip all html away I think...

---

### Post by kaivalagi on 2008-11-04
[COLOR="DarkGreen"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

Fixed in 2.02, html should no longer be present in any status message text

The first post has been updated and the new version (2.02) is available via apt too

Chimo

---

### Post by slinkey1981 on 2008-11-06
What could be causing the name of the last person on my list to have their screen name cut off and their status missing?

My Conky

```
#Conky Configuration File
maximum_width 300
background yes
border_width 1
cpu_avg_samples 3
default_color light grey
default_outline_color light grey
default_shade_color light grey
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont 
xftalpha 0.5
gap_x 3
gap_y 40
minimum_size 5 5
net_avg_samples 1
no_buffers yes
out_to_console no
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 3
update_interval 2
uppercase yes
use_spacer left
alignment top_right
double_buffer yes

TEXT

${color db7835}${font Capture it:size=17}System Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}OS: ${color light grey}${alignr}Ubuntu 8.04 Hardy Heron
${color dark grey}Kernal: ${color light grey}${alignr}$sysname $kernel 
${color dark grey}User: ${color light grey}${alignr}Shifty@$nodename

${color dark grey}Uptime:$alignr ${offset 10}${color dark red}${font Capture it:25} $uptime
${alignr}${color db7835}${time %H:%M}/23:59

${color db7835}${font Capture it:size=17}Hardware Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}CPU Make:$alignr ${color light grey}Intel Celeron
${color dark grey}CPU Frequency:$alignr ${color light grey}$freq MhZ
${color dark grey}CPU Temp:$alignr ${color light grey} ${acpitemp}${color light grey}.C
${color dark grey}GPU Temp:$alignr ${color light grey} ${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}.C
${color dark grey}Video RAM:$alignr ${color light grey} ${exec nvidia-settings -q VideoRam | grep Attribute | cut -d ' ' -f 6 | cut -c 1-6} KiB

${color db7835}${font Capture it:size=17}CPU/RAM Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}CPU: ${color light grey}$alignr ${cpu}%
${color light grey}${cpubar 7,300}
${color dark grey}RAM: ${color light grey}$alignr $memperc% ${color light grey}
${color light grey}${membar 7,300}

${color db7835}${font Capture it:size=17}Storage Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}Home $alignr ${color light grey}${fs_free /}/${fs_size /} 
${color light grey}${fs_bar 7,300 /}
${color dark grey}MediaShare $alignr ${color light grey}${fs_free /mnt/MediaShare}/${fs_size /mnt/MediaShare}
${color light grey}${fs_bar 7,300 /mnt/MediaShare}

${color db7835}${font Capture it:size=17}Network Info${voffset -4}${stippled_hr 4}${color dark grey}
${color gray}${font Hardkaze:size=10}Local IP:${color light grey}${alignr}${addr eth0}
${color dark grey}Internet IP:${color light grey}${alignr}${pre_exec wget -O - http://ip.tupeux.com | tail}
${downspeedgraph eth0 38,145 969400 1c5c00} ${alignr}${upspeedgraph eth0 38,145 969400 830000} 
${voffset -45}${color dark grey}Down:${color light grey}${downspeedf eth0}Kbps${color dark grey}${alignr}Up:${color light grey}${upspeedf eth0}Kbps${color dark grey}
${color dark grey}Down: ${color light grey}${totaldown eth0} ${color dark grey}${alignr}Up: ${color light grey}${totalup eth0}

${color db7835}${font Capture it:size=17}Online Friends${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}${execpi 60 conkyPidgin -o --template=/usr/share/conkypidgin/example/conkyPidgin.template}
```

My conkyPidgin

```
<alias>${alignr}${color white}<status>${color dark grey}
```

---

### Post by HippyRandall on 2008-11-06
> **slinkey1981 said:**
> What could be causing the name of the last person on my list to have their screen name cut off and their status missing?
add this above TEXT:

```
text_buffer_size 2048 # use 1024 for the forecast
```

---

### Post by HyperHacker on 2008-11-07
Nice. It could really use an "ignore group" option though instead of just individual buddies, and sort the buddies within the groups instead of only by group.

Also, modified to be able to change the "Online" and "Offline" strings with -O and -F or --onlinestring and --offlinestring:```
#!/usr/bin/python
# -*- coding: utf-8 -*-
###############################################################################
# conkyPidgin.py is a simple python script to display 
# details of pidgin buddies, for use in conky.
#
#  Author: Kaivalagi
# Created: 03/11/2008
# Modifications:
#    03/11/2008    Added --onlineonly option to only show online buddies in the list
#    03/11/2008    Added --ignorelist to handle ignoring unwanted pidgin buddy output
#    03/11/2008    Added --includelist to handle including only wanted pidgin buddy output
#    03/11/2008    Updated to handle buddy group and status_messages
#    03/11/2008    Updated to display a status of "Chatting" when the buddy is messaging

#    04/11/2008    Status message Now html striped from the text

import sys, traceback
try:
    import dbus
    DBUS_AVAIL = True
except ImportError:
    # Dummy D-Bus library
    class _Connection:
        get_object = lambda *a: object()
    class _Interface:
        __init__ = lambda *a: None
        ListNames = lambda *a: []
    class Dummy: pass
    dbus = Dummy()
    dbus.Interface = _Interface
    dbus.service = Dummy()
    dbus.service.method = lambda *a: lambda f: f
    dbus.service.Object = object
    dbus.SessionBus = _Connection
    DBUS_AVAIL = False

import re
from htmlentitydefs import name2codepoint
from optparse import OptionParser

class CommandLineParser:

    parser = None

    def __init__(self):

        self.parser = OptionParser()
        self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"Template file determining the format for each buddy's data. Use the following placeholders: <name>, <alias>, <group>, <status>, <status_message>.")
        self.parser.add_option("-o", "--onlineonly", dest="onlineonly", default=False, action="store_true", help=u"Only show online buddies")
        self.parser.add_option("-i", "--ignorelist", dest="ignorelist", type="string", metavar="LIST", help=u"A comma delimited list of names or aliases to ignore. Partial text matches on name or alias will be ignored if found")
        self.parser.add_option("-I", "--includelist", dest="includelist", type="string", metavar="LIST", help=u"A comma delimited list of names or aliases to include. Partial text matches on name or alias will be included if found. The ignorelist, if used, takes precedence. if this list is omitted all buddies will be included unless ignored.")
        self.parser.add_option("-v", "--verbose", dest="verbose", default=False, action="store_true", help=u"Request verbose output, not a good idea when running through conky!")
        self.parser.add_option("-V", "--version", dest="version", default=False, action="store_true", help=u"Displays the version of the script.")
        self.parser.add_option("-O", "--onlinestring", dest="onlinestring", type="string", metavar="string", help=u"String for \"Online\"")
	self.parser.add_option("-F", "--offlinestring", dest="offlinestring", type="string", metavar="string", help=u"String for \"Offline\"")

    def parse_args(self):
        (options, args) = self.parser.parse_args()
        return (options, args)

    def print_help(self):
        return self.parser.print_help()

class BuddyData:
    def __init__(self, name, alias, group, status, status_message):
        self.name = name
        self.alias = alias
        self.group = group
        self.status = status
        self.status_message = status_message

    def __cmp__(self, other):
        return cmp(self.group, other.group)
    
    def __str__(self):
        return str(self.name+"("+self.alias+")")
        
class ConkyPidgin:
    
    def __init__(self, options):
        self.options = options
        
    def testDBus(self, bus, interface):
        obj = bus.get_object('org.freedesktop.DBus', '/org/freedesktop/DBus')
        dbus_iface = dbus.Interface(obj, 'org.freedesktop.DBus')
        avail = dbus_iface.ListNames()
        return interface in avail

    def getTemplateOutput(self, template, name, alias, group, status, status_message):
        
        try:
            
            output = template
    
            output = output.replace("<name>",name)
            output = output.replace("<alias>",alias)
            output = output.replace("<group>",group)
            output = output.replace("<status>",status)
            output = output.replace("<status_message>",status_message)

            # get rid of any excess crlf's
            output = output.rstrip(" \n")
            
            return output
        
        except Exception,e:
            self.logError("getTemplateOutput:Unexpected error:" + e.__str__())
            return ""
    
    def getbuddyData(self):
        
        buddyDataList = []
        
        try:
                
            bus = dbus.SessionBus()

            if self.testDBus(bus, 'im.pidgin.purple.PurpleService'):
                
                    self.logInfo("Setting up dbus interface")
                    
                    remote_object = bus.get_object("im.pidgin.purple.PurpleService","/im/pidgin/purple/PurpleObject")
                    iface = dbus.Interface(remote_object, "im.pidgin.purple.PurpleService")
                    
                    self.logInfo("Calling dbus interface for IM data")
                        
                    # Iterate through every active account
                    for acctID in iface.PurpleAccountsGetAllActive():
                        
                        # get all the buddies associated with that account
                        buddies = iface.PurpleFindBuddies(acctID,"")

                        for buddyid in buddies:
                            
                            # get initial data
                            alias = iface.PurpleBuddyGetAlias(buddyid)
                            name = iface.PurpleBuddyGetName(buddyid)
                            online = iface.PurpleBuddyIsOnline(buddyid)
                            
                            if self.ignoreBuddy(name, alias) == False:

                                if self.includeBuddy(name, alias) == True:
                                    
                                    # determine whether to show this buddies details
                                    if online == 1 or self.options.onlineonly == False:
                                        
                                        # get all the extra details we want
                                        groupid = iface.PurpleBuddyGetGroup(buddyid)
                                        group = iface.PurpleGroupGetName(groupid)

					if self.options.onlinestring == None:
						self.options.onlinestring = "Online"
					if self.options.offlinestring == None:
						self.options.offlinestring = "Offline"
                                                                                
                                        if online == 1:
                                            status = self.options.onlinestring
                                        else:
                                            status = self.options.offlinestring
                                        
                                        # status message
                                        presenceid = iface.PurpleBuddyGetPresence(buddyid)
                                        statusid = iface.PurplePresenceGetActiveStatus(presenceid)
                                        status_message = self.getCleanText(iface.PurpleStatusGetAttrString(statusid, "message")) # needed for google encoded text
                                        
                                        if self.isBuddyChatting(name,iface):
                                            status = "Chatting"

                                        buddyData = BuddyData(name, alias, group, status, status_message)
                                        buddyDataList.append(buddyData)

                    # tidy up
                    del iface
                    del remote_object
                    del bus
            
            # sort by group
            buddyDataList.sort()
            
            return buddyDataList
                
        except Exception, e:
            self.logError("Issue calling the dbus service:"+e.__str__())
        
    def getOutputText(self):
        
        if self.options.template == None:
            
            # create default template
            template = "<alias> (<group>) - <status>\n\t<status_message>"
        else:
            # load the template file contents
            try:
                fileinput = open(self.options.template)
                template = fileinput.read()
                fileinput.close()
            except:
                self.logError("Template file no found!")
                sys.exit(2)

        try:
                
            buddyDataList = self.getbuddyData()
            
            for buddyData in buddyDataList:
                
                # output pidgin buddy data using the template
                output = self.getTemplateOutput(template, buddyData.name, buddyData.alias, buddyData.group, buddyData.status, buddyData.status_message)
                print output.encode("utf-8")
        
        except SystemExit:
            self.logError("System Exit!")
            return u""
        except Exception, e:
            traceback.print_exc()
            self.logError("Unknown error when calling getOutputText:" + e.__str__())
            return u""

    def isBuddyChatting(self,name,iface):
        imids = iface.PurpleGetIms()
        for imid in imids:
            convname = iface.PurpleConversationGetName(imid)
            if convname == name:
                return True
            
        return False
    
    def ignoreBuddy(self, name, alias):
        
        if self.options.ignorelist != None:
                    
            # for each text in the ignore list, should we be ignoring the buddy
            for ignore in self.options.ignorelist.split(","):
                # has the buddy been found in the list item
                if name.find(ignore) != -1 or alias.find(ignore) != -1:
                    return True
        
            return False
        
        else:
            return False

    def includeBuddy(self, name, alias):
        
        if self.options.includelist != None:
            
            # for each text in the ignore list, should we be ignoring the buddy
            for include in self.options.includelist.split(","):
                # has the buddy been found in the list item
                if name.find(include) != -1 or alias.find(include) != -1:
                    return True
        
            return False
        
        else:
            return True

    def getCleanText(self,text):
        text = text.replace("&apos;","'") # workaround for shitty xml codes not compliant with html
        text = re.sub('<(.|\n)+?>','',text) # remove any html tags
        return re.sub('&(%s);' % '|'.join(name2codepoint), lambda m: chr(name2codepoint[m.group(1)]), text)
                   
    def logInfo(self, text):
        if self.options.verbose == True:
            print >> sys.stdout, "INFO: " + text
    
    def logError(self, text):
        print >> sys.stderr, "ERROR: " + text
        self.error = self.error + "ERROR: " + text + "\n"
        self.errorfound = True
        
if __name__ == "__main__":
    
    parser = CommandLineParser()
    (options, args) = parser.parse_args()

    if options.version == True:
        print >> sys.stdout,"conkyPidgin v.2.02"
    else:
        if options.verbose == True:
            print >> sys.stdout,"*** INITIAL OPTIONS:"
            print >> sys.stdout,"    template:", options.template
            print >> sys.stdout,"    onlineonly:", options.onlineonly
            print >> sys.stdout,"    ignorelist:", options.ignorelist
            print >> sys.stdout,"    verbose:", options.verbose
            
        conkyPidgin = ConkyPidgin(options)
        conkyPidgin.getOutputText()
    

```

---

### Post by kaivalagi on 2008-11-07
> **HyperHacker said:**
> Nice. It could really use an "ignore group" option though instead of just individual buddies, and sort the buddies within the groups instead of only by group.

Also, modified to be able to change the "Online" and "Offline" strings with -O and -F or --onlinestring and --offlinestring


All good suggestions, I'll take a look at the weekend.[COLOR="Blue"] Edit: Alright so I've done it in 30 minutes before going to work :)[/COLOR]

The includelist and ignorelist options can easily be used for groups instead.

I assume you want to set custom strings of online/offline status so you can use custom fonts and display symbols instead?

---

### Post by kaivalagi on 2008-11-07
[COLOR="Red"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

Changes below:

[LIST]
[*]Updated --ignorelist and --includelist options to be based on group names rather than buddy names, not case sensitive now either
[*]Added --onlinetext, --offlinetext and --chattingtext options to set custom text for status output
[*]Updated README
[/LIST]

The first post is updated and the apt package will be available shortly

Chimo

---

### Post by HyperHacker on 2008-11-07
Cool. It won't ignore a group named "It's-a Me", though. (I did escape the space, and it ignores other groups with apostrophes in their names.)

---

### Post by kaivalagi on 2008-11-09
> **HyperHacker said:**
> Cool. It won't ignore a group named "It's-a Me", though. (I did escape the space, and it ignores other groups with apostrophes in their names.)

Did you put the group name in quotes e.g.

```
--ignorelist="It's-a Me"
```

I have just tried it and it's fine.

You could also just use "me"...as it will remove partial matches too

Hope that helps

---

### Post by kaivalagi on 2008-11-09
[COLOR="Cyan"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I've updated the script slightly, as follows:

[LIST]
[*]Updated sorting to not be case sensitive and be ordered by status (chatting, online then offline), group then alias
[*]Added webdings font to package and used for status output in example template
[/LIST]

The first post has been updated and the apt package is available

Chimo

---

### Post by kaivalagi on 2008-11-10
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Added --errorlog and --infolog options to log data to a file
[*]Refactored and tidied up
[*]Updated README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by cl0ckwork on 2008-11-10
seem to be having a problem. my setup seems to get cut off...
[IMG]http://i278.photobucket.com/albums/kk101/clockwork_kills/Screenshot-1-1.png[/IMG]

i already have my text buffer set at 2049
i know that it has stretched off the bottom of my screen before, but recently updated to the current one and its stops. maybe my max size is out of whack?

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Terminus:size=10
#xftfont zekton:size=9

# Text alpha when using Xft
xftalpha 1

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 5
maximum_width 400

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# colours
color1 white
# light blue
color2 6892C6
# orange
color3 E77320
# green
color4 78BF39
# red
color5 CC0000
# yellow
color6 FEB212

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 40

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)

text_buffer_size 2048

# stuff after 'TEXT' will be formatted on screen

#
#$color ${if_running rhythmbox}${execp conkyRhythmbox --template=/home/clockwork/.conkyscripts/conkyRhythmbox.template}${hr 2}${else}${font tengwar annatar:size=10}pouiduf poudaf piugf afioh${endif}
TEXT
${color gold}${font Terminus:style=Bold:size=14}@ ${font Space Age:size=14}Pidgin${font}
${execpi 60 conkyPidgin --template=/home/clockwork/.conkyscripts/conkyPidgin.template --onlineonly --onlinetext=a --offlinetext=r --chattingtext=q --ignorelist=AIM Bots}
```

---

### Post by kaivalagi on 2008-11-10
> **cl0ckwork said:**
> seem to be having a problem. my setup seems to get cut off...
[IMG]http://i278.photobucket.com/albums/kk101/clockwork_kills/Screenshot-1-1.png[/IMG]

i already have my text buffer set at 2049
i know that it has stretched off the bottom of my screen before, but recently updated to the current one and its stops. maybe my max size is out of whack?

You have too many online friends :)

What happens when you run the script in the terminal, do you see everything you'd expect?

Try increasing your text buffer some more?

---

### Post by cl0ckwork on 2008-11-10
:lolflag: i guess i gotta cut back on my social life :)

took out part of the options and increases the text buffer to 4096.
much better

**Edit**: it wont let me ignore more than 2 groups?

**Re-Edit**:just used the includelist option for now

---

### Post by kaivalagi on 2008-11-11
> **cl0ckwork said:**
> :lolflag: i guess i gotta cut back on my social life :)

took out part of the options and increases the text buffer to 4096.
much better

**Edit**: it wont let me ignore more than 2 groups?

**Re-Edit**:just used the includelist option for now

there is a limit to the length of text used in all the options, try using -i instead of --ignorelist, that might help.

---

### Post by cl0ckwork on 2008-11-11
is there anyway to include the mobile buddies as an offline group?
that may be the reason why it shows so many buddies.
i never talk to them on their phone anyways.

---

### Post by kaivalagi on 2008-11-11
> **cl0ckwork said:**
> is there anyway to include the mobile buddies as an offline group?
that may be the reason why it shows so many buddies.
i never talk to them on their phone anyways.

Mobile Buddies - please enlighten me...

If they are one group just use --ignorelist?

---

### Post by cl0ckwork on 2008-11-11
> **kaivalagi said:**
> Mobile Buddies - please enlighten me...

If they are one group just use --ignorelist?

they are still separated into the different buddies group, but instead of going away or signing off the go "mobile" and all messages sent to them are forwarded to their mobile phone.

it might be just a specific AIM thing, but i believe thats why so many of my buddies are showing up as online

---

### Post by kaivalagi on 2008-11-11
> **cl0ckwork said:**
> they are still separated into the different buddies group, but instead of going away or signing off the go "mobile" and all messages sent to them are forwarded to their mobile phone.

it might be just a specific AIM thing, but i believe thats why so many of my buddies are showing up as online

Nope, sorry, I had a look at the api and there is nothing exposed to tell me whether an online buddy is available via mobile...so I can't account for it

Does pidgin tell you thin somehow? Is it in the status message? If it is then I can possibly determine it from the text......maybe

Can you provide a screen of of an example output with the script?

---

### Post by cl0ckwork on 2008-11-11
sorry, no help with the script it doesnt show andything.
pidgin just shows a picture of a phone when a buddy goes mobile, although pidgin does list them as available.

would it be possible to make buddies that are away have a different status symbol?

---

### Post by kaivalagi on 2008-11-12
> **cl0ckwork said:**
> sorry, no help with the script it doesnt show andything.
pidgin just shows a picture of a phone when a buddy goes mobile, although pidgin does list them as available.

would it be possible to make buddies that are away have a different status symbol?

I tracked down the status data, away/mobile etc is all there...

I have something rudimentary working now, once I have fixed it up, **would you mind testing it**....I have no buddies with a mobile status ever (no AIM)

Chimo

---

### Post by cl0ckwork on 2008-11-12
no problem, just let me know what to do

---

### Post by kaivalagi on 2008-11-12
[COLOR="Green"]**TEST SCRIPT, ONLY USE IF YOU KNOW WHAT YOU@RE DOING**[/COLOR]

The test script to handle all the extra statuses is attached.

To test, extract the file and place it somewhere, then run the script in conky as follows:

```
${execpi 60 python /path/to/py/file/conkyPidgin.py ... options ...}
```

You could run it in the terminal to get verbose info out, which can help a lot:

```
python /path/to/py/file/conkyPidgin.py -v ... options ...
```

The options available are listed below. I added the text options for all the shown statuses and also added an --availableonly option, to only show people that are available to chat...I think that might be what you're after

Have a tinker with all the options and let me know how you get on, I don't know whether the 'mobile' status will be handled properly, so testing that is important. If you have any more suggestions, then speak up :)

If all is okay I'll update the example conkyrc for the installer then package everything up and roll it out :)

```
Usage: conkyPidgin.py [options]

Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        Template file determining the format for each buddy's
                        data. Use the following placeholders: <name>, <alias>,
                        <group>, <status>, <status_message>.
  -o, --onlineonly      Only show online buddies
  -a, --availableonly   Only show available buddies
  -i LIST, --ignorelist=LIST
                        A comma delimited list of groups to ignore. Partial
                        text matches on group will be ignored if found
  -I LIST, --includelist=LIST
                        A comma delimited list of groups to include. Partial
                        text matches on group will be included if found. The
                        ignorelist, if used, takes precedence. if this list is
                        omitted all groups will be included unless ignored.
  -C TEXT, --chattingtext=TEXT
                        [default: Chatting] Text to use for chatting status
                        output
  -A TEXT, --availabletext=TEXT
                        [default: Available] Text to use for available status
                        output
  -U TEXT, --unavailabletext=TEXT
                        [default: Unavailable] Text to use for unavailable
                        status output
  -N TEXT, --invisibletext=TEXT
                        [default: Invisible] Text to use for invisible status
                        output
  -W TEXT, --awaytext=TEXT
                        [default: Away] Text to use for away status output
  -M TEXT, --mobiletext=TEXT
                        [default: Mobile] Text to use for mobile status output
  -F TEXT, --offlinetext=TEXT
                        [default: Offline] Text to use for offline status
                        output
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

---

### Post by cl0ckwork on 2008-11-12
when running it through the terminal, i get no errors but it doesnt display buddies as mobile.
-availableonly option works, shows only those online and not away
buddies show up as away when they are away

all status text options work accordingly (with the exception to being mobile)
i dont have too many friends on MSN or Yahoo etc. so i could not tell if the invisible option was working

when running the script in conky, starting through the command line gives me this error
```
Traceback (most recent call last):
  File "/home/clockwork/conkyPidgin.py", line 280, in writeOutput
    print output.encode("utf-8")
IOError: [Errno 32] Broken pipe
ERROR: Unknown error when calling writeOutput:[Errno 32] Broken pipe

```

it seems to be running fine on my desktop other than that.

oh. and i realized i need a longer desktop.... my conky is running off the bottom with my list of buddies!!

but using the available only option did cut back on the list quite a bit

thank you :guitar:

---

### Post by kaivalagi on 2008-11-12
> **cl0ckwork said:**
> when running it through the terminal, i get no errors but it doesnt display buddies as mobile.
-availableonly option works, shows only those online and not away
buddies show up as away when they are away

all status text options work accordingly (with the exception to being mobile)
i dont have too many friends on MSN or Yahoo etc. so i could not tell if the invisible option was working

when running the script in conky, starting through the command line gives me this error
```
Traceback (most recent call last):
  File "/home/clockwork/conkyPidgin.py", line 280, in writeOutput
    print output.encode("utf-8")
IOError: [Errno 32] Broken pipe
ERROR: Unknown error when calling writeOutput:[Errno 32] Broken pipe

```

it seems to be running fine on my desktop other than that.

oh. and i realized i need a longer desktop.... my conky is running off the bottom with my list of buddies!!

but using the available only option did cut back on the list quite a bit

thank you :guitar:

Can you run the command in the terminal with the verbose option, the output from that should tell me what status text is used for people in "mobile" mode

e.g.

python /home/clockwork/conkyPidgin.py -v

---

### Post by cl0ckwork on 2008-11-12
ran it as verbose, just reports the buddy as available

---

### Post by kaivalagi on 2008-11-12
> **cl0ckwork said:**
> ran it as verbose, just reports the buddy as available

You should have something like below output when in verbose mode:

```

INFO: Adding IM data for buddy 'Michael', status type 'offline' -> status text 'Offline'
```

I need to see that for a buddy with the "mobile" state, to understand what status type the "mobile" mode is actually interpreted as...

The equivalent to the "status type 'offline'" part above

---

### Post by cl0ckwork on 2008-11-12
this is all it shows for a currently mobile buddy
```
INFO: Found status type 'available' for buddy 'sara', using the status text 'Available'
```

---

### Post by kaivalagi on 2008-11-12
> **cl0ckwork said:**
> this is all it shows for a currently mobile buddy
```
INFO: Found status type 'available' for buddy 'sara', using the status text 'Available'
```

Not what I expected at all, pidgin has a status type for mobile, maybe it's not being used in these situations...

Not much I can do, unless I have a buddy which has a mobile state, then maybe I can debug the API and set if anything will help.

---

### Post by cl0ckwork on 2008-11-12
i would offer to help but im not too hot with python...

---

### Post by kaivalagi on 2008-11-13
[COLOR="Green"]**[SIZE="5"]UPDATE[/SIZE]**[/COLOR]

Updated the script, the following has been done:

[LIST]
[*]Updated to now handle available, unavailable, invisible, away and mobile statuses. All have their own text options for output.
[*]Added --availableonly option to only show available buddies
[*]Updated example to use new status formatting options
[*]Updated README
[/LIST]

[COLOR="Red"]**[SIZE="2"]Note: Any existing use of the --onlinetext / -O option will break, new options should be used.[/SIZE]**[/COLOR]

The options for setting the text output are now:

```
  -C TEXT, --chattingtext=TEXT
                        [default: Chatting] Text to use for chatting status
                        output
  -A TEXT, --availabletext=TEXT
                        [default: Available] Text to use for available status
                        output
  -U TEXT, --unavailabletext=TEXT
                        [default: Unavailable] Text to use for unavailable
                        status output
  -N TEXT, --invisibletext=TEXT
                        [default: Invisible] Text to use for invisible status
                        output
  -W TEXT, --awaytext=TEXT
                        [default: Away] Text to use for away status output
  -M TEXT, --mobiletext=TEXT
                        [default: Mobile] Text to use for mobile status output
  -F TEXT, --offlinetext=TEXT
                        [default: Offline] Text to use for offline status
                        output
```

The first post has been updated and the apt package is available too.

Chimo

---

### Post by hachel on 2008-11-14
hello,
when i type conkyPidgin -o into the terminal it tells me this:
```
conkyPidgin -o
ERROR: Issue calling the dbus service:local variable 'status' referenced before assignment
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 271, in writeOutput
    for pidginData in pidginDataList:
TypeError: 'NoneType' object is not iterable
ERROR: Unknown error when calling writeOutput:'NoneType' object is not iterable
```
whats up with that?

---

### Post by kaivalagi on 2008-11-14
> **hachel said:**
> hello,
when i type conkyPidgin -o into the terminal it tells me this:
```
conkyPidgin -o
ERROR: Issue calling the dbus service:local variable 'status' referenced before assignment
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 271, in writeOutput
    for pidginData in pidginDataList:
TypeError: 'NoneType' object is not iterable
ERROR: Unknown error when calling writeOutput:'NoneType' object is not iterable
```
whats up with that?

Is Pidgin running?

---

### Post by hachel on 2008-11-14
yes, when I do it without -o or with an -a instead it works as it should

---

### Post by kaivalagi on 2008-11-14
> **hachel said:**
> yes, when I do it without -o or with an -a instead it works as it should

I think the status type isn't being found for a buddy, it works fine for me.

Can you run it in the terminal again like so:

```
conkyPidgin -o -v
```

And then post what you get please. I need to see something like this to determine the statustype coming back:

```
INFO: Adding IM data for buddy 'Mark (MSN)', status type 'available' -> status text 'Available'
INFO: Adding IM data for buddy 'Greg', status type 'available' -> status text 'Available'
```

Thanks

---

### Post by hachel on 2008-11-15
this is what i get, nothing new...
```
$ conkyPidgin -o -v
*** INITIAL OPTIONS:
    template: None
    onlineonly: True
    availableonly: False
    ignorelist: None
    includelist: None
    chattingtext: Chatting
    availabletext: Available
    unavailabletext: Unavailable
    invisibletext: Invisible
    awaytext: Away
    mobiletext: Mobile
    offlinetext: Offline
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Setting up dbus interface
INFO: Calling dbus interface for IM data
ERROR: Issue calling the dbus service:local variable 'status' referenced before assignment
INFO: Outputting buddy information...
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 271, in writeOutput
    for pidginData in pidginDataList:
TypeError: 'NoneType' object is not iterable
ERROR: Unknown error when calling writeOutput:'NoneType' object is not iterable

```
thanks so far

---

### Post by kaivalagi on 2008-11-15
it's as if pidgin tells the script no one is online...so with -o nothing is populated in the list

What messenger service are you using?

---

### Post by hachel on 2008-11-15
both msn and icq
it does list contacts from both services when I use the -a option

---

### Post by castironpants on 2008-11-16
I'd really just like to see a conky pidgin script that informs me of unread messages. I'm cool with just having the buddy list up if I need to see who's online, but I'm always missing unread IMs. Any way to have the script do that?

---

### Post by kaivalagi on 2008-11-16
I'm sure there will be a way, I'll do some digging in a while. I have another project I am working on at the moment which needs my full attention though.

[COLOR="Blue"]Edit: The "chatting" status sort of does that doesn't it? Maybe I am not understanding you here...[/COLOR]

---

### Post by tvich on 2008-11-18
Same problem as hachel.
Today I noticed my conky window was not populated with pidgin contacts (It was just fine the day before)
This is the call in .conkyrc
```
${color #e9c703}IM ${hr 2}$color
$color${execpi 60 conkyPidgin -o -t /home/my_username/scripts/conky/template-pidgin}

```
and this is my template in /home/my_username/scripts/conky/template-pidgin
```
<alias>${alignr}<status>

```
I restarted the box and my conky IM field was still empty. I first ran conky from the terminal and then conkypidgin with verbose and got the same error message as hachel. 
I then ran ''apt-get --purge remove conkypidgin conky pidgin'' and then reinstalled everything. The problem was still there. I thought that maybee there is something wrong with pidgin's msn. So I ran
```
apt-get install msn-pecan
``` and disabled my MSN account in pidgin and created a new account with msn-pecan called ''WLM''. Everything works now.

8.10 x64
Intel CPU
I use pidgin for MSN only.

---

### Post by kaivalagi on 2008-11-18
> **tvich said:**
> Same problem as hachel.
Today I noticed my conky window was not populated with pidgin contacts (It was just fine the day before)
This is the call in .conkyrc
```
${color #e9c703}IM ${hr 2}$color
$color${execpi 60 conkyPidgin -o -t /home/fran/scripts/conky/template-pidgin}

```
and this is my template in /home/my_username/scripts/conky/template-pidgin
```
<alias>${alignr}<status>

```
I restarted the box and my conky IM field was still empty. I first ran conky from the terminal and then conkypidgin with verbose and got the same error message as hachel. 
I then ran ''apt-get --purge remove conkypidgin conky pidgin'' and then reinstalled everything. The problem was still there. I thought that maybee there is something wrong with pidgin's msn. So I ran
```
apt-get install msn-pecan
``` and disabled my MSN account in pidgin and created a new account with msn-pecan called ''WLM''. Everything works now.

8.10 x64
Intel CPU
I use pidgin for MSN only.

What's confusing me is that I have no issues with my hotmail msn based IM buddies, I can't reproduce the problem.

I'll check to see whether I have msn-pecan installed....:confused:

---

### Post by kaivalagi on 2008-11-19
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Now loading the template file in unicode mode to allow for the extended character set
[*][SIZE="4"]**[COLOR="Red"]Changed option tags from <...> to [...][/COLOR]**[/SIZE], so <alias> now needs to be [alias] in the template to work
[*]Updated example template and README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by hachel on 2008-11-25
great stuff, it works now with the new update.
Just on thing: under synaptic conkyPidgin is listed as 2.07 but for some reason the commandline (conkyPidgin -V) still tells me it's 2.06, no matter though.
thanks

---

### Post by kaivalagi on 2008-11-25
> **hachel said:**
> great stuff, it works now with the new update.
Just on thing: under synaptic conkyPidgin is listed as 2.07 but for some reason the commandline (conkyPidgin -V) still tells me it's 2.06, no matter though.
thanks

Whoops, forgot to update that :)

---

### Post by tedrampart on 2008-11-27
I love this script.. what I've needed for a long time..

one issue I'm having with the template file.. 
I have:
```
[alias]${alignr}[status]
```

and conky doesn't recognize the conky variable for alignr (or any of them for that matter), and actually displays ${alignr}

eg: tedrampart${alignr}Away  is displayed in conky, any thoughts?

EDIT - need some sleep, I forgot to use execpi 60 conkyPidgin, instead of just execi... now it works like a charm.. thanks a bunch!!

---

### Post by super.rad on 2008-11-30
great script thanks, I have a question though.
My conky displays my buddy list like this
[IMG]http://i274.photobucket.com/albums/jj243/super_rad/screen1.png[/IMG]
What I want is for it to have their status displayed using pidgins status icons and then their names both aligned left and then which group they are in (MSN, AIM, etc) aligned on the right and not to show the custom status messages. Is this possible and if so how would i go about doing it?
These are the icons I want to be displayed instead of their status
[IMG]http://i274.photobucket.com/albums/jj243/super_rad/Screenshot-1.png[/IMG]

My .conkyrc for pidgin has this:
```
${execpi 60 python /home/fedora/Scripts/conkyPidgin.py -o}
```
Thanks

---

### Post by kaivalagi on 2008-11-30
> **super.rad said:**
> great script thanks, I have a question though.

My .conkyrc for pidgin has this:
```
${execpi 60 python /home/fedora/Scripts/conkyPidgin.py -o}
```
Thanks

Use a template file, take a look at the example folder in the tarball for details...

Remember conky is limited to text only, so somethings you want you just can't have :(

---

### Post by super.rad on 2008-11-30
Thanks, i'll have a look at the example folder and post back if i have any problems.
Didnt think conky could handle icons but haven't used conky for a few years so wasn't sure if it now could. Oh well.

---

### Post by kaivalagi on 2008-12-14
New app added to my PPA, new thread on this can be found through the apps link in my sig below...

Pidgin buddies list with icons...:)

---

### Post by laurielegit on 2008-12-16
I would like to have ConkyPidgin centered but using ${alignc} only centers the top "Buddy". See the attached thumbnail. Is there anyway I can have it totally aligned.

Thanks,

Laurie

---

### Post by plueschi on 2008-12-16
you have to edit your template

---

### Post by kaivalagi on 2008-12-16
> **plueschi said:**
> you have to edit your template

Spot on...

Use templates for the output and place any align$ / goto$ directives in the template itself....look at the example template and conkyrc for more help

---

### Post by laurielegit on 2008-12-16
This is my conkyPidgin.template:

```

${alignc}[alias] ([status])
${alignc}[status_message]
```

What am I doing wrong. The ${alignc} works fine on my conkyrc file, but not on the conkyPidgin.template?

---

### Post by kaivalagi on 2008-12-16
> **laurielegit said:**
> This is my conkyPidgin.template:

```

${alignc}[alias] ([status])
${alignc}[status_message]
```

What am I doing wrong. The ${alignc} works fine on my conkyrc file, but not on the conkyPidgin.template?

are you calling the script using execpi/execp?

Could be that the alignc isn't supported via execp?

Can you post your conkyrc file please...

---

### Post by laurielegit on 2008-12-16
```

# Conky configuration
background no
use_xft yes
xftfont sans:size=9
xftalpha 0.8
out_to_console no
update_interval 1
total_run_times 0
own_window no
own_window_type normal
own_window_transparent yes
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 5
border_margin 4
border_width 1
default_color grey
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 40
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer yes
alignment top_left
text_buffer_size 2048

TEXT
${color white}${alignc}$nodename - $kernel - Uptime: $uptime 
$color$stippled_hr
${color white}${alignc}Network: Wireless
${color grey}${alignc}${addr wlan0}
${color white}Bandwidth: ${color grey}       Up: ${color grey}${upspeed wlan0} k/s     ${color grey}Down: ${color grey}${downspeed wlan0} k/s	    
                         ${color grey}${totalup wlan0} Up      ${color grey}${totaldown wlan0} Down
$color$stippled_hr
${color white}${alignc}Unread Emails:
${alignc}${execi 1800 conkyEmail -t /home/laurie/Source/.conkyemail}$color$stippled_hr
${color white}${alignc}Load Average - ${loadavg}
${color grey}${alignc}Processes: ${color grey} $processes  ${color grey}Running:${color grey} $running_processes
${color white}Name:                    ${alignr}PID     CPU%   MEM%
  ${color grey} ${top name 1}     ${alignr}${top pid 1} ${top cpu 1} ${top mem 1}
  ${color grey} ${top name 2}     ${alignr}${top pid 2} ${top cpu 2} ${top mem 2}
  ${color grey} ${top name 3}     ${alignr}${top pid 3} ${top cpu 3} ${top mem 3}
  ${color grey} ${top name 4}     ${alignr}${top pid 4} ${top cpu 4} ${top mem 4}
${color white}Memory Usage:
  ${color grey} ${top_mem name 1} ${alignr}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
  ${color grey} ${top_mem name 2} ${alignr}${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
  ${color grey} ${top_mem name 3} ${alignr}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
  ${color grey} ${top_mem name 4} ${alignr}${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
$color$stippled_hr
${color white}CPU: $color ${color grey}${color white}     Usage: ${color grey} ${cpu}% ${color white}${cpubar}
                           RAM: $memperc% ${membar}
                         SWAP:  $swapperc% ${swapbar}
$color$stippled_hr
${color white}${alignc}Drives
${color white}System: ${alignc}${color grey}${fs_used /}${color white}/${color grey}${fs_size /} ${color white}${alignr}(${color grey}${fs_free /} ${fs_free_perc /}% ${color white} free)
         ${fs_bar /}
${color white}Home Directory: ${alignc}${color grey}${fs_used /home}${color white}/${color grey}${fs_size /home} ${color white}${alignr}(${color grey}${fs_free /home} ${fs_free_perc /home}% ${color white} free)
         ${fs_bar /home}
${color white}External: ${alignc}${color grey}${fs_used /media/disk}${color white}/${color grey}${fs_size /media/disk} ${color white}${alignr}(${color grey}${fs_free /media/disk} ${fs_free_perc /media/disk}% ${color white} free)
         ${fs_bar /media/disk}
$color$stippled_hr
${alignc}${color white}Pidgin:
${execi 60 conkyPidgin -t /usr/share/conkypidgin/example/conkyPidgin.template -o --ignorelist="No Conky"}
$color$stippled_hr
```

It seems to be execi. Could you please explain the importance of this (so I can fix my problem and learn somthing).

Thanks

---

### Post by kaivalagi on 2008-12-16
> **laurielegit said:**
> ```

${alignc}${color white}Pidgin:
${execi 60 conkyPidgin -t /usr/share/conkypidgin/example/conkyPidgin.template -o --ignorelist="No Conky"}

```

It seems to be execi. Could you please explain the importance of this (so I can fix my problem and learn somthing).

Thanks

No worries, execpi handles conky formatting from the output it receives through commands it calls, where as execi just spits out what it gets.

The conky documentation is brief but can be found here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

The bit you're interested in is:

[I]**execp**
Executes a shell command and displays the output in conky. warning: this takes a lot more resources than other variables. I'd recommend coding wanted behaviour in C and posting a patch. This differs from $exec in that it parses the output of the command, so you can insert things like ${color red}hi!${color} in your script and have it correctly parsed by Conky. Caveats: Conky parses and evaluates the output of $execp every time Conky loops, and then destroys all the objects. If you try to use anything like $execi within an $execp statement, it will functionally run at the same interval that the $execp statement runs, as it is created and destroyed at every interval.
[B]
execpi[/B]
Same as execp but with specific interval. Interval can't be less than update_interval in configuration. Note that the output from the $execpi command is still parsed and evaluated at every interval. [/I]


So, for the above conkyrc you would want something like this instead:

```

${color white}Pidgin:
${[COLOR="Red"]execpi[/COLOR] 60 conkyPidgin -t /usr/share/conkypidgin/example/conkyPidgin.template -o --ignorelist="No Conky"}

```

Your conky formatting commands should then be in the template and therefore output by the conkyPidgin script, which execpi will interpret and format the resultant output.

Hope that helps :)

---

### Post by laurielegit on 2008-12-16
To think that a single p could cause all that trouble. Thank you very much, another box I can tick of in my list of things to learn about conky. Thank you again.

---

### Post by laurielegit on 2008-12-21
I have two recommendations/request that I would like to see in this script. Would it be possible for it to:
1. Change the order that contacts are listed, in the way Pidgin allows, e.g. By log size (what I would personally like), by status and to be able to sort them manually. Could this be done by recognising the order that the contacts are listed in the classic pidgin Buddies list.
2. Put a limit on the number of contacts displayed. I would like this because I have a terminal embeded on my desktop directly below my conky, and sometimes, when too many people are online, the two overlap.  Also, It would probably be best to implement the first idea if you were going to implement this one, as I could define that I wanted contacts that I had a large log with to be displayed first and to have priority over others, thus meaning that valuable contacts were not cut off.

Thanks,

Laurie

---

### Post by plueschi on 2008-12-21
I have also a few requests about that script:

I use this your script to show my online buddies in conky and [this one]("http://fourlovesfour.blogspot.com/2008/10/conky-display-last-pidgin-message.html") to see on my conky when the last message has been recived and who sent it:

I've edited line 16 in [getim.py]("http://yourpaste.net/1423") and put that code to my .conkyrc:
```
Last Message from:${alignr}${execpi 1 python ~/scripts/conky/lastim.py} (${execi 1 ls -lta | grep .pidgin.log | awk '{print $7}'})
```

but i've got 2 issues: 

1. when the last message is form an icq-buddy there will only shown his/her UIN and not the nickname/alias...

2. I don't have any idea how to show the number of unread messages in pidgin... 

maybe it would be possible to put those two scripts together and solve the two issues?!

---

### Post by spupy on 2009-01-04
Hi, I'm trying to use your script in Gentoo. My conky version is 1.6.1, pidgin is 2.5.1.

I have pidgin running, but when I start conky with
```
${execi 60 /home/uibxn/Scripts/conkypidgin/conkyPidgin}
```

it fails with a "segmentation fault".

Running conkyPidgin on its own in a terminal print the buddy list.

How can I go about debugging this?

EDIT: It seems that conky had problem with printin all the buddies. Setting the "-o" option that prints only the online buddies solved the problem.

Thanks!

---

### Post by kaivalagi on 2009-01-04
> **spupy said:**
> Hi, I'm trying to use your script in Gentoo. My conky version is 1.6.1, pidgin is 2.5.1.

I have pidgin running, but when I start conky with
```
${execi 60 /home/uibxn/Scripts/conkypidgin/conkyPidgin}
```

it fails with a "segmentation fault".

Running conkyPidgin on its own in a terminal print the buddy list.

How can I go about debugging this?

EDIT: It seems that conky had problem with printin all the buddies. Setting the "-o" option that prints only the online buddies solved the problem.

Thanks!

Maybe there was too much text to output, try setting the text buffer in the conkyrc file to be larger and remove the -o option from the script...if you want to see all the buddies that is

---

### Post by kaivalagi on 2009-01-04
> **plueschi said:**
> I have also a few requests about that script:

I use this your script to show my online buddies in conky and [this one]("http://fourlovesfour.blogspot.com/2008/10/conky-display-last-pidgin-message.html") to see on my conky when the last message has been recived and who sent it:

I've edited line 16 in [getim.py]("http://yourpaste.net/1423") and put that code to my .conkyrc:
```
Last Message from:${alignr}${execpi 1 python ~/scripts/conky/lastim.py} (${execi 1 ls -lta | grep .pidgin.log | awk '{print $7}'})
```

but i've got 2 issues: 

1. when the last message is form an icq-buddy there will only shown his/her UIN and not the nickname/alias...

2. I don't have any idea how to show the number of unread messages in pidgin... 

maybe it would be possible to put those two scripts together and solve the two issues?!

The problem is that the getim script catches im events as it runs all the time but the conkyPidgin script is exec'ed over and over..they are not compatible really

---

### Post by kaivalagi on 2009-01-04
> **laurielegit said:**
> I have two recommendations/request that I would like to see in this script. Would it be possible for it to:
1. Change the order that contacts are listed, in the way Pidgin allows, e.g. By log size (what I would personally like), by status and to be able to sort them manually. Could this be done by recognising the order that the contacts are listed in the classic pidgin Buddies list.
2. Put a limit on the number of contacts displayed. I would like this because I have a terminal embeded on my desktop directly below my conky, and sometimes, when too many people are online, the two overlap.  Also, It would probably be best to implement the first idea if you were going to implement this one, as I could define that I wanted contacts that I had a large log with to be displayed first and to have priority over others, thus meaning that valuable contacts were not cut off.

Thanks,

Laurie

I am not sure about the log size, I have tried to figure out how to determine this but can't, maybe someone can help me out with that?

The limit option sounds like a good idea, when I have time I'll look into it...

---

### Post by markp1989 on 2009-01-04
> **kaivalagi said:**
> [COLOR="DarkGreen"]**[SIZE="4"]New Intrepid based package only[/SIZE]**[/COLOR]

**_[SIZE="3"][COLOR="Blue"]Intro[/COLOR][/SIZE]_**

This is a simple script to display buddy info from Pidgin. The script talks to Pidgin using dbus and allows templates...

There is a README with the install and attached here, I suggest you give it atleast a quick once over!

**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

Edit your sources.list file by running this:

```

gksudo gedit /etc/apt/sources.list

```

And add the following line on the end of the file, then save.

```

deb http://ppa.launchpad.net/m-buck/ubuntu intrepid main

```

Now that is done simply run the following to install (answering yes to the verification question)

```
sudo apt-get update && sudo apt-get install conkypidgin

```

**[COLOR="Blue"]Method 2: Using deb file[/COLOR]**

Download and run the attached .deb file

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR="Blue"]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the attached tar.gz file to an appropriate folder, and edit the conkyDeluge script to point to the correct location where conkyDeluge.py is.

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE="3"][COLOR="Blue"]Usage Help[/COLOR][/SIZE]_**

To use the script in conky in it's simplist form, you'll need an exec statement like this:

```
${execi 60 conkyPidgin}
```

To use a template for custom output, I suggest you read the README attached, and take a look at the example conkyrc and template files that are installed to "/usr/share/conkypidgin/example".

You can get the current help options at any time by running:

```

conkyPidgin -h

```

or

```

conkyPidgin --help

```

```
Usage: conkyPidgin [options]
Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        Template file determining the format for each buddy's
                        data. Use the following placeholders: [name], [alias],
                        [group], [status], [status_message].
  -o, --onlineonly      Only show online buddies
  -a, --availableonly   Only show available buddies
  -i LIST, --ignorelist=LIST
                        A comma delimited list of groups to ignore. Partial
                        text matches on group will be ignored if found
  -I LIST, --includelist=LIST
                        A comma delimited list of groups to include. Partial
                        text matches on group will be included if found. The
                        ignorelist, if used, takes precedence. if this list is
                        omitted all groups will be included unless ignored.
  -C TEXT, --chattingtext=TEXT
                        [default: Chatting] Text to use for chatting status
                        output
  -A TEXT, --availabletext=TEXT
                        [default: Available] Text to use for available status
                        output
  -U TEXT, --unavailabletext=TEXT
                        [default: Unavailable] Text to use for unavailable
                        status output
  -N TEXT, --invisibletext=TEXT
                        [default: Invisible] Text to use for invisible status
                        output
  -W TEXT, --awaytext=TEXT
                        [default: Away] Text to use for away status output
  -M TEXT, --mobiletext=TEXT
                        [default: Mobile] Text to use for mobile status output
  -F TEXT, --offlinetext=TEXT
                        [default: Offline] Text to use for offline status
                        output
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

**_[SIZE="3"][COLOR="Blue"]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [https://code.launchpad.net/~m-buck/+junk/conkypidgin](https://code.launchpad.net/~m-buck/+junk/conkypidgin)

And details on the packages available from me can be found here [https://launchpad.net/~m-buck/+archive](https://launchpad.net/~m-buck/+archive)

I have also created a new website, for now it is relatively sparse, but it does details my conky scripts to a certain degree. You can find it here: [http://www.kaivalagi.com](http://www.kaivalagi.com)

thanks for all your usefull work, i use the forecast script constantly. 


would love to use this , but i dont use pidgin. have you considered doing one for emesene?

---

### Post by kaivalagi on 2009-01-05
> **markp1989 said:**
> thanks for all your usefull work, i use the forecast script constantly. 


would love to use this , but i dont use pidgin. have you considered doing one for emesene?

I had a quick look at the source code for emesene and there doesn't seem to be a way to interrogate the app from outside of itself via dbus, it only seems to support plugins.

To be honest, I dont like the idea of implementing a script for a messenger app which only handles one protocol anyway.

Maybe when Empathy makes it's proper appearance it will attract the likes of yourself. I'll no doubt create a script to that at that time too, cause I'll be using it by then as well. [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy)

---

### Post by markp1989 on 2009-01-06
> **kaivalagi said:**
> I had a quick look at the source code for emesene and there doesn't seem to be a way to interrogate the app from outside of itself via dbus, it only seems to support plugins.

To be honest, I dont like the idea of implementing a script for a messenger app which only handles one protocol anyway.

Maybe when Empathy makes it's proper appearance it will attract the likes of yourself. I'll no doubt create a script to that at that time too, cause I'll be using it by then as well. [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy)

i understand, im thinking i may have to convert to pidgin now lol.

btw, thankyou for your conky python scripts, i appriciate the efort you have put in to them.

---

### Post by kaivalagi on 2009-01-07
[SIZE="4"]**[COLOR="Orange"]UPDATE[/COLOR]**[/SIZE]

The following updates have been made:

[LIST]
[*]Fixed buddy status handling
[*]Updated to sort based on activity in logs initially, falling back to groups then names after that in case no logging is switched on
[*]Added --limit option to restrict the number of buddies output, works in conjunction with new sort method to produce a usefully sorted short list
[/LIST]

@laurielegit - for the sorting of the list I went off log time stamp rather than size, so the order will be by who most recently chatted with you. Hope that makes sense.

The first post has been updated and the apt package will be available shortly

Chimo!

---

### Post by plueschi on 2009-01-08
> **kaivalagi said:**
> [SIZE="4"]
[*]Updated to sort based on activity in logs initially, falling back to groups then names after that in case no logging is switched on

hmmm i dont like that new kind of sorting :/
maybe you could bulid an switch in, which controls it?!

---

### Post by kaivalagi on 2009-01-08
> **plueschi said:**
> hmmm i dont like that new kind of sorting :/
maybe you could bulid an switch in, which controls it?!

what, if --limit is used sort the new way, otherwise as before?

Will take some doing, but I think it can happen...

---

### Post by kaivalagi on 2009-01-08
> **plueschi said:**
> hmmm i dont like that new kind of sorting :/
maybe you could bulid an switch in, which controls it?!

**how about if --limit is used, sort the new way, otherwise as before?**

This will take some doing, as the sorting criteria is built into the class that holds the data at present..I think there are more dynamic sorting approaches I can look at though...need to do some reading

---

### Post by kaivalagi on 2009-01-08
> **plueschi said:**
> hmmm i dont like that new kind of sorting :/
maybe you could bulid an switch in, which controls it?!

**what about if --limit is used, sort the new way, otherwise as before?**

This will take some doing, as the sorting criteria is built into the class that holds the data at present..I think there are more dynamic sorting approaches I can look at though...need to do some reading

---

### Post by laurielegit on 2009-01-08
Thank you *very*much. It's nice to use a program/script and know that the creator cares about it's users. And when you find that the program is brilliant as well, then there's really nothing that you can wish for. Thank you.

Laurie

---

### Post by kaivalagi on 2009-01-08
> **plueschi said:**
> hmmm i dont like that new kind of sorting :/
maybe you could bulid an switch in, which controls it?!

**how about if --limit is used, sort the new way, otherwise as before?**

This will take some doing, as the sorting criteria is built into the class that holds the data at present..I think there are more dynamic sorting approaches I can look at though...need to do some reading

---

### Post by kaivalagi on 2009-01-08
> **plueschi said:**
> hmmm i dont like that new kind of sorting :/
maybe you could bulid an switch in, which controls it?!

Didn't realise it would be such an issue, no worries.

I am removing the sorting change for default functionality, and adding a --sortbylogactivity option to switch it on as needed...release coming any mo...

---

### Post by kaivalagi on 2009-01-08
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

I've added --sortbylogactivity to change the sorting method for the list to be log file mod date based. If this option is not used default sorting by status, group then alias is done as before.

The changes are available in the first post and via apt

;)

---

### Post by kaivalagi on 2009-01-08
forum playing up...

---

### Post by kaivalagi on 2009-01-08
forum playing up...

---

### Post by kaivalagi on 2009-01-08
forum playing up...

---

### Post by kaivalagi on 2009-01-09
forum playing up...

---

### Post by plueschi on 2009-01-09
ah - since the update yesterday it works fine :D

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by stuv306 on 2009-01-09
WILLIAM WALLACE&#65306;"Fight, and you may die. Run, and you'll live at least a while. And dying in your beds many years from now. Would you be willing to trade? All the days from this day to that, for one chance, just one chance, to come back here and tell our enemies that they may take our lives, but they'll never take our Freedom! ---------------------------------------------------------------[wow gold](http://www.inwowgold.com)-[World of Warcraft Gold](http://www.inwowgold.com)-[cheap wow gold](http://www.inwowgold.com)-[Buy wow gold](http://www.inwowgold.com)-[wow power leveling](http://www.inwowgold.com/power-leveling/)

---

### Post by Forlornity on 2009-01-15
Nice script, really nice.
I'd just like to request an option for offline contacts only (so I can have different statuses in different lists, etc.)
As it stands my limited knowledge of python was enough to get it working, but it's very much a baaaaaad fix, ignoring all options and the like (requiring me to run a different script for offline only), wondering if you might make add this feature yourself (I'd do it were I better with Python, but hell, give me a few weeks (once my computing coursework's done) and I'll see if I can't figure it out).
Thanks, Forlornity

---

### Post by kaivalagi on 2009-01-18
> **Forlornity said:**
> Nice script, really nice.
I'd just like to request an option for offline contacts only (so I can have different statuses in different lists, etc.)
As it stands my limited knowledge of python was enough to get it working, but it's very much a baaaaaad fix, ignoring all options and the like (requiring me to run a different script for offline only), wondering if you might make add this feature yourself (I'd do it were I better with Python, but hell, give me a few weeks (once my computing coursework's done) and I'll see if I can't figure it out).
Thanks, Forlornity

I've added an --offlineonly option to the script and altered the code to cope. I've attached v 2.10 of the script package...can you give it a whirl?

If all is good then I'll release it via apt

Cheers

---

### Post by Gnounc on 2009-01-20
Ok, it took me a while, but I finally have conky where I want it (except for RSS) anyways, I noticed there isnt a thread devoted to gtk-desktop-info.
I'd like to see one similar to the "show your conkyrc and a screenshot" thread.
I'd like to see what novel uses it's been put towards. It would also help me to visualize its capabilities and help me to use it.

---

### Post by HippyRandall on 2009-01-20
> **Gnounc said:**
> Ok, it took me a while, but I finally have conky where I want it (except for RSS) anyways, I noticed there isnt a thread devoted to gtk-desktop-info.
I'd like to see one similar to the "show your conkyrc and a screenshot" thread.
I'd like to see what novel uses it's been put towards. It would also help me to visualize its capabilities and help me to use it.
You missed it in K's sig:
[http://ubuntuforums.org/showthread.php?p=6366056](http://ubuntuforums.org/showthread.php?p=6366056)

Hippy

---

### Post by Gnounc on 2009-01-20
oHo. haha thanks. How I missed that I dont know.

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

### Post by jim_mule on 2009-02-06
oh how i want this to work. but i keep getting this:

```
ERROR: Issue calling the dbus service:im.pidgin.purple.ObjectNotFound: The return object is not mapped (this is a Purple error)
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 323, in writeOutput
    for pidginData in pidginDataList:
TypeError: 'NoneType' object is not iterable
ERROR: Unknown error when calling writeOutput:'NoneType' object is not iterable

```

i am running intrepid, all updates made, gnome/pidgin all is fine and running and conky too. what can i do?

---

### Post by kaivalagi on 2009-02-06
> **jim_mule said:**
> oh how i want this to work. but i keep getting this:

```
ERROR: Issue calling the dbus service:im.pidgin.purple.ObjectNotFound: The return object is not mapped (this is a Purple error)
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 323, in writeOutput
    for pidginData in pidginDataList:
TypeError: 'NoneType' object is not iterable
ERROR: Unknown error when calling writeOutput:'NoneType' object is not iterable

```

i am running intrepid, all updates made, gnome/pidgin all is fine and running and conky too. what can i do?

It looks like Pidgin isn't running? The dbus service for pidgin isn't getting connected.

What version of Pidgin are you running? run this in the terminal:

```
pidgin -v
```

I get:

```
Pidgin 2.5.2
```

---

### Post by jim_mule on 2009-02-06
yes, pidgin -v = Pidgin 2.5.2 and pidgin is in the taskbar.
thanks for the quick reply.

---

### Post by kaivalagi on 2009-02-06
> **jim_mule said:**
> yes, pidgin -v = Pidgin 2.5.2 and pidgin is in the taskbar.
thanks for the quick reply.

I have created a small test script which looks for available dbus services on your pc that match some text, in this case "pidgin".

Grab the attached and put it anywhere on your PC, then run it in the terminal like this:

```
python **/path/to/file/**testdbus.py
```

I get:

```
Searching dbus services...
found: im.pidgin.purple.PurpleService
finished searching
```

---

### Post by jim_mule on 2009-02-07
1st time i tried your script i got the following:
```
./testdbus.py 
Searching dbus services...
found: im.pidgin.purple.PurpleService
finished searching

```

so i then gave conky another try:
```
ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 323, in writeOutput
    for pidginData in pidginDataList:
TypeError: 'NoneType' object is not iterable
ERROR: Unknown error when calling writeOutput:'NoneType' object is not iterable

```

tried the script again, after this restart of conky with conkyPidgin, and i get:

```
./testdbus.py 
Searching dbus services...
finished searching

```

mystery to me...

---

### Post by jim_mule on 2009-02-07
hmmm.
mystery remains. 
but i restarted pidgin. i did just a conkyPidgin on the command line, and no error, so put it back into my .conkyrc, and restarted conky again, and all is well. sometimes i still think the computer is run by elves with mood swings. thanks for the help, im happy to get pidgin into conky, brilliant.

---

### Post by kaivalagi on 2009-02-07
> **jim_mule said:**
> hmmm.
mystery remains. 
but i restarted pidgin. i did just a conkyPidgin on the command line, and no error, so put it back into my .conkyrc, and restarted conky again, and all is well. sometimes i still think the computer is run by elves with mood swings. thanks for the help, im happy to get pidgin into conky, brilliant.

Maybe uninstall and reinstall pidgin? I am at a loss as to why the dbus service comes and goes...

---

### Post by kaivalagi on 2009-02-08
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Not much of an update, just added --offlineonly option, so only offline buddies are displayed in the list.

Changes can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkypidgin_2.10_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkypidgin_2.10_source.changes)

The first post updated and the apt package should be available soon...

---

### Post by HarshReality on 2009-02-26
OK, we need templates and rc lines folks (particularly those where they are using a font to display the status rather than a message).

Love the script & thanks for the contribution!

---

### Post by kaivalagi on 2009-02-26
> **HarshReality said:**
> OK, we need templates and rc lines folks (particularly those where they are using a font to display the status rather than a message).

Love the script & thanks for the contribution!

Take a look at the example files in /usr/share/conkypidgin/example, the webdings font is used in the template in conjunction with configured characters in the conkyrc to produce symbols..

---

### Post by stefanos1 on 2009-04-14
Hello, thanks for all your scripts...

I don't know if my question is already answered.

Some contactse use some veeery large messages and that ruins my conky and fills the half desktop with it..

I just want to see for example

John(Available)

and no

John(Available)
**Liverpool owns-You 'll never walk alone-etc etc etc etc etc etc** 

:p

---

### Post by kaivalagi on 2009-04-15
> **stefanos1 said:**
> Hello, thanks for all your scripts...

I don't know if my question is already answered.

Some contactse use some veeery large messages and that ruins my conky and fills the half desktop with it..

I just want to see for example

John(Available)

and no

John(Available)
**Liverpool owns-You 'll never walk alone-etc etc etc etc etc etc** 

:p

You maybe able to setup conky to have a fixed width which wont change if large length text is output. Look at the maximum width setting in your conkyrc...[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Other than that I'd have to make some script changes, and this may be a little while off...

---

### Post by stefanos1 on 2009-04-15
> **kaivalagi said:**
> You maybe able to setup conky to have a fixed width which wont change if large length text is output. Look at the maximum width setting in your conkyrc...[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Other than that I'd have to make some script changes, and this may be a little while off...

Thanks will check it :guitar:

---

### Post by kaivalagi on 2009-04-15
> **stefanos1 said:**
> Thanks will check it :guitar:

I just read your request again and if you just want to get rid of the status message altogether, you can use a custom template.

Take a look at the example conkyrc which shows how you can call the command for this. There is also an example .template file showing the idea. The example files are found here: /usr/share/conkypidgin/example/

If you were to copy the example template somewhere suitable and remove the status message line, and then use this new template that would do it. So this:

```
${voffset 5}${color3}${font Webdings:size=16}[status]${color1}${font}${voffset -5}${goto 25}[alias] ([group])
${color3}${goto 25}[status_message]

```

Becomes this:

```
${voffset 5}${color3}${font Webdings:size=16}[status]${color1}${font}${voffset -5}${goto 25}[alias] ([group])

```

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

### Post by error420 on 2009-05-26
I just wanted to say thank you for sharing. This script works great. Using 9.04

---

### Post by kaivalagi on 2009-05-26
> **error420 said:**
> I just wanted to say thank you for sharing. This script works great. Using 9.04

Thanks for the nice feedback, it's always welcome :)

---

### Post by burymeinblack907 on 2009-05-31
Am I able to get help for conkyPidgin here?

---

### Post by merlin_ie on 2009-06-01
Hi Kaivalagi. Any chance you can help with a problem I'm having with this script? I get the following error in terminal : ```
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 333, in writeOutput
    print output.encode("utf-8")
IOError: [Errno 32] Broken pipe
ERROR: Unknown error when calling writeOutput:[Errno 32] Broken pipe
```

Also, as you can see in the screenshot, it only shows one person as online whereas there is actually 2 people online. (one is msn, other is yahoo) Any suggestions as to why it's not showing the second person? Would it be the first persons yahoo status message is too long perhaps?

[IMG]http://img37.imageshack.us/img37/2865/screenshoti.png[/IMG]

I don't know much about pidgin as I don't use it much. Just wanted to try your scripts. 

Is there any chance something like this can be done for amsn? 

Keep up the great work

---

### Post by kaivalagi on 2009-06-01
> **merlin_ie said:**
> Hi Kaivalagi. Any chance you can help with a problem I'm having with this script? I get the following error in terminal : ```
Traceback (most recent call last):
  File "/usr/share/conkypidgin/conkyPidgin.py", line 333, in writeOutput
    print output.encode("utf-8")
IOError: [Errno 32] Broken pipe
ERROR: Unknown error when calling writeOutput:[Errno 32] Broken pipe
```

Also, as you can see in the screenshot, it only shows one person as online whereas there is actually 2 people online. (one is msn, other is yahoo) Any suggestions as to why it's not showing the second person? Would it be the first persons yahoo status message is too long perhaps?

I don't know much about pidgin as I don't use it much. Just wanted to try your scripts. 

Is there any chance something like this can be done for amsn? 

Keep up the great work

I think the broken pipe error you are getting relates to the text length and it's support in Conky (may be wrong...)

Can you try extending the text buffer used in conky? I copied this from my weather script thread:

[I]Conky has a default limitation of 128 bytes for any text output from a variable (such as execi). If you are creating large templates with more characters than the default buffer size can handle, the output will get truncated. If this happens you can override the default behaviour by setting as new buffer size before the TEXT section in your conkyrc file, as follows:

```

text_buffer_size 1024

```[/I]
I wont be creating a script for amsn, it just doesn't support enough IM providers...try switching over from amsn to pidgin, I find it a more capable IM client

---

### Post by burymeinblack907 on 2009-06-02
I seem to be having the same problem as merlin_ie.  It only displays half a name when there's more buddies available.  I already have my text_buffer_size 2048.  Also when I test the command in terminal it displays everything correctly.  Any way to fix you know of? I posted a picture.

background yes
use_xft yes
text_buffer_size 2048
# Xft font when Xft is enabled
xftfont Terminus:size=9
# Text alpha when using Xft
xftalpha 0.8
update_interval 1
total_run_times 0
own_window yes
double_buffer yes
minimum_size 300 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 0
border_margin 0
border_width 0
default_color white
default_shade_color black
default_outline_color white
own_window        yes
own_window_transparent    yes
own_window_type        normal
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager
alignment top_left
gap_x 0
gap_y 30
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
use_spacer yes
# colours
color1 white
# light blue
color2 6892C6
# orange
color3 E77320
# green
color4 78BF39
# red
color5 CC0000


TEXT
${font Terminus:style=Bold:size=11}Pidgin Buddies${font}
${color1}${execpi 60 conkyPidgin -t /Conky/conkyPidgin.template -o -C _ -A a -U x -N s -W P -M j -F r}

---

### Post by kaivalagi on 2009-06-03
> **burymeinblack907 said:**
> I seem to be having the same problem as merlin_ie.  It only displays half a name when there's more buddies available.  I already have my text_buffer_size 2048.  Also when I test the command in terminal it displays everything correctly.  Any way to fix you know of? I posted a picture.

It must be conky related as the correct output turns up in the terminal. It looks like the conky window isn't large enough.

I would ask some questions on the conkyrc thread, if you here nothing more from here.

---

### Post by Sarai the Geek on 2009-06-16
This is a great script, works exactly as advertised! However, I've got a small screen (12.5 in) so I'm trying to free up some space by using a really minimalist conky. Is there a way I can get it to only display the *number* of online buddies?

---

### Post by kaivalagi on 2009-06-16
> **Sarai the Geek said:**
> This is a great script, works exactly as advertised! However, I've got a small screen (12.5 in) so I'm trying to free up some space by using a really minimalist conky. Is there a way I can get it to only display the *number* of online buddies?

Unfortunately not directly, although the default output format is one line per buddy so if you limit output to online only and then parse this output with a sed command you can get a count...e.g:

Terminal:
```
conkyPidgin -o | sed -n '$='
```

Conkyrc:
```
${execi 1800 conkyPidgin -o | sed -n '$='}
```

Should do the job for you :)

---

### Post by Sarai the Geek on 2009-06-16
> **kaivalagi said:**
> Unfortunately not directly, although the default output format is one line per buddy so if you limit output to online only and then parse this output with a sed command you can get a count...e.g:

Terminal:
```
conkyPidgin -o | sed -n '$='
```Conkyrc:
```
${execi 1800 conkyPidgin -o | sed -n '$='}
```Should do the job for you :)

It works perfectly. Kudos to you, sir, and thank you for all your awesome scripts!

---

### Post by kaivalagi on 2009-06-16
> **Sarai the Geek said:**
> It works perfectly. Kudos to you, sir, and thank you for all your awesome scripts!

My pleasure :)

---

### Post by Snow-Brother on 2009-06-18
This is a great script, thank you for creating it. I have a question about it though. I have pidgin set up for Aim and Xfire. Many of my friends use both (not all of them though). Would it be possible to set it up so that it will only show one copy of that friend if they happen to be logged on both Xfire and AIM? 

For example, if Friend1 is logged on AIM and Xfire, would it be possible to tell the script to display that friend on Xfire and only display them on AIM if they aren't logged onto anything else?

As I said, this is a great script, but it can become very cluttered if I have a lot of friends logged on to both AIM and Xfire at once. I don't want to remove them from either list because they don't always log on to both.

---

### Post by kaivalagi on 2009-06-18
> **Snow-Brother said:**
> This is a great script, thank you for creating it. I have a question about it though. I have pidgin set up for Aim and Xfire. Many of my friends use both (not all of them though). Would it be possible to set it up so that it will only show one copy of that friend if they happen to be logged on both Xfire and AIM? 

For example, if Friend1 is logged on AIM and Xfire, would it be possible to tell the script to display that friend on Xfire and only display them on AIM if they aren't logged onto anything else?

As I said, this is a great script, but it can become very cluttered if I have a lot of friends logged on to both AIM and Xfire at once. I don't want to remove them from either list because they don't always log on to both.

I have the same issue with my buddies too, in fact I am a problem for others as well 'cause I have 3 accounts to ensure I can talk to all my friends.

I assume the buddy alias is the same between accounts?

I'll add it to my todo list and get round to it at some point, no promises though...

---

### Post by Sarai the Geek on 2009-06-18
> **kaivalagi said:**
> My pleasure :)

One more thing- because it's counting by lines, when a buddy has a custom status message it counts that as an extra line and thus an extra buddy, so the count isn't always accurate. Is there a way to attach a template to that script call so that I can format it as 1 buddy per line with no status message?

---

### Post by kaivalagi on 2009-06-19
> **Sarai the Geek said:**
> One more thing- because it's counting by lines, when a buddy has a custom status message it counts that as an extra line and thus an extra buddy, so the count isn't always accurate. Is there a way to attach a template to that script call so that I can format it as 1 buddy per line with no status message?

Yep, use the --template option. From conkyPidgin --help :

```
  -t FILE, --template=FILE
                        Template file determining the format for each buddy's
                        data. Use the following placeholders: [name], [alias],
                        [group], [status], [status_message].
```

So, you would create a simple template file using the placeholders mentioned above and then use it by adding a --template=/path/to/file option in your exec calls.

In theory just use one placeholder for alias and you just want a count...

Cheers

---

### Post by dather on 2009-06-27
I found one bug,look at the ss
[[IMG]http://img514.imageshack.us/img514/6876/screenshott.th.jpg[/IMG]]("http://img514.imageshack.us/img514/6876/screenshott.jpg/")
You must do something to protect from names that have $

---

### Post by kaivalagi on 2009-06-27
> **dather said:**
> I found one bug,look at the ss
[[IMG]http://img514.imageshack.us/img514/6876/screenshott.th.jpg[/IMG]]("http://img514.imageshack.us/img514/6876/screenshott.jpg/")
You must do something to protect from names that have $

I'll do something about it in all scripts that could be affected

---

### Post by kaivalagi on 2009-06-27
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

[LIST]
[*]Updated to expand ~ based template paths
[*]Updated to make safe the output to stop unwanted conky execution
[/LIST]

Changes can be found here: [https://launchpad.net/~m-buck/+archive/conky/+files/conkypidgin_2.11_source.changes](https://launchpad.net/~m-buck/+archive/conky/+files/conkypidgin_2.11_source.changes)

The first post is updated and the apt package should be available soon...

---

### Post by dather on 2009-06-27
Nooooo w8, i want to hack one friend :(

---

### Post by kaivalagi on 2009-06-27
> **dather said:**
> Nooooo w8, i want to hack one friend :(

too late I'm afraid ;)

---

### Post by thecheeks on 2009-06-30
How do you get rid of the group name and the following '-'.

I just want screen names showing, no group name like (Buddies), the following dash, or status.

---

### Post by kaivalagi on 2009-06-30
> **thecheeks said:**
> How do you get rid of the group name and the following '-'.

I just want screen names showing, no group name like (Buddies), the following dash, or status.

Take a look at the template option, run conkyPidgin -h for more info

You'll need to create a new template to use. Start by copying the template from /usr/share/conkypidgin/example/conkyPidgin.template and then remove what you don't want. Also look at /usr/share/conkypidgin/example/conkyrc for how a template is used in a conkyrc

Hope that helps

---

### Post by merlin_ie on 2009-06-30
Hi kaivalagi. I was wondering if you could help with something. I've added the Facebook plugin to pidgin, but in your script, it only shows the persons account number instead of name. I was wondering if it's even possible to show contacts name instead. Or do you have any other suggestions? I've added a screen shot so you can see what I see. Also, I was wondering about a word wrap for long status messages on msn. I've tried a few I read but no success. Thanks for your time

[IMG]http://i198.photobucket.com/albums/aa307/simply-delta/Facebook.png[/IMG]

---

### Post by kaivalagi on 2009-07-01
> **merlin_ie said:**
> Hi kaivalagi. I was wondering if you could help with something. I've added the Facebook plugin to pidgin, but in your script, it only shows the persons account number instead of name. I was wondering if it's even possible to show contacts name instead. Or do you have any other suggestions? I've added a screen shot so you can see what I see. Also, I was wondering about a word wrap for long status messages on msn. I've tried a few I read but no success. Thanks for your time


Well you have both [name] and [alias] available to use in a custom template, it might be worth playing with template options to see how you can display the details to your liking.

If that doesn't work for you I don't know what else could....it sounds like the facebook plugin doesn't provide what you want.

---

### Post by merlin_ie on 2009-07-01
I've not had a chance to muck around with the script but I've just noticed now that someone was online on Facebook and their name appears fine in the script. So, it's an offline issue. I'll try and take look at template later. Thanks for earlier reply

---

### Post by kaivalagi on 2009-07-01
> **merlin_ie said:**
> I've not had a chance to muck around with the script but I've just noticed now that someone was online on Facebook and their name appears fine in the script. So, it's an offline issue. I'll try and take look at template later. Thanks for earlier reply

The script has an option to only show online users...that's an option

---

### Post by Xerran on 2009-08-13
Can someone please help a noob? Conky is killed when I start Pidgin.

Thanks in advance.

---

### Post by kaivalagi on 2009-08-14
> **Xerran said:**
> Can someone please help a noob? Conky is killed when I start Pidgin.

Thanks in advance.

Have you tried running conkyPidgin in the terminal to see what happens?
Use the --verbose option with conkyPidgin and post back anything that looks like it might help explain things...

---

### Post by Xerran on 2009-08-14
> **kaivalagi said:**
> Have you tried running conkyPidgin in the terminal to see what happens?
Use the --verbose option with conkyPidgin and post back anything that looks like it might help explain things...


Hi, I ran "conkyPidgin --verbose" in terminal and got the following-->>

*** INITIAL OPTIONS:
    template: None
    onlineonly: False
    availableonly: False
    ignorelist: None
    includelist: None
    chattingtext: Chatting
    availabletext: Available
    unavailabletext: Unavailable
    invisibletext: Invisible
    awaytext: Away
    mobiletext: Mobile
    offlinetext: Offline
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Setting up dbus interface
INFO: Calling dbus interface for IM data

(I did not post the friends names for obvious reasons ;)

---

### Post by Xerran on 2009-08-14
> **Xerran said:**
> Hi, I ran "conkyPidgin --verbose" in terminal and got the following-->>

*** INITIAL OPTIONS:
    template: None
    onlineonly: False
    availableonly: False
    ignorelist: None
    includelist: None
    chattingtext: Chatting
    availabletext: Available
    unavailabletext: Unavailable
    invisibletext: Invisible
    awaytext: Away
    mobiletext: Mobile
    offlinetext: Offline
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Setting up dbus interface
INFO: Calling dbus interface for IM data

(I did not post the friends names for obvious reasons ;)
My "startupconky.sh" looks like this-->>

#!/bin/bash

sleep 20 &&

conky -c ~/.conky/conkymain &


(I'm not sure if this has anything to do with it)

---

### Post by kaivalagi on 2009-08-14
> **Xerran said:**
> My "startupconky.sh" looks like this-->>

#!/bin/bash

sleep 20 &&

conky -c ~/.conky/conkymain &


(I'm not sure if this has anything to do with it)

Sorry, no idea from that, I can't reproduce...

---

### Post by Xerran on 2009-08-14
> **kaivalagi said:**
> Sorry, no idea from that, I can't reproduce...

Will my [COLOR=Red]**["conkyPidgin.py"]("http://pastebin.com/m17493be6")**[/COLOR] file help?

---

### Post by kaivalagi on 2009-08-14
> **Xerran said:**
> Will my ["conkyPidgin.py"]("http://pastebin.com/m17493be6") help?

Not really

Pidgin just crashed on me, but without any conky running...it is not that stable...

You may need to decrease the refresh interval of the execi for conkyPidgin...

---

### Post by Xerran on 2009-08-14
> **kaivalagi said:**
> Not really

Pidgin just crashed on me, but without any conky running...it is not that stable...

You may need to decrease the refresh interval of the execi for conkyPidgin...

Please forgive me for being such a n00b, I am in the conkyPidgin.py file but do not know what to look for.

---

### Post by kaivalagi on 2009-08-14
> **Xerran said:**
> Please forgive me for being such a n00b, I am in the conkyPidgin.py file but do not know what to look for.

Your ~/.conky/conkymain file has the command to call conkyPidgin in it, that command may need adjusting so the refresh rate is lower
e.g. ${execi 1 conkyPidgin ...} or ${exec conkyPidgin ...} would become ${execi 5 conkyPidgin ...} so instead of refreshing every second it would every 5...

---

### Post by Xerran on 2009-08-14
> **kaivalagi said:**
> Your ~/.conky/conkymain file has the command to call conkyPidgin in it, that command may need adjusting so the refresh rate is lower
e.g. ${execi 1 conkyPidgin ...} or ${exec conkyPidgin ...} would become ${execi 5 conkyPidgin ...} so instead of refreshing every second it would every 5...

This is what I get in the .conkyrc file pertaining conkyPidgin:

${font Liberation Sans:style=Bold:size=8}PIDGIN $stippled_hr${font}${if_running pidgin}
${voffset 4}${execpi 10 ~/.scripts/conkyPidgin.py -o -s -l 5}${else}
${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}   Pidgin not running${endif}

---

### Post by Xerran on 2009-08-15
Kaivalagi, thank you so much for your help.

I was still having issues, I'm using the latest version of "conky-colors" so what I did was add Pidgin to "startup applications" then edited the conkystartup.sh file so that conky loads after 60 seconds and it is working out OK so far.

---

### Post by Chris-buntu on 2009-08-17
Nice script, is there anyway to just list the online users and not their personal messages, the group they're in & their statuses?

---

### Post by Xerran on 2009-08-17
> **Chris-buntu said:**
> Nice script, is there anyway to just list the online users and not their personal messages, the group they're in & their statuses?

I'm using [conky-colors]("http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328"). It may be what your looking for.

---

### Post by kaivalagi on 2009-08-18
> **Chris-buntu said:**
> Nice script, is there anyway to just list the online users and not their personal messages, the group they're in & their statuses?

Make a custom template in your home folder based on the one here: /usr/share/conkypidgin/example/conkyPidgin.template  and then use it by pointing to it with the --template option.

HTH

---

### Post by 3aTi3 on 2009-08-27
aaaargh , you should put the 'text_buffer_size 1024' line to the example conky config file! 

i sucked so much with this :D

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by daeron666 on 2009-11-15
Hi!!

There's a way to sort the contacts in groups?

Thanks,
Stefano.

---

### Post by kaivalagi on 2009-11-15
> **daeron666 said:**
> Hi!!

There's a way to sort the contacts in groups?

Thanks,
Stefano.

The only sort option available at present is based on log size using the   -s or  --sortbylogactivity option:

```
  -s, --sortbylogactivity
                        If used the list is sorted by most recent activity
                        first, this is useful when limiting the list size with
                        the limit option

```

Right now I am not in the position to make changes, I am learning ArchLinux and have no means to update the launchpad repo as yet.

I will be deciding on how I will support the scripts going forwards once I know what I can do in Arch and what best suits all Linux derivatives...

---

### Post by AlucardArg on 2009-11-18
> **kaivalagi said:**
> Yep, use the --template option. From conkyPidgin --help :

```
  -t FILE, --template=FILE
                        Template file determining the format for each buddy's
                        data. Use the following placeholders: [name], [alias],
                        [group], [status], [status_message].
```

So, you would create a simple template file using the placeholders mentioned above and then use it by adding a --template=/path/to/file option in your exec calls.

In theory just use one placeholder for alias and you just want a count...

Cheers

I was just going to ask that. Had to read whole 14 pages just to get that :P
Anyway, as you said, I made a template (named "conkyPidgin2.template") what just says "[alias]", and in conkyrc, I put:
```
${execi 60 conkyPidgin -o -t /usr/share/conkypidgin/example/conkyPidgin2.template | sed -n '$='}
```
in case that helps anyone :P

But most important, I wanted to thank you for such a GREAT script! Works like a charm, just like I wanted.
Thank you!

---

### Post by kaivalagi on 2009-11-18
> **AlucardArg said:**
> But most important, I wanted to thank you for such a GREAT script! Works like a charm, just like I wanted.
Thank you!

Thanks, much appreciated

---

### Post by markp1989 on 2009-12-28
any way to make this only show screen names , and ignore the status/personal message thing?


thanks Markp1989

---

### Post by kaivalagi on 2009-12-29
> **markp1989 said:**
> any way to make this only show screen names , and ignore the status/personal message thing?


thanks Markp1989

A custom template should suffice to display only names, take a look at /usr/share/conkypidgin/example/conkyPidgin.template to get started. You probably just need a file with this in:

```
[alias]
```

And if you want all your buddies online or not to show, no further options are necessary, other wise take a look at the orderering and filtering options in help:

```
conkyPidgin -h
```

HTH

---

### Post by markp1989 on 2009-12-29
> **kaivalagi said:**
> A custom template should suffice to display only names, take a look at /usr/share/conkypidgin/example/conkyPidgin.template to get started. You probably just need a file with this in:

```
[alias]
```

And if you want all your buddies online or not to show, no further options are necessary, other wise take a look at the orderering and filtering options in help:

```
conkyPidgin -h
```

HTH

thanks :D  im using this with dzen2 to show my online facebook friends,

thanks :D markp1989 

here is the script im using to print conkyPidgin in dzen2 (only just discovered this, its awesome)  if any one is interested 
```

#!/bin/bash 
FG='#ffffff'
BG='#000000'
#FONT='-*-terminus-*-r-normal-*-*-120-*-*-*-*-iso8859-*'
while true ; do

online=`conkyPidgin -o -t /home/mark/Desktop/pidgintemplate -I FaceBook |tr '\n' ':'`

    printf "%s\n" "$online"
    sleep 120
done | dzen2 -e '' -y '885' -h '15' -sa 'r'  -ta c -fg $FG -bg $BG -fn $FONT
```

my template file just has [alias] in it.

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

### Post by Taiebot65 on 2010-02-13
Hello i am a fan of the glx-dock project [http://www.glx-dock.org/index.php]("http://www.glx-dock.org/index.php") and would like to tell you that your applet is also working on a futur new applet that one of the developper is creating. This applet is called "donky" (dock + conky) and i am really happy with your current project and hope you will continue to improve it for both project...

[IMG][[img]http://uppix.net/6/4/3/9b4766c378e03c2692207ff6d6e4ftt.jpg[/img]](http://uppix.net/6/4/3/9b4766c378e03c2692207ff6d6e4f.png)[/IMG]

Thanks

---

### Post by majusio on 2010-03-31
How to disable the status of contacts in conkypidgin?

---

### Post by kaivalagi on 2010-04-01
> **majusio said:**
> How to disable the status of contacts in conkypidgin?

If you use a custom template you can decide on what shows and what doesn't based on it's content, is that what you mean?

Have a look at the example files in /usr/share/conkypidgin/example, the conkyrc has either with or without template calls on show and the conkyPidgin.template file has all available options in there, you can remove what you want in your own copy as you see fit.

Does that help?

---

### Post by margemoosh on 2010-08-25
is there anyway to show friends avatar in conky?

---

### Post by kaivalagi on 2010-08-25
> **margemoosh said:**
> is there anyway to show friends avatar in conky?

I am sure there is, I haven't built any functinoality for this script though (good call though!) but have done for my gtk-desktop-info apps pidgin plugin

If I find some time at the weekend I'll take a look at it

Cheers

---

### Post by b0wter on 2010-09-20
Hey, first of all I have to thank you for sharing and maintaining this amazing script! =D>

I'd be happy if you'll (someday) include a sorting feature that makes it possible to sort the list by names :)

---

### Post by kaivalagi on 2010-09-23
The sorting by name is on my todo list now along with avatar support....not sure when I'll have the time though, too much work and family commitments right now...

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkypidgin_2.13_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkypidgin_2.13_source.changes)

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

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkypidgin_2.14_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkypidgin_2.14_source.changes)

The apt packages should be available soon

---

### Post by achmonth on 2010-11-28
Will you be able to add an option showing which of my accounts are enabled? I have five separate accounts and don't use all of them all the time, so I'd love it if Conky could tell me which of them are enabled.
I love your script, btw :)

---

### Post by kaivalagi on 2010-11-28
Give the attached a whirl...just replace /usr/share/conkyPidgin/conkyPidgin.py with the contents of the attached tarball

Help details of use:
```
  -t FILE, --template=FILE
                        Template file determining the format for each buddy's
                        data or account info. Use the following placeholders
                        for default buddy output: [name], [alias], [group],
                        [status], [status_message]. If outputting an account
                        listing use these placeholders: [name], [protocol],
                        [status]
  -L, --accountlisting  Show account listing with status rather than buddies
```

Therefore to get output of accounts use -L, and you don't need to use a template file as there is a basic one defined like so:
```
[name] ([protocol]) - [status]
```
Which would result in something like this:
```
username@hotmail.com (MSN) - Disabled
username@irc.freenode.net (IRC) - Enabled
username@googlemail.com/ (XMPP) - Enabled
username (Yahoo) - Enabled
```

But if that's not to your liking then feel free to define one.

Let me know how you get on

Cheers

---

### Post by achmonth on 2010-11-30
Wow, this is really sweet! I love it.
A million and fifty-seven thanks :)

---

### Post by kaivalagi on 2010-12-01
> **achmonth said:**
> Wow, this is really sweet! I love it.
A million and fifty-seven thanks :)

Glad to be of service :)

I'll rollout a new package at some point soon, is it working okay for you as is?

---

### Post by achmonth on 2010-12-01
I'ts working as it's supposed to, yes. I'm wondering though - would you be able to add an option only showing the active accounts and not the inactive ones?

I'd like an option showing something like

```
[email]username@irc.freenode.net[/email] (IRC)
[email]username@googlemail.com[/email]/ (XMPP)
username (Yahoo)
```

instead of

```
[email]username@hotmail.com[/email] (MSN) - Disabled
[email]username@irc.freenode.net[/email] (IRC) - Enabled
[email]username@googlemail.com[/email]/ (XMPP) - Enabled
username (Yahoo) - Enabled
```

Or is this already possible via the template file?

(Btw - what did you do to make sure the example accounts didn't show as links?)

---

### Post by kaivalagi on 2010-12-01
New version attached, replace as before ;)

I reused the options for buddy listing filtering:
```
  -o, --onlineonly      Only show online buddies. [COLOR="Red"]If outputting account
                        listings this option limits it to enabled only.[/COLOR]
  -a, --availableonly   Only show available buddies. [COLOR="red"]If outputting account
                        listings this option limits it to enabled only.[/COLOR]
  -f, --offlineonly     Only show offline buddies. [COLOR="red"]If outputting account
                        listings this option limits it to disabled only.[/COLOR]
```

As for the emails not linking I have no idea, I just pasted the text straight into code tags

I also optimised the logic somewhat, no if the -L option is added it should be a lot faster as it wont go through all the buddy info grabbing process too

---

### Post by achmonth on 2010-12-01
That did it :D
This is all what I dared hope for. I kneel down and kiss the ground before you.
Thanks once more :)

---

### Post by kaivalagi on 2010-12-14
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added an --accountlisting / -L option to switch from buddy listings to your own account listings with status and protocol. This supports the template option also, see help for more info.
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkypidgin_2.15_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkypidgin_2.15_source.changes)

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

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by leomeloxp on 2011-04-29
Man, I have to say this XD You're a lifesaver, really.

Thanks for the great Plugin, are you still thinking about updating it? It seems to do everything someone could ask for already, just out of curiosity.

I was thinking, dunno if I can do it via template or using -W -A and stuff but... Can you order your contacts by the group they belong to?

I managed to sort via Status by adding -A v -W w -U x, but no groups (maybe some *if*s on the template, but I don't know how yet)

I'm not good with Python (really should learn a bit of it), I started to actually use Linux only a few months ago, but I can try to be of some help to make the group sorting possible. Let me know if you have anything.

Thanks again =D

---

### Post by kaivalagi on 2011-04-29
No sorting by groups is there, should be fairly straight forward to do...maybe change the --sortbylogactivity to a --sort="LOGACTIVITY" / --sort="NAME" / --sort="GROUP" with NAME being the default

I am not sure when I can find the time though....if I get bored over the long weekend I'll take a look...

---

### Post by leomeloxp on 2011-04-29
I see, I took a look at the code, kind of got how it work... What adds the -s option is line 84, isn't it?
```
self.parser.add_option("-s", "--sortbylogactivity", dest="sortbylogactivity",
default=False, action="store_true",
help=u"If used the list is sorted by most recent activity 
first, this is useful when limiting the list size with the limit option")
```If it is, I noticed it redirects to line 371 that starts this:

```
if self.options.sortbylogactivity == True:
                pidginDataList.sort(key=lambda obj: obj.activitydatetime,reverse=True)
            else:
                pidginDataList.sort()

            return pidginAccountDataList, pidginDataList

```I'll see if I can get any further, I know some logic, but none Python coding XD

Take your time with the code, I'll let you know if I get anything.

Thanks for the quick reply =] See you o/

---

### Post by kaivalagi on 2011-04-29
Don't worry, I decided to take a quick look and went on a lambda rampage :)

e.g.:
```

            # sort the list by option
            if self.options.sortby == "DEFAULT":
                pidginAccountDataList.sort(key=lambda obj: (str(obj.status)+obj.protocol.lower()+obj.name.lower()))
                pidginDataList.sort(key=lambda obj: (str(obj.status)+obj.group.lower()+alias.lower()))
            elif self.options.sortby == "NAME":
                pidginAccountDataList.sort(key=lambda obj: (obj.name.lower()+str(obj.status)+obj.protocol.lower()))
                pidginDataList.sort(key=lambda obj: (obj.name+obj.alias+obj.group+str(obj.status)))
            elif self.options.sortby == "ALIAS":
                pidginAccountDataList.sort(key=lambda obj: (obj.name.lower()+str(obj.status)+obj.protocol.lower()))
                pidginDataList.sort(key=lambda obj: (obj.alias+obj.name+obj.group+str(obj.status)))
            elif self.options.sortby == "GROUP":
                pidginAccountDataList.sort(key=lambda obj: (obj.name.lower()+str(obj.status)+obj.protocol.lower()))
                pidginDataList.sort(key=lambda obj: (obj.group+obj.name+obj.alias+str(obj.status)))
            elif self.options.sortby == "STATUS":
                pidginAccountDataList.sort(key=lambda obj: (obj.name.lower()+str(obj.status)+obj.protocol.lower()))
                pidginDataList.sort(key=lambda obj: str(obj.status)+obj.name+obj.alias+obj.group)
            elif self.options.sortby == "LOGACTIVITY":
                pidginAccountDataList.sort(key=lambda obj: (str(obj.status)+obj.protocol.lower()+obj.name.lower()))
                pidginDataList.sort(key=lambda obj: obj.activitydatetime,reverse=True)
            else:
                raise Exception("Invalid sortby option provided")

```

I won't have time to release the package today (launchpad is being reallllllly slowly i.e. 20 hours for a build) but find attached a marginally tested new version of the .py file....let me know if that works for you!

Here's the help listing for the --sortby method:

```
 -s METHOD, --sortby=METHOD
                        [default: DEFAULT] Sort options for both buddy and
                        account listings. These are DEFAULT, NAME, ALIAS,
                        GROUP, STATUS or LOGACTIVITY. ALIAS, GROUP and
                        LOGACTIVITY sort options are not applicable for
                        account listings so appropriate sorting methods are
                        used instead. LOGACTIVITY is useful when limiting the
                        list size with the limit option.

```

Have fun :)

---

### Post by kaivalagi on 2011-04-29
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated to have a --sortby option replacing the --sortbylogactivity option. It takes the following values of DEFAULT, NAME, ALIAS, GROUP, STATUS or LOGACTIVITY. ALIAS, GROUP and LOGACTIVITY sort options are not applicable for account listings so appropriate sorting methods are used instead.
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkypidgin_2.16_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkypidgin_2.16_source.changes)

The apt packages should be available soon

[COLOR="Red"]**edit: Ubuntu/Debian/#! users may be waiting a while, estimated to be a tomorrow build completion date according to launchpad! Arch users will have the change already though :p**[/COLOR]

---

### Post by leomeloxp on 2011-04-29
Wow, that was quick XDD

Thank you very much. I just need to find my way to update it now (or wait for the ppa, which won't take that long anyway)

But yeah, this plugin is great, saves me lots of space on screen and time.

Thank you =D

--------
Edit:

One more thing, this is more for discussion, I don't know if it is your plug in that could solve it. 

I have some merged contacts on Pidgin (same people different protocols kind of thing). 
ConkyPidgin shows them as different contacts, which I think it is expected... Would there be a way of hiding them or just showing one "meta contact"?

See you o/

---

### Post by kaivalagi on 2011-04-29
if you sudo copy the attached .py file a couple of posts back over the top of /usr/share/conkypidgin/conky/pidgin.py that should do it...

If I find time I'll look at an option to "thin out" same named buddies from varying IM networks....going on the aliases would be best right? So same aliases is ignored?

---

### Post by leomeloxp on 2011-04-29
Did it now XD It took me a bit to find the .py file ^^'

Anyway, I tried aliases already, they just show one right under another XD

I don't really know how to do this, if Pidgin had a better support for Meta Contacts, like (I suppose) Kopete has. But that's not for us to work on, still depends on the developers.

Anyway, the sorting works like a charm, thanks again =]

---

### Post by kaivalagi on 2011-04-29
> **leomeloxp said:**
> Did it now XD It took me a bit to find the .py file ^^'

Anyway, I tried aliases already, they just show one right under another XD

I don't really know how to do this, if Pidgin had a better support for Meta Contacts, like (I suppose) Kopete has. But that's not for us to work on, still depends on the developers.

Anyway, the sorting works like a charm, thanks again =]

I hadn't added any alias removal yet....try the attached with the --distinctaliases option

---

### Post by leomeloxp on 2011-04-29
Ha ha =D It worked!

It is a pretty smart work around. Thanks once again XD

---

### Post by kaivalagi on 2011-04-30
No worries, bear in mind the next (the one already posted and taking forever to publish) release will not include the alias stuff (still not built on launchpad!) so just be aware when you update you might want to overwrite with the tarball here again!

---

### Post by kaivalagi on 2011-05-01
**[COLOR=Blue][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated to have a --distinctaliases option which when requested will remove any duplicate aliases found before outputting
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkypidgin_2.17_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkypidgin_2.17_source.changes)

The apt packages should be available soon

---

### Post by lurker_man on 2011-08-15
Hi all, my first post :D

I was just wondering if there is a way to have the script return only the amount of contacts in total and how many of them are online? I just want a summary to be displayed in my Conky so I don't really have a need for a list of the actual buddies online. 

Thanks for the script btw, I've only been using Linux for about three weeks now but I'm already starting to build up a good understanding thanks to your posts!

---

### Post by leomeloxp on 2011-08-15
Hello lurker man, and welcome to Linux =]

I don't really know how to do it yet (and I'm not currently on my computer) but If you try to do it from terminal it might work...

Look on to the output managing commands (eg grep), I remember that one of them show how many lines the output text has, that would be your total contacts, and with a filter to show only the online ones and the same command you can see the online only number =].

That's a rough workaround, if Kaivalagi sees this post soon (or someone else with more knowledge than me) they might be able to help you better.

Tell me if you get anything o/

---

### Post by joypunk on 2012-02-04
I'm having an issue getting my alignment to display correctly.

My conkyPidgin.template is:

```
[alias]${alignr}[status]
```

However, it only aligns the first entry correctly, everything else is aligned right, like this:

```
UserName             Status
             UserNameStatus
             UserNameStatus
             UserNameStatus
```

My .conkyrc code is as follows:

```
${execpi 60 conkyPidgin -o -s ALIAS --distinctalias -t ~/.config/conkyPidgin/conkyPidgin.template }
```

Any ideas?

---

### Post by Sector11 on 2012-02-04
> **joypunk said:**
> Any ideas?

Conky v1.8.1 has problems with spacing using ${goto xx} ${alignc} ${alignr} etc etc.

If that's the problem the fix is to drop back to v1.8.0

 OR use hard spaces in your template.

---

### Post by stevehaworth on 2012-04-06
I had this same issue with the 1st contact.

I prepended my call to conkyPidgin with an {alignr}, and also have the one within the template file- and it all lines up for me now.

.conkyrc:
${alignr 20}${execpi 60 conkyPidgin ...

Template file:
[alias]${alignr 20}[status]


Steve

---

### Post by stevehaworth on 2012-04-09
I've been having some fun with this and your other scripts
Pushing my buddy list to the background is handy as heck!!

One thing I have been trying to do though is to use the status text replacement options- and set a different color for each status.

I've tried doing so with different string options right in the "execpi", and in the python script.  Anything I try seems to break the script.

I know I much be missing something fundamental here- but is there a way to set colors on the [status] using the status replacement strings?

Thanks again!!
Steve

---

