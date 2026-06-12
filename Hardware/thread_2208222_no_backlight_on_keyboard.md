---
title: "no backlight on keyboard"
date: 2014-02-27
forum: Hardware
---

### Post by fanhs on 2014-02-27
i have a cmstorm keyboard and i have installed ubuntu 12.04 recently..my problem is that my keyboard's backlight isn't working! can you help me please?

---

### Post by David_Uriel_Rodrig on 2014-04-06
Hi, I had exactly the same problem and I found the solution to this in the next link:
[https://answers.launchpad.net/ubuntu/+source/linux/+question/241299](https://answers.launchpad.net/ubuntu/+source/linux/+question/241299)

Just in case I'll copy what worked for me:
"[COLOR=#333333][FONT=Ubuntu]sudo xmodmap -e 'add mod3 = Scroll_Lock'" [/FONT][/COLOR]
***********************************************
[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][RickB (malydog)]("https://launchpad.net/~malydog") said on 2014-02-02:[/TD]
[TD="class: bug-comment-index"]#20[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I'm glad to hear it helped you guys, thanks for the feedback. Here's an update...
First, I found a cool new command:
sudo xmodmap -e 'add mod3 = Scroll_Lock'
This makes the scroll lock key turn the backlight on and off (but does not override "xset led 3").
Second, my wife (the keyboard is for her) says that sometimes the backlight fails to turn on. No idea why, maybe there is a race condition when logging in.
So I have written a tiny shell script, put in a one second sleep to help avoid any potential race, and just in case it still fails I also execute the xmodmap command in the same script. So hopefully she can turn the backlight on with the scroll lock key if it does not come on automatically.
Here is the shell script:
#!/bin/bash
sleep 1
xset led 3
xmodmap -e 'add mod3 = Scroll_Lock'
I saved it as /home/wife/scripts/backlight.sh (don't forget to make it executable!).
Then I updated the .desktop file at /etc/xdg/autostart/backlight.desktop so that it runs the new shell script, like so:
[Desktop Entry]
Type=Application
Name=Devastator Backlight
Exec=/home/wife/scripts/backlight.sh
Icon=system-run
X-GNOME-Autostart-enabled=true
[/FONT][/COLOR]
***********************************************
[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][RickB (malydog)]("https://launchpad.net/~malydog") said on 2014-01-04:[/TD]
[TD="class: bug-comment-index"]#16[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]For example in Ubuntu I tried a few things that worked, some that didn't.
In the end I settled on this approach:
Create file /etc/xdg/autostart/backlight.desktop
Edit the file so it looks something like this:
[Desktop Entry]
Type=Application
Name=Devastator Backlight
Exec=xset led 3
Icon=system-run
X-GNOME-Autostart-enabled=true
[/FONT][/COLOR]
*************************************************

---

### Post by josephdaniel2 on 2014-07-11
> **David_Uriel_Rodrig said:**
> Hi, I had exactly the same problem and I found the solution to this in the next link:
[https://answers.launchpad.net/ubuntu/+source/linux/+question/241299](https://answers.launchpad.net/ubuntu/+source/linux/+question/241299)

Just in case I'll copy what worked for me:
"[COLOR=#333333][FONT=Ubuntu]sudo xmodmap -e 'add mod3 = Scroll_Lock'" [/FONT][/COLOR]
***********************************************
[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][RickB (malydog)]("https://launchpad.net/~malydog") said on 2014-02-02:[/TD]
[TD="class: bug-comment-index"]#20[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I'm glad to hear it helped you guys, thanks for the feedback. Here's an update...
First, I found a cool new command:
sudo xmodmap -e 'add mod3 = Scroll_Lock'
This makes the scroll lock key turn the backlight on and off (but does not override "xset led 3").
Second, my wife (the keyboard is for her) says that sometimes the backlight fails to turn on. No idea why, maybe there is a race condition when logging in.
So I have written a tiny shell script, put in a one second sleep to help avoid any potential race, and just in case it still fails I also execute the xmodmap command in the same script. So hopefully she can turn the backlight on with the scroll lock key if it does not come on automatically.
Here is the shell script:
#!/bin/bash
sleep 1
xset led 3
xmodmap -e 'add mod3 = Scroll_Lock'
I saved it as /home/wife/scripts/backlight.sh (don't forget to make it executable!).
Then I updated the .desktop file at /etc/xdg/autostart/backlight.desktop so that it runs the new shell script, like so:
[Desktop Entry]
Type=Application
Name=Devastator Backlight
Exec=/home/wife/scripts/backlight.sh
Icon=system-run
X-GNOME-Autostart-enabled=true
[/FONT][/COLOR]
***********************************************
[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][RickB (malydog)]("https://launchpad.net/~malydog") said on 2014-01-04:[/TD]
[TD="class: bug-comment-index"]#16[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]For example in Ubuntu I tried a few things that worked, some that didn't.
In the end I settled on this approach:
Create file /etc/xdg/autostart/backlight.desktop
Edit the file so it looks something like this:
[Desktop Entry]
Type=Application
Name=Devastator Backlight
Exec=xset led 3
Icon=system-run
X-GNOME-Autostart-enabled=true
[/FONT][/COLOR]
*************************************************
OMG, this helped me out alot! :D Thanks!

---

