---
title: "ThinkPad Battery Status Gnome Applet"
date: 2011-02-10
forum: Hardware
---

### Post by wolke on 2011-02-10
here is a gnome applet for tp_smapi. it has a text/graphical display, and does battery balancing for improving battery life.

[https://github.com/teleshoes/tpbattstat-applet](https://github.com/teleshoes/tpbattstat-applet)

I have a t400 with an ultrabay battery and a 9c main, and ubuntu 10.10 x86-64. If other folks could try it out and tell me if it works for them, id appreciate it.

it has several configurable charge and discharge strategies, and several configs for display in gconf. {no ui for changing them yet, tho, use gconf-editor}

[IMG]https://github.com/teleshoes/tpbattstat-applet/raw/master/examples/example_display.png[/IMG]

[IMG]https://github.com/teleshoes/tpbattstat-applet/raw/master/examples/example_display2.png[/IMG]

[IMG]https://github.com/teleshoes/tpbattstat-applet/raw/master/examples/example_display3.png[/IMG]

[IMG]https://github.com/teleshoes/tpbattstat-applet/raw/master/examples/example_gconf.png[/IMG]

its in alpha. here is a script that should install it.
```

#!/bin/bash
sudo apt-get install git build-essential libpanel-applet2-dev
cd /tmp
git clone git://github.com/teleshoes/tpbattstat-applet.git
cd tpbattstat-applet
./configure --prefix=/usr
sudo make install
gconftool-2 --install-schema-file tpbattstat-applet.schemas 
sudo rm -rf /tmp/tpbattstat-applet
gnome-panel --replace &
sudo /etc/init.d/apparmor reload

```

---

### Post by moptop on 2011-02-14
Hi,

I'm interested in this -- my battery issues are a real pain! -- but I'm having a little trouble making it work properly.  It shows up in the panel as indicated, and I can't change any of the gconf values (see the second attachment.  Thanks!
Matt

---

### Post by wolke on 2011-02-15
hi! those are the schemas, which are just gconf default values. the actual gconf preference keys for a gnome panel applet {such as Clock Applet or this applet} are under
```
/apps/panel/applets/**ID**/prefs
```
where **ID** is usually something like 'applet0'.

{you will probably have several IDs in there. tpbattstat is probably the highest one, but note that gnome-panel doesnt clean them up well. if you add an applet and remove it, the entry usually lingers; this is part of how gnome-panel manages its gconf keys, and is pretty annoying.}

each instance of an applet has its own preferences. for instance, you can add the clock twice, and make one display seconds and the other not. likewise, you can add TPBattStatApplet twice or more, but it will probably result in weird behaviour.

---

### Post by wolke on 2011-02-15
as for the other bit, you probably dont have tp_smapi installed. i bizarrely forgot to put this in the README, which i am fixing now.

tp_smapi provides devices under /sys/devices/platform/smapi that tpbattstat uses to read/write battery status.

the following perl script is how i install it, but there are a number of ways. check out think wiki for details on how to install for specific ubuntu releases.

[http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)

```
#!/usr/bin/perl
use strict;
use warnings;

system "apt-get install tp-smapi-source";
system "module-assistant prepare tp-smapi";
system "module-assistant auto-install tp-smapi";
system "modprobe tp-smapi";

open FH, '< /etc/modules';
my @lines = <FH>;
my @newlines;
for my $line(@lines){
  push @newlines, $line if $line !~ /^(tp-smapi|hdaps)\n?$/;
}
push @newlines, "tp-smapi\n";
push @newlines, "hdaps\n";
close FH;

open FH, '> /etc/modules';
print FH @newlines;
close FH;

system "chmod o+w /etc/modules";
system
  "echo 'KERNEL==\"event[0-9]*\", " .
  "ATTRS{phys}==\"hdaps/input1\"," .
  "ATTRS{modalias}==\"input:b0019v1014p5054e4801-*\",".
  "SYMLINK+=\"input/hdaps/accelerometer-event\"'".
  " | sudo tee /etc/udev/rules.d/51-hdaps.rules";
system "update-initramfs -u";

system
  "echo 'options thinkpad_ec force_io=1' > " .
  "/etc/modprobe.d/tp_smapi.conf";
system "modprobe -a tp_smapi hdaps";

```

---

### Post by wolke on 2011-02-15
short questionnaire for anyone that feels like answering it: 

1) what model thinkpad are you using? what distro? what version of gnome, if you installed a non-default one {e.g.: gnome shell 3.0}

2) do you have an ultrabay battery you want to balance? what kind of main battery do you have (6c, 9c, etc)?

3) do you want to show the percentage and/or power rate on the screen?

4) was this easy to install? did you try and give up because it was a pain? somewhere in the middle?

5) is the applet helpful? is the display really ugly? any horrible bugs?

feel free to answer whatever bits you like, and please leave any suggestions for features or display

---

### Post by johnwayner on 2011-03-25
1. T61p; Ubuntu 10.10; default Gnome

2. Ultrabay & 9c main., actually I'd like to be able to override the balancing by clicking on one of the battery icons to force that battery to drain/charge.  

3. percentages and time remaining

4. pretty easy. Although I missed the tp_smapi install requirement b/c it is on a new line in the README (or at least on the git page).  It was fairly obvious what the problem was at that point though.

5. I've only just started using it.  The display is fine.  I can't seem to get the configuration changes made in gconf to apply.  I'm probably doing something silly.

Thanks for writing this thing!  I was not looking forward to echoing out to files all the time :)

-Wayne

---

### Post by wolke on 2011-03-28
cool, thanks for the info. glad it worked for ya; hope it continues to!

ooh, #2 is a good feature, and easily implemented when i get some time.
the only downside to it is that its only useful if you use the two-batteries display which takes up a lot of room compared to the condensed 1-batt pic.

---

### Post by johnwayner on 2011-03-29
Heh... I've got a fairly high res screen so I use the two battery display.

You can put the overrides in the menu as well for those that use the condensed display.

---

### Post by johnwayner on 2011-03-29
I'm seeing the applet crash frequently when unlocking the screen or coming back from a suspend.

Is there a location I can look at for logging so I can help figure out what the problem is?

-Wayne

---

### Post by wolke on 2011-03-30
oh no, thats terrible. suspend doesnt work at all for me these days, so i never tested. im going to see if i can either get suspend to work or find a different tp to use for testing.

no, there is no log. the applet doesnt do any device i/o or anything. smapi-battaccess is the process that actually talks to smapi, and thats run afresh each gui update.

---

### Post by johnwayner on 2011-03-30
It seems to die when the screen is locked for longer periods of time (many hours).  So it may not be related to suspending at all.  

If it annoys me enough (and I have time), I'll throw some good ol' printf debugging statements in there and see where it's dying.

---

### Post by wolke on 2011-03-31
heh, just so you know, while looking for this bug, spotted a different one.
if both batteries are at 0%, the applet dies and pops up an annoying thing. it wont restart until one battery is at 1%.

turns out this is a useful 'feature'; saved my work just now.

---

### Post by johnwayner on 2011-04-01
Well, I was just sitting here working on the charger and the applet crashed.  I suspect it crashed once both batteries were at 100%.  This could explain why it had always crashed when I came back to my computer after letting it sit on the charger for a while.  It probably has nothing to do with suspending or screen locking/unlocking.  It's just that the batteries both charged while I was gone.

---

### Post by wolke on 2011-04-02
mine charges both to 100% all the time, though. {i notice it particularly because it says its not charging anymore.} the only time it ever crashes for me is right before the computer dies when both batts get to 0%.

if it IS when both get to 100%, i know just what it is thats dying.

areas that come to mind:
1) gconf key reading {gconf specs say to expect failures for all reads, but its hard to test what happens when it fails because it never does fail}
2) smapi-battaccess invokations {if it fails to open a pipe, it would null ptr}
3) something to do with painting both batteries {since it crashes for you and not for me}
4) basically everywhere else because c is such a shitty language for guis {totally didnt know there were python libs for gnome-applets when i wrote this; theres a re-write in this projects future}

im crazy busy with real work right now, but i plan on maintaining this project forever because thinkpads are the only machines with nice mouse buttons and touchpads.

---

### Post by wolke on 2011-05-07
rewrote it in python and removed make.
1) it doesnt crash for me ever now
2) installing is much easier, includes the schemas, assumes prefix=/usr, and is quick
3) you can run it in a standalone window now like this: python tpbattstat.py run-in-window. it has separate gconf keys
4) writing in it isnt painful anymore, so maybe i can actually add a prefs gui and interesting context menus.

---

### Post by wolke on 2011-06-19
1) added an ubuntu installer
2) added a patch to tp_smapi for newer thinkpads, e.g.: w520/t520/w510/t510
3) added dzen2 output

---

### Post by thion262 on 2011-10-24
Hi, im trying to install this applet in Debian Mint 11 and running into problems.

The install script (install.sh) completes successfully, and i can add the applet to the gnome-panel.

However, it only displays a "<?>" sign.
Has anyone run into this problem before?

I don't have apparmor installed, could that be a problem?

I'd be grateful for any input.

---

### Post by wolke on 2011-10-24
hello!
--
do you have tpsmapi installed? this is what tpbattstat uses to talk to the embedded controller.
1) compile it from: [http://packages.qa.debian.org/t/tp-smapi.html](http://packages.qa.debian.org/t/tp-smapi.html)
    {apt-get install tp-smapi-source; m-a a-i tpsmapi}
   or the latest at : [https://github.com/evgeni/tp_smapi](https://github.com/evgeni/tp_smapi)
2) you can try my script, ubuntu-tp-smapi-install, which grabs the source package, and patches it to support newer thinkpads like t420/t520/w520. the source package in debian unstable is much newer than the one in ubuntu's universe, so you might not need my patch.
--
i recommend that you DO install apparmor, but you dont need it. {smapi-battaccess, my cli frontend to tpsmapi, runs as root with setuid. apparmor makes it so it can only read/write smapi files. this adds a layer of protection against bugs running as root, though that bit of code is well-tested, small, and hasnt been changed in a long time}
--
lemme know if that was it

---

### Post by Im mad on 2011-10-25
> **thion262 said:**
> Hi, im trying to install this applet in Debian Mint 11 and running into problems.

The install script (install.sh) completes successfully, and i can add the applet to the gnome-panel.

However, it only displays a "<?>" sign.
Has anyone run into this problem before?

I don't have apparmor installed, could that be a problem?

I'd be grateful for any input.

I ran into the same problem on Debian stable. Tp-smapi is installed and loaded, but it only displays a "<?>" and at statistics it says "stats arent here yet".

Thanks for you effort, Wolke!

---

### Post by wolke on 2011-10-25
1) please check if tpsmapi is working first. as an example:

teleshoes:~$ cat /sys/devices/platform/smapi/BAT0/last_full_capacity 
77370

2) what thinkpad do you {both} have? newer thinkpads like w520/t520/t420 etc work, but the patch to make it work isnt on debian stable yet. {the patch is a one-liner instructing tpsmapi to load all lenovo thinkpads, instead of just lenovo thinkpads that announce their embedded controllers properly.}

3) whoops, statistics. forgot i was gonna do that. i probably still will. :/

4) i assume youre also using this in gnome-panel. {it also works nicely in dzen2 and as a standalone window}. is this gnome2 or gnome3 pretending its gnome2?

5) try this to run it as a standalone gtk application:
/usr/lib/tpbattstat-applet/tpbattstat.py -w
{please also paste its output so i can see if its crashing, and where}

---

### Post by Im mad on 2011-10-25
> **wolke said:**
> 1) please check if tpsmapi is working first. as an example:

teleshoes:~$ cat /sys/devices/platform/smapi/BAT0/last_full_capacity 
77370

2) what thinkpad do you {both} have? newer thinkpads like w520/t520/t420 etc work, but the patch to make it work isnt on debian stable yet. {the patch is a one-liner instructing tpsmapi to load all lenovo thinkpads, instead of just lenovo thinkpads that announce their embedded controllers properly.}

3) whoops, statistics. forgot i was gonna do that. i probably still will. :/

4) i assume youre also using this in gnome-panel. {it also works nicely in dzen2 and as a standalone window}. is this gnome2 or gnome3 pretending its gnome2?

5) try this to run it as a standalone gtk application:
/usr/lib/tpbattstat-applet/tpbattstat.py -w
{please also paste its output so i can see if its crashing, and where}
1) 89210, so it seems working (9 cell battery)

2) It's a T61p

3) I thought it might give a clou about something that might be missing to help the debug process. Sounds like a nice feature though!

4) I'm normally using cairo-dock, but for the time being I'm using gnome-panel (gnome2, debian stable isn't that up-to-date ;))

5) when executing I receive this error:
"using led pattern: ['']
Traceback (most recent call last):
  File "/usr/lib/tpbattstat-applet/tpbattstat.py", line 144, in <module>
    sys.exit(main())
  File "/usr/lib/tpbattstat-applet/tpbattstat.py", line 115, in main
    TPBattStatAppletFactory(applet, None)
  File "/usr/lib/tpbattstat-applet/tpbattstat.py", line 91, in TPBattStatAppletFactory
    TPBattStatApplet(applet).startUpdate()
  File "/usr/lib/tpbattstat-applet/tpbattstat.py", line 63, in startUpdate
    self.update()
  File "/usr/lib/tpbattstat-applet/tpbattstat.py", line 70, in update
    self.actions.performActions()
  File "/usr/lib/tpbattstat-applet/actions.py", line 35, in performActions
    self.updateLed()
  File "/usr/lib/tpbattstat-applet/actions.py", line 42, in updateLed
    Popen([LED_BATT_EXEC] + self.ledPattern, stdout=self.nullFile)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory"

Python-gnome2 and python-gnomeapplet are both installed.


Edit: when running as root (gksu /usr/lib/tpbattstat-applet/tpbattstat.py -w), I got the following error:
"(tpbattstat.py:5327): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported."

---

### Post by wolke on 2011-10-25
whoops. i added support for it to control my battery LED, because the W520 doesnt have an AC adapter LED. {no indication of when its charging, so i made it blink while discharging and be steady when charging}

the LED controls are fairly robust {mine blinks more rapidly as the battery gets lower, and alternates green and orange when the batteries are full}. 

however, LED support requires you to have two scripts in /usr/local/bin that i simply havent committed yet. i need to check at startup whether you have them, and simply ignore them if you dont.

im fixing it so it wont break right now. {also, ill commit the LED scripts as an optional install later. theyre just perl scripts, and they depend upon thinkpad_acpi}

---

### Post by wolke on 2011-10-25
please git pull && ./install.sh
restart gnome-panel and it should work.

---

### Post by Im mad on 2011-10-25
It works! Thanks a lot for the fast responses and especially the fix!

Edit:

> **moptop said:**
> Hi,

I'm interested in this -- my battery issues are a real pain! -- but I'm having a little trouble making it work properly.  It shows up in the panel as indicated, and I can't change any of the gconf values (see the second attachment.  Thanks!
Matt

I have a bit of the same problem. I see applet_0 under /apps/panel/applets/. The name is OAFIID:TPBattStatApplet, so it should be the applet, but I don't have a prefs map. Some other applets do, however. Explicit reinstalling of the schemas didn't work.

---

### Post by wolke on 2011-10-25
heres a few ideas that may help you solve it. lemme know

despite appearances, perhaps applet0 isnt the right one. gnome-panel doesnt clear out old ones in any predictable fashion. right-click and go to preferences-editing and see what the applet id is there {it says at the bottom of the dialog, e.g.: "gconf keys: /apps/panel/applets/applet14/prefs"}.

if it says applet0, the problem might be because it died in a weird way before. try adding a second one to the panel, check its prefs, and then remove the first one if it worked.


if that doesnt fix it, please run it in its own window again with 'tpbattstat.py -w' and see if you can edit the preferences then. {the edit-preferences dialog should show /apps/tpbattstat-applet/prefs/ instead of /apps/panel/applets/applet#/prefs}


you might want to confirm that my schema-installer actually worked. the schemas should be at '/schemas/apps/tpbattstat_applet/prefs'


if all else fails, remove it from the panel and start over. i.e.:
  {remove tpbattstat-applet instance}
gnome-panel --replace &
killall gnome-panel
killall python
./tpbattstat-applet/install.sh
gnome-panel &
  {add tpbattstat-applet instance}

---

### Post by wolke on 2011-10-26
i put up the LED controlling scripts. it requires thinkpad_acpi kernel module to be loaded, or it does nothing.

also, the tpacpi may or may not expose your battery led, or may name them differently.
{mine are tpacpi:green:bat and tpacpi:orange:bat, in /sys/devices/platform/thinkpad_acpi/leds}

---

### Post by Im mad on 2011-10-27
It works, preferences can be changed via the applet menu. I thought that was impossible, so I directly tried to change it via gconf-editor, which I still haven't figured out.

Thanks a lot, this program really comes in handy with two batteries!

---

### Post by wolke on 2011-10-27
np, glad you found it useful

---

### Post by Im mad on 2012-05-18
Any change this will be ported to gnome 3?

---

### Post by wolke on 2012-05-18
> **Im mad said:**
> Any change this will be ported to gnome 3?

im afraid ive never used gnome3, and i dont care to. sorry!

you might want to checkout mate, which i hear has gnome-panel applet support. if you have trouble with tpbattstat on mate, ill do my best to support you.

you can still use the program as a standalone gtk+ app {that still works, right? run "/usr/lib/tpbattstat-applet/tpbattstat.py -w"}. you could set it up to hover over your panel in a fixed spot when you start the computer {somehow or other, maybe i should add a -x and -y argument}.

you can also use it in dzen, which is how i use it these days.

---

