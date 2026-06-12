---
title: "Major problem after auto update!"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by archeryguru2000 on 2009-07-14
Hello all.  I recently received an update available message (about 2-3 hours ago) and accepted all updates (about 6 or 8... but I do not remember what they were 8-[ ).  Anyway, after updating I was prompted with a computer restart icon (which I thought was weird because I don't remember any of them including kernel dependencies, but I could've overlooked something).  I did not immediately restart because I was in the middle of downloading something... a large file.

However, after about an hour, I restarted my machine.  Now, I am having some major issues running just about any application.  When I open my CLI the terminal "box" shows up on my desktop, but nothing inside shows up... I'm not able to type anything in it, I cannot open firefox (I typing this from my Vista part. :( ), among many other apps.  I CAN however switch to a CLI through <ctrl>+<alt>+f1.  I tried executing
```
$: top
```
to see if something was eating my cpu/ram but nothing appeared to be running.  Can somebody suggest somewhere to search to find a remedy?

I also attempted to log into an older kernel... but the exact same problem exists there as well.  I'm totally stumped here.  Any help will be greatly appreciated.

One more thing to add... my conky startup script must be executing properly because it shows up on my desktop and shows that I'm connected to the internet, and continues to update.  Very odd!

Thanks,
~~archery~~

---

### Post by archeryguru2000 on 2009-07-14
Ok!  Booted back into Ubuntu.  I'm actually able to open/use Opera.  Yeeaaahh!  However, I still cannot use CLI, cannot even open nautilus, firefox, deluge, gnome-screenshot, gedit, (still checking other apps)...  I've found out that Opera and Synaptic still work.

This is extremely odd for me.  Does anybody have ANY suggestions?

~~archery~~

---

### Post by archeryguru2000 on 2009-07-14
Another bit of information that may be useful.  I tried opening Deluge and received this error/warning popup.

```

boost::filesystem::create_directory

```

I have never seen this error message before, and I wouldn't have a clue how to interpret it.  By the way it was a popup message, not a terminal message... fyi.

~~archery~~

---

### Post by archeryguru2000 on 2009-07-14
One more bit of information.  I don't know if this will help anybody (or if anybody is even reading this), but on my conky display I have a CPU speed reading which seems to bounce back and forth between 0.80 GHz and 2.00 GHz.  I don't necessarily remember this number flucuating... but I could be mistaken.

Also, if I attempt to use any of the aforementioned apps that do not appear to load/open, my internet connection is disrupted and everything seems to crash... except for conky, awn, and my other virtual terminals.  Even when this happens, 'top' never displays anything over ~2% CPU/RAM usage (which is usually top itself).

Sorry for the mass number of posts, but I'm kinda desperate here.  Any help appreciated.

~~archery~~

---

### Post by alexcckll on 2009-07-14
Did you cold-boot?  Just that with kernel updates it might help.

What hardware are you running?

---

### Post by archeryguru2000 on 2009-07-14
> **alexcckll said:**
> Did you cold-boot?  Just that with kernel updates it might help.

What hardware are you running?

"cold boot"?  Is that the same as hard (re-)boot?  If that's the case, no I have not.  Should I?  I'm not sure if that would help any.  Would that somehow erase some error message?

Anyway, my machine is an HP Pavillion dv6xxx with Atheros wifi, ~3G Ram, 120G hard-drive (dual boot Vist), AMD Turion 64x2 (however, I'm running a 32bit install), nVidia GeForce 7150 video card, ... , not sure what else to mention.

I'm currently typing this while booted into Vista... PLEASE HELP ME ESCAPE MY WINDOWS PARTITION!  ;)

~~archery~~

---

### Post by unlimitedz on 2009-07-14
Maybe your ubuntu partition ran out of space?

---

### Post by archeryguru2000 on 2009-07-14
Bump.  Somebody, please!  There has to be somebody out there that has an idea of what I could check.  Some error message, update log, CLI command to check something/somewhere, ... , somebody.

~~archery~~

---

### Post by archeryguru2000 on 2009-07-14
> **unlimitedz said:**
> Maybe your ubuntu partition ran out of space?

No sir, I have ~15G of free space.  I'm able to open up a nautilus window now.  However, I cannot manuever around very well.  For example, if I press the backspace button my window freezes... no matter what folder I'm in!  I still cannot get firefox or CLI to open/work.  I'm at a total loss here.

Thanks for the suggestion though.

~~archery~~

---

### Post by mikey.duhhh on 2009-07-14
> **archeryguru2000 said:**
> "cold boot"?  Is that the same as hard (re-)boot?  If that's the case, no I have not.  Should I?  I'm not sure if that would help any.  Would that somehow erase some error message?


Shut your system down.  Wait a minute or get a cup of coffee, then press the on button again.

Also try booting into recovery mode by selecting it in grub.  Then try typing startx or startX (don't remember the exact command).  And see if things work.  And one more thing, try booting into an older kernel and see if that helps.

---

### Post by irv on 2009-07-14
Have you tried running in recovery mode and doing a fix on system files?

---

### Post by archeryguru2000 on 2009-07-14
Thank you guys very much for your replies.  Actually, I just did shut down the computer and went to get the mail (drove to Post Office).  Also, I have tried Recovery Mode, but wasn't sure what (or where) to check for errors.  I've honestly never come across anything like this before.  One thing I've never checked yet is the suggestion by mikey.duhhh.  I'll reboot and then, through my virt-term try startx.  Maybe this will give some sort of error message.  I'll post back in a few.

Thanks again for the suggestions,
~~archery~~

---

### Post by archeryguru2000 on 2009-07-14
No such luck.  Tried $: startx, but it only complained about it already running (under window #7, ie <ctrl>+<alt>+f7).

I'm not sure but I think it might have something to do with my Gnome desktop.  If I press <alt>+f2 (which is how I run most apps), my run command window opens normally.  When I type (within said window) options begin appear, etc.  However, if I try to close that window (ie pressing Cancel, or clicking the upper close button, or by pressing <esc>) or even pressing enter to accept an application/command, the window hangs and darkens but nothing else happens.  After that all heck breaks loose.  If any other windows are open they too freeze.

Also, when I attempt to open gnome-terminal (my default CLI), the window itself appears but no text (ie user@machine-name$:_ ).  This happens whether or not I've attempted opening anything else.

I am, however, able to open a virtual terminal (<crtl>+<alt>+f1, etc.) and issue commands without a hitch. :-k

I also cannot take any screenshots to "show" what I'm talking about, which is driving me nuts because I'm not sure if I'm even describing this accurately.

Anyway, let me know if anybody has a suggestion about wherelse I might check.

~~archery~~

---

### Post by konnorrigby on 2009-07-14
I've never herd of this happening, but mabey if the partion is ran out of space try booting from the live cd/dvd and using G-Parted.
 
just my thought, hope i helped.

---

### Post by archeryguru2000 on 2009-07-14
> **konnorrigby said:**
> I've never herd of this happening, but mabey if the partion is ran out of space try booting from the live cd/dvd and using G-Parted.
 
just my thought, hope i helped.

Sorry, thought of that too.  I have ~15G of free space still available.

I tried looking up some ownerships as well; ~/.gnome, ~/.nautilus, ~/.mozilla, even tried ~/.*.  The only things that came up with a root ownership were ~/.. and ~/.dbus.  I'm not sure what either of those two are, but I didn't change anything either way.

But thanks anyway, I appreciate you taking the time to respond.
~~archery~~

---

### Post by irv on 2009-07-14
When you did the startx did you reboot and at the grub menu chose recovery mode and then goto a command prompt and do the startx from there? If not you will get errors because if you try to run it while x is running already this will happen.
When you try to run it from recovery command prompt, you might get error that will tell you what is wrong.

---

### Post by archeryguru2000 on 2009-07-14
> **irv said:**
> When you did the startx did you reboot and at the grub menu chose recovery mode and then goto a command prompt and do the startx from there? If not you will get errors because if you try to run it while x is running already this will happen.
When you try to run it from recovery command prompt, you might get error that will tell you what is wrong.

Yeah!  ;)  I'm an idiot!  I ran the startx command from a virtual terminal, not the recovery root shell.  I did however do just that this time.  And I did recieve an error message when the GUI started... but there was no discernable message within the box.  The title bar read "Error!", but I was unable to view anything within the popup box.  I was also unable to close that box.  Clicking on the upper 'x' only caused the box to shade to grey and then freeze.

I was unable to read any applicable messages within the shell (those lines flew by WAY too fast).  I know there's a way to direct (pipe, possibly) the output to a different location (text file, log file, 'less', something) but I do not remember how.

Thanks again for the assistance.
~~archery~~

---

### Post by irv on 2009-07-15
You might be to the point where I was last week. I did a update on my server, and during the update something happen to my hard drive. I knew I had a flaky driver I was using for my home directory, and it crashed and when I went to reboot, it could not find my home. See my thread about this and look at post #5. [http://ubuntuforums.org/showthread.php?t=1207960]("http://ubuntuforums.org/showthread.php?t=1207960"). This fixed my problems, but after trying everything I knew to try, I had no other choice. I hope you have a backup of your files.
After I got everything installed and working I did a complete backup of you system so if anything happens again I can just load and restore and be back running in one day.
I know this is not what you want to hear, but if anyone know another way let them post in here.

---

### Post by archeryguru2000 on 2009-07-15
Irv, I'm not quite sure that this is a similar problem.  I am able to access all of my files... I'm just not able to (properly) excecute all of my apps.  I just did an update (which included a newer kernel), rebooted and tried to open gnome-terminal... and it worked! \\:D/ I was very excited!  So then I pressed <alt>+f2 (my default 'run' for apps) and after typing nautilus and pressing enter... the %#@$ window froze! #-o I tried gnome-terminal again... but this time only the frame showed up with nothing inside of it.

Maybe there is some nautilus dependency that is corupt/damaged (or even missing) that I'm unaware of.  I may just try to re-install a bunch of programs (including nautilus) to try to narrow this down some.  Thanks again for the ideas however.

~~archery~~

---

### Post by irv on 2009-07-15
> **archeryguru2000 said:**
> Irv, I'm not quite sure that this is a similar problem.  I am able to access all of my files... I'm just not able to (properly) excecute all of my apps.  I just did an update (which included a newer kernel), rebooted and tried to open gnome-terminal... and it worked! \\:D/ I was very excited!  So then I pressed <alt>+f2 (my default 'run' for apps) and after typing nautilus and pressing enter... the %#@$ window froze! #-o I tried gnome-terminal again... but this time only the frame showed up with nothing inside of it.

Maybe there is some nautilus dependency that is corupt/damaged (or even missing) that I'm unaware of.  I may just try to re-install a bunch of programs (including nautilus) to try to narrow this down some.  Thanks again for the ideas however.

~~archery~~
That's a good place to start by re-installing the broken apps. I would of suggest doing this but I thought things were worst then that. I hope this fixes the problems for you.

---

### Post by archeryguru2000 on 2009-07-15
As I've started checking boxes (through Synaptic)  I've noticed that zero other boxes are being checked (dependencies).  I'm not sure if this is acutally going to get me anywhere if it is some obscure library file that is corupt.  But either way, I'm going to give it a shot.

I'll keep you posted on my progress.

~~archery~~

---

### Post by archeryguru2000 on 2009-07-15
One more thing to note.  Upon shutdown/reboot, I've noticed a [COLOR="Red"]**critical**[/COLOR] message that shows up.  It states something (goes by awfully quick) along the lines of:
```

CRITICAL: gdm_connection_close: assertion `conn != NULL' failed

```

Maybe this could help somebody identify a problem.

~~archery~~

---

### Post by archeryguru2000 on 2009-07-15
Ok, I've tried reinstalling the apps (at least the ones I'm aware of) that are not executing properly... no difference, even after reboot.  

I've also tried an approach that I found on a Gentoo bug report site.  It stated to remove the files in ~/.nautilus and ~/.metacity/sessions.  That had zero effect as well.

I tried searching some of the log files (/var/log/xxx), but couldn't locate anything unusual (absolutely no /var/log/crash files).

I'm starting to run out of options here.  I really really don't want to reinstall the OS.  That is simply not a fix.  I need to find out what the problem is.

Does anybody know of ANYWHERE else I can check.  Again, my problem(s) is applications (such as gnome-terminal, <alt>+f2, nautilus, firefox, panel, ...) will not open and/or execute.  I CAN run opera, deluge, and synaptic.

Please, any help is GREATLY appreciated,
~~archery~~

---

### Post by irv on 2009-07-15
> **archeryguru2000 said:**
> Ok, I've tried reinstalling the apps (at least the ones I'm aware of) that are not executing properly... no difference, even after reboot.  

I've also tried an approach that I found on a Gentoo bug report site.  It stated to remove the files in ~/.nautilus and ~/.metacity/sessions.  That had zero effect as well.

I tried searching some of the log files (/var/log/xxx), but couldn't locate anything unusual (absolutely no /var/log/crash files).

I'm starting to run out of options here.  I really really don't want to reinstall the OS.  That is simply not a fix.  I need to find out what the problem is.

Does anybody know of ANYWHERE else I can check.  Again, my problem(s) is applications (such as gnome-terminal, <alt>+f2, nautilus, firefox, panel, ...) will not open and/or execute.  I CAN run opera, deluge, and synaptic.

Please, any help is GREATLY appreciated,
~~archery~~

I know you said you tried re-installing, but did you try completely removing them and then installing from a fresh install. I would completely remove them, reboot, and then re-install and see if that would fix the broken apps. If that doesn't work and no one has an answer, then you must do what you have to do.

---

### Post by archeryguru2000 on 2009-07-15
Uh-oh!  I think this problem is getting worse.  Now I cannot get out of "Safe Graphics Mode".  I'm about done here.  If this problem isn't solved by the end of today... I'm trashing this partition!

---

