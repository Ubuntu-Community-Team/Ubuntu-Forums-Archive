---
title: "Run command when computer is idle"
date: 2008-11-10
forum: General Help
---

### Post by easoukenka on 2008-11-10
Basically how can I execute a command when computer is idle then execute another command when computer is no longer idle.

I am interested in starting and stopping rtorrent in daemon mode when computer is idle.  I already have crons setup for it etc I do not need help with this part.

I will also like to add this to other computers on my network.  So if someone else is not idle it will close mine with a simple ssh kill.  Then start again when they go idle.  This part is no problem for me to do on my own.

If I can get the above knowledge from someone else I will post any scripts that I create and a tutorial for you.  Thanks in advance.

---

### Post by ciscosurfer on 2008-11-10
Perhaps using [inotify-tools]("http://packages.ubuntu.com/intrepid/inotify-tools") would help in this situation.

---

### Post by easoukenka on 2008-11-10
Yeah that might do it I will start diving into documentation thanks for getting me started. 

Well it looks like it may not be for me.  Obviously possible but looks way to complicated for me :)  Thank you for input though I will probly use this tool for other things.

---

### Post by easoukenka on 2008-11-17
I have found my solution took some good googling was already kinda answered on this form at [http://ubuntuforums.org/showthread.php?p=3219643](http://ubuntuforums.org/showthread.php?p=3219643)

I hope someone else finds this useful it is really nice now my torrents are always going when the screensaver is on and killed when I am back.  No more forgetting to start my torrents or having to deal with my slow internet when they are running!  

Ok so with a few changes and the directions followed I came up with this.  Just follow the directions on the other thread  and replace the script on that page with this if you use rtorrent

#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
    if (m/^\s+boolean true/) {
        #when screensaver activates, run the following commands
        system("/home/eric/compiled/scripts/rtorrentstart");
        system("touch /home/eric/rtorrenthasstarted");
    } elsif (m/^\s+boolean false/) {
        #when screensaver deactivates, run the following commands
        system("kill `pgrep rtorrent`");
        system("touch /home/eric/rtorrenthasbeenkilled");
    }
}

---

### Post by ciscosurfer on 2008-11-17
Nice.  I might try something similar to this also.  You can also do something like```
system("killall rtorrent");
```instead of killing the processes by pid/pgrep.

---

### Post by easoukenka on 2008-11-18
Thank you I thought I would show you all my rtorrentstart script in case anyone is wondering how to get it running in complete daemon mode and are not sure how to start it themselves it took me some time to get this working with all the killing of rtorrent I needed to run screen -wipe or it wouldn't start sometimes.  

#!/bin/bash
screen -wipe #with all the improper shutdowns sometimes a screen is left hanging
screen -dmS programs /usr/bin/rtorrent

---

