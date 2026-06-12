---
title: "[SOLVED] help running my script on startup"
date: 2008-10-07
forum: General Help
---

### Post by porchrat on 2008-10-07
Hi again all.

Trying to get a REALLY simple one-liner script to run on startup...and am having some trouble.

The command I want to execute is this:

```
aticonfig --pplib-cmd "set fanspeed 0 65"
```

I need it to run as my 4850's fan doesn't kick in automatically (some sort of firmware issue) and I'd rather manually set the fan to run like this as opposed to messing with the BIOS on the card. (At least until ATI sort this thing out)

Anyway I put that line in a .sh script with a shebang and moved it to /etc/init.d and then used chown and chmod to match it to the other files in /etc/init.d

I then ran:

```
sudo update-rc.d foobar defaults
```

However it doesn't execute on startup.  Is it perhaps because it attempts to run before "aticonfig" commands can be executed?  i.e. before the ati stuff has loaded?

Hopefully this has been mentioned before on this forum and a simple link is all that is required, however I was unable to find something pertaining to this problem in particular (I'm bad at searching this forum so chances are I've missed it).

Any help is most appreciated.

---

### Post by Idefix82 on 2008-10-07
Simply putting the script into the /etc/init.d won't do, you also need to create a link in the /etc/rc2.d directory. You may want to read through the following excellent tutorial:
[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/]("http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/")

Sorry, I think you can ignore my comment. Your command should be fine I would have thought. But you can check it by looking at the /etc/rc2-d/ folder.

---

### Post by justleen on 2008-10-07
place the one line in /etc/profile? that gets executed for all users..
(Im not a star with update-rc.d, so I usually work around that)

---

### Post by geirha on 2008-10-07
Add the line to /etc/rc.local, which is executed as one of the last boot-up scripts.

EDIT: Also, to be on the safe side, supply the absolute path to aticonfig, in case it's not in $PATH at the time the script runs. Do ```
which aticonfig
``` to get the absolute path.

---

### Post by porchrat on 2008-10-07
> **Idefix82 said:**
> Simply putting the script into the /etc/init.d won't do, you also need to create a link in the /etc/rc2.d directory. You may want to read through the following excellent tutorial:
[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/]("http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/")

Sorry, I think you can ignore my comment. Your command should be fine I would have thought. But you can check it by looking at the /etc/rc2-d/ folder.

I believe I already created the link...I took a look in the /etc/rc2.d directory and I can see the link to "/etc/init.d/foobar" in there.

It's weird I don't understand why it doesn't execute...the S-link is right there.

Perhaps I will try justleen's idea.  I'm not really a big fan of doin that though as there isn't really a way to find it again in the future (other than trying one massive "grep") to comment the thing out...I mean...if I forget where I put it (as I'm sure I will).  Whereas at least with the /etc/init.d rc2.d link I can do a "find" for it.

---

### Post by porchrat on 2008-10-07
> **geirha said:**
> EDIT: Also, to be on the safe side, supply the absolute path to aticonfig, in case it's not in $PATH at the time the script runs. Do ```
which aticonfig
``` to get the absolute path.

That is a great idea and was sort of what I was trying to say in the initial post.  So should the script rather look something like this:

```
/usr/bin/aticonfig/./aticonfig --pplib-cmd "set fanspeed 0 65"
```

---

### Post by geirha on 2008-10-07
```
/usr/bin/aticonfig --pplib-cmd "set fanspeed 0 65"
```

should suffice

---

### Post by porchrat on 2008-10-07
> **porchrat said:**
> That is a great idea and was sort of what I was trying to say in the initial post.  So should the script rather look something like this:

```
/usr/bin/aticonfig/./aticonfig --pplib-cmd "set fanspeed 0 65"
```

OK that didn't work...any idea why?  I could try the recommendation of piggy-backing off one of the boot-up scripts, but I really would prefer this to be a stand-alone file...that way it is easier to deal with later when my bad memory lets me down.

By the way thank you for this link: [http://pthree.org/2008/02/26/managin...-to-runlevels/](http://pthree.org/2008/02/26/managin...-to-runlevels/) it was a very interesting read and I didn't know all that about runlevels before..despite having used the "init" command many times before to halt and/or restart the system (because you know that shutdown button in the top right corner just seems so far away in comparison to a few keystrokes :))

---

### Post by justleen on 2008-10-07
use /usr/bin/aticonfig/aticonfig

no need to declare the ./ since your using an abosulute path

---

### Post by porchrat on 2008-10-07
> **geirha said:**
> ```
/usr/bin/aticonfig --pplib-cmd "set fanspeed 0 65"
```

should suffice

Also didn't work...darn. :(

Maybe there is something wrong with my script? Maybe it needs a little more structure.

Like a "exit 0" at the end?

I'll give it a go and let you know.

Edit: Thought I would show you exactly what I have sitting in /etc/init.d 

```
#!/bin/sh

/usr/bin/aticonfig/aticonfig --pplib-cmd "set fanspeed 0 65"

```

---

### Post by comandrei on 2008-10-07
Put it in /etc/rc.local

---

### Post by geirha on 2008-10-07
> **porchrat said:**
> 
```
#!/bin/sh

/usr/bin/aticonfig/aticonfig --pplib-cmd "set fanspeed 0 65"

```

I don't use the proprietary ati drivers myself, but does it really put the binary inside a directory under /usr/bin ?!

Are you certain it's not /usr/bin/aticonfig?

---

### Post by porchrat on 2008-10-07
> **geirha said:**
> I don't use the proprietary ati drivers myself, but does it really put the binary inside a directory under /usr/bin ?!

Are you certain it's not /usr/bin/aticonfig?

For real...the path is /usr/bin/

aticonfig sits there in /usr/bin/, but it is an excutable binary, not a directory containing the binaries...weird huh?

EDIT: OK moved the thing into rc.local ...didn't realise that script actually did nothing...lets see what happens.

---

### Post by geirha on 2008-10-07
> **porchrat said:**
> For real...the path is /usr/bin/

aticonfig sits there in /usr/bin/, but it is an excutable binary, not a directory containing the binaries...weird huh?


No, that's not weird, that's how it should be :)

So you need to use /usr/bin/aticonfig, not /usr/bin/aticonfig/aticonfig

---

### Post by porchrat on 2008-10-07
Realised that before you had even replied :)...changed the path to remove the last "aticonfig"...still didn't work...damn you ATI!!

This is seriously strange...I do however want to thank you guys for all the help so far...I have learnt a lot (despite not being able to make it work), which I suppose in the end is the point.

I'm going to try it in /etc/init.d one last time with the correct path this time...I doubt it will work though.

If it doesn't I suppose I will just have to try and remember to run this script every time I start the machine...and pray that my memory holds out and one day I don't forget and end up with a 4850 idling at 81 degrees celcius...could fry eggs on that.  (yum...eggs)

If any you have any other ideas I would once again be grateful for the help.  Again thank you for the help so far it is most appreciated.

---

### Post by geirha on 2008-10-07
Try adding a line below the aticonfig line with:
```
echo "aticonfig exited with status $?" &>/tmp/aticonfig-test
```

Then, after it should've been run, look and see what the content of /tmp/aticonfig-test is.

---

### Post by porchrat on 2008-10-07
> **geirha said:**
> Try adding a line below the aticonfig line with:
```
echo "aticonfig exited with status $?" &>/tmp/aticonfig-test
```

Then, after it should've been run, look and see what the content of /tmp/aticonfig-test is.

OK I will try that...what does the "$?" argument mean?...just out of interest.

---

### Post by Idefix82 on 2008-10-07
Why don't you just start the script by hand using the start command as described in the tutorial I referred you to? Then at least you will know whether the script works.

---

### Post by geirha on 2008-10-07
$? is a special variable containing the exit status of the last run command. In this case, aticonfig.

The exit status is 0 if the command ran ok, anything else means it failed.

---

### Post by porchrat on 2008-10-07
Strangely enough /tmp/aticonfig-test is empty.  It was created...its just empty.

The thing is when I run this script from the console it runs without a problem.  Starts the fan up right away.

OK  when I run the script (just from the console...not running the one in /etc/init.d however they are the same script) I get this:

```
PPLIB command execution is Successful!
aticonfig exited with status 0
```

Also doing this results in the exact same output as that seen above:
```
/etc/init.d$ sudo ./4850fanspeed.sh stop
```

EDIT: forget that stupid comment...I see what you are talking about, but no matter which argument I put behind it (start, stop restart etc.) it seems to ignore it...just runs the script

---

### Post by geirha on 2008-10-07
Ah, sorry, that was bash syntax, not sh. Using > instead of &> should work, however the command has run if that file is created (even though it's empty), so for some reason it doesn't work when run from init.

---

### Post by blue13130 on 2008-10-07
> **comandrei said:**
> Put it in /etc/rc.local

I second this idea.  Use rc.local for this rather than an init.d script.  So much easier to do.  Just add the command you want to execute to /etc/rc.local

---

### Post by porchrat on 2008-10-07
> **blue13130 said:**
> I second this idea.  Use rc.local for this rather than an init.d script.  So much easier to do.  Just add the command you want to execute to /etc/rc.local

tried that...still doesn't run

---

### Post by Idefix82 on 2008-10-07
If
```
sudo /etc/init.d/foobar start
```
works then I can't see it not working on startup. Just use update-rc.d to make it start in run level 2 as the very last thing.
If on the other hand the above command does not work then the question is why does it start when you execute it elsewhere but not when it sits in init.d.

---

### Post by geirha on 2008-10-07
Perhaps the fglrx kernel module isn't loaded at the time aticonfig is run. Try adding ```
lsmod >/tmp/lsmod-output
``` at the end of the script to see what modules are loaded right after it has been run.

---

### Post by porchrat on 2008-10-07
OK have used update-rc.d to move the script to number 99 (right down there with rc.local) and left it at position for stop at runlevel 0 1 and 6.

Have also added lsmod >/tmp/lsmod-output to the script...will now restart, lets see what happens.

---

### Post by bodhi.zazen on 2008-10-07
Make sure your script and/or /etc/rc.local are executable.

---

### Post by porchrat on 2008-10-07
OK tried it at position 99...didn't run.

lsmod ouput file shows this (grepped version so we don't have to wade through relatively large ouput):

```
snd_seq_midi           10688  0 
serio_raw               9092  0 
fglrx                2054892  0 
snd_rawmidi            29856  1 snd_seq_midi
psmouse                46236  0 

```

looks to me like fglrx is already loaded when the script executes...?  Well...I'm stumped.

Is it just me or is fglrx freaking HUGE?

EDIT: the /etc/init.d/foobar.sh is executable...as are the links in /etc/rc*.d

---

### Post by geirha on 2008-10-07
Without knowing what that aticonfig command is trying to do, I can't think of anything more to try either. Does ati provide any support perhaps?

---

### Post by porchrat on 2008-10-07
I'll have to check their website for contact details, hopefully they will either tell me what aticonfig does and give me an idea as to why it doesn't run off init.d or they will solve the issue with the fan and let me know.  I mean if the fan worked I wouldn't need this workaround.  I haven't seen anything in my searching, but who knows, they may have solved this already.

Anyway thank you all for your help it is most appreciated.  Once again I am amazed at the generosity and the willingness to help and teach here at ubuntuforums.

I will of course continue to pop in and check out this thread so please feel free to jot down any ideas you may have.

Thanks again.
Porchrat

---

### Post by nitrousoxide82 on 2008-10-23
May it be that it is needed for X to be running? I have one of those early-run 4850's made by Powercolor and also ran into problems with it. I found the workaround for Windows in a Google search, and kept wondering if there was such a workaround for Linux and ended up finding the thread where this command was posted. (I'll be sure to head back there and say "Thanks!" :) Well, as I kept wondering, the card kept idling at 82 degrees C (compared to 58 degrees C on Vista with the workaround enabled). I ran this command under X and it worked, the fan kicked up and the idle temp. went down to 60 degrees C.

Now to the point, if it is the case that X needs to be running in order for the command to work, put the startup script in /etc/X11/Xsession.d instead of /etc/init.d, and that might work.

[Edit] I confirmed it now, aticonfig fails when trying to run with those options while X is not running. Placing the script in /etc/X11/Xsession.d causes the fan workaround to "kick in" as soon as you log into X -- but there might be a better place to put it into, to get it to set the fan up right after X starts.

---

### Post by porchrat on 2008-10-23
> **nitrousoxide82 said:**
> May it be that it is needed for X to be running? I have one of those early-run 4850's made by Powercolor and also ran into problems with it. I found the workaround for Windows in a Google search, and kept wondering if there was such a workaround for Linux and ended up finding the thread where this command was posted. (I'll be sure to head back there and say "Thanks!" :) Well, as I kept wondering, the card kept idling at 82 degrees C (compared to 58 degrees C on Vista with the workaround enabled). I ran this command under X and it worked, the fan kicked up and the idle temp. went down to 60 degrees C.

Now to the point, if it is the case that X needs to be running in order for the command to work, put the startup script in /etc/X11/Xsession.d instead of /etc/init.d, and that might work.

[Edit] I confirmed it now, aticonfig fails when trying to run with those options while X is not running. Placing the script in /etc/X11/Xsession.d causes the fan workaround to "kick in" as soon as you log into X -- but there might be a better place to put it into, to get it to set the fan up right after X starts.

Firstly I would like to say well done!  I'm glad someone had the presence of mind to figure this out because it was really stumping me.  I think you are right about X needing to be running first and I will of course investigate further.

I tried putting the script under /etc/X11/Xsession.d/4850fan.sh and X wouldn't start, logged into a shell and removed the script afterwards.  However as X was loading up it did indeed start the fan so at least I know that is the right place for the script...I will write down the error message and post it here, first I need to replicate the error.

Is there any particular method you followed when you moved the script in there?  Did you create any links or anything?

EDIT:  Nevermind I figured it out...I was trying to write an exit status ouput to /tmp in that particular script when I was trying to debug it under /etc/init.d and that seems to have been causing some errors...thanks for the solution you really have helped me out (me and all others that don't feel comfortable doing unofficial firmware updates on their early-model 4850's)

---

### Post by geirha on 2008-10-23
If that's the case, you might be able to run it a little bit sooner, right when the login screen has started. Try running the script from /etc/gdm/Init/Default

[http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en)

---

### Post by nitrousoxide82 on 2008-10-23
So that's the "better place" to put it for GNOME. I wonder where it is for KDE, I think I may have to edit /etc/kde3/kdm/Xstartup and place the command in there... I wonder if there is a better way (like just placing the script into some directory)? I'm mostly positive it will work, but that script might get overwritten in case of a KDE package upgrade.

Thanks for any input given.

---

