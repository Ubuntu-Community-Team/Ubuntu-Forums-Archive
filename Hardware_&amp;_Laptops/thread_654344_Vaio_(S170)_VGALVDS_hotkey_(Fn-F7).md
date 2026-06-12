---
title: "Vaio (S170) VGA/LVDS hotkey (Fn-F7)"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by thrutchy on 2007-12-31
Hi everyone.  This is my first post.  I'm new to debian/ubuntu.

Short story: Anybody have success with getting the LVDS/VGA hotkey (Fn-F7) to work on a sony?  More specifically an S-series S170, maybe?

Long story:

I've installed ubuntu 7.10 on two laptops (dell d420 & sony s170) over the holidays.  I had Mandrake 10 on the sony previously and also tried to install Fedora 8 on it.  Ubuntu 7.10 clearly did a better job at getting the devices set up than the others I used.

The main problems I had on both installations had to do with setting up the external monitor. The first was getting the X server to just connect to the external monitor and use the right mode (1680x1050 LCD).  Fortunately, both laptops have video that supports xrandr (intel 945 on the dell and radeon 9600 on the sony) and I was able to get some xorg.conf files that give me dual-head displays in similar ways.  For those interested, the resources I used to hack these together were:

[http://xorg.freedesktop.org/archive/X11R7.0/doc/html/radeon.4.html](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/radeon.4.html)
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)
[http://ubuntuforums.org/showthread.php?t=581947](http://ubuntuforums.org/showthread.php?t=581947)

For dual-head, one annoying thing was that I wasn't able to select which monitor was the primary that gets the panel(s).  Or better yet have each get there own panel.  The intel driver seemed to treat the external monitor as the primary and the radeon driver treated the internal LCD as the primary, so I ended up with two different setups.  I wanted the orientation between internal/external to be left/right, but the virtual size was limited to 2048 horizontally for the intel driver so I had to make the orientation top/bottom.  The virtual size was quite limited for both video setups.

One more key thing that I found in setting up the external monitor that I didn't see mentioned elsewhere was that I needed to put modelines for the external monitor and give a PreferredMode.  I found the right modelines by setting up the xorg.conf files from scratch with the external monitor plugged in.  Without these, X gave the right resolution, but it was compressed and shifted.  So the xorg.conf setup (forgot what it was) detected the external monitor better than X.

The last part of the external monitor setup was the Fn keys for switching between external and internal.  This kind-of works out of the box for the dell (Fn-F8).  When the external is plugged in, it turns it on  and moves and resizes the panel to the external monitor.  It won't cycle through any other modes (internal off/external on, or even back to internal on/external off).  It also won't give me the dual-head config I have in my xorg.conf (which works when starting the session with the external plugged in).  Unplugging the external and pressing the key again will get you back to where you started.  I'd like to know how to customize this further, but I haven't found how to setup the dell Fn keys.

For the sony s170 on the other hand, I haven't been able to get anything out of the equivalent hotkey (Fn-F7).  All other Fn keys work.  I have yet to find out how to configure this.  I've already tried this:

[http://ubuntuforums.org/showthread.php?p=4028611](http://ubuntuforums.org/showthread.php?p=4028611)

It does appear to use acpi for the hotkey actions since I disabled one of the scripts in /etc/acpi and that disabled the key.  So, the above does seem to be on the right track for my hotkeys.

---

### Post by thrutchy on 2008-01-01
I finally figured out how to setup the sony for external video (w/ hotkey switching).  Here's what I found:

* According to /var/log/acpid, Fn-F7 for the S170 generates:
    sony/hotkey SPIC 00000001 00000012

    The only difference vs. the TZ series was "SPIC" instead of "HKEY".

* Handling multiple types of external monitors was problematic.  A PreferredMode for a higher resolution monitor seemed to screw up lower resolution monitors (even though it knew it couldn't use those modes).  Instead I had my video switch script set the specific mode for specific monitor resolutions.

* I still haven't figured out how to specify my own script for the dell d420.  It does generate an event the matches the "videobtn" event (video.* 00000080), but it looks like the X server is doing the video switching (notifying client <X pid>).  When I setup a script to be called, it is called after the X server is notified.  I was hoping there was an xorg.conf option to turn this off, but I couldn't find one.

* The script I'm using for video rotating is below.  It rotates through 3 modes: internal, internal/external, and external.  For the internal/external mode, it looks at the virtual screen size and tries to make the two monitors use non-overlapping viewports.  It first tries to see if left/right fits and then tries above/below.  To get dual-head working all that you should need with this script is an xorg.conf that uses an xrandr compliant driver (i.e. intel, radeon, etc) and a virtual screen size that can fit both monitors either horizontally or vertically.


#!/usr/bin/perl

#use strict;

# use this to specify a specific mode for a resolution
# alternative to PreferredMode in monitor section
my(%modes) = (
        "1680x1050" => "1680x1050V",
);
$ARGV[0] = 0 if !defined($ARGV[0]);
$ARGV[1] = 0 if !defined($ARGV[1]);
$ARGV[2] = "LVDS" if !defined($ARGV[2]);
my($SERVER) = qr{$ARGV[0]}; # X server
my($SCREEN) = qr{$ARGV[1]}; # screen in server
my($PRIMARY) = qr{$ARGV[2]}; # primary output (always position at 0x0)

my($user, $tty, $display, $server, $screen);

open(W, "w -h -s |") or die("$!: w -h -s");
while (<W>) {
    ($user, $tty, $display) = split(' ');
    $display=~/^\:(\d+)(\.(\d+))?$/ or next;
    ($server, $screen) = ($1, $2 ? $3 : 0);
    last if $server=~$SERVER and $screen=~$SCREEN;
}
close(W);

open(XRANDRQ, "su - $user -c 'DISPLAY=$display xrandr -q' |") or die("$!: xrandr -q");

# find our screen first
my(@maximum_res);
while (<XRANDRQ>) {
    #print;
    if (/^Screen $screen:.* maximum (\d+)\s*x\s*(\d+)/) {
        @maximum_res = ($1,$2);
        last;
    }
}

my(%outputs);
my(@primary_res) = (0,0,-1,-1);
my(@secondary_res) = (0,0,-1,-1);
while (<XRANDRQ>) {
    #print;
    if (/^Screen \d+:/) {
        # ignore other screens
        last;
    } elsif (/^(\S+) connected ((\d+)\s*x\s*(\d+)\s*\+\s*(\d+)\s*\+\s*(\d+))?/) {
        # connected output/monitor
        my($output) = $1;
        my($res);
        if (!$2) {
            # the output is off (need to find preferred mode/resolution)
            while (<XRANDRQ>) {
                # assume mode matches this pattern for getting resolution
                # a + after the mode seems to indicate the preferred mode
                if (/^\s*(\d+)x(\d+).*\+/) {
                    $res = [$1,$2,-1,-1];
                    last;
                }
            }
        } else {
            # the output is on with given resolution
            $res = [$3,$4,$5,$6];
        }
        $outputs{$output} = $res;
        my($r) = ($output=~$PRIMARY) ? \@primary_res : \@secondary_res;
        for my $i (0..$#$res) {
            if ($res->[$i]>$r->[$i]) {
                $r->[$i] = $res->[$i];
            }
        }
    } elsif (/^(\S+) disconnected/) {
        # disconnected output/monitor
        $outputs{$1} = [];
    }
}

close(XRANDRQ);

#print("[@maximum_res]\n");
#while (my($output,$res)=each(%outputs)) { print("$output => [@$res]\n"); }

if ($primary_res[0]>0 and $primary_res[3]<0) {
    # turn primary on if it is connected and off
    $primary_res[2] = 0;
    $primary_res[3] = 0;
    # turn secondary off
    $secondary_res[2] = -1;
    $secondary_res[3] = -1;
} elsif ($secondary_res[0]>0 and $secondary_res[3]<0) {
    # turn secondary on if it is connected and off
    $secondary_res[2] = 0;
    $secondary_res[3] = 0;
    # shift secondary from primary if room in virtual screen
    for my $i (0..1) {
        if ($primary_res[$i]+$secondary_res[$i]<=$maximum_res[$i]) {
            $secondary_res[2+$i] = $primary_res[$i]
        }
    }
    # primary is likely already on
    $primary_res[2] = 0;
    $primary_res[3] = 0;
} elsif ($secondary_res[3]>=0) {
    # turn primary off when both are on (or primary is disconnected)
    $primary_res[2] = -1;
    $primary_res[3] = -1;
    # put secondary back to 0x0
    $secondary_res[2] = 0;
    $secondary_res[3] = 0;
} elsif ($primary_res[0]>0) {
    # should only get here if secondary is disconnected
    $primary_res[2] = 0;
    $primary_res[3] = 0;
}

my($command) = "xrandr --screen $screen";
while (my($output,$res)=each(%outputs)) {
    $command .= " --output $output";
    my($r) = ($output=~$PRIMARY) ? \@primary_res : \@secondary_res;
    if ($res->[0]<=0 or $r->[3]<0) {
        $command .= " --off";
    } else {
        my($xy) = $res->[0]."x".$res->[1];
        my($mode) = $modes{$xy};
        $mode = defined($mode) ? "--mode $mode" : "--auto";
        $command .= " $mode --pos $r->[2]x$r->[3]";
    }
}

#print(join(" ", "su", "-", $user, "-c", "DISPLAY=$display $command"), "\n");
exec("su", "-", $user, "-c", "DISPLAY=$display $command");

---

### Post by thrutchy on 2008-01-01
Here is another try at that script this time wrapped in code tags:

```


#!/usr/bin/perl

#use strict;

# use this to specify a specific mode for a resolution
# alternative to PreferredMode in monitor section
my(%modes) = (
        "1680x1050" => "1680x1050V",
);
$ARGV[0] = 0 if !defined($ARGV[0]);
$ARGV[1] = 0 if !defined($ARGV[1]);
$ARGV[2] = "LVDS" if !defined($ARGV[2]);
my($SERVER) = qr{$ARGV[0]}; # X server
my($SCREEN) = qr{$ARGV[1]}; # screen in server
my($PRIMARY) = qr{$ARGV[2]}; # primary output (always position at 0x0)

my($user, $tty, $display, $server, $screen);

open(W, "w -h -s |") or die("$!: w -h -s");
while (<W>) {
    ($user, $tty, $display) = split(' ');
    $display=~/^\:(\d+)(\.(\d+))?$/ or next;
    ($server, $screen) = ($1, $2 ? $3 : 0);
    last if $server=~$SERVER and $screen=~$SCREEN;
}
close(W);

open(XRANDRQ, "su - $user -c 'DISPLAY=$display xrandr -q' |") or die("$!: xrandr -q");

# find our screen first
my(@maximum_res);
while (<XRANDRQ>) {
    #print;
    if (/^Screen $screen:.* maximum (\d+)\s*x\s*(\d+)/) {
        @maximum_res = ($1,$2);
        last;
    }
}

my(%outputs);
my(@primary_res) = (0,0,-1,-1);
my(@secondary_res) = (0,0,-1,-1);
while (<XRANDRQ>) {
    #print;
    if (/^Screen \d+:/) {
        # ignore other screens
        last;
    } elsif (/^(\S+) connected ((\d+)\s*x\s*(\d+)\s*\+\s*(\d+)\s*\+\s*(\d+))?/) {
        # connected output/monitor
        my($output) = $1;
        my($res);
        if (!$2) {
            # the output is off (need to find preferred mode/resolution)
            while (<XRANDRQ>) {
                # assume mode matches this pattern for getting resolution
                # a + after the mode seems to indicate the preferred mode
                if (/^\s*(\d+)x(\d+).*\+/) {
                    $res = [$1,$2,-1,-1];
                    last;
                }
            }
        } else {
            # the output is on with given resolution
            $res = [$3,$4,$5,$6];
        }
        $outputs{$output} = $res;
        my($r) = ($output=~$PRIMARY) ? \@primary_res : \@secondary_res;
        for my $i (0..$#$res) {
            if ($res->[$i]>$r->[$i]) {
                $r->[$i] = $res->[$i];
            }
        }
    } elsif (/^(\S+) disconnected/) {
        # disconnected output/monitor
        $outputs{$1} = [];
    }
}

close(XRANDRQ);

#print("[@maximum_res]\n");
#while (my($output,$res)=each(%outputs)) { print("$output => [@$res]\n"); }

if ($primary_res[0]>0 and $primary_res[3]<0) {
    # turn primary on if it is connected and off
    $primary_res[2] = 0;
    $primary_res[3] = 0;
    # turn secondary off
    $secondary_res[2] = -1;
    $secondary_res[3] = -1;
} elsif ($secondary_res[0]>0 and $secondary_res[3]<0) {
    # turn secondary on if it is connected and off
    $secondary_res[2] = 0;
    $secondary_res[3] = 0;
    # shift secondary from primary if room in virtual screen
    for my $i (0..1) {
        if ($primary_res[$i]+$secondary_res[$i]<=$maximum_res[$i]) {
            $secondary_res[2+$i] = $primary_res[$i]
        }
    }
    # primary is likely already on
    $primary_res[2] = 0;
    $primary_res[3] = 0;
} elsif ($secondary_res[3]>=0) {
    # turn primary off when both are on (or primary is disconnected)
    $primary_res[2] = -1;
    $primary_res[3] = -1;
    # put secondary back to 0x0
    $secondary_res[2] = 0;
    $secondary_res[3] = 0;
} elsif ($primary_res[0]>0) {
    # should only get here if secondary is disconnected
    $primary_res[2] = 0;
    $primary_res[3] = 0;
}

my($command) = "xrandr --screen $screen";
while (my($output,$res)=each(%outputs)) {
    $command .= " --output $output";
    my($r) = ($output=~$PRIMARY) ? \@primary_res : \@secondary_res;
    if ($res->[0]<=0 or $r->[3]<0) {
        $command .= " --off";
    } else {
        my($xy) = $res->[0]."x".$res->[1];
        my($mode) = $modes{$xy};
        $mode = defined($mode) ? "--mode $mode" : "--auto";
        $command .= " $mode --pos $r->[2]x$r->[3]";
    }
}

#print(join(" ", "su", "-", $user, "-c", "DISPLAY=$display $command"), "\n");
exec("su", "-", $user, "-c", "DISPLAY=$display $command");


```

---

