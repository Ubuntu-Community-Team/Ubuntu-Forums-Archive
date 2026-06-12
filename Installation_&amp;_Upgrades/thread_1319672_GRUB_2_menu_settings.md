---
title: "GRUB 2 menu settings"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by ScottHW on 2009-11-08
Recently upgraded to Karmic (9.10).  Manually upgraded from GRUB (legacy) to GRUB 2.

Basically, things work fine.  I have a couple small issues I can't seem to get worked out, and didn't find posts describing them elsewhere.

I want GRUB 2 to act the same way GRUB (legacy) did; right after posting, I want "GRUB loading..." and a counter with 2 seconds delay, after which GRUB automatically boots the default option (in my case, Karmic).  The menu should NOT be displayed by default.

If I want to manually see the GRUB menu, to choose another boot option (WinXP), then there should be a key I can press to get to the GRUB menu; in GRUB (legacy) that key was ESC, now it's supposed to be SHIFT.

I've tried numerous times to edit /etc/default/grub (running update-grub after each edit).  Here's what I've found, what I believe are the relevant lines are shown.

```

...
GRUB_HIDDEN_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=FALSE
GRUB_TIMEOUT="0"
...

```

Results in "GRUB loading...", and then default boot.  Almost perfect, except that I thought the TIMEOUT_QUITE=FALSE was supposed to show a counter, according to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2).

More importantly, tho, is the fact that holding SHIFT does NOT bring up the GRUB 2 menu.


I've also tried
```

...
GRUB_HIDDEN_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=FALSE
GRUB_TIMEOUT="2"
...

```

This brings up the GRUB 2 menu, waits 2 seconds, then boots the default option.

How do I get what I want??

---

### Post by ScottHW on 2009-11-08
Oh, yah.  And two other things.

Anybody know whether 
```
GRUB_TIMEOUT="2"
```
actually is supposed to have the quotes?  Because the help ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) and wiki ([https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)) pages don't seem to show that, but they were in there after installing GRUB 2.  And I've seen a few other people posting their files that show the quotes.


Also, I believe the Wiki page ([https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)) has a typo; currently, it describes the setting
```
GRUB_HIDDEN_**MENU**_QUIET=true 
```
But most other documentation refers to this value as
```
GRUB_HIDDEN_**TIMEOUT**_QUIET=true 
```

Just FYI, because I haven't figured out if I am able to update that Wiki.

---

### Post by drs305 on 2009-11-08
I believe that Grub2 wiki is now redirected (or will be soon) to the ubuntu help documentation here: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")
but I have fixed it.

Holding down the SHIFT key does work, but because you have the "GRUB_TIMEOUT=0", it won't display the menu at all (it displays it for 0 seconds, then boots). Change the value to a positive integer and you will see the menu if you hold down the SHIFT key *during the initial boot process*.

There have been problems with the hidden menu, but yours is the first I've seen regarding not seeing the timer when the menu is hidden. As far as I can tell you have the correct settings.

The "quotes" issue doesn't matter, it will work either way.

---

### Post by pedja_portugalac on 2009-11-08
Excuse me to post my question here, just not to open new tread. There is one recommended update for grub this days, from (1.97~beta4-1ubuntu3) to 1.97~beta4-1ubuntu4. I have installed that one and by default it open configuration window with option "keep the current version installed". I have changed that option into "install package maintainer version". Please tell me if it's ok. Thank you very much and ones again excuse me to mix into your tread.

---

### Post by drs305 on 2009-11-08
> **pedja_portugalac said:**
> Excuse me to post my question here, just not to open new tread. There is one recommended update for grub this days, from (1.97~beta4-1ubuntu3) to 1.97~beta4-1ubuntu4. I have installed that one and by default it open configuration window with option "keep the current version installed". I have changed that option into "install package maintainer version". Please tell me if it's ok. Thank you very much and ones again excuse me to mix into your tread.

Yes it is ok, but any changes you have made to /etc/default/grub will be removed and you will have to make them again.

There is nothing wrong with opening a new post for such a question and is considered more polite.

---

### Post by ScottHW on 2009-11-09
drs305, thanks for your replies.  Forgive my ignorance, I don't know if you are on the GRUB dev team...?

Firstly, the quotes; if it makes no difference, perhaps the documentation and default files and the like should all use the same notation?  Either use the quotes, or let's get rid of them.  Might help to eliminate some confusion.

Next, I tried
```

GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=FALSE
GRUB_TIMEOUT=0

```
thinking that this would give me 10 seconds of countdown to manually bring up the GRUB menu.  But nope, after what seemed to be a short (<< 10 sec) delay, it booted default.

Now I tried
```

GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=FALSE
GRUB_TIMEOUT=10

```
Again, basically no delay BEFORE the menu, no countdown or anything.  Then 10 sec of delay waiting for me to make a choice.
From the help page:
[indent]**GRUB_HIDDEN_TIMEOUT=0 **
*# For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds. *
[/indent]

Am I misunderstanding these settings...?  Which code exactly is supposed to be executing these delays?  I know I don't fully understand the /boot/grub/grub.cfg file, but I don't see anything in there that looks like a delay at all.

If required, I can gladly copy or attach the other GRUB 2 settings files.

---

### Post by ScottHW on 2009-11-09
drs305, another aside.  If you are able to make changes, the help page Contents (index on the top-right of page) currently directs 
[INDENT]4. File Structure[indent]2. /etc/default/grub[/INDENT][/indent]

and 
[INDENT]5. Configuring GRUB 2[indent]1. /etc/default/grub[/INDENT][/indent]

to the same html anchor.  I believe the second one is in error.

---

### Post by drs305 on 2009-11-09
> **ScottHW said:**
> drs305, thanks for your replies.  Forgive my ignorance, I don't know if you are on the GRUB dev team...?
No, not even close. I am just an everyday user who is learning about G2. And there are huge gaps in my knowledge, as I don't often dual boot, don't install Windows, and don't try to configure USB devices. That is why I ask those that do to come up with guides for the rest of us. You can make an argument that this is the responsibility of the GRUB devs, but remember we all do this for free.

> 
Firstly, the quotes; if it makes no difference, perhaps the documentation and default files and the like should all use the same notation?  Either use the quotes, or let's get rid of them.  Might help to eliminate some confusion.

As I looked at the files, it appears that different devs had different styles. I agree it would be better if standardized. I will confirm it makes no difference with single entries without spaces and at least make the community doc page consistent. 

> 
Am I misunderstanding these settings...?  Which code exactly is supposed to be executing these delays?
GRUB_HIDDEN_TIMEOUT - Hides the menu (but not splash) for the given time. To display the menu immediately, place a # symbol at the start of this line.
GRUB_HIDDEN_TIMEOUT_QUIET - *False* is supposed to present a countdown timer in the upper left corner of a blank (or splash image bg) screen. *True* leaves a blank screen (or splash) with no countdown timer visible.
GRUB_TIMEOUT= Starts the timer *once the menu is displayed, if it is ever called up*. Whether or not the menu is displayed is decided by the "GRUB_HIIDEN_TIMEOUT" line. 

In your first example in the previous post, the menu should be hidden for 10 seconds with a countdown timer in the upper left of a blank (or splash image) screen with no menu visible. When 10 seconds elapse, it should boot to the default OS without ever seeing the menu.

In the second case, there should be a blank screen and countdown timer for 10 seconds, after which the menu should display for 10 seconds. Then the default OS should boot.

So I think you have the correct understanding. I have one machine on which the hidden menu works fine. On the other, I have to change a setting (I filed a bug report):
***Try this***: add this line and see if the hidden menu starts working:
> GRUB_DISABLE_OS_PROBER=true
then update-grub.
Of course, you will lose your automatic search for your other OSs, but at least you can see if you can get a hidden menu option to work.

 	
> Side note
The menu is auto-generated. I changed the title slightly in one of the subsections so it would not confuse the menu creator. Thanks for pointing this out.

---

### Post by ScottHW on 2009-11-09
Thanks for your help, drs305.  We seem to understand the settings the same way, so I'm not sure what exactly is going on.

I tried your suggestion
```

GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=TRUE
GRUB_DISABLE_OS_PROBER=TRUE
GRUB_TIMEOUT=10

```

but no change; no delay, no counter, then the menu shows up with a 10 second delay.

Also, my "other OS" WinXP still showed up after I ran update-grub.  I guess I don't know exactly when the OS discovery takes place, but since it didn't fix my issue anyway, it really makes little difference.

Are there any other diagnostics we can try?  Log files somewhere I could check, referring to GRUB actions?

---

### Post by drs305 on 2009-11-09
> **ScottHW said:**
> 
Are there any other diagnostics we can try?  Log files somewhere I could check, referring to GRUB actions?

Unfortuately I am away on a business trip for the next 3 days. On my desktop, I can get it to hide with the OS prober line. On my laptop, which I am currently using, it doesn't (as with you). For troubleshooting, what I did was use an odd timeout value such as 18 in the hidden menu entry. Then after updating grub I searched the grub.cfg file for "18". I found an entry in the 30_OS... section when the menu successfully hid itself, and no "18" when the entry failed. It let me try lots of combinations without having to reboot to check to see if it worked. Anytime I found the "18" it hid the menu; whenever it wasn't present it wouldn't hide it.

The /usr/sbin/grub-mkconfig file is the one that controls things. I printed it out and it is about 3 pages long. If you want to see exactly what steps G2 is taking to construct the menu this would be the file to look through.

I have no special skills to troubleshooting this but I am going to continue to play with combinatins and looking for a solution.

---

### Post by ScottHW on 2009-11-09
I like your idea about the uncommon delay to be used as a search term.  I'll take a look through some files, see what I can learn.

Well done, too, figuring out one of the contributing factors to whether or not the menu is being hidden.

To me, still, the main issue is
a) that the counter isn't delaying BEFORE the menu, and
b) that there is no counter display while delaying BEFORE the menu.
I'll try to track this down, with your "18" value search trick.

---

### Post by drs305 on 2009-11-09
ScottHW,

I tinkered with the files this evening and was able to get the hidden menu and timeout to work on my laptop. I wanted completely new G2 files, so here is what I did:
Copied my /etc and /boot/grub folders as a backup.
Uninstalled grub2 and grub-pc
Reinstalled grub-pc, then
sudo grub-install /dev/sda
sudo grub-install --recheck /dev/sda
Checked the /etc/grub.d to make sure the scripts were executable
(Some were not there, so I had to copy them from my backup /etc folder)
sudo update-grub

With new files, I changed the value of the hidden timeout, hidden timeout quiet, and added the os_prober false line. The final /etc/default/grub looked like this (I used a value of 180 this time to really stand out):
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=180
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
GRUB_DISABLE_OS_PROBER=true

```

With "sudo update-grub", it added the following lines in grub.cfg:
> 
### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if sleep --verbose --interruptible 180 ; then
    set timeout=0
  fi
fi
Having it put in the 30_os-prober section seemed odd, but that is where grub-mkconfig put it.

Knowing the lines which help hide the menu, at least in part since I haven't looked at the entire grub.cfg file yet, may allow us to place them elsewhere, and perhaps even restore 30_os-prober, although I will have to play with that at another time.

---

### Post by ScottHW on 2009-11-09
Wow, drs!  Impressive tinkering, I'll have to try this out when I get home.  Perhaps when you're back, we can compare.  While it works, it's such a strange concept to have to re-install with Linux, we ought to be able to compare files before/after your update process and figure out the offending lines/files/settings.

---

### Post by drs305 on 2009-11-09
I don't really recommend uninstalling and then reinstalling grub2 just to troubleshoot this. I just wanted to be absolutely sure the problem was not an extra space at the end of a line or something equally obscure that I might have done on my own. 

I am really interested in seeing if adding the sleep/timeout/verbose section somewhere else will allow re-enabling the os-prober.

---

### Post by raymondh on 2009-11-09
Nice work Drs.  :)

---

### Post by ScottHW on 2009-11-10
I don't really intend to uninstall/reinstall, but perhaps we can look at all the relevant files and find the differences/changes between yours and mine, and the changes we're making.  Along with anyone else who might be experiencing similar issues.

Need to figure out if this is specific to "Laptops", or what.  Because if all GRUB 2 installs were behaving this way, I think I would have found a bug about it already.

---

### Post by drs305 on 2009-11-10
The continuing saga:

I've now found a way to keep os-prober active and to get the hidden menu and hidden timeout features. 

Open /etc/grub.d/00_header as root:
```
gksudo gedit /etc/grub.d/00_header
```
Add this to the end of the file. "18" in this sample will hide the menu for 18 seconds:
> 
### BEGIN Hidden Menu Test ###
    cat << EOF
if [ ${timeout} != -1 ]; then
if  sleep --verbose --interruptible ${GRUB_HIDDEN_TIMEOUT}  ; then
    set timeout=${GRUB_HIDDEN_TIMEOUT}
fi
fi
EOF
### END Hidden Menu Test ###


Save the file and run "sudo update-grub".

1. The menu will be hidden for 18 seconds. Change the value as you wish. In this hack GRUB_HIDDEN_TIMEOUT prefers a blank to "O" if you don't want to hide the menu, although 0 will also work.
2. The GRUB_TIMEOUT value in /etc/default/grub will be honored. If and when the menu is displayed, it will be displayed for the value of this line and then boot the default OS.
3. The GRUB_HIDDEN_TIMEOUT line *will* be used.
4. The GRUB_HIDDEN_TIMEOUT_QUIET line *will* be honored.
5. You do not need the "GRUB_DISABLE_OS_PROBER" line in /etc/default/grub, so the menu will be hidden *and* it will search for other OS's.

Note I still consider this a hack and not a long term solution. ;-)

---

### Post by ScottHW on 2009-11-10
Brilliant!!

I agree, this does seem to be a "hack", but a perfectly working.  I'm saying all this from work, so I haven't even tested it on my Ubuntu laptop yet.

I only call it a hack because we haven't really isolated WHY the program wasn't working as designed/described.  So this doesn't address the underlying problem/bug, but DOES give the desired result.  Actually, we also don't know how wide-spread the "bug" we're working on actually is.  I'm kind of surprised that something relatively simple like this isn't being reported more.  Maybe it's just because I'm being picky about the behavior that I want.

I'll try it as soon as I get home.

Brilliant, drs

---

### Post by ScottHW on 2009-11-11
Alright; I modified my /etc/default/grub file like so, to make use of the easily-searchable idea.  Then I made sure to update the changes to /boot/grub/grub.cfg.
```

GRUB_HIDDEN_TIMEOUT=180
GRUB_HIDDEN_TIMEOUT_QUIET=FALSE
GRUB_TIMEOUT=120
...
scott@gateway:~$ sudo update-grub

```
By the way, you CANNOT keep back-up copies of your settings files like 00-header.bak in /etc/grub.d/ because they will just be compiled into the .cfg file, making duplicate entries.  I don't know what that would do to booting, because I caught it before trying.  Maybe nothing serious, maybe.

I looked through grub.cfg and found that GRUB_TIMEOUT=120 *did* translate into the lines
```
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=120
fi
```
written into the etc/grub.d/00_header section.

However, GRUB_HIDDEN_TIMEOUT=180 did *NOT* have any corresponding value assignment statement in grub.cfg.

So, while I don't exactly know the CAUSE of the problem, I think this is the core of it; ***for one reason or another, the Hide Menu instructions are NOT being written into the grub.cfg code.***

After implementing the previously mentioned drs305 Menu Hide Hack, and updating grub.cfg, the set timeout=120 lines are still present, followed by:
```
if [  != -1 ]; then
  if sleep --verbose --interruptible 180 ; then
    set timeout=180
  fi
fi
```
I'm a bit hesitant about the fact that that the inequality has no value on the left-hand side, but I'm certainly no expert programmer, and maybe this is totally acceptable...?

I guess let's give it a whirl...

---

### Post by ScottHW on 2009-11-11
Yes, Yes, YES!!!

Worked [SIZE="1"](almost)[/SIZE] exactly as it was supposed to.

GRUB loading...
(clears screen)
and then a counter, counting down from 180
upon pressing SHIFT, enters GRUB 2 menu
counting down form 120, with default option pre-selected

Overall, I would now give this aspect of GRUB 2 performance a 95%.  To bump it from A to A+ range, I'd like to see that (clear screen) behavior go away, because the numbers counting backwards on a totally blank screen certainly isn't much info from a usability standpoint.  I guess as I set my HIDE MENU delay back to 2 seconds, this will hardly matter, but still.

For that, then, I don't know if there's something "we" can do...?  Was one of the code lines in grub.cfg responsible for clearing the screen?

drs305, you are the man.

I'm going to file a bug for this, seems the appropriate thing to do.  I mean, if we both experienced this, then it's safe to assume other users (maybe only on laptops...?) are also getting this.

---

### Post by ScottHW on 2009-11-11
Actually, my earlier searches were not apparently effective, because when I tried to list the bug with Launchpad-- Ubuntu > “grub2” package > Bugs, I came across

Grub 2 1.97 Beta 4 Hidden Menu No Longer Works
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444495](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444495)

... which I now see was reported 6 wks ago, and has numerous comments, including none other than drs305.  Since you did all the work, you get all the glory;

Post your new solution there, I would consider your newest "hack" to be perfectly effective for Users.  The Dev team for GRUB 2 will need to take a look and see how/why this somehow went awry.

---

### Post by drs305 on 2009-11-11
That's the bug I've been updating, sorry I didn't link it earlier. I'll update the bug report when I return home from this trip.

The format of the conditional statement bothered me as well. I tried various versions but nothing seemed to work as well as the original, so I just left it that way. I am not a programmer - if I were it would really bother me to leave it like that. If someone can come up with a prettier format that works it would be great.

---

### Post by mbr78 on 2009-11-11
How do I install/enable graphical themes like these, [http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes), for GRUB2 in Ubuntu 9.10? I have read that Ubuntu 9.10 turns off the GRUB2 graphical menu by default.

---

### Post by ScottHW on 2009-11-11
mbr78

Good question, but typically you could either find a thread that addresses the question, or open your own.

This thread is related to a bug with the hide menu feature.


FYI, lots of info about GRUB 2 can be found at
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

And if you're interested in Graphical Menus, I assume you mean Splash screens...?
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming)

Actually, from your link, you appear to mean more than Splash screens.
Your link does actually have this line right at the top of the page....
[indent]*To learn how to create your own GRUB themes, refer to the [GRUB theme format manual]("http://http://grub.gibibit.com/Theme_format"). *[/indent]

Regardless, try another thread to address this further.

---

### Post by khanongsouk on 2009-11-12
i've found that if i edit a line in /etc/init.d/rc from CONCURRENCY=none to CONCURRENCY=shell the grub menu would not hide after two reboots and the cpufreq would be stuck in performance mode. 

After changing it back however, ubuntu would boot normally after two reboots and the cpufreq would eventually change to ondemand.

the /etc/init.d/rc file also states that "shell is obsolete".

hope this helps

---

