---
title: "Reverse Engineer Small Xfree86 Script"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by PhillD on 2007-03-26
Hi Everyone,

Over the past few weeks I have been trying to setup a Gunze Touch screen monitor on Xubuntu.  After lots of frustration and many posts to this message board, I finally have it working, but not very well!

The touch screen calibration is way off and I need to figure out how to set it correctly.  The monitor driver package did come with a configuration utility but it is way old and written for XFree86 X server and wont work on ubuntu’s Xorg.  I was wondering if someone could take a look at the calibration script and see exactly what it creates and how it insets the calibration data to the driver.

From what I can deduce, the calibration information is currently stored directly in the driver file as the calibration details I placed in the xorg.conf file do not get loaded from what I can see in the Xorg.0.log file.

The log file basically says that it loads the driver successfully but there is no calibration data found or invalid settings and that it is using the defaults.  The defaults must be stored in the driver file.  The calibration data that I do have in the xorg.conf file were taken straight from the manual for the driver so I don’t know how they can be invalid.  I must be missing something here.  Can someone please take a look at the following script and tell me what I would need to do to set new calibration parameters.

```

#!/usr/bin/wish
# -*-tcl-*-
# This comes from gunze-setup, distributed in gpm.
#
# This program is executed by wish, if there is no DISPLAY it will choke.
# Text mode support has been removed.

# The Gunze touchscreens don't adapt their output to calibration, so
# we must save calibration information somewhere...

# A command line argument is compulsory
set error 0
if [llength $argv]!=1 {
    set error 1
} else {
    if [string match /dev/* $argv] {
	if [string first tty $argv]>0 {
	    set mode ser
	} else {
	    set mode ps2
	}
    } else {
	set error 1
    }
}
if $error {
    puts stderr \
	    "$argv0: Need a touchscreen device like /dev/ttyS0, /dev/psaux, or /dev/gunzets (USB device)"
    exit 1
}

proc which cmd {
    global env
    foreach n [split $env(PATH) :] {
        if [file executable $n/$cmd] {return $n/$cmd}
    }
    error "$cmd: no such command"
}
if {[catch {which gunzets_control}]} {
    puts stderr "gunzets_control must be in your command search path"
    exit 1
}

# Set useful info
set datafile /etc/gunzets.calib
set rawdevice $argv
set cfgdevice $argv

puts "Calibration program for USB Gunze touch-screens"

# check generic permission
set who [exec whoami]
if [string compare $who root] {
    puts stderr "$argv: You must be root to be able to run this program"
    exit 1
}

# check if we can access this file
if [catch {set F [open $datafile a]} err] {
    puts stderr "$argv0: Can't open $datafile: $err"
    exit 1
}
close $F

# an abort procedure, and one to read touchscreen data
proc do_abort {msg} {
    global D mode
    wm withdraw .
    puts stderr $msg
    catch {close $D}
    exec gunzets_control on
    exit 1
}

proc get_position file {
    global rawdevice mode

    while 1 {
	#Decode input according to the type of device
	if {"$mode"=="ser"} {
	    fconfigure $file -translation cr
	    gets $file string
	    if [scan $string "%c%d,%d"  touch x y]!=3 {
		do_abort  "Received wrong data \"$string\" from $rawdevice"
	    }
	    if {$touch!=82 && $touch!=84} {
		    puts stderr "Warning: wrong first byte in \"$string\""
	    }
	    if $x>4095||$y>4095 {
		    puts stderr "Warning: wrong data in \"$string\""
	    }
	    # "R" is 82, "T" is 84
	    if {$touch==82} {set touch 0} else {set touch 1}
	} else {
	    #PS2
	    set s [read $file 3]
	    scan $s "%c %c %c" a b c
	    puts stderr "data: $a $b $c"
	    if $a<128||$b<128||$c>127 {
		do_abort  "Received wrong data from $rawdevice"
	    }
	    if $c<64 {set touch 0} else {set touch 1}
	    set x [expr (($a-128)<<3) | (($b & 0x70) >> 4)]
	    set y [expr (($b&15) <<6) | (($c & 0x3f))]
	}

	# If release, it's done
	if $touch==0 {
	    return "$sx $sy"
	}
	# If a touch event, save it
	if $touch==1 {
	    set sx $x; set sy $y
	} else {
	    do_abort "Received wrong data \"$string\" from $rawdevice"
	}
    }
}

# Turn the device off
exec gunzets_control off

set wid [winfo screenwidth .]
set hei [winfo screenheight .]
wm geometry . ${wid}x${hei}+0+0

set x [expr $wid/8]
set y [expr $hei/8]
set X [expr $wid - $x]
set Y [expr $hei - $y]
set hx [expr $wid/2]
set hy [expr $hei/2]
set cwid [expr 2*$x]
set chei [expr 2*$y]

# The offset variables account for window manager borders etc
set xoff1 0
set yoff1 0
set xoff2 0
set yoff2 0

proc recanvas {} {
    global x y X Y xoff1 xoff2 yoff1 yoff2
    catch {.l.c delete line}
    catch {.r.c delete line}
    
    set x1 [expr $x-$xoff1]
    set y1 [expr $Y-$yoff1]
    set x2 [expr $X-$xoff2]
    set y2 [expr $y-$yoff2]
    
    .l.c create line [expr $x1-50] $y1 [expr $x1+50] $y1 \
	    -width 3 -fill red -tag line
    .l.c create line $x1 [expr $y1-50] $x1 [expr $y1+50] \
	    -width 3 -fill red -tag line
    
    .r.c create line [expr $x2-50] $y2 [expr $x2+50] $y2 \
	    -width 3 -fill red -tag line
    .r.c create line $x2 [expr $y2-50] $x2 [expr $y2+50] \
	    -width 3 -fill red -tag line
}


pack [frame .l] -side left -expand true -fill both 
pack [frame .m] -side left -expand true -fill both 
pack [frame .r] -side left -expand true -fill both 
pack [canvas .l.c -width $cwid -hei $chei -scrollregion "0 0 $cwid $chei" \
	] -side bottom 
pack [frame .l.f] -expand true -fill both; #filler
pack [canvas .r.c -width $cwid -hei $chei -scrollregion "0 0 $cwid $chei" \
	] -side top
pack [frame .r.f] -expand true -fill both; #filler

pack [label .m.t -text "Gunze Calibrator" -foreground blue] -pady 40
pack [label .m.l -bd 5 -relief raised] -expand true -fill both
pack [label .m.s] -expand true -fill both

bind .l.c <Enter> {
    set xoff1 [expr %X - %x]
    set yoff1 [expr %Y - %y]
    set x1 [expr $x-$xoff1]
    set y1 [expr $Y-$yoff1]

    catch {.l.c delete line}
    
    .l.c create line [expr $x1-50] $y1 [expr $x1+50] $y1 \
	    -width 3 -fill red -tag line
    .l.c create line $x1 [expr $y1-50] $x1 [expr $y1+50] \
	    -width 3 -fill red -tag line
    
    set done1 1
    update
}
bind .r.c <Enter> {
    set xoff2 [expr %X - %x]
    set yoff2 [expr %Y - %y]
    set x2 [expr $X-$xoff2]
    set y2 [expr $y-$yoff2]

    catch {.r.c delete line}

    .r.c create line [expr $x2-50] $y2 [expr $x2+50] $y2 \
	    -width 3 -fill red -tag line
    .r.c create line $x2 [expr $y2-50] $x2 [expr $y2+50] \
	    -width 3 -fill red -tag line

    set done2 1
    update
}

set done1 0; set done2 0

update

.m.l config -text "Please move the mouse towards\n\
	the lower left corner, until a cross\n\
	appears (there's no need to click)"
vwait done1

update

if !$done2 {
    .m.l config -text "Please move the mouse towards\n\
	    the upper right corner, until a cross\n\
	    appears (there's no need to click)"
    vwait done2
}

.m.l config -text "\nWait....\n"
after 1000

.m.l config -text "Please touch the lower-left taget\n\
	and then the upper-right target\n\
	to calibrate the touch screen"
update

set D [open $rawdevice r+]
fconfigure $D -buffering none -translation auto

.m.s configure -text "Calibration started"
update

# Read coordinates
set first [get_position $F]

.l.c itemco line -fill green
.m.s configure -text "First target ok"
update

# Read coordinates
set second [get_position $F]

# support 12bit (Atsushi Nemoto)
if {[lindex $first 0] >= 1024 || [lindex $first 1] >= 1024 || \
       [lindex $second 0] >= 1024 || [lindex $second 1] >= 1024} {
       set first "[expr [lindex $first 0] / 4] [expr [lindex $first 1] / 4]"
       set second "[expr [lindex $second 0] / 4] [expr [lindex $second 1] / 4]"
}

.r.c itemco line -fill green
.m.s configure -text "Second target ok"
update



# Now save the coordinates
set F [open $datafile w]
puts $F "# Calibration coordinates for Gunze USB device"
puts $F "$first $second"
close $F
close $D

exec gunzets_control on

after 500
.m.l configure -text "Ok, press any key to exit"
bind all <Any-KeyPress> exit
vwait forever

```

Thanks

PhillD.

P.S. If you need more technical info please ask and I will be glad to post it.

---

### Post by PhillD on 2007-03-27
Hi Guys,

I poseted this one kinda late yesterday so I just wanted to bring it back up on the radar.

Thanks

PhillD

---

### Post by PhillD on 2007-03-29
Hi,

After 2 days of trying alternative things, I really need someone’s help finding out what the output file from the above script would look like.  I don't need real numbers, or need to know how it works just what the output file would look like.

I already know that the output file would be /etc/gunzets.calib

really need to know the content>

Please I am desperate.

PhillD

---

### Post by PhillD on 2007-03-30
The script cannot execute wish.  This is one of the problems that I had with the last script.  I run Xubuntu and it doesn't have wish installed.  how would i do this?

---

### Post by psyopper on 2007-05-24
Hi,

I popped over here from your other "my boss is a nightmare" thread. I'll leave my comments for that thread there...

Anywho... ever though to try ```
sudo apt-get install wish
``` or try Synaptic and see if it's there. You would be surprised at what you find with "apt-get install <insert esoteric package here>"...

:)

I'd be interested to see what you find with whatever repositories you have installed. Or you could just try here for the X11 Gunze stuff:

[http://repos.opensuse.org/xorg7/Java_Sun-Java-1.5_SUSE_Linux_10.1/i586/]("http://repos.opensuse.org/xorg7/Java_Sun-Java-1.5_SUSE_Linux_10.1/i586/")

Look for X11-input-gunze*

Will this work?

---

