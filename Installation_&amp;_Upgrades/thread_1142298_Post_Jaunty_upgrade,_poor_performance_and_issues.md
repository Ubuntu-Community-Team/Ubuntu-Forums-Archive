---
title: "Post Jaunty upgrade, poor performance and issues"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by vandy-sj on 2009-04-29
I'm just a desktop user, trialing Ubuntu as a possible switch from Windows. My previous Intrepid 8.10 was working nicely, and 'everything' was working. Last Thursday I applied the Jaunty 9.04 upgrade online (download, not using the Live CD), and it upgraded without a hitch. I also converted from ext3 to ext4 file system (using the recommended instructions), and that also had no problems. However, 9.04 is very disappointing so far. Computer utilization is up considerably: uses 30% more memory than Intrepid at idle, and CPU idle utilization jumped from 6% to 50% - with no applications running after a fresh boot up. OpenOffice 3.0 seems to work as before, but Firefox 3.0.10 is terrible. Firefox no longer plays MP3 music or live audio feeds, and the same goes for video playback (CNN news videos, etc.); which all worked perfectly on Intrepid. Firefox performance is VERRRRY SLOOOW, and sometimes cannot even connect to websites that I can confirm are online and quick in Windows using IE8. Jaunty just doesn't seem ready for 'primetime.' I haven't tried other features, as these are 'show stoppers' for me just now. I have downloaded and applied 5 updates since converting to Jaunty, but these issues are still there. Also, the Windows List in the bottom Border no longer displays running applications (neither minimized nor maximized windows). If I minimize an application, it just disappears from view with no way to recall it. If anyone knows of a fix, please let me know.

**[COLOR=Red][I have finally resolved all these issues. Scroll down to see my fixes][/COLOR]**

---

### Post by halovivek on 2009-04-29
Give this in terminal and try.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Then install the ubuntu restricted extras again to view and see the songs in Firefox.

---

### Post by vandy-sj on 2009-04-29
Thanks for the advice! I tried your recommendation and rebooted. 

Firefox is somewhat faster, but not like it used to be. I now get CNN videos displayed but no sound. I get no sound playback on CNN radio live streaming, nor on NPR audio program playbacks (MP3). System utilization is still quite high (50-68% CPU, memory greater than 70%) at idle. And still no Windows List on the bottom border to show running applications.

Any other suggestions?

---

### Post by vandy-sj on 2009-04-30
Update - Today downloaded and applied 24 updates, and rebooted. Upon reboot Firefox failed to start (launch), so I restarted again. This time Firefox launched, but the problems are still here - no audio playback from online news feeds and no audio with video playback. Oh, and still no Windows Lists (application tasks) visible on the bottom border. If Ubuntu Support is listening, I would sure appreciate some help.

---

### Post by slumbergod on 2009-04-30
I think some of the issues will take a few weeks for fixes to trickle down into the updates.

I've found several issues with my install. I had to get rid of pulse audio for my sound to work correctly. Then I had cpu spiking issues, which I resolved by downgrading the video driver to the intrepid one.

Then there have been issues with the apps I use most often - deluge(super buggy!) and vlc (resolved no fullscreen issue at last).

I recall intrepid being like this for me, and before that, hardy. Always, after patience updates sorted the issues out. I was going to stay with intrepid but the jaunty release had the latest xfce4.6 with it (xubuntu) so it was worthwhile.

---

### Post by vandy-sj on 2009-05-01
Thanks for your respond slumbergod! I had a few extra minutes to look closer today, and here is what I found (some echoes your findings). I normally don't have to dig in this far, but here goes.

I tried the new feature Computer Janitor, and it found and removed nearly 70 older DEB packages that were no longer needed, then rebooted.

The desktop performance perked up a little, but the sound and Windows Panel (bottom border) not displaying apps were still there.

I then tried using the System Testing feature to check my system - the swirling pointer showed up for a few seconds, then nothing. At this point I looked at the Log Files. Here is what I found:

~~~~~~~~~~
(From SysLog File) May 1 12:05:08 xxxx-desktop console-kit-daemon[2306]: WARNING: Couldn't read /proc/2305/environ: Failed to open file '/proc/2305/environ': No such file or directory 

[Confirmed, folder /proc/"2305" does NOT exist]

(From SysLog File) May  1 12:05:28 xxxx-desktop pulseaudio[3073]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed. 

[Confirmed, "/bin/pulseaudio" component is there; component "module-x11-xsmp.so" located in "/usr/lib/pulse-0.9/modules" folder, but fails to launch]

(From SysLog File) May  1 12:05:28 xxxx-desktop x-session-manager[2905]: WARNING: Could not launch application 'disk-manager-check.desktop': Unable to start application: Failed to execute child process "/usr/bin/disk-manager" (No such file or directory) 

[Confirmed, neither "disk-manager" folder nor "disk-manager-check.desktop" component exist]
~~~~~~~~~~

At this point I assume the "online Upgrade" process was not completely successful, and some system components were not upgraded or were removed (clean-up) but not replaced with a newer component (pure assumption on my part with my limited knowledge of Ubuntu). 

I'm considering saving my data and wiping the hard drive to try a 'clean install' from the Live CD. I haven't checked comments on the 'clean install' attempts yet. Any advice on doing this, or should I just "be patient" as you suggest?

---

### Post by vandy-sj on 2009-05-01
Update - I finally got sound back for local MP3 playback as well as online audio feeds and sound with videos. Here's the fix (at least it worked for me):

Step One:
Open a Terminal window and execute the following string:
sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras

Step Two:
a) System>Administration>Synaptic Package Manager
b) type "flashplugin" in the Quick search box
c) right click the box for "flashplugin-nonfree"
d) select "Mark for Reinstallation"
e) do the same for "flashplugin-installer" (not sure if this is necessary, but I did it)
f) click Apply
g) wait for it to finish

It took a while to apply the reinstall, but it worked. I rebooted following these steps.

Now to solve the System Testing and Windows Panel problems - baby steps forward.

---

### Post by vandy-sj on 2009-05-01
Another Update - I finally got System Testing working. Here's my fix:
a) System>Administration>Synaptic Package Manager
b) type "checkbox" in the Quick search box
c) right click the box for "checkbox"
d) select "Mark for Reinstallation"
e) do the same for "checkbox-gtk" (not sure if this is necessary, but I did it)
f) click Apply
g) wait for it to finish, then reboot

Still searching for Windows Panel (application taskbar) fix. Another baby step forward without having to 'clean install'.

---

### Post by vandy-sj on 2009-05-01
Final Update, I hope - Found the Panels (taskbar) fix, it resets the gnome-panel settings:

a) Open a Terminal window (must be in /home/username location)

b) Execute the following commands:
b1) gconftool-2 --recursive-unset /apps/panel
b2) killall gnome-panel
b3) rm -rf .gnome2 .gconf .gconfd .metacity
b4) gconftool -s --type bool /apps/update-notifier/auto_launch false

c) Exit Terminal window and reboot

On my Jaunty desktop it now looks like my previous Intrepid layout (e.g., shutdown icon now on top panel right corner instead of top center), but everything is back and it works OK.

I avoided a 'clean install' by fixing these issues after an online Upgrade. 

It appears that general performance has also returned to previous Intrepid-level; with CPU usage idling at ~35% and memory down to 50% usage. I still have a couple of WARNINGS in the SysLog, but most things seem to be working again. 

I hope this helps someone else.

---

