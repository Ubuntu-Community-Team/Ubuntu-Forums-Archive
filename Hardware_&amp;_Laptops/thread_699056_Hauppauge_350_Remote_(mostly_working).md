---
title: "Hauppauge 350 Remote (mostly working)"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by marvin1969 on 2008-02-17
All,
   I have a new installation of Mythbuntu 7.04 on an AMD-64 mobile with two Hauppauge 350 tuners (using only 1 remote) .  I got the Haupapauge remote (A415-HPG) mostly, but I cannot get some of the additonal buttons to function.  IRW shows them working, and the lirc conf file for it looks fine (I edited the base Hauppauge file to remove any remote other than the one for the 350 with the A415 remote) in /usr/share/lirc/remotes/hauppauge/).  Conf file attached. I even added an entry to the /usr/share/lirc/lirc.hwdb with my new entry so I could have Mythbuntu Control Center pick it up.  This looks to be working fine, but still none of the other special keys works)
    I wrote a quick script to make reading /home/mythtv/.lircrc easier (crazy stuff like sorting and the ability to sort the remotes in the file and create a sorted LIRCRC file), and saw that most of the extra keys (TV, Video, Music, Pictures, Radio, and the 4 color keys) weren't listed, so I created entries for them w/ and w/o configs (neithe worked and the file is attached. I'll even provide the quick/dirty Perl if if anyone wants it.
    When I try to edit the keys in Myth with the remote, none of the new special keys generates anything when I try to set an action to them.  What am I missing?

Thanks.
/home/mythtv/.lircrc
```

begin
    remote = Hauppauge_350
    prog = elisa
    button = Back/Exit
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Down
    config = move_down_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Forward
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Left
    config = move_left_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Menu/i
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = OK
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Rewind
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Right
    config = move_right_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Up
    config = move_up_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Vol+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Vol-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Down
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Forward
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Left
    config = seek -6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = OK
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Replay/SkipBackward
    config = seek -15 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Rewind
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Right
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = SkipForward
    config = seek +15 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Up
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Vol+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Vol-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Blue
    config = B
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Go
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Green
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Menu/i
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Music
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Pictures
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Radio
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Red
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Replay/SkipBackward
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = SkipForward
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Videos
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Yellow
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Back/Exit
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Down
    config = down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Forward
    config = seek_forward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Left
    config = left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Menu/i
    config = menu
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Play
    config = play_pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Rewind
    config = seek_backward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Right
    config = right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Up
    config = up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Vol+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Vol-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Ch+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Ch-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Down
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Forward
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Left
    config = key-nav-left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = OK
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Replay/SkipBackward
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Right
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = SkipForward
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Up
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Vol+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Vol-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Down
    config = EventDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Forward
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Left
    config = EventLeft
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = OK
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Replay/SkipBackward
    config = EvenPrior
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Rewind
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Right
    config = EventRight
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = SkipForward
    config = EventNext
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Up
    config = EventUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Vol+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Vol-
    config = Volume-
    repeat = 0
    delay = 0
end



```

/usr/share/lirc/remotes/hauppauge/lirc.conf.my350
```

#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote

```

And the PERL script if anyone would like it (it was quick/dirty, but it works well and makes reading the .LIRCRC much easier when you want to know what apps are configured with what buttons)
LIRCSORT.PL
```

#!/usr/bin/perl

# Input file
$lircrc     =   '.lircrc';
# Output file
$sortLirc   =   'lircrc_sort';
# Default values for key repeat and delay
$repeat     =   '0';
$delay      =   '0';
$makeNewFile=   0;
# Open the input file or tell me why
open (INP, "< $lircrc") || die "Error opening LIRCRC \"$lircrc\" \: $!\n";


while (<INP>)
{
    chomp;
    #print "LINE: $_\n";
    $line   =   $_;
    # If this is the end of a block, reset all the flags
    if ( $line =~ m/^end/g )
    {
        #print "\tSection End.\n";
        $inBlock    =   0;
        $app        =   undef;
        $remote     =   undef;
        $remoteApp  =   undef;
        $button     =   undef;
        $config     =   undef;
    }
    #  This will get the name of the remote for this block and saves it to the list of remotes
    if ($inBlock && ( $line =~ m/(\s+remote =\s)/g ) )
    {
        # $' = everything AFTER the pattern match.
        #print "\t\tRemote = $'\n";
        # $' = everything AFTER the pattern match.
        $remote        =   $';
        $remotes{$'}   =   1;
    }
    #  This will get the name of the app for this block and saves it to the list of apps
    if ($inBlock && ( $line =~ m/(\s+prog =\s)/g ) )
    {
        # $' = everything AFTER the pattern match.
        #print "\t\tProg = $'\n";
        # $' = everything AFTER the pattern match.
        $app        =   $';
        $remoteApp  =   $remote . '||' . $app;
        $remoteApps{$remoteApp}   =   1;
    }
    # This will get the name of the button for this block and save it.
    if ($inBlock && ( $line =~ m/(\s+button =\s)/g ) )
    {
        # $' = everything AFTER the pattern match.
        #print "\t\tButton: $'\n";
        $button =   $';
    }
    # This will get the configuratio for the button (what keyboard stroke/app command it maps to)
    if ($inBlock && ( $line =~ m/(\s+config =\s)/g ) )
    {
        # $' = everything AFTER the pattern match.
        #print "\t\tConfig: $'\n";
        $config =   $';
        #print "remoteApp    =   $remoteApp\n";
        $$remoteApp{$button}  =   $config;
    }
    if ( $line =~ m/^begin/g )
    {
        #print "\tSection Begin.\n";
        $inBlock    =   1;
    }
}
open (OUT, "> $sortLirc") || die "Error with output file \"$sortLirc\": $!\n";

# Get the list of names of remotes+applications and sort it.
foreach (sort (keys (%remoteApps))) 
{
    # Get the name of the remote+app
    $remoteApp    =   $_;
    # Split the remote and app names for individual usage
    ($remt,$appl) =   split (/\|\|/, $remoteApp, 2);
    # Print to the screen the name of the remote, application and header columns for the data 
    print "\nREMOTE:  $remt\n  Application:  $appl\n";
    print "\tButton:\t Key/Cmd: \n";
    print "\t=====================\n";
    ($remt, $appl)  =   undef;
    # Get the list of buttons for the remote+application
    @tmp    =   keys (%$remoteApp);
    #  For each of the sorted button names...
    foreach (sort @tmp)
    {
        # get the name of the remote and the application
        ($rmt,$application) =   split (/\|\|/, $remoteApp, 2);
        # Print the button name and assigned keystroke/command
        print "\t$_\t$$remoteApp{$_}\n";
        # Print the sorted list to the output file
        if ($makeNewFile)
        {
            select OUT;
        }
        else 
        {
            select NULL;
        }
        print "begin\n";
        #           Name of the remote
        print "    remote = $rmt\n";
        #           Name of the application
        print "    prog = $application\n";
        #           Name of the button being configured
        print "    button = $_\n";
        #           Command/Keystroke being assigned to the button
        print "    config = $$remoteApp{$_}\n";
        #           Repetitions to allow
        print "    repeat = $repeat\n";
        #           Delay in repetitions to allow
        print "    delay = $delay\n";
        print "end\n\n";
        select STDOUT;
    }
    
}

```

---

### Post by marvin1969 on 2008-02-23
I have continued to play around with this, but have made no progress.  Can anyone provide a suggestion?

TIA,
M

---

