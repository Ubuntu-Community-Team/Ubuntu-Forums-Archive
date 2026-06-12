---
title: "HP B110a Photosmart printer"
date: 2013-09-08
forum: Hardware
---

### Post by Carbs70 on 2013-09-08
Hey,

In previous version of Ubuntu, I had no problems with my printer. But for the past year, since 12.04LTS, I'm unable to print.

I can:
[LIST]
[*]Find the printer on the network
[*]Scan using XSANE, which is launched via HP Device Manager
[*]Use HP Device Manager to perform 'Align cartridges'
[*]Use HP Device Manager to see ink levels
[/LIST]

But I cannot:
[LIST]
[*]Print a test page
[*]Print anything else!
[/LIST]

The HP Device manager looks like, for all intents and purposes it is sending a print job, updating status to "in progress", and then completing the job.
No action on the printer front however, and when I look at the Printer via Ubuntu Printer Properties, I see the status "Processing - no profiles specified in PPD"

I've uninstalled and reinstalled the HPLIP drivers many times.... and it appears they must be working given the levels of success I'm having....except for the one critical issue of printing lol!

Anyone got any ideas?

---

### Post by Carbs70 on 2013-09-30
New version of HPLIP turned up today......still no joy however. 

Does anyone have any ideas?  :confused::confused::confused:

---

### Post by Petro Dawg on 2013-09-30
Does the printer work if you connect directly with a USB cable instead of over the network?  Of course testing this may require you to move equipment, which may not be an option for you. 

Also, have you tried other drivers, I believe there are some generic HP drivers in HPLIP (I'm not at my home PC so I can't verify that at the moment).  But you might try a generic driver, or one for a similar model (which may end up allowing you to print, but not scan... or such troubles).

---

### Post by oldfred on 2013-10-01
Are you using the HPLIP from Ubuntu repository or the much newer version directly from HP?

I have an HP Deskjet 3520 and installed from HP without issue.
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

