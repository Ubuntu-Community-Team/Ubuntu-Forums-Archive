---
title: "Ubuntu 9.04 crashes constantly on my ThinkPad X61 Tablet, with no apparent cause"
date: 2009-05-23
forum: Hardware
---

### Post by Cherry Cotton on 2009-05-23
Ever since I upgraded to Ubuntu 9.04 “Jaunty Jackalope,” my ThinkPad X61 Tablet has been crashing constantly, generally at least once every day. I would really appreciate your help with this stubborn and seemingly irreproducible problem.

IMMEDIATE SYMPTOMS

When my system crashes, it goes down hard. Everything freezes up. The graphics are frozen in place. The mouse cursor will not move. If there is any sound playing, it will become stuck (the very last snippet will play over again, endlessly). If I try to SSH in from another machine, the operation will time out. There are no flashing LEDs (Caps Lock, etc.) that would indicate a kernel panic, and Alt+PrtSc will not work to shut the system down. The only option is to turn the machine off manually.

LOG FILES

The logs will show _nothing._ This is what is the most infuriating. Time and again, I’ve checked the logs and found nothing that isn’t completely unremarkable. In every case, bar none, the last message in each major log will be something both entirely innocuous and not matching up with the time of the crash, often by a difference of minutes. (I always know the precise time of the crash because I set my GNOME panel clock to show seconds, and it will freeze up along with everything else during the crash.) Most common is the Network Manager roaming messages that dominate my logs.

The _only_ evidence that something went wrong is _thoroughly_ bizarre. My X.org log—Xorg.0.log.old—will have a _different mimetype._ Instead of “text/x-log,” it will be “application/x-trash.” However, if I open it explicitly in a text editor, there is no problem, not even any binary junk in the file. It will be, once again, completely unremarkable, and reveal nothing about the cause of the crash. (Keep in mind that the mimetype change doesn’t happen until the failure itself. While running Ubuntu, my X.org log, Xorg.0.log, will be logging events just fine, and its mimetype will be the standard “text/x-log.”) (I should note that this problem could be unrelated; I haven’t checked to see if this happens when X.org exits “normally.” I suppose I should do that, now.)

THINGS I’VE TRIED

I’ve tried to isolate the problem. I’ve tried using the 2.6.30 RC5 kernel and the [X Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"), and the crashes will still happen. I’ve tried using [the old Intel graphics driver]("https://launchpad.net/~siretart/+archive/ppa"), compiled for Jaunty, with no luck. I’ve successfully changed my xorg.conf-based Wacom configuration to a proper hotplugging-based one, and though it brings me peace of mind (and xorg.conf is now at its default, nearly-empty state) it hasn’t solved the crashing.

I’ve also tried using Apport to collect crash reports, with no luck. (Obviously, I imagine it’s hard for Apport to create a crash report for a crash that brings down the entire system, but it was worth a try.)

WHAT DO I DO?

This has been incredibly trying for me! I don’t know where the problem is, so I don’t know where to file a bug. All logs seem to be clean of evidence of something going wrong, so I don’t know what avenues to go down. The system seems blissfully unaware of its own problem.

I’ve Googled my brains out and haven’t found anything. I’m not sure this is a common problem, even with my particular model.

It’s heartbreaking for me because I do art, and I’ve been working on digital painting projects of the kind where saving can take a full minute or more, so saving constantly is never an option for me. So, I’m determined to solve this problem, but I’ve run out of options on my own.

I’ve attached the output of lspci -vvnn to this post. I don’t have an Xorg.0.log.old that pertains to this problem, because I had to restart X just now due to a different problem (argh), but I’ll post one once I have this problem again (won’t be long, I imagine.)

Any advice, help, thoughts, or anything else relevant to this problem would be greatly appreciated! I think I’m at least fairly Linux-literate, so I should be able to obtain any other information on my system that you might request. Thank you!

---

### Post by TheUsualSuspect on 2009-05-23
I have the same problem on a Acer Travelmate 6292 and after yet another total crash last night I've been searching for some fix to the problem. I can't relate it to anything specific - it usually locks up when using OpenOffice.org, but last night it crashed while running DSL in VirtualBox. When Ubuntu locks up the system is totally unresponsive and I have to do a hard shut down by pushing the power button - and of course lose any unsaved data in the process. I suspect my integrated Intel graphics card has something to do with it, but I'm far from sure. However, Ubuntu is running smoothly on my Asus eee pc 901 (the UNR flavor).

I'm using my Travelmate and OpenOffice.org in order to write my master's thesis and quite frankly I can't take anymore of this.. I can't afford to lose my work whenever Ubuntu decides to crash, so I'm afraid the only remedy right now is to back up all my data and try a distro that can provide a more stable environment.

---

### Post by Favux on 2009-05-23
Hi Cherry Cotton,

It sounds like your aware of the Intel video issues with Jaunty and have dealt with it.  You're also aware of the xorg-xserver bug which makes using xorg.conf a bad idea.

So have you ruled out a temperature problem?  I've seen several threads on high temps with Jaunty.  If your temp does turn out to be up you could use top to find out if a process is responsible.

Maybe the video thing is a red herring and you have a RAM problem.  That's usually what causes the symptoms you're describing.  Have you tested it?

---

### Post by Cherry Cotton on 2009-05-23
Thanks.

Okay, I’ve tried a few things. First, the memtest comes back with a clean bill of health. I left it going overnight, and attached is what it looked like when I woke up.

Second, for the memtest, I shut the system off normally, and when I brought it up again I looked at the old X.org log. Sadly, it seems like the weird mimetype change is “normal” behavior; it does that even when you shut the system off without problems. I’ve attached the log, just in case it’s relevant.

Temperature might be the issue... the system runs hot enough often enough that I keep a temperature monitor in my GNOME panel. The difficulty, though, is that over time I’ve had this crash in all kinds of circumstances... sometimes I have my computer in laptop mode, sometimes I have it in slate mode rotated right, sometimes I have it in slate mode rotated left, and sometimes it’s just sitting on my wooden nightstand during the night, and in each such case I’ve had this crash more than once. How I’m using the computer determines, generally, how much temperature becomes a problem... it’s typically lowest when it’s not in use, then when it’s being used in laptop mode, then when it’s being used in slate mode (when I’m typically holding it close to myself), and finally it runs hottest when I have it in slate mode rotated left, when the hot fan is pointing toward me (aaaagh!). (When the screen is rotated left, the buttons are at left, so this is the setting I use for doing art. Likewise, when the machine is at right, the buttons are at right, so I use that mode for reading. I’ve rigged the radio switch to change between rotation modes; I’ve spent way too much time customizing my PC like this...)

Anyway, if temperature is the issue, what would be a good way to monitor my system’s temperature over time, to try and diagnose the issue? (Also, from now on, I’ll be sure to write down the temperature at crash time, since, after all, it’s on my GNOME panel.)

Thanks, y’all. More thoughts on this issue are quite welcome!

(It’s also good—and a little sad—to know that this issue is not specific to my ThinkPad machine. I wonder if we should contact some hardware-type experts...)

(Oh! I should note one more thing. I did have crashing problems back in 8.10, when I first got this machine. However, those were garden-variety kernel panics, flashing LEDs and everything. I was happy to upgrade, hoping that the new kernel wouldn’t have this problem. As far as I can tell, it doesn’t; I just have new problems. Anyway, I don’t think I ever figured out what was behind those kernel panics...)

---

### Post by Cherry Cotton on 2009-05-23
I just noticed that my system, while sitting on the table doing nothing, was running really hot (80°C) and [Tracker was getting its usual loop of errors.]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205") (I&#8217;ve been getting those Tracker errors in the past few days. That&#8217;s much less time, though, than these crashes have been happening, as they began when I upgraded back when Jaunty was a release candidate.) So, I shut down Tracker in the system monitor and the temperature went down to normal... hmm. Anyway, I&#8217;ll turn off Tracker and see if that makes a difference over time.

---

### Post by Favux on 2009-05-23
Hi Cherry Cotton,

Looks like you may have found the problem.  And of course make sure the vents and fan are clean.  Maybe blowing some canned air through things when powered down.

---

### Post by Cherry Cotton on 2009-05-23
No dice :(

It crashed just now, while I was reading something. Tracker was turned off, and the temperature was at a mild 53°C.

I really don’t know what to do, now...

---

### Post by Cherry Cotton on 2009-05-23
There’s [a thread here about these weird crashes]("http://ubuntuforums.org/showthread.php?t=1137378"). I hope we can get this problem solved, soon....

---

### Post by arupgowda on 2009-06-03
I have the same problem. Ibex worked just fine. After upgrading to Jaunty, I have had the same issues as Cotton has. I have a HP DV6000 laptop, with an Nvidia 7200 graphics card. 
I am sick of this issue and am planning to downgrade to Hardy Heron.

---

### Post by spazerujemy on 2009-11-09
Hello Cotton,

i hope someone still follows this old thread. I wonder if you were ever able to resolve the matter?

Because i am experiencing the symtoms Cotton described so excellently. I am using a T42 thinkpad and Karmic Koala

greetings

jan

---

### Post by Cherry Cotton on 2009-11-10
For me, the problem stopped when I upgraded from Jaunty to Karmic (though I did so back during the alpha, I was so desperate to solve the problem). I’m sorry you got the problem with Karmic! Ugh...

The only time I remember someone saying they fixed it was [this post]("http://ubuntuforums.org/showpost.php?p=8056047&postcount=50") on that other thread, whose author said the problem went away when he installed a specific custom kernel package. I don’t know if that would work in all cases, though.

---

### Post by spazerujemy on 2009-11-10
Thanks, C. Cotton, I will dig into the solution described if/when i experience the next crash. I still hope that this will go away somehow...

jan

---

