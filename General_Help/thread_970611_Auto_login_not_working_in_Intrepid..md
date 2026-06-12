---
title: "Auto login not working in Intrepid."
date: 2008-11-04
forum: General Help
---

### Post by edhgoose on 2008-11-04
I've used gdmsetup (System/Administration/Login Window) to check the Auto Login and have it automatically log my username in. It worked fine in Hardy, but no longer in Intrepid.

The gdm.conf file has the correct values too.

How do I fix this?

Many thanks,

Goose

---

### Post by mindwarp on 2008-11-04
Please post the output of:

cat /etc/gdm/gdm.conf
and
cat /etc/gdm/gdm.conf-custom

---

### Post by cybrsaylr on 2008-11-04
Auto login works fine in Intrepid for me.

---

### Post by edhgoose on 2008-11-07
Sorry it took me a couple of days, here you go:

cat /etc/gdm/gdm.conf:

```

# How long gdm should wait before it assumes a started Xserver is defunct and
# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
GdmXserverTimeout=10

[security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=false
# Allow login as root via XDMCP.  This value will be overridden and set to
# false if the /etc/default/login file exists and contains
# "CONSOLE=/dev/login", and set to true if the /etc/default/login file exists
# and contains any other value or no value for CONSOLE.
AllowRemoteRoot=false
# This will allow remote timed login.
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions.
RelaxPermissions=1
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# If your HOME is managed by automounter, set to true
SupportAutomount=false
# Number of seconds to wait after a failed login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line, a
# good default to have (why is this a "negative" setting? because if it is
# false, you could still not allow it by setting command line of any particular
# server).  It's probably better to ship with this on since most users will not
# need this and it's more of a security risk then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do not add
# a "-nolisten tcp", as then the query just wouldn't work, so this setting only
# affects truly attached sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS by
# detecting "root-squashing".  It seems bad practice to place cookies on things
# that go over the network by default and thus we do not do it by default.
# Sometimes you can however use safe remote filesystems where this is OK and
# you may want to have the cookie in your home directory.
#NeverPlaceCookiesOnNFS=true
# Will cause PAM_DISALLOW_NULL_AUTHTOK to be passed as a flag to
# pam_authenticate and pam_acct_mgmt, disallowing NULL password.  This setting
# will only take effect if PAM is being used by GDM.  This value will be
# overridden with the value from /etc/default/login if it contains
# "PASSREQ=[YES|NO]"
#PasswordRequired=false
# Specifies the PAM Stack to use, "gdm" by default.
PamStack=gdm
# GDM allows configuration of how ut_line is set when it does utmp/wtmp and
# audit processing.  If VT is being used, then ut_line will be set to the
# device associated with the VT.  If the console is attached and has a device
# name specified in the [servers] section, then this value will be used.
# Otherwise the value is defaulted to the value specified in UtmpLineAttached
# for attached displays and UtmpLineRemote for remote displays.  The value
# can be left empty which means that ut_line will be set to an empty value
# (if not VT and no value specified in the [servers] section.  The values
# can contain "%d" which is translated to the DISPLAY value or %h which
# is translated to the hostname.  The values for both keys  must begin with
# "/dev/".
UtmpLineAttached=/dev/console
UtmpLineRemote=
# If true and the specified UtmpLineAttached or UtmpLineRemote does not exist,
# then create a pseudo-device filename that will be touched when the utmp
# record is updated.  Creating such a psuedo-device ensures that programs
# that stat the utmp device associated with ut_line such as finger, last,
# etc. work in a reasonable way.  
UtmpPseudoDevice=false

# XDMCP is the protocol that allows remote login.  If you want to log into GDM
# remotely (I'd never turn this on on open network, use ssh for such remote
# usage).  You can then run X with -query <thishost> to log in, or
# -indirect <thishost> to run a chooser.  Look for the 'Terminal' server type
# at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
# Honor indirect queries, we run a chooser for these, and then redirect the
# user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests.
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time.
#MaxSessions=16
# Maximum wait times.
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way.
#Port=177
# Willing script, none is shipped and by default we'll send hostname system id.
# But if you supply something here, the output of this script will be sent as
# status of this host so that the chooser can display it.  You could for
# example send load, or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc that
# we need.  Unless you need a specific gtkrc that doesn't correspond to a
# specific theme, then just use the GtkTheme key.
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the GUI.
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does not yet
# have this ability.
#AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can also
# specify 'all' to allow all installed themes.  These should be just the
# basenames of the themes such as 'Thinice' or 'LowContrast'.
#GtkThemesToAllow=all

# Maximum size of an icon, larger icons are scaled down.
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# The following options for setting titlebar and setting window position are
# only useful for the standard login (gdmlogin) and are not used by the
# themed login (gdmgreeter).
#
# The standard login has a title bar that the user can move.
#TitleBar=true
# Don't allow user to move the standard login window.  Only makes sense if
# TitleBar is on.
#LockPosition=false
# Set a position for the standard login window rather then just centering the
# window.  If you enter negative values for the position it is taken as an
# offset from the right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0

# Enable the Face browser.  Note that the Browser key is only used by the
# standard login (gdmlogin) program.  The Face Browser is enabled in
# the Graphical greeter by selecting a theme that includes the Face
# Browser, such as happygnome-list.  The other configuration values that
# affect the Face Browser (MinimalUID, DefaultFace, Include, Exclude,
# IncludeAll, GlobalFaceDir) are used by both the Standard and Themed
# greeter.
Browser=true
# The default picture in the browser.
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the face
# browser or in the gdmselection list for Automatic/Timed login.  They will not
# be displayed regardless of the settings for Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in the
# gdmsetup selection list for Automatic/Timed login.  Users should be separated
# by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from the
# gdmsetup selection list for Automatic/Timed login.  Excluded users will still
# be able to log in, but will have to type their username.  Users should be
# separated by commas.  
Exclude=nobody
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users will be
# displayed except users excluded via the Exclude setting and user ID's less
# than MinimalUID.  Scanning the password file can be slow on systems with
# large numbers of users and this feature should not be used in such
# environments.  The setting of IncludeAll does nothing if Include is set to a
# non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture.
#GlobalFaceDir=/usr/share/pixmaps/faces/

# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with GDM and edit it.  It is not a standard locale.alias
# file, although GDM will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter.
Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# Logo shown on file chooser button in gdmsetup (do not modify this value).
#ChooserButtonLogo=/usr/share/pixmaps/gdm-foot-logo.png
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true

# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however.
#SystemMenu=true
# Configuration is available from the system menu of the greeter.
ConfigAvailable=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user to
# connect to some remote host.  Local XDMCP does not need to be enabled,
# however.
#ChooserButton=true

# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome to
# "Welcome" and for DefaultWelcome to "Welcome to %n", and properly translate
# the message to the appropriate language.  Note that %n gets translated to the
# hostname of the machine.  These default values can be overridden by setting
# DefaultWelcome and/or DefaultRemoteWelcome to false, and setting the Welcome
# and DefaultWelcome values as desired.  Just make sure the strings are in
# utf-8 Note to distributors, if you wish to have a different Welcome string
# and wish to have this translated you can have entries such as
# "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n

# Xinerama screen we use to display the greeter on.  Not for true multihead,
# currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
# The Standard greeter (gdmlogin) uses BackgroundColor as the background
# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor
# as the background color.
BackgroundColor=#dab082
GraphicalThemedColor=#dab082
# XDMCP session should only get a color, this is the sanest setting since you
# don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true

# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# If this is true then the background program is run always, otherwise it is
# only run when the BackgroundType is 0 (None).
#RunBackgroundProgramAlways=false
# Delay before starting background program
#BackgroundProgramInitialDelay=30
# Should the background program be restarted if it is exited.
#RestartBackgroundProgram=true
# Delay before restarting background program
#BackgroundProgramRestartDelay=30

# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode
# where the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=auto
# Do not show any visible feedback in the password field. This is standard for
# instance in console, xdm and ssh.
#UseInvisibleInEntry=false

# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=bijou/:blueswirl/:circles/:debblue-list/:debblue/:ayo/:debian-dawn/:debian-greeter/:debian/:glassfoot/:hantzley/:happygnome/:industrial/:crystal/:linsta
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false

# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font to
# be used when displaying the contents of the file.
#InfoMsgFont=Sans 24

# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
#SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
# user successfully logs in.
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
# user fails to log in.
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# Specifies a program to be called by the greeter/login program when the
# initial screen is displayed.  The purpose is to provide a hook where files
# used after login can be preloaded to speed performance for the user. The
# program will only be called once only, the first time a greeter is displayed.
# The gdmprefetch command may be used.  This utility will load any libraries
# passed in on the command line, or if the argument starts with a "@"
# character, it will process the file assuming it is an ASCII file containing a
# list of libraries, one per line, and load each library in the file.
PreFetchProgram=/usr/lib/gdm/gdmprefetch @/etc/gdm/gdmprefetchlist

# The chooser is what's displayed when a user wants an indirect XDMCP session,
# or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts.
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png.
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are scanning
# actually, we continue to listen even after this has expired).
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to a
# query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer.
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced
# when officially registered xdmcp multicast address of TBD will be available.
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names.
#AllowAdd=true

[debug]
# This will cause GDM to send debugging information to the system log, which 
# will create a LOT of output.  It is not recommended to turn this on for
# normal use, but it can be useful to determine the cause when GDM is not
# working properly.
Enable=false
# This will enable debug messages for accessibilty gesture listeners into the
# syslog.  This includes output about key events, mouse button events, and
# pointer motion events.  This is useful for figuring out the cause of why the
# gesture listeners may not be working, but is too verbose for general debug.
Gestures=false

# Attached DISPLAY Configuration
#
[servers]
# This section defines which attached DISPLAYS should be started by GDM by
# default.  You can add as many DISPLAYS as desired and they will always be
# started.  The key for each entry must be a unique number that cooresponds to
# the DISPLAY number to start the X server.  For a typical single-display
# machine, there will only be one entry "0" for DISPLAY ":0".  The first word
# in the value corresponds to an X server definition in the "X Server
# Definitions" section of the configuration file.  For example, the entry:
#
# 0=Standard
#
# Means that DISPLAY ":0" will start an X server as defined in the 
# [server-Standard] section.
#
# The optional device argument is used to specify the device that is associated
# with the DISPLAY.  When using Virtual Terminals (VT), this value is ignored
# and GDM will use the correct device name associated with the VT.  If not
# using VT, then GDM will use the value specified by this optional argument.
# If the device argument is not defined, then GDM will use the default setting
# for attached displays defined in the UtmpLineAttached configuration option.
# For the main display (typically DISPLAY ":0"), "/dev/console" is a reasonable
# value.  For other displays it is probably best to not include this argument
# unless you know the specific device associated with the DISPLAY.  The device
# value can contain "%d" which is translated to the DISPLAY value or %h which
# is translated to the hostname.
#
0=Standard device=/dev/console

# Example of how to set up DISPLAY :1 to also use Standard.
#1=Standard

# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

# X Server Definitions
#
# Note: Is your X server not listening to TCP requests?  Refer to the 
# security/DisallowTCP setting!

[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

#priority=0

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/X11R6/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params anyway,
# and terminate would be bad for xdmcp choosing).  You can make a terminal
# server flexible, but not with an indirect query.  If you need flexible
# indirect query server, then you must get rid of the -terminate and the only
# way to kill the flexible server will then be by Ctrl-Alt-Backspace.
flexible=false
# Do not handle this X server for attached displays.
handled=false

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you wish to
# allow a chooser server then make this true.  This is the only way to make a
# flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a machine they
# will get this same server but run with "-terminate -query hostname".
chooser=true

[customcommand]
# This section allows you specify up to 10 custom commands. Each of the
# commands can be defined by the seven parameters listed below. In each of the
# descriptions of the parameters N can take on any values between 0 and 9,
# i.e. CustomCommand0=,CustomCommand1=,...,CustomCommand9=.  The  numbers
# can have gaps as long as they fit within predefined set of 10, and their
# placement order within this section and with respect to each other is
# not important.
#
# CustomCommandN, CustomCommandTextN, CustomCommandLabelN, 
# CustomCommandLRLabelN, CustomCommandTooltipN, CustomCommandIsPersistentN
# and CustomCommandNoRestartN should all be defined for a given integer N, 
# where N can be a number from 0-9 (if not the default values will be 
# assigned except CustomCommandN for which no default exists).

# Custom command to run.  Multiple commands may be specified separated by 
# semicolons.  GDM will use the first valid command.  Examples:
# /sbin/bootwindoze;/usr/bin/bootwindoze, or
# /sbin/runupdate;/usr/local/sbin/runupdate
#
#CustomCommandN=

# Custom command dialog message that will appear on all warning dialogs.
# This will vary depending on what you want to do. Examples:
# Are you sure you want to restart system into Windoze?, or
# Are you sure you want do do this?
#CustomCommandTextN=

# Custom command label that will appear as stock label on buttons/menu items.
# This option can't contain any semicolon characters (i.e. ";").
# Examples:
# _Windoze, or
# _Update Me
#CustomCommandLabelN=

# Custom command label that will appear as stock label on radio buttons/list
# items.  The underscore indicates the mnemonic used with this item.  Examples:
#   Restart into _Windoze
#   Perform system _Update
#CustomCommandLRLabelN=

# Custom command tooltip. Examples
# Restarts the computer into Windoze
# Updates the computer software to the most recent version(s)
#CustomCommandTooltipN=

# Custom command persistence option. Setting it to true will allow this
# command to appear outside the login manager, e.g. on the desktop through 
# Log Out/Shut Down dialogs. The default value is false.
#CustomCommandIsPersistentN=

# Custom command gdm/system restart option. Setting it to true will not
# restart gdm after command execution.  The default commands (reboot, shut
# down) all reboot the system by default which is why the default setting
# is true.
# In addition when corresponding CustomCommandIsPersistentN option is set to
# true, setting CustomCommandNoRestartN to false will place CustomCommandN
# in the Shut Down dialog set of actions, setting it to true will place
# CustomCommandN in the Log Out dialog set of actions.
#CustomCommandNoRestartN=
#
# Example layout for more than one command:
#CustomCommand0=
#CustomCommandText0=
#CustomCommandLabel0=
#CustomCommandLRLabel0=
#CustomCommandTooltip0=
#CustomCommandIsPersistent0=
#CustomCommandNoRestart0=
#
#CustomCommand1=
#CustomCommandText1=
#CustomCommandLabel1=
#CustomCommandLRLabel1=
#CustomCommandTooltip1=
#CustomCommandIsPersistent1=
#CustomCommandNoRestart1=
#
# and so on

```

and cat /etc/gdm/gdm.conf-custom

```

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# Older versions of GDM used the "gdm.conf" file for configuration.  If your
# system has an old gdm.conf file on the system, it will be used instead of
# this file - so changes made to this file will not take effect.  Consider
# migrating your configuration to this file and removing the gdm.conf file.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# /usr/share/gdm/defaults.conf file for information about each option.  Also
# refer to the reference documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]




AutomaticLogin=goose




TimedLogin=goose

TimedLoginDelay=10

[security]

[xdmcp]

[gui]

[greeter]

























[chooser]

[debug]

[servers]

```

Hope this reveals something! Cheers!

---

### Post by edhgoose on 2008-11-11
Anyone able to shed some light on this?

Cheers

---

### Post by lithorus on 2008-11-12
I have the same problem. One thing I've noticed is that it seems that my system tries to start gdm premature and it crashes on first try.

---

### Post by gogreenpower on 2008-11-12
im having the same problem, could it be the customized login screen im using?

---

### Post by edhgoose on 2008-11-12
I'm not using a custom login screen, so I don't think thats the problem.

All I've done is upgraded Hardy to Intrepid. In Hardy it worked, in Intrepid it doesn't. I've not customised anything else, at least as far as I know anyway.

---

### Post by gogreenpower on 2008-11-12
i have the time delay login working but still no auto login

---

### Post by OfMacandMen on 2008-12-06
You have to add the following lines to the /etc/gdm/gdm.conf-custom

[daemon]

AutomaticLoginEnable=true

AutomaticLogin=username

---

### Post by eternalnewbee on 2008-12-06
How about saving the session?
**Main Menu > System > Preferences > Sessions > Options**, and click **Save Currently running applications**.

---

### Post by jmacx81 on 2008-12-06
When I go to System>Administration>Login Window I get this 

"Failed to run /usr/sbin/gdmsetup as user root."

"Unable to copy the user's Xauthorization file."

I never would have seen this if I wouldn't have looked at this thread.

---

