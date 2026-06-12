---
title: "Brightness locks keyboard &amp;&amp; BEEPing over terminal"
date: 2008-10-28
forum: General Help
---

### Post by ZKjellberg on 2008-10-28
Hi folks,

Question #1: I put Intrepid Ibex (BETA and now RC) on my laptop, which is an older Dell Latitude D500 keyboard. Whenever I use the shortcut FN+ArrowUp/Down for brightness, my keyboard becomes unresponsive to all activity EXCEPT for brightness, kill X(CTR/ALT+Backspace), or switch to TTY. If I kill X or switch to TTY and back, my keyboard will respond once more.

Any idea why this occurs?

---------------------------------------------------------------

Question #2: I am running a desktop with Ubuntu LAMP 8.04 and am using the box for many activities. Essentially I am logging into the system using SSH, (through gnome-terminal or putty) using screen to retain a session, and using irssi to connect to a local bitlbee server for instant messages. So now after explaining that, I am wondering what would be required to enable a 'beep' notification for when I receive IMs.

For Gnome-Terminal, Terminal bell is enabled (by default) and Putty has 'default system alert sound' enabled. For screen, I have done ^A ^G to switch to AUDIBLE BELL.

Essentially, I am stuck on trying to figure out how to make irssi notify me of activity. (beyond time change and users logging on/off) I've attempting '^A M' to monitor through screen, but this will go off to any activity such as time change or users logging on/off. Also, this has never made a 'beep' noise, and simple shows a little window stating "ACTIVITY IN WINDOW #'

Any recommendations?

---

### Post by ZKjellberg on 2008-10-29
Is there a way to stimulate a beep over SSH to see if I am having issues receiving them?

I tested with 
echo -n '^G'
I am capable of receiving beeps, but unsure of what i'd need to set in irssi to enable them.

Also, I am uncapable of finding any logs which could explain my keyboard/brightness issue.

---

