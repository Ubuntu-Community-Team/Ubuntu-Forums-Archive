---
title: "Griffin Powermate (package for volume control and shutdown)"
date: 2009-12-05
forum: Hardware
---

### Post by StonedOne on 2009-12-05
Hello everyone, this Thread is about "Griffin Powermate" (_[http://store.griffintechnology.com/desktop/powermate](http://store.griffintechnology.com/desktop/powermate)_).

I created a package for Ubuntu (currently Ubuntu 11.10, see last page of this thread)

Following features are currently supported:
*Volume control (lower and raise with turning)
*Shutdown timer (push for 5 minute timer, push again to cancel timer)
*Enable device for every user
*Enable device on boot
*Enable device on replug
*Shutdown-Sound when timer is activated
*Untiy-Desktop is supported

Not supported (but hopefully soon):
*dim the blue light
*skipping files in default ubuntu player (this needs a menu for control)

The package is mostly bash scripts, so it's not hard to understand. To make this package better for everyone i need feedback.
So just try it and reply to this thread...

Greetings Stoned

---

### Post by spank_me on 2009-12-30
Hi,

Do you have source for this driver ? If so, could you please email it to me ? 

I am trying to get my Powermate to work on Ubuntu 9.04 on a ARM based Freescale processor.

Thanks.

---

### Post by StonedOne on 2009-12-30
Hey there,

the attachment contains an .deb-package and the source file i changed.

After installation the powermate should work. After reboot you have to replug the powermate (udev recognizes it) i did not insert an autostart script.

For automatic start use a startup script for gnome and just execute "/etc/maryjoana/scripts/start-evrouter.sh" on login.

You can find configuration files under "/etc/maryjoana".

Feedback is appriciated!

---

### Post by StonedOne on 2009-12-30
Oh my bad, just saw you are on an the old 9.04 version.

Here is the old package i used before but no updates from me for this one ;)
Maybe you can try your hardware on the new version while your at it ...

Waiting for the new LTS 10.04 to get a stable basement for further enhancments

Greetings Stoned

---

### Post by chacal23 on 2010-01-07
;) hello
i seek for the 64bit **ubuntu 9.10 Karmic Koala **
THX;)

---

### Post by StonedOne on 2010-01-13
Right now i don't have access to the Internet at home, but i will create a package as soon it works again. Stay tuned...

Can anyone give me feedback if it works as aspected?

I will then create a init script to start powermate automaticly on reboot.

---

### Post by choyak on 2010-06-06
I just installed this, and the volume control works, however the blue LED will not dim when decreasing the volume, and the mute will not function by pressing the knob.  Is there a configuration for this?  You also need to replug after booting, but the volume control functions correctly.

---

### Post by StonedOne on 2010-06-06
Hey thanks for the feedback...

You are right the dim does not work right now, i will work on this next winter. Right now im creating a menu for using different Keys while turning the powermate.

The mute function is not active by default in this package. Default is poweroff hardware after 5 minutes. Change this value in "/etc/maryjoana/conf/evrouterrc", you can use any XKey or write own scripts.

The replug is also correct, dont know how to solve this on a per user basis. Im working on this...

This software also works under Ubuntu 10.04 but the beep wont work anymore while pressing the powermate. This is the same issue like the activation on boot, i have to figure out how to do stuff on user basis (which user is logged in).

If anyone has better solutions inside the scripts please post them here. I will insert the code and create a new package.

---

### Post by ChrisBryant on 2010-11-03
Hi Stoned, thanks for putting this up and sharing it. I used to have my powermate working in Gentoo with evdev but haven't set it up again in ubuntu. Do you have any updates on this or should I test with your old package posted here?

Also, could you create a PPA for it and/or submit it for inclusion into Ubuntu repositories? :-) 

Thanks again!!

---

### Post by StonedOne on 2010-11-03
Hey Chris,

there is a package i use at home right now for Ubuntu 10.04. It has one Issue it will not autodetect the device on boot. You will have to replug the powermate to activate it.

A good workaround for this problem is to create an startscript for your user under system->preferences and execute the script "/etc/maryjoana/scripts/start-evrouter.sh"

With Ubuntu 10.10 the "start-evrouter.sh"-script will not get started with a udev-rule (unplug and plugin again) there are some issues with user rights (you have to be root to use the script)

You can use and play with the scripts, if you have any improvements or suggestions just post them here. It is all just bashscripts and config files...

When it gets cold in germany i will work on this again ;)

Greetings

---

### Post by bryan8 on 2010-11-05
Fantastic.  I have tried many things that haven't worked.  Finally you have provided something that does!

Many Thanks,

---

### Post by StonedOne on 2010-12-09
Here we go!

This is a good one for Ubuntu 10.10. Works on boot and for every user on the system.
I was waiting for this so long ...

The new "Unity Desktop" which will be default with Ubuntu 11.04 gives a great opportunity for the powermate. Maybe the desktop can be fully controlled with the powermate device.

Let's see what future releases bring...

Greetings from Germany

Stoned

PS:
Feedback is very welcome!!!

---

### Post by shpedoikal on 2010-12-10
Thanks for this, StonedOne.  I downloaded, installed  maryjoana-powermate and got it working on 10.10.

One issue I ran into was that /usr/sbin/evrouter wasn't executable.  After manually 

chmod a+x /usr/bin/evrouter

all worked well.

One question though -- is there a way to change the sensitivity on the powermate?  I'd like to make it less sensitive, as it is I tend to blast volume to max by accidentally turning it the wrong way...

Thanks

---

### Post by StonedOne on 2010-12-11
Your right, on my tests i update the package and it worked because the old evrouter file was executable.

I will correct this and build a new package.

Right now i have problems with the timed poweroff command. All scripts are executed as expected but the command "poweroff" does not work when executed through powermate script.

Anyone else has this problem?

Stoned

---

### Post by StonedOne on 2010-12-11
@shpedoikal

The sensitivity could be less if you use a script to adjust the volume. Right now the volume is set directly through evrouter.

The config file "/etc/maryjoana/conf/evrouter" will give the change to set scripts behind powermate turns.

Then you can use something like amixer to set volume as you wish. If you have something reliable i can put it into the package.

Good luck...

---

### Post by shpedoikal on 2010-12-17
@StonedOne

Thanks, I did edit evrouterrc to make the button mute instead of launch the shutdown script, which is great.  For others, just change this:

> "Griffin PowerMate" "" any key/256 "Shell//etc/maryjoana/scripts/init-shutdown.sh"to this:

> "Griffin PowerMate" "" any key/256 "XKey/XF86AudioMute"

I've got a script with a simple amixer command to only increment the volume by 1%, which works when launched standalone, but this line:

> "Griffin PowerMate" "" any key/7/1 "Shell//etc/maryjoana/scripts/amixer_volume_up.sh"

doesn't seem to make evrouter launch it.  I've played with permissions a little with no luck.  Any luck debugging the issue with the shutdown script?  Maybe we're hitting the same issue here...

Shpedoikal

---

### Post by shpedoikal on 2010-12-17
Attaching the volume scripts.  They operate on the Master channel.

shpeodikal

---

### Post by shpedoikal on 2010-12-17
I fixed my issue here.  Using evrouter -d /dev/input/powermate, it suggested a slightly different format for my evrouterrc file.  Based on those suggestions I slightly changed the evrouterrc to look like this:

> Window ""
"Griffin PowerMate" "/dev/input/powermate" none key/256 "XKey/XF86AudioMute"
"Griffin PowerMate" "/dev/input/powermate" none rel/7/1 "SHELL//etc/maryjoana/scripts/amixer_volume_up.sh"
"Griffin PowerMate" "/dev/input/powermate" none rel/7/-1 "SHELL//etc/maryjoana/scripts/amixer_volume_down.sh"
Now it works just fine.  Thanks @StonedOne :-)

---

### Post by StonedOne on 2010-12-19
Hey it's great you can use the package as you want to, so it seams that it is not too complex ;)

I fixed my issues with the "shutdown-timer.sh" now it also works user specific. If it is ok i added your amixer scripts for everyone who wants to use it. But i still think the default is the best setup. Because you can mute with lowering the volume and the push button is free for the timer.

Anyways the file "/etc/maryjoana/conf/evrouterrc" now contains all possible configuration, just use the lines you want to.

Thanks for the feedback...

Stoned

---

### Post by Jirget on 2011-02-09
I just got my powermate today, and finding this readymade and up to date package really made my day.

I don't have anything more to contribute then a simple: Thank you!

---

### Post by gskjold on 2011-03-23
I have ubuntu 10.10 x64, and it seems to not work. 

Starting EvRouter.../etc/maryjoana/scripts/start-evrouter.sh: line 31: /usr/bin/evrouter: No such file or directory

Any suggestions?

---

### Post by StonedOne on 2011-03-24
Hey there,

im using the same Ubuntu Version (also 64bit) and it should work. Please check following points:

[LIST=1]
[*]Check if file exists ("ls -la /usr/bin/evrouter")
[LIST=1]
[*]if not i must take a look at the package
[/LIST]
[*]Check if file is executable (must have "x")
[LIST=1]
[*]type "/usr/bin/evrouter" (look for output)
[*]if you can not start the programm type ("chmod +x /usr/bin/evrouter")
[/LIST]
[/LIST]
If you still can not get it to work post all outputs of the commands here and i will see what i can do.
I think its the second point ... ;)

---

### Post by phroman on 2011-04-14
Brother, thank you so much for this package!

---

### Post by StonedOne on 2011-11-17
Hey there,

i created a new package for Ubuntu 11.10 (tested for 32bit should work also for 64bit)

Currently im using the new Unity Desktop and this package works like expected now.

There is als a shutdown sound again... just try it and leave your comments!

Greetings
StonedOne

---

### Post by StonedOne on 2011-11-18
The Shutdown-Command seems not working
and 64bit needs a 32bit library.

... looking into this!

I'll get back when i solved the problem.

---

### Post by frakthem on 2012-01-18
So I am running Ubuntu 11.10 64bit and was having issues installing this package as instructed.  I installed the hesus-powermate...deb package and couldn't get it to start.  All I got were those file not found errors.  SO I got it working by unpacking the evrouter package from [http://www.bedroomlan.org/projects/evrouter](http://www.bedroomlan.org/projects/evrouter) and over-writing the evrouter binary included w/ the hesus-powermate package.  

I had to change a few things in the conf file too, 
My display is :0 not :0.0 (not sure if this is new for 11 or not)
My /dev/input/powermate was actually /dev/input/event7
I changed those to reflect my system and it works!  

My only issue so far is I get a 

touch: missing file operand
Try 'touch --help' for more information.

When I push the button on the powermate.   Is that expected?  Can I make that mute/unmute or something?

---

### Post by StonedOne on 2012-01-18
You are right the 64bit version is not working because of dependencies. 

When i got some spare time and can fix this, i will post a new package here.

To your Problems:

1. If you use the Package from BedroomLAN you may get problems with unplugging/replugging it. Error handling is messed up there ... but it will work.

2. The device is only named powermate when you use the given udev-rules from the hesus-package.

3. The functions for the powermate device can be configured in evrouter.rc file. When pushing the button a script will be executed. This scripts wants to log into /var/log/hesus where it trys to touch the log file. This is not working because the script was not correctly install.

Normaly the push executes a timer for shutdown...

Sorry for the not working 64bit package, i will get to it some day.

---

### Post by frakthem on 2012-01-18
Thanks!  

I uncommented the line for audio mute instead of the shutdown script and everything works great now.

I am not concerned about the hotplug honestly this is my desktop at work which should never be turned off or heads will roll!

This is a good workaround for those of you using Ubuntu 11.10/64bit if you understand the limitations.

---

### Post by marvin1969 on 2012-01-23
Thanks for the work on the Powermate.  I have the basics working now on the 10.10 64-bit.  Would love to see this become a generally selectable package for Synaptic.

---

### Post by TallDaveOS on 2012-05-17
Hi @marvin1969
I tried the Hesus file above at #24, though it wouldn't work for me. How did you get your PowerMate to work, and do you perhaps have a working package or link to one ?
Cheers, Dave

Here's my Q that someone relpled to suggesting the forum.. [http://askubuntu.com/questions/138148/need-help-with-griffin-powermate-usb-volume-controller-new-64-bit-desktop-ub](http://askubuntu.com/questions/138148/need-help-with-griffin-powermate-usb-volume-controller-new-64-bit-desktop-ub)

---

### Post by shdawson on 2012-08-16
Hello,


Trying to get hesus-powermate_1.2-0_all.deb running on Linux Mint 13.  Not working, not installing.  Says it installs, but does not.

The terminal window, viewing while installing, produces no errors.  What are the requirements for installation, package and dependency wise, please?


Thank You,
SHD

---

### Post by shdawson on 2012-08-17
Maybe it is a simple error near line 11?

dpkg: error processing /media/1G_USB/hesus-powermate_1.2-0_all.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 11 package 'hesus-powermate':
 blank line in value of field 'Description'
Errors were encountered while processing:
 hesus-powermate_1.2-0_all.deb


Only a guess, I really don't know why this is not installing.


-SHD

---

### Post by shdawson on 2012-08-28
Worked with a friend, who's hacked it to get it to install in Mint on a 32bit machine.

The problem with the the current 'hesus-powermate_1.2-0_all.deb' package is the Description field, in ./control file.  It has some blank lines that the current Ubuntu/Mint dpkg version does not take kindly to and the install fails.  The solution was to modify this file and remove the empty lines.

We used the evrouter-0.4 binary from [http://www.bedroomlan.org/projects/evrouter](http://www.bedroomlan.org/projects/evrouter) and all seems to work as intended when powermate is hotplugged.

We changed the group in the udev rules from "admin" to "input", because my user was already a member of the input group.

Finally, we changed the /etc/hesus/conf/evrouterrc:

Window ""
"Griffin PowerMate" "" any rel/7/1 "XKey/Down"
"Griffin PowerMate" "" any rel/7/-1 "XKey/Up"

...to enable scrolling up & down in different windows, rather than adjusting the volume.

Please find attached the modified package - I hope it helps.
 
Thanks again for making this package.  I personally very much appreciate it.

---

### Post by auser2 on 2013-03-03
Hello,

I just downloaded the Zip from the last post and installed "PowerMate & Linx Mint.deb" - which worked without problem.

It is working on Unity, but my usual Desktop is Gnome (I use Ubuntu 12.04) - and there it is not working!

Is it also working on Gnome Classic (Backport)?

How can i track down the problem?

The EvRouter Daemon seems to work:
Starting PowerMate at Sun Mar  3 14:31:12 CET 2013...device exists
Starting EvRouter...tmp-file created......done
Starting PowerMate at Sun Mar  3 14:31:12 CET 2013...device exists
Starting EvRouter...device  0: /dev/input/powermate: Griffin PowerMate
Display name: :0.0
Parsed 2 rules, 96 bytes
tmp-file created......done

In evrouterrc i have:
Window ""
"Griffin PowerMate" "" any rel/7/1 "XKey/Down"
"Griffin PowerMate" "" any rel/7/-1 "XKey/Up"

which should do a scrolling, but isn't.

do you have any ideas?

regards,
gerd

---

### Post by shdawson on 2013-03-03
> **auser2 said:**
> Hello,

I just downloaded the Zip from the last post and installed "PowerMate & Linx Mint.deb" - which worked without problem.

It is working on Unity, but my usual Desktop is Gnome (I use Ubuntu 12.04) - and there it is not working!

Is it also working on Gnome Classic (Backport)?

How can i track down the problem?

The EvRouter Daemon seems to work:
Starting PowerMate at Sun Mar  3 14:31:12 CET 2013...device exists
Starting EvRouter...tmp-file created......done
Starting PowerMate at Sun Mar  3 14:31:12 CET 2013...device exists
Starting EvRouter...device  0: /dev/input/powermate: Griffin PowerMate
Display name: :0.0
Parsed 2 rules, 96 bytes
tmp-file created......done

In evrouterrc i have:
Window ""
"Griffin PowerMate" "" any rel/7/1 "XKey/Down"
"Griffin PowerMate" "" any rel/7/-1 "XKey/Up"

which should do a scrolling, but isn't.

do you have any ideas?

regards,
gerd

It only works after the boot, log-on, wait about 10-seconds approach.  There is a temp file created for the device. The OS sets that up.  It is a matter of letting the OS setup that file.  Now, if you can resolve that problem, please let me know.  I am running Linux Mint.  I unplug it at the end of my day and plug it in the next day.  It works for me, I love it.  I read a lot of pages, so vertical scrolling is a benefit like no other through this device.

---

### Post by auser2 on 2013-03-03
Hello shdawson,

Yes, the reboot was it! Is the re-plugin really necessary? Is there no workaround (i remember to read something about startup scripts in the beginning of the thread).

regards,
Gerd

---

### Post by shdawson on 2013-03-03
> **auser2 said:**
> Hello shdawson,

Yes, the reboot was it! Is the re-plugin really necessary? Is there no workaround (i remember to read something about startup scripts in the beginning of the thread).

regards,
Gerd


The OS has to create that temp file for the device.  That is OS specific.  Let me know what you get working.


-SHD

---

### Post by saegematz on 2013-04-08
would be to be had cool sometime even more options. For example, I have the keys "high" and "under it" and Return. Is to the song select thought with a Car PC. If I select, however, no song and only the key presses it would be to be had cool then maybe 5-second time to have instead of "high" & "under it" the function according to loud and  more quietly. I do not suppose that Powermate the difference knows between turn and with pushed  button  turn.
But I have to run it the first time immediately got.
Big thanks to you to all
Soory for my bad english.
Translation tool used

---

### Post by shdawson on 2013-04-09
The Powermate does transmit unique signal with push and turn.

Run the command:
sudo evrouter -D /dev/input/event*


This will show what DEVICE ID and what EVENT ID your Griffin PowerMate is set to.

Lets go with the example the the PowerMate is set to EVENT 11.  Run the following syntax:
sudo evrouter -d /dev/input/event11


Then, turn the PowerMate knob, push and turn the knob, whatever you want.  You will see all kinds of stuff show up in the terminal window.  These are the commands (information) that the PowerMate is transmitting and how the operating system, in my case Linux Mint, is seeing that information.

Go to:
/etc/hesus/conf/evrouterrc

...and edit the file.  This is the configuration file.


Enjoy!

---

### Post by pravinbravi on 2013-12-12
[SIZE=1]*Also posted the same at: [http://askubuntu.com/questions/138148/need-help-with-griffin-powermate-usb-volume-controller-new-64-bit-desktop-ub/390013#390013](http://askubuntu.com/questions/138148/need-help-with-griffin-powermate-usb-volume-controller-new-64-bit-desktop-ub/390013#390013)*[/SIZE]

For a very long time I had been struggling to  get powermate working in Ubuntu, my favourite OS. It was frustrating and  finally I got it going and I do want to share with you all how I did.  My sincere thanks to all the people from the references. I needed  something more definitive, there is none available. Therefore this  endeavour.
  This is how I got my ***volume control*** with ***Griffin Powermate*** USB device  working in ***Ubuntu Saucy Salamander 13.10 amd64***. Please bear with me and  do the following.

  **References.**
  
[LIST=1]
[*][http://screamingroot.org/node/5](http://screamingroot.org/node/5) 
[*][http://www.mp3car.com/input-devices/146252-using-griffin-powermate-in-linux.html](http://www.mp3car.com/input-devices/146252-using-griffin-powermate-in-linux.html) 
[*][http://www.bedroomlan.org/projects/evrouter](http://www.bedroomlan.org/projects/evrouter) (for evrouter) 
[*][http://tomthegeek.blogspot.com/2007/05/griffin-powermate-working-with-ubuntu.html](http://tomthegeek.blogspot.com/2007/05/griffin-powermate-working-with-ubuntu.html) 
[*][http://ubuntuforums.org/showthread.php?t=1346654&page=3](http://ubuntuforums.org/showthread.php?t=1346654&page=3)
[*][http://superuser.com/questions/471253/ubuntu-how-to-run-a-terminal-command-on-boot](http://superuser.com/questions/471253/ubuntu-how-to-run-a-terminal-command-on-boot) 
[/LIST]
  [B]
HowTo:[/B]
  
A. Make a file "/etc/udev/rules.d/10-local.rules" and put the following in the file
  
```
sudo gedit /etc/udev/rules.d/10-local.rules
```
  
code line:
  
```
SUBSYSTEMS=="usb", ATTRS{product}=="Griffin PowerMate", KERNEL=="event?", NAME="input/powermate"
```
  
Save and close
  
B. Create group called "powermate" add yourself and other users to  that group, you can give it a GID of 1001 or some like that. You can do  so by editing the file /etc/group
  
```
sudo gedit /etc/group
```
  
code line:

```
powermate:1001:your-user-name
```
  
C. Now edit / make file "/etc/udev/rules.d/40-permissions.rules" and add the following
  
```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```
  
code lines:
  
```
ATTRS{product}=="Griffin PowerMate" GROUP="powermate", MODE="0666"
```
  
Save and close.
  
D. Download and install evrouter from: [http://www.bedroomlan.org/projects/evrouter](http://www.bedroomlan.org/projects/evrouter) or use the repository at [http://www.bedroomlan.org/bedroomlan-debian-repository](http://www.bedroomlan.org/bedroomlan-debian-repository)
  
E. Create /etc/evrouterrc (or $HOME/.evrouterrc, I prefer /etc/evrouterrc) with the following:
  
```
sudo gedit /etc/evrouterrc
```
  
code lines:
  
```
Window ""
"Griffin PowerMate" "" any key/256 "XKey/XF86AudioMute"
"Griffin PowerMate" "" any rel/7/1 "XKey/XF86AudioRaiseVolume"
"Griffin PowerMate" "" any rel/7/-1 "XKey/XF86AudioLowerVolume"
```
  
F. Find out the powermate input event number (in mine it is event7), by running the following command. 
  
```
evrouter /dev/input/*
```
  
In the long output, you should see a line like the following
  
```
device  0: /dev/input/event7: Griffin PowerMate
```
  
G. Create /usr/local/bin/powermate with:
  
```
sudo gedit /usr/local/bin/powermate
```
  
code lines:
  
```
#!/bin/sh
evrouter -c /etc/evrouterrc /dev/input/event7
```
  
H. If you are a lazy guy like me and would like it to autorun at  start up, you can do so by adding the script file to, /etc/rc.local or  any such other.
  
```
sudo gedit /etc/rc.local
```
  
code line (add before exit 0 line):
  
```
/usr/local/bin/powermate
```
  
Save and close.
  
Try it and see. Best of luck. I love it now. Hopefully you folks can get it working it too.

---

### Post by shdawson on 2013-12-14
Thanks!

Some questions and concerns:
-Generating a group manually with an arbitrary group ID, instead of using the groupadd command, which will make sure that the ID created is the correct number and there are no clashes with existing groups. Why did you go with manually generating the group ID?

-Allowing write access for the device to all with the dreaded 0666. This is asking for trouble on many levels. Can the permissions be reduced to 0640, with what you have assembled?


Kindly,
SHD

---

### Post by pravinbravi on 2014-03-01
I tried, but it didn't work. Funny. And also the group ID keeps changing on every restart.

---

### Post by shdawson on 2014-03-01
OK, well then the groups will need to be manual with an arbitrary ID.

How about the permissions? Did you try changing those?

-S

---

### Post by kellyvotrenom on 2014-03-15
I have been searching the internet trying to get my Griffin Powermate to work as a volume up/ down, mute on/off. I have tried various solutions that have been posted and I have searched this forum and tried most of the solutions in this thread.  I am using ubuntu 12.04 with the LXDE desktop on this machine.


Tried this: [http://screamingroot.org/node/5](http://screamingroot.org/node/5)
Have created '/etc/evrouterrc' but the reference to this '(or $HOME/.evrouterrc)' confuses me a little.The final line 'Setup your session to auto-run powermate on login (or just be lazy like me and run it when you need it).' is something I don't understand - I don't even get how to run powermate manually. Also, I'm not sure if the commands here refer to volume control or some other functions.


My group name is 'powermate' not 'video'.  I am a member of the group, the evrouter daemon is running and seeing the powermate.  The Power Mate is event 5, when I run 'sudo evrouter -d /dev/input/event5'  I see '"Griffin PowerMate" "/dev/input/event5" none key/256 "fill this in!"
' (or rel/7/ + or - 1 when I turn the knob)


Then I attempted the hesus-powermate package which I installed thru GDebi but when I went to look at the installed files (etc/hesus/ for example) they aren't there.  If I click on the 'treminal' tab in GDebi it looks like some sort of error but the terminal window doesn't persist long enough for me to read it.  In any event, it doesn't seem to install.


The last things I attempted were to change the 'evrouterrc' file to:


Window ""
"Griffin PowerMate" "" any key/256 "XKey/XF86AudioMute"
"Griffin PowerMate" "" any rel/7/1 "XKey/XF86AudioRaiseVolume"
"Griffin PowerMate" "" any rel/7/-1 "XKey/XF86AudioLowerVolume"


and change the ' /usr/local/bin/powermate ' to include the line :
evrouter -c /etc/evrouterrc /dev/input/event5


I also created '/etc/udev/rules.d/40-permissions.rules' with the code line 'ATTRS{product}=="Griffin PowerMate" GROUP="powermate", MODE="0666" '


and then finally put this line in rc.local '/usr/local/bin/powermate'.  




Any help would be appreciated.


mark springer
industrial arts

---

### Post by shdawson on 2014-03-15
I think you have pieces of different options going, but they are not going to work together.

[http://ubuntuforums.org/showthread.php?t=1346654&page=4&p=12202644#post12202644](http://ubuntuforums.org/showthread.php?t=1346654&page=4&p=12202644#post12202644)

I recommend uninstalling everything you have tried and trying this option. If it works, and it probably will, then we can tweak from there. Otherwise, you have a system issue that needs further diagnosis.

FWIT, evrouter-0.4 helped a lot to get it going for me.

-SHD

---

### Post by kellyvotrenom on 2014-03-15
Thanks, I was thinking that as well.  I 'll go back and re-trace my steps and remove what I have installed.  I may just re-install Ubuntu since this had been a side by side install with Windows and I will not be running that OS on this machine any longer.

I do have evrouter 0.4 installed on the machine, so after I clean things up I may have an easier go of it.

Thanks again, I will post again with my success - or more questions :)

---

### Post by ikt on 2014-03-16
Anyone have any ideas on getting the script to run on login?

I've tried rc.local, a cronjob, the ubuntu startup applications program, none of them work.

rc.local just doesn't appear to run, when I put in something to test it, i get output from the test but nothing from the script.

cronjobs complain of no X display to output to, running the script as root in the current session appears to be the hard part.

Anyone got it working? (Ubuntu 14.04)

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/bin/powermate.sh

exit 0

and my powermate.sh:

> #!/bin/sh
/usr/bin/evrouter -c /etc/evrouterrc /dev/input/event12

With 755 file permissions.

---

### Post by kellyvotrenom on 2014-03-19
Still having problems with getting this to work




Did a new install of Fubuntu, installed evrouter and then installed 'PowerMate & Linx Mint.deb'.  Went to check the files under etc/hesus and there weren't any.  Tried a reboot and received an error (something about 'major systems error - sorry didn't make a note of it)


Tried to create the /etc/apt/sources.list.d/bedroomlan.list file but couldn't figure how to with the new install.  I had learned previouly to create new files using gksudo nautilus so I tried that and received no response. Figured I needed to install Nautilus an when I went to Synaptic I got this error:


Software index is broken
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


So I figured I needed to remove the hesus package but went I went to GDebi to remove I got this:
E: The package hesus-powermate needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


Added these lines to /etc/apt/sources.list &#64257;le thinking that might be the problem. Not it (I didn't think so but a shot in the dark)
deb [http://debian.bedroomlan.org/debian/](http://debian.bedroomlan.org/debian/) unstable main non-free contrib
deb-src [http://debian.bedroomlan.org/debian/](http://debian.bedroomlan.org/debian/) unstable non-free contrib


Searched for solution and tried sudo apt-get update and then sudo apt-get install -f.  Got the hesus powermate error message in terminal.  Finally tried sudo dpkg --remove --force-remove-reinstreq hesus-powermate


and back to normal.


But what is the problem and how do install the hesus powermate package?  Is that what I am trying to do?  I asssume this from the link you posted.


Thanks
mark springer
industrial arts

---

### Post by kellyvotrenom on 2014-03-29
Finally got it working - 


Followed the directions here :* [http://screamingroot.org/node/5](http://screamingroot.org/node/5)*


	but changed the group name in /etc/udev/rules.d/powermate.rules to powermate and made sure I was part of the powermate group.


SUBSYSTEM=="input", ATTRS{idVendor}=="077d", ATTRS{idProduct}=="0410", SYMLINK+="powermate", MODE="660", GROUP="powermate"


	And then changed the content of /etc/evrouterrc from this:
Window ""
"Griffin PowerMate" "" any key/256 "XButton/2"
"Griffin PowerMate" "" any rel/7/1 "XButton/5"
"Griffin PowerMate" "" any rel/7/-1 "XButton/4"


	to this:
Window ""
"Griffin PowerMate" "" any key/256 "XKey/XF86AudioMute"
"Griffin PowerMate" "" any rel/7/1 "XKey/XF86AudioRaiseVolume"
"Griffin PowerMate" "" any rel/7/-1 "XKey/XF86AudioLowerVolume"
from this site: *[http://www.mp3car.com/input-devices/146252-using-griffin-powermate-in-linux.html](http://www.mp3car.com/input-devices/146252-using-griffin-powermate-in-linux.html)*


	and finally got the volume to work by running this command:


'sudo evrouter -c /etc/evrouterrc /dev/powermate'
 from this link: *[http://www.linuxquestions.org/questions/linux-hardware-18/don't-understand-instructions-for-griffin-powermate-mouse-4175490996/](http://www.linuxquestions.org/questions/linux-hardware-18/don't-understand-instructions-for-griffin-powermate-mouse-4175490996/)*
(see bottom of post)


My questions now are:


Why do I have to run it as sudo? I placed evrouterrc in the home folder but it wouldn't run using  'evrouter -c /etc/evrouterrc /dev/powermate'.  I renamed the file .evrouterrc (which I learned makes it hidden) but still not running as regular user.  Also, how would I get it to run on log in?






Thanks


Mark Springer
industrial arts

---

