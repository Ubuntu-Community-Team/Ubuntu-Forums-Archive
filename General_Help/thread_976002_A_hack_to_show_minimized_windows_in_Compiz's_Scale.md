---
title: "A hack to show minimized windows in Compiz's Scale plugin"
date: 2008-11-08
forum: General Help
---

### Post by Greg T. on 2008-11-08
Attached is a Python script to deal with the fact that minimized windows aren't shown in Compiz's Scale plugin. The script unminimizes these windows, launches Scale, and (when Scale is finished) returns the windows to their previously minimized state.

It can be initiated via a hot corner using the CompizConfig Settings Manager or via a launcher. You're on your own to set up a hot corner or launcher; I won't explain these options here. (But see post #9 below from hamidoo for some help on hot corners.) These options are relatively simple, but I don't use hot corners and the process of setting up a launcher is a little different in each of Gnome, KDE, and XFCE.

This script is an imperfect hack, largely due to the processor-intensive task of unminimizing multiple windows at once. Window contents are discarded when windows are minimized and it takes time to recreate the contents when windows are unminimized, so the script can be a bit slow. On the other hand, on my middle-of-the-road desktop I was able to listen to Pandora skip-free even when unminimizing a couple dozen windows at once, though it took a while. 

[SIZE="4"]**Prerequisites**[/SIZE]

Make sure you have Scale and Dbus as enabled Compiz plugins (and optionally Scale Addons as well). One way to do so is through ccsm, the CompizConfig Settings Manager. Fire up a terminal window and type the following:

```
sudo apt-get install compizconfig-settings-manager
```

Then start ccsm to see what's enabled (you can use the "Filter" search box to help locate plugins):

```
ccsm
```

Oh, and make sure Compiz is actually running, not some other window manager. (This has happened to me more than once.) 

That out of the way, there are some dependencies that need to be met. To install them, type the following in a terminal:

```
sudo apt-get install wmctrl xwit python-wnck
```

[SIZE="4"]**Setup**[/SIZE]

Download the "scale.py" file attached below.

Make it executable.* Make sure to do this! If the script doesn't work, the most likely cause is that permissions were not set properly.* If you have saved it to your home directory as scale.py, type in a terminal:

```
chmod 755 scale.py
```

Try it out:

Code:

```
./scale.py
```

If it works, consider hooking it up using a hot corner or a launcher, as mentioned above.

[SIZE="4"]**Configuration**[/SIZE]

**Hot Corner Options--**If you set this script up with a hot corner and attempt to activate the script using the hot corner *while a previously activated instance of the script is already running*, you have several possible behaviors to choose from. Look for the first use of the "hotCornerOption" variable in the script to configure your preference.
    
[INDENT][0] (Default) First instance runs Scale with unminimizing windows. Second instance does nothing. (In other words, it continues to wait for user action to exit the first instance of Scale w/unminimized windows.)
    
[1] The instances alternate between Scale both with and without unminimizing windows, the first instance being Scale *without* unminimizing windows. (However, if there are no previously unminimized windows to choose from, the script unminimizes all windows.)
    
[2] The instances alternate between Scale both with and without unminimizing windows, the first instance being Scale *with* unminimizing windows. [/INDENT]

**Viewport Options--**Scale can show the windows in the current viewport (the default) or all viewports; this script can be adjusted for either option. To change this, look for the command near the end of this script that begins 'org/freedesktop/compiz...', as follows:
    
```
'/org/freedesktop/compiz/scale/allscreens/initiate_key'
```
        
To have Scale show windows from all viewports, change the command as follows:
    
```
'/org/freedesktop/compiz/scale/allscreens/initiate_all_key'
```
        
Regardless of which approach you use, only the windows in the current viewport are (un)minimized. To (un)minimize windows from all viewports would be a dizzying experience due to the rapid viewport changing it would require.

[SIZE="4"]**Bugs**[/SIZE]

In addition to being a bit slow in general, on occasion if a window unminimizes well before its screen contents are drawn (i.e., it's initially a gray box and later gets filled in), the script may begin re-minimizing windows prematurely. The script's re-minimization functionality is triggered when it detects a window activation event that occurs after Scale has started; in some rare cases, the late-breaking screen-drawing is interpreted as this event, rather than a user selection of a window. The behavior manifests itself shortly after Scale launches: windows will begin rearranging and disappearing spontaneously. The script includes a short timer to help catch and stop this problem, but it's not foolproof. If you have problems, you can adjust the timer. Look for the first instance of "pluginDelay" variable in the script to address this if it's an issue for you.

This bug is most likely to occur when there are a large number of minimized windows running on a slow system. For instance, I encountered considerable problems on a fresh install of Kubuntu 8.10 beta, which suffered from some particularly bad nvidia performance issues. On a well-functioning install, I rarely if ever encounter this bug on a day-to-day basis, even on a low-powered eee 1000. 

One other bug: If you escape out of Scale without choosing or closing (using the Scale Addon plugin) any windows or selecting the desktop, window re-minimization still will be pending. Reminimization is dependent upon some window being selected or closed before you exit Scale, or the desktop being selected; if you do none of these, reminimization will occur after Scale exits, when you click on an inactive window.

Finally, some Netbook Remix users may be unable to use this script out of the box. For these users, triggerring the script will often cause all windows to be immediately minimized. These users will need to uncomment the 'blackList' variable listed below. They may also need to 'sticky' a window (and preferrably make it reside under other windows) to achieve full functionality. Use of a screenlet such as ClockScreenlet can do the trick. See post #18 and subsequent posts for more.

---

### Post by x0x on 2008-11-09
doest work for me...

---

### Post by dillinjah on 2008-11-18
I just wanted to say thanks for the wonderful workaround. 

It was a breeze to setup, and it is fairly quick.

---

### Post by ctothej on 2008-12-06
Thanks for this. You can make things a bit faster for scale if you shorten the Minimize animation duration. Can't wait till this is fixed...

---

### Post by dariusdwtt on 2008-12-08
Styling!

Looks good with a beam up animation :D

---

### Post by projection on 2008-12-15
Thank you.

---

### Post by potomek on 2009-01-27
Any idea how to activate it via hot corner?

---

### Post by dyous87 on 2009-02-01
Well you can set it to hot corners using Brightside:

```
sudo apt-get install brightside
```Then configure it to one of the corners by running

```
brightside-properties
```This method however did not work very well for me. First of all I don't really like brightside very much. It takes a little long for it to actually activate the scale plugin and it seems a little buggy sometimes not even working. 

Also I really would like to be able to use this Scale Plugin hack by just brining the mouse to the bottom of the screen. Is there anyway or any application in Gnome that allows for this?

As a side note I would really like to thank the OP for this excellent hack. It works really well and would be absolutely perfect if only I could be able to access it using the bottom of the screen.

---

### Post by hamidoo on 2009-04-23
[SOLVED]
Thanks man for this awesome script!
It works for me.
I also found a very simple and fast way to activate the script on hot screen corners.
Open CompizConfig Settings Manager and search for plugin name "commands"
then add the command e.g ~/scale.py (~ is you home folder) ,then add Edge binding

---

### Post by easoukenka on 2009-09-02
worked great thank you very much!

---

### Post by stinkeye on 2009-09-02
> **hamidoo said:**
> [SOLVED]
Thanks man for this awesome script!
It works for me.
I also found a very simple and fast way to activate the script on hot screen corners.
Open CompizConfig Settings Manager and search for plugin name "commands"
then add the command e.g ~/scale.py (~ is you home folder) ,then add Edge binding

Thanks hamidoo that works.
Nice script greg t . Should be an otion in compiz.
I now have the top left corner for the scale plugin and the top right corner to run your script.

---

### Post by ashcroft3000 on 2009-09-04
Excellent work, Greg! Way to go!

Just like hamidoo and stinkeye I defined two hot corners: the left bottom for regular Scale and the right bottom for Scale with minimized windows. I was really amazed when I found out that repeated calls of your script - multiple pointer movements to the hot corner, that is - make a running Scale switch between these two behaviours! So the first move displays all windows, the second move hides minimized windows, the third one shows all windows again and so on...

I'm wondering whether it's possible to reverse the order of these two Scale "styles". This way we could spare a precious hot corner and also simplify the UI. So the first move / call should invoke regular Scale behaviour, the second should bring up all windows etc.

Can't be too hard, I guess! I tried to change this on my own, but unfortunately no hablo Python. Could anybody help out, please?

Thanks in advance, mates!

Cheerio
 Richard

---

### Post by krisofe on 2009-09-05
Just a thanks since 20090905 in Jaunty :-)

---

### Post by stinkeye on 2009-09-06
I just did an install of karmic alpha 5 and to get it working I also had to install python-wnck.```
sudo apt-get install python-wnck
```

---

### Post by Greg T. on 2009-09-07
I've posted a new version to provide the hot corner functionality requested in post #12. See the updated first post for instructions. (ashcroft3000, I think you'd be looking at using option 1.) 

I've also updated the instructions to note the upcoming need for python-wnck. 

Thanks for the feedback, everyone.

---

### Post by ashcroft3000 on 2009-09-08
Greg T, you - are - the MAN! Thanks a zillion!

Hey, I LOVE this community!

---

### Post by ngine13 on 2009-09-13
Thank you very much! :)

It works great!

I couldn't install python-wnck on jaunty, but as i said it rocks anyway.

pmousoul@acer5920g:~$ sudo apt-get install python-wnck
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-wnck



Thank you again! :)

---

### Post by raziv on 2009-10-05
A blessed initiative indeed! (thumbs up!)
I am too a user of scale, silently wishing for this option for a long time...
Now I'm using the karmic netbook beta, and... the script doesn't work for me :-( (not fair! not fair! - seems like everyone else is having so much fun with this script! :-))
When I run the script I see windows appear and then immediately get minimized again. The original scale plugin works fine, naturally for unminimized windows only...
Anyone got this working on a netbook version of ubuntu? I've started looking into it and any help would be welcome.

---

### Post by Greg T. on 2009-10-05
Hmmm... This may be an example of the bug I noted in the first post. Especially on slow computers, it can crop up. What netbook are you using? Have you tried to adjust the timer mentioned in the instructions?

---

### Post by raziv on 2009-10-05
I'm using an Acer Aspire One with the N280 Atom processor, Intel 945 graphics thingy. I must say it is surprisingly responsive, btw - I usually run it with loads of compiz plugins running about.
When I run the script the scaling is pretty quick, and the re-minimization is almost instantaneous. Cranking pluginDelay up to "infinity" (1000.0) doesn't help either.
Inserting primitive debug-prints into the script reveals that the delay issue never comes up. Almost always the only reminimized window is the "firstIneligibleWin")

The script correctly identifies the minimized windows and un-minimizes them. But when the scale plugin is activated they all get minimized.

Inserting various time.sleep lines within the script identified the culprit: the windows all get minimized when the first ineligible window is activated (line: "window_command(firstIneligibleWin, 'activate')"). Trying the second ineligible window had the same result: immediate minimization of all windows.

If I comment-out this activation command, the windows get minimized when gtk.main() is called...

Does this make any sense?
----
Just made another check: The windows get minimized even if I don't call the scale plugin at all! Either one of the commands (activate/gtk.main) causes all the windows to minimize!

Does _this_ make any sense?

SIDE NOTE:
I'm using the latest version of libwnck22 which gives the following warnings upon "import wnck":
** (.:9848): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (.:9848): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (.:9848): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'

downgrading to libwnck22=2.26.0-0ubuntu1 fixed these warnings, but the script behaved the same.

---

### Post by raziv on 2009-10-05
Got it! Ha Ha!:KS
My netbook system has these three "ineligible windows":
- Home
- Top Expanded Edge Panel
- Untitled window
I think the first one has to do with the netbook-launcher,
the 2nd one is self-explanatory,
and the 3rd, well, I suspect it is some kind of system process.
Anyway, letting the script activate any one of the first two results in a "show desktop" event, and all windows are minimized. However, activating the third, "Untitled window", leads to no such thing and the script works! It - Works! Yay! :)
So, I attach my modified (netbook) version.

---

### Post by Greg T. on 2009-10-06
Excellent detective work! I downloaded Netbook Remix last night and confirmed what you found. I'm sure it took some digging through the script to figure that out, and I appreciate the effort. It certainly saved me some time.

Your fix is potentially problematic, though. The issue with "Untitled window" is that it can be transient. For instance, on my netbook, it wasn't listed. However, I may have an alternative fix + workaround in the next day or two, when I can find the time.

---

### Post by raziv on 2009-10-06
I'm glad to hear I saved you some time - I'm sure the whole community will benefit from that :).
Regarding the "untitled window", indeed after re-login it wasn't there, causing the script not to work again, but then in a short time it reappeared and the script started running smoothly. 
Investigating the ineligible windows:
"Home" = netbook-launcher
"Top Expanded Edge Panel" = the top panel
The netbook-launcher "sits flat" on the desktop and focusing to it causes a minimization of all the windows (triggers a "show desktop" event, as can be identified by placing a "show desktop applet" in the panel and seeing it gets toggled), so I can understand the effect of activating it.
Regarding the top panel - I have no idea why activation of it causes a "show desktop" event.
And after a long investigation I found that:
"Untitled window" = compiz' "switcher-window" (that thing that pops up when you press alt-tab).
Well, ahem, this is not a very stable foundation for an app, to say the least... So a better workaround is called for...
My fix is not potentially problematic - it is _definitely_ problematic :P, as it relies on a side-effect of using compiz, which may not always be available...

---

### Post by Greg T. on 2009-10-07
Nasty bug. At first, I thought that "Home" and "Top Expanded Edge Panel" were simply ignoring the activation attempts, but instead they were being activated and were basically short-circuiting the script, as you pointed out. 

My workaround would be to create an application window at startup, placed permanently below all other windows, and made sticky. Sticky windows are among the non-tasklist "ineligibleWindows" that are subject to activation. For instance, the Screenlets application (sudo apt-get screenlets, if you don't have it) allows a clock to be placed on the desktop. It shows up in wmctrl -l as "ClockScreenlet.py." This screenlet includes options allowing it to be be placed underneath all other apps and made sticky. In practice, on the Netbook Remix it's effectively buried and invisible, but for a Screenlets daemon that appears in the system tray. It can be added to the list of startup applications as well, using this command:

```
python -u /usr/share/screenlets/Clock/ClockScreenlet.py
```

To go along with this workaround, I'll have a new version of the script posted soon. Rather than asking users to figure out and explicitly list the name of whatever application they've stickied, the script probably will include a list of blacklisted window names that can't be activated. This will leave the "good" non-tasklist window(s) as the only one(s) left that the script can activate. The blacklist will be commented out by default so that it doesn't interfere with users of other versions. (The "Top Expanded Edge Panel" works just fine with this script in vanilla Ubuntu, for instance.) 

Not perfect, but it should work.

---

### Post by Greg T. on 2009-10-09
New version posted with Karmic Netbook Remix fix.

---

### Post by raziv on 2009-10-10
Works like a charm! Blacklisting did the job! Thanks, Greg!

---

### Post by bademeister on 2009-12-02
Works great! I've been looking for this some time. A shame that compiz doesn't do it natively, kwin can do it.... 

Thanks for this workaround!!

Cheers
Paul

---

### Post by mlissner on 2009-12-10
Still works here. Good stuff.

---

### Post by eriro on 2010-02-12
Hey!
Is there any way to get this working in lucid netbook edition as well? Or should it actually work as well? I followed the instructions above but can't get it to unminimize my windows. 

Thanks in advance...

---

### Post by Greg T. on 2010-02-12
I haven't tried Lucid Remix yet, but I'll give it a shot in the next couple weeks, I imagine. Stay tuned.

---

### Post by Greg T. on 2010-03-17
Tried Lucid Remix alpha 3 tonight (in Virtualbox) and couldn't get 3D effects to work properly. Hopefully, it's a fixable bug and it'll iron itself out down the line.

Not really a fan of the netbook releases. Too restrictive, in my opinion.

---

### Post by raziv on 2010-03-28
I have upgraded to the lucid netbook beta, and the script at first made my netbook-launcher interface disappear, leaving me with an "ordinary" desktop. To fix this, I added 'x-nautilus-desktop' to "blackList" in the script. Now all's well again :D.

---

### Post by itisbasi on 2010-03-28
Tried it on lucid Desktop beta1 and there seems to be quite a few unmet dependencies to the python-gnome2extras package. Downloaded only the wctrl and xwit packages and ran the script and it works like a charm. Many thanks to Greg T.

---

### Post by matthewn on 2010-04-18
Wonderful script; just wanted to say thanks; wish I found this a long time ago!

---

### Post by keypox on 2010-05-22
does this still work?

---

### Post by Greg T. on 2010-05-22
Still works for me using Ubuntu 10.04.

---

### Post by sqren on 2010-05-25
Thank you!

---

### Post by apochry on 2010-06-25
Hey guys, 
I'm trying to make this work for me, but since I'm new by Ubuntu and Linux at all, so I have some difficulties. This what I get when I try to install the -extras and -wnck packeges:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gnome2-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-gtkspell python-gtkmozembed python-gksu2 python-gdl python-gda
  python-eggtrayicon
E: Package python-gnome2-extras has no installation candidate

```

Am I doing something wrong or the package is missing?
I'm using Ubuntu 10.04 LTS -  Lucid Lynx and have the ccsm installed and running right.
Any help will be appreciated. Thanks.

---

### Post by Greg T. on 2010-06-25
Hmmm.... python-gnome2-extras may no longer be a dependency. I just noticed that it's no longer on my system. A little research suggests it was removed when I updated to 10.4.

About a year ago, python-wnck was split out of python-gnome2-extras. Without it, python-gnome2-extras may no longer be needed. I've updated the instructions to remove it, as it no longer is available for download.

I know your message indicates that you also had trouble installing the -wnck package, but your error message was specific to python-gnome2-extras. Try the revised instructions and see if you have better fortune this time around.

---

### Post by apochry on 2010-06-26
Hey, Greg T.!

Worked perfectly this time. Unfortunately I have a slow CPU and it's not going very smoothly, but this is my issue.

Thank you for the great feature and the support!

---

### Post by david_katona on 2010-07-12
Thank you, Greg! It's a great script!

---

### Post by ehabh on 2010-07-29
Thanks cured me of osX envy :)

---

### Post by Dragonlaw on 2010-08-19
> **ehabh said:**
> thanks cured me of osx envy :)

yes same here! Thanks greg!

---

### Post by keypox on 2010-08-25
Nice fix, 

but couldnt we get something more eligant like in snow leopard, smaller boxes for minimized windows.

---

### Post by spoovy on 2010-09-02
This kind of works for me, but not usefully, I think there's a bug.

Example - I have three windows open, two maximized, one minimized.  I activate the script, and the three window previews all appear as expected.

But as soon as my cursor moves over one of the maximized window previews, the screen flashes and the minimized window preview disappears, leaving the other two side by side.  I can select one of these two as normal, but obviously not the third one, cos that's disappeared.

If however I carefully steer my cursor around the maximized window previews and move over a minimized window preview first, this behaviour does no occur; I can select the window preview normally, bringing up my previously minimized window.

---

### Post by guguma on 2010-09-26
Greg,

I just wanted to thank you for this great script. Assigned your script to a keyboard shortcut and it works wonderfully.

It works kinda slow but who cares, it is way faster than finding a specific window in a cramped up taskbar (or dock).

one of the best contributions I have ever seen, thanks again.

---

### Post by mrjoeyman on 2010-10-05
Thanks very much! So far works great. Very user friendly instructions, so easy even a cave man can do it.:)

---

### Post by jesus.iniesta on 2010-10-15
It works for me in Maverick when i run the script, but: there isn't any way to attach it to a HotCorner??

---

### Post by jesus.iniesta on 2010-10-15
Sorry for the double post, I have just found it in CCSM -> commands

PD: Thank you for such a great and useful work.

---

### Post by aninona on 2011-01-01
how can I use the hack without having ccsm installed? I use fluxbox. tnx

---

### Post by Greg T. on 2011-01-01
> **aninona said:**
> how can I use the hack without having ccsm installed? I use fluxbox. tnx

You can't. To use this, you have to be running Compiz, not Fluxbox.

From the Fluxbox [FAQ]("http://fluxbox-wiki.org/index.php?title=FAQ#Can_I_use_fluxbox_or_parts_of_it_with_XGL.2FCompiz.2FBeryl.3F"):

[INDENT]Fluxbox is a windowmanager, compiz and beryl are window managers (combined with a composite manager). So you can only replace fluxbox with one of them.... Fluxbox is not modular, so you can't use the fluxbox menu, toolbar, slit or anything else with compiz. You can read the eyecandy section for some nice effects with fluxbox or switch completely to compiz/beryl and miss all the great features fluxbox has.[/INDENT]

---

### Post by allenbina on 2011-01-15
if i have it set to a key (f9), it opens perfectly, but if I want to hit the key again to close all the windows, it doesn't exactly work.  any workaround?

---

### Post by allenbina on 2011-01-15
I think I answered my question 

 # ************************************************************************
    # Launch the Scale plugin of the Compiz window manager
    # ************************************************************************
    # Aside from ESCaping out, Scale will exit upon one of three actions:
    #    Selecting a tasklist window, closing the last tasklist window, or
    #    showing the desktop

Guess it can't be done.

---

### Post by matthewls on 2011-01-27
Thanks Greg. I've been looking for this for a while. Great work.
Matthew

---

### Post by gwbennett on 2011-03-05
Thanks! Loved scale, and had it set to bottom left edge activation but was annoyed it didn't include minimized windows. Used the "commands" plugin to create the binding to ~/.scale.py (made the file hidden) Works great.

---

### Post by jon4248 on 2011-04-22
Tested and working, for me anyways, in Natty Narwhal :) it really fits in well with the new unity interface, I set it to the bottom corner...just perfect...for me anyways. 

Anywho, Thanks Greg T. for the awesome script, and thanks hamidoo for the ccsm hotcorner setting.

---

### Post by jesuisbenjamin on 2011-04-23
Thanks! :) Good job and nice to read your script and learn!
The Compiz should probably learn from it too :P

---

### Post by vys on 2011-10-18
this is beautiful. the perfect answer.

---

### Post by User Abuser on 2011-10-20
this is awesome. that's how it should work it the first place :D
thank you very muchy! :KS

---

