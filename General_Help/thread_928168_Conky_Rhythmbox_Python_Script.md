---
title: "Conky Rhythmbox Python Script"
date: 2008-09-23
forum: General Help
---

### Post by kaivalagi on 2008-09-23
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE=3][COLOR=Blue]Intro[/COLOR][/SIZE]_**

This is a simple script to display what is current playing in Rhythmbox. The script talks to Rhythmbox using dbus, and allows the outputting of track info and the use of templates...

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
sudo apt-get update && sudo apt-get install conkyrhythmbox

```

**[COLOR=Blue]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyRhythmbox script to point to the correct location where conkyRhythmbox.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

You can get the current help options at any time by running (change the path as necessary):

```

conkyRhythmbox -h

```or

```

conkyRhythmbox --help

``````
Usage: conkyRhythmbox [options]
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
                        BR (bitrate k/s), LE (length), PP (current position in
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

```**_[SIZE=3][COLOR=Blue]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkyrhythmbox"]https://code.launchpad.net/~conky-companions/+junk/conkyrhythmbox
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by HippyRandall on 2008-09-23
W00T!!!
I can now get rid of exaile! at least until they come out with 0.3 or w/e it is. Thanks man. Now to figure out a new layout...

Hippy

---

### Post by kaivalagi on 2008-09-23
I couldn't help myself, I found out how to get the dbus info for Rhythmbox so had to do it!

I am switching to Rhythmbox now too...

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

### Post by mp3_freak_721 on 2008-09-25
Noob here: how do you put it into you config file?

---

### Post by kaivalagi on 2008-09-26
> **mp3_freak_721 said:**
> Noob here: how do you put it into you config file?

Okay, if you install this using method 1 all the hard work is done for you without any possible problems...

Once you have installed the script can be run from the command line and through an exec call in conky as "conkyRhythmbox"

There is an example provided with the install, which if you open in an editor you'll see how things work. The file is: /usr/share/conkyrhythmbox/example/conkyrc

To run this example conky for this script, the following should be entered into the terminal:

```
conky -c /usr/share/conkyrhythmbox/example/conkyrc

```

All of this is in the README.txt file attached in the first post of this thread, I suggest you have a quick read :)

Any issues just ask...

---

### Post by kaivalagi on 2008-10-04
[COLOR="DarkGreen"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

The script has been updated and is available in the first post and via apt, the changes are as follows:

[LIST]
[*]Updated script to now use "[" and "]" as template brackets rather than "{" and "}" so that the execp/execpi conky command can be used, this enables the use of $font, $color options in the template which conky will then make adjustments for in the output!
[*]Updated example files to use new template functionality with execpi in conky
[*]Updated README for usage changes
[/LIST]

Note the change to templates, [] rather than {} for options now....

Have fun

---

### Post by daveg on 2008-10-25
I guess you didn't realise this, but there's already a command that does this which is part of the rhythmbox package (and has been for quite some time) called rhythmbox-client:

```
$ rhythmbox-client --help
Usage:
  rhythmbox-client [OPTION...]

Help Options:
  -?, --help                 Show help options

Application Options:
  --debug                    
  --no-start                 Don't start a new instance of Rhythmbox
  --quit                     Quit Rhythmbox
  --no-present               Don't present an existing Rhythmbox window
  --hide                     Hide the Rhythmbox window
  --next                     Jump to next song
  --previous                 Jump to previous song
  --notify                   Show notification of the playing song
  --play                     Resume playback if currently paused
  --pause                    Pause playback if currently playing
  --play-pause               Toggle play/pause mode
  --play-uri=URI to play     Play a specified URI, importing it if necessary
  --enqueue                  Add specified tracks to the play queue
  --clear-queue              Empty the play queue before adding new tracks
  --print-playing            Print the title and artist of the playing song
  --print-playing-format     Print formatted details of the song
  --set-volume               Set the playback volume
  --volume-up                Increase the playback volume
  --volume-down              Decrease the playback volume
  --print-volume             Print the current playback volume
  --mute                     Mute playback
  --unmute                   Unmute playback
```

---

### Post by kaivalagi on 2008-10-25
> **daveg said:**
> I guess you didn't realise this, but there's already a command that does this which is part of the rhythmbox package (and has been for quite some time) called rhythmbox-client:

Yes, I did know it was there, but this script allows for easier and better formatting of output, especially via a template file and the execpi/execp conky commands...

rhythmbox-client is great for controlling the music player from the console, but unless users want to spend hours on grep, sed and cut commands to strip and format the required details, it isn't a great tool to display current song details.

Your call if you want to use the script or not :)

---

### Post by champs on 2008-10-29
I gave the Rhythmbox a go..... working my way through your signature links.

It worked a treat, straight away, but I have noticed that when the song changes, a line from the previous line gets left behind, and pushes everything else up a line or two.

Screenshots below are from the 5th and 9th songs, and after the last song of the album finished.

---

### Post by cl0ckwork on 2008-10-29
> **champs said:**
> I gave the Rhythmbox a go..... working my way through your signature links.

It worked a treat, straight away, but I have noticed that when the song changes, a line from the previous line gets left behind, and pushes everything else up a line or two.

Screenshots below are from the 5th and 9th songs, and after the last song of the album finished.

i have been noticing the same thing.
i just restart conky and it goes away ^_^

---

### Post by kaivalagi on 2008-10-29
> **champs said:**
> I gave the Rhythmbox a go..... working my way through your signature links.

It worked a treat, straight away, but I have noticed that when the song changes, a line from the previous line gets left behind, and pushes everything else up a line or two.

Screenshots below are from the 5th and 9th songs, and after the last song of the album finished.

Can you post the relevant part of your conkyrc and the template.

I have no issues, and am using the following:

conkyrc:

```
TEXT
${if_running rhythmbox}${color3}${execibar 1 conkyRhythmbox --datatype=PP}
${execp conkyRhythmbox --template=/home/mark/Scripts/conky/conkyRhythmbox.template}${endif}
```

template:

```
${color3}${font Liberation Sans:style=Bold:size=10}${alignr 320}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${font Liberation Sans:style=Bold:size=12}${alignr 320}[--datatype=TI]
${font Liberation Sans:style=Italic:size=11}${alignr 320}[--datatype=AR]
${font}${alignr 320}[--datatype=AL]
```

---

### Post by champs on 2008-10-29
rhythmbox.conf

```

TEXT
${font arial:size=10}${color2}RHYTHMBOX ${hr 2}$color
${font arial:size=8}${if_running rhythmbox}${execp conkyRhythmbox --template=/etc/conky/rhythm.template}${endif}

```

rhythm.template

```

${color1}Artist:  ${color}[--datatype=AR]
${color1}Album:  ${color}[--datatype=AL]
${color1}Title:  ${color}[--datatype=TI]
${color1}Position:  ${color}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color1}Rating:  ${color}[--datatype=RT]
${color1}Volume:  ${color}[--datatype=VO]

```

---

### Post by kaivalagi on 2008-10-30
> **champs said:**
> I gave the Rhythmbox a go..... working my way through your signature links.

It worked a treat, straight away, but I have noticed that when the song changes, a line from the previous line gets left behind, and pushes everything else up a line or two.

Screenshots below are from the 5th and 9th songs, and after the last song of the album finished.

> **cl0ckwork said:**
> i have been noticing the same thing.
i just restart conky and it goes away ^_^

Well, I have tried to reproduce the error and can't, I don't think it is a problem with the script, I suspect conky has some issues with execp commands?

Can you try changing the "execp" with "execpi 1" and then see whether the problem remains? failing that try using the exec command with an alternative template without the {} formatting text, and see whether you still get issues...

What versions of conky are you running? I am running 1.6.1 in Hardy (compiled from source)

```
conky -v
```

It might be worth asking the same questions on the conkyrc thread in case someone else has seen this before...

I am not sure how much help I can provide here

---

### Post by champs on 2008-10-30
1.5.1 on Hardy from repos

---

### Post by kaivalagi on 2008-10-30
> **champs said:**
> 1.5.1 on Hardy from repos

In that case can you try using exec instead of execp to see whether this stops the issue....I suspect execp and execpi have been tweaked quite a bit since that version....

I assume you are upgrading to Intrepid in a couple of days or so? If not I recommend you compile conky from source, see [http://conky.sourceforge.net](http://conky.sourceforge.net) for the tarball.

Cheers

---

### Post by champs on 2008-11-01
2.6.27-7 and conky 1.61 seem to have fixed the issue.....

I won't go into how long it took to get the new kernel to work.... painful...

---

### Post by kaivalagi on 2008-11-01
> **champs said:**
> 2.6.27-7 and conky 1.61 seem to have fixed the issue.....

I won't go into how long it took to get the new kernel to work.... painful...

Yeah, intrepid was painful for me too, I had to install from scratch using an ext2 partition. Everythings okay now though :)

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

### Post by anxiousdog on 2008-11-02
I'm using Intrepid now and this script is working, but I keep getting the following in my terminal over and over until I kill Conky. Is there a fix?

```
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
sh: Su: not found
sh: Su: not found
sh: Su: not found
sh: Su: not found
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
sh: Su: not found

```

---

### Post by kaivalagi on 2008-11-03
> **anxiousdog said:**
> I'm using Intrepid now and this script is working, but I keep getting the following in my terminal over and over until I kill Conky. Is there a fix?

```
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
sh: Su: not found
sh: Su: not found
sh: Su: not found
sh: Su: not found
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
ERROR: Issue calling the dbus service:org.freedesktop.DBus.GLib.UnmappedError.RbShellPlayerError.Code4: Playback position not available
sh: Su: not found

```

The "Playback position not available" is a known issue, it happens when the script is half way through determining all the details for a song, and the song changes. I am not sure why the "SU: not found" error is occuring. I assume you are getting conky output for your songs?

If conky is started in a session instead, you wont get bombarded with these error messages...as there is no originating terminal window for the script.

I could remove the error messages altogether, but in doing so will also remove the messages that need to be displayed if there is a real problem.

At some point in the week I'll have a look and see what I can do...

---

### Post by anxiousdog on 2008-11-03
> **kaivalagi said:**
> The "Playback position not available" is a known issue, it happens when the script is half way through determining all the details for a song, and the song changes. I am not sure why the "SU: not found" error is occuring. I assume you are getting conky output for your songs?

If conky is started in a session instead, you wont get bombarded with these error messages...as there is no originating terminal window for the script.

I could remove the error messages altogether, but in doing so will also remove the messages that need to be displayed if there is a real problem.

At some point in the week I'll have a look and see what I can do...

Eh, leave the error. I'll just reboot and that will fix that part. :)

I'm not sure why I have the sh:su error either. This is my conkyrc and the error I'm getting. I've posted that I do have an error with your gcal as well.

```
anxiousdog@ubuntu1:~$ killall conky
anxiousdog@ubuntu1:~$ conky &
[1] 26979
anxiousdog@ubuntu1:~$ Conky: desktop window (1c000b1) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x2c00001)
Conky: drawing to double buffer
ERROR: GoogleCalendarEngine Initialisation:Unexpected error:'root'
sh: Su: not found

```

```
# conky configuration
# edited by Mark Buck (Kaivalagi) <m_buck@hotmail.com>

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 0
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 45

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

# colours
color1 white
# pink
color2 ff3399
# pink again
color3 ff3399
# blue
color4 9dd7ff
# red
color5 CC0000

text_buffer_size 2048

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${voffset 5}${font Impact:size=55}${time %I:%M}$font
${voffset -70}${font Impact:size=14}${color1}$alignr${time %A}
$alignr${time %B %d}
$alignr${time %Y}$font
${execpi 1800 conkyForecast --location=UKXX0103 --template=/usr/share/conkyforecast/example/conkyForecast.template --imperial}
${color0}${hr 1}$color
${font Awesome 80s,:size=30}${color1}g${font Disko:size=30}${color2}What's Doin'
${color1}${font Print Bold:size=14}${execi 600 conkyGoogleCalendar --username=username --password=password --daysahead=8 --limit=5 --requestCalendarNames="kids"}
${color1}${font Mono:size=8}${pre_exec cal -3 | cut -c23-64 | sed 's/^/   /' }
${voffset -78}${color1}${font Bitstream Vera Sans Mono:size=8}${execpi 60 DKV=`date +%_d`; cal | sed '1d' | sed '1e' | sed '/./!d' | sed 's/^/   /' | sed 's/$/ /' | fold -w 24 | sed -n '/^.\{21\}/p' | sed /" $DKV "/s/" $DKV "/" "'${color2}'"$DKV"'${color1}'" "/}$font$color
${color0}${hr 1}$color
${font Rock Star 2.0,:size=30}${color1}o${font Disko:size=30}${color2}Now Playin'
${voffset -15}${font Print Bold:size=14}${color2} Artist:  ${color1}${exec conkyRhythmbox --datatype=AR}${font}
${font Print Bold:size=14}${color2} Title:  ${color1}${exec conkyRhythmbox --datatype=TI}${font}
${font Print Bold:size=14}${color2} Duration:  ${color1}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}${font}
```

---

### Post by kaivalagi on 2008-11-03
> **anxiousdog said:**
> Eh, leave the error. I'll just reboot and that will fix that part. :)

I'm not sure why I have the sh:su error either. This is my conkyrc and the error I'm getting. I've posted that I do have an error with your gcal as well.

```

${color1}${font Mono:size=8}${pre_exec cal -3 | cut -c23-64 | sed 's/^/   /' }
${voffset -78}${color1}${font Bitstream Vera Sans Mono:size=8}${execpi 60 DKV=`date +%_d`; cal | sed '1d' | sed '1e' | sed '/./!d' | sed 's/^/   /' | sed 's/$/ /' | fold -w 24 | sed -n '/^.\{21\}/p' | sed /" $DKV "/s/" $DKV "/" "'${color2}'"$DKV"'${color1}'" "/}$font$color
${color0}${hr 1}$color
```

The su error is from your calendar script I think, I recall it being mentioned on the conkyrc thread before now...I don't use it my self so I don't know the solution, but I think there is one

I've replied to your post on the gcal thread :)

---

### Post by anxiousdog on 2008-11-03
> **kaivalagi said:**
> The "Playback position not available" is a known issue, it happens when the script is half way through determining all the details for a song, and the song changes. I am not sure why the "SU: not found" error is occuring. I assume you are getting conky output for your songs?

If conky is started in a session instead, you wont get bombarded with these error messages...as there is no originating terminal window for the script.

I could remove the error messages altogether, but in doing so will also remove the messages that need to be displayed if there is a real problem.

At some point in the week I'll have a look and see what I can do...

Nevermind... I took away my code part by part and I see the sh: Su: issue is with my little calendar script, not with Rhythmbox or gcal.

But for what it's worth, the playback position error is not throwing. :)

Also, is there a way to draw a progress bar for playback rather than the numbers?

---

### Post by kaivalagi on 2008-11-03
> **anxiousdog said:**
> Nevermind... I took away my code part by part and I see the sh: Su: issue is with my little calendar script, not with Rhythmbox or gcal.

But for what it's worth, the playback position error is not throwing. :)

Also, is there a way to draw a progress bar for playback rather than the numbers?

yep, I use the percent position output with the execibar, like so:
```

${execibar 1 conkyRhythmbox --datatype=PP}
```

execbar doesn't behave properly, so execibar 1 is used instead...

---

### Post by anxiousdog on 2008-11-03
> **kaivalagi said:**
> yep, I use the percent position output with the execibar, like so:
```

${execibar 1 conkyRhythmbox --datatype=PP}
```

execbar doesn't behave properly, so execibar 1 is used instead...

Thanks, I like that bar. :)

---

### Post by champs on 2008-11-05
Would it be possible to pipe the album art somehow?

---

### Post by ad_267 on 2008-11-05
How does this perform when listening to radio? I'm using rhythmbox-client at the moment and when listening to the radio I get a blank artist and the title is the station name, even when Rhythmbox knows the actual song artist and title and artist and is showing them in the title bar.

---

### Post by kaivalagi on 2008-11-06
> **ad_267 said:**
> How does this perform when listening to radio? I'm using rhythmbox-client at the moment and when listening to the radio I get a blank artist and the title is the station name, even when Rhythmbox knows the actual song artist and title and artist and is showing them in the title bar.

Never tried using radio with this script

If rhythmbox provides all radio based info in the title then that's where it will come from...

Does my script not display this info?

---

### Post by ad_267 on 2008-11-06
I tried using this when listening to the radio and I get this output for anything:
```
ERROR: Issue calling the dbus service:float division
Unknown
```

That's with errors disabled. With errors enabled:
```
ERROR: Issue calling the dbus service:float division
ERROR: Issue calling the dbus service:float division
```

rhythmbox-client gives a blank artist and the radio station as the title.

---

### Post by kaivalagi on 2008-11-07
> **ad_267 said:**
> I tried using this when listening to the radio and I get this output for anything:
```
ERROR: Issue calling the dbus service:float division
Unknown
```

That's with errors disabled. With errors enabled:
```
ERROR: Issue calling the dbus service:float division
ERROR: Issue calling the dbus service:float division
```

rhythmbox-client gives a blank artist and the radio station as the title.

I'll take a look, first I have to find a radio to add...any good ones you can recommend?

---

### Post by ad_267 on 2008-11-07
> **kaivalagi said:**
> I'll take a look, first I have to find a radio to add...any good ones you can recommend?

This is one I listen to a lot: [http://www.95bfm.com/bfm128.m3u](http://www.95bfm.com/bfm128.m3u)
I don't know what kind of music you're into though, that's my university radio station and they play heaps of different stuff. That one doesn't always have the artist and title though. This station seems to always show these in rhythmbox: [http://streams.swcast.net/launch.cgi/radioxy/hi-band.pls](http://streams.swcast.net/launch.cgi/radioxy/hi-band.pls)

I'm not that worried about this if it would be a lot of work. What you've done so far is really great.

Cheers,
Adam

---

### Post by kaivalagi on 2008-11-07
> **ad_267 said:**
> This is one I listen to a lot: [http://www.95bfm.com/bfm128.m3u](http://www.95bfm.com/bfm128.m3u)
I don't know what kind of music you're into though, that's my university radio station and they play heaps of different stuff. That one doesn't always have the artist and title though. This station seems to always show these in rhythmbox: [http://streams.swcast.net/launch.cgi/radioxy/hi-band.pls](http://streams.swcast.net/launch.cgi/radioxy/hi-band.pls)

I'm not that worried about this if it would be a lot of work. What you've done so far is really great.

Cheers,
Adam

Still at work at 10:45PM...I need a remote login sorted to my home machine so I can play with my scripts :)

I'll take a look over the next few days, no worries

---

### Post by kaivalagi on 2008-11-09
[COLOR="Indigo"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've added rudimentary support for displaying stream info when using online radio

Changes as follows:

[LIST]
[*]Added genre to the datatypes, used with --datatype=GE
[*]Added stream support, to display what is available and not crash
[*]Updated README
[/LIST]

The first post has been updated and the apt package is available

Chimo

---

### Post by ad_267 on 2008-11-09
> **kaivalagi said:**
> 
I've added rudimentary support for displaying stream info when using online radio

That's awesome thanks! Works great.

---

### Post by kaivalagi on 2008-11-09
> **ad_267 said:**
> That's awesome thanks! Works great.

Glad it works

Out of interest, in your experience, is the title text always in the same format for all radio stations? Or is it down to what they define it as?

---

### Post by ad_267 on 2008-11-09
I don't listen to a lot of different radio stations, but the ones I use all seem to show the title in the format "Artist - Title". I don't know if this is a Rhythmbox thing or something set by the radio station.

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

### Post by pijiu on 2008-11-14
This is cool but it doesn't display my korean or chinese songs :s

---

### Post by kaivalagi on 2008-11-15
> **pijiu said:**
> This is cool but it doesn't display my korean or chinese songs :s

mmm, it should support unicode and not be a problem, I don't have any korean/chinese songs to try it out on so can't create the problem.

Can you try the attached script, I have amended it in a couple of places to hopefully handled what you need.

just run it like before, except using the python command, e.g.

```
${exec python /path/to/file/conkyRhythmbox.py ..options...}
```

If that doesn't help, can you provide with with a link to an offending mp3/ogg to try out?

---

### Post by Cammy on 2008-11-15
After being defeated by the mail script, I was not to be denied! :lolflag:

The music script works great.  Hopefully execibar will get a size attribute sometime soon, so it can be the same size as my other bars.

---

### Post by Cammy on 2008-11-15
Ok, I sort of spoke too soon.

I seem to have artifacts from the previous song played that appear below the current song.  It looks something like this:

[=======progress bar======]
Time stuff
Title
Artist
Rating


Portion of previous title
Previous rating


Other than making my conky area smaller, how do I get rid of that?

I'm also getting "Unknown" for some entries even though 1) I have no "Unknowns" in my music collection, and I've used the -u switch to suppress the Unknowns.

---

### Post by kaivalagi on 2008-11-15
> **Cammy said:**
> After being defeated by the mail script, I was not to be denied! :lolflag:

The music script works great.  Hopefully execibar will get a size attribute sometime soon, so it can be the same size as my other bars.

Glad to hear it

Deluge and Pidgin next?

---

### Post by Cammy on 2008-11-15
lol! I'm not even sure what Deluge is.

I think I have my previous problem solved.  I had the --nounknown option in the conkyrc instead of the template.  When I moved all the options to the template file, the display cleared up.  So far.

Fingers crossed that that was it.

---

### Post by cl0ckwork on 2008-11-15
> **Cammy said:**
> lol! I'm not even sure what Deluge is.

I think I have my previous problem solved.  I had the --nounknown option in the conkyrc instead of the template.  When I moved all the options to the template file, the display cleared up.  So far.

Fingers crossed that that was it.

what version of conky are you running?
if it is just from the hardy repos, you may need to compile the next version from sourceforge.
i had problems with version 1.5.1 from the repos because it didnt agree with any {execi} option

---

### Post by Cammy on 2008-11-15
1.5.1

So far it's been running for close to an hour and everything looks correct.

EDIT: I went ahead and bumped it up to 1.6.1 anyway.

---

### Post by pijiu on 2008-11-16
> **kaivalagi said:**
> mmm, it should support unicode and not be a problem, I don't have any korean/chinese songs to try it out on so can't create the problem.

Can you try the attached script, I have amended it in a couple of places to hopefully handled what you need.

just run it like before, except using the python command, e.g.

```
${exec python /path/to/file/conkyRhythmbox.py ..options...}
```

If that doesn't help, can you provide with with a link to an offending mp3/ogg to try out?

[http://www.megaupload.com/?d=YS4FMETX](http://www.megaupload.com/?d=YS4FMETX)

Can you try this if you wouldn't mind?

---

### Post by kaivalagi on 2008-11-17
> **pijiu said:**
> [http://www.megaupload.com/?d=YS4FMETX](http://www.megaupload.com/?d=YS4FMETX)

Can you try this if you wouldn't mind?

Doesn't want to download, I just get "waiting..."

Is there not a legal download on a good site I can use?

---

### Post by Cammy on 2008-11-17
kaivalagi, I just tried that song, and here's what it looks like on my conky.  Looks fine, except for the Korean characters in the title that my font doesn't have an equivalent for.

---

### Post by pijiu on 2008-11-17
I'm guessing it's something just simple like not using a supported font right? How would I find out a list of fonts that support Korean Chinese and Japanese?

---

### Post by kaivalagi on 2008-11-17
> **pijiu said:**
> I'm guessing it's something just simple like not using a supported font right? How would I find out a list of fonts that support Korean Chinese and Japanese?

Not sure about what is available already

If you want pure Korean fonts I found some here: [http://www.wazu.jp/gallery/Fonts_Korean.html](http://www.wazu.jp/gallery/Fonts_Korean.html)

Just pop the ttf's into ~/.fonts and run "fc-cache -v" to refresh the font cache

---

### Post by Cammy on 2008-11-17
Then there's always the option of removing the Korean portion of the title in the ID3 tag.

---

### Post by kaivalagi on 2008-11-17
> **Cammy said:**
> Then there's always the option of removing the Korean portion of the title in the ID3 tag.

That's got to be the favourite...assuming the id tag editor can handle the characters and doesn't crash :)

---

### Post by Cammy on 2008-11-17
Hey, kaivalagi.  Any chance of getting conky's ${scroll} feature added to the template?  I noticed that the newest conky has scrolling ability, and thought it would be cool for long song titles on my narrow conky, but it doesn't seem to work with execi and the rhythmbox script.

---

### Post by ad_267 on 2008-11-17
> **Cammy said:**
> Hey, kaivalagi.  Any chance of getting conky's ${scroll} feature added to the template?  I noticed that the newest conky has scrolling ability, and thought it would be cool for long song titles on my narrow conky, but it doesn't seem to work with execi and the rhythmbox script.

For long titles I just pass the output of the script into fold.

Eg: ```
execp conkyRhythmbox --template=/home/adam/.conkyRhythmbox.template --nounknownoutput | fold -w33 -s
```

---

### Post by Cammy on 2008-11-17
> **ad_267 said:**
> For long titles I just pass the output of the script into fold.

Eg: ```
execp conkyRhythmbox --template=/home/adam/.conkyRhythmbox.template --nounknownoutput | fold -w33 -s
```

Nice!!!!

---

### Post by kaivalagi on 2008-11-17
That's a good thing to know, thanks ad_267!

Cammy, have you tried using the scroll option in the template, if supported by execp/execpi it might well work...not sure as it's inside an exec call but worth trying

---

### Post by Cammy on 2008-11-17
> **kaivalagi said:**
> Cammy, have you tried using the scroll option in the template, if supported by execp/execpi it might well work...not sure as it's inside an exec call but worth trying

I did, but I might have boogered up the syntax (I'm good at doing that).  I'll play around with it some more.

---

### Post by pijiu on 2008-11-17
Hey guys I managed to get Korean and Chinese to display as you can see:

[IMG]http://img249.imageshack.us/img249/5770/59137805ob7.png[/IMG]

I was wondering if you guys can help me with the alignment of my conky script. As you can see after the titles I have "//.time" etc, the first word is slightly to the right. Also if you look at the RB down at the bottom you can see a more extreme version of this. How can I fix this?

```
    background no
    use_xft yes
    xftfont WenQuanYi Zen Hei:size=10
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type override
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 300
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    stippled_borders 0
    border_margin 5
    border_width 1
    default_color white
    default_shade_color black
    default_outline_color black
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT

    ${voffset 20}
    ${font WenQuanYi Zen Hei:size=20}${color light gray}//.UBUNTU${color Black}LINUX
    ${voffset -90}
    ${color DimGray}
    ${font}
    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.system ${color black} ${hr 2}
    $font${color DimGray}$sysname $kernel $alignr $machine
    Intel Pentium D $alignr${freq_g}Ghz
    Uptime $alignr${uptime}
    File System $alignr${fs_type}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.processors ${color black}${hr 2}
    $font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
    CPU2  ${cpu cpu2}% ${cpubar cpu2}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.mem ${color black}${hr 2}
    $font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.hdd ${color black}${hr 2}
    $font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.processes ${color black}${hr 2}
    ${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
    $font${top_mem name 3}${alignr}${top mem 3} %
    $font${top_mem name 4}${alignr}${top mem 4} %
    $font${top_mem name 5}${alignr}${top mem 5} %

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.network ${color black}${hr 2}
    $font${color DimGray}${endif}${if_existing /sys/class/net/wlan0/operstate up}IP (wlan0):$alignr${addr wlan0}
    AP: ${wireless_essid wlan0} ${alignr}Bitrate: ${wireless_bitrate wlan0}

    Down: ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
    ${downspeedgraph wlan0 20,90} ${alignr}${upspeedgraph wlan0 20,90}
    Total: ${totaldown wlan0} ${alignr}Tota: ${totalup wlan0}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.time ${color black}${hr 2}

    ${voffset -15} ${color light gray} ${font :size=24}$alignr${time %H:%M}
    ${voffset -25} ${font WenQuanYi Zen Hei:bold:size=8}$alignr${time %A}
    ${font :bold:size=10}$alignr${time %d %b. %Y}
    $endif

    ${color light gray}${font WenQuanYi Zen Hei:size=14}${font WenQuanYi Zen Hei:Bold:size=10}//.Rhythmbox${font}${color black}${hr 2}

    ${color1}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template --nounknownoutput | fold -w33 -s}

```

---

### Post by Cammy on 2008-11-17
> **pijiu said:**
> I was wondering if you guys can help me with the alignment of my conky script. As you can see after the titles I have "//.time" etc, the first word is slightly to the right. Also if you look at the RB down at the bottom you can see a more extreme version of this. How can I fix this?

Get rid of $font as the first item in each of those lines and put it at the end of the previous line instead.  I also prefer ${font} instead of $font but it probably doesn't make any difference.

---

### Post by pijiu on 2008-11-17
> **Cammy said:**
> Get rid of $font as the first item in each of those lines and put it at the end of the previous line instead.  I also prefer ${font} instead of $font but it probably doesn't make any difference.

Hey thanks! Just one more thing, I still don't know how to get the Rhythmbox section to align like the rest.

---

### Post by Cammy on 2008-11-17
> **pijiu said:**
> Hey thanks! Just one more thing, I still don't know how to get the Rhythmbox section to align like the rest.

Can you post your template contents?

---

### Post by tsedrey on 2008-11-17
To add to bombardment of questions...

I am have it working fine, but I don't want to see UNKNOWN UNKNOWN etc. when it isn't open. So I tried $(if_running Rhythmbox) / $(endif) and now nothing will show up ever. I even tried your example of:

${if_running rhythmbox}${color3}${execibar 1 conkyRhythmbox --datatype=PP}
${execp conkyRhythmbox --template=/home/mark/Scripts/conky/conkyRhythmbox.template}${endif}

but nothing shows up when I do that. Is there a way to fix this? Is there something that my computer is missing? 

Great work on the script so far. 
Thanks.

---

### Post by cl0ckwork on 2008-11-17
> **tsedrey said:**
> To add to bombardment of questions...

I am have it working fine, but I don't want to see UNKNOWN UNKNOWN etc. when it isn't open. So I tried $(if_running Rhythmbox) / $(endif) and now nothing will show up ever. I even tried your example of:

${if_running rhythmbox}${color3}${execibar 1 conkyRhythmbox --datatype=PP}
${execp conkyRhythmbox --template=/home/mark/Scripts/conky/conkyRhythmbox.template}${endif}

but nothing shows up when I do that. Is there a way to fix this? Is there something that my computer is missing? 

Great work on the script so far. 
Thanks.

you can add this as an option to conkyRhythmbox
```
  -n, --nounknownoutput
                        Turn off unknown output such as "Unknown" for title
                        and "0:00" for length. Command line option overridden
                        if used in templates.

```

---

### Post by tsedrey on 2008-11-17
I'm sorry, I am kind new at this, where do I add -n....?

---

### Post by cl0ckwork on 2008-11-18
> **tsedrey said:**
> I'm sorry, I am kind new at this, where do I add -n....?

right in here
```
${if_running rhythmbox}${color3}${execibar 1 conkyRhythmbox --datatype=PP}
${execp conkyRhythmbox --template=/home/mark/Scripts/conky/conkyRhythmbox.template [highlight]-n[/highlight]}${endif}
```

---

### Post by pijiu on 2008-11-18
> **Cammy said:**
> Can you post your template contents?

```
    background no
    use_xft yes
    xftfont WenQuanYi Zen Hei:size=10
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type override
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 300
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    stippled_borders 0
    border_margin 5
    border_width 1
    default_color white
    default_shade_color black
    default_outline_color black
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT

    ${voffset 20}
    ${font WenQuanYi Zen Hei:size=20}${color light gray}//.UBUNTU${color Black}LINUX
    ${voffset -90}
    ${color DimGray}
    ${font}
    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.system ${color black} ${hr 2}${font}
    ${color DimGray}$sysname $kernel $alignr $machine
    Intel Pentium D $alignr${freq_g}Ghz
    Uptime $alignr${uptime}
    File System $alignr${fs_type}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.processors ${color black}${hr 2}${font}
    ${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
    CPU2  ${cpu cpu2}% ${cpubar cpu2}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.mem ${color black}${hr 2}${font}
    ${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.hdd ${color black}${hr 2}${font}
    ${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.processes ${color black}${hr 2}${font}
    ${color DimGray}${top_mem name 2}${alignr}${top mem 2} %${font}
    ${top_mem name 3}${alignr}${top mem 3} %${font}
    ${top_mem name 4}${alignr}${top mem 4} %${font}
    ${top_mem name 5}${alignr}${top mem 5} %

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.network ${color black}${hr 2}${font}
    ${color DimGray}${endif}${if_existing /sys/class/net/wlan0/operstate up}IP (wlan0):$alignr${addr wlan0}
    AP: ${wireless_essid wlan0} ${alignr}Bitrate: ${wireless_bitrate wlan0}

    Down: ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
    ${downspeedgraph wlan0 20,90} ${alignr}${upspeedgraph wlan0 20,90}
    Total: ${totaldown wlan0} ${alignr}Tota: ${totalup wlan0}

    ${font WenQuanYi Zen Hei:bold:size=10}${color light gray}//.time ${color black}${hr 2}${font}

    ${voffset -15} ${color light gray} ${font :size=24}$alignr${time %H:%M}
    ${voffset -25} ${font WenQuanYi Zen Hei:bold:size=8}$alignr${time %A}
    ${font :bold:size=10}$alignr${time %d %b. %Y}
    $endif

    ${color light gray}${font WenQuanYi Zen Hei:size=14}${font WenQuanYi Zen Hei:Bold:size=10}//.Rhythmbox${color black}${hr 2}

    ${color1}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template --nounknownoutput | fold -w33 -s}
```
```
${color Dimgray}Artist:${color lightgray}[--datatype=AR]
${color dimgray}Album:${color lightgray}[--datatype=AL]
${color dimgray}Title:${color lightgray}[--datatype=TI]
${color dimgray}Position:${color lightgray}[--datatype=PT]/[--datatype=LE]
```

Here it is ^__^

---

### Post by Cammy on 2008-11-18
> **pijiu said:**
> 
```
${color Dimgray}Artist:${color lightgray}[--datatype=AR]
${color dimgray}Album:${color lightgray}[--datatype=AL]
${color dimgray}Title:${color lightgray}[--datatype=TI]
${color dimgray}Position:${color lightgray}[--datatype=PT]/[--datatype=LE]
```

Here it is ^__^

Ok, I'm not home, so I can't test, and the only thing I can see is that you have "Dimgray" with the D in uppercase instead of lowercase.  Try changing that to dimgray maybe, and in your .conkyrc get rid of the ${color1} at the beginning of the last line.  You don't need that since you've specified your colors in the template.

btw, I didn't even know you could specify colors in the actual template.

---

### Post by cl0ckwork on 2008-11-18
> **Cammy said:**
> Ok, I'm not home, so I can't test, and the only thing I can see is that you have "Dimgray" with the D in uppercase instead of lowercase.  Try changing that to dimgray maybe, and in your .conkyrc get rid of the ${color1} at the beginning of the last line.  You don't need that since you've specified your colors in the template.

btw, I didn't even know you could specify colors in the actual template.

by using the {execi...} command you can use the formatting like that in a template

---

### Post by kaivalagi on 2008-11-18
> **cl0ckwork said:**
> by using the {execi...} command you can use the formatting like that in a template

I am sure you meant {execpi...} or {execp...} :)

---

### Post by cl0ckwork on 2008-11-18
> **kaivalagi said:**
> I am sure you meant {execpi...} or {execp...} :)

true, it was early and i shouldve been paying attention in class :lolflag:

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

### Post by TerminusEst on 2008-11-20
Any way to get rid of the "unrated" text?

EDIT: nvm, I figured it out, in conkyRhythmbox.py I replaced 
```
output = "Unrated"
```
with:
```
output = ""
```

---

### Post by kaivalagi on 2008-11-20
> **TerminusEst said:**
> Any way to get rid of the "unrated" text?

EDIT: nvm, I figured it out, in conkyRhythmbox.py I replaced 
```
output = "Unrated"
```
with:
```
output = ""
```

It makes sense to have nothing I guess, I'll make the change it for the next release

---

### Post by TerminusEst on 2008-11-20
> **kaivalagi said:**
> It makes sense to have nothing I guess, I'll make the change it for the next release

Good idea :)
Also if anyone is interested, this is how my rhythmbox section looks like :

[IMG]http://i51.photobucket.com/albums/f375/DefenderoftheGate/conkyrhythm.png[/IMG]

in .conkyrc:
```
${voffset 4}${font BulletBalls AOE:size=16}Z${font}  ${font Arial Bold:size=9}${voffset -5}${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=TI}${font}
${voffset 4}Artist: ${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=AR}  ${alignr}${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=PT}/${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=LE}
${voffset 2}${execibar 1 ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=PP}
${voffset 2}${font PizzaDude Bullets:size=10}BBBBB${font}${offset -60}${font PizzaDude Bullets:size=10}${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=RT --ratingchar=D}${font}
```

will require "BulletBalls" and "PizzaDude Bullets" fonts

---

### Post by kaivalagi on 2008-11-20
> **TerminusEst said:**
> Good idea :)
Also if anyone is interested, this is how my rhythmbox section looks like :

[IMG]http://i51.photobucket.com/albums/f375/DefenderoftheGate/conkyrhythm.png[/IMG]

in .conkyrc:
```
${voffset 4}${font BulletBalls AOE:size=16}Z${font}  ${font Arial Bold:size=9}${voffset -5}${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=TI}${font}
${voffset 4}Artist: ${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=AR}  ${alignr}${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=PT}/${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=LE}
${voffset 2}${execibar 1 ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=PP}
${voffset 2}${font PizzaDude Bullets:size=10}BBBBB${font}${offset -60}${font PizzaDude Bullets:size=10}${exec ~/.scripts/conkyrhythmbox-2.03/conkyRhythmbox --datatype=RT --ratingchar=D}${font}
```

will require "BulletBalls" and "PizzaDude Bullets" fonts

Very nice!

---

### Post by cedeel on 2008-11-22
There seems to be an error with your script when trying to print non-ascii characters.

The following is being output on the command line:

Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 466, in <module>
    main()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 463, in main
    rhythmboxinfo.writeOutput()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 416, in writeOutput
    print output.encode("utf-8")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 5: ordinal not in range(128 )


In conky, nothing is output :(

---

### Post by kaivalagi on 2008-11-22
> **cedeel said:**
> There seems to be an error with your script when trying to print non-ascii characters.

The following is being output on the command line:

Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 466, in <module>
    main()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 463, in main
    rhythmboxinfo.writeOutput()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 416, in writeOutput
    print output.encode("utf-8")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 5: ordinal not in range(128 )


In conky, nothing is output :(

I can't reproduce the problem, if you don't mind could you try editing the script you have as follows?

assuming you installed using apt/deb package, edit the file:

```
gksudo gedit /usr/share/conkyrhythmbox/conkyRhythmbox.py
```

find the section of code like this:

```
    def writeOutput(self):
		
        if self.options.template != None:
```

and change it to this:

```
    def writeOutput(self):

		output = u""
		
        if self.options.template != None:
```

If that works, great, if not I'll need to do some more digging.

Also, what is the title, artist and album that is being played?

Chimo

---

### Post by Cammy on 2008-11-25
kaivalagi, is there any chance of adding a lyrics option anytime in the future?  I just noticed that (probably because I enabled the lyrics plugin on rhythmbox) I have lyrics for all my music in ~/.lyrics/artist/songname.lyric

Someone over in the general conky thread made a lyrics script for Amarok, but Amarok takes forever to launch on my machine, and I also don't want to lose what I already have with your rhythmbox script.

---

### Post by kaivalagi on 2008-11-25
> **Cammy said:**
> kaivalagi, is there any chance of adding a lyrics option anytime in the future?  I just noticed that (probably because I enabled the lyrics plugin on rhythmbox) I have lyrics for all my music in ~/.lyrics/artist/songname.lyric

Someone over in the general conky thread made a lyrics script for Amarok, but Amarok takes forever to launch on my machine, and I also don't want to lose what I already have with your rhythmbox script.

In theory I can do this at some point, shouldn't be a problem.

However I am very busy with another project so any new functionality on my existing scripts is on hold at present...

I'll add it to my TODO's...

---

### Post by Cammy on 2008-11-25
> **kaivalagi said:**
> I'll add it to my TODO's...

As it turns out, the guy who wrote the Amarok one had a rhythmbox version, so you can put that on your back, back burner unless you have another compelling reason to add it.

---

### Post by I wanted to leave on 2008-12-01
kaivalagi

Thank you for the rhythmbox cover-art plugin :biggrin:

You are an absolute champion for this :KS

---

### Post by kaivalagi on 2008-12-02
> **bra10n said:**
> kaivalagi

Thank you for the rhythmbox cover-art plugin :biggrin:

You are an absolute champion for this :KS

You found that did you :) It was someone elses work, which I modified and created a package for....

Wait until you see my next project released...can't say any more yet even though I am dying to.... :)

---

### Post by HippyRandall on 2008-12-02
> **kaivalagi said:**
> can't say any more yet even though I am dying to.... :)
:lolflag:
me too

---

### Post by I wanted to leave on 2008-12-02
> **kaivalagi said:**
> You found that did you :) It was someone elses work, which I modified and created a package for....

Wait until you see my next project released...can't say any more yet even though I am dying to.... :)

Stand tall. I can wait... just long enough for you to talk though :lolflag:

---

### Post by IceReaver75 on 2008-12-03
I just installed this and I'm not not getting and info from artist,album or title it just says unknown even though its a cd and rythmbox gives all the info.  While running conky with a terminal opened i get this error message:

ERROR:dbus.proxies:Introspect error on :1.264:/org/gnome/Rhythmbox/Player: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.264 was not provided by any .service files

Not sure what this means at all? this is what is at the end of my conky file

${if_running rhythmbox}
${color white}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template}${color}
${endif}

Edit: Its working for everyhting else: internet radio, mp3s just not when playing a cd.  I'm not sure if this script is set-up to handle cd playback but when playing a cd everything but the progrss is listed as unknown.

---

### Post by kaivalagi on 2008-12-04
> **IceReaver75 said:**
> I just installed this and I'm not not getting and info from artist,album or title it just says unknown even though its a cd and rythmbox gives all the info.  While running conky with a terminal opened i get this error message:

ERROR:dbus.proxies:Introspect error on :1.264:/org/gnome/Rhythmbox/Player: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.264 was not provided by any .service files

Not sure what this means at all? this is what is at the end of my conky file

${if_running rhythmbox}
${color white}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template}${color}
${endif}

Edit: Its working for everyhting else: internet radio, mp3s just not when playing a cd.  I'm not sure if this script is set-up to handle cd playback but when playing a cd everything but the progrss is listed as unknown.

Never though to try a CD before :) All my CD's are ripped to MP3's and stored away...

I'll take a look at the reason why it doesn't work soon, I have something else on the go right now..

---

### Post by IceReaver75 on 2008-12-04
> **kaivalagi said:**
> Never though to try a CD before :) All my CD's are ripped to MP3's and stored away...

I'll take a look at the reason why it doesn't work soon, I have something else on the go right now..

Alright thanks for taking a look.  Take your time whenever you get a chance is fine.

---

### Post by kaivalagi on 2008-12-14
New app added to my PPA, new thread on this can be found through the apps link in my sig below...

---

### Post by sanjit on 2008-12-20
Thanks. I love that plugin. I wish they all had that plugin.

It features well in my setup.

---

### Post by Dethv on 2008-12-21
Thank you so much kaivalagi for these guides. I'm using both your email and rhythmbox scripts and they are working perfectly. :D

---

### Post by ryniek on 2008-12-30
Thanks for the script. It's great, but the Track Number don't want to work. It gaves me the Genre not the Track number. And sometimes when it changes to next song, conky is being killed automatically.
And it doesn't support European letters i.e. Polish letters.

---

### Post by kaivalagi on 2008-12-31
> **ryniek said:**
> Thanks for the script. It's great, but the Track Number don't want to work. It gaves me the Genre not the Track number. And sometimes when it changes to next song, conky is being killed automatically.
And it doesn't support European letters i.e. Polish letters.

I can confirm the track number output is screwed, now fixing...

Unicode support should be working, pijiu got it working for Korean characters here: [http://ubuntuforums.org/showpost.php?p=6200263&postcount=59](http://ubuntuforums.org/showpost.php?p=6200263&postcount=59)

I think you need to have this setting in the conkyrc file above TEXT...
```
override_utf8_locale yes
```

Any chance of running the script with an errorlogfile option set so we can see the error when conky crashes?

---

### Post by kaivalagi on 2008-12-31
[COLOR="Green"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

New script available with the following changes:

[LIST]
[*]Unrated rating now outputs nothing
[*]Fixed statustext to work inside template now
[*]Fixed track number output
[/LIST]

The first post has been updated and the apt package will be available shortly

Cheers

---

### Post by The_Orig on 2009-01-08
The script works great with Rhythmbox playing normal playlists, but for some reason it can't ascertain the title, artist, or album of last.fm songs. The output is "unknown" for my .conkyrc file and your example one. 

I've attached verbose output from conkyRhythmbox.

---

### Post by kaivalagi on 2009-01-09
I'll take a look at some point, I also have to get CD support sorted too

---

### Post by ryniek on 2009-01-10
> **kaivalagi said:**
> 
I think you need to have this setting in the conkyrc file above TEXT...
```
override_utf8_locale yes
```


i have this setting. But if i'm listening to song which has polish letters, i.e. **&#322;,&#261;,&#281;,&#347;**, Rhythmbox Script can't show these letters on Conky. I've installed the latest version (2.0.4) of your script and it's the same situation. 

> **kaivalagi said:**
> 
Any chance of running the script with an errorlogfile option set so we can see the error when conky crashes?

Actually the conky is working fine. The progressbar from you script was the fault of the conky crash. When the song has been automatically changed, sometimes progressbar had crashed with the conky and sometimes it worked fine. I think the bug works randomly. Now i'm using only percent notificator of passed song time, without progressbar, and it works fine for now.

Cheers.

---

### Post by kaivalagi on 2009-01-10
@ryniek

When you run the script in the terminal do you get the correct characters output?

I am seeing issues with unicode support in conky quite a bit lately, I have a sneaky feeling conky is causing the issue

Can you try using conky with execi instead of execpi etc, as I suspect the execp/execpi behaves differently with unicode support (not certain though)

---

### Post by ryniek on 2009-01-10
If i type ```
exec conkyRhythmbox --datatype=TI
``` in Terminal, it disappears, nothing else. 

when i changed **exec** to **execpi**, the output in Conky was something like that:
```
Artist: ${execpi}
```

But when i have **exec**, the output is fine. 

When i changed to **exec**, and turn on conky, i had a Traceback in Terminal:

```
Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 474, in <module>
    main()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 471, in main
    rhythmboxinfo.writeOutput()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 424, in writeOutput
    print output.encode("utf-8")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc5 in position 6: ordinal not in range(128)
```

but everything, except polish letters in output, works fine. 
Cheers.

---

### Post by kaivalagi on 2009-01-10
loose the exec in the terminal, i.e.

```
conkyRhythmbox --datatype=TI
```

What then?

I assume it still has a problem...

I'll take a look at some point in the next couple of days...busy weekend right now :)

---

### Post by ryniek on 2009-01-10
**Artist**:
```
ryniek@RyniekOnDesktop:~$ conkyRhythmbox --datatype=TI
Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 474, in <module>
    main()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 471, in main
    rhythmboxinfo.writeOutput()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 424, in writeOutput
    print output.encode("utf-8")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc5 in position 9: ordinal not in range(128)
ryniek@RyniekOnDesktop:~$ 

```

**Album**:
```
ryniek@RyniekOnDesktop:~$ conkyRhythmbox --datatype=AL
Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 474, in <module>
    main()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 471, in main
    rhythmboxinfo.writeOutput()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 424, in writeOutput
    print output.encode("utf-8")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc5 in position 6: ordinal not in range(128)
ryniek@RyniekOnDesktop:~$ 

```

Album and Artist of randomly choosen by me song has polish letters.

---

### Post by kaivalagi on 2009-01-10
Can you install the attached deb file, this is the next version (2.05) with what I hope is the fix...

Let me know how you get on, if all is okay I'll rollout the update via apt

---

### Post by ryniek on 2009-01-10
Thanks man. I've installed ver. 2.0.5 and by now i don't have any problems. Unicode works fine, polish letters in output works fine. Thanks   :)

---

### Post by kaivalagi on 2009-01-10
**[COLOR="Red"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Fixed the script to handle unicode output better (I hope)

The first post has been updated and the apt package should be available soon

---

### Post by ryniek on 2009-01-10
When i'm listening to songs which has been performed by many artist, the output is to long and it extends too much on desktop. I modified the script like that:
```

elif datatype == "AR": #artist
    if self.musicData.artist == None or len(self.musicData.artist) == 0:
        output = None
    else:
        output = self.musicData.artist[0:30] + "..."
```

Could you add the option which could cut off output bigger than maybe 35 letters?
It could help other who don't know Python.

---

### Post by yello_ubu on 2009-01-14
Using the last.fm plugin, I get "Unknown" for both artist & title. Works fine playing mp3s etc.

Edit: typing 'rhythmbox-client --print-playing' in terminal returns both the artist and title so the data should be available to conkyRhythmbox... hopefully!!

---

### Post by kaivalagi on 2009-01-14
@ryniek - I'll add a maxlength option to the script at some point, I've added it to my todo list for now...it will need to work on the command line and in templates, so it can be used for only certain datatypes if need be.

@yello_ubu - I have both CD and last.fm support in my todo list

Not sure when I'll start on the mods...I have quite a bit on right now

Cheers
[COLOR="Navy"]
Edit: Update coming now :) I couldn't help myself[/COLOR]

---

### Post by yello_ubu on 2009-01-14
Cheers kaivalagi. No hurry, as and when. I'll stay tuned!:D

---

### Post by kaivalagi on 2009-01-14
[COLOR="DarkRed"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I've updated the script as follows:

[LIST]
[*]Updated to handle CD and last.fm music sources better
[*]Added --maxlength option for command line and templates, to limit string output if need be
[*]Updated README
[/LIST]

Maxlength usage help:
```

  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
```


The first post has been updated with the new attachments and the apt based packages are available

---

### Post by yello_ubu on 2009-01-15
Whoosh! That was fast!! Works perfectly on last.fm too! Cheers kaivalagi :D

---

### Post by The_Orig on 2009-01-16
Awesome, last.fm works now. Thanks for the quick update :)!

---

### Post by kaivalagi on 2009-01-16
> **The_Orig said:**
> Awesome, last.fm works now. Thanks for the quick update :)!

Great quote! Suits today's times...

---

### Post by The_Orig on 2009-01-17
Thanks :)!

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

### Post by kwagster on 2009-02-03
Does anybody else get a huge jump in CPU usage (like ~50% boost) by running this? If I do "killall conky" the CPU usage drops like crazy and I tried running conky with my old conkyrc and the boost didn't appear again.

---

### Post by Cammy on 2009-02-04
> **kwagster said:**
> Does anybody else get a huge jump in CPU usage (like ~50% boost) by running this? If I do "killall conky" the CPU usage drops like crazy and I tried running conky with my old conkyrc and the boost didn't appear again.

Are you using any fancy fonts?  I had the same problem when I used that stylebats font.

---

### Post by kaivalagi on 2009-02-04
> **kwagster said:**
> Does anybody else get a huge jump in CPU usage (like ~50% boost) by running this? If I do "killall conky" the CPU usage drops like crazy and I tried running conky with my old conkyrc and the boost didn't appear again.

Can you narrow down where the CPU usage is? conky or conkyRhythmbox.py?

---

### Post by paulus4605 on 2009-02-05
when using the rhythmbox.py I got also a huge increase of cpu usage 
just using the basic setup as it came through the repos
when killing it,the cpu was happy again.

---

### Post by kaivalagi on 2009-02-05
> **kwagster said:**
> Does anybody else get a huge jump in CPU usage (like ~50% boost) by running this? If I do "killall conky" the CPU usage drops like crazy and I tried running conky with my old conkyrc and the boost didn't appear again.

> **paulus4605 said:**
> when using the rhythmbox.py I got also a huge increase of cpu usage 
just using the basic setup as it came through the repos
when killing it,the cpu was happy again.

I haven't noticed any intense CPU activity, but I do run quad core...I don't think there is anything that can be done other than increasing the refresh interval in the execi call.

You have a couple of other options...

1) You could try the rhythmbox-desktop-art package in my repo instead. It is a plugin for Rhythmbox which supports track info and album art on the desktop.

2) Use my own new python app gtk-desktop-info...link in my sig ;) The rhythmbox plugin displays everything I want...see attached. It works well with gnome at the moment - if the wallpaper becomes an issue due to compiz wallpaper settings or kde/xfce use, use the --wallpaper option.

---

### Post by HarshReality on 2009-03-02
> **kaivalagi said:**
> I haven't noticed any intense CPU activity, but I do run quad core...I don't think there is anything that can be done other than increasing the refresh interval in the execi call.

You have a couple of other options...

1) You could try the rhythmbox-desktop-art package in my repo instead. It is a plugin for Rhythmbox which supports track info and album art on the desktop.

2) Use my own new python app gtk-desktop-info...link in my sig ;) The rhythmbox plugin displays everything I want...see attached. It works well with gnome at the moment - if the wallpaper becomes an issue due to compiz wallpaper settings or kde/xfce use, use the --wallpaper option.



So what are we using to display the album art?

---

### Post by kaivalagi on 2009-03-03
> **HarshReality said:**
> So what are we using to display the album art?

Options 1 or 2 above both support album art...

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

### Post by Laserion on 2009-04-24
Is there a way to set or specify the length/width of the execibar?

my main .conkyrc is set to 1024 768 and with a maximum width of 1010. I just want to set a width if it's possible? TIA!

${execibar 1 conkyRhythmbox --datatype=PP} or i'm just missing something? it's located on the lower left of my desktop screen, and I want to set the width so it won't go to the other end right of the screen....

---

### Post by kaivalagi on 2009-04-24
> **Laserion said:**
> Is there a way to set or specify the length/width of the execibar?

my main .conkyrc is set to 1024 768 and with a maximum width of 1010. I just want to set a width if it's possible? TIA!

${execibar 1 conkyRhythmbox --datatype=PP} or i'm just missing something? it's located on the lower left of my desktop screen, and I want to set the width so it won't go to the other end right of the screen....

What you want is possible and it's all down to the "maximum_width" settings of your conkyrc. It has nothing to do with the conkyRhythmbox script.

SHould be straight forward...if you need help I would suggest posting on this thread: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

I just don't use Conky anymore, I have my own app, see my sig below ;)

---

### Post by Laserion on 2009-04-25
yup, my maximum_width is set to 1010. And also combined the conkyRhythmbox on my .conkyrc configuration....

Really appreciate your time and help, bro! Thanks for the link and big thanks for the prompt response!

wow, you have your own app, kewl!

---

### Post by anandamide on 2009-04-26
Thanks SO MUCH for this, I love conky and have been searching all over for a Rhythmbox app.

So far works fine under Jaunty :-).

---

### Post by kaivalagi on 2009-04-27
> **anandamide said:**
> Thanks SO MUCH for this, I love conky and have been searching all over for a Rhythmbox app.

So far works fine under Jaunty :-).

You have a couple of other options I have created too that aren't conky based...

A) Use my new app, see the link in my sig

B) You could try the "rhythmbox-desktop-art" package which is available in my ppa's. It is a plugin for rhythmbox which displays song info/cover art when the song changes, it can also control rhythmbox in simple ways...based on other package installs the below steps are needed for the rb plugin to become available:

1) Create the necessary list file for access to the rhythmbox repository by running one of these.

Jaunty Jackalope:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/m-buck-rhythmbox-jaunty.list -O /etc/apt/sources.list.d/m-buck-rhythmbox-jaunty.list
```

Intrepid Ibex:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/m-buck-rhythmbox-intrepid.list -O /etc/apt/sources.list.d/m-buck-rhythmbox-intrepid.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/ubuntu/ppa/m-buck-rhythmbox-key.gpg -O- | sudo apt-key add -
```

3) Now that is done simply run the following to install

```
sudo apt-get update && sudo apt-get install rhythmbox-desktop-art

```

4) Restart rhythmbox and you should find the plugin listed as "Desktop-Art"

---

### Post by wpf999 on 2009-05-05
Just got to tell you - your Rhythmbox desktop art plugin is FANTASTIC! Brilliant job. So much easier and more flexible than the Conky rhythmbox script. Looks really sexy too :-) Thanks sooo much.

---

### Post by Cammy on 2009-05-05
I think I'm going to need to reinstall this script.  It's stopped working since my upgrade to Jaunty.

---

### Post by kaivalagi on 2009-05-06
> **Cammy said:**
> I think I'm going to need to reinstall this script.  It's stopped working since my upgrade to Jaunty.

Have you followed the new instructions to install from the new ppa location? The old PPA is not being updated anymore, there is now a conky specific ppa where all the updates will go.

See the first post for details on the PPA setup :)

---

### Post by Cammy on 2009-05-06
> **kaivalagi said:**
> Have you followed the new instructions to install from the new ppa location? The old PPA is not being updated anymore, there is now a conky specific ppa where all the updates will go.

See the first post for details on the PPA setup :)

I've not had a chance yet, as I'm still working on getting my system conky where I want it.  I also still need to copy my .lyrics folder over from my old hard drive.  I'm sure getting my rhythmbox script running again won't be too tough. :)

---

### Post by kaivalagi on 2009-05-06
> **Cammy said:**
> I've not had a chance yet, as I'm still working on getting my system conky where I want it.  I also still need to copy my .lyrics folder over from my old hard drive.  I'm sure getting my rhythmbox script running again won't be too tough. :)

We'll any problems, big or small, just let us know

Once you need to make sure the rb script is up-to-date all you need to do is the following in the terminal (assuming it's already installed, otherwise apt-get install instead at the end):

```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/m-buck-conky-jaunty.list -O /etc/apt/sources.list.d/m-buck-conky-jaunty.list
wget -q http://www.kaivalagi.com/ubuntu/ppa/m-buck-conky-key.gpg -O- | sudo apt-key add -
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Cammy on 2009-05-06
Good news!  My conkyRhythmbox is running!

Now I just need to figure out what happened to the lyrics script.  It shows nothing.

---

### Post by Cammy on 2009-05-06
Fixed!  I was playing a 'live' song so the lyrics plug-in couldn't find the lyrics for it.  When I played an album version, I got my lyrics back. :)

---

### Post by merlin_ie on 2009-05-21
must say i'm simply loving the rhythmbox / conky script but i just wanted to know, is there a script to scroll or display lyrics to make it REALLY cool? :D

---

### Post by kaivalagi on 2009-05-21
> **merlin_ie said:**
> must say i'm simply loving the rhythmbox / conky script but i just wanted to know, is there a script to scroll or display lyrics to make it REALLY cool? :D

Look for a script posted in the .conkyrc thread here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

The script is written by eightmillion I think. If you can't find it (there are a lot of posts) just ask for it there and I am sure someone will post what they have :)

---

### Post by shane25119 on 2009-05-30
This will likely be a very elementary question, but I installed the script as per the first post in this thread.  Now, when I try to start conkyRhythmbox I simply get the name of the present song in the terminal- nothing appears on my desktop.  Googleing has been futile- any help is much appreciated!!

---

### Post by merlin_ie on 2009-05-30
> **shane25119 said:**
> This will likely be a very elementary question, but I installed the script as per the first post in this thread.  Now, when I try to start conkyRhythmbox I simply get the name of the present song in the terminal- nothing appears on my desktop.  Googleing has been futile- any help is much appreciated!!

Hi Shane. In the /usr/share/conkyrhythmbox/example you will find the conkyrc script. Open and you will see near bottom the following : 

```
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}Rhythmbox${font}

${color4}Template Output:
${color1}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template}
```

I add that to the conky file in /etc/conky and it works fine

Or you can use the "Standard Output" part under it, whatever flips your switch :D

Hope this helps

---

### Post by shane25119 on 2009-05-30
Hi Merlin- thanks for the quick reply-

I tried what you suggested, I got the same difference.  Fortunately, I just figured out how to turn on desktop display via the Rhythmbox plugins... still I'd like to be able to use conky- because, quite frankly, it does a lot more than the RB plugin.

---

### Post by merlin_ie on 2009-05-30
well, i just typed ran conky in terminal and it showed fine with details...then i ran conkyRhythmbox same way and that worked too..mind you, i forgot to mention that i have the conkyRhythmbox.template part in etc/conky and edited it to point to that folder, so maybe that would help?

Edit : I just took a look at it now and terminal was going crazy, saying i had to change the permissions in the conkyRhythmbox.py script so i did that and pasted this in AGAIN and it worked perfectly

```
${color4}Template Output:
${color1}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template}

```

again, hope this helps

---

### Post by shane25119 on 2009-05-30
Merlin- by running conky before conkyRhythmbox I now have it going.... how though would I go about moving conky from a window to a more widget like setup on the desktop?

Furthermore--- how do I get rid of the other stuff running in conky (ie: RAM usage, free space on my hdd etc)?

Thanks so much!

Shane

---

### Post by merlin_ie on 2009-05-31
> **shane25119 said:**
> Merlin- by running conky before conkyRhythmbox I now have it going.... how though would I go about moving conky from a window to a more widget like setup on the desktop?

Furthermore--- how do I get rid of the other stuff running in conky (ie: RAM usage, free space on my hdd etc)?

Thanks so much!

Shane

Sorry for taking so long to reply Shane. I've attatched a slim version of my conky. It should be simple to figure out. It only shows Rhythmbox output, the file system status (just swap, root and external drives are displayed) and Battery Level. When you open mine, you will see my external drives marked ELEMENTS and MOVIES. Just change those names to whatever yours are named. And anything you don't like, you can just delete it. That's the good thing :D

Have fun

---

### Post by shane25119 on 2009-05-31
Wonderful!  That did the trick!!!  Thank you so much!

---

### Post by merlin_ie on 2009-05-31
> **shane25119 said:**
> Wonderful!  That did the trick!!!  Thank you so much!

No problem, I'm still learning myself lol. For more things, you can look here : [HTML]http://conky.sourceforge.net/variables.html[/HTML] Interesting ones there

---

### Post by [S]Duke on 2009-07-13
I was wondering, does this scrypt (or do you guys have one), include the ability to show progress through a bar?

---

### Post by kaivalagi on 2009-07-14
> **'[S]Duke said:**
> I was wondering, does this scrypt (or do you guys have one), include the ability to show progress through a bar?

There are a few ways to get progress displayed through a bar, the simplest is as follows using execibar and the percentage progress from the script:

```
${execibar 1 conkyRhythmbox --datatype=PP}
```

Hope that helps

---

### Post by csabo2 on 2009-07-23
Awesome work mate, thanks :)

---

### Post by kaivalagi on 2009-07-23
> **csabo2 said:**
> Awesome work mate, thanks :)

Thanks for the thanks :)

---

### Post by aslamp on 2009-07-25
has anybody considered using the Imlib2 config option when compiling conky?
from there you can use the $image tag to stick in images.

so does anybody know how find the current album art?

more info on Imlib2 -> [http://conky.wikia.com/wiki/Conky_and_Images_%28Imlib2%29](http://conky.wikia.com/wiki/Conky_and_Images_%28Imlib2%29)

---

### Post by kaivalagi on 2009-07-25
> **aslamp said:**
> has anybody considered using the Imlib2 config option when compiling conky?
from there you can use the $image tag to stick in images.

so does anybody know how find the current album art?

more info on Imlib2 -> [http://conky.wikia.com/wiki/Conky_and_Images_%28Imlib2%29](http://conky.wikia.com/wiki/Conky_and_Images_%28Imlib2%29)

Are you saying you would like a "cover art filepath" datatype 'cause I already have a working bit of code used in gtk-desktop-info... :)

I've added a --datatype=CA option, this will provide you with the current songs cover art filepath to wrap the $image function around. If none is found an empty string is returned. I have dealt with spaces and brackets in the filepath (they need "\" prefixes)

Running this:
```
conkyRhythmbox --datatype=CA
```I get:
```
/home/mark/Music/Indie/Elbow/Asleep\ In\ The\ Back\ \(2001\)/folder.jpg
```
Anyway, give the attached deb install a try, if all works I'll rollout a new package for everyone and probably update the exaile script too

I have no idea on the use of the $image function in conky so I can't help there, but this option will give you an image path to use...

Let me know how you get on!

---

### Post by aslamp on 2009-07-25
i got it working =D. here's a snap of my current setup, with the config:

[IMG]http://i27.tinypic.com/24no7s4.jpg[/IMG]

```
${offset 69}${font AvantGardeLTMedium:size=10}${exec rhythmbox-client --print-playing-format %tt}
${offset 69}$color1${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/jack/.album}${image /home/jack/.album -p 0,2 -s 64x64}
```

the last line is the important stuff. it basically copies whatever the album image is to ~/.album, then conky displays that. make sure to put a ```
imlib_cache_size 0
``` in your conky file so it doesn't cache it.

and again, you have to compile conky with "--enable-imlib2" in order to use the $image tag.

enjoy!

---

### Post by kaivalagi on 2009-07-26
> **aslamp said:**
> i got it working =D

Nicely done, I've posted a link to your post above on the main conkyrc thread, lettings others know about it there...

I've released the new packages for Rhythmbox and Exaile already :)

---

### Post by kaivalagi on 2009-07-26
**[COLOR=DarkRed][SIZE=4]UPDATE[/SIZE][/COLOR]**

I have added cover art support to the script, now cover art image filepaths can be found by using the --datatype=CA option. This option will be useful to anyone using the $image function now available with conky v1.7.1+
 
Package changes can be seen here:  [URL="https://launchpad.net/%7Em-buck/+archive/conky/+files/conkyrhythmbox_2.07_source.changes"]https://launchpad.net/~m-buck/+archive/conky/+files/conkyrhythmbox_2.07_source.changes
[/URL] 
The apt packages should be available shortly, the first post has the new packages attached also

Chimo

[COLOR=DarkSlateGray]Edit: I forgot to update the README and the help output to detail the CA datatype availability...this will be updated in the next release whenever that is...[/COLOR]

---

### Post by ryniek on 2009-07-26
Hi.
The Conky script is great, but i heard that in Ubuntu 9.10 and later, default song player will be Banshee. So could You add the Banshee support for Conky script? Of course it's not a problem to install Rhythmbox. The script already supports Exaile, but one more player on support list, probably would make it more popular  :)

---

### Post by kaivalagi on 2009-07-26
> **ryniek said:**
> Hi.
The Conky script is great, but i heard that in Ubuntu 9.10 and later, default song player will be Banshee. So could You add the Banshee support for Conky script? Of course it's not a problem to install Rhythmbox. The script already supports Exaile, but one more player on support list, probably would make it more popular  :)

I have already added banshee support to my gtk-desktop-info app and I was planning to creating a conkyBanshee script soon, should be available shortly

Keep a look in for a "conkybanshee" package in my ppa, it will definitely be available before any dedicated thread is created ;)

[COLOR=Navy]edit: New package, new thread...conkyBanshee details here: [http://ubuntuforums.org/showthread.php?t=1223883](http://ubuntuforums.org/showthread.php?t=1223883)[/COLOR]

---

### Post by terrorcore on 2009-07-31
Hello all.

Noob question here...I am using Ubunto 8.10 Intrepid Ibex. I followed the install instructions, but there is no usr/share/conkyRythmbox folder.  Where did I go wrong? I have conky installed and running nicely..I just wanted to add this feature to it.

---

### Post by kaivalagi on 2009-07-31
> **terrorcore said:**
> Hello all.

Noob question here...I am using Ubunto 8.10 Intrepid Ibex. I followed the install instructions, but there is no usr/share/conkyRythmbox folder.  Where did I go wrong? I have conky installed and running nicely..I just wanted to add this feature to it.

so running the following in a terminal errors? Notice the lower case and first slash

```
ls /usr/share/conkyrhythmbox
```

If when you run this:

```
conkyRhythmbox --version
```

You get something like this:

```
conkyRhythmbox v.2.0?
```

Everything is in place...

Cheers

---

### Post by terrorcore on 2009-07-31
When I run that, I get this:

ls: cannot access /usr/share/conkyrhythmbox: No such file or directory

---

### Post by kaivalagi on 2009-07-31
> **terrorcore said:**
> When I run that, I get this:

ls: cannot access /usr/share/conkyrhythmbox: No such file or directory

Can you run this:

```
sudo apt-get update && sudo apt-get install conkyrhythmbox
```

---

### Post by terrorcore on 2009-07-31
I ran that command, it looked like it worked, but I'm still getting the same error as before.

---

### Post by kaivalagi on 2009-07-31
> **terrorcore said:**
> I ran that command, it looked like it worked, but I'm still getting the same error as before.

Not sure what is wrong without knowing more, you are running Ubuntu yes?

Try uninstalling then reinstalling...

```
sudo apt-get update && sudo apt-get remove conkyrhythmbox & sudo apt-get install conkyrhythmbox
```

Can you also tell me what the results of this are:

```
cat /usr/bin/conkyRhythmbox
```

It is hopefully there....

---

### Post by terrorcore on 2009-07-31
Before uninstalling and reinstalling:

cat /usr/bin/conkyRhythmbox

After

#! /bin/sh
cd /usr/share/conkyrhythmbox/
$PYTHONPATH /usr/bin/python /usr/share/conkyrhythmbox/conkyRhythmbox.py "$@"


it's displaying artist which is a start...I think I can tweak it from here.

Thank for the help!

---

### Post by hendyfinisha on 2009-08-03
> **aslamp said:**
> i got it working =D. here's a snap of my current setup, with the config:
 
[IMG]http://i27.tinypic.com/24no7s4.jpg[/IMG]
 
```
${offset 69}${font AvantGardeLTMedium:size=10}${exec rhythmbox-client --print-playing-format %tt}
${offset 69}$color1${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/jack/.album}${image /home/jack/.album -p 0,2 -s 64x64}
```
 
the last line is the important stuff. it basically copies whatever the album image is to ~/.album, then conky displays that. make sure to put a ```
imlib_cache_size 0
``` in your conky file so it doesn't cache it.
 
and again, you have to compile conky with "--enable-imlib2" in order to use the $image tag.
 
enjoy!
 
Noob question:
01. Do we add the line 'imlib_cache_size 0' anywhere in the .conckyrc file or other file?
02. How do we compile conky with '--enable-imlib2'?
Thank you.

---

### Post by aslamp on 2009-08-03
1. you can put "imlib_cache_size 0" anywhere in your conkyrc before the TEXT part

2. you need the imlib2 package, so run "sudo apt-get install libimlib2 libimlib2-dev", then run "./configure --enable-imlib2" inside the source folder, then "make" and "sudo make install"

if you have any errors in configuring or compiling, you might need to install those packages =]

---

### Post by hendyfinisha on 2009-08-04
> **aslamp said:**
> 1. you can put "imlib_cache_size 0" anywhere in your conkyrc before the TEXT part
 
2. you need the imlib2 package, so run "sudo apt-get install libimlib2 libimlib2-dev", then run "./configure --enable-imlib2" inside the source folder, then "make" and "sudo make install"
 
if you have any errors in configuring or compiling, you might need to install those packages =]
 
Thanks for your help.
One more question: how to put the album art below? When I used your code, it directly put the art at the top of the conky window.

---

### Post by hendyfinisha on 2009-08-05
> **hendyfinisha said:**
> Thanks for your help.
One more question: how to put the album art below? When I used your code, it directly put the art at the top of the conky window.

I figured it out thanks!
My conky:

---

### Post by DigiBeuk on 2009-08-05
> **hendyfinisha said:**
> I figured it out thanks!
My conky:

Could you tell me how did it my picture is still at the top of my conky window thanks

---

### Post by hendyfinisha on 2009-08-05
> **DigiBeuk said:**
> Could you tell me how did it my picture is still at the top of my conky window thanks
 
You can change the value of 0,20 to x,y. I believe x is for horizontal position and y for vertical position. For example, instead of 0,20, I used 0,250 to make it appear around the middle of the conky window.

---

### Post by Cammy on 2009-08-07
Wow, my rhythmbox lyric script is now overwriting my lyric files with some licensing restriction crap.  I might need to dump rhythmbox and use something else soon.

---

### Post by kaivalagi on 2009-08-07
> **Cammy said:**
> Wow, my rhythmbox lyric script is now overwriting my lyric files with some licensing restriction crap.  I might need to dump rhythmbox and use something else soon.

It screwed my lyrics support in gtk-desktop-info too, all music plugins now show this:

```
Unfortunately, due to licensing restrictions from some of the major music publishers we can no longer return lyrics through the LyricWiki API (where this application gets some or all of its lyrics).

The lyrics for this song can be found at the following URL:
http://lyricwiki.org/The_Verve:Bittersweet_Symphony<br>

(Please note: this is not the fault of the developer who created this application, but is a restriction imposed by the music publishers themselves.)

```

---

### Post by dariusdwtt on 2009-08-13
Same thing here :( my conky is all conky.

BUT with a little investigation, I have found that although the python script I have ([kaivalagi]("http://ubuntuforums.org/member.php?u=494551")) doesn't work,

my Rhythmbox lyrics plug-in (Copyright © 2005-2007 Jonathan Matthew, Eduardo Gonzalez, Sirio Bolaños) which has a couple options of which site to use, still works with

leoslyrics.com and lyrc.com.ar but naturally not with the wiki...

so either the python script can be rewritten to use one, or both, of these,
or
the Rhythmbox plug-in can pipe the info to conky some how...???

What are your thoughts?

---

### Post by kaivalagi on 2009-08-13
> **dariusdwtt said:**
> Same thing here :( my conky is all conky.

BUT with a little investigation, I have found that although the python script I have ([kaivalagi]("http://ubuntuforums.org/member.php?u=494551")) doesn't work,

my Rhythmbox lyrics plug-in (Copyright © 2005-2007 Jonathan Matthew, Eduardo Gonzalez, Sirio Bolaños) which has a couple options of which site to use, still works with

leoslyrics.com and lyrc.com.ar but naturally not with the wiki...

so either the python script can be rewritten to use one, or both, of these,
or
the Rhythmbox plug-in can pipe the info to conky some how...???

What are your thoughts?

I want to investigate other lyrics sites besides lyricwiki, or figure out how to "screen scrape" the html content from the viewable web page on the main lyricwiki site.

The problem is that will the other lyrics sites be subject to the same restrictions lyricwiki is under currently? No doubt they will become more popular now lyricwiki can't provide lyrics via an api...

---

### Post by Takehaniyasubiko on 2009-08-16
Hi, I'm a Linux noob but I've manged to install your wonderful script. I have a question, though. Is it normal for the position of the track information to be updated every 10-15 seconds? I though it should be real-time.

---

### Post by kaivalagi on 2009-08-16
> **Takehaniyasubiko said:**
> Hi, I'm a Linux noob but I've manged to install your wonderful script. I have a question, though. Is it normal for the position of the track information to be updated every 10-15 seconds? I though it should be real-time.

It will update how often you tell it, via the conky execi command.

As conky refreshes everything itself you can't keep state or drive output from events etc.

---

### Post by Takehaniyasubiko on 2009-08-16
> **kaivalagi said:**
> It will update how often you tell it, via the conky execi command.

As conky refreshes everything itself you can't keep state or drive output from events etc.
Thank you! I'm such a noob that I didn't know what "execi" was about. 

Anyway, I've fought with this whole day (especially with email script) but I've managed to overcome the basics and my desktop looks like this:
 
[ATTACH]125122[/ATTACH]

It's simple, I know, but I'm using Linux (Crunchbang) for only two days so I'm still happy that I was able to do at least this much.

Overall, I must say that... Linux is wonderful! I can't believe I was using Windows all this time...

---

### Post by kaivalagi on 2009-08-17
> **Takehaniyasubiko said:**
> Thank you! I'm such a noob that I didn't know what "execi" was about. 

Anyway, I've fought with this whole day (especially with email script) but I've managed to overcome the basics and my desktop looks like this:
 
[ATTACH]125122[/ATTACH]

It's simple, I know, but I'm using Linux (Crunchbang) for only two days so I'm still happy that I was able to do at least this much.

Overall, I must say that... Linux is wonderful! I can't believe I was using Windows all this time...

Welcome to the club :)

---

### Post by wobin77 on 2009-09-08
> **Takehaniyasubiko said:**
> Thank you! I'm such a noob that I didn't know what "execi" was about. 

Anyway, I've fought with this whole day (especially with email script) but I've managed to overcome the basics and my desktop looks like this:
 
[ATTACH]125122[/ATTACH]

It's simple, I know, but I'm using Linux (Crunchbang) for only two days so I'm still happy that I was able to do at least this much.

Overall, I must say that... Linux is wonderful! I can't believe I was using Windows all this time...


Care to post your conkyrc? I like your layout. 
I m also just using linux, and like you i have to say it's way better than windows!

---

### Post by Cammy on 2009-09-10
Question on the lyrics script.

In lyricsdownloader.py, what are the variable names for sing title and artist?  Mine seems to have %s for both.

I'm trying to set it up to use a different lyrics website.

---

### Post by kaivalagi on 2009-09-11
> **Cammy said:**
> Question on the lyrics script.

In lyricsdownloader.py, what are the variable names for sing title and artist?  Mine seems to have %s for both.

I'm trying to set it up to use a different lyrics website.

You're best asking eightmillion, it's his script...

I have just come back from holiday and won't be looking too heavily into anything right now (jet lagged right now after travelling half way round the world in less than 2 days and I have a new job on Monday). I am planning to investigate a way to grab the lyrics from the lyricwiki web pages rather than an api, not sure whether this has already been done (I suspect so as lot's of apps are affected by the switching off of the api functions).

---

### Post by Cammy on 2009-09-11
> **kaivalagi said:**
> You're best asking eightmillion, it's his script...
Sorry, I'd forgotten about that.

> **kaivalagi said:**
> I am planning to investigate a way to grab the lyrics from the lyricwiki web pages rather than an api, not sure whether this has already been done (I suspect so as lot's of apps are affected by the switching off of the api functions).
Yeah, that's along the lines of what I was thinking.  I've checked the source of several lyrics web pages, and they all have the lyrics in a <div>.  It seems like it should be possibly to use regexes to search for that div, then display everything up to the close </div>.  Then, in the script, you'd just have a variable where you'd supply the ID (or class) of the <div> you're looking for, depending on what website you were using.

I've already gotten it to show the web page source on my desktop.  Now I just need to figure out a way to filter for that div.

---

### Post by kaivalagi on 2009-09-11
> **Cammy said:**
> Sorry, I'd forgotten about that.


Yeah, that's along the lines of what I was thinking.  I've checked the source of several lyrics web pages, and they all have the lyrics in a <div>.  It seems like it should be possibly to use regexes to search for that div, then display everything up to the close </div>.  Then, in the script, you'd just have a variable where you'd supply the ID (or class) of the <div> you're looking for, depending on what website you were using.

I've already gotten it to show the web page source on my desktop.  Now I just need to figure out a way to filter for that div.

Yeah, regex is the answer....I'll never master it though, I just can't get my head around the endless options...

---

### Post by igotswings on 2009-09-11
${offset 69}${font AvantGardeLTMedium:size=10}${exec rhythmbox-client --print-playing-format %tt}
${offset 69}$color1${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/jack/.album}${image /home/jack/.album -p 0,2 -s 64x64}

I put this code in put the picture never changes:confused:

---

### Post by kaivalagi on 2009-09-11
> **igotswings said:**
> ${offset 69}${font AvantGardeLTMedium:size=10}${exec rhythmbox-client --print-playing-format %tt}
${offset 69}$color1${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/jack/.album}${image /home/jack/.album -p 0,2 -s 64x64}

I put this code in put the picture never changes:confused:

I think conky caches the image by default, anyone know the way around this? I know there is one...

I don't use conky these days so can't help on this front

You could try the conkyrc thread for more help, as this is a generic conky issue unrelated to my script

Sorry I couldn't be of more help

---

### Post by stepper on 2009-09-11
> **igotswings said:**
> ${offset 69}${font AvantGardeLTMedium:size=10}${exec rhythmbox-client --print-playing-format %tt}
${offset 69}$color1${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/jack/.album}${image /home/jack/.album -p 0,2 -s 64x64}

I put this code in put the picture never changes:confused:

Do you have *imlib_cache_size 0* before TEXT ?

---

### Post by savalas on 2009-09-24
Hello,

I use the rhythmboxscript for conky, and I want to show the output centered, not bottom_left or bottom_right. ...but this the only way I can run it!?

Does anyone have an idea how to center the output?

```
use_xft yes
xftfont HandelGotDLig:size=12
background yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
override_utf8_locale yes
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_borders no
draw_shades no
draw_graph_borders 
stippled_borders 0
border_margin 5
border_width 1
default_color 38FF00
gap_x 15
gap_y 15
alignment bottom_left
minimum_size 400
maximum_width 1280
text_buffer_size 2048

TEXT
${if_running rhythmbox}${exec rhythmbox-client --print-playing}
```

---

### Post by savalas on 2009-09-25
I got it!

minimum_size is / was the problem. I put it up to minimum_size 1280 and now it works!

---

### Post by kaivalagi on 2009-09-25
> **savalas said:**
> I got it!

minimum_size is / was the problem. I put it up to minimum_size 1280 and now it works!

Nice one

A quick heads up, if you have general formatting questions for your conkyrc(s) head on over to the conkyrc thread and ask there, there are a lot of users on there and you'll get assistance really quickly (most of the time)

---

### Post by savalas on 2009-09-25
Thanx for the hint kaivalagi, 

...will do that for the next time!;)

---

### Post by yk1000 on 2009-10-24
> **aslamp said:**
> i got it working =D. here's a snap of my current setup, with the config:

[IMG]http://i27.tinypic.com/24no7s4.jpg[/IMG]

```
${offset 69}${font AvantGardeLTMedium:size=10}${exec rhythmbox-client --print-playing-format %tt}
${offset 69}$color1${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/jack/.album}${image /home/jack/.album -p 0,2 -s 64x64}
```the last line is the important stuff. it basically copies whatever the album image is to ~/.album, then conky displays that. make sure to put a ```
imlib_cache_size 0
``` in your conky file so it doesn't cache it.

and again, you have to compile conky with "--enable-imlib2" in order to use the $image tag.

enjoy!


This may be a dumb question, but why is there a need to copy the image to another location before displaying it with ${image}? Isn't copying the same image every time conky updates (e.g. every second) unnecessary, especially while it's still playing the same song? 

I attempted to make a slideshow of images in conky earlier, and I found that replacing current.jpg with a new image and then showing that image (current.jpg) turned out to use considerably more CPU than showing all the images directly from their respective paths.

So I tried making a small script and parsing this with ${execp testscript}.
#!/bin/bash
file=`conkyRhythmbox --datatype=CA`
echo '${image '$file' -p 450,190 -s 64x64}'
exit

The only issue with this is that the image path might have spaces - when
conky tries to parse the image path it doesn't see the escape character "\ ".
Is there any workaround for this? or is ${image} simply incapable of parsing out the spaces?

---

### Post by kaivalagi on 2009-10-24
> **yk1000 said:**
> This may be a dumb question, but why is there a need to copy the image to another location before displaying it with ${image}? Isn't copying the same image every time conky updates (e.g. every second) unnecessary, especially while it's still playing the same song? 

I attempted to make a slideshow of images in conky earlier, and I found that replacing current.jpg with a new image and then showing that image (current.jpg) turned out to use considerably more CPU than showing all the images directly from their respective paths.

So I tried making a small script and parsing this with ${execp testscript}.
#!/bin/bash
file=`conkyRhythmbox --datatype=CA`
echo '${image '$file' -p 450,190 -s 64x64}'
exit

The only issue with this is that the image path might have spaces - when
conky tries to parse the image path it doesn't see the escape character "\ ".
Is there any workaround for this? or is ${image} simply incapable of parsing out the spaces?

You need to handle the various chars that need escaping...a few string replaces should do it, I don't know the shell command to do that of hand...

---

### Post by trayzz on 2009-10-28
thanks alot!! 
now i can lean back and enjoy my conky once more :popcorn:

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by dilch on 2009-11-11
hi, here ubuntu 9.04 with openbox and crunchbang, everything i used of the script worked except the coverart.
when i'm using the command exec conkyRhythmbox -d CA in a terminal, the terminal just quits;)
very nice function, but what is my mistake, i'm new to conky. i used installationway1



thx for help

[IMG]http://img692.imageshack.us/img692/6378/screenshotconky.jpg[/IMG]

---

### Post by kaivalagi on 2009-11-11
> **dilch said:**
> hi, here ubuntu 9.04 with openbox and crunchbang, everything i used of the script worked except the coverart.
when i'm using the command exec conkyRhythmbox -d CA in a terminal, the terminal just quits;)
very nice function, but what is my mistake, i'm new to conky. i used installationway1

thx for help


Last time I was in Ubuntu was with 9.04 and the coverart datatype option worked fine :confused:

Can you try running the same but with the --verbose option too in case it can tell you anything...and if it closes the terminal again extend the command further piping the output into a text file and then look at that, e.g.:

```
conkyRhythmbox --datatype=CA --verbose > /tmp/rb.txt
```

If you can get more info post it back so I can have more to go on...I have never had or heard of an issue like you describe...so without more info I don't think I can help much

---

### Post by dilch on 2009-11-11
> **kaivalagi said:**
> Last time I was in Ubuntu was with 9.04 and the coverart datatype option worked fine :confused:

Can you try running the same but with the --verbose option too in case it can tell you anything...and if it closes the terminal again extend the command further piping the output into a text file and then look at that, e.g.:

```
conkyRhythmbox --datatype=CA --verbose > /tmp/rb.txt
```

If you can get more info post it back so I can have more to go on...I have never had or heard of an issue like you describe...so without more info I don't think I can help much

here is the terminaline, also a part of it is shown in conky.
```
michael@michael-laptop:~$ conkyRhythmbox --datatype=CA --verbose
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
/media/shared/My\ Music/iTunes/iTunes\ Music/Red\ Hot\ Chili\ Peppers/Greatest\ Hits/Folder.jpg

```

i hope i could help you so you can me;)

here's my conkyTEXT
```
TEXT
AUDIO ${hr 2}
Title:  ${font freemono:size=7.5}${exec conkyRhythmbox -d TI}${font}
Artist: ${font freemono:size=7.5}${exec conkyRhythmbox -d AR}${font}
Album:  ${font freemono:size=7.5}${exec conkyRhythmbox -d AL}${font}
Time:   ${font freemono:size=7.5}${exec conkyRhythmbox -d PT}${font}/${font freemono:size=7.5}${exec conkyRhythmbox -d LE}${font}
${exec conkyRhythmbox --datatype=CA --verbose}
```

---

### Post by kaivalagi on 2009-11-11
> **dilch said:**
> here is the terminaline, also a part of it is shown in conky.
```
michael@michael-laptop:~$ conkyRhythmbox --datatype=CA --verbose
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
/media/shared/My\ Music/iTunes/iTunes\ Music/Red\ Hot\ Chili\ Peppers/Greatest\ Hits/Folder.jpg

```

i hope i could help you so you can me;)

here's my conkyTEXT
```
TEXT
AUDIO ${hr 2}
Title:  ${font freemono:size=7.5}${exec conkyRhythmbox -d TI}${font}
Artist: ${font freemono:size=7.5}${exec conkyRhythmbox -d AR}${font}
Album:  ${font freemono:size=7.5}${exec conkyRhythmbox -d AL}${font}
Time:   ${font freemono:size=7.5}${exec conkyRhythmbox -d PT}${font}/${font freemono:size=7.5}${exec conkyRhythmbox -d LE}${font}
${exec conkyRhythmbox --datatype=CA[COLOR="Red"] --verbose[/COLOR]}
```

Lets have a go...first thing remove the --verbose from the exec in your conkyrc, only good in the terminal for understanding what is going on. If you leave it in your conkyrc you are likely to get a lot of extra output...

Now I think there will be an issue with the image path where you have spaces as escape characters ("\") will be introduced....not sure - use of the sed command to remove escape characters may help. As a minimum you will need to use the $image variable in your conkyrc to display the image for the path returned, there are examples of this and the sed command use in this thread or/and the conkyrc thread I think, just do a few searches.

Looks like you can run the script without it killing your terminal window anyway, which is a good thing...now you just need to display an image from the filepath the script provides :)

Hope that helps and have fun!

---

### Post by dilch on 2009-11-12
```
TEXT
${exec rhythmbox-client --print-playing-format %tt}
${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/michael/.album}${image /home/michael/.album -p 0,2 -s 80x80}
```

at the moment i'm here, had an eye on the explanation some pages before, as you told me^^ i haven't found the sed-command here [http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html") or with google, so i simple copy&pasted the example. i also installed the packages but i don't know what is meant with
> and again, you have to compile conky with "--enable-imlib2" in order to use the $image tag. or the second half in > 2. you need the imlib2 package, so run "sudo apt-get install libimlib2 libimlib2-dev", then run "./configure --enable-imlib2" inside the source folder, then "make" and "sudo make install"
and i believe, this is the reason why conky says "couldn't load image" when i start it from terminal ;) . what exactly do i have to do?

---

### Post by kaivalagi on 2009-11-12
> **dilch said:**
> ```
TEXT
${exec rhythmbox-client --print-playing-format %tt}
${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/michael/.album}${image /home/michael/.album -p 0,2 -s 80x80}
```

at the moment i'm here, had an eye on the explanation some pages before, as you told me^^ i haven't found the sed-command here [http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html") or with google, so i simple copy&pasted the example. i also installed the packages but i don't know what is meant with
 or the second half in 
and i believe, this is the reason why conky says "couldn't load image" when i start it from terminal ;) . what exactly do i have to do?

I am not sure what the state of the conky compiled package is in the main ubuntu repositories but it looks like it doesn't support the $image variable as imlib support isn't compiled in. This means either 1) you need to find an alternative package to install with the support included or 2) you need to compile the source code...

I think the package for conky found here: [https://launchpad.net/~norsetto/+archive/ppa](https://launchpad.net/~norsetto/+archive/ppa) , will sort you out both for image support and also any lua/cairo scripting support too (which you may get into if you read what users are doing in the conkyrc thread)

You can either add this repo to your apt settings (look into synaptic repositories settings for setup or edit your /etc/apt/sources.list) or download the latest package and install manually (you will not recieve updates then though!)

Hope that helps

---

### Post by dilch on 2009-11-12
```
Conky 1.7.2 compiled Thu Sep 17 23:40:46 UTC 2009 for Linux 2.6.27-14-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * wireless
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * Lua

  Lua bindings:

```

i already am "up to date". i thought (because of my bad englisch ;) ) that i have to do something else... so, do you see a mistake in my conkyline?
because 
```
michael@michael-laptop:~$ conkyRhythmbox --datatype=CA --verbose
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA

```
is still the same and started in a terminal, conky is unable to find the picture. so the problem is the sed, or? 

EDIT: or perhaps not... the picture is correct in the folder .album but it seems like conky can't "catch" it
```
Conky: Unable to load image '/home/michael/.album'
sh: ret: not found

```

EDIT2: got it. i'am surpirsed, that it worked for the other people here :) in my case, i need
```

TEXT
${exec rhythmbox-client --print-playing-format %tt}
${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/michael/.album}${image /home/michael/.album[COLOR="Red"]/Folder.jpg[/COLOR] -p 0,2 -s 80x80}

```
, the name of the file missed.

thx for your help

---

### Post by kaivalagi on 2009-11-13
@dilch

Glad you got there in the end and apologies for not helping more, I have not used my own coverart functionality with conky so it's all guess work for me :)

---

### Post by dilch on 2009-11-13
> **kaivalagi said:**
> @dilch

Glad you got there in the end and apologies for not helping more, I have not used my own coverart functionality with conky so it's all guess work for me :)

please no apologies:D it's great work you did + i'm a noob + you showed me the right direction ;)

---

### Post by tacoguard on 2009-11-13
```
conkyRhythmbox --datatype=CA
```
Doesn't return anything for me. Just a blank line.

---

### Post by kaivalagi on 2009-11-14
> **tacoguard said:**
> ```
conkyRhythmbox --datatype=CA
```
Doesn't return anything for me. Just a blank line.

That might be because no coverart can be found for the music you are playing...?

---

### Post by olive33 on 2009-11-22
same problem for me, but not for all albums
cover is present and displayed by the  rhythmbox pluggin 

Ok I found it!
for each album added since my upgrade to Karmic Koala, I have to drag'drop the folder.jpg from nautilus to the cover-display pluggin in Rhythmbox, it creates a copy nammed Cover.jpg.
making this copy "by hand" have no effect.
very strange?
may be a problem with Rhythmbox, the pluggin, but not conkyRhythmbox.py?
O.

---

### Post by olive33 on 2009-11-24
Sorry,
after rebooting, same problem :(
O.

---

### Post by emeraldgirl08 on 2009-12-02
I got album art to display and change with song. However one question I have is how do I exit out of Rhythmbox? I right-click on the tray icon and it just pops back up.


And is it normal for the CPU to be hovering around upper 50's to lower 60%s???
Here is my conkyrc file.

---

### Post by kaivalagi on 2009-12-03
> **emeraldgirl08 said:**
> I got album art to display and change with song. However one question I have is how do I exit out of Rhythmbox? I right-click on the tray icon and it just pops back up.


And is it normal for the CPU to be hovering around upper 50's to lower 60%s???
Here is my conkyrc file.

Right click->Exit/Quit is the norm to exit, you could always run:

```
killall rhythmbox
```

As a last resort...

---

### Post by Pott on 2009-12-04
Ok... I'm a little lost...
I followed the instructions, everything seems to have installed ok.

I pasted this into my Conky file:

${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]

And did the conky -c for the file.

Now obviously I'm missing something there. 
I did this just as a try. I just want it to display Artist, Title, Album, and if possible album art (though all my album art are tagged in the songs with ID3 2.3).

Using Karmic with the latest Conky I believe.

EDIT:

ok, I copied this instead of all the above
${if_running rhythmbox}${exec rhythmbox-client --print-playing}
And I get the title + artist which is a good start but not quite there yet...

EDIT2:

Ok got it!

Title:  ${exec conkyRhythmbox -d TI}
Artist: ${exec conkyRhythmbox -d AR}
Album:  ${exec conkyRhythmbox -d AL}
Time:   ${exec conkyRhythmbox -d PT}/${exec conkyRhythmbox -d LE}

That gives me the correct output. Just a little format tweaking to do now :) Great thread, great script, thanks!!

---

### Post by kaivalagi on 2009-12-04
> **Pott said:**
> Ok... I'm a little lost...
I followed the instructions, everything seems to have installed ok.

I pasted this into my Conky file:

${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]

And did the conky -c for the file.

Now obviously I'm missing something there. 
I did this just as a try. I just want it to display Artist, Title, Album, and if possible album art (though all my album art are tagged in the songs with ID3 2.3).

Using Karmic with the latest Conky I believe.

EDIT:

ok, I copied this instead of all the above
${if_running rhythmbox}${exec rhythmbox-client --print-playing}
And I get the title + artist which is a good start but not quite there yet...

EDIT2:

Ok got it!

Title:  ${exec conkyRhythmbox -d TI}
Artist: ${exec conkyRhythmbox -d AR}
Album:  ${exec conkyRhythmbox -d AL}
Time:   ${exec conkyRhythmbox -d PT}/${exec conkyRhythmbox -d LE}

That gives me the correct output. Just a little format tweaking to do now :) Great thread, great script, thanks!!

Your initial text (based on [] instead of {} ) should be put into a template file, then you can execpi the script giving it the template filepath using --template=blah. This means only one exec is needed in your conky rc file instead of lots...

Glad you got it working with the old fashion way :)

---

### Post by jollyroger87 on 2009-12-14
Is it possible, to put a progress-bar from ConkyRhythmbox into a lua-circle-script ? What's the name and arg ?

---

### Post by kaivalagi on 2009-12-14
> **jollyroger87 said:**
> Is it possible, to put a progress-bar from ConkyRhythmbox into a lua-circle-script ? What's the name and arg ?

You're on your own with the lua scripts, but the script can provide a value from 0 to 100 for progress using this:

```
conkyRhythmbox --datatype=PP
```

Nice idea!

---

### Post by jollyroger87 on 2009-12-15
i failed, anybody a better idea ?  ```
	{ 		name='conkyRhythmbox --datatype=PP', 		arg='conkyRhythmbox --datatype=PP', 		max=100, 		bg_colour=0x000000, 		bg_alpha=0.1, 		fg_colour=0xffcc1e, 		fg_alpha=0.4, 		x=0, y=0, 		radius=108, 		thickness=5, 		start_angle=90, 		end_angle=180 	},
```  ```
Conky: unknown variable conkyrhythmbox Conky: llua_do_call: function conky_ring_stats execution failed: /home/tristan/.conky/rings.lua:186: attempt to perform arithmetic on local 'value' (a nil value)
```

---

### Post by kaivalagi on 2009-12-16
> **jollyroger87 said:**
> i failed, anybody a better idea ?  ```
	{ 		name='conkyRhythmbox --datatype=PP', 		arg='conkyRhythmbox --datatype=PP', 		max=100, 		bg_colour=0x000000, 		bg_alpha=0.1, 		fg_colour=0xffcc1e, 		fg_alpha=0.4, 		x=0, y=0, 		radius=108, 		thickness=5, 		start_angle=90, 		end_angle=180 	},
```  ```
Conky: unknown variable conkyrhythmbox Conky: llua_do_call: function conky_ring_stats execution failed: /home/tristan/.conky/rings.lua:186: attempt to perform arithmetic on local 'value' (a nil value)
```

You need to find a way to make a call to a python script from the lua script directly, rather than getting conky to try itself...I think the conky integration is for conky functions only

---

### Post by Afteroid on 2009-12-30
Hi,

All my mp3-files have embedded covers in its ID3-tags. Rhythmbox displays the covers correctly. But conkyRhythmbox doesn't. Isn't it possible that conkyRhythmbox displays this covers?

Because when I run

```
conkyRhythmbox -d CA
```there is no output. Just a blank line. But when I drag&drop a cover directly in Rhythmbox, I get the correct output afterwards with the command above. But I really don't want to drag&drop all covers in Rhythmbox. So again, isn't it possible, that conkyRhythmbox take the cover from the Tag, or what is my problem?

Thanks in advance.
afteroid

---

### Post by kaivalagi on 2009-12-30
> **Afteroid said:**
> Hi,

All my mp3-files have embedded covers in its ID3-tags. Rhythmbox displays the covers correctly. But conkyRhythmbox doesn't. Isn't it possible that conkyRhythmbox displays this covers?

Because when I run

```
conkyRhythmbox -d CA
```there is no output. Just a blank line. But when I drag&drop a cover directly in Rhythmbox, I get the correct output afterwards with the command above. But I really don't want to drag&drop all covers in Rhythmbox. So again, isn't it possible, that conkyRhythmbox take the cover from the Tag, or what is my problem?

Thanks in advance.
afteroid

Right now it is not possible for my script to get the cover from the tags, I'll need to investigate.

Out of curiosity how do you "inject" covers into the id3 tags in the first place? Is there a good tool out there for it or is it a particular player? A bulk updater perhaps? Sounds like a great idea to do things this way if players generally support it...

---

### Post by Afteroid on 2009-12-30
Thx for your fast reply. 

There are a lot of tag tools out there: easytag, cowbell, Kid3, mp3tag (Windows), etc. There are also command-line tools like eyed3 or id3v2. Or you can do it with amarok scripts or a Sonbird applet. Songbird can e.g. download Covers and put them to the ID3-Tag. Pretty cool thing, especially if you use different players/operating systems. By the way, Rhythmbox has got a bug, that it can't display covers from tags. The Bug is fixes in version 0.12.6.

Is it possible to integrate a datatype option to your script, that print the file path to the current playing song? That would be great. Because then one could display the cover from the ID3-Tag with the --write-images option of eyeD3.

---

### Post by kaivalagi on 2010-01-02
> **Afteroid said:**
> Thx for your fast reply. 

There are a lot of tag tools out there: easytag, cowbell, Kid3, mp3tag (Windows), etc. There are also command-line tools like eyed3 or id3v2. Or you can do it with amarok scripts or a Sonbird applet. Songbird can e.g. download Covers and put them to the ID3-Tag. Pretty cool thing, especially if you use different players/operating systems. By the way, Rhythmbox has got a bug, that it can't display covers from tags. The Bug is fixes in version 0.12.6.

Is it possible to integrate a datatype option to your script, that print the file path to the current playing song? That would be great. Because then one could display the cover from the ID3-Tag with the --write-images option of eyeD3.

When the RB bug is fixed it should I can start on upgrading the script for tag based images I guess. 

Filename:

```
conkyRhythmbox --datatype=FN

```

You can run conkyRhythmbox -h and all the datatypes are listed against the option.

Hope that helps

---

### Post by llawwehttam on 2010-01-05
I've only stated using conky in the last two weeks and have just had a chance to experiment with it.

For all the other sections in my conky there are small icons eg for the OS symbol and the like.

I have seen other people have an icon before the Rhythmbox entry using your script but I don't know how to do it myself. I probably could if I had the time but I'm really busy right now so the help would be appreciated.

---

### Post by kaivalagi on 2010-01-05
> **llawwehttam said:**
> I've only stated using conky in the last two weeks and have just had a chance to experiment with it.

For all the other sections in my conky there are small icons eg for the OS symbol and the like.

I have seen other people have an icon before the Rhythmbox entry using your script but I don't know how to do it myself. I probably could if I had the time but I'm really busy right now so the help would be appreciated.

When you say icon do you mean the cover art for the currently playing song?

If so this script provides the (unescaped) path for cover art using this:

```
conkyRhythmbox --datatype=CA
```

If this is used in conjunction with the $image variable in your conkyrc you can display the image...

I don't have an example for you, maybe someone else can assist? **HINT HINT!!**

If you don't get any help try searching/asking here: [http://ubuntuforums.org/showthread.php?t=281865&page=378](http://ubuntuforums.org/showthread.php?t=281865&page=378)

Hope that helps

Edit: Also, search this thread for **${image** - you will find something useful I am sure, it has been talked about before now

---

### Post by llawwehttam on 2010-01-05
I wasn't actually meaning the album art but now you've suggested it I think i will use that. I meant a rhythmbox icon to go just before the details of your currently playing music.

 If you use ./conkycolours --rhythmbox  when compiling it gives you a small icon but I don't know where it is located (I'm quite new to the world of programming). 
If you know where it is could it possible be built in?

thanks

---

### Post by kaivalagi on 2010-01-05
> **llawwehttam said:**
> I wasn't actually meaning the album art but now you've suggested it I think i will use that. I meant a rhythmbox icon to go just before the details of your currently playing music.

 If you use ./conkycolours --rhythmbox  when compiling it gives you a small icon but I don't know where it is located (I'm quite new to the world of programming). 
If you know where it is could it possible be built in?

thanks

These small icons are either:
[LIST]
[*]a character from a special font
[*]an image displayed using ${image...}
[/LIST]

You're best asking on the .conkyrc thread to be honest, this is not a conkyRhythmbox script issue but general conky howto stuff

Also, take a look at the conky documentation, it is quite helpful - try here: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Sorry but in the linux world some reading is compulsory - no shortcuts here ;) You ought to try Arch Linux...then reading is an absolute necessity

---

### Post by llawwehttam on 2010-01-05
> **kaivalagi said:**
> These small icons are either:
[LIST]
[*]a character from a special font
[*]an image displayed using ${image...}
[/LIST]

You're best asking on the .conkyrc thread to be honest, this is not a conkyRhythmbox script issue but general conky howto stuff

Also, take a look at the conky documentation, it is quite helpful - try here: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Sorry but in the linux world some reading is compulsory - no shortcuts here ;)

lol I know :] Ive been using linux for about 7 years now but it has improved vastly in that time. Even slackware is now usable lol.

---

### Post by kaivalagi on 2010-01-05
> **llawwehttam said:**
> lol I know :] Ive been using linux for about 7 years now but it has improved vastly in that time. Even slackware is now usable lol.

Apologies, I am so used to "I need this now, it's open source so you must help me!" from noobs

Don't get me started on Slackware! I tried using version v1.0 when at Uni many moons ago, I learn't a lot and steered clear of Linux for at least 6 months before having a crack at RH...I am just loving Arch these days though and won't give anything else a second thought...rolling releases are the dogs danglies!

In all seriousness though, you are best asking on the conkyrc thread, most general conky questions have been answered there (just look at the number of posts...)

Any script specific questions just fire away, cheers

---

### Post by llawwehttam on 2010-01-05
> **kaivalagi said:**
> Apologies, I am so used to "I need this now, it's open source so you must help me!" from noobs


lol I know exactly what you mean. I use ubuntu but I don't mind the distro update as I do change distro now and again and obviously have a separate /home partition. I also am planning on setting up a small freeNAS in the corner of my room just to back up to now and again.

If I was planning on using the same install for a longer length of time I might consider arch but I'm too lazy to set it up at the moment. I did use FreeBSD for a while but kde4 put me off it( i had a lot of crashes). the FreeBSD part was fine, the kde4 however was not so if it start working with gnome ( I know it does but its a pain to set up) in the future i might go back to it.

Anyway to get back to topic it is a font called Poky that does the small icons but I'm still having trouble with the artwork. I'll post on the conky thread when I get round to it.

Thanks

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

### Post by hhh on 2010-01-21
Hey kaivalagi,

Maybe you saw my posts in the conky thread. Almost all my listening at home now is from Last FM via Rhythmbox, and I would love to be able to display the cover art from Last FM on my desktop. I've been messing with your scripts but no joy so far. Do you know if this is possible using any of your scripts/apps/plugins?

---

### Post by kaivalagi on 2010-01-22
> **hhh said:**
> Hey kaivalagi,

Maybe you saw my posts in the conky thread. Almost all my listening at home now is from Last FM via Rhythmbox, and I would love to be able to display the cover art from Last FM on my desktop. I've been messing with your scripts but no joy so far. Do you know if this is possible using any of your scripts/apps/plugins?

I did try getting that to work a long long time ago, but hit problems I think

When I get a chance (if) I'll take a look at the weekend and see what I can find out the second time around...

---

### Post by Soovija on 2010-01-23
Maybe I havent found the options, but I would need bitrate information from Rythmbox to show with conky.

Thanks ahead.

---

### Post by sdlynx on 2010-02-06
this is great!  thanks so much =D

---

### Post by wikid_one on 2010-02-11
I'm having a problem getting the script to display the status as paused.  stopped (unknown) and playing work just fine, but when Rhythmbox is paused, the output still stays at Playing.  This goes for pausing mid song as well as immediately upon starting before anything is played.

```

[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Unknown
[peter@archbox ~]$ rhythmbox-client --play
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Playing
[peter@archbox ~]$ rhythmbox-client --pause
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Playing
[peter@archbox ~]$ rhythmbox-client --quit
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Unknown

```

Let me know what other info you need in order to help figure out what is going on. Thanks.

---

### Post by Metalworks on 2010-02-28
hi noob here, how to change rhythmbox position like this one..?
[http://i695.photobucket.com/albums/vv319/dityamada/Linux/myDesk.png](http://i695.photobucket.com/albums/vv319/dityamada/Linux/myDesk.png)

while mine is like this:
[IMG]http://i46.tinypic.com/o8xbg4.png[/IMG]

on the bottom right, i know that the pic above is using banshee, but it also conky, can't my rhythmbox arranged like that..? along with system, btw, my system already set on the top right, and my rhythmbox part away from System.

thank you.

---

### Post by kaivalagi on 2010-02-28
> **Metalworks said:**
> hi noob here, how to change rhythmbox position like this one..?
[http://i695.photobucket.com/albums/vv319/dityamada/Linux/myDesk.png](http://i695.photobucket.com/albums/vv319/dityamada/Linux/myDesk.png)

while mine is like this:
[IMG]http://i46.tinypic.com/o8xbg4.png[/IMG]

on the bottom right, i know that the pic above is using banshee, but it also conky, can't my rhythmbox arranged like that..? along with system, btw, my system already set on the top right, and my rhythmbox part away from System.

thank you.

Look in my PPA here: [https://launchpad.net/~m-buck/+archive/rhythmbox](https://launchpad.net/~m-buck/+archive/rhythmbox) , you'll find a rhythmbox plugin which is quite good, you can also control the music with it

If you want to use conky you'll need to get creative :)

---

### Post by Metalworks on 2010-03-01
> **kaivalagi said:**
> Look in my PPA here: [https://launchpad.net/~m-buck/+archive/rhythmbox](https://launchpad.net/~m-buck/+archive/rhythmbox) , you'll find a rhythmbox plugin which is quite good, you can also control the music with it

If you want to use conky you'll need to get creative :)

thank you, i have download the deb file and installed it but i can get it appear on my desktop, is there anyway or what's the command for it..?

sorry i never use ubuntu before, that's why i'm here to learn from the masters :)

---

### Post by kaivalagi on 2010-03-01
> **Metalworks said:**
> thank you, i have download the deb file and installed it but i can get it appear on my desktop, is there anyway or what's the command for it..?

sorry i never use ubuntu before, that's why i'm here to learn from the masters :)

It is a rhythmbox plugin not a seperate application so you need to go into rhythmbox settings and enable it there, once in setup mode you can resize and move the "box" around on the desktop to suit.

I wouldn't call any of us lot masters, the masters are the ones that put all the effort into creating GNU\Linux, and I don't use Ubuntu anyway :)

Cheers

---

### Post by Metalworks on 2010-03-01
> **kaivalagi said:**
> It is a rhythmbox plugin not a seperate application so you need to go into rhythmbox settings and enable it there, once in setup mode you can resize and move the "box" around on the desktop to suit.

I wouldn't call any of us lot masters, the masters are the ones that put all the effort into creating GNU\Linux, and I don't use Ubuntu anyway :)

Cheers

thank you, i already figure it out tho, only takes a few edit on .conkycolors and .conkycr :D

---

### Post by wikid_one on 2010-03-02
> **wikid_one said:**
> I'm having a problem getting the script to display the status as paused.  stopped (unknown) and playing work just fine, but when Rhythmbox is paused, the output still stays at Playing.  This goes for pausing mid song as well as immediately upon starting before anything is played.

```

[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Unknown
[peter@archbox ~]$ rhythmbox-client --play
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Playing
[peter@archbox ~]$ rhythmbox-client --pause
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Playing
[peter@archbox ~]$ rhythmbox-client --quit
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Unknown

```

Let me know what other info you need in order to help figure out what is going on. Thanks.

Just a little update...
I switched to Banshee and installed your conkyBanshee script. Everything works as it should on that one.  Just in case anyone is interested, here is my setup for both the Banshee and Rhythmbox scripts (just replace conkyBanshee with conkyRhythmbox where necessary)

```
#!/bin/bash

test=`conkyBanshee --datatype=ST`
if [ $test == "Playing" ]; then 
    echo "&#9654;"
elif [ $test == "Paused" ]; then 
    echo "&#10074;&#10074;"
else
    echo "&#9632;"
fi

```

```
TEXT
${alignc 5}${font DejaVu Sans Mono:size=18}${color ebebeb}${execi 1 ~/.scripts/rbox}${font}
${color 3465a4}Artist:
${color ebebeb}${exec conkyBanshee --datatype=AR}
${color 3465a4}Title:
${color ebebeb}${exec conkyBanshee --datatype=TI}

${color ebebeb}${font}${exec conkyBanshee --datatype=PT}${alignr}${exec conkyBanshee --datatype=LE}
${execibar 1 conkyBanshee --datatype=PP}

```

---

### Post by alecive on 2010-03-08
> **wikid_one said:**
> I'm having a problem getting the script to display the status as paused.  stopped (unknown) and playing work just fine, but when Rhythmbox is paused, the output still stays at Playing.  This goes for pausing mid song as well as immediately upon starting before anything is played.

```

[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Unknown
[peter@archbox ~]$ rhythmbox-client --play
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Playing
[peter@archbox ~]$ rhythmbox-client --pause
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Playing
[peter@archbox ~]$ rhythmbox-client --quit
[peter@archbox ~]$ conkyRhythmbox --datatype=ST
Unknown

```Let me know what other info you need in order to help figure out what is going on. Thanks.

But there is a way to solve this problem?

---

### Post by kaivalagi on 2010-03-08
> **alecive said:**
> But there is a way to solve this problem?

Looking at the code for handling status, if nothing is found to be playing but the player is running you should get "stopped" and if playing you should get "playing"..."unknown" if rhythmbox is not running, nothing for paused...I think a long time ago when this was written there were no other methods to discover status.

Edit: I have just checked and I think I can get a paused status using the getPlaying option after confirming there is a song loaded (stopped or not stopped status). I'll attach a modified .py file for replacement soon so you can test and make sure it works...

[COLOR="Blue"]Edit2: If you can't wait for the release find attached the .py file that needs to be replaced to get the fix. Just copy it over the top of the old one here: /usr/share/conkyrhythmbox/conkyRhythmbox.py

Cheers[/COLOR]

---

### Post by kaivalagi on 2010-03-08
**[COLOR=Blue][SIZE=4]UPDATE[/SIZE][/COLOR]**

I have updated the script to correctly output the "paused" playing status, as mentioned in previous posts.
 
Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.08_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.08_source.changes)

The apt packages should be available shortly

Chimo

---

### Post by alecive on 2010-03-08
Thanks a lot!

Without your scripts my conky would be useless!

:popcorn::P

---

### Post by kaivalagi on 2010-03-12
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

I have updated the script to include a bitrate datatype, used via --datatype=BR

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.09_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.09_source.changes)

The apt packages are available now

Cheers

---

### Post by Soovija on 2010-05-01
Finally. Thanks m8.

---

### Post by konlungkao on 2010-05-01
Finally. Thanks m8.:P

---

### Post by kaivalagi on 2010-05-01
> **Soovija said:**
> Finally. Thanks m8.

> **konlungkao said:**
> Finally. Thanks m8.:P

What do you mean, it's been almost 6 weeks since that update :lolflag:

---

### Post by eternal_restt on 2010-05-06
hey, i installed the script along with conky-colors in arch from source, and the script doesn't work, just shows up as unknown for everything, ideas?

---

### Post by kaivalagi on 2010-05-06
> **eternal_restt said:**
> hey, i installed the script along with conky-colors in arch from source, and the script doesn't work, just shows up as unknown for everything, ideas?

conky colours is nothing to do with me sorry, try looking at the first post here and at the example found in /usr/share/conkyrhythmbox/example

Hope that helps

---

### Post by eternal_restt on 2010-05-06
is there any plugin i need to enable in rythmnbox?

---

### Post by kaivalagi on 2010-05-07
> **eternal_restt said:**
> is there any plugin i need to enable in rythmnbox?

Nope, just conky to output the results of this script. If you want coverart on the desktop you may want to use the rhythmbox-desktop-art package also available in the conkyhardcore ppa, this will appear as a plugin in rhythmbox settings...

---

### Post by rajadain on 2010-05-07
Hey,
First off, thanks for the conky scripts: they really make me want to spend more time on Linux than anything else.

I installed this script to get info on my Rhythmbox, and I want to use it with the conky I got from [~sen7 in deviantArt]("http://sen7.deviantart.com/art/Conky-Mira-100078939"). Here's the code that I use in his file:

```
TEXT
${color a4a4a4}${alignc 2}${font DejaVu Sans Mono:size=18}${execi 1 ~/scripts/mpd.awk}
${font}${color DAA520}${alignc}${voffset -15}${exec conkyRhythmbox --statustext=&#9654;,&#10074;&#10074;  ,&#9632; --datatype=ST}

${color FFC125}Artist:
${color a4a4a4}${exec conkyRhythmbox --datatype=AR}
${color FFC125}Title:
${color a4a4a4}${exec conkyRhythmbox --datatype=TI}
${color FFC125}Album:
${color a4a4a4}${exec conkyRhythmbox --datatype=AL}

${color a4a4a4}${exec conkyRhythmbox --datatype=PT}${alignr}${exec conkyRhythmbox --datatype=LE}
```

Now the problem of course is the Play, Pause and Stop buttons. When I try and run this, I get the following error:

```
Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 528, in <module>
    main()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 525, in main
    rhythmboxinfo.writeOutput()
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 477, in writeOutput
    print output.encode("utf-8")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 0: ordinal not in range(128)

```

Do you think you could help me out by getting your script to recognize Unicode characters?

---

### Post by rajadain on 2010-05-07
And is there some way of getting a "bar"? Look at the this link for the kind of look that I'm trying to go for: [http://sen7.deviantart.com/art/Conky-Mira-100078939](http://sen7.deviantart.com/art/Conky-Mira-100078939). I just need the buttons and play bar. Thanks!

---

### Post by kaivalagi on 2010-05-07
> **rajadain said:**
> Do you think you could help me out by getting your script to recognize Unicode characters?

Try adding this to your conkyrc, above the "TEXT" line somewhere:
```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
```

> **rajadain said:**
> And is there some way of getting a "bar"? Look at the this link for the kind of look that I'm trying to go for: [http://sen7.deviantart.com/art/Conky-Mira-100078939](http://sen7.deviantart.com/art/Conky-Mira-100078939). I just need the buttons and play bar. Thanks!

For a bar you could use the --datatype=PP (percentage position) within the $execibar variable...e.g.
```
${execibar 1 conkyRhythmbox --datatype=PP}
```

Take a look at [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html) for more info on what you can do with conky. More info about the script can be found in the first post of this thread or by running:
```
conkyRhythmbox -h
```

Hope that helps :)

---

### Post by Pablo Pablovski on 2010-05-07
Hey kaivalagi,
I've been using your excellent scripts for a while now, and all of a sudden conkyRhythmbox has stopped displaying album art. I have v2.09 on Lucid.

Conky extract:

```
${if_running rhythmbox}${font Aller:size=11}${color #6E9CC7}Rhythmbox Is Now Playing:${execp rm "/home/pablo/.album"}${image /home/pablo/.album -p 0,885 -s 72x72}
${color darkgrey}${execp conkyRhythmbox --datatype=TI}${font Aller:size=9}${color}
${execp conkyRhythmbox --datatype=AL}
${execp conkyRhythmbox --datatype=AR}
${execibar 1 conkyRhythmbox --datatype=PP}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/pablo/.album}${image /home/pablo/.album -p 0,885 -s 72x72}
```

If I enter "conkyRthymbox --datatype=CA", the filename and path are returned, so I think there's something wrong with the cp. But I don't know what.

I also have conkyBanshee installed, and it works fine - with an equivalent (read: the same) CP command in the same conky script. So... help!

P

---

### Post by Pablo Pablovski on 2010-05-07
> **Pablo Pablovski said:**
> Hey kaivalagi,
I've been using your excellent scripts for a while now, and all of a sudden conkyRhythmbox has stopped displaying album art. I have v2.09 on Lucid.

Conky extract:

```
${if_running rhythmbox}${font Aller:size=11}${color #6E9CC7}Rhythmbox Is Now Playing:${execp rm "/home/pablo/.album"}${image /home/pablo/.album -p 0,885 -s 72x72}
${color darkgrey}${execp conkyRhythmbox --datatype=TI}${font Aller:size=9}${color}
${execp conkyRhythmbox --datatype=AL}
${execp conkyRhythmbox --datatype=AR}
${execibar 1 conkyRhythmbox --datatype=PP}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/pablo/.album}${image /home/pablo/.album -p 0,885 -s 72x72}
```

If I enter "conkyRthymbox --datatype=CA", the filename and path are returned, so I think there's something wrong with the cp. But I don't know what.

I also have conkyBanshee installed, and it works fine - with an equivalent (read: the same) CP command in the same conky script. So... help!

P

And.. it's started working again. kaivalagi, those are some mysterious powers you got, f'sure!

---

### Post by rajadain on 2010-05-07
> **kaivalagi said:**
> Try adding this to your conkyrc, above the "TEXT" line somewhere:
```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
```


I already have that line in my conkyrc file. I'm posting the whole thing this time (in case something else was left out that could help with the analysis):

```
# Use Xft?
use_xft yes
xftfont cure:size=6

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window  yes
own_window_transparent no
own_window_type widget
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

maximum_width 87

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color 303030
#default_shade_color white
#default_outline_color black
own_window_colour 262524

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 565

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

TEXT
${color a4a4a4}${alignc 2}${font DejaVu Sans Mono:size=18}
#${execi 1 ~/scripts/mpd.awk}
${font}${color DAA520}${alignc}${voffset -15}${exec conkyRhythmbox --statustext=&#9654;,&#10074;&#10074;,&#9632; --datatype=ST} 
${color FFC125}Random:${color a4a4a4}${alignr}${mpd_random}

${color FFC125}Artist:
${color a4a4a4}${exec conkyRhythmbox --datatype=AR}
${color FFC125}Title:
${color a4a4a4}${exec conkyRhythmbox --datatype=TI}
${color FFC125}Album:
${color a4a4a4}${exec conkyRhythmbox --datatype=AL}

${color a4a4a4}${exec conkyRhythmbox --datatype=PT}${alignr}${exec conkyRhythmbox --datatype=LE}
${color DAA520}${execibar 1 conkyRhythmbox --datatype=PP}
```

Also, am I doing something wrong (calling exec conkyRhythmbox too many times) ? Because whenever I run this conky, my processor usage shoots up to 30% and stays there (whereas it hovers around 3-5% without it). My other conkys don't do this, so I'm pretty sure its because of the script. It happens in your example as well.

The original author made it for MPD using an awk script, but its probably not applicable in this case. I don't know if that would've taken less resources or not.

<Sigh>. With a 2 year old laptop equipped with one of the oldest C2D's still out there and has heating issues, I guess I'll just give up. Thanks for everything anyway: your scripts are really good and I use the email one all the time. :)

EDIT:
I found a less resource intensive way to get what I wanted. Well, not all of it, because this isn't as powerful as your script, but it does my job:

```
${color FFC125}Artist:
${color a4a4a4}${exec rhythmbox-client --no-start --no-present --print-playing-format "%ta"}
${color FFC125}Title:
${color a4a4a4}${exec rhythmbox-client --no-start --no-present --print-playing-format "%tt"}
${color FFC125}Album:
${color a4a4a4}${exec rhythmbox-client --no-start --no-present --print-playing-format "%at"}

${color a4a4a4}${exec rhythmbox-client --no-start --no-present --print-playing-format "%te"}${alignr}${exec rhythmbox-client --no-start --no-present --print-playing-format "%td"}
```

Still no bar, and it doesn't have the status ability that yours had, but it's good enough for me for now :).

---

### Post by kaivalagi on 2010-05-08
@rajadain

You can use templates with this script, so it only gets called once. By putting all the required bits into a template and then calling the script in the conkyrc once with an a associated --template setting, the script will do everything in one go, should bring down CPU usage a bit!

Have a look at the example conkyrc and conkyRhythmbox.template files under /usr/share/conkyrhythmbox/example

Cheers

---

### Post by kaivalagi on 2010-05-08
> **Pablo Pablovski said:**
> And.. it's started working again. kaivalagi, those are some mysterious powers you got, f'sure!

:lolflag:

Probably one song works and another doesn't?

---

### Post by Jonas_Stolt on 2010-05-13
I listen to radio through Rhytmbox. Artist and Title shows as Untitled in Conky. Is there anyway to use if/else filter here and not show artist and titled when it's untitled?

---

### Post by kaivalagi on 2010-05-13
> **Jonas_Stolt said:**
> I listen to radio through Rhytmbox. Artist and Title shows as Untitled in Conky. Is there anyway to use if/else filter here and not show artist and titled when it's untitled?

The script will show "Unknown" if there is no data so I am assuming that Rhythmbox provides "Untitled" for radio. This means the script is not at fault for this and shouldn't really been adjusted to suit. I suggest using a sed command in the conkyrc to remove "Untitled" from any output text, here's a good list of sed one liners: [http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

Here an example of it removing untitled from an echoed line of text:
```
echo "abc Untitled 123" | sed 's/Untitled//g'
```

This outputs "abc  123"

essentially you call the script for the title using something like this inside the conkyrc (not tested):
```
${exec conkyRhythmbox --datatype=TI | sed 's/Untitled//g'}
```

Hope that helps

---

### Post by Jonas_Stolt on 2010-05-13
> **kaivalagi said:**
> 
essentially you call the script for the title using something like this inside the conkyrc (not tested):
```
${exec conkyRhythmbox --datatype=TI | sed 's/Untitled//g'}
```
Hope that helps

Thank you.
That works fine.

---

### Post by reksveks on 2010-05-30
Hi, 
I have trying to get this script to work all day. However i cannot get Conky to show the album cover, for all but one album there is no output from the script when i used the "-datatype=CA" extension also it only says the location of the file but doesn't view it.
Reksveks

---

### Post by reksveks on 2010-05-30
Hi, 
I have trying to get this script to work all day. However i cannot get  Conky to show the album cover, for all but one album there is no output  from the script when i used the "-datatype=CA" extension also it only  says the location of the file but doesn't view it. The notification in Rhythmbox shows an album cover
Reksveks

Conky Version is 1.8 and conkyRhythmbox Version is 2.09

---

### Post by merlin_ie on 2010-05-30
> **reksveks said:**
> Hi, 
I have trying to get this script to work all day. However i cannot get Conky to show the album cover, for all but one album there is no output from the script when i used the "-datatype=CA" extension also it only says the location of the file but doesn't view it.
Reksveks

can you show the part of code you're using please

---

### Post by reksveks on 2010-05-30
I am confused to what you are asking for ? my current conkyrc files is  all confused because i have tried a number of different scripts that aim  to download the album art from a website, so i have just commented out  the line that is not used at the moment.

I think this is the part relevant to this script 
> 
${offset 69}${font AvantGardeLTMedium:size=10}${exec rhythmbox-client  --print-playing-format %tt}
${offset 69}$color1${exec rhythmbox-client --print-playing-format  %ta}$font${exec ret}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`"  /home/reksveks/.album}${image /home/reksveks/.album -p 0,2 -s  64x64}This what happens when i use the script in terminal

> reksveks@reksveks-iomega ~ $ conkyRhythmbox --datatype=CA
/home/reksveks/.cache/rhythmbox/covers/Nobuo\ Uematsu\ -\ Final\  Fantasy\ VII.jpg
[I]change song 
reksveks@reksveks-iomega ~ $ conkyRhythmbox --datatype=CA
  
[/I]I am confused to why it becomes blank.

A couple of other things, i am currently booting Linux Mint 9 off a usb hardrive and the music library is there in a separation ntfs partition; probably no relevance however i am not sure.

---

### Post by merlin_ie on 2010-05-30
> **reksveks said:**
> I am confused to what you are asking for ? my current conkyrc files is  all confused because i have tried a number of different scripts that aim  to download the album art from a website, so i have just commented out  the line that is not used at the moment.

I think this is the part relevant to this script 


This what happens when i use the script in terminal


I am confused to why it becomes blank

To be honest, I use a script for Amarok 1.4. Well, I don't know what to tell you. from looking at that, I can see spaces in the file names so that might be something. other than that, if you look in your conkyrc, you will see something about "imlib cache". might help to put that to 0. other than that, I'll leave it to the Rhythmbox experts. sorry, I thought I might be able to help in some way:(

---

### Post by justmecharly on 2010-06-18
my conky doesnt show the album art.

${exec conkyRhythmbox -d CA}

gives me the path to the art but not the picture.

i read ppl had this problem before but i never found the working answer.

i use the latest conky, it should be able to display images.

i read that i have to combine it maybe, but how? 

i would love to get help with how my conky entry has to look like for it to work.

thank you

---

### Post by kaivalagi on 2010-06-18
> **justmecharly said:**
> my conky doesnt show the album art.

${exec conkyRhythmbox -d CA}

gives me the path to the art but not the picture.

i read ppl had this problem before but i never found the working answer.

i use the latest conky, it should be able to display images.

i read that i have to combine it maybe, but how? 

i would love to get help with how my conky entry has to look like for it to work.

thank you

All my script does is provide the image path, you need to use this with the image variable in conky to output the actual image...have a look in the pages on conky hardcore, a link is in  my sig as "conky guide"

---

### Post by justmecharly on 2010-06-20
thank you for the fast response. 

using the image variable is exactly what i cant get to work.

how does the conky config file line has to look like?

${exec conkyRhythmbox -d CA} this gives me the path...

so how do i combine that with $image ?

i need help with how the code has to look like.

---

### Post by kaivalagi on 2010-06-20
There are several ways, I way you can capture the path and use it is via a template file and display that...e.g.

The main call of rhythmbox with template
```
${execpi 1 conkyRhythmbox --template="path/to/template/file"}
```

The template has something like this in it along with other wanted output such as track name, artist etc:
```
${image [--datatype=CA] -p 0,0 -s 300x300}
```
Note that the "[--datatype=CA]" will get replaced with the actual path.

Much the same as described in the conky hardcore site for weather image output...worth a proper read as mentioned already!

Hope that helps

---

### Post by fireandfuel on 2010-07-26
Hi, I find out that conkyRhythmbox output URI instead of path to the cover art.
So it doesn't work when you have space characters or special characters at the path to the cover art.

I have the same problem with Amarok2. Thus I edited a Amarok1.4 script to display it:
[http://ubuntuforums.org/showpost.php?p=9478352&postcount=2](http://ubuntuforums.org/showpost.php?p=9478352&postcount=2)

PS: The script for Amarok 1.4 is at the same thread.

A command to encode URIs is:
```
perl -MURI::Escape -lne 'print uri_unescape($_)'
```

---

### Post by wlourf on 2010-08-30
Hi kaivalagi,

About your script conkyRhythmbox, I wanted to display times in second format instead of mm:ss format (125 instead 02:05). I didn't find the option in your script, I am right ?
It is for use with a lua script, the famous Londonali's rings or my rings which can display elapsed time on a ring.
So I add this option to the script -S --seconds for an output in seconds. As I don't need to use a template with the Lua script, I call the script like this :
```
conkyRhythmbox --datatype=PT  -S
conkyRhythmbox --datatype=LE  -S

```Am I right?
I attach the modified script to this message. If you can have a look to it as I don't use python everyday; thanks !

---

### Post by kaivalagi on 2010-08-30
> **wlourf said:**
> Hi kaivalagi,
About your script conkyRhythmbox, I wanted to display times in second format instead of mm:ss format (125 instead 02:05). I didn't find the option in your script, I am right ?
It is for use with a lua script, the famous Londonali's rings or my rings which can display elapsed time on a ring.
So I add this option to the script -S --seconds for an output in seconds. As I don't need to use a template with the Lua script, I call the script like this :
```
conkyRhythmbox --datatype=PT  -S
conkyRhythmbox --datatype=LE  -S

```Am I right?
I attach the modified script to this message. If you can have a look to it as I don't use python everyday; thanks !

Yeah, looks like you got it working just fine, although you missed the situation when nothing is available and defaults are output.

I kept the -S and use --secondsoutput for the options but the innards changed a little. Depending on time I may well update all my music scripts to have this option :)

Can you try the attached to make sure it does what you expect too before I roll out a package?

Thanks


Nice to see someone else having a go at python AND lua!

edit: now preparing packages for banshee, exaile, guayadeque and rhythmbox which will include -S/--secondsoutput options ;)

---

### Post by wlourf on 2010-08-30
well I ran the changes I made to your script without rhythmbox and I didn't get any errrors.
Anyway, your last file works just fine with Lua scripts :
I can run it with :
```
    name="",
    arg=conky_parse("${exec conkyRhythmbox --datatype=PT -S}"),
    max=conky_parse("${exec conkyRhythmbox --datatype=LE -S}"),    
```or with :
```
    name="",
    arg= io.popen('conkyRhythmbox --datatype=PT -S','r'):read(),
    max= io.popen('conkyRhythmbox --datatype=LE -S','r'):read(),
```which should be faster I guess but not so easy to use for everybody.

For reminder, parameters in the Lua scripts are usually like that ```
name="cpu",
arg="cpu1",
max=100
```to display cpu usage with max at 100 %

Thanks for your quick answer !

---

### Post by kaivalagi on 2010-08-30
You could have used the PP datatype me thinks...and set the max to 100...

Oh well, never mind lol

---

### Post by wlourf on 2010-08-30
ah yes ! good idea ! :-)

---

### Post by kaivalagi on 2010-08-30
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Changes as follows:
[LIST]
[*]Added --secondsoutput / -S option to output time in seconds
[*]Added conkyRhythmbox-GetCoverArt script although currently not triggering on track change, it seems the dbus signal for track change isn't working... :(
[/LIST]
 
Package changes can be seen here:  [http://launchpadlibrarian.net/54623596/conkyrhythmbox_2.12_source.changes](http://launchpadlibrarian.net/54623596/conkyrhythmbox_2.12_source.changes)

The apt packages should be available shortly

Cheers

---

### Post by kaivalagi on 2010-08-30
> **wlourf said:**
> ah yes ! good idea ! :-)

Bit of a wasted effort on my part really...next time if you could explain in full what you intend on trying to do I may be able to set you straight without too much effort!

Trying to think of what you could use the seconds output for now, binary output maybe? Similar to the binary clock...or outputting straight seconds for time

---

### Post by wlourf on 2010-08-30
sorry K. I didn't realize my mistake sooner and my english is certainly too poor some times !

Anyway, I find an usage to the seconds output option : my ring starts as usual clockwise with a 100 %-scale ring, and when time left is less than 60 seconds, the ring turns anti-clockwise with a 60 seconds-scale ring, like a countdown counter. Colours also change:
```
local time_le=io.popen('conkyRhythmbox --datatype=LE -S','r'):read()
local time_pt=io.popen('conkyRhythmbox --datatype=PT -S','r'):read()
local time_left = time_le-time_pt

if time_left<60 then
    rb_arg=time_left
    rb_max=60
    rb_colour=0xFF0000
    rb_inverse=true
else
    rb_arg=io.popen('conkyRhythmbox --datatype=PP','r'):read()
    rb_max=100
    rb_colour=0xFFFF00
    rb_inverse=false
end


rings_settings={
    {
    name="",
    arg=rb_arg,
    max=rb_max,    
    xc=650,
    yc=100,
    radius=40,
    thickness=10,
    sectors=60,
    inverse_arc=rb_inverse,
    bg_colour1={{0,0x999999,0},{0.5,0x999999,1}, {1,0x999999,0}},
    fg_colour1={{0,rb_colour,0},{0.5,rb_colour,1}, {1,rb_colour,0}},
    },        }
```

---

### Post by kaivalagi on 2010-08-30
It's okay, gave me something to do in between water changes on my fish tanks today :)
To be fair though wlourf it's probably a good thing this seconds only output, I am sure lua scripters will find lots they can do with it like you have...would love to see a vid of this functionality you've created!

I may well have to start creating lua content soon, and play catch with with you guys :)

---

### Post by wlourf on 2010-08-30
One last question before you go playing! I'm trying to run this script [http://ubuntuforums.org/showpost.php?p=8117609&postcount=9846](http://ubuntuforums.org/showpost.php?p=8117609&postcount=9846) which should  convert the album from square to circle.
It works fine with amarok but if I replace this line :
```
cover="$(dcop amarok player coverImage)"
```by this one
```
cover="$(conkyRhythmbox --datatype=CA)"
``` I get an error : unable to open the file. 
I think it's because there is spaces in the filename (there is no space with amarok cache) but I can't get it working, even after playing with $IFS.
It's certainly a bash script problem but if you have an idea about it ...:)

---

### Post by kaivalagi on 2010-08-30
Can you compare the 2 commands for the same music?

I dont use kde or amarok so can't see what the problem is, a comparison would be good

It would be nice to see what equivalent path works with amarok compared to RB...then I may be able to do something in the script itself to cope

edit: I doubt you have amarok installed either...you need to give me more to go on otherwise I'd be doing everything you are trying and I don't have the time or inclination

---

### Post by wlourf on 2010-08-30
I don't use kde either but amarok runs on my openbox.

I have the same behaviour with this simple script :
```
#!/bin/bash

#cover="$(dcop amarok player coverImage)"
cover="$(conkyRhythmbox --datatype=CA)"
echo $cover
cp $cover /tmp/cover

```If I use the line for amarok, output is like this :
```
/home/wlourf/.kde/share/apps/amarok/albumcovers/cache/130@3cff6d32f16f9e9c05a567bba686a710
```If I use the line for rhythmbox, output is :
```
/home/wlourf/Musique/Nirvana\ -\ Incesticide\ \(1992\)/Nirvana-Incesticide-Trasera.jpg
cp: option invalide -- '\'

```which means Invalid option -- '\' :D

If now I rename the folder witout spaces, it works, the output is :
```
/home/wlourf/Musique/Nirvana-Incesticide-1992/Nirvana-Incesticide-Trasera.jpg

```(Unfortunately, your script doesn't read the ID3 Tag to see if a cover is tagged in the file)

Now if I try the command cp in a terminal with a filename with a space, theses two lines work :
```
cp "/home/wlourf/tmp/cover space" out1
cp /home/wlourf/tmp/cover\ space out2
```And If I use the output where I have the message "Invalid output" before, it works (in a terminal):
```
cp /home/wlourf/Musique/Nirvana\ -\ Incesticide\ \(1992\)/Nirvana-Incesticide-Trasera.jpg /tmp/out2
```It's why I say the output of your script is OK but I can't use it in a bash script, so it's a bash script problem I can't solve myself:(

---

### Post by kaivalagi on 2010-08-30
Would be be better if the "\" escape chars weren't there, i.e. you just wrap the path in double quotes? If so just edit the existing py and remove these lines:

```

                                #handle escape chars, are there anymore???
                                coverart = coverart.replace(" ", "\ ")
                                coverart = coverart.replace("(", "\(")
                                coverart = coverart.replace(")", "\)")

```

Oh, and the getcoverart script I added into the package (which fails to trigger on track change) does pull art from the id3 tags, it works with guayadeque just fine.

This function (as part of the whole conkyRhythmbox-GetCoverart.py script) works with rhythmbox but iI haven't added the equivalent to the main script as it would potentially happen every second! I want to get the conkyRhythmbox-GetCoverart.py one working instead as it will happen only when required (dbus events don't seem to work though):

```

import eyeD3

...

    def getCoverartImage(self,savepath):

        # get file path from dbus track properties
        if "location" in self.props:
            location = self.props["location"]
        
        srcfilepath = location.replace("file://","").replace("%20"," ")
        dstfolder = os.path.dirname(savepath) 
        dstfile = savepath.replace(os.path.dirname(savepath)+"/","")
        
        tag = eyeD3.Tag()
        
        if os.path.isfile(srcfilepath):
            if os.path.splitext(srcfilepath)[1] == ".mp3":
                # Extract picture
                try:
                    tag.link(srcfilepath)
                    for image in tag.getImages():
                        image.writeFile(dstfolder, dstfile)
                        return savepath
                except:
                    print "Unable to extract image for: " + srcfilepath
                    traceback.print_exc()
        return ""


```

---

### Post by wlourf on 2010-08-30
> **kaivalagi said:**
> Would be be better if the "\" escape chars weren't there, i.e. you just wrap the path in double quotes? If so just edit the existing py and remove these lines:

```

                                #handle escape chars, are there anymore???
                                coverart = coverart.replace(" ", "\ ")
                                coverart = coverart.replace("(", "\(")
                                coverart = coverart.replace(")", "\)")

```Oh, and the getcoverart script I added into the package (which fails to trigger on track change) does pull art from the id3 tags, it works with guayadeque just fine.

This function (as part of the whole conkyRhythmbox-GetCoverart.py script) works with rhythmbox but iI haven't added the equivalent to the main script as it would potentially happen every second! I want to get the conkyRhythmbox-GetCoverart.py one working instead as it will happen only when required (dbus events don't seem to work though):

```

import eyeD3

...

    def getCoverartImage(self,savepath):

        # get file path from dbus track properties
        if "location" in self.props:
            location = self.props["location"]
        
        srcfilepath = location.replace("file://","").replace("%20"," ")
        dstfolder = os.path.dirname(savepath) 
        dstfile = savepath.replace(os.path.dirname(savepath)+"/","")
        
        tag = eyeD3.Tag()
        
        if os.path.isfile(srcfilepath):
            if os.path.splitext(srcfilepath)[1] == ".mp3":
                # Extract picture
                try:
                    tag.link(srcfilepath)
                    for image in tag.getImages():
                        image.writeFile(dstfolder, dstfile)
                        return savepath
                except:
                    print "Unable to extract image for: " + srcfilepath
                    traceback.print_exc()
        return ""


```

for the eyeD3, I will see that later, thanks!
for the escape char, I prefer to change the bash script  with :
```
cover="$(conkyRhythmbox --datatype=CA)"
 #remove \ characters from conkyRhythmbox output
cover=${cover//\\/}
``` and it works fine.

I put all the files needed to run this conky in the attachment if someone is interested 
And a video is available [here]("http://www.youtube.com/watch?v=llIGQcRUc_M"). Unfortunately, I didn't success to capture the sound !
And as you can see on the video, this conky looks better on a dark background.

---

### Post by kaivalagi on 2010-08-30
Very nice indeed, great example of proper conky work!

I hope you're going to post it into the conkyrc thread, would be a shame not to show it off!

I may well hack about with it for MPD :)

---

### Post by wlourf on 2010-08-31
Done, I posted another version in the conky [thread]("http://ubuntuforums.org/showthread.php?p=9790544#post9790544"), more simple whitout the countdown effect (sorry for the  --secondsoutput !) but more easy to configure, at least the colors (with an optional gradient):
```
--call the widgets 
--or use full path if you don't call the conkyrc from it's own directory
dofile ("./rings.lua")
dofile ("./text.lua")

function conky_main()
    --set the colors here
    --foreground
    fg_col1=0x97EF93
    fg_col2=0xF61330
    --background
    bg_col1=0xC9C6C6

    --call the functions into the widgets
    conky_main_rings()
    conky_draw_text()
end

```
and thanks again for your help!

---

### Post by kaivalagi on 2010-09-02
No worries, glad to be of service :)

---

### Post by Covi on 2010-10-07
Using Perl and urldecode, sed, and a copy in /tmp/ dir instead of call to CoverArt directly,... works for me ^^!:

```
# 1. Set cover from conkyRhythmbox -d CA. Get realpath:
COVER="`conkyRhythmbox -d CA | perl -MURI::Escape -lne 'print uri_unescape($_)' 
| sed 's/\\\//;q'`"
if [ '' != "$COVER" ]; then 
	rm -f $TMPCOVER
	ln -s "$COVER" $TMPCOVER
	exit
fi
```

I've modified too the original script to get the FilePath of file (-d FP), and try to get a cover from album directory **if CoverArt returns an empty value**.
Function to get album dir and clean the path: ("file://" can be removed from the original script).
```
coverFromFilePath() {
	# with sed for (file://) <sed 's/file:\/\///;q'> instead of <cut -c 8->.
	FILEC="`conkyRhythmbox -d FP | cut -c 8- | sed 's/\(.*\)\/.*./\1\/'$1'.jpg/;q' 
| perl -MURI::Escape -lne 'print uri_unescape($_)'`"
}
```

Now, we can use an array with usual names for cover [cover, front, album...] and a loop to search images:
```

# COVERNAMES=(front cover album)
# 2. Set cover from conkyRhythmbox -d FP:
for i in "${COVERNAMES[@]}"; do 
	coverFromFilePath $i
	if [ -f "$FILEC" ]; then 
		COVER=$FILEC
	fi
done
```

---
Now, I don't have problems with any chars:
e.g.:```
ln -s /home/covi/Música/Música HDD USB/H/Horner, James/Avatar. Music from the Motion Picture
/Cover.jpg /tmp/cover
```

I hope this is useful and sorry for my poor English :(

---

### Post by kaivalagi on 2010-10-07
Thanks Covi, I haven't got time to look into it right now but that may well help me get a solution together in the script using regex etc so you can do away with all the shell scripting on top of python...

---

### Post by Covi on 2010-10-07
Of course, it's the best solution.
But some users as me (with Latin chars, spaces, etc, in music directory) may have problems once the CoverArt is obtained (if it is obtained... that's another matter).

I mean, the problem is not conkyRhythmbox python script, it's conky :( ...or, to be honest, my music library names :mrgreen:

---
I think the unique real solution is that Python script makes a useful copy of CoverArt in somewhere place. /tmp/cover maybe a good option :roll:

PS: The Rhythmbox cache covers, have the same problem with chars at time of use in Conky :(

---

### Post by kaivalagi on 2010-10-08
> **Covi said:**
> I think the unique real solution is that Python script makes a useful copy of CoverArt in somewhere place. /tmp/cover maybe a good option :roll:

You may well be right, I may try linking to the file with a common file name in /tmp as I do with my mpdcron based scripts ;)

---

### Post by Covi on 2010-10-11
This is another -not solid- solution that's works fine (atm) for me:
CoverArt plugin uses this format to store cover in ~/.cache/rhythmbox/
```
artist = artist.replace('/', '-')
album = album.replace('/', '-')
return art_folder + '/%s - %s.%s' % (artist, album, extension)
```
That is: *%at - %aa* for rhythmbox-client and *-d AR & -d AL*. So...
```
# 1. Trying native method: '%at - %aa' is the default format of plugin CoverArt:
COVERNATIVE="`rhythmbox-client --no-start --print-playing-format '%at - %aa'`"
COVERNAME="`conkyRhythmbox2 -d CA | sed 's/\(.*\)\/.*./\1\/'$COVERNATIVE'.jpg/;q'`"
# XXX If have cover, link to tmp/cover:
if [[ -f "${COVERNAME}" ]] ; then 
	rm -f $TMPCOVER
	ln -s "$COVERNAME" $TMPCOVER
	exit 1
fi
```Now we only need a loop for image extension.
...however, we still have the same problems as before if CA is empty.

I hope it helps.

---

### Post by majmcdonald on 2010-10-18
I had some problems getting the title of the internet radio song titles to work.  I noticed in the code that the title would only be set from the "stream-song-title" if the title was empty.  For the stations that I listen to, at least, it never was empty - the title would always contain the name of the station.  I made a small change to correct that:

```

# if no title and a stream song title then use that instead (internet radio)
if "rb:stream-song-title" in props:
    title = props["rb:stream-song-title"] + " (" + title + ")"

```

---

### Post by kaivalagi on 2010-10-20
> **majmcdonald said:**
> I had some problems getting the title of the internet radio song titles to work.  I noticed in the code that the title would only be set from the "stream-song-title" if the title was empty.  For the stations that I listen to, at least, it never was empty - the title would always contain the name of the station.  I made a small change to correct that:

```

# if no title and a stream song title then use that instead (internet radio)
if "rb:stream-song-title" in props:
    title = props["rb:stream-song-title"] + " (" + title + ")"

```

Working away from home on windows machines, when I get back I'll certainly look at integrating those changes, thanks!

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)
[*]Updated to provide a copy of coverart files in a custom path to avoid file naming issues. The file where coverart gets copied to when using the --datatype=CA option is determined by the -c/--coverartpath option, note that if this option is set to an empty string i.e. "" the original file path is provided for the coverart path. The default path is /tmp/cover.
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.13_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.13_source.changes)

The apt packages should be available soon

Cheers

**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by Pablo Pablovski on 2010-10-26
Hey kaivalagi,
ubuntu 10.10
rhythmbox 0.13.1
conkyrhythmbox 2.1.3

After updating conkyrhythmbox, I've started to have a problem - no song details (title, artist, album) are displayed in conky, nor is cover art displayed.

```
ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/home/pablo/.cache/rhythmbox/covers/Neutral%20Milk%20Hotel%20-%20On%20Avery%20Island.jpg'
```

I changed the -c option to point to the folder where the coverart is, but as you can see from the screenshot, it's still not working.

Any ideas / diagnostics?

TIA,
PP

EDIT: forgot to say, I've done the symbolic link thing described in your post above

---

### Post by Pablo Pablovski on 2010-10-26
And here's the relevant section of .conkyrc

```
${color}${if_running rhythmbox}${font Aller:size=11}${color #656565}Rhythmbox Is Now Playing:${execp rm "/home/pablo/.album"}${image /home/pablo/.album -p 0,865 -s 88x88}
${color #B0B0B0}${execp conkyRhythmbox -n --datatype=TI}${font Aller:size=10}
${color #656565}from ${color #B0B0B0}${execp conkyRhythmbox -n --datatype=AL}${color #656565}
by      ${color #B0B0B0}${execp conkyRhythmbox --datatype=AR}${color #656565}
${execibar 1 conkyRhythmbox -n --datatype=PP}
${exec cp "`conkyRhythmbox -n --datatype=CA | sed -e 's/%20/ /g;s/%21/ /g;s/%27/ /g;s/%28/ /g;s/%29/ /g;s/%5B/ /g;s/%5D/ /g;s/%26/ /g;s/\\\//g'`" /home/pablo/.album}${image /home/pablo/.album -p 0,865 -s 88x88}
${endif}

```

---

### Post by kaivalagi on 2010-10-26
> **Pablo Pablovski said:**
> I changed the -c option to point to the folder where the coverart is, but as you can see from the screenshot, it's still not working.

Any ideas / diagnostics?

Have a look at this post I made earlier for the same issues but in conkyBanshee, the player might be different but the way the scripts work is the same: post 86 onwards here: [http://ubuntuforums.org/showpost.php?p=10026243](http://ubuntuforums.org/showpost.php?p=10026243)

The -p option defines the image filepath of the file that will be copied to by the script, so you always have the same filepath to use for cover art images...remove the -p option changes and follow what is in the above post.

Hope that helps

---

### Post by Pablo Pablovski on 2010-10-27
Thanks, k. I'm still having the same problem. Here's the relevant section of my amended .conkyrc.

```

${color #B0B0B0}${execp conkyRhythmbox -n --datatype=TI}${font Aller:size=10}${image /tmp/cover -p 0,865 -s 88x88}
${color #656565}from ${color #B0B0B0}${execp conkyRhythmbox -n --datatype=AL}${color #656565}
by      ${color #B0B0B0}${execp conkyRhythmbox -n --datatype=AR}${color #656565}
${execibar 1 conkyRhythmbox -n --datatype=PP}
${endif}

```

I've removed the amended -c setting, which *should* mean the script looks to /tmp/cover for artwork. However, the error message I get still indicate it's looking to the .cache folder in my home folder. And /tmp/cover doesn't exist, which makes it look like the script isn't "seeing" the new coverart path setting.

```
pablo@ubuntu-64:~$ conkyRhythmbox --datatype=PP
ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/home/pablo/.cache/rhythmbox/covers/10%2C000%20Maniacs%20-%20Blind%20Man%27s%20Zoo.jpg'
0
pablo@ubuntu-64:~$ 

```

(Does the "u" character just before the path look right to you?)

As you'll have seen from the screenshot above, the script no longer writes the artist, song, album and progress bar on screen - those areas are blank.

So, no coverart and no details... Any thoughts?

Appreciate your help..

PP

---

### Post by kaivalagi on 2010-10-27
> **Pablo Pablovski said:**
> So, no coverart and no details... Any thoughts?

You haven't got a call in there for --datatype=CA at all so no file will have been created...stick an "${exec conkyRhythmbox --datatype=CA}" anywhere below TEXT to make that happen...

Also can you run it in a terminal window first to makesure something comes back? e.g.
```
conkyRhythmbox --datatype=CA
```

---

### Post by Pablo Pablovski on 2010-10-27
Weirdly, I occasionally see the title, song and / or album details appear in the right place, but only as a new track starts playing and only for a few seconds (until the exact moment that the OSD-notify popup announcing the new song actually disappears, in fact). :confused:

```
ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/mnt/Music2/Music/Alabama%203/Power%20In%20The%20Blood/Folder.jpg'

```

Note that the error message is now referring to "Folder.jpg" in the (correct) original music folder as being the missing file (i.e. not /tmp/cover, and not the Rhythmbox cache folder, as if the coverart file location had been set to "".

---

### Post by Pablo Pablovski on 2010-10-27
> **kaivalagi said:**
> You haven't got a call in there for --datatype=CA at all so no file will have been created...stick an "${exec conkyRhythmbox --datatype=CA}" anywhere below TEXT to make that happen...

Also can you run it in a terminal window first to makesure something comes back? e.g.
```
conkyRhythmbox --datatype=CA
```

Sorry, our posts crossed. Here's the output.

```
pablo@ubuntu-64:~$ conkyRhythmbox --datatype=CA
ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/mnt/Music2/Music/Alabama%203/Power%20In%20The%20Blood/Folder.jpg'

pablo@ubuntu-64:~$ 

```

---

### Post by Pablo Pablovski on 2010-10-27
And here's the amended script segment (sorry for the schoolboy error!)

```
${color #B0B0B0}${exec conkyRhythmbox --datatype=CA}
${color #B0B0B0}${execp conkyRhythmbox -n --datatype=TI}${font Aller:size=10}${image /tmp/cover -p 0,865 -s 88x88}
${color #656565}from ${color #B0B0B0}${execp conkyRhythmbox -n --datatype=AL}${color #656565}
by      ${color #B0B0B0}${execp conkyRhythmbox -n --datatype=AR}${color #656565}
${execibar 1 conkyRhythmbox -n --datatype=PP}

```

---

### Post by kaivalagi on 2010-10-27
Well I thought I'd test the thing out myself (I don't use rhythmbox anymore) and I get nothing back for the cover art as for my version (0.13.1-4) there is no cover art info available to use...

I am in no position to test and debug the script because of it, last time I used it it was working but something has obviously changed with the app.

But....I think I see the problem, the path returned by RB is URL friendly (has %20's in it) so doesn't work when copying files etc...I've edited the .py file to fix that but can't test, would you mind trying the attached?

If you extract and copy the file to your /tmp folder and run the following you should be able to try the edited version in the way you have been running the current one:
```

cd /usr/share/conkyforecast/
sudo mv conkyRhythmbox.py conkyRhythmbox.py.backup
sudo cp /tmp/conkyRhythmbox.py conkyRhythmbox.py

```

Please run is using --verbose and let me know what happens...

Also, what version of RB are you running?

---

### Post by Pablo Pablovski on 2010-10-27
Wow, thanks for going to all that trouble - really appreciate it. I'll try the amended version and report back shortly.

I'm using Rhythmbox 0.13.1, which looks like a slightly older version than you have. Mine is the repo version.

---

### Post by kaivalagi on 2010-10-27
> **Pablo Pablovski said:**
> I'm using Rhythmbox 0.13.1, which looks like a slightly older version than you have. Mine is the repo version.

I'm on Arch not Ubuntu, further issues with testing as I can't use the exact same app as you...

---

### Post by Pablo Pablovski on 2010-10-27
Looks.... better. No error message.

```
pablo@ubuntu-64:~$ conkyRhythmbox -v --datatype=CA
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
/home/pablo/.cache/rhythmbox/covers/Mandalay%20-%20Instinct.jpg
pablo@ubuntu-64:~$ 

```

And I can now see track, album, artist and progress details in conky, though the coverart is missing - instead, the path to the cover file appears in its place. See bottom right of screenshot.

A file with that name (with the %20s) doesn't exist, but one with spaces in the file name does.

---

### Post by kaivalagi on 2010-10-27
> **Pablo Pablovski said:**
> And I can now see track, album, artist and progress details in conky, though the coverart is missing - instead, the path to the cover file appears in its place. See bottom right of screenshot.

Right, I think the solution I gave wasn't great and also the image tag needs editing too for position.

Can I make a suggestion that you use a template file (look at the example I pointed to before)...essentially you'll call the script like this:
```
${execp conkyRhythmbox --template=/path/to/template.file}
${execibar 1 conkyRhythmbox -n --datatype=PP}
```

and have a template like this:
```
${color #B0B0B0}[-n --datatype=TI]${font Aller:size=10}${image [--datatype=CA] -n -p 0,865 -s 88x88}
${color #656565}from ${color #B0B0B0}[-n --datatype=AL]${color #656565}
by      ${color #B0B0B0}[-n --datatype=AR]${color #656565}
```

I think you seeing that versus what you've got will hopefully make sense. Play around with the image placement and note I added the -n to the image variable..stops caching...(see here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html))

> **Pablo Pablovski said:**
> A file with that name (with the %20s) doesn't exist, but one with spaces in the file name does.
Try opening the cover art file in the browser and see what the URL looks like ;)

If that all works out *fingers crossed* let me know and I'll rollout the new script file

---

### Post by kaivalagi on 2010-10-27
> **majmcdonald said:**
> I had some problems getting the title of the internet radio song titles to work.  I noticed in the code that the title would only be set from the "stream-song-title" if the title was empty.  For the stations that I listen to, at least, it never was empty - the title would always contain the name of the station.  I made a small change to correct that:

```

# if no title and a stream song title then use that instead (internet radio)
if "rb:stream-song-title" in props:
    title = props["rb:stream-song-title"] + " (" + title + ")"

```

Missed the change off the last release by mistake, any new rollout will have it in ;)

---

### Post by kaivalagi on 2010-10-27
> **Pablo Pablovski said:**
> ```
pablo@ubuntu-64:~$ conkyRhythmbox -v --datatype=CA
...
/home/pablo/.cache/rhythmbox/covers/Mandalay%20-%20Instinct.jpg

```
...
A file with that name (with the %20s) doesn't exist, but one with spaces in the file name does.

Missed that, I don't get why you still have %20 in the path...I have put a replace function in to put a space in it's place

You should also see this in the output too:
```
INFO: Copying coverart from /home/pablo/.cache/rhythmbox/covers/Mandalay%20-%20Instinct.jpg to /tmp/cover
```

Can you please use the attached in case I forgot to save properly before zipping up previously...

---

### Post by Pablo Pablovski on 2010-10-27
> **kaivalagi said:**
> Right, I think the solution I gave wasn't great and also the image tag needs editing too for position.

Can I make a suggestion that you use a template file (look at the example I pointed to before)...essentially you'll call the script like this:
```
${execp conkyRhythmbox --template=/path/to/template.file}
${execibar 1 conkyRhythmbox -n --datatype=PP}
```

and have a template like this:
```
${color #B0B0B0}[-n --datatype=TI]${font Aller:size=10}${image [--datatype=CA] -n -p 0,865 -s 88x88}
${color #656565}from ${color #B0B0B0}[-n --datatype=AL]${color #656565}
by      ${color #B0B0B0}[-n --datatype=AR]${color #656565}
```

I think you seeing that versus what you've got will hopefully make sense. Play around with the image placement and note I added the -n to the image variable..stops caching...(see here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html))


Try opening the cover art file in the browser and see what the URL looks like ;)

If that all works out *fingers crossed* let me know and I'll rollout the new script file

Ok, I've set up the template file, stripped out the unnecessary lines from ./conkyrc and started it...

Now, on some albums, the title, album, artist and progress is correctly displayed, on others I only get a partial display that's missing either the artist or the album and sometimes has truncated info - see screenshot.

The path/to/coverart is now gone, but there's still no cover art. And I get the following errors in console:

```
ERROR: Unknown template option: -n 
ERROR: Unknown template option: -n 
ERROR: Unknown template option: -n 
Conky: Unable to load image '/home/pablo/.cache/rhythmbox/covers/Mandalay%20-%20Instinct.jpg'

```

When opened in the browser, the filename really is

```
file:///home/pablo/.cache/rhythmbox/covers/Mandalay%20-%20Instinct.jpg
```

But then, you knew that...

---

### Post by Pablo Pablovski on 2010-10-27
.conkyrc segment

```
${color}${if_running rhythmbox}${font Aller:size=11}${color #656565}Rhythmbox Is Now Playing:
${execp conkyRhythmbox --template=~/.conkyRhythmbox.template}
${execibar 1 conkyRhythmbox --datatype=PP}
${endif}
```

Template

```
${color #B0B0B0}[-n --datatype=TI]${font Aller:size=10}${image [--datatype=CA] -n -p 0,865 -s 88x88}
${color #656565}from ${color #B0B0B0}[-n --datatype=AL]${color #656565}
by      ${color #B0B0B0}[-n --datatype=AR]${color #656565}
```

---

### Post by kaivalagi on 2010-10-27
> **Pablo Pablovski said:**
> ```
ERROR: Unknown template option: -n 
ERROR: Unknown template option: -n 
ERROR: Unknown template option: -n 
Conky: Unable to load image '/home/pablo/.cache/rhythmbox/covers/Mandalay%20-%20Instinct.jpg'

```


I just don't get why there are still %20's in there, it should be "/tmp/cover" anyway...that'll be why you are not seeing any cover art!. I don't think the original .py file has been replaced. Try running the one attached in the command line like this:

```
python2 conkyRhythmbox.py --datatype=CA -v
```

Oh, the template only supports long options so the -n's inside []'s need to be --nounknownoutput instead, e.g.:

```
${color #B0B0B0}[--nounknownoutput --datatype=TI]${font Aller:size=10}${image [--datatype=CA] -n -p 0,865 -s 88x88}
${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]${color #656565}
by      ${color #B0B0B0}[--nounknownoutput --datatype=AR]${color #656565}
```

I wish I could test this on my setup, I get no coverart back and my RB covers folder is empty even if I see cover art in the player...grrrrh, it's as if the coverart plugin is knackered

edit: I'll be calling it a day shortly, so I'll probably pick up where we left off tomorrow evening, just post back what you find...

---

### Post by Pablo Pablovski on 2010-10-27
> **kaivalagi said:**
> 
You should also see this in the output too:
```
INFO: Copying coverart from /home/pablo/.cache/rhythmbox/covers/Mandalay%20-%20Instinct.jpg to /tmp/cover
```

Can you please use the attached in case I forgot to save properly before zipping up previously...

Don't see that comment in the output - do I need verbose mode for that?

And, I've applied that version.

```
pablo@ubuntu-64:~$ conkyRhythmbox --version
conkyRhythmbox v.2.08
pablo@ubuntu-64:~$ 

```

---

### Post by kaivalagi on 2010-10-27
> **Pablo Pablovski said:**
> Don't see that comment in the output - do I need verbose mode for that?

And, I've applied that version.

```
pablo@ubuntu-64:~$ conkyRhythmbox --version
conkyRhythmbox v.2.08
pablo@ubuntu-64:~$ 

```

You are running a really old version :confused:

What happened to copying the one I attached? The one available in the repos is 2.13 and the one attached is 2.14

Try the latest suggestion, calling the attached .py file directly using the python2 command

Logging off now, enough for tonight!

---

### Post by Pablo Pablovski on 2010-10-27
> **kaivalagi said:**
> You are running a really old version :confused:

What happened to copying the one I attached? The one available in the repos is 2.13 and the one attached is 2.14

Try the latest suggestion, calling the attached .py file directly using the python2 command

Logging off now, enough for tonight!

Oops! I hadn't copied the newer version to the /usr/share folder. I have now:

```
pablo@ubuntu-64:~$ conkyRhythmbox --version
conkyRhythmbox v.2.14
pablo@ubuntu-64:~$ 

```

And - it's working! I fixed the -n switches and it burst into life. All except the progressbar, but I'll have a play with that and report back.

Thank you SOO much for your help and your time - it's really good of you. I hope it's not some ungodly hour in your timezone...

Have a beer on me..

PP

---

### Post by kaivalagi on 2010-10-27
Thank **** for that :biggrin:

For what it's worth the script needing a little fixing anyway, I wouldn't have worked as was, you just gave me the excuse to spend time looking at it some :)

No probs anyway, I'm in the same timezone as you just further south, put my location into google maps and see...my avatar pic tells of a different place where I want to be this time of year.

Just finished my last bottle of Leffe :( I have spirits :)

Have fun and expect an update to be rolling out soon (if you get the updates :confused:)

---

### Post by Pablo Pablovski on 2010-10-27
> **kaivalagi said:**
> Thank **** for that :biggrin:

For what it's worth the script needing a little fixing anyway, I wouldn't have worked as was, you just gave me the excuse to spend time looking at it some :)

No probs anyway, I'm in the same timezone as you just further south, put my location into google maps and see...my avatar pic tells of a different place where I want to be this time of year.

Just finished my last bottle of Leffe :( I have spirits :)

Have fun and expect an update to be rolling out soon (if you get the updates :confused:)

Yes, indeed - thank **** for that. 

FWIW, it was instructive for me, too. I'm not a programmer (but you knew that, too :)), but I've gained some insight into Python, parameters and following instructions...

Norwich, eh? As in Nickers Off Ready When I Come Home? Well, put the spirits away and.. Unless, your partner is in the other timezone. In which case, back to the booze!

Anyway, I look forward to future updates. I've certainly been getting those - it was yesterdau's update to 2.13 that kicked all this off.

Thanks again - fingers crossed, it'll be plain sailing from here. If only I could fix the progressbar problem...:P

PP

---

### Post by Cavsfan on 2010-10-27
Hi! I was trying to get a Rhythmbox Conky going and just tried the default conkyrc that I initially installed:

```
# conky configuration
# edited by kaivalagi

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Terminus:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 5
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
[COLOR="Red"]border_margin 0[/COLOR]

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window        yes
own_window_transparent    yes
own_window_type        override
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
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

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}Rhythmbox${font}

${color4}Template Output:
${color1}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template}

${color4}Standard Output:
${voffset 5}${color4} Title:  ${color1}${font}${exec conkyRhythmbox --datatype=TI} 
${color4} Position:  ${color1}${font}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}
```
And I entered this is terminal **conky -c /usr/share/conkyrhythmbox/example/conkyrc**
Nothing showed up on the desktop (Rhythmbox was running) and this is what showed in terminal:
```
Conky: /usr/share/conkyrhythmbox/example/conkyrc: 47: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (1a000ad) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x5600001)
Conky: drawing to double buffer
```
I have no clue where to begin. :confused:
Thanks in advance!

---

### Post by kaivalagi on 2010-10-27
> **Pablo Pablovski said:**
> Norwich, eh? As in Nickers Off Ready When I Come Home? Well, put the spirits away and.. Unless, your partner is in the other timezone. In which case, back to the booze!

She's here, too much knickers off though, she's 4 months pregnant and can't drink :p

If it were the other place it would be 11am...and I would be sweating my bollocks off wearing a skirt :) See...an Englishman can have more in common with a Scotsman than you'd think ;)

Post away if you have questions, I'll answer when I can...today was a slack day so I could afford the time, most of the time it's not the case though.

Cheers

---

### Post by kaivalagi on 2010-10-27
> **Cavsfan said:**
> I have no clue where to begin. :confused:
Thanks in advance!

Even with that error it should display something

Can you try running this in the terminal (to print the song title)
```
conkyRhythmbox --datatype=TI
```

if that works then the script is fine and it's conky related, in which case I suggest visiting the conky pitstop site for lots of working examples. See the link in my sig

p.s. you do have rhythmbox running and playing something right?

I really must get away from the PC now, I work in computers and have been at this one since 8am! Enough is enough...

---

### Post by Cavsfan on 2010-10-27
OUtput of **conkyRhythmbox --datatype=TI**

```
ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/home/cavsfan/.cache/rhythmbox/covers/Aerosmith%20-%20Get%20Your%20Wings.jpg'
Unknown
cavsfan@cavsfan-MS-7529:~$ ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/home/cavsfan/.cache/rhythmbox/covers/Aerosmith%20-%20Get%20Your%20Wings.jpg'
ERROR:: command not found
cavsfan@cavsfan-MS-7529:~$ Unknown
No command 'Unknown' found, did you mean:
 Command 'unknown' from package 'fastlink' (universe)
Unknown: command not found

```Sorry, I know what you mean about working all day!

---

### Post by kaivalagi on 2010-10-27
> **Cavsfan said:**
> OUtput of **conkyRhythmbox --datatype=TI**
```
ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/home/cavsfan/.cache/rhythmbox/covers/Aerosmith%20-%20Get%20Your%20Wings.jpg'

```

The next post should get you on the road to it working...might be a little time before it's available, I posted the update a while back and launchpad is being slow tonight...

I really am off the PC now lol

---

### Post by kaivalagi on 2010-10-27
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated to provide internet station as well as title if present for streamed music
[*]Fixed cover art copying bug due to filename issues
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.14_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.14_source.changes)

The apt packages should be available soon

Cheers

---

### Post by Cavsfan on 2010-10-27
> **kaivalagi said:**
> **[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated to provide internet station as well as title if present for streamed music
[*]Fixed cover art copying bug due to filename issues
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.14_source.changes]("https://launchpad.net/%7Econkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.14_source.changes")

The apt packages should be available soon

Cheers

I had it running and got an update yesterday. Go on and get off this thing and have a life man! Enjoy! There is always tomorrow!
Thanks for your help!!! :)

---

### Post by Cavsfan on 2010-10-27
I just got the update 
```
cavsfan@cavsfan-MS-7529:~$ conkyRhythmbox --version
conkyRhythmbox v.2.14
cavsfan@cavsfan-MS-7529:~$ 
```

When I enter the original command I still get the same thing:
```
cavsfan@cavsfan-MS-7529:~$ conky -c /usr/share/conkyrhythmbox/example/conkyrc
Conky: /usr/share/conkyrhythmbox/example/conkyrc: 47: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (1a000ad) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x5800001)
Conky: drawing to double buffer
```

But, when I enter **conkyRhythmbox --datatype=TI** it just gives me the song name.
I have a conky on the right side of the screen displaying cpu, gpu, network, weather, etc. but I haven't seen rhythmbox yet.
I am new to this conky thing and I thought I could have them both going at the same time.
Have a good night! I am off this thing for the night myself! :P

---

### Post by Pablo Pablovski on 2010-10-27
> **kaivalagi said:**
> She's here, too much knickers off though, she's 4 months pregnant and can't drink :p

If it were the other place it would be 11am...and I would be sweating my bollocks off wearing a skirt :) See...an Englishman can have more in common with a Scotsman than you'd think ;)

Post away if you have questions, I'll answer when I can...today was a slack day so I could afford the time, most of the time it's not the case though.

Cheers

Lol, sounds like you haven't spent *enough* time programming! Good luck with the forthcoming happy event. And I don't mean you wearing a kilt!

Quick update on the progressbar thing - it works ok if I move the conky execibar command to before the "execp..template=..." command, but not after. Not a worry, it's fine like that, but it might be indicative of a bug in the script. 

The other thing I've noticed is that the conky output sometimes goes weird on the last line (artist) - the text is occasionally replaced by a single digit in a random colour (purple, cyan, yellow). No idea what that's about, no pattern detected yet.

And, and, the artist, song, album and progressbar plus coverart are not displayed if there's an "&" in the artist name. 

If I change the artist name (in RB) to x AND y, and restart the track, suddently the conky output is ok again. Happened with "Pearl Jam & Neil Young" and "The Mamas & The Papas". It seems to be ok if there's an "&" in the song title, but also fails if there's one in the album title. Escape characters, no doubt.

I'm about to turn in myself, but I'll have a look at it tomorrow.

PP

---

### Post by Pablo Pablovski on 2010-10-27
.conkyrc excerpt:

```
${color}${if_running rhythmbox}${font Aller:size=11}${color #656565}Rhythmbox Is Now Playing:
${color #656565}${execibar 1 conkyRhythmbox --datatype=PP}
${execp conkyRhythmbox --template=~/.conkyRhythmbox.template}
${color #656565}${execibar 1 conkyRhythmbox --datatype=PP}
${endif}
```

Template:
```
${color #B0B0B0}[--nounknownoutput --datatype=TI]${font Aller:size=10}${image [--datatype=CA] -n -p 0,865 -s 88x88}
${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]
${color #656565}by      ${color #B0B0B0}[--nounknownoutput --datatype=AR]
```

Console output when playing artist or song with "&" in title:

```
ERROR: Issue calling the dbus service:[Errno 2] No such file or directory: u'/home/pablo/.cache/rhythmbox/covers/Alison Krauss %26 Union Station - New Favorite.jpg'

```

Screenshots of output without and with an "&" in artist name att.

---

### Post by kaivalagi on 2010-10-27
I need to find a way of escaping out all web friendly character codes...

I did it for %20 -> space, %26 needs to be an & and there will be shed loads more...must be a better way of doing it

...for another day

if you want to fix it for now find the line in the .py which has this:

```
coverart = coverart.replace("file://","").replace("%20"," ")
```

and add another replace for the above so that bit becomes:

```
coverart = coverart.replace("file://","").replace("%20"," ").replace("%26","&")
```

This might not be exact so think it through a little

Cheers

edit: long term fix attached which should cope with all escaped characters, I'll release it after you confirm it works :)
now using:
```
coverart = urllib.unquote(coverart).replace("file://",""))
```

---

### Post by XcamiloX on 2010-10-28
hola, el Script me generaba un error con las tildes (soy colombiano), ejemplo: /home/user/M%C3%BAsica/ (música) y lo solucione, (no se mucho de python) pero se corrigió el error, espero el aporte sirva :)

**ENGLISH**

hi, the  script I generated an error with the accents (I am Colombian), example:  / home/user/M% C3% BAsica/ (Música) and solve it (not much of  python), but corrected the error, hope serve as input:)

```
#encode characters
aa = "á"
ee = "é"
ii = "í"
oo = "ó"
uu = "ú"
aa = aa.decode("utf-8")
ee = ee.decode("utf-8")
ii = ii.decode("utf-8")
oo = oo.decode("utf-8")
uu = uu.decode("utf-8")
```and

```
#we replace the characters
coverart = coverart.replace("file://","").replace("%20"," ").replace("%25", "%").replace("%26","&").replace("%C3%A1", aa).replace("%C3%A9", ee).replace("%C3%AD", ii).replace("%C3%B3", oo).replace("%C3%BA", uu)
```

---

### Post by kaivalagi on 2010-10-28
> **XcamiloX said:**
> hi, the  script I generated an error with the accents (I am Colombian), example:  / home/user/M% C3% BAsica/ (Música) and solve it (not much of  python), but corrected the error, hope serve as input:)

Hi/Hola,

Firstly thanks for the input I hadn't though of accented chars however can you try out the latest tarball I posted as this doesn't use normal replace but unquotes the URL friendly chars instead.

I just checked in the debugger and "urllib.unquote("%C3%A1")" for example does output to "á" but this needs testing properly. I can't as 1) I have no music titles with accents and 2) rhythmbox in Arch isn't behaving itself at the moment

Let me know your findings!

---

### Post by XcamiloX on 2010-10-28
hi, I tried the last script (the one above) and did not work, continue the error, which now runs modified.

---

### Post by Cavsfan on 2010-10-28
I was getting this:
```
**conky -c /usr/share/conkyrhythmbox/example/conkyrc**
Conky: /usr/share/conkyrhythmbox/example/conkyrc: 47: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (1c000ad) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x5a00001)
Conky: drawing to double buffer
```So, I changed ```
border_margin 0 to border_inner_margin 0
```and ```
use_spacer true to use_spacer left
```And it still doesn't show on my desktop with Rhythmbox playing, but it doesn't get an error.
```
**conky -c /usr/share/conkyrhythmbox/example/conkyrc**
Conky: desktop window (1c000ad) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x6000001)
Conky: drawing to double buffer
```It could be that I just can't do what I am trying to do. I already have a conky on the right side of my desktop.
I thought I could have this other one display on the left side when Rhythmbox was playing.
Is this not possible?

---

### Post by kaivalagi on 2010-10-28
> **XcamiloX said:**
> hi, I tried the last script (the one above) and did not work, continue the error, which now runs modified.

mmmm, I see it working when debugging, i.e. the conversion from html quoted char to real deal...

Can you provide the error you are seeing for the latest script, it should help identify the issue, likely a unicode issue if anything...

---

### Post by kaivalagi on 2010-10-28
> **Cavsfan said:**
> It could be that I just can't do what I am trying to do. I already have a conky on the right side of my desktop.
I thought I could have this other one display on the left side when Rhythmbox was playing.
Is this not possible?

The example is just that, it is isn't working because of conky version differences I'm sure people can adapt as you have.


You can run more than one conky at the same time, just use "conky -c /conkyrcfilepath" more than once, just make sure the positioning doesn't overlap...

---

### Post by Pablo Pablovski on 2010-10-28
> **kaivalagi said:**
> I need to find a way of escaping out all web friendly character codes...

I did it for %20 -> space, %26 needs to be an & and there will be shed loads more...must be a better way of doing it

...for another day

if you want to fix it for now find the line in the .py which has this:

```
coverart = coverart.replace("file://","").replace("%20"," ")
```

and add another replace for the above so that bit becomes:

```
coverart = coverart.replace("file://","").replace("%20"," ").replace("%26","&")
```

This might not be exact so think it through a little

Cheers

edit: long term fix attached which should cope with all escaped characters, I'll release it after you confirm it works :)
now using:
```
coverart = urllib.unquote(coverart).replace("file://",""))
```

You, Sir, are a stud and a superstar, and I hope you have beers to hand cos I'm raising one in your name now. Top class commitment and support.

Screenies to show that "&"s in song title, artist and album don't lead to loss of displayed info. Though... I did note that the presence of a "#" in the title does cause problems....

Slainte!

PP

---

### Post by kaivalagi on 2010-10-28
> **Pablo Pablovski said:**
> Screenies to show that "&"s in song title, artist and album don't lead to loss of displayed info. Though... I did note that the presence of a "#" in the title does cause problems....


Great news, now just to get over the accented text before I release, I don't suppose you have any media like XcamiloX mentioned do you? I am not sure he will get back soon or not with more details and I would really like to know how the script fares...

edit: nevermind, I edited the code to test the issue and as far as I am concerned it works with accents too:
```
                            coverart = ""
                            if "rb:coverArt-uri" in props:
                                coverart = props["rb:coverArt-uri"]
                                if coverart.find("http://") != -1:
                                    coverart = ""
                                else:
                                    coverart = urllib.unquote(coverart).replace("file://","")
                            
                            [COLOR="Red"]coverart = "file:///tmp/M%C3%BAsica.jpg"
                            coverart = urllib.unquote(coverart).replace("file://","")[/COLOR]
                            
                            if coverart != "" and self.options.coverartpath != "":
                                self.logInfo("Copying coverart from %s to %s"%(coverart, self.options.coverartpath))
                                shutil.copy(coverart, self.options.coverartpath)
                                coverart = self.options.coverartpath
```

I put the 2 lines in red in place, copied and renamed an image file I had so there was something to copy (/tmp/Música.jpg) and bingo, file gets copied to /tmp/cover no probs...


> **XcamiloX said:**
> hi, I tried the last script (the one above) and did not work, continue the error, which now runs modified.
You must have not copied the file into the right place and used the older version or something...I'm going with the update I have now...

---

### Post by kaivalagi on 2010-10-28
> **Pablo Pablovski said:**
> I did note that the presence of a "#" in the title does cause problems....

Bol%#cks, I should read more carefully, I'll see if I can fix that too, #'s are control chars for html character codes, should be fun...can you give me an example?

Good job I hadn't rolled out the script yet to Ubuntu..Arch is already there but that's easy to fix

edit: works for cover art file names and titles, definitely need that example!
edit2: I'll rolling it out...more to want than wonder on

---

### Post by Pablo Pablovski on 2010-10-28
> **kaivalagi said:**
> Bol%#cks, I should read more carefully, I'll see if I can fix that too, #'s are control chars for html character codes, should be fun...can you give me an example?

Good job I hadn't rolled out the script yet to Ubuntu..Arch is already there but that's easy to fix

edit: works for cover art file names and titles, definitely need that example!
edit2: I'll rolling it out...more to want than wonder on

Hmmm. I just got the repo update, and I'm getting problems with some albums.

```
pablo@ubuntu-64:~$ conkyRhythmbox --version
conkyRhythmbox v.2.14
pablo@ubuntu-64:~$ 

``` 

The version you posted here this morning was 2.15, right? I'll copy the newer .py and try again.

An exmaple of a song where it failed to display anything was "Radio #1" by Air.

BRB..

---

### Post by Cavsfan on 2010-10-28
> **kaivalagi said:**
> The example is just that, it is isn't working because of conky version differences I'm sure people can adapt as you have.


You can run more than one conky at the same time, just use "conky -c /conkyrcfilepath" more than once, just make sure the positioning doesn't overlap...

That was exactly the problem! The first conky I was just running at startup with "conky" and not specifying the location.
So I have added the location to the startup command, but the Rhythmbox conky overlaps the other one on the right side.
I got it moved to the left bottom.
And could I add this as a startup too and will it come up when I start Rhythmbox or not?
Thanks! Getting a little closer!

---

### Post by Pablo Pablovski on 2010-10-28
Right, here goes.

```
pablo@ubuntu-64:~$ conkyRhythmbox --version
conkyRhythmbox v.2.15
pablo@ubuntu-64:~$ 

```

"Radio #1" appears in conky as simply "Radio" and fails to display coverart, even though:

```
pablo@ubuntu-64:~$ conkyRhythmbox --datatype=TI
Radio #1
pablo@ubuntu-64:~$ 

```

/tmp/cover is the correct image while "Radio #1" is playing. Other songs from the same album are fine.

---

### Post by kaivalagi on 2010-10-28
Gotta love launchpad, fairly quick last night, tonight though: [https://launchpad.net/~conkyhardcore/+archive/ppa/+build/2021546](https://launchpad.net/~conkyhardcore/+archive/ppa/+build/2021546)
"Start in 9 hours" ouch!

---

### Post by Pablo Pablovski on 2010-10-28
> **kaivalagi said:**
> ... I don't suppose you have any media like XcamiloX mentioned do you? I am not sure he will get back soon or not with more details and I would really like to know how the script fares...


I tested it with a song called "La Vigüela", and it's fine - coverart, title etc. all displayed correctly. It also worked with a song called Renée. 

Can't find any other accented tracks / artists, but I'll come back if anything fails.

---

### Post by kaivalagi on 2010-10-28
> **Pablo Pablovski said:**
> Right, here goes.

```
pablo@ubuntu-64:~$ conkyRhythmbox --version
conkyRhythmbox v.2.15
pablo@ubuntu-64:~$ 

```

"Radio #1" appears in conky as simply "Radio" and fails to display coverart, even though:

```
pablo@ubuntu-64:~$ conkyRhythmbox --datatype=TI
Radio #1
pablo@ubuntu-64:~$ 

```

/tmp/cover is the correct image while "Radio #1" is playing. Other songs from the same album are fine.

mmmmm, if it's output by the script and can also copy cover art files with a # in the name I'd say it's conky handling #'s as comments (can't get round that) but I think the cover art just isn't found...can you run this in the terminal so we see the original path in the copying file log info:
```
conkyRhythmbox --datatype=CA -v
```

---

### Post by Pablo Pablovski on 2010-10-28
```
pablo@ubuntu-64:~$ conkyRhythmbox --datatype=CA -v
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Copying coverart from /home/pablo/.cache/rhythmbox/covers/Air - 10,000 Hz Legend.jpg to /tmp/cover
INFO: Preparing output for datatype:CA
/tmp/cover
pablo@ubuntu-64:~$ 

```

---

### Post by kaivalagi on 2010-10-28
Does the file open if you run:
```
eog "/home/pablo/.cache/rhythmbox/covers/Air - 10,000 Hz Legend.jpg"
```

---

### Post by Pablo Pablovski on 2010-10-28
> **kaivalagi said:**
> Does the file open if you run:
```
eog "/home/pablo/.cache/rhythmbox/covers/Air - 10,000 Hz Legend.jpg"
```

Yep.

---

### Post by kaivalagi on 2010-10-28
Looks like it should have been copied fine and therefore display....

Wait a minute!!! Is the $image tag on the same line as the title line and therefore "commented" out by the title name i.e. this won't be processed:
```
#1 ${image /tmp/cover....
```
it would have started life out as:
```
...[--datatype=TI] ${image [--datatype=CA....
```

edit: just checked back in the posts, move the $image on to the last line in the template away from everything else!
e.g.
```
${color #B0B0B0}[--nounknownoutput --datatype=TI]${font Aller:size=10}
${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]${color #656565}
by      ${color #B0B0B0}[--nounknownoutput --datatype=AR]${color #656565}
${image [--datatype=CA] -n -p 0,865 -s 88x88}
```

Maybe a bit premature but am I good or am I goooood \\:D/

---

### Post by Pablo Pablovski on 2010-10-28
> **kaivalagi said:**
> Wait a minute!!! Is the $image tag on the same line as the title line and therefore "commented" out by the title name i.e. this won't be processed:

Genius! The image tag was indeed on the same line as the title line in the template... so, a little moving around and Shazzzaaam! Coverart displayed!

```
{color #B0B0B0}[--nounknownoutput --datatype=TI]${font Aller:size=10}
${image [--datatype=CA] -n -p 0,865 -s 88x88}${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]
${color #656565}by      ${color #B0B0B0}[--nounknownoutput --datatype=AR]
```

Ok, you can definitely take the rest of the evening off. :P

---

### Post by Cavsfan on 2010-10-28
I guess I got all I really needed as you can see.


[[IMG]http://ompldr.org/tNXlpZQ[/IMG]]("http://ompldr.org/vNXlpZQ")

But, I was wondering if you are going to do the amd64 version too?
It looked like you only had the i386 version going out tonight.
Here is what I have and I was curious as to how **Pablo** had 2.15.
```
cavsfan@cavsfan-MS-7529:~$ conkyRhythmbox --version
conkyRhythmbox v.2.14
cavsfan@cavsfan-MS-7529:~$ 

```
Anyway thanks dude! You are the man! Have a great night! :P

---

### Post by Pablo Pablovski on 2010-10-28
> **Cavsfan said:**
> I guess I got all I really needed as you can see.


[[IMG]http://ompldr.org/tNXlpZQ[/IMG]]("http://ompldr.org/vNXlpZQ")

But, I was wondering if you are going to do the amd64 version too?
It looked like you only had the i386 version going out tonight.
Here is what I have and I was curious as to how **Pablo** had 2.15.
```
cavsfan@cavsfan-MS-7529:~$ conkyRhythmbox --version
conkyRhythmbox v.2.14
cavsfan@cavsfan-MS-7529:~$ 

```
Anyway thanks dude! You are the man! Have a great night! :P

I've attached v.2.15 of kaivalagi's conkyRythmbox .py script. Extract the file to /tmp, then run the following commands.

```
cd /usr/share/conkyrhythmbox
sudo mv conkyRhythmbox.py conkyRhythmbox.py.backup
sudo cp /tmp/conkyRhythmbox.py conkyRhythmbox.py
```

Voila. v.2.15. Or, wait till it gets uploaded to the repo.

---

### Post by kaivalagi on 2010-10-28
> **Cavsfan said:**
> But, I was wondering if you are going to do the amd64 version too?

Glad to see you got it working, there is only one version for all platforms, that's the beauty of python, it compiles at runtime ;) Don't pay attention to the 1386 nonsense in launchpad, it's irrelevant...I run 64 bit Arch to run and develop the stuff for other Arch users and you Ubuntu lot :p

Like PP posted above just use the source file for now or wait until launchpad decides to build the packages for you...it's currently waiting in a queue on the server with 6 hours to go and that's before I can copy across from hardy to other versions which wont happen until tomorrow (about 10-11 hours away minimum)...

---

### Post by kaivalagi on 2010-10-29
**[COLOR=DarkOrange][SIZE=4]UPDATE[/SIZE][/COLOR]**

Changes as follows:
[LIST]
[*]Fixed cover art copying again, hopefully for the last time :) It now uses urllib.unquote to fix up all file names for copying including accented names
[/LIST]
 
Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.15_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.15_source.changes)

The apt packages should be available shortly

Cheers

---

### Post by Cavsfan on 2010-10-29
> **kaivalagi said:**
> Glad to see you got it working, there is only one version for all platforms, that's the beauty of python, it compiles at runtime ;) Don't pay attention to the 1386 nonsense in launchpad, it's irrelevant...I run 64 bit Arch to run and develop the stuff for other Arch users and you Ubuntu lot :p

Like PP posted above just use the source file for now or wait until launchpad decides to build the packages for you...it's currently waiting in a queue on the server with 6 hours to go and that's before I can copy across from hardy to other versions which wont happen until tomorrow (about 10-11 hours away minimum)...

Thanks! I got it! Working great!!! :)

---

### Post by Cavsfan on 2010-10-29
OK, now I am trying to add the cover art to it and the pictures are getting copied to directory and they look great. 
/home/cavsfan/.cache/rhythmbox/covers/
But, I am having some trouble with where to put what :confused: 

I found out I was supposed to move my cronky and template as they got written over with the recent update, so at least I am learning.

I have basically taken your example and am trying to add the album art to the bottom line.
I think I have entered the line to display the art, but it is not showing up.
Here is my cronky:
```
# conky configuration
# edited by kaivalagi

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Terminus:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 5
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window        yes
own_window_transparent    yes
own_window_type        override
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer left

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

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}Rhythmbox${font}

${color4}Template Output:
${color1}${execp conkyRhythmbox --template=/home/cavsfan/.conkyrhythmbox/conkyRhythmbox.template}
${execibar 1 conkyRhythmbox --datatype=PP}
${color4}Standard Output:
${voffset 5}${color4} Title:  ${color1}${font}${exec conkyRhythmbox --datatype=TI} 
${color4} Position:  ${color1}${font}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}
```And here is my template:
```
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]

{color #B0B0B0}[--nounknownoutput --datatype=TI]${font Aller:size=10}
${image [--datatype=CA] -n -p 0,865 -s 88x88}${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]
${color #656565}by      ${color #B0B0B0}[--nounknownoutput --datatype=AR]
```Thanks in advance!!! :)

---

### Post by Cavsfan on 2010-10-29
Here is what my screen looks like with the above files:

[[IMG]http://ompldr.org/tNXl5Mw[/IMG]]("http://ompldr.org/vNXl5Mw")

The cover art displays in Rythmbox, just not in the conky. I am sure this is simple for you to figure out.
Thanks! 
Cheers! :)

---

### Post by kaivalagi on 2010-10-29
"0,865" seems a bit extreme, this setting for $image is the position from the corner of the conky window and not the screen...I think that's your problem...

Hope that helps

---

### Post by Pablo Pablovski on 2010-10-30
> **kaivalagi said:**
> "0,865" seems a bit extreme, this setting for $image is the position from the corner of the conky window and not the screen...I think that's your problem...

Hope that helps

I think you're right in that the positioning of the image is the problem, assuming Cavsfan wants the image to appear on the LHS of the screen. 

I suspect the 0,865 setting was copied from my template file, and I have conky displayed on the RHS of the screen, with the image near the bottom of the conky window. "0,865" tells conky to place the image 0 pixels *from the LHS of the conky window* and 865 pixels *from the top of the conky window*.

So, I'd try something like 0,0 as a start - that'll put the image 0 pixels from the left hand edge of conky and 0 pixels from the top, then use trial and error to line it up as desired.

You'll also need to make sure the conky window is big enough to accommodate the image, per your placement and image size (currently 88*88 pixels):

```
# Minimum size of text area
minimum_size 300 5
maximum_width 300

```

And

```
${image [--datatype=CA] -n -p 0,865 -s 88x88}${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]

```

---

### Post by Cavsfan on 2010-10-30
I don't have the slightest clue as to what I am doing...
Yes I am trying to put it at the bottom left hand side of the screen.

My conkyrc:
```
# Minimum size of text area
minimum_size 500 5
maximum_width 800
```at the bottom of conkyrc:
```
TEXT
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}Rhythmbox${font}
${color4}Template Output:
${color1}${execp conkyRhythmbox --template=/home/cavsfan/.conkyrhythmbox/conkyRhythmbox.template}
${execibar 1 conkyRhythmbox --datatype=PP}
${color4}Standard Output:
${voffset 5}${color4} Title:  ${color1}${font}${exec conkyRhythmbox --datatype=TI} 
${color4} Position:  ${color1}${font}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}
```My entire conkyRhythmbox.template:
```

${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
${image [--datatype=CA] -n -p 0,500 -s 250x250}${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]
```I still cannot see any album art and it is displaying in Rhythmbox perfectly.
Here is another picture with Rhythmbox showing playing Filter - Take a Picture.
So, you can see what I have at the bottom left and you can see what should be showing there.
I am completely lost as what to enter into these values and I have played with them and nothing happens.

I have a "/" displayed above the bar when the song is playing and when it's paused a "c" displays. :confused:

[[IMG]http://ompldr.org/tNXpiYQ[/IMG]]("http://ompldr.org/vNXpiYQ")

I should probably just give up on the album art, but when I noticed Pablo Pablovski got it working I thought I could too. ](*,)

---

### Post by Pablo Pablovski on 2010-10-30
Ok, so your conky window is 500 px "long" and 800 px "wide". The other thing we need to confirm is the alignment in conkyrc - I'm guessing "bottom_left".

```
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right
```

So, if you want to place the image at the top left of the conky window, you'd use an image command in the template:

```
${image [--datatype=CA] -n -p 0,0 -s 250x250}${color #656565}from ${color #B0B0B0}[--nounknownoutput --datatype=AL]
```

Note the "0,0" - that's 0 pixels from the left of the conky window and 0 down from the top. You've currently got that set as 0,500, which means the image will be placed 0 px from the left of the window (which is ok), and 500px from the top - which means the image is effectively being placed after (or beyond) the bottom of the conky window. So, you don't see it - think of it as being like text in a browser window - if it's beyond the end of the diplayable area, you can't see it (without using scroll bars, and your conky window doesn't have those).

You might also find that a 250*250px image is too big for the window - it's half the horizontal size of the window - 128*128 might be better, but you could mess about with the placement and size of the image and of the conky window till you find what you're looking for.

Oh yeah, I almost forgot. Be aware that the image will be put wherever you tell conky to put it - even if that's on top of the other text that conky's displaying, so you'll probably need to do a bit of experimenting with layout once you get the image displayed to avoid the image wiping out your text. I use a few spacer lines in my conkyrc (att) but you could use the voffset varable to do the same thing.

---

### Post by akhenaton on 2010-11-10
Hi all,

kaivalagi this script print this in python >= 2.7:

conkyRhythmbox.py", line 45
    self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=TI]. The following are possible options within each item: --datatype,--ratingchar. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")

I think that optparse module is deprecated, more info in:
[http://docs.python.org/library/optparse.html](http://docs.python.org/library/optparse.html)

I don't a python programmer.

Thanks for the great script !!!
[LEFT]
[/LEFT]

---

### Post by Cavsfan on 2010-11-11
Pablo, suddenly I started seeing the image in the window!!! But, it was just about 1/4 of the actual 
size of the picture. I looked in tmp and the pic was 432x432! I am just happy to see any picture.

It seems almost every picture is a different size though. Not sure what can be done about that.
Thanks! :)

---

### Post by kaivalagi on 2010-11-13
> **akhenaton said:**
> Hi all,

kaivalagi this script print this in python >= 2.7:

conkyRhythmbox.py", line 45
    self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=TI]. The following are possible options within each item: --datatype,--ratingchar. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")

I think that optparse module is deprecated, more info in:
[http://docs.python.org/library/optparse.html](http://docs.python.org/library/optparse.html)

I don't a python programmer.

Thanks for the great script !!!
[LEFT]
[/LEFT]

Thanks for the heads up...not sure why though but I have no issues and I am running 2.7...

If I run this it's fine:
```
]$ python2.7 /usr/share/conkyforecast/conkyForecast.py --datatype=MP
First Quarter

```

I know from version 3 there will be lots of issues...

---

### Post by kaivalagi on 2010-11-21
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to dynamically call the available python exec as /usr/bin/python is linked to Python 3 (Arch) or will be at some point (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.16_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.16_source.changes)

The apt packages should be available soon

---

### Post by Pablo Pablovski on 2010-11-21
> **Cavsfan said:**
> Pablo, suddenly I started seeing the image in the window!!! But, it was just about 1/4 of the actual 
size of the picture. I looked in tmp and the pic was 432x432! I am just happy to see any picture.

It seems almost every picture is a different size though. Not sure what can be done about that.
Thanks! :)

Cavsfan, the "250x250" bit in the "image" variable specifies the size that the image will be **resized to**. For me, at least, it doesn't matter what size the original image is, it gets resized according to the setting in the image variable.

So, if you're misisng bits of a large image, try smaller resize values - I find 80x80 works well on my 1680x1050 screen. If yours is smaller than that, try 64x64 or similar. If you get that, and the placement, right, you'll see the whole image, eg:

```
${image [--datatype=CA] -n -p 0,0 -s 64x64}]
```

---

### Post by Cavsfan on 2010-11-21
> **Pablo Pablovski said:**
> Cavsfan, the "250x250" bit in the "image" variable specifies the size that the image will be **resized to**. For me, at least, it doesn't matter what size the original image is, it gets resized according to the setting in the image variable.

So, if you're misisng bits of a large image, try smaller resize values - I find 80x80 works well on my 1680x1050 screen. If yours is smaller than that, try 64x64 or similar. If you get that, and the placement, right, you'll see the whole image, eg:

```
${image [--datatype=CA] -n -p 0,0 -s 64x64}]
```

Thanks! I have a 1920x1200 screen and put it to 80x80 and it seemed like it worked for one song, but 
another with another song the pic. was less than 1/4 of the actual size of the pic.

And the "-p 0,0" seems to have no effect, I have tried 0,500, 20,0 and 0,0 and the position does not change.
I change it and save conkyRhyhmbox.template and then save the .conkyrc file and it disappears and then reappears.
```
${image [--datatype=CA] -n -p 0,0 -s 80x80}
```

---

### Post by Pablo Pablovski on 2010-11-22
Cavsfan,
Could you post a screenshot and your .conkyrc plus the template file? The -p position switch works for me, as does the the -s scale switch, so there might be something else in the config file that's stopping it working.

Also, what version of conky are you using?

```
conky --version
```

My conky window is 280px wide and is placed on the RHS of the screen. I place the CA image at 0,865 - so it's on the LH edge (0) and 865 px down from the top of the conky window. The CA image is always the same 80x80px.

---

### Post by Cavsfan on 2010-11-24
> **Pablo Pablovski said:**
> Cavsfan,
Could you post a screenshot and your .conkyrc plus the template file? The -p position switch works for me, as does the the -s scale switch, so there might be something else in the config file that's stopping it working.

Also, what version of conky are you using?

```
conky --version
```My conky window is 280px wide and is placed on the RHS of the screen. I place the CA image at 0,865 - so it's on the LH edge (0) and 865 px down from the top of the conky window. The CA image is always the same 80x80px.

I have 2 conkys - one on the right side of the screen displaying weather and cpu temps etc. And it takes the whole right side of my screen.
So, I put the Rhythmbox conky on the left bottom of the screen.

My .conkyrc (for Rhythmbox)
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,sticky,below,skip_pager,skip_taskbar
own_window_transparent yes
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 5.0

# Minimum size of text area
# minimum_size 10 2

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 0
border_outer_margin 0

# border width
border_width 1

# Max width
maximum_width 280

# Default colors and also border colors, 
default_color B0B0B0
default_shade_color B0B0B0
default_outline_color B0B0B0

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 1
gap_y 0

#I Don't cache images
imlib_cache_size 0

override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8

# stuff after 'TEXT' will be formatted on screen

TEXT



${color}${if_running rhythmbox}${font Aller:size=11}${color #656565}Rhythmbox Is Now Playing:
${color #656565}${execibar 1 conkyRhythmbox --datatype=PP}
${execp conkyRhythmbox --template=~/.conkyrhythmbox/conkyRhythmbox.template}
${endif}


```Here's the conkyRhythmbox.template for it:
```
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
${image [--datatype=CA] -n -p 0,0 -s 80x80}
```And the versions:
conky-all - 1.8.0-1
conkyrhythmbox - 2.16
conkyforecast - 2.15

And what is weird is some songs do not display the picture in the cronky, but there is a picture at the bottom left hand of Rhythmbox.
That should be displaying.
Here is a screenshot: (You can see that the pictures do not match in size)

[[IMG]http://ompldr.org/tNmFycQ[/IMG]]("http://ompldr.org/vNmFycQ")

---

### Post by kaivalagi on 2010-11-25
Good taste in music Cavsfan :D

I'm really into the black keys right now, their new album called brothers is VERY good...

Haven't been keeping up with the image issues, but all the config looks the way it should...on face value

---

### Post by Cavsfan on 2010-11-25
> **kaivalagi said:**
> Good taste in music Cavsfan :D

I'm really into the black keys right now, their new album called brothers is VERY good...

Haven't been keeping up with the image issues, but all the config looks the way it should...on face value

Thanks. I just don't think they will ever be the same without Layne Stayley! His voice is what I thought made them Alice in Chains.
The one octave lower sound, Layne's fabulous voice. It is sad that the heroin got to him like it did! I can't believe people are still doing that crap!

But, you are right their new album is good and I am glad Jerry is still going strong. Their new guy even sounds a lot like Layne 
although no one will ever replace his voice.

Anyway, as you can see from the picture, the picture that displays on the Conky at the bottom left just has "Alice" instead of 
"Alice in Chains" like in the Rhythmbox picture. If you could help me figure out how to get the conky to resize it, I would be grateful!

You have all of my files. Thanks for your help

---

### Post by kaivalagi on 2010-11-26
> **Cavsfan said:**
> Anyway, as you can see from the picture, the picture that displays on the Conky at the bottom left just has "Alice" instead of 
"Alice in Chains" like in the Rhythmbox picture. If you could help me figure out how to get the conky to resize it, I would be grateful!

You have all of my files. Thanks for your help

Try posting all your files and asking in the conkyrc thread ([http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)), this must have been a problem for someone else in there before now...

---

### Post by Pablo Pablovski on 2010-11-27
Cavsfan, I tried your conky / template combuination and found I wasn't getting the image displayed at all for some reason. So, I had a play about with them and found that if I moved the image variable to the top of the template file, the image displayed properly - right size, position.

Here's the amended template:

```
${image [--datatype=CA] -n -p 0,0 -s 80x80}
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
```

You might need to play about with positioning and size of the text to get everything as you want it - I had to move the "Rhythmbox Is Now Playing" line down a bit to get it lined up.

Fingers crossed!

PP

---

### Post by Cavsfan on 2010-11-27
> **Pablo Pablovski said:**
> Cavsfan, I tried your conky / template combuination and found I wasn't getting the image displayed at all for some reason. So, I had a play about with them and found that if I moved the image variable to the top of the template file, the image displayed properly - right size, position.

Here's the amended template:

```
${image [--datatype=CA] -n -p 0,0 -s 80x80}
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
```You might need to play about with positioning and size of the text to get everything as you want it - I had to move the "Rhythmbox Is Now Playing" line down a bit to get it lined up.

Fingers crossed!

PP

I wish I had read your post before I did what **kaivalagi** suggested and posted in the post your conky and screenshot thread!

Viola! That worked perfectly!!! Well, the picture resized perfectly at least.
The picture is perfectly placed, but there is some garbage at the bottom where the only thing I would think is displayed is volume.

Here is a screen of it while playing and it looks good except for the weird stuff where volume should be.

[[img]http://ompldr.org/tNmMwYQ[/img]](http://ompldr.org/vNmMwYQ)

And here is a screen when the song gets done and you can see there is still garbage where volume should be, just different garbage.

[[img]http://ompldr.org/tNmMwZg[/img]](http://ompldr.org/vNmMwZg)

Thanks for your help!

---

### Post by Laggg on 2010-11-28
I'm having trouble getting Rhythmbox working on my conky set-up. Here is what I get when I type: 'conkyRhythmbox -v'

```
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
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:TI
Rusko b2b Markle (12-Jul-2007)

```

Here is my ~/.conkyrc
```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

format_human_readable

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=9
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color 3C3B37

color0 292927
color1 C6B9A6
color2 292927

TEXT
${font Droid Sans:style=Bold:size=8}Maverick Meerkat $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--UPDATES
${goto 32}Updates: ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 0' | cut -c15-16}°C${color}${font}  ${color2}${cpugraph 0 8,50 104E8B 0077ff}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 1' | cut -c15-16}°C${color}${font}  ${color2}${cpugraph cpu2 8,50 104E8B 0077ff}${color}
${goto 32}CPU3: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu3}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 2' | cut -c15-16}°C${color}${font}  ${color2}${cpugraph cpu3 8,50 104E8B 0077ff}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Droid Sans:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${font}
# |--CPU
${voffset 2}${color0}${font Poky:size=14}s${font}${color}${voffset -8}${goto 32}SWAP: ${font Droid Sans:style=Bold:size=8}${color1}${swapperc}%${color}${font}
${voffset 4}${offset 1}${color0}${swapbar 4,18}${color}${voffset -4}${goto 32}F: ${font Droid Sans:style=Bold:size=8}${color2}$swapmax${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}$swap${color}${font}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -12}${goto 28}${font Arial Black:size=38}${color2}${time %H}${color}${font}${voffset -28}${font Droid Sans:style=Bold:size=11}${color2}${time :%M}${time :%S}${color}${font}
${voffset -2}${goto 100}${font Droid Sans:style=Bold:size=8}${color2}${time %A}${color}${font}
${goto 100}${time %d %b %Y}
################
# - CALENDAR - #
################
${voffset -2}${color0}${font Poky:size=16}D${font}${voffset -8}${font Droid Sans:style=Bold:size=7}${offset -17}${voffset 4}${time %d}${font}${color}${voffset -1}${font Droid Sans Mono:size=7}${execpi 300 DJS=`date +%_d`; cal |sed '2,7!d'| sed '/./!d' | sed 's/^/${goto 32} /'| sed 's/$/ /' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${font Droid Sans:style=Bold:size=8}${color1}'"$DJS"'${color}${font Droid Sans Mono:size=7}'" "/}${voffset -1}
####################
# - MEDIA PLAYER - #
####################
${voffset 4}${font Droid Sans:style=Bold:size=8}MEDIA PLAYER $stippled_hr${font}
${execi 6 /home/realeyes/.conkycolors/bin/conkyCover}${execpi 2 conkyRhythmbox -t /home/realeyes/.conkycolors/templates/conkyPlayer.template}
#
#${color4}Template Output:
#${color1}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/#conkyRhythmbox.template}

#${color4}Standard Output:
#${voffset 5}${color4} Title:  ${color1}${font}${exec conkyRhythmbox --datatype=TI} 
#${color4} Position:  ${color1}${font}${exec conkyRhythmbox --datatype=PT}/${exec #conkyRhythmbox --datatype=LE}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 104E8B 0077ff}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 104E8B 0077ff}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 /usr/share/conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 104E8B 0077ff}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup eth0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 104E8B 0077ff}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown eth0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 /usr/share/conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 104E8B 0077ff}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 104E8B 0077ff}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}
```

Can anyone help me get my Rhythmbox working? Is there anything else I need to post? My Rhythmbox.py script or something? Any help appreciated.

---

### Post by Pablo Pablovski on 2010-11-28
> **Cavsfan said:**
> I wish I had read your post before I did what **kaivalagi** suggested and posted in the post your conky and screenshot thread!

Viola! That worked perfectly!!! Well, the picture resized perfectly at least.
The picture is perfectly placed, but there is some garbage at the bottom where the only thing I would think is displayed is volume.

Here is a screen of it while playing and it looks good except for the weird stuff where volume should be.

[[img]http://ompldr.org/tNmMwYQ[/img]](http://ompldr.org/vNmMwYQ)

And here is a screen when the song gets done and you can see there is still garbage where volume should be, just different garbage.

[[img]http://ompldr.org/tNmMwZg[/img]](http://ompldr.org/vNmMwZg)

Thanks for your help!

Excellent - progress!

I'm beginning to think there's a problem with the conkyrhythmbox script (sorry, kaivalagi...) such that the last entry in a template file doesn't display correctly. While I was testing your script, console errors of the "unknown command {ima}" variety appeared. At that point, the "image" variable was last in in the template.

To test, kill conky and re-run it from the console - note down any error messages and post them.

You could also try moving the template contents back to the main conky script. I haven't tried doing that yet, but there's a chance it'll work ok - in which case, the problem looks to be in the parsing of the template.

---

### Post by kaivalagi on 2010-11-28
> **Cavsfan said:**
> I wish I had read your post before I did what **kaivalagi** suggested and posted in the post your conky and screenshot thread!
It might be worth posting what worked though, I suspect conky has a bug...?
> **Cavsfan said:**
> Viola! That worked perfectly!!! Well, the picture resized perfectly at least.
Glad you got it working anyway :)


> **Pablo Pablovski said:**
> I'm beginning to think there's a problem with the conkyrhythmbox script (sorry, kaivalagi...) such that the last entry in a template file doesn't display correctly. While I was testing your script, console errors of the "unknown command {ima}" variety appeared. At that point, the "image" variable was last in in the template.

To test, kill conky and re-run it from the console - note down any error messages and post them.

You could also try moving the template contents back to the main conky script. I haven't tried doing that yet, but there's a chance it'll work ok - in which case, the problem looks to be in the parsing of the template.

Mmmmm, I would think it's the parsing execp/execpi having issue as this hasn't been a problem before now. In fact I use the same template file consuming code in all my scripts, my forecast one for example has images on the last line:
```

...
${color1}${font Liberation Sans:style=Bold:size=9}[--datatype=DW --centeredwidth=15 --startday=3]
${voffset 70}${color1}${font}[--datatype=CT --centeredwidth=15 --startday=3]
${color1}${font}[--datatype=HT --centeredwidth=7 --startday=3]/[--datatype=LT --centeredwidth=7 --startday=3]
${color1}${font}[--datatype=WS --imperial --centeredwidth=15 --startday=3]
${color1}${font}[--datatype=WD --centeredwidth=15 --startday=3]
${color2}${hr}
${image [--datatype=WI] -p 5,60 -s 64x64}
${image [--datatype=WI --startday=0] -p 5,205 -s 64x64}
${image [--datatype=WI --startday=1] -p 5,355 -s 64x64}
${image [--datatype=WI --startday=2] -p 5,505 -s 64x64}
${image [--datatype=WI --startday=3] -p 5,650 -s 64x64}
${image [--datatype=MI] -p 53,60 -s 16x16}

```

What happens if you put a simple carriage return on the last line of the template, still having images rendered from the end of the template?

---

### Post by kaivalagi on 2010-11-28
> **Laggg said:**
> Can anyone help me get my Rhythmbox working? Is there anything else I need to post? My Rhythmbox.py script or something? Any help appreciated.

The conkyRhythmbox -v output looks fine, TI is the default datatype if not set and that's what you got output for.

What happens if you run this command in the terminal/console i.e. the one doing stuff in your conkyrc:

```
conkyRhythmbox -t /home/realeyes/.conkycolors/templates/conkyPlayer.template --verbose
```

You may also what to delete the lines after this command in your conkyrc that are currently commended out, the conkyrc is not a true script so expect strange behaviour due to lots of lines commended out such as conky windows being longer than you want etc.

---

### Post by Pablo Pablovski on 2010-11-28
> **kaivalagi said:**
> 
Mmmmm, I would think it's the parsing execp/execpi having issue as this hasn't been a problem before now. In fact I use the same template file consuming code in all my scripts, my forecast one for example has images on the last line:
```

...
${color1}${font Liberation Sans:style=Bold:size=9}[--datatype=DW --centeredwidth=15 --startday=3]
${voffset 70}${color1}${font}[--datatype=CT --centeredwidth=15 --startday=3]
${color1}${font}[--datatype=HT --centeredwidth=7 --startday=3]/[--datatype=LT --centeredwidth=7 --startday=3]
${color1}${font}[--datatype=WS --imperial --centeredwidth=15 --startday=3]
${color1}${font}[--datatype=WD --centeredwidth=15 --startday=3]
${color2}${hr}
${image [--datatype=WI] -p 5,60 -s 64x64}
${image [--datatype=WI --startday=0] -p 5,205 -s 64x64}
${image [--datatype=WI --startday=1] -p 5,355 -s 64x64}
${image [--datatype=WI --startday=2] -p 5,505 -s 64x64}
${image [--datatype=WI --startday=3] -p 5,650 -s 64x64}
${image [--datatype=MI] -p 53,60 -s 16x16}

```

What happens if you put a simple carriage return on the last line of the template, still having images rendered from the end of the template?

If I do that with Cavsfan's script, the image isn't displayed, though the correct details for "Volume" are output. Same if I delete the CR on the end of the line. 

When I move the image variable to the top, it displays, but the "volume" output doesn't. I'm presuming a conky with "bottom left" alignment expands "up the screen" (in the same way that one with "top right" alignment expands "down the screen") so  the more lines of output that conky displays, the further up the screen the output will start.

I tried adding a copy of the Volume variable to the bottom of the template:

```
${image [--datatype=CA] -n -p 0,0 -s 80x80}
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
${color3}Volume:${color1}[--datatype=VO]
```

to see if it's just the last variable that doesn't get actioned, but the volume didn't display even then, although I do get spurious output (see the screenshot). I also get theses errors in console:

```
Conky: unknown variable col
```

So, still looks like a parsing issue somewhere. Apologies for maligning your excellent script earlier - you're right, of course - it looks like a conky isuse.

---

### Post by kaivalagi on 2010-11-28
> **Pablo Pablovski said:**
> I also get theses errors in console:
```
Conky: unknown variable col
```

Ooooo, this could be a big clue!

"${col" could be a truncated "${color3}" etc, try upping the text buffer size in conky, it might be running out of buffer for all this text which would explain all the bizarre unexplainable behaviour with the images etc

Copied from the first post of the forecast script:
[INDENT]Conky has a default limitation of 128 bytes for any text output from a variable (such as execi). If you are creating large templates with more characters than the default buffer size can handle, the output will get truncated. If this happens you can override the default behaviour by setting as new buffer size before the TEXT section in your conkyrc file, as follows:
```

text_buffer_size 1024

```
[/INDENT]
Just keep increasing it until the script works okay...


> **Pablo Pablovski said:**
> So, still looks like a parsing issue somewhere. Apologies for maligning your excellent script earlier - you're right, of course - it looks like a conky isuse.
No worries, I'll be the first to admit a fault with the script and fix it, it's just not changed enough for a long time to be it ;)

---

### Post by Pablo Pablovski on 2010-11-28
> **kaivalagi said:**
> Ooooo, this could be a big clue!

"${col" could be a truncated "${color3}" etc, try upping the text buffer size in conky, it might be running out of buffer for all this text which would explain all the bizarre unexplainable behaviour with the images etc

Copied from the first post of the forecast script:
[INDENT]Conky has a default limitation of 128 bytes for any text output from a variable (such as execi). If you are creating large templates with more characters than the default buffer size can handle, the output will get truncated. If this happens you can override the default behaviour by setting as new buffer size before the TEXT section in your conkyrc file, as follows:
```

text_buffer_size 1024

```
[/INDENT]
Just keep increasing it until the script works okay...


Yes! That's it! I changed it to 1024 - still the same issue. Upped it to 2048, and - to use Cavsfan's term - voila! Perfect output. Screenie att.

Now all we need to do is wait for Cavsfan to turn up and try it out...

---

### Post by Cavsfan on 2010-11-28
```
text_buffer_size 1024
```Thanks to both of you! This was my whole problem! My .conkyrc did not have this variable in it.
When I added it everything looks perfect! I put everything in the template and put the album art line at the top.

I changed maximum_width from 280 to 320 too.

[[IMG]http://ompldr.org/tNmNhNg[/IMG]]("http://ompldr.org/vNmNhNg")

Now, if someone could help me figure out how to get my cpu temperature folder back for my 3rd core I would be happy as a clam!
When I updated to the new kernel the other day it some how deleted a folder that tells conky the cpu temp. of my 3rd core! 

The other 3 are still there and I cannot figure out how to get the missing one back.
Please see this thread: 
[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1629933_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1629933")

Thanks! :p

---

### Post by Pablo Pablovski on 2010-11-28
Great, glad it's finally working as you'd like.

Re: your temp display issue. Not something I know much about, but I *think* it mught be related to the lmsensors (or lm-sensors) package. Do a bit of searching for lm-sensors. Check that it's properly installed:

```
pablo@ubuntu-64:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.42 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:     +3.33 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:     +4.97 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:    +11.71 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:    3068 RPM  (min =    0 RPM)
CHASSIS FAN Speed:   0 RPM  (min =    0 RPM)
CHIPSET FAN Speed:   0 RPM  (min =    0 RPM)
CPU Temperature:   +38.0°C  (high = +90.0°C, crit = +125.0°C)  
MB Temperature:    +32.0°C  (high = +70.0°C, crit = +125.0°C)  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +41.0°C                                    

```


WARNING! Not my area of expertise.

---

### Post by Cavsfan on 2010-11-28
> **Pablo Pablovski said:**
> Great, glad it's finally working as you'd like.

Re: your temp display issue. Not something I know much about, but I *think* it mught be related to the lmsensors (or lm-sensors) package. Do a bit of searching for lm-sensors. Check that it's properly installed:

WARNING! Not my area of expertise.

Thanks, but I am missing the folder for some odd reason. I tried uninstalling lm-sensors and reinstalling it to no avail. See what I mean

```
cavsfan@cavsfan-MS-7529:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +41.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +41.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +40.0°C  (high = +76.0°C, crit = +100.0°C)  

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:       +3.36 V
in1:         +1.12 V  (max =  +2.04 V)   
in2:         +0.92 V
in3:         +0.76 V
in4:         +0.98 V
in5:         +1.11 V
in6:         +0.91 V
3VSB:        +3.36 V
Vbat:        +3.31 V
fan1:       2439 RPM
fan2:       2752 RPM
fan3:       2762 RPM
fan4:          0 RPM  ALARM
temp1:       +32.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:       +36.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +95.0°C, hyst = +91.0°C)  sensor = thermistor
temp3:       +33.0°C  (high = +70.0°C, hyst = +68.0°C)  
                      (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

```Core 0,1 and 3 are there, just not 2. I cannot find what process created the folder in the first place.
Thanks!

---

### Post by kaivalagi on 2010-11-28
> **Cavsfan said:**
> Core 0,1 and 3 are there, just not 2. I cannot find what process created the folder in the first place.
Thanks!

I doubt there is a "process" as such that would have created those folders as they are system folders...take a look at the sys folder and what is beneath...all those folders would not have been created by a conky process...

Interestingly I have nothing equivalent to yourself in my sys/bus/platform folders and that's whether I am looking at ArchLinux or Ubuntu versions 10.04 or 10.10 in VMs

I'd hazard a guess that these folder hierarchies alter with kernel updates and you've updated and now they don't work for you...try looking through them to find something suitable or better still look at alternative methods to do what you want...plug away in the the conkyrc thread not here though ;)

---

### Post by Cavsfan on 2010-11-28
> **kaivalagi said:**
> I doubt there is a "process" as such that would have created those folders as they are system folders...take a look at the sys folder and what is beneath...all those folders would not have been created by a conky process...

Interestingly I have nothing equivalent to yourself in my sys/bus/platform folders and that's whether I am looking at ArchLinux or Ubuntu versions 10.04 or 10.10 in VMs

I'd hazard a guess that these folder hierarchies alter with kernel updates and you've updated and now they don't work for you...try looking through them to find something suitable or better still look at alternative methods to do what you want...plug away in the the conkyrc thread not here though ;)

Yes, I have an nvidia video card and prob a different mobo, sensors-detect would find different things.
I am trying to install the previous kernel and maybe the current one too.
Thanks! My Rhythmbox conky is smoking now!

---

### Post by Laggg on 2010-11-30
> **kaivalagi said:**
> The conkyRhythmbox -v output looks fine, TI is the default datatype if not set and that's what you got output for.

What happens if you run this command in the terminal/console i.e. the one doing stuff in your conkyrc:

```
conkyRhythmbox -t /home/realeyes/.conkycolors/templates/conkyPlayer.template --verbose
```

You may also what to delete the lines after this command in your conkyrc that are currently commended out, the conkyrc is not a true script so expect strange behaviour due to lots of lines commended out such as conky windows being longer than you want etc.

Well, I've got some of the kinks worked out, except now the album covers appear at the top let of my conky, and not in the 'MEDIA PLAYER' box they're supposed to be in. When I run:
```
conkyRhythmbox -t /home/realeyes/.conkycolors/templates/conkyPlayer.template --verbose
```

I get back...
```
realeyes@The-Blue-Box:~$ conkyRhythmbox -t /home/realeyes/.conkycolors/templates/conkyPlayer.template --verbose
*** INITIAL OPTIONS:
    datatype: TI
    template: /home/realeyes/.conkycolors/templates/conkyPlayer.template
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Copying coverart from /home/realeyes/.cache/rhythmbox/covers/Rusko - Studio Mix for Radio 1 - Mary Anne Hobbs.jpg to /tmp/cover
INFO: Preparing output for datatype:ST
INFO: Preparing output for datatype:AR
INFO: Preparing output for datatype:AL
INFO: Preparing output for datatype:TI
INFO: Preparing output for datatype:PT
INFO: Preparing output for datatype:LE
${if_running exaile}
${voffset -12}${color0}${font Webdings:size=16}U${font}${color}${voffset -2}${goto 32}Status:${alignr}${color2}Playing${color}
${voffset 4}${color0}${color0}${font Musicelements:size=19}z${font}${color}${voffset -8}${goto 32}Song:${alignr}${color2}Rusko${color}
${color2}${alignr}Studio Mix for Radio 1 - Mary Anne Hobbs${color}
${color2}${alignr}"Cockney Knees Up Mix"${color}
${voffset -7}${color0}${font Martin Vogel's Symbols:size=19}U${font}${color}${voffset -4}${goto 32}Time:${alignr}${color2}0:22/25:39${color}${voffset 2}$else
${voffset -12}${color0}${font Webdings:size=16}U${font}${color}${voffset -2}${goto 32}Status:${alignr}${color2}off${color}
${voffset 12}$alignc${font Droid Sans:style=Bold:size=8}${color2}${color}${font}${voffset -10}
$endif

```

Here is the relevant part of my ~/.conkyrc file.
```
####################
# - MEDIA PLAYER - #
####################
${voffset 4}${font Droid Sans:style=Bold:size=8}MEDIA PLAYER $stippled_hr${font}
${execi 6 /home/realeyes/.conkycolors/bin/conkyCover}${execpi 2 conkyRhythmbox -t ~/Conky/conky_colors/conkycolors/templates/conkyPlayer.template}
```

I went ahead and got ImageMagick as well, by typing:
```
 sudo apt-get -y install imagemagick
```

So, maybe it's working a bit? I just need to know how to align the album art to the right section of the conky. Oh! And here is my template file :P
(conkyPlayer.template)
```
${color1}Status:${color1}[--datatype=ST]
${color1}Artist:${color1}[--datatype=AR]
${color1}Album:${color1}[--datatype=AL]
${color1}Title:${color1}[--datatype=TI]
${color1}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${color1}Rating:${color1}[--datatype=RT]
${color1}Volume:${color1}[--datatype=VO]
${image [--datatype=CA] -n -p 0,0 -s 80x80}
```

---

### Post by kaivalagi on 2010-12-01
Good stuff, looking alright now then

To get the image in the right place you need to edit this line from your template, specifically the 2 numbers in bold:
```
${image [--datatype=CA] -n -p **0,0** -s 80x80}
```

From conky documentation [here]("conky.sourceforge.net/variables.html") the full set of image options are detailed as such:

[INDENT]**image** <path to image> (-p x,y) (-s WxH) (-n) (-f interval)
Renders an image from the path specified using Imlib2. Takes 4 optional arguments: a position, a size, a no-cache switch, and a cache flush interval. Changing the x,y position will move the position of the image, and changing the WxH will scale the image. If you specify the no-cache flag (-n), the image will not be cached. Alternately, you can specify the -f int switch to specify a cache flust interval for a particular image. Example: ${image /home/brenden/cheeseburger.jpg -p 20,20 -s 200x200} will render 'cheeseburger.jpg' at (20,20) scaled to 200x200 pixels. Conky does not make any attempt to adjust the position (or any other formatting) of images, they are just rendered as per the arguments passed. The only reason $image is part of the TEXT section, is to allow for runtime modifications, through $execp $lua_parse, or some other method.[/INDENT]

Basically you need to mess with x,y to get the image in the right place

---

### Post by Laggg on 2010-12-01
> **kaivalagi said:**
> Good stuff, looking alright now then

To get the image in the right place you need to edit this line from your template, specifically the 2 numbers in bold:
```
${image [--datatype=CA] -n -p **0,0** -s 80x80}
```

From conky documentation [here]("conky.sourceforge.net/variables.html") the full set of image options are detailed as such:

[INDENT]**image** <path to image> (-p x,y) (-s WxH) (-n) (-f interval)
Renders an image from the path specified using Imlib2. Takes 4 optional arguments: a position, a size, a no-cache switch, and a cache flush interval. Changing the x,y position will move the position of the image, and changing the WxH will scale the image. If you specify the no-cache flag (-n), the image will not be cached. Alternately, you can specify the -f int switch to specify a cache flust interval for a particular image. Example: ${image /home/brenden/cheeseburger.jpg -p 20,20 -s 200x200} will render 'cheeseburger.jpg' at (20,20) scaled to 200x200 pixels. Conky does not make any attempt to adjust the position (or any other formatting) of images, they are just rendered as per the arguments passed. The only reason $image is part of the TEXT section, is to allow for runtime modifications, through $execp $lua_parse, or some other method.[/INDENT]

Basically you need to mess with x,y to get the image in the right place

Thank you very much :D

---

### Post by kaivalagi on 2010-12-11
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated main script to only actually copy over found cover art when --datatype=CA is requested
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.17_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyrhythmbox_2.17_source.changes)

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

### Post by Cavsfan on 2010-12-16
> **kaivalagi said:**
> **[COLOR=Red][SIZE=3]IMPORTANT NEWS[/SIZE][/COLOR]**

All the script packages have now been copied into the **Conky Companions PPA**. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this: 

```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*

```Then follow the modified first post instructions for the scripts

[COLOR=Red]**Script updates will only be published through this new ppa going forwards**[/COLOR]

I got an error saying /etc/apt/sources.list.d/m-buck* didn't exist. But. it removed the other one.
And I added the one on page one, so I guess I am good to go right because it works beautifully!

---

### Post by kaivalagi on 2010-12-17
> **Cavsfan said:**
> I got an error saying /etc/apt/sources.list.d/m-buck* didn't exist. But. it removed the other one.
And I added the one on page one, so I guess I am good to go right because it works beautifully!

Yeah, lots will, the m-buck* removal is for really old repo list files, they were in use before conkyhardcore

Glad it's working for you :)

---

### Post by Cavsfan on 2011-01-13
Hi kaivalagi,
I was on Maverick and all was smooth until the other day and everything seemed to screw up, so I went back to Lucid the LTS.  I made 
sure to preserve and backup my conkys and for some odd reason the album art is no longer displayed in Lucid when I play the exact 
same songs that did display the album art in Maverick.

Would you have any clue as to why this would be? Everything else is good, just no album art.
Thanks! :D

---

### Post by kaivalagi on 2011-01-13
> **Cavsfan said:**
> Would you have any clue as to why this would be? Everything else is good, just no album art.
Thanks! :D

No idea, the script versions are identical with all Ubuntu versions from Hardy to Natty - I would hazard a guess that the Rhythmbox d-bus methods or inner workings are different...maybe enabling backports might give you a newer more robust version of Rhythmbox? Or try to track down a PPA for development versions of the player maybe?

---

### Post by Cavsfan on 2011-01-13
The folder had 4 different sized album art pics for some odd reason and when I dropped the small one into Rhythnbox, it went back to normal.
I'm still good! Sorry to bother you!

But, I did have one question though: can it be changed to update every second as the Position only changes every 5 seconds instead of by the second.
Or would that be a bad thing?
Thanks!

---

### Post by kaivalagi on 2011-01-14
> **Cavsfan said:**
> But, I did have one question though: can it be changed to update every second as the Position only changes every 5 seconds instead of by the second.
Or would that be a bad thing?

You could have it run every second no worries but with cover art in place too that's a lot of file copying going on

You could split it up into 2 execs, one for the main details on the song and it's progress which is executed every second and another for the cover art...e.g.

```
${execpi 1 conkyRhythmbox --template=template/for/details}
${execpi 5 conkyRhythmbox --template=themplate/for/coverart}

```

Have a play and see what's best for you

---

### Post by Cavsfan on 2011-01-14
> **kaivalagi said:**
> You could have it run every second no worries but with cover art in place too that's a lot of file copying going on

You could split it up into 2 execs, one for the main details on the song and it's progress which is executed every second and another for the cover art...e.g.

```
${execpi 1 conkyRhythmbox --template=template/for/details}
${execpi 5 conkyRhythmbox --template=themplate/for/coverart}

```Have a play and see what's best for you

Thanks, I'll try that as soon as I can get around to it. :D

---

### Post by Cavsfan on 2011-01-14
One thing that is puzzling me about the album art displaying in the Conky is this: I start up Rhythmbox and 
play a song and the art appears at the bottom left of Rhythmbox, but not in the Conky.
If I open the folder with the songs and drag the picture over the existing picture in Rhythmbox, Conky will then display it properly. 
Where does the Conky get the album art from anyway?
Thanks! :)

---

### Post by kaivalagi on 2011-01-14
> **Cavsfan said:**
> Where does the Conky[COLOR="Blue"]Rhythmbox[/COLOR] get the album art from anyway?
Thanks! :)

From the code:
```
                            coverart = ""
                            if "rb:coverArt-uri" in props:
                                coverart = props["rb:coverArt-uri"]
                                if coverart.find("http://") != -1:
                                    coverart = ""
                                else:
                                    coverart = urllib.unquote(coverart).replace("file://","")
```

So the coverart is retrieved from the rb:coverArt-url property available via d-bus...

Just checked and it's not working so at some point the coverart property has been removed from the app (script was working...). I am running RB v.0.13.2. I guess when you drag cover art to RB it then populates the RB database for that album with the cover art given...but doesn't by default when fetched from the net?

I don't think I can do anything about it as it looks like a Rhythmbox issue to me...at a guess...might be worth asking the question to the RB devs why the coverart is not present by default in the d-bus methods?

---

### Post by Cavsfan on 2011-01-14
> **kaivalagi said:**
> From the code:
```
                            coverart = ""
                            if "rb:coverArt-uri" in props:
                                coverart = props["rb:coverArt-uri"]
                                if coverart.find("http://") != -1:
                                    coverart = ""
                                else:
                                    coverart = urllib.unquote(coverart).replace("file://","")
```So the coverart is retrieved from the rb:coverArt-url property available via d-bus...

Just checked and it's not working so at some point the coverart property has been removed from the app (script was working...). I am running RB v.0.13.2. I guess when you drag cover art to RB it then populates the RB database for that album with the cover art given...but doesn't by default when fetched from the net?

I don't think I can do anything about it as it looks like a Rhythmbox issue to me...at a guess...might be worth asking the question to the RB devs why the coverart is not present by default in the d-bus methods?

Thanks and I am glad to know that it is not just me! I am using version 0.12.8 which I guess comes with Lucid.
So, when the devs fix it we should be good to go. :D

---

### Post by kaivalagi on 2011-01-14
> **Cavsfan said:**
> So, when the devs fix it we should be good to go. :D
If they know it's broken! I don't use RB anymore hence not knowing of the issue until now so I am not best placed to raise and test the issue/fix...and what I have mentioned is a best guess but worth raising

The fact that you have it working after doing things in RB means it must be RB at fault anyway...the script asks RB for the info after all

---

### Post by Cavsfan on 2011-01-19
I think I may have found the solution! :D I had down graded to Lucid from Maverick as you may know and this is what I had 
done in Lucid before and the album art appeared in Rhythmbox after doing so!

I was ripping my older CDs and the CDDB info did not populate until I found this solution.

```
sudo apt-get install cddb python-cddb libcddb-get-perl libcddb2 libaudio-cd-perl libcddb-perl
```The album art now displays with the conkyRhythmbox script!

:guitar:

See if that doesn't fix the album art issue for you. For some odd reason when I play song 1 it doesn't display, but if I go to 
song 2 it does and when I go back to song 1 it's still good.

Then when I closed Rhythmbox and then reopened it all was good, even song 1! :D

---

### Post by Cavsfan on 2011-01-19
Sorry about the triple post. I clicked once and it gave proxy error, so I clicked again and when it finally took I seen there were 3.

---

### Post by Cavsfan on 2011-01-19
I think I may have found the solution! :D I had down graded to Lucid from Maverick as you may know and this is what I had 
done in Lucid before and the album art appeared in Rhythmbox after doing so!

I was ripping my older CDs and the CDDB info did not populate until I found this solution.

```
sudo apt-get install cddb python-cddb libcddb-get-perl libcddb2 libaudio-cd-perl libcddb-perl
```The album art now displays with the conkyRhythmbox script!

:guitar:

See if that doesn't fix the album art issue for you. For some odd reason when I play song 1 it doesn't display, but if I go to 
song 2 it does and when I go back to song 1 it's still good.

Then when I closed Rhythmbox and then reopened it all was good, even song 1! :D

---

### Post by kaivalagi on 2011-01-19
> **Cavsfan said:**
> Sorry about the triple post. I clicked once and it gave proxy error, so I clicked again and when it finally took I seen there were 3.

Yeah, this site is knackered at the moment, I am guessing the database server is low on space and resources etc...

---

### Post by niiiklas on 2011-01-29
Hey, I'm experiencing a little problem with conkyRhythmbox from time to time.  It's kind of hard to reproduce as I'm not exactly sure what's causing  the problem in the first place.

I'm using conky in combination with a lua script to construct the name  of the album art as it's stored by Rhythmbox (in  ~/.cache/rhythmbox/covers). If the file is not present there I'm calling  conkyRhythmbox -d CA and copy the image from /tmp/cover to the covers directory. That is the  case when I have a file called folder.jpg in the path where the mp3  resides. Sometimes, however, when a folder.jpg is present and correctly  displayed in RB, conkyRhythmbox returns an empty string... sometimes,  because the rest of the time it'll work just fine.

The only additional information I can give you is that double-clicking the image in RB doesn't open the folder.jpg in the image viewer. So I'm guessing the problem is actually related to RB resp. the RB plugin and not conkyRhythmbox, but I thought I'd ask here if anyone else faced a similar problem in the past.

Cheers.

Edit: Noticed a song that didn't have a folder.jpg but an image that was displayed in RB although it wasn't present in the covers folder. Weirdly enough I fixed it by d&d'ing the cover that was displayed in RB onto the cover art frame in RB itself. By doing that I guess I manually told RB to copy the cover to the covers directory. Only thing that baffles me is where the cover resided in the first place :/

---

### Post by kaivalagi on 2011-01-29
> **niiiklas said:**
> Edit: Noticed a song that didn't have a folder.jpg but an image that was displayed in RB although it wasn't present in the covers folder. Weirdly enough I fixed it by d&d'ing the cover that was displayed in RB onto the cover art frame in RB itself. By doing that I guess I manually told RB to copy the cover to the covers directory. Only thing that baffles me is where the cover resided in the first place :/

Yeah, there isn't much I can help with, but I do know what you're speaking of. RB does sometimes display coverart but doesn't populate the d-bus methods for it too, until you re-download the cover art again and then it's stored appropriately...the only thing I can suggest is raising it as a bug with RB trying to give full details on how to reproduce if you can.......

---

### Post by niiiklas on 2011-01-29
Alright, thanks for the info. I filed a bug report here [https://bugzilla.gnome.org/show_bug.cgi?id=640915](https://bugzilla.gnome.org/show_bug.cgi?id=640915)

---

### Post by jmadero on 2011-01-30
Can someone help me out with this, I have the following: 

>    {
        name='if_match "${mpd_status}"=="Playing"}${mpd_percent}${else}${if_match "${mpd_status}"=="Paused"}${mpd_percent}${else}0${endif}${endif',
        --name='mpd_percent',
        arg='',
        max=100,
        bg_colour=0x2C3949,
        bg_alpha=0.5,
        fg_colour=0x71A1DF,
        fg_alpha=0.5,
        x=771, y=61,
        radius=28.5,
        thickness=5,
        start_angle=-90,
        end_angle=270
    },


But I ant to replace mpd with rhythmbox --database pp. Any suggestions? I have conkyRhythmbox installed (running Ubuntu 10.10). Tried a bunch of things and it's just not working. Thanks in advance.

---

### Post by kaivalagi on 2011-01-30
> **jmadero said:**
> But I ant to replace mpd with rhythmbox --database pp. Any suggestions? I have conkyRhythmbox installed (running Ubuntu 10.10). Tried a bunch of things and it's just not working. Thanks in advance.

That's Lua from one of wlourf's scripts right?

This is only a guess so I am not entirely sure if putting an exec in like this would work, the trouble is you are using a "name" to drive functionality which seems a bit wrong...?

```
{
name='if_match "${exec conkyRhythmbox -d ST}"=="Stopped"}0${else}${exec conkyRhythmbox -d PP}${endif}',
--name='mpd_percent',
arg='',
max=100,
bg_colour=0x2C3949,
bg_alpha=0.5,
fg_colour=0x71A1DF,
fg_alpha=0.5,
x=771, y=61,
radius=28.5,
thickness=5,
start_angle=-90,
end_angle=270
},
```

If that don't work (it wont handle RB not running...)then sorry but you're gonna have to wait for the conkyrc thread to reopen for posting again as ask there

---

### Post by jmadero on 2011-01-30
Thanks for the reply. No luck with that script. I actually got the original script from here:

[http://sen7.deviantart.com/art/Conky-NightDrive-151418309](http://sen7.deviantart.com/art/Conky-NightDrive-151418309)


Been modifying it quite a bit and this was one of the things I wanted to do. I'm going to keep playing around to get it to work. MPD is nice but it's too much work and I run mysql on the MPD port so I'd prefer just getting a rhythmbox ring going. If you have any other suggestions I'll give it a try. Thanks again

---

### Post by kaivalagi on 2011-01-30
> **jmadero said:**
> Thanks for the reply. No luck with that script. I actually got the original script from here:

[http://sen7.deviantart.com/art/Conky-NightDrive-151418309](http://sen7.deviantart.com/art/Conky-NightDrive-151418309)


Been modifying it quite a bit and this was one of the things I wanted to do. I'm going to keep playing around to get it to work. MPD is nice but it's too much work and I run mysql on the MPD port so I'd prefer just getting a rhythmbox ring going. If you have any other suggestions I'll give it a try. Thanks again

I run MPD, it would be worth changing it's default port if there's a clash ;)

If you are slightly interested in MPD have a look at a tool called mpd cron, it can fire any scripting you want off an event such as song change etc...very handy :) It might just sway it for you?

Here's scripts I run using it:
```
#!/usr/bin/env sh

# get lyrics (if found) and copy it to /tmp/lyrics
lyricsfile="$HOME/.lyrics/$MPD_SONG_TAG_ARTIST-$MPD_SONG_TAG_TITLE.txt"
outputlyricsfile="/tmp/lyrics"
if [ -f "$lyricsfile" ]; then
    rm -f "$outputlyricsfile"
    echo "lyrics.sh - Linking '$outputlyricsfile' to cover file '$lyricsfile'"
    ln -s "$lyricsfile" "$outputlyricsfile"
else
    rm -f "$outputlyricsfile"
fi
```

```
#!/usr/bin/env sh

##### get coverart linked #####
# get cover (if found) and copy it to /tmp/cover
coverfile="$HOME/.covers/$MPD_SONG_TAG_ARTIST-$MPD_SONG_TAG_ALBUM.jpg"
outputcoverfile="/tmp/cover"
if [ -f "$coverfile" ]; then
    rm -f "$outputcoverfile"
    echo "coverart.sh - Linking '$outputcoverfile' to cover file '$coverfile'"
    ln -s "$coverfile" "$outputcoverfile"
else
    echo "coverart.sh - No matching cover art file found here: '$coverfile'"
    rm -f "$outputcoverfile"
fi

```

---

### Post by Cavsfan on 2011-01-30
> **niiiklas said:**
> Alright, thanks for the info. I filed a bug report here [https://bugzilla.gnome.org/show_bug.cgi?id=640915](https://bugzilla.gnome.org/show_bug.cgi?id=640915)

I am glad to see the bug reported! :) I am having some of the same issues, but filing a but report is a bit above my capabilities at present.
Thanks!

---

### Post by Cavsfan on 2011-02-07
Just wondering, but I guess this would be another Rhythmbox bug or issue When playing a song the 
bar doesn't move in either Rhythmbox or conkyRhythmbox

As you can see the song is at :48 and the bar hasn't moved.

[[IMG]http://ompldr.org/tN2J2Zw[/IMG]]("http://ompldr.org/vN2J2Zw")

---

### Post by kaivalagi on 2011-02-07
> **Cavsfan said:**
> Just wondering, but I guess this would be another Rhythmbox bug or issue When playing a song the 
bar doesn't move in either Rhythmbox or conkyRhythmbox

As you can see the song is at :48 and the bar hasn't moved.

[[IMG]http://ompldr.org/tN2J2Zw[/IMG]]("http://ompldr.org/vN2J2Zw")

I would say 99% it's a RB fault, might be worth running d-feet when this is happening and requesting the Elapsed time with it to see, the time is returned in seconds

---

### Post by Cavsfan on 2011-02-08
> **kaivalagi said:**
> I would say 99% it's a RB fault, might be worth running d-feet when this is happening and requesting the Elapsed time with it to see, the time is returned in seconds

I got d-feet from Synaptic and found RB on the Session Bus and found a couple of places that mentioned Elapsed time, but
don't have a clue as to what I am looking for. Could you point me in the right direction?
Thanks!
And how's that baby coming? I remember she was ready to have the baby.

---

### Post by kaivalagi on 2011-02-08
This screenshot should show what you need to know, once you have opened the getElapsed execute dialog just click execute to get the elapsed time in seconds (L signifies "long int").

Mum is fine, 7 1/2 months in, not long now...due March 24th. Baby is a big time mover so she's not getting much rest...

---

### Post by Cavsfan on 2011-02-09
> **kaivalagi said:**
> This screenshot should show what you need to know, once you have opened the getElapsed execute dialog just click execute to get the elapsed time in seconds (L signifies "long int").

Mum is fine, 7 1/2 months in, not long now...due March 24th. Baby is a big time mover so she's not getting much rest...

My D-feet looks just like yours and each time I click execute the number gets higher, although the bar in both never move.
Does that mean it is a RB bug?

Good to hear the baby is coming along great! March will be here before you know it!
I have a 2 year old grandson who is going to be a chick magnet. 
He already is. Today he held his Mum's face and gave her a kiss! He is a very smart kid and huge. He looks like a 3 year old!

---

### Post by kaivalagi on 2011-02-09
> **Cavsfan said:**
> My D-feet looks just like yours and each time I click execute the number gets higher, although the bar in both never move.
Does that mean it is a RB bug?

Good to hear the baby is coming along great! March will be here before you know it!
I have a 2 year old grandson who is going to be a chick magnet. 
He already is. Today he held his Mum's face and gave her a kiss! He is a very smart kid and huge. He looks like a 3 year old!

Mmmmm, if d-feet works then so should the conkyRhythmbox script as it sources the information from d-bus just like d-feet does...

Can I suggest that you run the conkyRB script in a terminal making a request for the progress with a verbose argument added too, like so:

```
conkyRhythmbox --datatype=PT --verbose
```

For me I get this normally:

```
]$ conkyRhythmbox --datatype=PT --verbose
*** INITIAL OPTIONS:
    datatype: PT
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:PT
0:30

```

Post back the output, hopefully that should highlight any anomalies, assuming it has an error in amongst the output


This is our second child, the first is now 7 yrs and he too is a babe magnet :) We are constantly joking about how many girl friends he has...on the way to and from school he's always being chatted up by the girls...and some are from a few years up in school :lolflag:

Kids, gotta love em...they bring light into a dark world :)

---

### Post by Cavsfan on 2011-02-10
Here is my output and it looks like yours at least I think. The screen looks like it did at last post with no movement 
of the bar in conky or Rhythmbox.

```
$ conkyRhythmbox --datatype=PT --verbose
*** INITIAL OPTIONS:
    datatype: PT
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:PT
0:43

```And here is a copy of my conkyRhythmbox.template:

```
${image [--datatype=CA] -n -p 0,0 -s 80x80}
${color3}${execibar 1 conkyRhythmbox --datatype=PP}
${color3}Status:${color1}[--datatype=ST]
${color3}Artist:${color1}[--datatype=AR]
${color3}Album:${color1}[--datatype=AL]
${color3}Title:${color1}[--datatype=TI]
${color3}Position:${color1}[--[COLOR=Red]datatype=PT[/COLOR]]/[--datatype=LE] - [--datatype=PP]%
${color3}Rating:${color1}[--datatype=RT]
${color3}Volume:${color1}[--datatype=VO]
```You are right about kids. They are what makes everything worthwhile!
I forgot to tell you in addition to putting his hands on her face and kissing her, he also told her she was pretty! And he just turned 2!
It doesn't get any better! Melts your heart.  :grin:

---

### Post by kaivalagi on 2011-02-10
If the script doesn't fail and comes back with 0:43 over and over which matches the progress bar then it must RB at fault, some internal code getting in a cufuddle when calculating the progress somehow

---

### Post by dannyamayay on 2011-02-11
Hi, I've noticed if the titles are really long it'll automatically expand Conky's width.
 I limited the gapx and I fiddled with the output of Artist/Song/PT by using ${alignc} so the titles would expand from the center and it looked nicer. However the longer title names appear cut-off. If possible update the script for allowing scrolling output so the whole title can be read and not be cut off.

If there's already a way to do this with conky care to share? lol (;
I haven't read anything of the sort so far.

---

### Post by kaivalagi on 2011-02-11
The examples are as such just examples, I would expect you to edit things to your liking, everyone does ;)

Scrolling by the scripting won't work as the script has no state it is just re-executed every interval by conky, however there is a scroll variable with conky that might be worth a shot...

Go here and look at variables: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

---

### Post by Cavsfan on 2011-02-11
> **kaivalagi said:**
> If the script doesn't fail and comes back with 0:43 over and over which matches the progress bar then it must RB at fault, some internal code getting in a cufuddle when calculating the progress somehow

The output of that command displayed in seconds at the end changes every time I enter it again, but the progress bar in both do not move.
I am not going to worry about it though. It's no biggie.

Thanks. :D

---

### Post by yiannis66 on 2011-02-16
```
To run this script, yuo need conkyRhythmbox form kaivalagi 
http://ubuntuforums.org/showthread.php?t=928168


It also use a script from larryni to display cover with some effects.
the script is in the cover folder

And it uses 2 Lua script (from myself) packed into one single file.

And you need to install convert and rhymthbox of course !

```
I try to have the cover from rhythmbox and I don't know how to
"install convert".
Please help.
Thanks

---

### Post by TeoBigusGeekus on 2011-02-16
```
sudo apt-get install convert
```
&#960;&#945;&#964;&#961;&#953;&#974;&#964;&#951;.

---

### Post by yiannis66 on 2011-02-16
&#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974;.
But I get this

```
yiannis@yiannis-desktop:~$ sudo apt-get install convert
[sudo] password for yiannis: 
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#960;&#949;&#961;&#953;&#947;&#961;&#945;&#966;&#942;&#962; &#964;&#951;&#962; &#964;&#961;&#941;&#967;&#959;&#965;&#963;&#945;&#962; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
E: &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#949;&#973;&#961;&#949;&#963;&#951; &#964;&#959;&#965; &#960;&#945;&#954;&#941;&#964;&#959;&#965; convert
yiannis@yiannis-desktop:~$ ]
```

---

### Post by TeoBigusGeekus on 2011-02-16
Can you post the output of
```
whereis convert
```
?

---

### Post by yiannis66 on 2011-02-16
this is:

```
yiannis@yiannis-desktop:~$ whereis convert
convert: /usr/bin/convert /usr/share/man/man1/convert.1.gz
yiannis@yiannis-desktop:~$ 

```
Are u in greek forum? if yes,what user name u use?

---

### Post by TeoBigusGeekus on 2011-02-16
I'm in no greek forum.

Convert is already installed on your system.

---

### Post by yiannis66 on 2011-02-16
o.k
My proplem is when I run the conkyRhythmbox i get this

```
yiannis@yiannis-desktop:~$ 
Conky: desktop window (1c00045) is subwindow of root window (15a)
Conky: window type - desktop
Conky: drawing to created window (0x4a00001)
Conky: drawing to double buffer
convert: missing an image filename `/tmp/cover' @ convert.c/ConvertImageCommand/2838.
rm: &#945;&#948;&#965;&#957;&#945;&#956;&#943;&#945; &#948;&#953;&#945;&#947;&#961;&#945;&#966;&#942;&#962; «/»: &#917;&#943;&#957;&#945;&#953; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962;
convert: missing an image filename `/tmp/cover' @ convert.c/ConvertImageCommand/2838.
rm: &#945;&#948;&#965;&#957;&#945;&#956;&#943;&#945; &#948;&#953;&#945;&#947;&#961;&#945;&#966;&#942;&#962; «/»: &#917;&#943;&#957;&#945;&#953; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962;
convert: missing an image filename `/tmp/cover' @ convert.c/ConvertImageCommand/2838.
```
and my template is that:
```
${image [--datatype=CA] -n -p 0,0 -s 80x80}
${voffset -110}${font purisa:style=Bold:size=12}
${goto 350}Artist: [--datatype=AR]
${goto 350}Title: [--datatype=TI]
${goto 350}Album: [--datatype=AL]
${goto 350}Position: [--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${goto 350}Status: [--datatype=ST]
${voffset -81}${goto 780}Year: [--datatype=YR]
${goto 780}Track: [--datatype=TN]
#${goto 780}Rating: [--datatype=RT]
${goto 780}Volume: [--datatype=VO]
```
that is what i get when I run -v:
```
yiannis@yiannis-desktop:~$ conkyRhythmbox -v --datatype=CA
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA

yiannis@yiannis-desktop:~$ 
```

---

### Post by TeoBigusGeekus on 2011-02-16
I'm not familiar with the script; better wait for an answer from kaivalagi.

---

### Post by kaivalagi on 2011-02-16
So I assume you figured out that you need to install image magick to have the convert application for image work...

And it looks like you are not getting an image back from the script when run...maybe the song / player has none?

Start simple and use the script to just see if you can get a /tmp/cover path returned and then make sure that an image is there by opening /tmp/cover using something like eog or gimp. Once you are seeing an image okay then move on to the more complicated stuff...

Cheers

---

### Post by yiannis66 on 2011-02-16
Thanks for your help.
after that I have this:

```
yiannis@yiannis-desktop:~$ conkyRhythmbox -v --datatype=CA
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Copying coverart from /home/yiannis/.cache/rhythmbox/covers/001_Bob Sinclar feat. Sean Pau - &#902;&#947;&#957;&#969;&#963;&#964;&#959;.jpg to /tmp/cover
/tmp/cover
yiannis@yiannis-desktop:~$ 

```
But no icon for the cover yet.

---

### Post by kaivalagi on 2011-02-16
So what happens when you open /tmp/cover like this from the terminal:

```
eog /tmp/cover &
```

I assume it's a valid image?

---

### Post by yiannis66 on 2011-02-17
Hello,that is:
```
yiannis@yiannis-desktop:~$ eog /tmp/cover &
[2] 2213
[1]   Done                    eog /tmp/cover
yiannis@yiannis-desktop:~$ 

```
But no icon there,is empty...

---

### Post by yiannis66 on 2011-02-17
O.k at the second try I have a cover in the tmp/cover.
but I have in terminal this:

```
(eog:2409): GLib-GIO-CRITICAL **: g_app_info_equal: assertion `G_IS_APP_INFO (appinfo1)' failed
```

---

### Post by kaivalagi on 2011-02-17
So you have an image, if eog is not working that's another issue altogether...some songs with accented characters can cause issue...maybe that is the root cause of any issues you are having.

---

### Post by yiannis66 on 2011-02-17
Do you have any idea how can i fix it?

---

### Post by kaivalagi on 2011-02-17
> **yiannis66 said:**
> Do you have any idea how can i fix it?

No cause I have no idea of the exact problem...and the trouble is I don't use RB I use MPD these days...

Maybe one of the script users can help? What RB version are they running versus yourself? Does cover art work with that?

All I can say is it did work last time I checked

If you get no answer out of users of the script by the weekend I'll have to setup the player on my system and test it...0.13.3 is the version I have available to test with easily

---

### Post by yiannis66 on 2011-02-20
At the and I Put this in the conkyrc:
```
${exec conkyRhythmbox --datatype=CA}${image /tmp/cover -n -p 0,0 -s 200x200}
```
and the only proplem left to solve us u cn see at the photo is
the text(tmp/cover) stays on the cover
[[IMG]http://img228.imageshack.us/img228/5360/screenshot1fh.png[/IMG]](http://img228.imageshack.us/i/screenshot1fh.png/)

---

### Post by kaivalagi on 2011-02-20
> **yiannis66 said:**
> At the and I Put this in the conkyrc:
```
${exec conkyRhythmbox --datatype=CA}${image /tmp/cover -n -p 0,0 -s 200x200}
```
and the only proplem left to solve us u cn see at the photo is
the text(tmp/cover) stays on the cover
[[IMG]http://img228.imageshack.us/img228/5360/screenshot1fh.png[/IMG]](http://img228.imageshack.us/i/screenshot1fh.png/)

The --datatype=CA call will return the image path, there is no way around it doing that

The best approach is to use a template and have something like this where the [--datatype=CA] will be replaced with the image path when it is called:

```
${image [--datatype=CA] -p 0,0 -s 100x100}
```

then when parsed by the execp/execpi call it will be render like so:

```
${image /tmp/cover -p 0,0 -s 100x100}
```

HTH

---

### Post by yiannis66 on 2011-02-20
You are the best [SIZE="4"][FONT="Arial Black"]kaivalagi[/FONT][/SIZE]
Thanks you very much for your help and for the scripts that I am using for all conkys.

---

### Post by kaivalagi on 2011-02-20
Careful my head will explode with too much praise :)

Hope you get things working how you wanted, and please post what you've done for others 

Just in case the approach with templates and images is unclear, you need to cover the following off in any of my scripts that provide image paths and template options:

[LIST=1]
[*]have a main exec call in the conkyrc using execp or execpi (needed to parse content not actually written in the conkyrc in conky fashion)
[*]the scipt needs to support template files, use a template option to point at content as required
[*]the template file can have all the formatting methods you would expect in a conkyrc such as font / color etc etc
[*]the template file also needs requests via placeholders for data by the script, these are done like so: [--datatype=CA] or [--datatype=TI] etc. These should be mentioned in the scripts help content (call it with the -h option to see it)
[*]Note that conky 1.8.1 has problems with execpi/execp based formatting with the goto and offset functions producing silly squares, 1.8.0 has no such issues
[/LIST]

---

### Post by yiannis66 on 2011-02-22
I have from [http://crunchbanglinux.org/forums/topic/3728/images-in-conky-specifically-rhythmbox-album-art/]("http://crunchbanglinux.org/forums/topic/3728/images-in-conky-specifically-rhythmbox-album-art/")
A script name albumart and I made a small change at the line 8 
I put the " /tmp/cover "
So now is that :
 ```
#!/bin/bash
artist=`rhythmbox-client --print-playing-format %ta`
album=`rhythmbox-client --print-playing-format %aa`
str="`echo "$artist $album" | sed -e s/\\ /+/g`"
wget `wget "http://www.albumart.org/index.php?srchkey=$str&itempage=1&newsearch=1&searchindex=Music" -q -O - | 
grep "http://www.albumart.org/images/zoom-icon.jpg" -m 1 | 
sed -e 's/" border="0" class="image_border.*//' |
sed -e 's/.*img src="//'` -q -O /tmp/cover
```
Isave it in my home folder and I make my conkyrc after TEXT:
```
${font Santana:size=12}${color FFFF00}${exec conkyRhythmbox --datatype=AR}
${exec conkyRhythmbox --datatype=AL}
${exec conkyRhythmbox --datatype=PP}%
${exec conkyRhythmbox --datatype=CA}${image /tmp/cover -n -p 10,100 -s 200x200}
${exec ~/albumart}
```
And everythink is perfect.
[IMG]http://img810.imageshack.us/img810/4205/screenshot1sj.png[/IMG]

---

### Post by karmila on 2011-03-24
> **kaivalagi said:**
> The --datatype=CA call will return the image path, there is no way around it doing that

The best approach is to use a template and have something like this where the [--datatype=CA] will be replaced with the image path when it is called:

```
${image [--datatype=CA] -p 0,0 -s 100x100}
```then when parsed by the execp/execpi call it will be render like so:

```
${image /tmp/cover -p 0,0 -s 100x100}
```HTH

Wow :D

Thanks Mark, I had same question with conkyClementine and this answer solved my problem.

---

### Post by kaivalagi on 2011-03-24
> **karmila said:**
> Wow :D

Thanks Mark, I had same question with conkyClementine and this answer solved my problem.

You could do it this way but you may not even need the --datatype=CA thing as if you run the conkyClementine-GetCoverart script it will create a file in a known path instead on track change (much more efficient)...not all players work with an alternative script like this but clementine does as it presents the event handlers in it's d-bus methods ;)

---

### Post by karmila on 2011-03-26
> **kaivalagi said:**
> You could do it this way but you may not even need the --datatype=CA thing as if you run the conkyClementine-GetCoverart script it will create a file in a known path instead on track change (much more efficient)...not all players work with an alternative script like this but clementine does as it presents the event handlers in it's d-bus methods ;)

That would be much better.

This is CA part from my conkyrc
```
${execp conkyClementine --template=/path/to/conkyClementine.template}

```

And this is the template
```
${image [--datatype=CA] -p 30,290 -s 62x62}
```

I run GetCoverart.py script at terminal and see how it works but how to add the script to conkyrc?

---

### Post by kaivalagi on 2011-03-26
> **karmila said:**
> That would be much better.

This is CA part from my conkyrc
```
${execp conkyClementine --template=/path/to/conkyClementine.template}

```

And this is the template
```
${image [--datatype=CA] -p 30,290 -s 62x62}
```

I run GetCoverart.py script at terminal and see how it works but how to add the script to conkyrc?

Posted a bit of the history and a reply in the conkyClementine thread where this discussion belongs ;)
[http://ubuntuforums.org/showpost.php?p=10602389&postcount=33](http://ubuntuforums.org/showpost.php?p=10602389&postcount=33)

---

### Post by vehemoth on 2011-04-01
Is it possible to convert %20 etc to the keyboard characters, when i run conkyRhythmbox --datatype=CA it outputs everything right it just has %20, %5 etc instead, i can't use this in my conky setup

---

### Post by kaivalagi on 2011-04-02
> **vehemoth said:**
> Is it possible to convert %20 etc to the keyboard characters, when i run conkyRhythmbox --datatype=CA it outputs everything right it just has %20, %5 etc instead, i can't use this in my conky setup

What version of conkyRhythmbox are you running, the latest should "unquote" all these character codes...%20 => space etc

The current version is 2.17

```
conkyRhythmbox --version
```

You're not using conky colors or something like that are you? If you are that will be why, always out of date those...

---

### Post by vehemoth on 2011-04-02
> **kaivalagi said:**
> What version of conkyRhythmbox are you running, the latest should "unquote" all these character codes...%20 => space etc

The current version is 2.17

```
conkyRhythmbox --version
```

You're not using conky colors or something like that are you? If you are that will be why, always out of date those...

2.07, i got it as a deb is there a deb for the newer one or just source?

---

### Post by vehemoth on 2011-04-02
Thanks, I found it, you are so great, keep up the good work.

---

### Post by kaivalagi on 2011-04-02
> **vehemoth said:**
> Thanks, I found it, you are so great, keep up the good work.

No probs, if you are using Ubuntu I suggest you install it using the repo as per the first option in the first post, that way you'll keep updated

Cheers

---

### Post by vehemoth on 2011-04-02
Ok new problem, I tried using --statustest but the only value i could get it to return was the track title.

---

### Post by kaivalagi on 2011-04-02
Statustest is a setting that will affect --datatype=ST output text, I think you've misunderstood what it is for:
```
-s TEXT, --statustext=TEXT
                        [default: Playing,Paused,Stopped] The text must be
                        comma delimited in the form 'A,B,C'. Command line
                        option overridden if used in templates.

```

Not setting it will leave the default text output depending on what the state actually is, so when this is executed:
```
conkyRhythmbox --datatype=ST
```

you can get one of these:
```
Playing
Paused
Stopped
```

If you wanted A or B or C instead then you would use this:
```
conkyRhythmbox --datatype=ST --statustext="A,B,C"
```

---

### Post by vehemoth on 2011-04-02
> **kaivalagi said:**
> Statustest is a setting that will affect --datatype=ST output text, I think you've misunderstood what it is for:
```
-s TEXT, --statustext=TEXT
                        [default: Playing,Paused,Stopped] The text must be
                        comma delimited in the form 'A,B,C'. Command line
                        option overridden if used in templates.

```

Not setting it will leave the default text output depending on what the state actually is, so when this is executed:
```
conkyRhythmbox --datatype=ST
```

you can get one of these:
```
Playing
Paused
Stopped
```

If you wanted A or B or C instead then you would use this:
```
conkyRhythmbox --datatype=ST --statustext="A,B,C"
```

Thank you, you were very quick in answering, can you tell me what are the advantages of using a template.

---

### Post by kaivalagi on 2011-04-02
> **vehemoth said:**
> Thank you, you were very quick in answering, can you tell me what are the advantages of using a template.

You got lucky, expect to wait for hours or days the next time around ;)

Templates mean only one exec call in your conky is required and so less resource requirements and more speed. With a template all the required information is known by the script on the first call and it is gathered in one go anyway so it all gets output at the same time

Well worth it IMHO, if you get used to using templates a lot of the other scripts work in the same way :)

Make sure the conkyrc exec call to the script with templates is done via the execpi or execp command, it's needed to parse the output properly for conky formatting variables!

---

### Post by vehemoth on 2011-04-02
Well, if you're going away one more question, is there a data output for stream, So that I can get what's playing on the internet radio

---

### Post by vehemoth on 2011-04-02
How do you write a template, my template causes unknown character issues.

```

${voffset 10}${offset 80}${font }${color slate grey}Track: ${color}[--datatype=TN]
${voffset 10}${offset 80}${color slate grey}Time: ${color}[--datatype=PT]
${voffset -13}${offset 190}${color}/[--datatype=LE]
${voffset 20}${color slate grey}Track: ${color}[--datatype=TI]
${color slate grey}Artist: ${color}[--datatype=AR]
${color slate grey}Album: ${color}[--datatype=AL]
${color slate grey}Genre: ${color}[--datatype=GE]
${color slate grey}Status: ${color}[--datatype=ST]
${color slate grey}Volume: ${color}[--datatype=VO]

```

---

### Post by vehemoth on 2011-04-02
> **vehemoth said:**
> How do you write a template, my template causes unknown character issues.

```

${voffset 10}${offset 80}${font }${color slate grey}Track: ${color}[--datatype=TN]
${voffset 10}${offset 80}${color slate grey}Time: ${color}[--datatype=PT]
${voffset -13}${offset 190}${color}/[--datatype=LE]
${voffset 20}${color slate grey}Track: ${color}[--datatype=TI]
${color slate grey}Artist: ${color}[--datatype=AR]
${color slate grey}Album: ${color}[--datatype=AL]
${color slate grey}Genre: ${color}[--datatype=GE]
${color slate grey}Status: ${color}[--datatype=ST]
${color slate grey}Volume: ${color}[--datatype=VO]

```

It was caused by the other lines of code in there, the stuff other than [--datatype=eg]

---

### Post by vehemoth on 2011-04-02
Is the problem with parsing new line characters caused by your script, conky or something else?

---

### Post by vehemoth on 2011-04-03
Can i seperate the %st (stream) part from the rest of the title when listening to internet radio

---

### Post by kaivalagi on 2011-04-03
An easy way to determine whether conky has an issue or the script does is to the run the script in the command line instead of conky, and add the --verbose option on the end.

Give that a go as I am a little blind right now, you've not actually posted the errors just descriptively what you've seen...the template looks to be okay but I have not tested it.

For certain characters it is required that the UTF8 character set is configured for use in Conky. If UTF8 is not enabled you can end up seeing nonsense output. To enable UTF8 the following should be added before the TEXT section in your conkyrc file:
```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
```

You may also want to post your conkyrc if you're still stuck

---

### Post by quillerszasza on 2011-04-05
Hi people!

I'm using the following script for displaying album art:

```
${exec conkyRhythmbox --datatype=AR --nounknownoutput}
${exec conkyRhythmbox --datatype=TI --nounknownoutput}
${exec conkyRhythmbox --datatype=PT --nounknownoutput} / ${exec conkyRhythmbox --datatype=LE --nounknownoutput}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/szasza/.album}${image /home/szasza/.album -p 166,810 -s 64x64}
```

It is working fine ... when there is an album art in Rhythmbox. If not, it displays the previous album's (or the previous previous album's) cover. How can I get it show a - let's say - "noalbum.jpg" instead, or display nothing at all?

By the way, many many thanks for your great work!
Quiller

---

### Post by merlin_ie on 2011-04-05
> **quillerszasza said:**
> Hi people!

I'm using the following script for displaying album art:

```
${exec conkyRhythmbox --datatype=AR --nounknownoutput}
${exec conkyRhythmbox --datatype=TI --nounknownoutput}
${exec conkyRhythmbox --datatype=PT --nounknownoutput} / ${exec conkyRhythmbox --datatype=LE --nounknownoutput}
${exec cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" /home/szasza/.album}${image /home/szasza/.album -p 166,810 -s 64x64}
```

It is working fine ... when there is an album art in Rhythmbox. If not, it displays the previous album's (or the previous previous album's) cover. How can I get it show a - let's say - "noalbum.jpg" instead, or display nothing at all?

By the way, many many thanks for your great work!
Quiller

i know the following link is for Amarok, but it in principal it should fit your needs : [http://www.larryni.me.uk/blog/2009/10/18/display-amarok-album-art-in-conky/]("http://www.larryni.me.uk/blog/2009/10/18/display-amarok-album-art-in-conky/")

let me know if it helps..not near Ubuntu machine at moment so this is all i can think of

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by makroelektro on 2011-05-08
...Sloved

---

### Post by vehemoth on 2011-05-12
Hello
I've got a problem when dealing with album art that has utf8 characters in the filepath. "conkyRhythmbox -d CA" won't copy it.

Also is there a way to just get the path to the album art rather than copying it to the set director
Thanks

---

### Post by Sector11 on 2011-05-12
> **vehemoth said:**
> Hello
I've got a problem when dealing with album art that has utf8 characters in the filepath. "conkyRhythmbox -d CA" won't copy it.

Also is there a way to just get the path to the album art rather than copying it to the set director
Thanks

A shot in the dark, I dont use rhythmbox but do you have:

```
override_utf8_locale yes  # Force UTF8? requires XFT
TEXT
```
Set above TEXT?

Can you show a sample of the path?  That might help.

---

### Post by vehemoth on 2011-05-15
> **Sector11 said:**
> A shot in the dark, I dont use rhythmbox but do you have:

```
override_utf8_locale yes  # Force UTF8? requires XFT
TEXT
```Set above TEXT?

Can you show a sample of the path?  That might help.

Yes I do, as it displays the album text just not the image. Here's that example path
~/Music/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100; -- Jamendo - OGG Vorbis q7 - 2011.03.20 [[www.jamendo.com]](www.jamendo.com])

---

### Post by kaivalagi on 2011-05-16
> **vehemoth said:**
> Yes I do, as it displays the album text just not the image. Here's that example path
~/Music/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100; -- Jamendo - OGG Vorbis q7 - 2011.03.20 [[www.jamendo.com]](www.jamendo.com])

Would the above be a good example file path to an image that I could mock up? If not give me something to go on as far as cover art filepath for the copy

No promises as I have very little time available right now but I suspect it relates to the shutil utility which I use to copy the files...


These are the lines of code responsible for the copy:
```
                    else:
                        self.logInfo("Copying coverart from %s to %s"%(self.musicData.coverart, self.options.coverartpath))
                        [COLOR="Red"]**shutil.copy(self.musicData.coverart, self.options.coverartpath)**[/COLOR]
                        self.musicData.coverart = self.options.coverartpath                        
                        output = self.musicData.coverart
```

Maybe you could find an alternative to what is in red above if you are waiting for a proper fix from me?

---

### Post by vehemoth on 2011-05-16
> **kaivalagi said:**
> Would the above be a good example file path to an image that I could mock up? If not give me something to go on as far as cover art filepath for the copy

No promises as I have very little time available right now but I suspect it relates to the shutil utility which I use to copy the files...


These are the lines of code responsible for the copy:
```
                    else:
                        self.logInfo("Copying coverart from %s to %s"%(self.musicData.coverart, self.options.coverartpath))
                        [COLOR=Red]**shutil.copy(self.musicData.coverart, self.options.coverartpath)**[/COLOR]
                        self.musicData.coverart = self.options.coverartpath                        
                        output = self.musicData.coverart
```Maybe you could find an alternative to what is in red above if you are waiting for a proper fix from me?

Yeah, that was one of the albums that wasn't working for me, I think it's the non ascii characters.
[http://www.jamendo.com/en/artist/Artist_%28356%29](http://www.jamendo.com/en/artist/Artist_%28356%29) You can download that album for free to test it if you want.

---

### Post by kaivalagi on 2011-05-16
Sorry but I don't use Rhythmbox normally these days and trying to get cover art to even be found is proving difficult....I doubt I can get this working without spending quite a bit of time on RB to begin with.

What I have attempted is to provide what the path would likely be found as in the script to see what the copy command would do....it copies the cover art fine e.g:
```
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Copying coverart from /home/USER/Music/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;.jpg to /tmp/cover
```

Do you get an error when running in the terminal window with the --verbose option?

I wonder whether this is a cover art not being even discovered rather than the copy not working?

Can you post the --verbose output from the script when run it with one of those tracks playing e.g. what you get from this in a console:

```
conkyRhythmbox --datatype=CA --verbose
```

P.S. Interesting guitar player...I am not so keen on standard rock but track 5 (&#1044;&#1080;&#1088;&#1080;&#1078;&#1072;&#1073;&#1083;&#1100;) was listened to more than once...

---

### Post by vehemoth on 2011-05-17
Yeah sometimes I just get albums for the one song, but I like a bit of his stuff.

Here's that output
```

*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Copying coverart from /home/vehemoth/Music/ogg/Ð&#154;Ð¾Ð½ÑÑ&#130;Ð°Ð½Ñ&#130;Ð¸Ð½ - Ð&#154;Ð¾Ð½ÑÑ&#130;Ð°Ð½Ñ&#130;Ð¸Ð½Ð¾Ð¿Ð¾Ð»Ñ&#140; -- Jamendo - OGG Vorbis q7 - 2011.03.20 [www.jamendo.com]/[cover] Ð&#154;Ð¾Ð½ÑÑ&#130;Ð°Ð½Ñ&#130;Ð¸Ð½ - Ð&#154;Ð¾Ð½ÑÑ&#130;Ð°Ð½Ñ&#130;Ð¸Ð½Ð¾Ð¿Ð¾Ð»Ñ&#140;.jpg to /tmp/cover
Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 224, in getOutputData
    shutil.copy(self.musicData.coverart, self.options.coverartpath)
  File "/usr/lib/python2.6/shutil.py", line 84, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 50, in copyfile
    with open(src, 'rb') as fsrc:
IOError: [Errno 2] No such file or directory: u'/home/vehemoth/Music/ogg/\xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd - \xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd\xd0\xbe\xd0\xbf\xd0\xbe\xd0\xbb\xd1\x8c -- Jamendo - OGG Vorbis q7 - 2011.03.20 [www.jamendo.com]/[cover] \xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd - \xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd\xd0\xbe\xd0\xbf\xd0\xbe\xd0\xbb\xd1\x8c.jpg'
ERROR: Unknown error when calling getOutputData:[Errno 2] No such file or directory: u'/home/vehemoth/Music/ogg/\xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd - \xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd\xd0\xbe\xd0\xbf\xd0\xbe\xd0\xbb\xd1\x8c -- Jamendo - OGG Vorbis q7 - 2011.03.20 [www.jamendo.com]/[cover] \xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd - \xd0\x9a\xd0\xbe\xd0\xbd\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd1\x82\xd0\xb8\xd0\xbd\xd0\xbe\xd0\xbf\xd0\xbe\xd0\xbb\xd1\x8c.jpg'

```

---

### Post by kaivalagi on 2011-05-17
Ouch, it really screwed up that text....even before the copy...it must relate to the unquote call then

```
coverart = urllib.unquote(coverart).replace("file://","")
```

....not sure what I can do about this :confused:

Can you comment out the above line from your /usr/share/conkyrhythmbox/conkyRhythmboxbox.py file with a # then try again?

It will break still as it wont be able to copt the original file due to an invalid path, but the verbose output from it might give me more to go on...

Cheers

---

### Post by vehemoth on 2011-05-17
I think I got the right line, this is the output then.

```

  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 185
    genre = props["genre"]                            
    ^
IndentationError: expected an indented block

```

And if I did it from the else statement this is what you get.
```

*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Copying coverart from file:///home/vehemoth/Music/ogg/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C%20--%20Jamendo%20-%20OGG%20Vorbis%20q7%20-%202011.03.20%20%5Bwww.jamendo.com%5D/%5Bcover%5D%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C.jpg to /tmp/cover
Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 224, in getOutputData
    shutil.copy(self.musicData.coverart, self.options.coverartpath)
  File "/usr/lib/python2.6/shutil.py", line 84, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 50, in copyfile
    with open(src, 'rb') as fsrc:
IOError: [Errno 2] No such file or directory: dbus.String(u'file:///home/vehemoth/Music/ogg/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C%20--%20Jamendo%20-%20OGG%20Vorbis%20q7%20-%202011.03.20%20%5Bwww.jamendo.com%5D/%5Bcover%5D%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C.jpg', variant_level=1)
ERROR: Unknown error when calling getOutputData:[Errno 2] No such file or directory: dbus.String(u'file:///home/vehemoth/Music/ogg/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C%20--%20Jamendo%20-%20OGG%20Vorbis%20q7%20-%202011.03.20%20%5Bwww.jamendo.com%5D/%5Bcover%5D%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C.jpg', variant_level=1)

```

Is it on Ubuntu 11.04 that it works fine, I don't know if it will help but I'm running debian squeeze.

---

### Post by kaivalagi on 2011-05-18
Well the unquote works for the file path e.g. this:

```
file:///home/vehemoth/Music/ogg/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C%20--%20Jamendo%20-%20OGG%20Vorbis%20q7%20-%202011.03.20%20%5Bwww.jamendo.com%5D/%5Bcover%5D%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C.jpg
```

becomes this:

```
/home/vehemoth/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100; -- Jamendo - OGG Vorbis q7 - 2011.03.20 [www.jamendo.com]/[cover] &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;.jpg
```

this tells me that the original filecopy error of "No such file or directory" is due to maybe characters that need escaping but aren't?

We could try copying the file in the console using this (or similar):

```
cp /home/vehemoth/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100; -- Jamendo - OGG Vorbis q7 - 2011.03.20 [www.jamendo.com]/[cover] coverart-test.jpg
```

If there is an issue with the copy itself we can find out what and correct for me...,maybe those "[" / "]" characters are to blame and they need a "\" insfront maybe? Not sure as I have to have my breakfast and get to work ;)

---

### Post by vehemoth on 2011-05-19
> **kaivalagi said:**
> Well the unquote works for the file path e.g. this:

```
file:///home/vehemoth/Music/ogg/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C%20--%20Jamendo%20-%20OGG%20Vorbis%20q7%20-%202011.03.20%20%5Bwww.jamendo.com%5D/%5Bcover%5D%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C.jpg
```becomes this:

```
/home/vehemoth/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100; -- Jamendo - OGG Vorbis q7 - 2011.03.20 [www.jamendo.com]/[cover] &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;.jpg
```this tells me that the original filecopy error of "No such file or directory" is due to maybe characters that need escaping but aren't?

We could try copying the file in the console using this (or similar):

```
cp /home/vehemoth/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100; -- Jamendo - OGG Vorbis q7 - 2011.03.20 [www.jamendo.com]/[cover] coverart-test.jpg
```If there is an issue with the copy itself we can find out what and correct for me...,maybe those "[" / "]" characters are to blame and they need a "\" insfront maybe? Not sure as I have to have my breakfast and get to work ;)

I don't think that's the issue as almost all if not all my music has those characters in the folder name. It just seems to be the music with non ascii characters that are doing it.

---

### Post by Sector11 on 2011-05-19
I have been watching this with some interest, so I grabbed the album with thoughts if installing Rhythembox and trying to help.

First thing I did was open it with VLC, where I see the name of the Artist and the song, and the cover Art:
[[img]http://dl.dropbox.com/u/16070765/thmb_&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;.png[/img]](http://dl.dropbox.com/u/16070765/full_&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;.png)
Man can he ever pluck those strings.....
The cover art is called:
> %5Bcover%5D%20%C3%90%C2%9A%C3%90%C2%BE%C3%90%C2%BD%C3%91%C2%81%C3%91%C2%82%C3%90%C2%B0%C3%90%C2%BD%C3%91%C2%82%C3%90%C2%B8%C3%90%C2%BD%20-%20%C3%90%C2%9A%C3%90%C2%BE%C3%90%C2%BD%C3%91%C2%81%C3%91%C2%82%C3%90%C2%B0%C3%90%C2%BD%C3%91%C2%82%C3%90%C2%B8%C3%90%C2%BD%C3%90%C2%BE%C3%90%C2%BF%C3%90%C2%BE%C3%90%C2%BB%C3%91%C2%8C.jpg


I got to thinking and thought why not ---- I renamed the cover art
[[img]http://dl.dropbox.com/u/16070765/thmb_&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;_2.png[/img]](http://dl.dropbox.com/u/16070765/full_&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;_2.png)
> [cover] &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;.jpg
As you see - it works too.

What happens if you do that and run it in Rhythembox?

Sometimes - simple - works best!  Lets hope this is one of them.

EDIT:  I agree with Mark #5 is great!!!!!

---

### Post by vehemoth on 2011-05-19
> **Sector11 said:**
> I have been watching this with some interest, so I grabbed the album with thoughts if installing Rhythembox and trying to help.

First thing I did was open it with VLC, where I see the name of the Artist and the song, and the cover Art:
[[IMG]http://dl.dropbox.com/u/16070765/thmb_%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD.png[/IMG]]("http://dl.dropbox.com/u/16070765/full_%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD.png")
Man can he ever pluck those strings.....
The cover art is called:


I got to thinking and thought why not ---- I renamed the cover art
[[IMG]http://dl.dropbox.com/u/16070765/thmb_%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD_2.png[/IMG]]("http://dl.dropbox.com/u/16070765/full_%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD_2.png")

As you see - it works too.

What happens if you do that and run it in Rhythembox?

Sometimes - simple - works best!  Lets hope this is one of them.

EDIT:  I agree with Mark #5 is great!!!!!

I can only get it working in rhythmbox if the cover is named with both the artist and the album.

---

### Post by Sector11 on 2011-05-20
> **vehemoth said:**
> I can only get it working in rhythmbox if the cover is named with both the artist and the album.



Try a test:

Create a new folder:
/home/vehemoth/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;

And copy everything in:
```
file:///home/vehemoth/Music/ogg/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C%20--%20Jamendo%20-%20OGG%20Vorbis%20q7%20-%202011.03.20%20%5Bwww.jamendo.com%5D
```
to it. 

Now rename:
```
%5Bcover%5D%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C.jpg
```
to:
```
[cover] &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;.jpg
```

And try playing that.

I realize that it's not helping with the conkyRhythmbox box problem but it might get it working and the problem fix can come later.

Does Rhythmbox have any problems with playing the album at all?

---

### Post by vehemoth on 2011-05-20
> **Sector11 said:**
> Try a test:

Create a new folder:
/home/vehemoth/ogg/&#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;

And copy everything in:
```
file:///home/vehemoth/Music/ogg/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C%20--%20Jamendo%20-%20OGG%20Vorbis%20q7%20-%202011.03.20%20%5Bwww.jamendo.com%5D
```to it. 

Now rename:
```
%5Bcover%5D%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C.jpg
```to:
```
[cover] &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; - &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085;&#1086;&#1087;&#1086;&#1083;&#1100;.jpg
```And try playing that.

I realize that it's not helping with the conkyRhythmbox box problem but it might get it working and the problem fix can come later.

Does Rhythmbox have any problems with playing the album at all?

I don't see what you are getting at, they are both the same, ones just converting the characters that aren't letters or numbers into a different format.

---

### Post by vehemoth on 2011-05-20
How about this, I downloaded all of the albums by these people [http://www.jamendo.com/en/artist/distemper](http://www.jamendo.com/en/artist/distemper). I copied the folders into my music directory. Rhythmbox plays them all fine and shows the album art, however conkyRhythmbox only shows the album art from their albums that don't have Russian names.

---

### Post by Sector11 on 2011-05-20
> **vehemoth said:**
> How about this, I downloaded all of the albums by these people [http://www.jamendo.com/en/artist/distemper](http://www.jamendo.com/en/artist/distemper). I copied the folders into my music directory. Rhythmbox plays them all fine and shows the album art, however conkyRhythmbox only shows the album art from their albums that don't have Russian names.

Re my last post, I was just wondering if by changing all the characters it might work.

And it look like conkyRhythmbox can't handle the Russian character set and possibly other languages.  Or more to the point the "shutil utility" that conkyRhythmbox uses.

Time to dig ...

---

### Post by kaivalagi on 2011-05-21
If the normal copy command works for these files using the same text that would be used (printed to screen in verbose output) then it is just shutil.copy at fault....if we can determine this then we can look at alternatives to the one line which does the copying of the file...

---

### Post by Sector11 on 2011-05-21
> **kaivalagi said:**
> If the normal copy command works for these files using the same text that would be used (printed to screen in verbose output) then it is just shutil.copy at fault....if we can determine this then we can look at alternatives to the one line which does the copying of the file...

That first part got me thinking: > **kaivalagi said:**
> If the normal copy command works for these files using the same text that would be used...... so I wenk looking in: [The Python Standard Library]("http://docs.python.org/library/index.html") I don't see anything with else with [shutil]("http://docs.python.org/library/shutil.html") that might help.

BUT, what about popping out to a shell and doing the copy with the ["pipes module"]("http://docs.python.org/library/pipes.html")?

Even that last one in 35.11.1. Template Objects (same page) looks promising:
Template.copy(infile, outfile)
    Copy infile to outfile through the pipe.

Just trying to help....

---

### Post by kaivalagi on 2011-05-21
> **Sector11 said:**
> Just trying to help....

Thanks

If the copy works through the terminal I can use the shell with something like the following function, this one gives me the output so if nothing is returned I can assume it worked I think:


```
    def getShellCommandOutput(self, shell_command):

        self.logInfo("Running shell command '%s'"%shell_command)

        proc = subprocess.Popen(shell_command,
                           shell=True,
                           stdout=subprocess.PIPE,
                           )
        output = proc.communicate()[0].rstrip("\n")

        return output

```

edit: Find attached an updated script for you guys to try, not tested yet!

Rather than copy the file it made more sense to sym link it, so I've used the following code:

```
                elif datatype == "CA": #coverart
                    if self.musicData.coverart == None or len(self.musicData.coverart) == 0:
                        output = None
                    else:
                        #self.logInfo("Copying coverart from %s to %s"%(self.musicData.coverart, self.options.coverartpath))
                        #shutil.copy(self.musicData.coverart, self.options.coverartpath)
                        self.logInfo("Linking coverart from %s to %s"%(self.musicData.coverart, self.options.coverartpath))
                        linkcmd = "ln -s %s %s"%(self.musicData.coverart, self.options.coverartpath)
                        self.getShellCommandOutput(linkcmd)
                       
                        self.musicData.coverart = self.options.coverartpath                        
                        output = self.musicData.coverart
```

The attached has the added code and required subprocess imports too

Fingers crossed that sorts it...let me know ;)

---

### Post by Sector11 on 2011-05-21
> **kaivalagi said:**
> Thanks

The attached has the added code and required subprocess imports too

Fingers crossed that sorts it...let me know ;)

OK, I broke down and installed Rhythmbox and conkyRhythmbox and grabbed the latest above and copied it over the repo version, extracted the Album to:
```
file:///media/5/Music/%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%20-%20%D0%9A%D0%BE%D0%BD%D1%81%D1%82%D0%B0%D0%BD%D1%82%D0%B8%D0%BD%D0%BE%D0%BF%D0%BE%D0%BB%D1%8C
```
that looks like:
[[img]http://dl.dropbox.com/u/16070765/thmb_looks-like.png[/img]](http://dl.dropbox.com/u/16070765/full_looks-like.png)

The files:
```
Readme%20-%20www.jamendo.com%20.txt


License.txt


10%20-%20%C3%90%C2%9F%C3%90%C2%BE%C3%91%C2%89%C3%90%C2%B5%C3%91%C2%87%C3%90%C2%B8%C3%90%C2%BD%C3%90%C2%B0.mp3


09%20-%20%C3%90%C2%9F%C3%90%C2%B5%C3%91%C2%80%C3%90%C2%B5%C3%90%C2%BA%C3%91%C2%80%C3%90%C2%B5%C3%91%C2%81%C3%91%C2%82%C3%90%C2%BE%C3%90%C2%BA.mp3


08%20-%20%C3%90%C2%9C%C3%91%C2%8B%C3%91%C2%81%C3%90%C2%BB%C3%90%C2%B8.mp3


07%20-%20%C3%90%C2%9C%C3%90%C2%B8%C3%90%C2%B3.mp3


06%20-%20%C3%90%C2%94%C3%91%C2%83%C3%91%C2%88%C3%90%C2%B0.mp3


05%20-%20%C3%90%C2%94%C3%90%C2%B8%C3%91%C2%80%C3%90%C2%B8%C3%90%C2%B6%C3%90%C2%B0%C3%90%C2%B1%C3%90%C2%BB%C3%91%C2%8C.mp3


04%20-%20love.mp3


03%20-%20In%20this%20wild%20world.mp3


02%20-%20%C3%90%C2%A0%C3%90%C2%BE%C3%91%C2%82%C3%90%C2%B0.mp3


01%20-%20%C3%90%C2%BC%C3%90%C2%BE%C3%91%C2%80%C3%90%C2%B5.mp3


%5Bcover%5D%20%C3%90%C2%9A%C3%90%C2%BE%C3%90%C2%BD%C3%91%C2%81%C3%91%C2%82%C3%90%C2%B0%C3%90%C2%BD%C3%91%C2%82%C3%90%C2%B8%C3%90%C2%BD%20-%20%C3%90%C2%9A%C3%90%C2%BE%C3%90%C2%BD%C3%91%C2%81%C3%91%C2%82%C3%90%C2%B0%C3%90%C2%BD%C3%91%C2%82%C3%90%C2%B8%C3%90%C2%BD%C3%90%C2%BE%C3%90%C2%BF%C3%90%C2%BE%C3%90%C2%BB%C3%91%C2%8C.jpg

```
A picture is worth a 1000 words ....
[[img]http://dl.dropbox.com/u/16070765/thmb_not-yet.png[/img]](http://dl.dropbox.com/u/16070765/full_not-yet.png)

No Coverart - but my #! pop-up notifier show it perfect as does the mouse over Rhythmbox icon action in the tint2 panel.

{sigh} - good music though - but then, I'm a blues fan.

The conky & template are modified from the Examples
**conky:**
```
# conky configuration
# edited by kaivalagi

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont monospace:size=9  ####  changed font

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 1000
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 0 ### needs "_inner_" or "_outer_" now to work

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment top_left         #### changes

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 10

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

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

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
text_buffer_size 3048 ###  I needed to add this

TEXT
${color4}${font monospace:style=Bold:size=14}@ ${font monospace:style=Bold:size=11}Rhythmbox${font}

${color4}Template Output:
${color1}${execp conkyRhythmbox --template=~/conky/rb/conkyRhythmbox.template}
```

**~/conky/rb/conkyRhythmbox.template**
```
  Status: [--datatype=ST]
  Artist: [--datatype=AR]
   Album: [--datatype=AL]
   Title: [--datatype=TI]
Position: [--datatype=PT] / [--datatype=LE] [--datatype=PP]%
  Rating: [--datatype=RT]
  Volume: [--datatype=VO]

      YR: [--datatype=YR]
Track No: [--datatype=TN] 

Cover:${image [--datatype=CA] -p 0,235 -s 100x100}
## note 7 blank lines for image







```

---

### Post by kaivalagi on 2011-05-21
mmmmm, I'm assuming this:

```
override_utf8_locale no
```

changed to this:

```
override_utf8_locale yes
```

will get the text looking right?

I need to play when I get time....need to see what sym link is created if any and what the command response is...

---

### Post by Sector11 on 2011-05-21
> **kaivalagi said:**
> mmmmm, I'm assuming this:

```
override_utf8_locale no
```

changed to this:

```
override_utf8_locale yes
```

will get the text looking right?

I need to play when I get time....need to see what sym link is created if any and what the command response is...

DARN IT, Batman!!!  I missed that, I am so use to having it set as yes ....  changed it and I get:

```
  19:06 ~
         $ conky -c ~/conky/rb/conkyrc
Conky: desktop window (1ad) is root window
Conky: window type - override
Conky: drawing to created window (0x1800001)
Conky: drawing to double buffer
Conky: Unable to load image '-p'
```

[[img]http://dl.dropbox.com/u/16070765/thmb_no-cover-text.png[/img]](http://dl.dropbox.com/u/16070765/full_no-cover-text.png)

--- NEXT!

---

### Post by vehemoth on 2011-05-22
Now I get no cover art. I used the latest deb and sudo cp to get that .py into /usr/share/conkyrhythmbox, I then logged out and back in, that was all.
When rhythmbox gets the coverart it seems to take it from the folder of the current song, so long as it matches the artist and album in the metadata in the music file.

If it helps here is my conky, it is 1.8.0 (I think)

```

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_hints undecorated,below,skip_taskbar
background no
maximum_width 300

####
## Default sizes
#
default_bar_size 200 6

####
## Force images to redraw when they change.
#
imlib_cache_size 0

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 300 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 960
gap_y 40

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale
xftfont Terminus:size=8
xftalpha 0.8

#lua_load /home/linus/scripts/.draw_bg.lua
#lua_load /home/vehemoth/.conky/bargraph_small.lua
##lua_load /home/vehemoth/.conky/bargraph_small2.lua
#lua_draw_hook_pre draw_bg
##lua_draw_hook_post main_bars

TEXT
${image /home/vehemoth/.conky/debian.png -p 25,5}
${voffset -6}${offset 205}${color d60651}${font Terminus:size=30}6.0
${voffset -25}${offset 60}${color grey}${font Terminus:size=8.3}THE UNIVERSAL OPERATING SYSTEM

${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}System${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
${color slate grey}Kern:${color }$kernel
${voffset -13}${offset 150}${color slate grey}UpTime: ${color }$uptime
${color slate grey}Domain Name:${color }$nodename
${voffset -13}${offset 150}${color slate grey}SysName: ${color }$sysname

${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}Processors${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
${color slate grey}CPU:${color } $cpu%
${voffset -13}${offset 80}${color}${freq}MHz
${voffset -13}${offset 136}${color slate grey}Core 1:${color }${cpu cpu1}%
${voffset -13}${offset 220}${color slate grey}Core 2:${color }${cpu cpu2}%
${cpugraph 20,130 000000 ffffff}  ${color }${cpugraph cpu1 20,78 000000 ffffff}  ${color }${cpugraph cpu2 20,78 000000 ffffff}
${color slate grey}Processes:${color }$processes
${voffset -13}${offset 130}${color slate grey}Running:${color }$running_processes
${voffset -13}${offset 220}${color slate grey}Threads:${color }$running_threads

${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}Memory${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${membar 3,100}
${voffset -26}${offset 164}${color slate grey}SWAP:  ${color }$swapperc% $swap/$swapmax
${offset 164}${swapbar 3,100}

${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}HDD${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${fs_bar 3,100 /}
${voffset -26}${offset 164}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 164}${fs_bar 3,100 /home}

${color slate grey}Disk I/O:${color }${diskio}
${voffset -13}${offset 136}${color slate grey}I/R:${color }${diskio_read}
${voffset -13}${offset 220}${color slate grey}O/W:${color }${diskio_write}
${diskiograph 20,130 000000 ffffff}  ${diskiograph_read 20,78 000000 ffffff}  ${diskiograph_write 20,78 000000 ffffff}

${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}Top Processes${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
${color slate grey}Highest CPU:
${color ddaa00} ${top name 1}
${color lightgrey} ${top name 2}
${color lightgrey} ${top name 3}
${color lightgrey} ${top name 4}
${voffset -52}${offset 105}${color ddaa00}${top cpu 1}
${offset 105}${color lightgrey}${top cpu 2}
${offset 105}${color lightgrey}${top cpu 3}
${offset 105}${color lightgrey}${top cpu 4}

${voffset -78}${offset 145}${color slate grey}Highest MEM:
${offset 145}${color ddaa00} ${top_mem name 1}
${offset 145}${color lightgrey} ${top_mem name 2}
${offset 145}${color lightgrey} ${top_mem name 3}
${offset 145}${color lightgrey} ${top_mem name 4}
${voffset -52}${offset 270}${color ddaa00}${top_mem mem 1}
${offset 270}${color lightgrey}${top_mem mem 2}
${offset 270}${color lightgrey}${top_mem mem 3}
${offset 270}${color lightgrey}${top_mem mem 4}

${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}Network${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
${color slate grey}Internal IP: ${color}${addr eth0}
${voffset -13}${offset 152}${color slate grey}External IP: ${color }${execi 3600 /home/vehemoth/.conky/wan.sh}
${color slate grey}Up: ${color }${upspeed eth0}
${voffset -13}${offset 152}${color slate grey}Down: ${color }${downspeed eth0}
${color}${upspeedgraph eth0 20,146 000000 ffffff}  ${downspeedgraph eth0 20,146 000000 ffffff}
${color slate grey}Connections:${color }${tcp_portmon 1 32767 count} in / ${tcp_portmon 32768 61000 count} out ${alignr} ${color slate grey}Service/Port:${color}
${voffset 5}${tcp_portmon 1 65535 rhost 0} ${alignr} ${tcp_portmon 1 65535 rservice 0} ${color ddaa00}${tcp_portmon 1 65535 rport 0}${color}
${tcp_portmon 1 65535 rhost 1} ${alignr} ${tcp_portmon 1 65535 rservice 1} ${color ddaa00}${tcp_portmon 1 65535 rport 1}${color}
${tcp_portmon 1 65535 rhost 2} ${alignr} ${tcp_portmon 1 65535 rservice 2} ${color ddaa00}${tcp_portmon 1 65535 rport 2}${color}
${tcp_portmon 1 65535 rhost 3} ${alignr} ${tcp_portmon 1 65535 rservice 3} ${color ddaa00}${tcp_portmon 1 65535 rport 3}${color}
${tcp_portmon 1 65535 rhost 4} ${alignr} ${tcp_portmon 1 65535 rservice 4} ${color ddaa00}${tcp_portmon 1 65535 rport 4}${color}

${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}Time${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
${voffset -4}${font Terminus:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
${font :size=10}${voffset 3}${alignc}${color ddaa00}${time %a,}${time %e %B %G}${voffset -15}

##################
##  RHYTHMBOX   ##
##################
${if_running rhythmbox}${font WenQuanYiMicroHei:bold:size=8.70}${color 4b74b4}Now Playing${color slate grey}${offset 8}${voffset -2}${hr 2}${font}${voffset 7}
#Down to business
${exec ~/.conky/rhythmbox-ca.sh}${image /tmp/cover -p 0,780 -s 64x64}
${execp conkyRhythmbox --template=/home/vehemoth/.conky/first.template}
${execp conkyRhythmbox --template=/home/vehemoth/.conky/second.template}
${execp conkyRhythmbox --template=/home/vehemoth/.conky/third.template}
${voffset -75}${offset 78}${execbar conkyRhythmbox --datatype=PP}
${endif}

```rhythmbox-ca.sh
```

#!/bin/bash
if test `conkyRhythmbox --datatype=CA`;
then
    return
else
    cp /home/vehemoth/.conky/none.png /tmp/cover
fi

```and here is the verbose output of the CA datatype.

```

*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Linking coverart from /home/vehemoth/Music/ogg/Atomic cat - Trance Imagination -- Jamendo - OGG Vorbis q7 - 2010.07.19 [www.jamendo.com]/[cover] Atomic cat - Trance Imagination.jpg to /tmp/cover
Traceback (most recent call last):
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 228, in getOutputData
    self.getShellCommandOutput(linkcmd)
  File "/usr/share/conkyrhythmbox/conkyRhythmbox.py", line 479, in getShellCommandOutput
    self.logger.info("Running shell command '%s'"%shell_command)
AttributeError: RhythmboxInfo instance has no attribute 'logger'
ERROR: Unknown error when calling getOutputData:RhythmboxInfo instance has no attribute 'logger'

```

---

### Post by kaivalagi on 2011-05-22
There was a bug in the tarballed py I posted recently, replace any "self.logger.info" for "self.logInfo"...there should be one in the new function I added...doh

edit: attached zip with edited file (not on a linux box hence the .zip)

---

### Post by Sector11 on 2011-05-22
> **kaivalagi said:**
> There was a bug in the tarballed py I posted recently, replace any "self.logger.info" for "self.logInfo"...there should be one in the new function I added...doh

edit: attached zip with edited file (not on a linux box hence the .zip)

Grabbed that and tried it ...
[[img]http://dl.dropbox.com/u/16070765/thmb_latest.png[/img]](http://dl.dropbox.com/u/16070765/full_latest.png)
Still get the [] vs the names.

and:
```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes   ###  CHANGED
```
Also, not shown, no errors reported in terminal and no image.

---

### Post by vehemoth on 2011-05-23
Okay, I can't do python so here is the output (maybe you need to put speech mark things ' around the ln command, e.g. ln -s '/home/cover' )

```

*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Linking coverart from /home/vehemoth/Music/ogg/Magdalen Graal - Magdalen Graal -- Jamendo - OGG Vorbis q7 - 2010.03.08 [www.jamendo.com]/[cover] Magdalen Graal - Magdalen Graal.jpg to /tmp/cover
INFO: Running shell command 'ln -s /home/vehemoth/Music/ogg/Magdalen Graal - Magdalen Graal -- Jamendo - OGG Vorbis q7 - 2010.03.08 [www.jamendo.com]/[cover] Magdalen Graal - Magdalen Graal.jpg /tmp/cover'
ln: target `/tmp/cover' is not a directory
/tmp/cover

```

---

### Post by kaivalagi on 2011-05-23
Needs quotes around the paths atleast I'd say...not sure when I'll get to play again with this in the short term...it might have to wait until next weekend

---

### Post by Sector11 on 2011-05-23
Here is my conky, as I said, a modified conkyRhythmbox Example as is my template:
```
# conky configuration
# edited by kaivalagi
# killall conky && conky -c ~/conky/rb/conkyrc

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont monospace:size=9  ####  changed font

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 1000
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 0 ### needs "_inner_" or "_outer_" now to work

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment top_left         #### changes

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 100
gap_y 100

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes   ###  CHANGED

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

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

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
text_buffer_size 3048 ###  I needed to add this

TEXT
${color4}${font monospace:style=Bold:size=14}@ ${font monospace:style=Bold:size=11}Rhythmbox${font}

${color1}${execp conkyRhythmbox --template=~/conky/rb/conkyRhythmbox.template}
```

**~/conky/rb/conkyRhythmbox.template**
```
  Status: [--datatype=ST]
  Artist: [--datatype=AR]
   Album: [--datatype=AL]
   Title: [--datatype=TI]
Position: [--datatype=PT] / [--datatype=LE] [--datatype=PP]%
  Rating: [--datatype=RT]
  Volume: [--datatype=VO]

      YR: [--datatype=YR]
Track No: [--datatype=TN] 

Cover:${image [--datatype=CA] -p 0,235 -s 100x100}








```
There are 8 blank lines after:
```
Cover:${image [--datatype=CA] -p 0,235 -s 100x100}
```

The original files are here:
```
/usr/share/conkyrhythmbox/example/conkyRhythmbox.template
/usr/share/conkyrhythmbox/example/conkyrc
```
[[img]http://dl.dropbox.com/u/16070765/thmb_conkyRhythmbox.png[/img]](http://dl.dropbox.com/u/16070765/full_conkyRhythmbox.png)

---

### Post by vehemoth on 2011-05-25
What os are you using,
have you got utf8 enabled in the terminal
did you install the latest version of conkyRhythmbox from the repos
do you have the latest conky

Your conkyrc works on mine so I'd say that the most likely thing is utf8 support in the terminal.

And regarding that "yes" thing, I don't think use_utf8 need yes on the end but check in the conky man pages. I believe that they are also enabled by default so you could delete the line.

---

### Post by Sector11 on 2011-05-25
> **vehemoth said:**
> What os are you using,
have you got utf8 enabled in the terminal
did you install the latest version of conkyRhythmbox from the repos
do you have the latest conky

Your conkyrc works on mine so I'd say that the most likely thing is utf8 support in the terminal.

And regarding that "yes" thing, I don't think use_utf8 need yes on the end but check in the conky man pages. I believe that they are also enabled by default so you could delete the line.
[LIST]
[*]**By works, do you mean you see the cover-art?**
[*]I'm using [#! 10 - Statler]("http://crunchbanglinux.org/"), based on Debian Squeeze.
[*]No DE, maybe that's a problem, just OpenBox.
[*]I have the latest conkyRhythmbox from the repos AND the two that came after that, that kaivalagi edited and posted here in the thread to work on this problem.
[*]I am using conky v1.8.0 - it is enough for this, and it is the same version kaivalagi uses.
[/LIST]

```
override_utf8_locale
 	[COLOR="DarkRed"]**Force UTF8?**[/COLOR] requires XFT
use_xft
 	Use Xft (anti-aliased font and stuff)

xftalpha
 	Alpha of Xft font. Must be a value at or between 1 and 0.

xftfont
 	Xft font to use.
```

If you use "override_utf8_locale yes" you need to have use_xtf yes and xftfont set as I do.

Now this is a new one for me:
> **vehemoth said:**
> have you got utf8 enabled in the terminal
How does one do that?  I use "terminator". I'll have to look that up.

I have also installed "rhythmbox-desktop-art v2.00"

Now, one thing I did notice that when I check the "plugins" (Edit > Plugins) in Rhythmbox it is not accessible.

[[img]http://dl.dropbox.com/u/16070765/thmb_DesktopArt.png[/img]](http://dl.dropbox.com/u/16070765/full_DesktopArt.png)

I thought it was because I do not run a composite manager. Turning on composite manager doesn't help, that option is still not available to me.

However that images explains why the coverart shows in Rhythmbox - it grabs it from the Internet, according to what it says, and turning it off, turns off the cover art.

Just so you know, I have beta tested most of kaivalagi's apps from the beginning, using Ubuntu, Xubuntu and now Debian, not the google stuff though as I don't use those services.  I may not be the smartest person going but I do try everything I can to eliminate problems from "the users point of view".  I am not a programmer, K will tell you that, but sometimes I can look at things and see the "logic" and make changes to fix - OR REALLY BREAK - things.  I've had to re-install my OS more than once because "I" broke it trying things. :D

Everything I've done here is simply to help you.  When the problem is fixed, whether I find the answer, you find the answer or someone else does, I'll remove Rhythmbox, conkyRhythmbox and rhythmbox-desktop-art.

---

### Post by kaivalagi on 2011-05-25
You don't need "rhythmbox-desktop-art v2.00" for a conky only solution as that provides an alternative to conky for cover art output on the desktop...might be the best option though!

For conky all you _should_ need is the cover art plugin enabled to get the cover art sorted as and when then conkyRhythmbox should find it on running....I don't get this though, cover art never comes back for me either. I Rhythmbox v2.90.1 installed, although I only use it for testing the script for others...mpd and sonata for me!

---

### Post by vehemoth on 2011-05-26
> **Sector11 said:**
> 
[LIST]
[*]**By works, do you mean you see the cover-art?**
[*]I'm using [#! 10 - Statler]("http://crunchbanglinux.org/"), based on Debian Squeeze.
[*]No DE, maybe that's a problem, just OpenBox.
[*]I have the latest conkyRhythmbox from the repos AND the two that came after that, that kaivalagi edited and posted here in the thread to work on this problem.
[*]I am using conky v1.8.0 - it is enough for this, and it is the same version kaivalagi uses.
[/LIST]

```
override_utf8_locale
     [COLOR=DarkRed]**Force UTF8?**[/COLOR] requires XFT
use_xft
     Use Xft (anti-aliased font and stuff)

xftalpha
     Alpha of Xft font. Must be a value at or between 1 and 0.

xftfont
     Xft font to use.
```If you use "override_utf8_locale yes" you need to have use_xtf yes and xftfont set as I do.

Now this is a new one for me:

How does one do that?  I use "terminator". I'll have to look that up.

I have also installed "rhythmbox-desktop-art v2.00"

Now, one thing I did notice that when I check the "plugins" (Edit > Plugins) in Rhythmbox it is not accessible.

[[IMG]http://dl.dropbox.com/u/16070765/thmb_DesktopArt.png[/IMG]]("http://dl.dropbox.com/u/16070765/full_DesktopArt.png")

I thought it was because I do not run a composite manager. Turning on composite manager doesn't help, that option is still not available to me.

However that images explains why the coverart shows in Rhythmbox - it grabs it from the Internet, according to what it says, and turning it off, turns off the cover art.

Just so you know, I have beta tested most of kaivalagi's apps from the beginning, using Ubuntu, Xubuntu and now Debian, not the google stuff though as I don't use those services.  I may not be the smartest person going but I do try everything I can to eliminate problems from "the users point of view".  I am not a programmer, K will tell you that, but sometimes I can look at things and see the "logic" and make changes to fix - OR REALLY BREAK - things.  I've had to re-install my OS more than once because "I" broke it trying things. :D

Everything I've done here is simply to help you.  When the problem is fixed, whether I find the answer, you find the answer or someone else does, I'll remove Rhythmbox, conkyRhythmbox and rhythmbox-desktop-art.

I'm not very good at communicating my ideas, sorry.

But I was saying that all of the text showed up fine on my system.
I use debian squeeze, so I'm assuming it's something to do with crunchbang's terminal as the conky and conkyRhythmbox should be the same.

Maybe this page can help you with utf8 support [http://crunchbanglinux.org/forums/topic/408/japanese-input-please-help/](http://crunchbanglinux.org/forums/topic/408/japanese-input-please-help/)

---

### Post by vehemoth on 2011-05-26
> **kaivalagi said:**
> You don't need "rhythmbox-desktop-art v2.00" for a conky only solution as that provides an alternative to conky for cover art output on the desktop...might be the best option though!

For conky all you _should_ need is the cover art plugin enabled to get the cover art sorted as and when then conkyRhythmbox should find it on running....I don't get this though, cover art never comes back for me either. I Rhythmbox v2.90.1 installed, although I only use it for testing the script for others...mpd and sonata for me!

Nothing important, does ubuntu have a different naming because they are only up to rhythmbox 0.13 [http://projects.gnome.org/rhythmbox/](http://projects.gnome.org/rhythmbox/)

---

### Post by Sector11 on 2011-05-26
> **kaivalagi said:**
> You don't need "rhythmbox-desktop-art v2.00" for a conky only solution as that provides an alternative to conky for cover art output on the desktop...might be the best option though!

For conky all you _should_ need is the cover art plugin enabled to get the cover art sorted as and when then conkyRhythmbox should find it on running....I don't get this though, cover art never comes back for me either. I Rhythmbox v2.90.1 installed, although I only use it for testing the script for others...mpd and sonata for me!

OK.  I didn't know that and grabbed it.  Can't hurt.

I get the cover art for ANY album I have (3 now)

[LIST=1]
[*]&#1053;&#1072;&#1089;&#1090;&#1103; &#1071;&#1089;&#1085;&#1072;&#1103; - &#1052;&#1086;&#1103; &#1051;&#1102;&#1073;&#1086;&#1074;&#1100;
[*]Siberian Jungle Vol.2
[*]The Very Best Of Roy Orbison
[/LIST]

... **IN** Rhythmbox, the #! Popup using “zenity" and on the mouse over function when I put the mouse on the Rhythmbox icon in Tint2.

It looks like I'm behind the time: Rhythmbox 0.12.8 from the Debian repos.
How can you have v2.90 the [website]("http://projects.gnome.org/rhythmbox/") says the latest version is:
> The latest stable release is 0.13.3  (changelog, news).

---

### Post by Sector11 on 2011-05-26
> **vehemoth said:**
> I'm not very good at communicating my ideas, sorry.

But I was saying that all of the text showed up fine on my system.
I use debian squeeze, so I'm assuming it's something to do with crunchbang's terminal as the conky and conkyRhythmbox should be the same.

Maybe this page can help you with utf8 support [http://crunchbanglinux.org/forums/topic/408/japanese-input-please-help/](http://crunchbanglinux.org/forums/topic/408/japanese-input-please-help/)

No need to apologize, I had a thought that English was not your native language when I saw the Japanese font: WenQuanYiMicroHei.  I may have been wrong about that but I chose to explain things in full rather than not enough.  And #! 10 based on Debian Squeeze uses the Debian Squeeze repos, so basically we are running the same system.  I know there are die-hard people in the Debian forums that will shoot me down in flames because it's not "pure" but that's a matter of semantics.

Today however I see everything is working - the Russian font and all - EXCEPT the cover art.  Strange, I didn't do anything different, din't install anything!  I've seen that page you linked to as I have two friends married to Japanese ladies.  One living in Japan and one believe it or not in Sweden.  :D

[CENTER][[img]http://dl.dropbox.com/u/16070765/thmb_RB-1.png[/img]](http://dl.dropbox.com/u/16070765/full_RB-1.png)  [[img]http://dl.dropbox.com/u/16070765/thmb_RB-2.png[/img]](http://dl.dropbox.com/u/16070765/full_RB-2.png)

[[img]http://dl.dropbox.com/u/16070765/thmb_RB-3.png[/img]](http://dl.dropbox.com/u/16070765/full_RB-3.png)  [[img]http://dl.dropbox.com/u/16070765/thmb_RB-4.png[/img]](http://dl.dropbox.com/u/16070765/full_RB-4.png)[/CENTER]

So back to the original question - where's the beef? (cover art)

---

### Post by Sector11 on 2011-05-26
> **vehemoth said:**
> Nothing important, does ubuntu have a different naming because they are only up to rhythmbox 0.13 [http://projects.gnome.org/rhythmbox/](http://projects.gnome.org/rhythmbox/)

I missed this, kaivalagi doesn't use Ubuntu anymore, he uses ARCH Linux now. And yes, I have the same question.  He was using Ubuntu when he created these apps and continues to support them.

---

### Post by vehemoth on 2011-05-27
Coverart was broken in those updates you installed after the ones from the ppa, they were broken when he was trying to fix the utf8 support.

English is my native language, I'm just not very good at communicating.

That conky is just a heavily modified one from the .conkyrc thread (the first conky I think), there were things in it that I havn't removed (I need to rebuild it from the ground up). Whoever wrote it probably has a different native language (I don't think I even have all of the fonts used).

---

### Post by vehemoth on 2011-05-27
> **Sector11 said:**
> I missed this, kaivalagi doesn't use Ubuntu anymore, he uses ARCH Linux now. And yes, I have the same question.  He was using Ubuntu when he created these apps and continues to support them.

It's also Rhythmbox v2.90.1 on fedora 15, though I don't know why.

---

### Post by Sector11 on 2011-05-27
> **vehemoth said:**
> Coverart was broken in those updates you installed after the ones from the ppa, they were broken when he was trying to fix the utf8 support.

English is my native language, I'm just not very good at communicating.

That conky is just a heavily modified one from the .conkyrc thread (the first conky I think), there were things in it that I havn't removed (I need to rebuild it from the ground up). Whoever wrote it probably has a different native language (I don't think I even have all of the fonts used).

Oh, OK, fixed the language, broke the art.  Stranger things have happened.  I know that kaivalagi is extremely busy these days and trying hard to find time with a new job and a new baby.

Oh then in that case I do apologize. I thought it was because of the font, now I understand.  Well, that's why I though you were not English, I am sorry.

I didn't even get the art "before" the fix in conky.

---

### Post by vehemoth on 2011-05-27
I changed to debian wheezy and now I don't even get the cover art with the original .deb from the ppa.

```

*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA

```

---

### Post by kaivalagi on 2011-05-28
just use the "rhythmbox-desktop-art" plugin available in the ppa, that's what I used when running with RB...

---

### Post by vehemoth on 2011-05-28
> **kaivalagi said:**
> just use the "rhythmbox-desktop-art" plugin available in the ppa, that's what I used when running with RB...

Sweet as, cheers for all your help anyways guys. :)

---

### Post by kaivalagi on 2011-05-28
> **vehemoth said:**
> Sweet as, cheers for all your help anyways guys. :)

No worries, I should have suggested using it earlier on...assuming it works that is!

I figure the conky side of cover art should work but with the varying versions of rhythmbox we have and it's cover art workings it ain't easy to get the the bottom of the issues

The desktop art plugin also provides controls on the desktop to skip tracks etc...the one in the PPA was adapted by me slightly from the original to have a checkbox to turn on/off song info...so it can be used to just display the image and controls with conky doing the song info if that's what's wanted....

Cheers

---

### Post by Sector11 on 2011-05-28
> **kaivalagi said:**
> just use the "rhythmbox-desktop-art" plugin available in the ppa, that's what I used when running with RB...

:(  The plugin will not plugin for me.

[[img]http://dl.dropbox.com/u/16070765/thmb_RB-D-A.png[/img]](http://dl.dropbox.com/u/16070765/full_RB-D-A.png)

---

### Post by vehemoth on 2011-05-30
Yeah, same for me.
Debian squeeze and wheezy have the same rhythmbox.

Doesn't matter anyway because I think I've fallen in love with clementine.

---

### Post by Sector11 on 2011-05-30
> **vehemoth said:**
> Yeah, same for me.
Debian squeeze and wheezy have the same rhythmbox.

Doesn't matter anyway because I think I've fallen in love with clementine.

Well, that ends that...  and I'm using GMB - GMusicBrowser.  It's so lightweight as to not be there.

---

### Post by kaivalagi on 2011-05-30
> **Sector11 said:**
> Well, that ends that...  and I'm using GMB - GMusicBrowser.  It's so lightweight as to not be there.

MPD............you will all use it in the end, just a matter of time MUHAHAHAHAHA

Running music through a daemon which handles shoutcast/icecast out of the box too is the dogs danglies, oh and if you log out, music still plays too! It can be remote controlled from an android/iphone too

And....it's supported in conky by default...plus coverart and lyrics can be handled nicely via a little tool called mpdcron and some custom scripts (I made) which are called on track changes

---

### Post by Neon612 on 2011-05-30
If anyone is still interested I've been hacking away at a conkySongbird script (stolen from Kai's Exaile script, thank you for all the the work you have done) and have gotten russian song title to display as well as coverart taken from the mp3 tags. There is probably a much better way to do it but it works for me.

I've also tried my hand at the Rhythmbox problem. Russian text and some coverart displays, the unicode error for the filenames is fixed (at least for cyrillic chars). The only problem left is the coverart displays the first cover when rhythmbox starts playing but never changes.

I've attached what I'm talking about. The first image is the right cover, the second is supposed to be different.

The cover art is copied to /tmp/cover, and I have checked. The second cover is displayed in /tmp but not in conky.

Edit: I'm using Sector11's example setup from a few pages back

---

### Post by Sector11 on 2011-05-30
> **kaivalagi said:**
> MPD............you will all use it in the end, just a matter of time MUHAHAHAHAHA

I heard the sound of a ghost but no chains....

> **kaivalagi said:**
> Running music through a daemon which handles shoutcast/icecast out of the box too is the dogs danglies, oh and if you log out, music still plays too! It can be remote controlled from an android/iphone too

Ahhhhhhhhhhhh, wise man once said, no android - no music!
How dare you mention "i"SOMETHING here!   :D

> **kaivalagi said:**
> And....it's supported in conky by default...plus coverart and lyrics can be handled nicely via a little tool called mpdcron and some custom scripts (I made) which are called on track changes

```
if_mpd_playing
```
> if mpd is playing or paused, display everything between $if_mpd_playing and the matching $endif
Well, I'll be a monkey's ... don't even think it!
Now to find out what to put between there.  :D

Good start!
```
mpd_album
 	Album in current MPD song

mpd_artist
 	Artist in current MPD song must be enabled at compile

mpd_bar 	(height),(width)
 	Bar of mpd's progress

mpd_bitrate
 	Bitrate of current song

mpd_elapsed
 	Song's elapsed time

mpd_file
 	Prints the file name of the current MPD song

mpd_length
 	Song's length

mpd_name
 	Prints the MPD name field

mpd_percent
 	Percent of song's progress

mpd_random
 	Random status (On/Off)

mpd_repeat
 	Repeat status (On/Off)

mpd_smart 	(max length)
 	Prints the song name in either the form "artist - title" or file name, depending on whats available

mpd_status
 	Playing, stopped, et cetera.

mpd_title 	(max length)
 	Title of current MPD song

mpd_track
 	Prints the MPD track field

mpd_vol
 	MPD's volume 
```

---

### Post by kaivalagi on 2011-05-30
> **Neon612 said:**
> If anyone is still interested I've been hacking away at a conkySongbird script (stolen from Kai's Exaile script, thank you for all the the work you have done) and have gotten russian song title to display as well as coverart taken from the mp3 tags. There is probably a much better way to do it but it works for me.

I've also tried my hand at the Rhythmbox problem. Russian text and some coverart displays, the unicode error for the filenames is fixed (at least for cyrillic chars). The only problem left is the coverart displays the first cover when rhythmbox starts playing but never changes.

I've attached what I'm talking about. The first image is the right cover, the second is supposed to be different.

The cover art is copied to /tmp/cover, and I have checked. The second cover is displayed in /tmp but not in conky.

Edit: I'm using Sector11's example setup from a few pages back

Nice one! Maybe you should get on board with the conky companions PPA side of things with the conkySongbird script!

Can you post the script, details on the fix for the unicode side of things and the conkyrc as I'll see what can be done in the other music player scripts to handle Russian (and other) characters...

Your issue with the image not changing sounds like the conky $image variable is caching rather than refetching the /tmp/cover image, either add a "-n" to the image variable options or set the image cache (can't recall the config setting needed above TEXT line, check the conky documentation at [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)) to 0

---

### Post by kaivalagi on 2011-05-30
> **Sector11 said:**
> Now to find out what to put between there.  :D

Thought this would get you started, any more mpd posts need to go elsewhere though, PM me if you want :)

Here's part of my conkyrc for mpd:
```

.
.
.
mpd_host		<IP ADDRESS_OF_SERVICE>
mpd_password            <PASSWORD>
mpd_port		6600

TEXT
${image $HOME/.scripts/conky/opaque.png -p -1,-1 -s 260x329}
$if_mpd_playing${font Liberation Sans:style=Bold:size=6}${alignr 10}${if_match "$mpd_repeat" == "On"}REPEAT$endif
${alignr 10}${if_match "$mpd_random" == "On"}SHUFFLE$endif
${voffset 200}
${color2}${font}${mpd_bar 10,256}
${voffset 5}${color2}${font}${goto 15}${mpd_elapsed}/${mpd_length} - ${mpd_percent}%${alignr 5}${mpd_status} ${mpd_bitrate}k/s
${voffset 5}${color1}${font Liberation Sans:style=Bold:size=9}${alignc}${mpd_title}
${font}${alignc}${color2} from the album ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_album}
${color2}${font}${alignc} by ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_artist}
${color2}${hr}
${if_existing /tmp/lyrics}${image $HOME/.scripts/conky/opaque.png -p -1,330 -s 260x565}
${color1}${font Liberation Sans:style=Bold:size=9}${exec fold -s -w 40 /tmp/lyrics | sed 's/^/  /'}
${color2}${hr}$endif
${if_existing /tmp/cover}${image /tmp/cover -p 4,4 -s 254x254 -n}$endif
$endif
```


And here are the 2 scripts I use with mpdcron, for me they need to live in $HOME/.mpdcron/hooks/ to get fired on track changes. Note the red text is what is made available by mpdcron

coverart.sh:
```
#!/usr/bin/env sh
##### get coverart linked #####
coverfile="$HOME/.covers/**[COLOR="Red"]$MPD_SONG_TAG_ARTIST[/COLOR]**-**[COLOR="red"]$MPD_SONG_TAG_ALBUM[/COLOR]**.jpg"
outputcoverfile="/tmp/cover"
if [ -f "$coverfile" ]; then
    rm -f "$outputcoverfile"
    echo "coverart.sh - Linking '$outputcoverfile' to cover file '$coverfile'"
    ln -s "$coverfile" "$outputcoverfile"
else
    echo "coverart.sh - No matching cover art file found here: '$coverfile'"
    rm -f "$outputcoverfile"
fi
```

lyrics.sh:
```
#!/usr/bin/env sh

# get lyrics (if found) and copy it to /tmp/lyrics
lyricsfile="$HOME/.lyrics/[COLOR="red"]**$MPD_SONG_TAG_ARTIST**[/COLOR]-[COLOR="red"]**$MPD_SONG_TAG_TITLE**[/COLOR].txt"
outputlyricsfile="/tmp/lyrics"
if [ -f "$lyricsfile" ]; then
    rm -f "$outputlyricsfile"
    echo "lyrics.sh - Linking '$outputlyricsfile' to cover file '$lyricsfile'"
    ln -s "$lyricsfile" "$outputlyricsfile"
else
    rm -f "$outputlyricsfile"
fi
```

---

### Post by Sector11 on 2011-05-30
> **Neon612 said:**
> If anyone is still interested I've been hacking away at a conkySongbird script (stolen from Kai's Exaile script, thank you for all the the work you have done) and have gotten russian song title to display as well as coverart taken from the mp3 tags. There is probably a much better way to do it but it works for me.

Stolen?  Oh my!  CCCC'd maybe but stolen; never.  :D
Hey, if it works ... it's good.  :D

Ahhhhhhhh no wonder I don't know what it is - Songbird is a MacWindows app!

> **Neon612 said:**
> I've also tried my hand at the Rhythmbox problem. Russian text and some coverart displays, the unicode error for the filenames is fixed (at least for cyrillic chars). The only problem left is the coverart displays the first cover when rhythmbox starts playing but never changes.

I've attached what I'm talking about. The first image is the right cover, the second is supposed to be different.

The cover art is copied to /tmp/cover, and I have checked. The second cover is displayed in /tmp but not in conky.

Edit: I'm using Sector11's example setup from a few pages back

Well, to be honest it's not really mine.  It's modified from:

[I]/usr/share/conkyrhythmbox/example/conkyrc
/usr/share/conkyrhythmbox/example/conkyRhythmbox.template[/I]

What would happen if you changed */tmp/*cover ?
I ask because I have had bad luck with /tmp/ in the past.
~/rb/cove or something else maybe.

Looks good Neon612, hope you keep at it.

---

### Post by Sector11 on 2011-05-30
> **kaivalagi said:**
> Your issue with the image not changing sounds like the conky $image variable is caching rather than refetching the /tmp/cover image, either add a "-n" to the image variable options or set the image cache (can't recall the config setting needed above TEXT line, check the conky documentation at [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)) to 0

**@ Neon612:**

```
imlib_cache_size 0
```

---

### Post by Neon612 on 2011-05-30
> **kaivalagi said:**
> Nice one! Maybe you should get on board with the conky companions PPA side of things with the conkySongbird script!

I'd love to but ... uh ... how?

> **kaivalagi said:**
> Can you post the script, details on the fix for the unicode side of things and the conkyrc as I'll see what can be done in the other music player scripts to handle Russian (and other) characters...

Attached file.
The unicode fix is just a dict where each set of hex values are mapped to their equivalent Cyrillic character. I'm sure there is a better way to do it, but this is what I got working for me.

The dict is inside a function (russify... original right?) the loops through every key/value pair, replacing the hex mess with the right char. I'm guessing that other characters could be added by just extending the dict.

The linking of the cover image I removed (commented out) and converted it to reading from the mp3 tags, using the eyeD3 python library. It retrieves the image data, opens /tmp/cover and outputs the data into the file.

> **kaivalagi said:**
> Your issue with the image not changing sounds like the conky $image variable is caching rather than refetching the /tmp/cover image, either add a "-n" to the image variable options or set the image cache (can't recall the config setting needed above TEXT line, check the conky documentation at [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)) to 0

Thanks, the -n flag fixed things.

> **Sector11 said:**
> Stolen?  Oh my!  CCCC'd maybe but stolen; never.  :D
Hey, if it works ... it's good.  :D

Ahhhhhhhh no wonder I don't know what it is - Songbird is a MacWindows app!

C4'd!!

Actually, Songbird started out as a crossplatform music player from mozilla. They eventually discontinued the linux version as official releases but most of their developers are using linux so it is still possible to get a linux edition.

---

### Post by kaivalagi on 2011-05-31
> **Neon612 said:**
> I'd love to but ... uh ... how?

Firstly thanks very much for your efforts so far, it's nice when someone is willing to take on a little development and aid the cause! 

You'd be best understanding an existing branch layout etc including the bazaar and aur folders and what they do for builds

Once you have that nailed then get to grips with bazaar (versioning) and we can see to get you added to the team members so you can init/commit and push a branch up

Once the code and support files are looking right on the bazaar server we have a script you can use to pull down source, do a debian source package and upload to launchpad for building...this forms the start of package creation for ubuntu/debian etc.

Probably some details you need to get to grips with there...PM me for help on it, either way if it were me I would start by understanding an existing code branch and all that it entails...conkyRhythmbox might be a good choice :)

> **Neon612 said:**
> Attached file.
The unicode fix is just a dict where each set of hex values are mapped to their equivalent Cyrillic character. I'm sure there is a better way to do it, but this is what I got working for me.

The dict is inside a function (russify... original right?) the loops through every key/value pair, replacing the hex mess with the right char. I'm guessing that other characters could be added by just extending the dict.

Mmmmm, not so keen on this as it would require handling all sorts of characters as and when they turn up - what happens when some polish / chinese / swedish songs need support.

There must be something that does the job properly - you would hope anyway. For example I used urllib.unquote to handle anything in the past...but this must have issue with Russian chars....? I thought it coped but as I had issue with getting a coverart path in the first place so couldn't be sure...maybe I should try the Russian songs with a player such as Exaile to see how the code fairs...all needs time though which is in limited supply

I would be interested if your line here:
```
taglocation = self.russify(location.replace('file://', '').replace('%20', ' ')).encode('utf-8')
```

would still work if like this:
```
taglocation = urllib.unquote(location).replace("file://", "").encode("utf-8")
```

> **Neon612 said:**
> The linking of the cover image I removed (commented out) and converted it to reading from the mp3 tags, using the eyeD3 python library. It retrieves the image data, opens /tmp/cover and outputs the data into the file.

I used this same method with other scripts where I can handle the track change event in dbus (not implemented by RB and working)...take a look at the conkyExaile-GetCoverart.py script as part of conkyExaile for an example of what I mean...it uses this along with other methods to try and get coverart sorted.

MP3 image tag functions used on thier own wont support much as most mp3's I have (and lots of others I suspect) don't include embedded images and I for one don't want them to....

> **Neon612 said:**
> Thanks, the -n flag fixed things.
No worries

Sorry if I am coming across as a picky a$$hole, I don't mean to provoke etc, I am always looking for the longer term all encompassing solution so no more work will be required as the rolling out of a package update can be slow going and I like to minimise that :)

I hope you get where I am coming from with all this and maybe you have some ideas that would fit with my ideals...all help is appreciated even if it might not come across that way ;)

edit: I wish rhythmbox would fetch cover art paths for me in the first place...then I could test this thing properly

---

### Post by Sector11 on 2011-05-31
> **kaivalagi said:**
> Sorry if I am coming across as a picky a$$hole, I don't mean to provoke etc, I am always looking for the longer term all encompassing solution so no more work will be required as the rolling out of a package update can be slow going and I like to minimise that :)

I hope you get where I am coming from with all this and maybe you have some ideas that would fit with my ideals...all help is appreciated even if it might not come across that way ;)

{hands on hips} now now Mr K. you have never come across that way. You should have a little more faith in yourself. I sure do!

If I could code, I'd be right in there as thick as I am into conky.  But alas, all I can do is beta test things and help that way.  I'd love to take some of the workload off your shoulders.  I'm still looking for a nice Python Book to buy.  may have to wait until later this year when I head north for a holiday.

---

### Post by Sector11 on 2011-05-31
I just had a thought, if Rhythmbox and, VLC can see the cover art and display the songs with the proper "characters" why can't that type of coding be used.

[[img]http://dl.dropbox.com/u/16070765/thmb_names.png[/img]](http://dl.dropbox.com/u/16070765/full_names.png)

Easy to tell I'm not a programmer huh.

---

### Post by Neon612 on 2011-05-31
> **kaivalagi said:**
> Firstly thanks very much for your efforts so far, it's nice when someone is willing to take on a little development and aid the cause! 

You'd be best understanding an existing branch layout etc including the bazaar and aur folders and what they do for builds

Once you have that nailed then get to grips with bazaar (versioning) and we can see to get you added to the team members so you can init/commit and push a branch up

Once the code and support files are looking right on the bazaar server we have a script you can use to pull down source, do a debian source package and upload to launchpad for building...this forms the start of package creation for ubuntu/debian etc.

Probably some details you need to get to grips with there...PM me for help on it, either way if it were me I would start by understanding an existing code branch and all that it entails...conkyRhythmbox might be a good choice :)

I'll have to get back to you on this. I read it over and my eyes just sort of glazed over. I'll take a look and see what I can learn. DO you happen to have any links to point me in the right direction?

Thanks.


> **kaivalagi said:**
> Mmmmm, not so keen on this as it would require handling all sorts of characters as and when they turn up - what happens when some polish / chinese / swedish songs need support.

There must be something that does the job properly - you would hope anyway. For example I used urllib.unquote to handle anything in the past...but this must have issue with Russian chars....? I thought it coped but as I had issue with getting a coverart path in the first place so couldn't be sure...maybe I should try the Russian songs with a player such as Exaile to see how the code fairs...all needs time though which is in limited supply

I would be interested if your line here:
```
taglocation = self.russify(location.replace('file://', '').replace('%20', ' ')).encode('utf-8')
```

would still work if like this:
```
taglocation = urllib.unquote(location).replace("file://", "").encode("utf-8")
```

The unquote will take us right back to the beginning. I'm noticing that the filestrings are set up as two hex digits. Something like %d0%ae, and then after the unquote it treats each percent symbol as separate characters. So instead of one character coming out (\xd0\xae) we get two (\xd0 and \xae). If there is a way to convert the %d0%ae into its unicode number, that should at least be closer to working the right way.


> **kaivalagi said:**
> Sorry if I am coming across as a picky a$$hole, I don't mean to provoke etc, I am always looking for the longer term all encompassing solution so no more work will be required as the rolling out of a package update can be slow going and I like to minimise that :)

I hope you get where I am coming from with all this and maybe you have some ideas that would fit with my ideals...all help is appreciated even if it might not come across that way ;)

edit: I wish rhythmbox would fetch cover art paths for me in the first place...then I could test this thing properly

No worry there. I'm sort of the same way, a perfectionist at heart that is more worried about code working then just for the sake of getting it out there.

---

### Post by kaivalagi on 2011-05-31
> **Neon612 said:**
> I'll have to get back to you on this. I read it over and my eyes just sort of glazed over. I'll take a look and see what I can learn. DO you happen to have any links to point me in the right direction?

Thanks.


Install "bazaar" or "bzr", run this somewhere suitable in the terminal and look at the contents:

```
bzr branch lp:~conky-companions/+junk/conkyrhythmbox
```

Pay special attention to the "debian" folder and it's contents as well as the setup.py and changelog file

I learnt from example / trial error so I can't really point you towards any docs. Once you get the local files side of things sussed I can help with bzr command usage and launchpad setup (need a login and pgp/ssh keys setup for auth)

> **Neon612 said:**
> The unquote will take us right back to the beginning. I'm noticing that the filestrings are set up as two hex digits. Something like %d0%ae, and then after the unquote it treats each percent symbol as separate characters. So instead of one character coming out (\xd0\xae) we get two (\xd0 and \xae). If there is a way to convert the %d0%ae into its unicode number, that should at least be closer to working the right way.
Mmmmm, maybe unquote will work if python knows to play nice with unicode in the first place, using something like sys.setdefaultencoding() could help but on further reading it looks like different encoding methods might be needed for different character sets, e.g. iso-8859-1 for some latin types and koi8-r for Russian...

To be honest if I can't find a dynamic way of handling everything nicely then it wont handle it at all...you can only please some of the people some of the time ;)

> **Neon612 said:**
> No worry there. I'm sort of the same way, a perfectionist at heart that is more worried about code working then just for the sake of getting it out there.
I do this in my day job except it's java or .net....you'd think I would leave this stuff well alone when I come home....some of the time I do wonder why I do it :)

---

### Post by kaivalagi on 2011-05-31
> **Sector11 said:**
> I just had a thought, if Rhythmbox and, VLC can see the cover art and display the songs with the proper "characters" why can't that type of coding be used.

[[img]http://dl.dropbox.com/u/16070765/thmb_names.png[/img]](http://dl.dropbox.com/u/16070765/full_names.png)

Easy to tell I'm not a programmer huh.

I think you may have just hit the nail on the head, I need to start looking at some of the python source code for some of the players (RB and VLC are not python though)....when I find the time that is!

---

### Post by Sector11 on 2011-05-31
> **kaivalagi said:**
> I think you may have just hit the nail on the head, I need to start looking at some of the python source code for some of the players (RB and VLC are not python though)....when I find the time that is!

I'm outside the box looking in, sometimes I see might something that a programmer might over look.  BTW, GMusicBrowser is a perl script and it has no problem either:

[[img]http://dl.dropbox.com/u/16070765/thmb_GMB-2.png[/img]](http://dl.dropbox.com/u/16070765/full_GMB-2.png)
Maybe that will be easier.

OR - are you ready for this .....  Ta da!

[Music software written in Python]("http://wiki.python.org/moin/PythonInMusic")

---

### Post by Neon612 on 2011-05-31
> **kaivalagi said:**
> Mmmmm, maybe unquote will work if python knows to play nice with unicode in the first place, using something like sys.setdefaultencoding() could help but on further reading it looks like different encoding methods might be needed for different character sets, e.g. iso-8859-1 for some latin types and koi8-r for Russian...

To be honest if I can't find a dynamic way of handling everything nicely then it wont handle it at all...you can only please some of the people some of the time ;)

I feel like I've just been hit over the head. The fix is so simple (I hope it works for more than russian characters, I can't test it).

Simply change:```
location = props["location"]
``` to ```
location = props["location"].encode('utf-8')
```

And change ```
taglocation = urllib.unquote(location).replace("file://", "").encode("utf-8")
``` to ```
taglocation = urllib.unquote(location).replace("file://", "")
```

:lolflag:

And my russify function is not even needed

---

### Post by kaivalagi on 2011-05-31
> **Neon612 said:**
> I feel like I've just been hit over the head. The fix is so simple (I hope it works for more than russian characters, I can't test it).

Simply change:```
location = props["location"]
``` to ```
location = props["location"].encode('utf-8')
```


Even better still, put this (in red) near the top of the python file after the imports and forget the encode calls as they should be the default functionality (should be!):

```

import urllib
import subprocess

[COLOR="Red"][B]reload(sys)
sys.setdefaultencoding('utf-8')
[/B][/COLOR]
try:
    import dbus
    DBUS_AVAIL = True

```

Atleast in theory it should work with the existing coverart code if RB provides a path in the first place (doesn't for me)....I haven't tried it though as I can't so please let me know how it turns out! Just add the red to an unchanged .py file....

---

### Post by Neon612 on 2011-05-31
> **kaivalagi said:**
> Even better still, put this (in red) near the top of the python file after the imports and forget the encode calls as they should be the default functionality (should be!):

```

import urllib
import subprocess

[COLOR="Red"][B]reload(sys)
sys.setdefaultencoding('utf-8')
[/B][/COLOR]
try:
    import dbus
    DBUS_AVAIL = True

```

Atleast in theory it should work....I haven't tried it though so please let me know how it turns out!

Just tried it and no dice. The location encode is still needed.

---

### Post by kaivalagi on 2011-05-31
> **Neon612 said:**
> Just tried it and no dice. The location encode is still needed.

Darn it....well an encode('utf-8') on the end of the coverart path code (pre your changes) should mean the cover art paths comes through okay and are useable I would hope...I would prefer no id3 tag stuff unless if it's in addition if cover art isn't coming from the dbus provided properties

edit: attached original py with amendments for unicode string prep (still using file linking though), can you run it using '--datatype=CA --verbose' with one of those Russian songs playing? I really wish I could get the song coverart to come through for me with RB....this is torture!

---

### Post by Neon612 on 2011-05-31
```
darin@computer-2:~/Desktop$ python conkyRhythmbox.py --datatype=CA --verbose
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Linking coverart from /home/darin/.cache/rhythmbox/covers/Ð’Ð¸Ð° Ð“Ñ€Ð° - ÐŸÐ¾Ð¿Ñ‹Ñ‚ÐºÐ° â„–5.jpg to /tmp/cover
Traceback (most recent call last):
  File "conkyRhythmbox.py", line 232, in getOutputData
    self.getShellCommandOutput(linkcmd)
  File "conkyRhythmbox.py", line 483, in getShellCommandOutput
    self.logger.info("Running shell command '%s'"%shell_command)
AttributeError: RhythmboxInfo instance has no attribute 'logger'
ERROR: Unknown error when calling getOutputData:RhythmboxInfo instance has no attribute 'logger'

```

What is this 'logger' its looking for?

---

### Post by kaivalagi on 2011-05-31
> **Neon612 said:**
> ```
darin@computer-2:~/Desktop$ python conkyRhythmbox.py --datatype=CA --verbose
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Linking coverart from /home/darin/.cache/rhythmbox/covers/Ð&#8217;Ð¸Ð° Ð&#8220;Ñ&#8364;Ð° - Ð&#376;Ð¾Ð¿Ñ&#8249;Ñ&#8218;ÐºÐ° â&#8222;&#8211;5.jpg to /tmp/cover
Traceback (most recent call last):
  File "conkyRhythmbox.py", line 232, in getOutputData
    self.getShellCommandOutput(linkcmd)
  File "conkyRhythmbox.py", line 483, in getShellCommandOutput
    self.logger.info("Running shell command '%s'"%shell_command)
AttributeError: RhythmboxInfo instance has no attribute 'logger'
ERROR: Unknown error when calling getOutputData:RhythmboxInfo instance has no attribute 'logger'

```

What is this 'logger' its looking for?
My bad, I copy and pasted code and didn't update something....

Change any "self.logger.info" to be "self.logInfo" :)

There should only be one entry

Although, this means there was an error and looking at the path it ain't good:

/home/darin/.cache/rhythmbox/covers/Ð&#8217;Ð¸Ð° Ð&#8220;Ñ&#8364;Ð° - Ð&#376;Ð¾Ð¿Ñ&#8249;Ñ&#8218;ÐºÐ° â&#8222;&#8211;5.jpg

edit: to top it all, the Rhythmbox version I now have wont play ball as they've changed the dbus interface quite considerably....I have v2.90.1

---

### Post by vehemoth on 2011-06-01
Probably of no help, but I would suggest sticking an echo command after getting the information from dbus so that you can tell where the script is going wrong.

I don't know whether you have to use slightly different commands when dealing with unicode in python.
Here's a link that might help [http://docs.python.org/library/functions.html#unicode](http://docs.python.org/library/functions.html#unicode)

---

### Post by Neon612 on 2011-06-01
I've attached an updated script using the one from page 50 (51?). Its still using linking, well heres the verbose output:
```
darin@computer-2:~/Desktop$ python untitled\ folder/conkyRhythmbox.py --datatype=CA --verbose
*** INITIAL OPTIONS:
	datatype: CA
	template: None
	ratingchar: *
	nounknownoutput: False
	secondsoutput: False
	maxlength: 0
	verbose: True
	errorlogfile: None
	infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Linking coverart from /home/darin/.cache/rhythmbox/covers/&#1042;&#1080;&#1072; &#1043;&#1088;&#1072; - &#1057;&#1090;&#1086;&#1087;! &#1057;&#1085;&#1103;&#1090;&#1086;!.jpg to /tmp/cover
INFO: Running shell command 'ln -sf "/home/darin/.cache/rhythmbox/covers/&#1042;&#1080;&#1072; &#1043;&#1088;&#1072; - &#1057;&#1090;&#1086;&#1087;! &#1057;&#1085;&#1103;&#1090;&#1086;!.jpg" "/tmp/cover"'
/tmp/cover
```

---

### Post by vehemoth on 2011-06-01
> **Neon612 said:**
> I've attached an updated script using the one from page 50 (51?). Its still using linking, well heres the verbose output:
```
darin@computer-2:~/Desktop$ python untitled\ folder/conkyRhythmbox.py --datatype=CA --verbose
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
INFO: Linking coverart from /home/darin/.cache/rhythmbox/covers/&#1042;&#1080;&#1072; &#1043;&#1088;&#1072; - &#1057;&#1090;&#1086;&#1087;! &#1057;&#1085;&#1103;&#1090;&#1086;!.jpg to /tmp/cover
INFO: Running shell command 'ln -sf "/home/darin/.cache/rhythmbox/covers/&#1042;&#1080;&#1072; &#1043;&#1088;&#1072; - &#1057;&#1090;&#1086;&#1087;! &#1057;&#1085;&#1103;&#1090;&#1086;!.jpg" "/tmp/cover"'
/tmp/cover
```

If that script doesn't use unicode and can only handle Russian characters then you might have some problems. It wasn't just Russian that we had problems with there was stuff like this [http://www.jamendo.com/en/artist/Artist_%28245%29](http://www.jamendo.com/en/artist/Artist_%28245%29) 

how do the scripts such as conky clementine do it, do they provide more information over dbus than rhythmbox.

I also think there was an update somewhere that broke support for the coverart part of the conkyrhythmbox script.

---

### Post by Neon612 on 2011-06-02
> **vehemoth said:**
> If that script doesn't use unicode and can only handle Russian characters then you might have some problems. It wasn't just Russian that we had problems with there was stuff like this [http://www.jamendo.com/en/artist/Artist_%28245%29](http://www.jamendo.com/en/artist/Artist_%28245%29) 

how do the scripts such as conky clementine do it, do they provide more information over dbus than rhythmbox.

I also think there was an update somewhere that broke support for the coverart part of the conkyrhythmbox script.


I know for certain it will work with russian letters. Someone else will have to test the others.

As to the coverart part, if the characters will display the coverart should as well.

---

### Post by DarkTide on 2011-06-04
Hi all,

kaivalagi this script print this in python >= 2.7:

conkyRhythmbox.py", line 45
    self.parser.add_option("-t", "--template", dest="template",  type="string", metavar="FILE", help=u"define a template file to generate  output in one call. A displayable item in the file is in the form  [--datatype=TI]. The following are possible options within each item:  --datatype,--ratingchar. Note that the short forms of the options are  not currently supported! None of these options are applicable at command  line when using templates.")

I think that optparse module is deprecated, more info in:
[http://docs.python.org/library/optparse.html](http://docs.python.org/library/optparse.html)

I don't a python programmer.

Thanks for the great script !!!

---

### Post by kaivalagi on 2011-06-04
> **DarkTide said:**
> Hi all,

kaivalagi this script print this in python >= 2.7:

conkyRhythmbox.py", line 45
    self.parser.add_option("-t", "--template", dest="template",  type="string", metavar="FILE", help=u"define a template file to generate  output in one call. A displayable item in the file is in the form  [--datatype=TI]. The following are possible options within each item:  --datatype,--ratingchar. Note that the short forms of the options are  not currently supported! None of these options are applicable at command  line when using templates.")

I think that optparse module is deprecated, more info in:
[http://docs.python.org/library/optparse.html](http://docs.python.org/library/optparse.html)

I don't a python programmer.

Thanks for the great script !!!

I am using python v2.7.1...no issues here. Are you using an up-to-date script? I recall an issue in the past but can't remember if I fixed it or it was python 3.0 related issues...

```
 [USER@towerpc1 ~]$ python --version
[COLOR="Lime"]**Python 2.7.1**[/COLOR]
 [USER@towerpc1 ~]$ conkyRhythmbox --version
[COLOR="Lime"]**conkyRhythmbox v.2.17**[/COLOR]
 [USER@towerpc1 ~]$ conkyRhythmbox -h
Usage: conkyRhythmbox.py [options]

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
                        BR (bitrate k/s), LE (length), PP (current position in
                        percent), PT (current position in time), VO (volume),
                        RT (rating). Not applicable at command line when using
                        templates.
  -c PATH, --coverartpath=PATH
                        [default: /tmp/cover] The file where coverart gets
                        copied to if found when using the --datatype=CA
                        option. Note that if set to an empty string i.e. ""
                        the original file path is provided for the coverart
                        path.
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

---

### Post by Sector11 on 2011-06-05
> **kaivalagi said:**
> I am using python v2.7.1...no issues here. Are you using an up-to-date script? I recall an issue in the past but can't remember if I fixed it or it was python 3.0 related issues...

```
 [USER@towerpc1 ~]$ python --version
[COLOR="Lime"]**Python 2.7.1**[/COLOR]
 [USER@towerpc1 ~]$ conkyRhythmbox --version
[COLOR="Lime"]**conkyRhythmbox v.2.17**[/COLOR]
```

HMMMMMMMMMMMM!!!!!!!
```
  14:27 ~
         $ python --version
[COLOR="DarkOrange"]Python 2.6.6[/COLOR]

  14:27 ~
         $ conkyRhythmbox --version
[COLOR="DarkOrange"]conkyRhythmbox v.2.18[/COLOR]

  14:28 ~
         $ 
```
Less Python more conkyRhythmbox  :D

---

### Post by ashhab2010 on 2011-10-04
can someone tell me how to apply this script.... everything is installed but i dont know how to use the script...

---

### Post by von Stalhein on 2011-10-20
I've installed 11.10 and got everything in my old Maverick conky working except for Rhythmbox

```
RHYTHMBOX (ELEVATOR MUSIC) ${hr 1}
${font Arial:size=8}
${voffset 4}Artist:${alignr}${exec conkyRhythmbox --datatype=AR}${font}
${voffset 4}${alignr}${exec conkyRhythmbox --datatype=TI}${font}
${voffset 4}Duration:${alignr}${exec conkyRhythmbox --datatype=PT}#${font}
${endif}

```

I've reinstalled it with no result - is there something missing from the code perchance? Thanks!

---

### Post by kaivalagi on 2011-10-22
> **von Stalhein said:**
> I've installed 11.10 and got everything in my old Maverick conky working except for Rhythmbox

```
RHYTHMBOX (ELEVATOR MUSIC) ${hr 1}
${font Arial:size=8}
${voffset 4}Artist:${alignr}${exec conkyRhythmbox --datatype=AR}${font}
${voffset 4}${alignr}${exec conkyRhythmbox --datatype=TI}${font}
${voffset 4}Duration:${alignr}${exec conkyRhythmbox --datatype=PT}#${font}
${endif}

```

I've reinstalled it with no result - is there something missing from the code perchance? Thanks!

Try running a conkyRhythmbox command in the console with the verbose option on so you see what is happening e.g.

```
conkyRhythmbox --datatype=TI --verbose
```

This should explain things a little better...

---

### Post by von Stalhein on 2011-10-23
Thanks kaivalagi - I should have remembered that from re-setting up my Conky script in the fresh install of 11.10 :(

Anyway, it's calling the wrong interface (I think?) - any suggestions on what/how to adjust?
```
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
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.UnknownMethod: Method "getVolume" with signature "" on interface "org.gnome.Rhythmbox.Player" doesn't exist

Unknown

```

---

### Post by davesbrain on 2011-11-04
Please help with conky Rhythmbox.  Basically, the album art is not showing in conky.
It IS showing in my /home/davejr/.album directory.
I do have conky Rhythmbox installed via synaptic.

Terminal is spitting this out:
> sh: ret: not found
sh: albumart: not found
Conky: Unable to load image '/home/davejr/.album'
Conky: Unable to load image '/home/davejr/.album'
Conky: Unable to load image '/home/davejr/.album'
sh: ret: not found
sh: albumart: not found
Conky: Unable to load image '/home/davejr/.album'


Here is relevant section:
```
${voffset -110}${font Arial:bold:size=10}${color5}RHYTHMBOX ${color8}${hr 2}
${goto 100}${font Arial:bold:size=8}${color0}${exec rhythmbox-client --print-playing-format %tt}
${goto 100}${font Arial:bold:size=8}${color0}${exec rhythmbox-client --print-playing-format %ta}$font${exec ret}
${execi 1 albumart}${image /home/davejr/.album -p 0,500 -s 64x64}
```

---

### Post by Pocio on 2011-12-10
> **kaivalagi said:**
> Thought this would get you started, any more mpd posts need to go elsewhere though, PM me if you want :)

Here's part of my conkyrc for mpd:
```

.
.
.
mpd_host		<IP ADDRESS_OF_SERVICE>
mpd_password            <PASSWORD>
mpd_port		6600

TEXT
${image $HOME/.scripts/conky/opaque.png -p -1,-1 -s 260x329}
$if_mpd_playing${font Liberation Sans:style=Bold:size=6}${alignr 10}${if_match "$mpd_repeat" == "On"}REPEAT$endif
${alignr 10}${if_match "$mpd_random" == "On"}SHUFFLE$endif
${voffset 200}
${color2}${font}${mpd_bar 10,256}
${voffset 5}${color2}${font}${goto 15}${mpd_elapsed}/${mpd_length} - ${mpd_percent}%${alignr 5}${mpd_status} ${mpd_bitrate}k/s
${voffset 5}${color1}${font Liberation Sans:style=Bold:size=9}${alignc}${mpd_title}
${font}${alignc}${color2} from the album ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_album}
${color2}${font}${alignc} by ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_artist}
${color2}${hr}
${if_existing /tmp/lyrics}${image $HOME/.scripts/conky/opaque.png -p -1,330 -s 260x565}
${color1}${font Liberation Sans:style=Bold:size=9}${exec fold -s -w 40 /tmp/lyrics | sed 's/^/  /'}
${color2}${hr}$endif
${if_existing /tmp/cover}${image /tmp/cover -p 4,4 -s 254x254 -n}$endif
$endif
```


And here are the 2 scripts I use with mpdcron, for me they need to live in $HOME/.mpdcron/hooks/ to get fired on track changes. Note the red text is what is made available by mpdcron

coverart.sh:
```
#!/usr/bin/env sh
##### get coverart linked #####
coverfile="$HOME/.covers/**[COLOR="Red"]$MPD_SONG_TAG_ARTIST[/COLOR]**-**[COLOR="red"]$MPD_SONG_TAG_ALBUM[/COLOR]**.jpg"
outputcoverfile="/tmp/cover"
if [ -f "$coverfile" ]; then
    rm -f "$outputcoverfile"
    echo "coverart.sh - Linking '$outputcoverfile' to cover file '$coverfile'"
    ln -s "$coverfile" "$outputcoverfile"
else
    echo "coverart.sh - No matching cover art file found here: '$coverfile'"
    rm -f "$outputcoverfile"
fi
```

lyrics.sh:
```
#!/usr/bin/env sh

# get lyrics (if found) and copy it to /tmp/lyrics
lyricsfile="$HOME/.lyrics/[COLOR="red"]**$MPD_SONG_TAG_ARTIST**[/COLOR]-[COLOR="red"]**$MPD_SONG_TAG_TITLE**[/COLOR].txt"
outputlyricsfile="/tmp/lyrics"
if [ -f "$lyricsfile" ]; then
    rm -f "$outputlyricsfile"
    echo "lyrics.sh - Linking '$outputlyricsfile' to cover file '$lyricsfile'"
    ln -s "$lyricsfile" "$outputlyricsfile"
else
    rm -f "$outputlyricsfile"
fi
```

Hi kaivalagi, Can I ask for your help with mpdcron?
I use it "standalone", not for conky purposes, but I adapt your script for displaying the album cover in the notification...However I cannot get it work.

mpdcron reads the album art in the format Artist - Album from a selected folder.
With the script, I successfully create a symbolic link of the cover in the folder ~/.covers but mpdcron does not show the album art anyway.
Here's the modified script:

```
#!/usr/bin/env sh

# get cover (if found) and link it to /tmp/cover
coverfile="$HOME/Musica/Album/$MPD_SONG_TAG_ARTIST/$MPD_SONG_TAG_ALBUM/cover.jpg"
outputcoverfile="$HOME/.covers/$MPD_SONG_TAG_ARTIST - $MPD_SONG_TAG_ALBUM"
if [ -f "$coverfile" ]; then
    #rm -f "$outputcoverfile"
    echo "coverart.sh - Linking '$outputcoverfile' to cover file '$coverfile'"
    ln -s "$coverfile" "$outputcoverfile"
else
    echo "coverart.sh - No matching cover art file found here: '$coverfile'"
    rm -f "$outputcoverfile"
fi
```

Here's mpdcron config file:
```
# mpdcron example configuration
# vim: set et sw=4 sts=4 tw=80 ft=desktop :
# Copy this file to MPDCRON_DIR/mpdcron.conf where MPDCRON_DIR is
# ~/.mpdcron by default.

# mpdcron related options are specified in the main group
[main]
# Location of the pid file.
# pidfile = /var/run/mpdcron.pid
# Wait this many seconds after sending signal to kill the daemon
killwait = 3

# Mpd related options are specified in the mpd group.
[mpd]
# The list of events to wait for
events = database;stored_playlist;playlist;player;mixer;output;options;update
# Inverval in seconds for reconnecting to Mpd.
reconnect = 5
# Timeout in milliseconds for Mpd timeout, 0 for default timeout of
# libmpdclient.
timeout = 0

[player]
# modules is a semicolon delimited list of modules to load.
modules = notification;scrobbler

[main]
modules = notification

[notification]
# Covers path, defaults to ~/.covers
cover_path = ~/.covers
# Cover suffix, defaults to jpg
cover_suffix =
# Notification timeout in milliseconds.
timeout = 50000
# Notification type
type = mpd
# Notification urgency, one of low, normal, critical
urgency = normal
# Notification hints in format TYPE:NAME:VALUE, specifies basic extra data
# to pass. Valid types are int, double, string and byte
hints =

```

Finally, here's the error that mpdcron gives me:

```
Sending status & currentsong commands to Mpd server
[notification] Failed to find cover for album (Tool - 10,000 Days), suffix: 
[notification] Sending notify for song (Tool - Jambi), id: 517, pos: 1
Setting environment variable MC_CALLS_PLAYER=1
Running hook: hooks/player home directory: /home/milo/.mpdcron
Sending idle command with mask 0xff

```

As you can see, mpdcron complains about not finding the cover for the album, but I can assure you that in ~/.covers I've got a jpg file named Tool - 10,000 Days.
I searched up and down for a solution but nothing...
So, having used your script, I try here but feel free to say if I am too much OT or if I bothered you.

Thank you very much.

---

### Post by kaivalagi on 2011-12-10
mmmmmm, I am not sure I can be of help but what you are trying to do seems a big wrong to me as you are attempting to feed one function of mpdcron (notification) using another (script to link cover art)...maybe mpdcron is attempting to notify before the sym linking is done?

Some more thoughts which could well lead nowhere:

The output indicates there is no known suffix even though it should be jpg by default:

```
Sending status & currentsong commands to Mpd server
[notification] Failed to find cover for album (Tool - 10,000 Days), [COLOR="Red"]suffix: [/COLOR]

```

```
# Cover suffix, [COLOR="red"]defaults to jpg[/COLOR]
cover_suffix =
```

So what happens if you use, any difference?:

```
# Cover suffix, defaults to jpg
cover_suffix = [COLOR="red"]jpg[/COLOR]

```

Also what happens if instead of sym linking the cover art you copy it?

---

### Post by Pocio on 2011-12-10
First of all, let me thank you for your help, you are very kind...

> **kaivalagi said:**
> maybe mpdcron is attempting to notify before the sym linking is done?

Exactly the first thing I thought. However, If i manually put the cover with the correct filename in the correct path, previous to start reproducing it I get the same error anyway.

> 
The output indicates there is no known suffix even though it should be jpg by default:

...

So what happens if you use, any difference?:


I tried several combination, no suffix, suffix specified, filename with suffix, filename without it...always the same error!

> 
Also what happens if instead of sym linking the cover art you copy it?

Same error again...

Thank you anyway!!

---

### Post by kaivalagi on 2011-12-10
What about asking the author Ali Polatel: [https://github.com/alip](https://github.com/alip)

---

### Post by StiveKnoxx on 2012-01-05
Same problem here.

Here's some outputs:

```
$ conkyRhythmbox --datatype=TI

ERROR: Issue calling the dbus service:org.freedesktop.DBus.Error.UnknownMethod: Method "getVolume" with signature "" on interface "org.gnome.Rhythmbox.Player" doesn't exist
```
```
$ dbus-send --print-reply --dest=org.gnome.Rhythmbox /org/gnome/Rhythmbox org.freedesktop.DBus.Introspectable.Introspect

method return sender=:1.333 -> dest=:1.342 reply_serial=2
   string "<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node>
  <node name="Shell"/>
</node>
"
``````
$ dbus-send --print-reply --dest=org.gnome.Rhythmbox /org/gnome/Rhythmbox/Player          org.gnome.Rhythmbox.Player.getPlayingUri

Error org.freedesktop.DBus.Error.UnknownMethod: Method "getPlayingUri" with signature "" on interface "org.gnome.Rhythmbox.Player" doesn't exist
```

```
$ conkyRhythmbox --version
conkyRhythmbox v.2.17

Rhythmbox version is 2.90.1
```


Yes, I have dbus plugins enabled in rhythmbox plugins list...

---

### Post by kaivalagi on 2012-01-06
Looks like they've changed the dbus methods...if someone could installed a tool called dfeet you will be able to view what is available...not much free time right now so I can't say when I will be able to review the situation and find out why things have broken.....I use MPD with Sonata these days ;)

---

### Post by StiveKnoxx on 2012-01-06
```
$ dbus-send --print-reply --dest=org.gnome.Rhythmbox /org/gnome/Rhythmbox/Shell org.freedesktop.DBus.Introspectable.Introspect
method return sender=:1.157 -> dest=:1.964 reply_serial=2
   string "<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node>
  <interface name="org.freedesktop.DBus.Introspectable">
    <method name="Introspect">
      <arg name="data" direction="out" type="s"/>
    </method>
  </interface>
  <interface name="org.freedesktop.DBus.Properties">
    <method name="Get">
      <arg name="interface" direction="in" type="s"/>
      <arg name="propname" direction="in" type="s"/>
      <arg name="value" direction="out" type="v"/>
    </method>
    <method name="Set">
      <arg name="interface" direction="in" type="s"/>
      <arg name="propname" direction="in" type="s"/>
      <arg name="value" direction="in" type="v"/>
    </method>
    <method name="GetAll">
      <arg name="interface" direction="in" type="s"/>
      <arg name="props" direction="out" type="a{sv}"/>
    </method>
  </interface>
  <interface name="org.gnome.Rhythmbox.Shell">
    <method name="notify">
      <arg name="userRequested" type="b" direction="in"/>
    </method>
    <method name="clearQueue">
    </method>
    <method name="removeFromQueue">
      <arg name="uri" type="s" direction="in"/>
    </method>
    <method name="quit">
    </method>
    <method name="addToQueue">
      <arg name="uri" type="s" direction="in"/>
    </method>
    <method name="setSongProperty">
      <arg name="uri" type="s" direction="in"/>
      <arg name="propname" type="s" direction="in"/>
      <arg name="value" type="v" direction="in"/>
    </method>
    <method name="getSongProperties">
      <arg name="uri" type="s" direction="in"/>
      <arg name="arg1" type="a{sv}" direction="out"/>
    </method>
    <method name="present">
      <arg name="arg0" type="u" direction="in"/>
    </method>
    <method name="getPlaylistManager">
      <arg name="arg0" type="o" direction="out"/>
    </method>
    <method name="getPlayer">
      <arg name="arg0" type="o" direction="out"/>
    </method>
    <method name="activateSource">
      <arg name="uri" type="s" direction="in"/>
      <arg name="play" type="u" direction="in"/>
    </method>
    <method name="loadURI">
      <arg name="arg0" type="s" direction="in"/>
      <arg name="arg1" type="b" direction="in"/>
    </method>
    <signal name="databaseLoadComplete">
    </signal>
    <signal name="removableMediaScanFinished">
    </signal>
    <signal name="visibilityChanged">
      <arg type="b"/>
    </signal>
  </interface>
</node>
"

```

---

### Post by kaivalagi on 2012-01-07
So there is only the org.gnome.Rhythmbox.Shell interface for use now then? No .player one which was used previously?

I'm installing Rhythmbox and d-feet to look myself, I need to see all offerings from the dbus service exposed by RB to be certain of what is going on...

**edit:** I am not sure what you are seeing as I have just installed RB 2.90.1 on Arch (i.e. the vanilla install untouched by Ubuntu fingers) and I can't even see the dbus interface you are pulling back or the ones the script currently works with (i.e. org.gnome.Rhythmbox.Shell and org.gnome.Rhythmbox.Player)

See the attached screenshot of what I see (i.e. org.gnome.Rhythmbox3)...

Looks like even if I was to bring the script up-to-date with what I see I would be breaking previous builds of RB working with it....I feel that this script may go the same route as the conkyDeluge one did which is nowhere, due to the continual changing of interface methods required...

What do you see on the dbus session bus for RB? That's what I would like to know...

**edit2:** I suggest using rhythmbox-client...

---

### Post by Lateralus138 on 2012-09-23
Hello, I have the example config up and running and I have Rhythmbox playing and yet it is displaying only Unkown for everything and 00.00.00 for time. I have tried many songs so far.

---

### Post by kaivalagi on 2012-09-23
> **Lateralus138 said:**
> Hello, I have the example config up and running and I have Rhythmbox playing and yet it is displaying only Unkown for everything and 00.00.00 for time. I have tried many songs so far.

read my previous post above, the interface to communicate with RB changed and the script isn't updated to suit.

---

### Post by Lateralus138 on 2012-09-23
> **kaivalagi said:**
> read my previous post above, the interface to communicate with RB changed and the script isn't updated to suit.
Yeah I'm sorry I posted this from the beginning of the thread and only just seen the last few comments right after I posted.

---

### Post by Sector11 on 2012-09-23
> **Lateralus138 said:**
> Yeah I'm sorry I posted this from the beginning of the thread and only just seen the last few comments right after I posted.

Perhaps this: [How To - Conky/Lua, Music and Cover Art - 2 Methods for 18 Apps]("http://crunchbanglinux.org/forums/topic/15356/how-to-conkylua-music-and-cover-art-2-methods-for-18-apps/"). One never knows.

---

### Post by Lateralus138 on 2012-09-23
> **Sector11 said:**
> Perhaps this: [How To - Conky/Lua, Music and Cover Art - 2 Methods for 18 Apps]("http://crunchbanglinux.org/forums/topic/15356/how-to-conkylua-music-and-cover-art-2-methods-for-18-apps/"). One never knows.
Ok thank you very much, I'll check it out.

---

### Post by VastOne on 2012-10-05
> **Lateralus138 said:**
> Ok thank you very much, I'll check it out.

The conky/python I use within that How To is the very same one that kaivalagi designed and you have already tested.

I see no way with Rhythmbox3 and specifically org.gnome.Rhythmbox3 for these scripts to function anymore.  There is no way to pull metadata.

---

### Post by Jedcurtis on 2012-10-06
Well hello again Sector11.  @vastone, I posted a similar post on #! that you can just ignore.  I see that this is a prob with RB pulling the metadata.  Can you tell me, do any of the scripts for the other media players listed among the '18' music apps still work, and if so, which one should I be using?  I'm happy to use either of the methods i.e. python or Lua.  Let me know!
Also thanks again Sector11 for pointing me in the right direction!  You can't believe how much arclance helped me out.  The guy is a genius just like you said!!!

Thanks again,
Jed

---

### Post by VastOne on 2012-10-06
> **Jedcurtis said:**
> Well hello again Sector11.  @vastone, I posted a similar post on #! that you can just ignore.  I see that this is a prob with RB pulling the metadata.  Can you tell me, do any of the scripts for the other media players listed among the '18' music apps still work, and if so, which one should I be using?  I'm happy to use either of the methods i.e. python or Lua.  Let me know!
Also thanks again Sector11 for pointing me in the right direction!  You can't believe how much arclance helped me out.  The guy is a genius just like you said!!!

Thanks again,
Jed

I would recommend any of the other 17 apps in that How To, and give the loudest shout to GMusicBrowser. You might want to check out the How To on GMB I have as well ... [GMusicBrowser and Custom Layouts]("http://crunchbanglinux.org/forums/topic/20323/how-to-gmusicbrowser-and-custom-layouts/")

kaivalagi, Sector11, arclance... It does not get much better than that! :)

---

### Post by Jedcurtis on 2012-10-07
Thanks a lot Vastone!  What a great music player!  Had never heard of it.  Attached is my latest favorite look for my desktop!  This was much "easier" than setting up conky, especially if your working with python or Lua scripts within the conky!  Forget Ryhthmbox!  I'm a definite convert to GMB!!!  Should be the default in Ubuntu as far as I'm concerned...
Again, thanks a lot...

Jed

---

### Post by VastOne on 2012-10-07
> **Jedcurtis said:**
> Thanks a lot Vastone!  What a great music player!  Had never heard of it.  Attached is my latest favorite look for my desktop!  This was much "easier" than setting up conky, especially if your working with python or Lua scripts within the conky!  Forget Ryhthmbox!  I'm a definite convert to GMB!!!  Should be the default in Ubuntu as far as I'm concerned...
Again, thanks a lot...

Jed

Glad to hear that Jed... It looks great! :guitar:

Thank you.

---

### Post by Sector11 on 2012-10-08
> **VastOne said:**
> kaivalagi, Sector11, arclance... It does not get much better than that! :)

You forgot VastOne with his :guitar: and :-({|=

---

### Post by Sector11 on 2012-10-08
**@ Jed**

Lookin' good there Jed, lookin' good!

---

### Post by Jedcurtis on 2012-10-09
> **Sector11 said:**
> **@ Jed**

Lookin' good there Jed, lookin' good!

Why thank-you very much sir!!!  Without you, arclance, vastone, vindsl etc. etc. etc., I'd be no-where!  I've learned a lot and have all of you to thank.  Proving once again, "an old dog, can learn new tricks".

I'm still playing around with "other" conky scripts I've downloaded and 'made-my-own' but I'm still mostly just a copy/paste guy!

You guys are the greatest.  Speaking of "other", I've a copy of v9000 and it has a template called "s11template.lua" which doesn't take much of a giant leap to imagine it must be sector11's!  In it, it calls up an "/images/cyan-1.png" file.  Is that perhaps a directory one would need for that template to work?  If so, is it available somewhere to download?  No biggie, just wanted to see it in action!

Thanks,
Jed

---

### Post by Sector11 on 2012-10-09
> **Jedcurtis said:**
> Why thank-you very much sir!!!  Without you, arclance, vastone, vindsl etc. etc. etc., I'd be no-where!  I've learned a lot and have all of you to thank.  Proving once again, "an old dog, can learn new tricks".

I'm still playing around with "other" conky scripts I've downloaded and 'made-my-own' but I'm still mostly just a copy/paste guy!

You guys are the greatest.  Speaking of "other", I've a copy of v9000 and it has a template called "s11template.lua" which doesn't take much of a giant leap to imagine it must be sector11's!  In it, it calls up an "/images/cyan-1.png" file.  Is that perhaps a directory one would need for that template to work?  If so, is it available somewhere to download?  No biggie, just wanted to see it in action!

Thanks,
Jed

OK how about a little hop.  :D

shhhh ... [COLOR="LemonChiffon"]copy paste is my friend - don't tell anyone![/COLOR] ... shhh

You can get the [1x1 pixel images here]("http://ubuntuforums.org/showthread.php?p=12277272#post12277272") with an explanation of how/why I used them.  That conky was a work in process.

Put the images where you want but in the lua template you have to call them up like so using YOUR direct path - no **~/**path allowed:
```
image({x=205,y=5,w=1,h=260,file="/home/sector11/Conky/images/LightSlateGrey_1.png"})
```

Here's a shot of them in action:
[[IMG]http://t.imgbox.com/abwcRqTe.jpg[/IMG]](http://imgbox.com/abwcRqTe)

And that template if you are interested:
```
--[[
 The latest script is a lua only weather script. aka: v9000
 http://crunchbanglinux.org/forums/topic/16100/weather-in-conky/

 the file:
http://dl.dropbox.com/u/19008369/v9000.tar.gz

 mrppeachys LUA Tutorial
 http://crunchbanglinux.org/forums/topic/17246/how-to-using-lua-scripts-in-conky/

sun_rise_24[n]
sun_set_24[n]
moon_rise_24[n]
moon_set_24[n]
now["time_24"]
now["fc_hour1_time_24"]
now["fc_hour2_time_24"]
now["fc_hour3_time_24"]

]]
_G.weather_script = function()--#### DO NOT EDIT THIS LINE ##############
--these tables hold the coordinates for each repeat do not edit #########
top_left_x_coordinate={}--###############################################
top_left_y_coordinate={}--###############################################
--#######################################################################
--SET DEFAULTS ##########################################################
--set defaults do not localise these defaults if you use a seperate display script
default_font="Anonymous Pro:bold"--font must be in quotes
default_font_size=11
default_color=0xffffff--white
default_alpha=1--fully opaque
default_image_width=50
default_image_height=50
--END OF DEFAULTS #######################################################
--START OF WEATHER CODE -- START OF WEATHER CODE -- START OF WEATHER CODE
out({c=0x00BFFF,a=1,x=10,y=15,txt=now["date"].." "..now["month_short"].." "..now["year"]..": Fetched @ "..now["time_24"]})
image({x=20,y=20,h=40,w=40,file=now["weather_icon"]})
-- Temp / FeelsLike & CONDITIONS TEXT
out({c=0x48D1CC,a=1,f="digitalk",fs=50,x=80,y=60,txt=now["temp"]})
out({c=0x00BFFF,a=1,f="digitalk",fs=50,x=140,y=60,txt=now["feels_like"]})
out({c=0xA4FFA4,a=1,x=81,y=72,txt="Temp          WC · HI"})

out({c=0x48D1CC,a=1,f="Zekton",fs=18,x=10,y=94,txt=now["conditions_short"]})

-- data titles
--    data output
datay=110   -- y=datay or
datayy=15   -- y=datay+(datayy*1) use 1 or more

out({c=0xFAFAEC,a=1,x=10,y=datay,txt="Wind Chill:"})
   out({c=0x48D1CC,a=1,x=70,y=datay,txt=now["wind_chill"].."°"})
out({c=0xFAFAEC,a=1,x=100,y=datay,txt="Heat Index:"})
   out({c=0xFF8C00,a=1,x=165,y=datay,txt=now["heat_index"].."°"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*1),txt="Today's Hi·Lo:"})
   out({c=0xFF8C00,a=1,x=100,y=datay+(datayy*1),txt=high_temp[1].."°"})
   out({c=0x48D1CC,a=1,x=140,y=datay+(datayy*1),txt=low_temp[1].."°"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*2),txt="Wind:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*2),txt=now["wind_km"]})
   out({c=0x48D1CC,a=1,x=110,y=datay+(datayy*2),txt=now["wind_nesw"]})
   out({c=0xFAFAEC,a=1,x=140,y=datay+(datayy*2),txt="@"})
   out({c=0x48D1CC,a=1,x=165,y=datay+(datayy*2),txt=now["wind_deg"]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*3),txt="Hum:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*3),txt=now["humidity"].."%"})
out({c=0xFAFAEC,a=1,x=110,y=datay+(datayy*3),txt="DP:"})
   out({c=0x48D1CC,a=1,x=145,y=datay+(datayy*3),txt=now["dew_point"].."°"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*4),txt="Bar:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*4),txt=now["pressure_mb"]})
out({c=0xFAFAEC,a=1,x=110,y=datay+(datayy*4),txt="Vis:"})
   out({c=0x48D1CC,a=1,x=145,y=datay+(datayy*4),txt=now["visibility"]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*5),txt="Ceil:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*5),txt=now["ceiling"]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*6),txt="Precip:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*6),txt=precipitation[1].."%"})
out({c=0xFAFAEC,a=1,x=110,y=datay+(datayy*6),txt="Cloud:"})
   out({c=0x48D1CC,a=1,x=150,y=datay+(datayy*6),txt=cloud_cover[1].."%"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*7),txt="UV:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*7),txt=uv_index_num[1]})
   out({c=0x48D1CC,a=1,x=110,y=datay+(datayy*7),txt=uv_index_txt[1]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*8),txt="Sun:"})
   out({c=0xFAFAEC,a=1,x=60,y=datay+(datayy*8),txt=sun_rise_24[1]})
   out({c=0x48D1CC,a=1,x=120,y=datay+(datayy*8),txt=sun_set_24[1]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*9),txt="Moon:"})
   out({c=0xFAFAEC,a=1,x=60,y=datay+(datayy*9),txt=moon_rise_24[1]})
   out({c=0x48D1CC,a=1,x=120,y=datay+(datayy*9),txt=moon_set_24[1]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*10),txt="Phase:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*10),txt=moon_phase[1]})

-- line
image({x=205,y=5,w=1,h=260,file="/home/sector11/Conky/images/LightSlateGrey_1.png"})
-- 3 hour output
out({c=0x48D1CC,a=1,f="Anonymous Pro:bold",fs=12,x=220,y=15,txt="Next 3"})
out({c=0x48D1CC,a=1,f="Anonymous Pro:bold",fs=12,x=220,y=30,txt="Hours"})
-- 1st hour
out({c=0xA4FFA4,x=220,y=50,txt=now["fc_hour1_time_24"]..":00"})
image({w=30,h=30,x=223,y=55,file=now["fc_hour1_wicon"]}) -- image({w=30,h=30,x=223,y=55,file="/home/sector11/Conky/images/red_1.png"})
out({x=228,y=100,txt=now["fc_hour1_temp"] .."°"})
-- 2nd hour
out({c=0xA4FFA4,x=220,y=datay+(datayy*1),txt=now["fc_hour2_time_24"]..":00"})
image({w=30,h=30,x=223,y=130,file=now["fc_hour2_wicon"]}) -- image({w=30,h=30,x=223,y=130,file="/home/sector11/Conky/images/red_1.png"})
out({x=228,y=180,txt=now["fc_hour2_temp"] .."°"})
-- 3rd hour
out({c=0xA4FFA4,x=220,y=210,txt=now["fc_hour3_time_24"]..":00"})
image({w=30,h=30,x=223,y=215,file=now["fc_hour3_wicon"]}) -- image({w=30,h=30,x=223,y=215,file="/home/sector11/Conky/images/red_1.png"})
out({x=228,y=datay+(datayy*10),txt=now["fc_hour3_temp"] .."°"})
-- lines - to the right of the Next 3 Hours and today's forecast
-- vertical from top
image({x=385,y=5,w=1,h=130,file="/home/sector11/Conky/images/LightSlateGrey_1.png"})
-- hoizontal between top and bottom sections
image({x=270,y=134,w=115,h=1,file="/home/sector11/Conky/images/LightSlateGrey_1.png"})
-- vertical to bottom
image({x=270,y=135,w=1,h=130,file="/home/sector11/Conky/images/LightSlateGrey_1.png"})

--start or weather forecast table section
--set start forecast day
start_day=1
--set total forecast days you want to display
number_of_days=10
topy=15
topyy=135 -- topy+(topyy*1)
topx=285
topxx=120
--set coordinates for top lef corners for each repeat
top_left_x_coordinate[1],top_left_y_coordinate[1]        =topx            ,topy
   top_left_x_coordinate[2],top_left_y_coordinate[2]     =topx+(topxx*1)  ,topy
top_left_x_coordinate[3],top_left_y_coordinate[3]        =topx+(topxx*2)  ,topy
   top_left_x_coordinate[4],top_left_y_coordinate[4]     =topx+(topxx*3)  ,topy
top_left_x_coordinate[5],top_left_y_coordinate[5]        =topx+(topxx*4)  ,topy
   top_left_x_coordinate[6],top_left_y_coordinate[6]     =topx            ,topy+(topyy*1)
top_left_x_coordinate[7],top_left_y_coordinate[7]        =topx+(topxx*1)  ,topy+(topyy*1)
   top_left_x_coordinate[8],top_left_y_coordinate[8]     =topx+(topxx*2)  ,topy+(topyy*1)
top_left_x_coordinate[9],top_left_y_coordinate[9]        =topx+(topxx*3)  ,topy+(topyy*1)
   top_left_x_coordinate[10],top_left_y_coordinate[10]   =topx+(topxx*4)  ,topy+(topyy*1)
--########################################################################################
for i=start_day,number_of_days-(start_day-1) do --start of day repeat, do not edit #######
tlx=top_left_x_coordinate[i] --sets top left x position for each repeat ##################
tly=top_left_y_coordinate[i] --sets top left y position for each repeat ##################
--########################################################################################
out({c=0xA4FFA4,a=1,x=tlx,y=tly,txt=forecast_day_short[i].."  "..forecast_date[i].."  "..forecast_month_short[i]})
image({x=tlx,y=tly+5,h=30,w=30,file=weather_icon[i]})
out({c=0xFF8C00,a=1,x=tlx+35,y=tly+15,txt=high_temp[i].."°"})
out({c=0x48D1CC,a=1,x=tlx+35,y=tly+30,txt=low_temp[i].."°"})
out({c=0x48D1CC,a=1,x=tlx,y=tly+50,txt=conditions_short[i]})

out({c=0xFAFAEC,a=1,x=tlx,y=tly+65,txt="P: "..precipitation[i].."%"})
   out({c=0xFAFAEC,a=1,x=tlx+50,y=tly+65,txt="UV: "..uv_index_num[i]})
out({c=0xFAFAEC,a=1,x=tlx,y=tly+80,txt="H: "..humidity[i].."%"})
	out({c=0xFAFAEC,a=1,x=tlx+50,y=tly+80,txt=uv_index_txt[i]})
out({c=0xFAFAEC,a=1,x=tlx,y=tly+95,txt="S: "..sun_rise_24[i]})
   out({c=0x48D1CC,a=1,x=tlx+60,y=tly+95,txt=sun_set_24[i]})
out({c=0xFAFAEC,a=1,x=tlx,y=tly+110,txt="M: "..moon_rise_24[i]})
   out({c=0x48D1CC,a=1,x=tlx+60,y=tly+110,txt=moon_set_24[i]})
--########################################################################################
end--of forecast repeat section ##########################################################
--########################################################################################
--END OF WEATHER CODE ----END OF WEATHER CODE ----END OF WEATHER CODE ---
--#######################################################################
end--of weather_display function do not edit this line ##################
--#######################################################################

```

Three fonts needed: Zekton, digitalk & Anonymous Pro

The conky:
```
## To use #! in a conky use: ${exec echo '#!'}
## killall conky && conky -c ~/Conky/S11_v9_H.conky &
##
## The latest script is a lua only weather script. aka: v9000
## http://crunchbanglinux.org/forums/topic/16100/weather-in-conky/
##
## the file:
## http://dl.dropbox.com/u/19008369/weatheragain9000.lua.tar.gz
##
## mrppeachys LUA Tutorial
## http://crunchbanglinux.org/forums/topic/17246/how-to-using-lua-scripts-in-conky/
##
##
###  Begin Window Settings  ##################################################
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
#own_window_hints below,skip_taskbar,skip_pager
own_window_colour gray
own_window_class Conky
own_window_title Horizontal v9000

# Use the Xdbe extension? (eliminates flicker)
# It is highly recommended to use own window with this one
# so double buffer won't be so big.
double_buffer yes

### ARGB can be used for real transparency
### NOTE that a composite manager is required for real transparency.
### This option will not work as desired (in most cases) in conjunction with
### own_window_type normal
# own_window_argb_visual yes

### When ARGB visuals are enabled, this use this to modify the alpha value
### Use: own_window_type normal
### Use: own_window_transparent no
### Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
# own_window_argb_value 0

minimum_size 860 260  ##820 260   ## width, height
maximum_width 860     ##820       ## width, usually a good idea to equal minimum width

gap_x 0        ### left &right
gap_y 10        ### up & down

alignment top_middle
####################################################  End Window Settings  ###
###  Font Settings  ##########################################################
# Use Xft (anti-aliased font and stuff)
use_xft yes
xftfont Anonymous Pro:size=9

# Alpha of Xft font. Must be a value at or between 1 and 0 ###
xftalpha 1
# Force UTF8? requires XFT ###
override_utf8_locale yes

draw_shades no
default_shade_color black

draw_outline no # amplifies text if yes
default_outline_color black

uppercase no
######################################################  End Font Settings  ###
###  Color Settings  #########################################################
default_shade_color gray
default_outline_color black

default_color DCDCDC #220 220 220	Gainsboro
color0 8FBC8F #143 188 143	DarkSeaGreen
color1 778899 #119 136 153	LightSlateGray
color2 FF8C00 #255 140   0	DarkOrange
color3 7FFF00 #127 255   0	Chartreuse
color4 FFA07A #255 160 122	LightSalmon
color5 FFDEAD #255 222 173	NavajoWhite
color6 00BFFF #  0 191 255	DeepSkyBlue
color7 00FFFF #  0 255 255	Cyan
color8 FFFF00 #255 255   0	Yellow
color9 B22222 #178  34  34	FireBrick
#####################################################  End Color Settings  ###
###  Borders Section  ########################################################
draw_borders no
# Stippled borders?
stippled_borders 0
# border margins
border_inner_margin 5
border_outer_margin 0
# border width
border_width 0
# graph borders
draw_graph_borders no
#default_graph_size 15 40
#####################################################  End Borders Secton  ###
###  Miscellaneous Section  ##################################################
# Boolean value, if true, Conky will be forked to background when started.
background yes

# Adds spaces around certain objects to stop them from moving other things
# around, this only helps if you are using a mono font
# Options: right, left or none
use_spacer none

# Default and Minimum size is 256 - needs more for single commands that
# "call" a lot of text IE: bash scripts
text_buffer_size 256

# Subtract (file system) buffers from used memory?
no_buffers yes

# change GiB to G and MiB to M
short_units yes

# Like it says, ot pads the decimals on % values
# doesn't seem to work since v1.7.1
pad_percents 2

#   Maximum size of user text buffer, i.e. layout below TEXT line in config file
#  (default is 16384 bytes)
# max_user_text 16384

# Desired output unit of all objects displaying a temperature. Parameters are
# either "fahrenheit" or "celsius". The default unit is degree Celsius.
# temperature_unit Fahrenheit

##############################################  End Miscellaneous Section  ###
###  LUA Settings  ###########################################################
## Above and After TEXT - requires a composite manager or blinks.
##
# lua_load ~/Conky/LUA/draw-bg.lua
#TEXT
# ${lua conky_draw_bg 10 0 0 0 0 0x000000 0.6}
#
## ${lua conky_draw_bg corner_radius x_position y_position width height color alpha}
##
## OR Both above TEXT (No composite manager required - no blinking!)
#
lua_load ~/Conky/LUA/draw-bg.lua
lua_draw_hook_pre draw_bg 20 0 0 0 0 0x000000 0.5
# lua_draw_hook_post draw-bg 125 0 0 0 0 0x000000 0.01
#
# TEXT
#
############### V9000 ########################################################
#starts the lua weather data gathering function, call once at top of conkyrc
lua_load ~/v9000/v9000.lua
lua_draw_hook_post weather
lua_load ~/Conky/templates/h-10d-template.lua
#######################################################  End LUA Settings  ###
# The all important - How often conky refreshes.
# If you have a "Crey" try: 0.2 - smokin' - but watch the CPU useage go UP!
update_interval 1800

TEXT

```
**[COLOR="Red"]NOTE:[/COLOR]** 1 blank line after TEXT

---

### Post by Sector11 on 2012-10-09
OH MY!!!!!!!!!!  Talking about conky here's something new: Sector11 with a one liner!!!!!

[[img]http://t.imgbox.com/adeOXaU9.jpg[/img]](http://imgbox.com/adeOXaU9)[quote=doggie]OH! OH! Pick me! Pick me![/quote]
Shamelessly borrowed, with modifications, from [Voyager Linux](http://voyager.legtux.org/) while found on the ARCH forums.
Imagine that no shame anywhere.  ;)

**The Oneliner:**
```
#=== borrowed from: === Voyager Linux === http://voyager.legtux.org/ =========
###  Begin Window Settings  ##################################################
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
#own_window_colour black
own_window_class Conky
own_window_title OneLiner

# Use the Xdbe extension? (eliminates flicker)
# It is highly recommended to use own window with this one
# so double buffer won't be so big.
double_buffer yes

### ARGB can be used for real transparency
### NOTE that a composite manager is required for real transparency.
### This option will not work as desired (in most cases) in conjunction with
### own_window_type override
own_window_argb_visual yes

### When ARGB visuals are enabled, this use this to modify the alpha value
### Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
#own_window_argb_value 200

#minimum_size 500 500 ## width, height
#maximum_width 500  ## width, usually a good idea to be '=' or '>' minimum width

gap_x -40 # left-right
gap_y 5 # up-down

alignment top_middle
###################################################  End Window Settings  ###
###  Font Settings  #########################################################
# Use Xft (anti-aliased font and stuff)
use_xft yes
xftfont DejaVu Sans Mono:size=9

# Alpha of Xft font. Must be a value at or between 1 and 0 ###
xftalpha 0
# Force UTF8? requires XFT ###
override_utf8_locale yes

draw_shades no
default_shade_color black

draw_outline no # amplifies text if yes
default_outline_color black

uppercase no
######################################################  End Font Settings  ###
###  Color Settings  #########################################################
default_shade_color grey
default_outline_color black

default_color DCDCDC #220 220 220    Gainsboro
color0 8FBC8F #143 188 143    DarkSeaGreen
color1 778899 #119 136 153    LightSlateGray
color2 FF8C00 #255 140   0    DarkOrange
color3 7FFF00 #127 255   0    Chartreuse
color4 FFA07A #255 160 122    LightSalmon
color5 FFDEAD #255 222 173    NavajoWhite
color6 00BFFF #  0 191 255    DeepSkyBlue
color7 00FFFF #  0 255 255    Cyan
color8 FFFF00 #255 255   0    Yellow
color9 B22222 #178  34  34    FireBrick
#####################################################  End Color Settings  ###
###  Borders Section  ########################################################
draw_borders no
# Stippled borders?
stippled_borders 0
# border margins
border_inner_margin 0
border_outer_margin 0
# border width
border_width 0
# graph borders
draw_graph_borders no #yes
default_graph_size 15 40
#####################################################  End Borders Secton  ###
###  Miscellaneous Section  ##################################################

# Boolean value, if true, Conky will be forked to background when started.
background no

# Adds spaces around certain objects to stop them from moving other things
# around, this only helps if you are using a mono font
# Options: right, left or none
use_spacer none

# Default and Minimum size is 256 - needs more for single commands that
# "call" a lot of text IE: bash scripts
text_buffer_size 256

# Subtract (file system) buffers from used memory?
no_buffers yes

# change GiB to G and MiB to M
short_units yes

# Like it says, ot pads the decimals on % values
# doesn't seem to work since v1.7.1
pad_percents 2

##############################################  End Miscellaneous Section  ###
###  LUA Settings  ###########################################################
## Above and After TEXT - requires a composite manager or blinks.
##
# lua_load ~/Conky/LUA/draw-bg.lua
#TEXT
#${lua conky_draw_bg 10 0 0 0 0 0x000000 0.6}
#
## ${lua conky_draw_bg corner_radius x_position y_position width height color alpha}
##
## OR Both above TEXT (No composite manager required - no blinking!)
#
lua_load ~/Conky/LUA/draw-bg.lua
lua_draw_hook_pre draw_bg 5 0 0 0 0 0x000000 0.3
#
#######################################################  End LUA Settings  ###
# The all important - How often conky refreshes.
# If you have a "Crey" try: 0.2 - smokin' - but watch the CPU useage go UP!
update_interval 1


TEXT
 ${color6}HHD${color8} ${execi 15 hddtemp -n /dev/sda}°${color3} / ${color}${fs_free /} | ${fs_size /} ${color3}/home ${color}${fs_free /home} | ${fs_size /home}  ${color6}RAM${color} ${color3}${if_match ${memperc} < 10}00${memperc}\
${else}${if_match ${memperc} < 100}0${memperc}\
${else}${memperc}\
${endif}${endif} %${color} ${mem} | ${memmax}  ${color6}CPU ${color8}${platform f71882fg.2560 temp 1}°${color} ${color3}1|${color}${if_match ${cpu cpu1} < 10}00${cpu cpu1}\
${else}${if_match ${cpu cpu1} < 100}0${cpu cpu1}\
${else}${cpu cpu1}\
${endif}${endif}·${color3}2|${color}${if_match ${cpu cpu2} < 10}00${cpu cpu2}\
${else}${if_match ${cpu cpu2} < 100}0${cpu cpu2}\
${else}${cpu cpu2}\
${endif}${endif}·${color3}3|${color}${if_match ${cpu cpu3} < 10}00${cpu cpu3}\
${else}${if_match ${cpu cpu3} < 100}0${cpu cpu3}\
${else}${cpu cpu3}\
${endif}${endif}·${color3}A|${color}${color3}${if_match ${cpu cpu0} < 10}00${cpu cpu0}\
${else}${if_match ${cpu cpu0} < 100}0${cpu cpu0}\
${else}${cpu cpu0}\
${endif}${endif} % ${color6}GPU ${color8}${nvidia temp}° ${color3}Vid ${color}${nvidia gpufreq} Mhz${color3} MEM ${color}${nvidia memfreq} Mhz ${color6}MOBO${color8} ${platform f71882fg.2560 temp 2}°${color}
```

**The Clock:**
```
#=== borrowed from: === Voyager Linux === http://voyager.legtux.org/ =========
#                               conkyrc_orange
#
#  author  : SLK
#  version : v2011011601
#  license : Distributed under the terms of GNU GPL version 2 or later
#
#=== Modified by: Sector11 09 Oct 12 =========================================
###  Begin Window Settings  ##################################################
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
#own_window_colour black
own_window_class Conky
own_window_title Clock

### ARGB can be used for real transparency
### NOTE that a composite manager is required for real transparency.
### This option will not work as desired (in most cases) in conjunction with
### own_window_type override
own_window_argb_visual yes

### When ARGB visuals are enabled, this use this to modify the alpha value
### Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
#own_window_argb_value 200

# Use the Xdbe extension? (eliminates flicker)
# It is highly recommended to use own window with this one
# so double buffer won't be so big.
double_buffer yes

minimum_size 156 0 ## width, height
maximum_width 156  ## width

gap_x 5 # left-right
gap_y 5 # up-down

alignment top_left
###################################################  End Window Settings  ###
###  Font Settings  #########################################################
# Use Xft (anti-aliased font and stuff)
use_xft yes
xftfont WenQuanYi Micro Hei Mono:size=8

# Alpha of Xft font. Must be a value at or between 1 and 0 ###
xftalpha 0
# Force UTF8? requires XFT ###
override_utf8_locale yes

draw_shades no
default_shade_color black

draw_outline no # amplifies text if yes
default_outline_color black

uppercase no
######################################################  End Font Settings  ###
###  Color Settings  #########################################################
default_shade_color grey
default_outline_color black

default_color DCDCDC #220 220 220    Gainsboro
color0 8FBC8F #143 188 143    DarkSeaGreen
color1 778899 #119 136 153    LightSlateGray
color2 FF8C00 #255 140   0    DarkOrange
color3 7FFF00 #127 255   0    Chartreuse
color4 FFA07A #255 160 122    LightSalmon
color5 FFDEAD #255 222 173    NavajoWhite
color6 00BFFF #  0 191 255    DeepSkyBlue
color7 00FFFF #  0 255 255    Cyan
color8 FFFF00 #255 255   0    Yellow
color9 B22222 #178  34  34    FireBrick
#####################################################  End Color Settings  ###
###  Borders Section  ########################################################
draw_borders no
# Stippled borders?
stippled_borders 0
# border margins
border_inner_margin 0
border_outer_margin 0
# border width
border_width 0
# graph borders
draw_graph_borders no #yes
default_graph_size 15 40
#####################################################  End Borders Secton  ###
###  Miscellaneous Section  ##################################################

# Boolean value, if true, Conky will be forked to background when started.
background no

# Adds spaces around certain objects to stop them from moving other things
# around, this only helps if you are using a mono font
# Options: right, left or none
use_spacer none

# Default and Minimum size is 256 - needs more for single commands that
# "call" a lot of text IE: bash scripts
text_buffer_size 256

# Subtract (file system) buffers from used memory?
no_buffers yes

# change GiB to G and MiB to M
short_units yes

# Like it says, ot pads the decimals on % values
# doesn't seem to work since v1.7.1
pad_percents 2

##############################################  End Miscellaneous Section  ###
###  LUA Settings  ###########################################################
## Above and After TEXT - requires a composite manager or blinks.
##
# lua_load ~/Conky/LUA/draw-bg.lua
#TEXT
#${lua conky_draw_bg 10 0 0 0 0 0x000000 0.6}
#
## ${lua conky_draw_bg corner_radius x_position y_position width height color alpha}
##
## OR Both above TEXT (No composite manager required - no blinking!)
#
lua_load ~/Conky/LUA/draw-bg.lua
lua_draw_hook_pre draw_bg 10 0 0 0 0 0x000000 0.3
#
lua_load ~/.conky/conky5/clock_conky.lua
lua_draw_hook_post main
#
#######################################################  End LUA Settings  ###
# The all important - How often conky refreshes.
# If you have a "Crey" try: 0.2 - smokin' - but watch the CPU useage go UP!
update_interval 1


TEXT
${voffset 55}${goto 55}${color7}${font White Rabbit:size=22}${time %e}${color1}${goto 45}${font WenQuanYi Micro Hei Mono:size=10}${time %a}
${goto 55}${color2}${font WenQuanYi Micro Hei Mono:size=9}${time %b}${color3} ${font WenQuanYi Micro Hei Mono:size=12}${time %y}${font}







```
[color=red]**NOTE:**[/color] 6 blank lines at the end.

**clock_conky.lua**
```
--==============================================================================
--  Modifired from: conky_orange.lua
--  author  : SLK
--  version : v2011011601
--  license : Distributed under the terms of GNU GPL version 2 or later
--
--  Sector11: 09 Oct 12 - clock_conky.lua
--==============================================================================

require 'cairo'

--------------------------------------------------------------------------------
--                                                                    clock DATA
-- HOURS
clock_h = {
    {
    name='time',                   arg='%H',                    max_value=12,
    x=78,                          y=80,
    graph_radius=53,
    graph_thickness=3,
    graph_unit_angle=30,           graph_unit_thickness=30,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.0,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.3,
    txt_radius=34,
    txt_weight=1,                  txt_size=10.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.6,
    graduation_radius=53,
    graduation_thickness=6,        graduation_mark_thickness=2,
    graduation_unit_angle=30,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    },
}
-- MINUTES
clock_m = {
    {
    name='time',                   arg='%M',                    max_value=60,
    x=78,                          y=80,
    graph_radius=57,
    graph_thickness=2,
    graph_unit_angle=6,            graph_unit_thickness=6,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.3,
    txt_radius=70,
    txt_weight=0,                  txt_size=9.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.6,
    graduation_radius=57,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=30,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    },
}
-- SECONDS
clock_s = {
    {
    name='time',                   arg='%S',                    max_value=60,
    x=78,                          y=80,
    graph_radius=50,
    graph_thickness=2,
    graph_unit_angle=6,            graph_unit_thickness=2,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.0,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.2,
    txt_radius=40,
    txt_weight=0,                  txt_size=12.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.3,
    graduation_radius=0,
    graduation_thickness=0,        graduation_mark_thickness=0,
    graduation_unit_angle=0,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.0,
    },
}

--------------------------------------------------------------------------------
--                                                                 rgb_to_r_g_b
-- converts color in hexa to decimal
--
function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

-------------------------------------------------------------------------------
--                                                            angle_to_position
-- convert degree to rad and rotate (0 degree is top/north)
--
function angle_to_position(start_angle, current_angle)
    local pos = current_angle + start_angle
    return ( ( pos * (2 * math.pi / 360) ) - (math.pi / 2) )
end

-------------------------------------------------------------------------------
--                                                              draw_clock_ring
-- displays clock
--
function draw_clock_ring(display, data, value)
    local max_value = data['max_value']
    local x, y = data['x'], data['y']
    local graph_radius = data['graph_radius']
    local graph_thickness, graph_unit_thickness = data['graph_thickness'], data['graph_unit_thickness']
    local graph_unit_angle = data['graph_unit_angle']
    local graph_bg_colour, graph_bg_alpha = data['graph_bg_colour'], data['graph_bg_alpha']
    local graph_fg_colour, graph_fg_alpha = data['graph_fg_colour'], data['graph_fg_alpha']

    -- background ring
    cairo_arc(display, x, y, graph_radius, 0, 2 * math.pi)
    cairo_set_source_rgba(display, rgb_to_r_g_b(graph_bg_colour, graph_bg_alpha))
    cairo_set_line_width(display, graph_thickness)
    cairo_stroke(display)

    -- arc of value
    local val = (value % max_value)
    local i = 1
    while i <= val do
        cairo_arc(display, x, y, graph_radius,(  ((graph_unit_angle * i) - graph_unit_thickness)*(2*math.pi/360)  )-(math.pi/2),((graph_unit_angle * i) * (2*math.pi/360))-(math.pi/2))
        cairo_set_source_rgba(display,rgb_to_r_g_b(graph_fg_colour,graph_fg_alpha))
        cairo_stroke(display)
        i = i + 1
    end
    local angle = (graph_unit_angle * i) - graph_unit_thickness

    -- graduations marks
    local graduation_radius = data['graduation_radius']
    local graduation_thickness, graduation_mark_thickness = data['graduation_thickness'], data['graduation_mark_thickness']
    local graduation_unit_angle = data['graduation_unit_angle']
    local graduation_fg_colour, graduation_fg_alpha = data['graduation_fg_colour'], data['graduation_fg_alpha']
    if graduation_radius > 0 and graduation_thickness > 0 and graduation_unit_angle > 0 then
        local nb_graduation = 360 / graduation_unit_angle
        local i = 1
        while i <= nb_graduation do
            cairo_set_line_width(display, graduation_thickness)
            cairo_arc(display, x, y, graduation_radius, (((graduation_unit_angle * i)-(graduation_mark_thickness/2))*(2*math.pi/360))-(math.pi/2),(((graduation_unit_angle * i)+(graduation_mark_thickness/2))*(2*math.pi/360))-(math.pi/2))
            cairo_set_source_rgba(display,rgb_to_r_g_b(graduation_fg_colour,graduation_fg_alpha))
            cairo_stroke(display)
            cairo_set_line_width(display, graph_thickness)
            i = i + 1
        end
    end

    -- text
    local txt_radius = data['txt_radius']
    local txt_weight, txt_size = data['txt_weight'], data['txt_size']
    local txt_fg_colour, txt_fg_alpha = data['txt_fg_colour'], data['txt_fg_alpha']
    local movex = txt_radius * (math.cos((angle * 2 * math.pi / 360)-(math.pi/2)))
    local movey = txt_radius * (math.sin((angle * 2 * math.pi / 360)-(math.pi/2)))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, txt_weight);
    cairo_set_font_size (display, txt_size);
    cairo_set_source_rgba (display, rgb_to_r_g_b(txt_fg_colour, txt_fg_alpha));
    cairo_move_to (display, x + movex - (txt_size / 2), y + movey + 3);
    cairo_show_text (display, value);
    cairo_stroke (display);
end

-------------------------------------------------------------------------------
--                                                               go_clock_rings
-- loads data and displays clock
--
function go_clock_rings(display)
    local function load_clock_rings(display, data)
        local str, value = '', 0
        str = string.format('${%s %s}',data['name'], data['arg'])
        str = conky_parse(str)
        value = tonumber(str)
        draw_clock_ring(display, data, value)
    end

    for i in pairs(clock_h) do
        load_clock_rings(display, clock_h[i])
    end
    for i in pairs(clock_m) do
        load_clock_rings(display, clock_m[i])
    end
    for i in pairs(clock_s) do
        load_clock_rings(display, clock_s[i])
    end
end

-------------------------------------------------------------------------------
--                                                                         MAIN
function conky_main()
    if conky_window == nil then
        return
    end

    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local display = cairo_create(cs)

--[[    local updates = conky_parse('${updates}')
    update_num = tonumber(updates)

    if update_num > 5 then ]]
        go_clock_rings(display)
        go_gauge_rings(display)
    --end

end

```

---

### Post by Happy Wash on 2012-10-28
Good day everybody,

Can somebody explain everything about Rhythmbox and Conky.
I see on my pc many files from Rhythmbox like: conkyRhythmbox and conkyRhythmbox.py. This is in my personal and usr/share.

I just started with Ubuntu and just install Conky -Colors.
Off course Rhythmbox is not working.
Also that i try to fix.

So if anybody can help me with this i will appreciate that.

Mario

---

### Post by mekt3k on 2013-01-27
I am having trouble running the conkyRhythmbox script on conky. And when I tried the command /usr/share/conkyrhythmbox/conkyRhythmbox.py --datatype=TI on the terminal, it returns the value "Unknown". What could be possibly wrong?

---

