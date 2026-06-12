---
title: "Scheduled tasks (cron gui)"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by new_tolinux on 2009-11-02
Hello,

I did an upgrade from 9.04 to 9.10 and after some small problems (where Google was very helpful ;)) I'm only stuck at one point.

How do I open the "Scheduled tasks" gui?
At [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) I read this:
> **Note:** In Karmic(9.10), you have to enable X ACL for localhost to connect to for GUI applications to work. Only thing is: I haven't got the slightest clue what that is.
I tried to enter this in the terminal:
```
~$ xhost +local:
```and
```
~$ xhost +localhost
```But it still didn't work.

At last I tried to start "gnome-schedule" from the terminal, with these results:
```
/usr/share/gnome-schedule/mainWindow.py:158: DeprecationWarning: Use the new widget gtk.Tooltip
  tip = gtk.Tooltips ()
/usr/share/gnome-schedule/mainWindow.py:159: DeprecationWarning: Use the new widget gtk.Tooltip
  tip.enable ()
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 304, in schedule_reload
    data = self.crontab.read ()
  File "/usr/share/gnome-schedule/crontab.py", line 438, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/crontab.py", line 604, in parse
    success, ver, title, desc, output, display, command_d = self.get_job_data (job_id)
  File "/usr/share/gnome-schedule/crontab.py", line 690, in get_job_data
    return True, ver, title, desc, output, display, command_d
UnboundLocalError: local variable 'display' referenced before assignment 
```Can someone help me out?
Ofcourse I know that it can be done through "crontab -e", but I liked the gui.

---

### Post by Lars Noodén on 2009-11-02
1) Are you trying find a gui to set cron to run a program at a specific time?

2) Or are you trying to run a gui program at a scheduled time via cron?

3) Or do you want a pop-up reminder?


If #1, then look at kcron or gnome-schedule.

If #2, please give more details about the goal.

If #3, then look for something like kalarm.

---

### Post by new_tolinux on 2009-11-02
> **Lars Noodén said:**
> 1) Are you trying find a gui to set cron to run a program at a specific time?

2) Or are you trying to run a gui program at a scheduled time via cron?

3) Or do you want a pop-up reminder?


If #1, then look at kcron or gnome-schedule.

If #2, please give more details about the goal.

If #3, then look for something like kalarm.
#1
Tried gnome-schedule and did quote the results in the start-post. No gui started.
kcron seems to be for Kubuntu, not for gnome?

#2
I have soms scripts (.sh) that need to run at a certain time. Each script on another time, but all repeatedly every hour/day/week (depending on the script).

In the past (Ubuntu 9.04) I used the gui Scheduled tasks (add/remove programs). In 9.10 it just does not start at all.
Like I said above, another (terminal) option is "crontab -e", but I liked the gui. I'm just not good when it comes to remember what-goes-where in the crontab and the gui edited the crontab but had named fields like "hour", "minute", "seconds", "day", and so on.

#3 not at all. Ubuntu is primarily used as a webserver for testing purposes. Although there are some other programs that run there, it is not the machine I normally work at.

---

### Post by Lars Noodén on 2009-11-03
> **new_tolinux said:**
> #1
Tried gnome-schedule and did quote the results in the start-post. No gui started.
kcron seems to be for Kubuntu, not for gnome?


kcron is for ubuntu, kubuntu, xubuntu, edubuntu, debian, gnewsense, red hat, centos, fedora, yellowdog, slackware, opensolaris, netbsd, and so on ...

> **new_tolinux said:**
> #1
#2
I have soms scripts (.sh) that need to run at a certain time. Each script on another time, but all repeatedly every hour/day/week (depending on the script).


Ok.  Just checking.  The scripts themselves do not cause any GUI action. 
When you run crontab for the first time on ubuntu, it  asks about which editor you want.  Nano is the easiest, but the line wrapping can be a problem.  

> **new_tolinux said:**
> #1
In the past (Ubuntu 9.04) **I used the gui Scheduled tasks (add/remove programs). In 9.10 it just does not start at all.**
Like I said above, another (terminal) option is "crontab -e", but I liked the gui. I'm just not good when it comes to remember what-goes-where in the crontab and the gui edited the crontab but had named fields like "hour", "minute", "seconds", "day", and so on....


There's the real problem.  That's the kind of thing that warrants a bug report if we can't figure it out here.

When you installed 9.04, did you install X (xorg) or a gui like gnome?
If so, when you installed 9.10, did you leave that off?
If not, then how are you connecting to the server in question, with the -X or without?

[INDENT][FONT="Courier New"]ssh **-X** xx.yy.zz.aa[/FONT][/INDENT]

---

### Post by new_tolinux on 2009-11-03
> **Lars Noodén said:**
> kcron is for ubuntu, kubuntu, xubuntu, edubuntu, debian, gnewsense, red hat, centos, fedora, yellowdog, slackware, opensolaris, netbsd, and so on ...
Ok. I didn't know that, but was thinking that programs with a K were for the KDE-desktop-enviroment (which is not present).
> **Lars Noodén said:**
>  Ok.  Just checking.  The scripts themselves do not cause any GUI action. 
When you run crontab for the first time on ubuntu, it  asks about which editor you want.  Nano is the easiest, but the line wrapping can be a problem.  
Before the upgrade (in 9.04) I started "Scheduled tasks" to edit the tasks. I didn't know for sure what would happen during the upgrade, so I left all the times equal, only added that they run only in Februari (I figured out that the upgrade should have finished by then and I knew that Januari=1, Februari=2, and so on. Because I had a script at x.01 Januari was not an option).
After the upgrade I had to edit them back. Because "Scheduled tasks" didn't work, I used "crontab -e" with Nano. Worked perfectly, because I could locate the "2" between the other numbers and stars.
I didn't see any action on screen before. Besides that all scripts have >/dev/null added. All scripts match the example below, although times, /path/to/script.sh and JOB_ID are different. That should be no problem, beside 1 script that can not produce output before next week all scripts work fine in 9.10 (as far as I can see, every script does produce the expected output at the expected time). The script I can not test, was working perfectly in 9.04 also, and except of editing the time no scripts or tasks were edited since then.
Example: 1 * * * * sh /path/to/script.sh >/dev/null 2>&1#JOB_ID_1
> **Lars Noodén said:**
>  There's the real problem.  That's the kind of thing that warrants a bug report if we can't figure it out here.

When you installed 9.04, did you install X (xorg) or a gui like gnome?
If so, when you installed 9.10, did you leave that off?
If not, then how are you connecting to the server in question, with the -X or without
Maybe it's my bad, but it is also running Gnome. The "server" is in fact a notebook, and used as a notebook when I'm not at home.
I didn't connect to the machine from the network or the internet.
Gnome was installed in 9.04 and the upgrade was done with an Alternate x86 CD (internet connection present) from Gnome. Gnome is also present (and started) in 9.10
9.04 was also (fresh/clean) installed using an Alternate x86 CD (internet connection present).

By the way. I have already tried to reinstall "Scheduled tasks" by marking it for reinstallation in Synaptics because maybe something did go wrong during installation. Didn't change anything, still won't start.

---

### Post by Lars Noodén on 2009-11-05
> **new_tolinux said:**
> ... The "server" is in fact a notebook, and used as a notebook when I'm not at home. I didn't connect to the machine from the network or the internet.
Gnome was installed in 9.04 and the upgrade was done with an Alternate x86 CD (internet connection present) from Gnome. Gnome is also present (and started) in 9.10
9.04 was also (fresh/clean) installed using an Alternate x86 CD (internet connection present).


Ok.  That clears up a lot.  It also makes, in some ways, easier for you to find your way around.  Anything you can run while sitting at the keyboard, can also be run remotely via [SSH](http://manpages.ubuntu.com/manpages/karmic/en/man1/ssh.1.html) using the '-X' option, that's a capital X.

You can test remote access with some known-good applications like firefox.

To help with th diagnostic of the cronjob, copy the line and comment out the copy by putting a # as the first character on the left.

Then on the uncommented line take out the redirects, e.g.
this
[INDENT][FONT="Courier New"]sh /path/to/script.sh >/dev/null 2>&1#JOB_ID_1[/FONT][/INDENT]

becomes

[INDENT][FONT="Courier New"]sh /path/to/script.sh[/FONT][/INDENT]

then any output from the script will be sent to the local mail spool

alternately you can put it in a place where you can get it as a log

[INDENT][FONT="Courier New"]sh /path/to/script.sh > /tmp/script.log 2>&1 [/FONT][/INDENT]

The error message might help.  

Were you able to successfully re-install kcron or gnome-schedule and use it while sitting at the keyboard of the 'server' ?

---

### Post by new_tolinux on 2009-11-05
> **Lars Noodén said:**
> Ok.  That clears up a lot.  It also makes, in some ways, easier for you to find your way around.  Anything you can run while sitting at the keyboard, can also be run remotely via [SSH]("http://manpages.ubuntu.com/manpages/karmic/en/man1/ssh.1.html") using the '-X' option, that's a capital X.
You can test remote access with some known-good applications like firefox.
I sometimes use putty to log on remotely (text-only), but that's only if I'm lazy, because the machine is in fact almost within reach (7 foot/2 metres).
> **Lars Noodén said:**
> To help with th diagnostic of the cronjob, copy the line and comment out the copy by putting a # as the first character on the left.
The tasks themselves run fine. No problem there, most of them do something which later is put into a mysql-database through a php-script that is called from the sh-script. Output there is as expected, at the right time. I can use "crontab -e" and select nano to edit the cron jobs without any error.
> **Lars Noodén said:**
> Were you able to successfully re-install kcron or gnome-schedule and use it while sitting at the keyboard of the 'server' ?
I did try to reinstall the "Scheduled tasks" from the add/remove programs-section, without any change. It still won't start and when I start "gnome-schedule" (without quotes) from the terminal I still get the error-message, as I put in the first message.
I also tried installing kcron, but KDE is not installed. To install kcron I have to install about the complete KDE-enviroment, so I cancelled that one.

The problem is not re-scheduling tasks, or creating new scheduled tasks, the only problem is that the gui (gnome-schedule) is not working.
Not that big of a problem, I can do without the gnome-gui for editing tasks. It only would be more simple if the gui works. * * * 1 * sh path/to/script.sh in Nano is just not as easy as a gui that has a field called "minute", "second", "hour", "day" etc.

---

### Post by Lars Noodén on 2009-11-05
I missed the exact details how you are launching gnome-schedule.  If you are sitting physically at the machine, do you use gksudo or kdesudo?

If you are sitting at the machine and using the GUI there, then 

If you connect remotely, using 'ssh -X', you have to have an X server running and available on the client machine.  Linux, Solaris, the BSDs all do that by default.  OS X has it on the install disk, but you have to launch it first and then use that to log in via ssh.

---

### Post by Lars Noodén on 2009-11-05
Sorry.  Forget all that.  I am trying the new version of gnome-schedule on karmic and get this error:

```

$ kdesudo gnome-schedule
ERROR: Could not load icon
ERROR: Could not load icon
ERROR: Could not load icon
ERROR: Could not load icon
ERROR: Could not load icon
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 88, in __init__
    self.widget.set_icon(self.iconPixbuf)
AttributeError: main instance has no attribute 'iconPixbuf'

```

I suspect you have found a bug...

---

### Post by new_tolinux on 2009-11-05
I did not sudo anything. Not in 9.04 and not in 9.10
Gnome - Programs menu (not sure what it is called in English, I use the Dutch translation pack) - System tools (idem) - Scheduled tasks (named so in the Dutch translation, odd, because it should be named like "Geplande taken" in Dutch) -> No result in 9.10, worked fine in 9.04

Gnome - Terminal:
```
~$ gnome-schedule
/usr/share/gnome-schedule/mainWindow.py:158: DeprecationWarning: Use the new widget gtk.Tooltip
  tip = gtk.Tooltips ()
/usr/share/gnome-schedule/mainWindow.py:159: DeprecationWarning: Use the new widget gtk.Tooltip
  tip.enable ()
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 304, in schedule_reload
    data = self.crontab.read ()
  File "/usr/share/gnome-schedule/crontab.py", line 438, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/crontab.py", line 604, in parse
    success, ver, title, desc, output, display, command_d = self.get_job_data (job_id)
  File "/usr/share/gnome-schedule/crontab.py", line 690, in get_job_data
    return True, ver, title, desc, output, display, command_d
UnboundLocalError: local variable 'display' referenced before assignment
```
And again no Gnome-window with the application.

Only thing is..... the comments I get in terminal don't mean anything to me. They could as well have been Chinese.
I know, my bad, but linux is to me like DOS was in the early days. It took me a few years before I started to understand it.

---

### Post by Lars Noodén on 2009-11-05
As mentioned, it looks like you have found a bonafide bug, so it is probably time for a bug report if you have the inclination.  
Could you be so kind as to file one?
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Most of the time things work right out of the box, but the occasional bug report is a fairly inexpensive cost of doing business.  

I can't help with getting it to work, but can go through the message very superficially.

> **new_tolinux said:**
> 
Only thing is..... the comments I get in terminal don't mean anything to me. They could as well have been Chinese..

Ok, but these have nothing to do with Linux or ubuntu, except they happen to occur just now using ubuntu.  

The error message you just showed is output from a series of [python](http://www.python.org/) scripts that make up the package called 'gnome-sessions' which makes use of module from [GTK](http://www.gtk.org/features.html) to provide buttons and menus and all other GUI components (via PyGTk)
  
[INDENT][FONT="Courier New"]ls /usr/share/gnome-schedule/[/FONT][/INDENT]

Three scripts gnome-schedule.py, mainWindow.py, and crontab.py display symptoms.  The line numbers are there along with the error message, if you know python.  

I don't.  It was on my List of Things to Do for a while.

---

### Post by new_tolinux on 2009-11-05
Ok.
I did file a bug, but I linked it to an existing bug which was suggested by launchpad.
[https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/419471](https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/419471)

There was a suggestion that deleting everything in ~/.gnome/gnome-schedule/crontab/ should do the trick.
To be sure I wouldn't lose anything I first made a "backup" by using:
~$ crontab -l >somefile.txt (l = decapitalized L)
Then deleted the contents of ~/.gnome/gnome-schedule/crontab/
Result -> Scheduled tasks (gnome-schedule) works again (and deleting those files didn't delete any existing tasks)

Thanks for helping me out there =D>
I'll mark this thread as being solved.

---

### Post by craig100 on 2009-11-15
Deleting contents of ~/.gnome/gnome-schedule/crantab worked for me too!  

Thanks

Craig

---

### Post by ub-newbie on 2009-12-08
Deleting contents of ~/.gnome/gnome-schedule/crantab worked for me too!

---

### Post by Zeno Izen on 2010-01-20
I just upgraded to Karmic yesterday evening (Jan 19 2010) and I guess this bug hasn't been fixed yet.

Or maybe I'm wrong.  In any case I'm going to delete the above-mentioned file... but should I file a bug report?

---

### Post by Lars Noodén on 2010-01-21
> **Zeno Izen said:**
> I just upgrade to Karmic yesterday evening (Jan 19 2010) and I guess this bug hasn't been fixed yet.

Or maybe I'm wrong.  In any case I'm going to delete the above-mentioned file... but should I file a bug report?

Add to the [existing bug report](http://ubuntuforums.org/showthread.php?t=1311385) if a relevant one exists and include the details from your new system and the program in error.

```

lsb_release -rd 
apt-cache policy gnome-schedule

```

---

