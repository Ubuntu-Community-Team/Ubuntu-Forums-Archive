---
title: "Logitech G15 drivers?"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by Sp@z on 2005-12-26
Has anyone out here heard of any drivers for this keyboard and Linux yet? This keyboard is awesome! The LCD and "G" keys are non working in linux and on the G15 forums there is rumor of someone working on drivers for it and Linux. Also Logitech has released the SDK for this and many ppl say that making a driver for it should be realitivly easy for coders interested. I wouldn't have a clue, but it is worth mentioning. Here is the websight with more info. Thanx all!

[http://www.g15forums.com/](http://www.g15forums.com/)

---

### Post by Vectrox on 2006-04-24
Maybe this is something, havent test it yet, dont have a installation of Linux right now (ashamed)

[http://glyf.livejournal.com/52211.html](http://glyf.livejournal.com/52211.html)

---

### Post by jnorth on 2006-07-13
Sheesh - I thought these things would catch on faster.  Anyway - here's a binary I'm using to talk to the lcd.  It requires you write your own shell script to send output to a named pipe, which then displays on the lcd.

Works ok, but my scripting is not the greatest.  I have it currently so I can see system info, mail count, amarok stats, and I'm trying to get the program button underneath to switch the screens, right now it just alternates.

Supposedly you can send other data to it with this but I'm not an advanced uer, only dangerous :)

Anyway - still looking for something better.

---

### Post by Jaymo on 2006-07-23
Care to link that binary you made? :).

---

### Post by subpar on 2006-08-01
There's something you can get named simply g15lcd, which will also support the Gkeys.

[http://www.waug.at/g15lcd/](http://www.waug.at/g15lcd/)

---

### Post by drdnl on 2006-08-07
could someone please post a howto from scratch/nothing to g15lcd + amarok script installed?

Doesnt have to be extremely detailed, I just need some help with getting the driver/script running and the g15 keys. I'd greatly appreciate any help.

Or, if possible maybe a .deb?

---

### Post by sirlancelot on 2006-08-09
I have the screen working using [g15lcd]("http://www.waug.at/g15lcd/") but I have to run it with --nokeys because apparently my kernel doesn't have uinput.

Can someone point me in the right direction as to how to setup/install/activate uinput on Kubuntu-dapper-i386 most recent?

---

### Post by maximouse on 2006-08-10
"modprobe uinput" works for me.

BTW: Does anybody know how to get write access to the usb ports without invoking root every startup?

---

### Post by SiliconViper on 2006-08-10
In an effort to support my fellow Ubuntu geeks with G15 keyboards, I have done what I can to aid in this process. Precompiled binaries (in both .tar.bz2 and .deb formats) are available on my site, and I have included initscripts to make it even simpler.

Download the package from here

[http://chris.olstrom.com/software/misc/g15lcd/](http://chris.olstrom.com/software/misc/g15lcd/)

```

$ sudo dpkg -i g15lcd-VERSION.deb
$ sudo /etc/init.d/g15lcd start

```

Now you can pipe things to /var/run/g15lcd and they will (if formatted correctly) be displayed on that little screen. However, in a further attempt to simplify this process, I created a little utility I call 'g15display' (.tar.bz2 and .deb also available).

Download the package from here

[http://chris.olstrom.com/software/perl/g15display/](http://chris.olstrom.com/software/perl/g15display/)

```

$ sudo dpkg -i g15display-VERSION.deb
$ g15display

```


This should print some text to the LCD, showing that it is working.

Now, this prints to it once. I dump my rhythmbox data to it, so I want it to update more often... that's what /usr/bin/g15display.loop is for. You'll need to edit it a bit, as it is broken currently (mis-entered pathname).

**EDIT: No editing required anymore. This has been corrected.**

```

$ g15display.loop

```

Will run g15display every few seconds, updating the display. I display uptime, load, and rhythmbox data here, so this makes sense. Sometimes, it doesn't. Feel free to add whatever functionality you want to the configs, and send me your config files, I'll put together an archive of them for everyone.

Enjoy.

---

### Post by SiliconViper on 2006-08-10
So yeah... that bug? Fixed. No more need to edit the file. That's corrected now.

---

### Post by Zarneth on 2006-08-17
Seem to be having trouble getting it to start
```
zar@zar:~/new/g15lcd-1.2-pre0$ sudo /etc/init.d/g15lcd start
Starting g15lcd...
mknod: `/var/run/g15lcd': File exists

```

Anyone have any ideas what to kick first?

---

### Post by SiliconViper on 2006-08-17
Yeah, to fix that... just do:

```
sudo rm -vf /var/run/g15lcd
```

As for using it properly, I just tested that out on another system... turns out I forgot to add something in the preinst script. You can correct this by issuing the following commands:

```
sudo addgroup g15lcd
sudo adduser your-username-here g15lcd
```

This is because /var/run/g15lcd is owned by gid 'g15lcd', which may not actually exist on your system, and even if it did, you aren't in it, unless you add yourself. I'll try fixing this in one of the installation scripts, but for now... the commands above will suffice.

---

### Post by Zarneth on 2006-08-17
Figured out the group part allready but that's fixed the not starting issue. 

Still nothing though for g15display. on the other hand I get an error in dmesg. each time it tries to update the LCD.
> [17181093.020000] usb 2-4.1.3.4: usbfs: usb_submit_urb returned -28


---

### Post by theToolman on 2006-08-18
> **maximouse said:**
> "modprobe uinput" works for me.

BTW: Does anybody know how to get write access to the usb ports without invoking root every startup?

yes; if you prefer to DIY then you can make a module load on boot by appending a line (an a comment if u like) to /etc/modules, namely:
```

#uinput for G15
uinput

```
the app compiles and works fine as described on the home page once uinput is loaded (at least on dapper, possibly earlier).  instead of rebooting, run ```
sudo modprobe uinput
```

---

### Post by sirlancelot on 2006-08-20
Thanks a lot theToolman! Those worked for me =D>

---

### Post by drdnl on 2006-08-23
Thank you SiliconViper for your help with the debs, I finally have my g15 display running and with it the final piece of hardware running perfectly under Linux. With some tinkering I got it to autorun at boot and it has been running/booting perfectly now for the last 2/3 days. Now on to the next step, to attain or even surpass the plugins made for windows. At the moment I have this "code" running:

```
g15display, by Chris Olstrom
-----------------------------------------
`uptime | sed -e s/load\ average// | sed -e s/\,//g`
`grep "model name" /proc/cpuinfo | sed -e s/model\ name//`
-----------------------------------------
`dcop amarok player artist` - `dcop amarok player album`
`dcop amarok player track` - `dcop amarok player title`
```

This is a modified piece of code that I found in the SAMPLE file that came with g15display, i call it "code" because my additions are only of the most basic nature and it is only capable of dumping the 
raw track info to the lcd with no formatting whatsoever.

Obviously I'm not a programmer, when i first got it up and running I tested its capabilities by typing into /etc/g15display the first command I could think of: `reboot`... Luckily nothing important was running at the time :)

What I'm hoping someone could write as an easy to execute program that hooks into SiliconViper's configuration is an Amarok version of this [plugin]("http://www.g15forums.com/forum/showthread.php?t=1157")

Not necessarily the entire thing with the playlist selecting and individual volume control but just the first page with the song info plus duration and an equalizer to once again show off to friends. It's been about 3 months now since my switch to Linux and I miss that great equalizer.

In the meantime, my thanks to everyone working on getting the g15 to play nice with linux.

---

### Post by phroztbyt3 on 2006-08-24
i cannot get it to work.. i did all the steps correctly... but it doesnt show up on my lcd at all.. anything... and i know that I input everything correctly.. am i missing something?

---

### Post by Immorten on 2006-09-03
> **SiliconViper said:**
> 
Now you can pipe things to /var/run/g15lcd and they will (if formatted correctly) be displayed on that little screen.
Enjoy.

I'm kind of new to Ubuntu, or Linux in general.
What do you mean by "Pipe things to /var/run/g15lcd"?

Thanks in advance

---

### Post by SiliconViper on 2006-09-03
> **Immorten said:**
> I'm kind of new to Ubuntu, or Linux in general.
What do you mean by "Pipe things to /var/run/g15lcd"?

Thanks in advance

I mean you can dump text into /var/run/g15lcd, which is a named pipe.

---

### Post by SiliconViper on 2006-09-03
> **drdnl said:**
> Thank you SiliconViper for your help with the debs, I finally have my g15 display running and with it the final piece of hardware running perfectly under Linux. With some tinkering I got it to autorun at boot and it has been running/booting perfectly now for the last 2/3 days. Now on to the next step, to attain or even surpass the plugins made for windows. At the moment I have this "code" running:

```
g15display, by Chris Olstrom
-----------------------------------------
`uptime | sed -e s/load\ average// | sed -e s/\,//g`
`grep "model name" /proc/cpuinfo | sed -e s/model\ name//`
-----------------------------------------
`dcop amarok player artist` - `dcop amarok player album`
`dcop amarok player track` - `dcop amarok player title`
```

This is a modified piece of code that I found in the SAMPLE file that came with g15display, i call it "code" because my additions are only of the most basic nature and it is only capable of dumping the 
raw track info to the lcd with no formatting whatsoever.

Obviously I'm not a programmer, when i first got it up and running I tested its capabilities by typing into /etc/g15display the first command I could think of: `reboot`... Luckily nothing important was running at the time :)

What I'm hoping someone could write as an easy to execute program that hooks into SiliconViper's configuration is an Amarok version of this [plugin]("http://www.g15forums.com/forum/showthread.php?t=1157")

Not necessarily the entire thing with the playlist selecting and individual volume control but just the first page with the song info plus duration and an equalizer to once again show off to friends. It's been about 3 months now since my switch to Linux and I miss that great equalizer.

In the meantime, my thanks to everyone working on getting the g15 to play nice with linux.

I have a simple subroutine for my now_playing script, that supports amaroK, if you want it. It'd be trivial to modify for use with g15display.

As for doing what that plugin does, in my (limited) experience with amaroK and Winamp, the latter has a more robust plugin architecture, and makes it easy to hook into all sorts of interal goodies, while the former does not.

I could be wrong, though.

---

### Post by drdnl on 2006-09-03
Sure, I'd be more than happy to try out your now_playing script, feel free to post it and I'll let you know what I think.

As for the possibility of more advanced scripts, I have no idea about programming. It is quite possible that that winamp plugin is simply too hard to execute on linux. At least without some hard work.

Either way, thank you in advance for the now_playing script,

-D

---

### Post by SiliconViper on 2006-09-03
I stand corrected, I have support for JuK, not amaroK.

**now_playing.pm**

Invoke with NowPlaying('','juk','');

```


#### Now_Playing Script, by Chris Olstrom
## Released under the GPL v2. Have fun.

sub NowPlaying {
	my ($null,$player,$args) = @_;
	my $display;

	# JuK support added 2005-09-10 00:06
	if ( $player eq 'juk' ) {
		my @trackProperties = `dcop juk Player trackProperties`;
		my %trackInfo;
		
		for ( my $iCounter = 0; $iCounter < @trackProperties; $iCounter++ ) {
			chomp($trackProperties[$iCounter]);
			$trackInfo{$trackProperties[$iCounter]} = `dcop juk Player trackProperty $trackProperties[$iCounter]`;
			chomp($trackInfo{$trackProperties[$iCounter]});
		}
		$trackInfo{'NowPlaying'} = "$trackInfo{'Artist'} - $trackInfo{'Album'} - $trackInfo{'Title'}";
		$display = $trackInfo{'NowPlaying'};
	}
	
	# mocp support added 2006-05-25 02:29
	if ( $player eq 'mocp' ) {
		my @raw = `mocp --info`;
		my @data;
		for ( my $iCounter = 0; $iCounter < @raw; $iCounter++ ) {
			chomp($raw[$iCounter]);
			my @field = split(/: /,$raw[$iCounter]);
			$data[$iCounter] = $field[1];
		}
		my $state       = $data[0];
		my $file        = $data[1];
		my $title       = $data[2];
		my $artist      = $data[3];
		my $songtitle   = $data[4];
		my $album       = $data[5];
		my $totaltime   = $data[6];
		my $currenttime = $data[7];
		my $timeleft    = $data[8];
		my $totalsec    = $data[9];
		my $currentsec  = $data[10];
		my $bitrate     = $data[11];
		my $rate        = $data[12];
	
		$display     = "$artist - $songtitle";
		
	}
	
	# mpd support added 2005-12-09 13:11, requires mpc
	if ( $player eq 'mpd' ) {
		$display = `mpc status | head -n 1`;
		chomp($display);
	}
	
	# rhythmbox support added 2006-03-22 01:40 in Python, wrapped in Perl as of 2006-04-01 01:06
	if ( $player eq 'rhythmbox' ) {
		$display = `python /home/siliconviper/bin/lib/rhythmbox.py`;
		chomp ($display);
	}
	
	# xmms support added 2005-06-06 13:27, requires xmms-info plugin
	if ( $player eq 'xmms' ) {
		$display = `cat /tmp/xmms-info | grep Title | head -n 1 | sed -e 's/Title: //'`;
		chomp($display);
	}

	if ( $args =~ m/--strip/ ) {
		print "$player\_playing[ " . $display . " ]";
	}

	## RAW output added 2006-07-19 23:31, to fit on my the LCD of my Logitech G15.
	if ( $args =~ m/--raw/ ) {
		print "$display";
	}

	if ( !$args ) {
		print "\x02\x0310$player\_playing\x0F[ " . $display . " ]";
	}
}

return 1;

```

**rhythmbox.py**
```

#!/usr/bin/env python

import bonobo

bonobo.activate()
try:
        songInfo = bonobo.get_object('OAFIID:GNOME_Rhythmbox','GNOME/Rhythmbox').getPlayerProperties().getValue('song').value()
        print songInfo.artist + ' - ' + songInfo.title
except:
        print 'Failed.'

```

---

### Post by oolunchbox on 2006-09-05
I've got the LCD working (great app SiliconViper!) but I cannot figure out how to get it to load at startup. Can anyone help? Also, is there any way to change the font size? I've got zero experience programming but I'm really excited to finally have this working.

---

### Post by Elpram on 2006-09-14
Hey, I'm trying to install this script of yours, however I run into the following error:
sh: /var/run/g15lcd: Permission denied
I have made sure to add a group g15lcd, and add myself to it, but it doesn't seem to work.

Any suggestions?

---

### Post by T-Chip on 2006-09-15
oolunchbox:
The "syntax" for sending things into the pipe, if you will, as I use it (and the README uses it, heh) is:
```
echo "T? \"Write some text here\"" > PATH_TO_PIPE
```
Where '?' is replaced by one of three letters, S, M or L (Small, Medium and Large, respectively), and PATH_TO_PIPE with ... the path to the pipe. In the case of SiliconViper's script, this would be /var/run/g15lcd. So, to reiterate the oldest of programs, you should be able to run the following, after starting the script:
```
echo "TL \"Hello world!\"" > /var/run/g15lcd
```
EDIT: I'm sorry, I think I misunderstood your problem. If you want to edit the size of text that g15display outputs, change the "TS" at the very bottom line to either "TM" or "TL" (as I described above).

Elpram: check whether the script actually sets the correct permissions. It should set g+w (group write permissions) on that file specifically. Check it by running ls -l on the directory, maybe using grep g15lcd to narrow down the output. I can't see how such a small glitch would find its way into the script, but who knows? If nothing else, you can at least check whether the rest of the program works by trying to send something through it via sudo or the like.

On another note, SiliconViper, the binary you offered in your .deb didn't do much for me (Linux kept complaining about not finding certain shared libraries - I suspect architecture differences, but I have no idea). However, using the rest of the package, compiling my own binary, and installing it over the one you provided, your package works fully. Thanks for easing the job of setting this up :-)

---

### Post by SiliconViper on 2006-09-16
You are certainly welcome. Anything I can do to give back to the community that has given so much to me, I gladly do.

---

### Post by Aneurysm9 on 2006-09-26
The g15lcd utility that is referenced here is no longer being developed.  It has been replaced by a suite of libraries and programs that should make it easier for programmers to develop new utilities for the G15.  The relevant tools can be found at [http://g15tools.sf.net](http://g15tools.sf.net)

---

### Post by drdnl on 2006-09-28
I've made a howto: explaining the installation of the G15Tools plus some debs here [http://www.ubuntuforums.org/showthread.php?t=267118]("http://www.ubuntuforums.org/showthread.php?t=267118")

---

### Post by brussel on 2006-11-16
I'm using the latest Ubuntu release, 6.10, and get the following error on the first step:

> 
sudo dpkg -i g15lcd-VERSION.deb
dpkg: error processing g15lcd-VERSION.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 g15lcd-VERSION.deb



Have any idea what this may be about?

---

### Post by brussel on 2006-11-16
I'm using the latest Ubuntu release, 6.10, and get the following error on the first step:

> 
sudo dpkg -i g15lcd-VERSION.deb
dpkg: error processing g15lcd-VERSION.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 g15lcd-VERSION.deb



Have any idea what this may be about?

---

### Post by SiliconViper on 2006-11-18
You need to download the .deb package first, and then install it with dpkg. The version number needs to be substituted for -VERSION, so if it was version 9.2, the command would be...```
sudo dpkg -i g15lcd-9.2.deb
```. The examples all list -VERSION, so as to be release-agnostic. The instructions should be as valid for later releases as for older ones.

Hopefully this helps.

---

### Post by Sturmeh on 2008-05-06
You know what would be cool?

Display represntations of the four workspaces on the LCD, and the four lcd aux keys can automatically switch between them.

That could be very interesting in combination with Compiz effects. :D

EDIT: I don't care if i bumped a two year old thread, the G15 refresh came out this year lol.

---

### Post by SiliconViper on 2008-05-06
> **Sturmeh said:**
> You know what would be cool?

Display represntations of the four workspaces on the LCD, and the four lcd aux keys can automatically switch between them.

That could be very interesting in combination with Compiz effects. :D


That would be awesome to see. The LCD doesn't support enough detail to accomplish proper thumbnailing, But a basic box indicating each workspace should be possible. Maybe shade the active one, and display a line of text at the bottom of the LCD with the Workspace Title, if there is one defined?

Would you be interested in writing something like this?

> **Sturmeh said:**
> 
EDIT: I don't care if i bumped a two year old thread, the G15 refresh came out this year lol.

Necromancy is an essential part of the internet. Especially forums.

---

### Post by maxxwizard on 2008-05-26
i couldn't get your driver to work SiliconViper.

i installed the g15daemon (and other components) from Synaptic and the clock appeared. i used amarok and its g15 script, but the program and the script is utter crap.

i'm new to linux, but i'd like to learn how to create a script that will utilize the g15daemon to output my rhymthbox info (artist, song title, and a simple progress bar).

---

### Post by signseeker on 2008-05-26
Thanks guys. I will try some of this out when I get home.

---

### Post by SiliconViper on 2008-05-26
> **maxxwizard said:**
> i couldn't get your driver to work SiliconViper.

i installed the g15daemon (and other components) from Synaptic and the clock appeared. i used amarok and its g15 script, but the program and the script is utter crap.

i'm new to linux, but i'd like to learn how to create a script that will utilize the g15daemon to output my rhymthbox info (artist, song title, and a simple progress bar).


It seems like there is a bit of confusion regarding which code is being referenced by which thread. This thread is not related to g15daemon, sorry!

The scripts I have written to output to the lcd utilize g15lcd, not g15daemon. If you have any questions regarding my code though, please ask.

---

### Post by maxxwizard on 2008-05-26
> **SiliconViper said:**
> It seems like there is a bit of confusion regarding which code is being referenced by which thread. This thread is not related to g15daemon, sorry!

The scripts I have written to output to the lcd utilize g15lcd, not g15daemon. If you have any questions regarding my code though, please ask.

i couldn't get your script to work. i started g15lcd (so the pipe is created), but trying to start g15display (script that would bring send info to the pipe) would give cause terminal to hang. i can still type in the terminal though. it's like the script is stuck in a loop or something.

---

### Post by SiliconViper on 2008-05-26
> **maxxwizard said:**
> i couldn't get your script to work. i started g15lcd (so the pipe is created), but trying to start g15display (script that would bring send info to the pipe) would give cause terminal to hang. i can still type in the terminal though. it's like the script is stuck in a loop or something.

Are you using the g15lcd script, or g15lcd.loop? Can you paste or screenshot the terminal window, starting before your launch it, until the problem occurs?

---

