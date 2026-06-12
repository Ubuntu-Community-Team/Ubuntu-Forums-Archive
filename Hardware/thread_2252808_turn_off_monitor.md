---
title: "turn off monitor"
date: 2014-11-14
forum: Hardware
---

### Post by il lupo on 2014-11-14
Hello, All--

My goal is to turn off my monitor while practicing.  i'm preparing for a recital and practice at home with a MIDI keyboard that controls Qsampler.  The problem is that, even though i have a quad-core machine with eight gigs of RAM running at 1.8ghz, my CPU still manages to get tasked.  This makes some bad slips (xruns) in the audio stream.  i usually get them when i'm running my screensaver--which i need to do, as i can spend sometimes up to an hour on a single passage.

i've done a few things to manage my resources, such as turn off pulseaudio.  That way, i'm just using JACK.  Nonetheless, i still get these xruns--but only when the screensaver is running.  i've seen that take up us much as 50% of my CPU.  The alternative is that the screensaver so taxes xorg that xorg takes up to 50% of my CPU.

My thought, then, is to turn off the monitor.  Some earlier searching taught me this command:  xset dpsm force off.  It works fine, but after a few seconds, i'm bounced back to my login screen.  Also, i came across [this thread]("http://ubuntuforums.org/showthread.php?t=1317747&page=3&p=9433671#post9433671") earlier, today.  It gave me the same problem.

If anybody has some experience with this, i'd greatly appreciate the help.

Thank you, and take care.
il lupo

---

### Post by buzzingrobot on 2014-11-15
You could actually turn off the monitor, but that would not stop the screensaver runnning if it's enabled.

You might create another user account just for practice sessions, in which the screensaver is disabled.  When it's time for practice, switch to that user.

You could, also, track down the screensaver process and kill it, but that's a bit brute force.

Screensavers do consume reaources, especially if they frequently load and unloaded images. I don't use one since I'm never around to see it and it's been years since screens needed any 'saving'.

---

### Post by houstonbofh on 2014-11-16
You could chang your screensaver to just "Blank Screen" which uses no resources.

---

### Post by pqwoerituytrueiwoq on 2014-11-16
[http://pastebin.com/SQhTN6pR](http://pastebin.com/SQhTN6pR)
that is a script that you can use the toggle the screensaver
use the -t option to toggle it
i use this for fullscreen html5 videos

---

### Post by il lupo on 2014-11-19
Hi, Everybody--

Thanks for the replies.  [COLOR=#000000]pqwoerituytrueiwoq[/COLOR], i'm not exactly sure what the script does.  i have experience with the command line, but i'm not a programmer.  However, i believe that your solution, houstonbofh, will work.  i will use buzzingrobot's suggestion and try it with a separate user account just for practicing.  i like the way my screensaver is set up, for now.

In any event, i'll give it another whirl, tomorrow.  i haven't had time to practice over the past two days, as i've run into another problem.  That, however, is another post....

Thanks, again, Everybody!

---

### Post by il lupo on 2014-11-20
After a steady two hours of practicing using your solution, houstonbofh, my system ran my setup with only 8 xruns.  Plugging things in and out of JACK, that's to be expected.  i didn't even need to use another account, either, buzzingrobot.  i used Settings to switch to blank screen, and my previous settings were remembered when i switched back.  The second account still might be a good idea, though, if ever i need to run things in such a way as to seriously manage resources.  But i won't be doing anything that big for a while.  Thanks, again, everybody!

---

