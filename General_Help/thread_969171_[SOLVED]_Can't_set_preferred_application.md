---
title: "[SOLVED] Can't set preferred application"
date: 2008-11-03
forum: General Help
---

### Post by thomasyen on 2008-11-03
I just installed Ubuntu Intrepid, and I decided to change the default application for playing Ogg Vorbis files from Rhythmbox to XMMS. After right-clicking on an Ogg Vorbis file, selecting "Open with Other Application" (it says that all Ogg Vorbis audio files will be played using the selected program), then selecting XMMS, the file was played using XMMS. However, when I double clicked on the file to play it again, it was opened using Rhythmbox instead of XMMS. Seems the default application for Ogg Vorbis files was not changed. I've never encountered this problem before, when I was using Hardy. Any ideas on how to ix this? Any help would be appreciated.

---

### Post by scouser73 on 2008-11-04
**Right-click** on the file you want to play in XMMS, select **Properties** and then click the **Open With** tab and select XMMS.

---

### Post by thomasyen on 2008-11-06
I tried that, and got XMMS to play it (as I already described in my previous post). The question is, how do I get that selection to persist? By persist, I mean that the system will use XMMS as the default player from then on. Have any of you encountered the same problem? (If not, I'm considering a reinstall of Intrepid.)

---

### Post by mc4man on 2008-11-06
Are you sure your setting XMMS as default for Ogg Vorbis thru the right click -> **properties** -> open with?
If so the setting should hold.

To ck. further go to home folder -> .local/share/applications/mimeapps.list.
Look for this line - 'audio/x-vorbis+ogg='
The first listed app is the default.

For example mine is 
audio/x-vorbis+ogg=kde-amarok.desktop;vlc.desktop;
(amarok is the default, vlc is an option from the right click -> open with menu.

Edit: did a quick ck. xmms should work fine as default.
You'd see an entry 'similar' to this (SODCKU may/would be diff. on mine vs. yours
audio/x-vorbis+ogg=userapp-xmms-SODCKU.desktop; ect.,ect.

There should also be a blue diamond xmms.desktop in .local/share/apllications (userapp-xmms-SODCKU.desktop would be it's complete name(only shown as xmms

---

### Post by thomasyen on 2008-11-08
So I suppose I can set the preferred application by directly modifying .local/share/applications/mimeapps.list?
(The right-click -> select preferred application method doesn't hold for me, for some strange reason.)

---

### Post by mc4man on 2008-11-08
> So I suppose I can set the preferred application by directly modifying .local/share/applications/mimeapps.list?
Generally speaking no that's not a good idea, though in some cases or at some point you could.

Basically mimeapps.list reflects 3 things
Default and available choices from insertion of removable media using an apps default .desktop, a copied .desktop with an altered name and Exec= or a custom definition for an app (userapp) 

A right click 'open with' choice on files or folders using an apps default.desktop or a copied .desktop with altered name and Exec= or a custom definition (userapp) 

A double left click file association again using any of the 3 above .desktops though in this case the .desktop is moved to first listed

In most 'lines' the first listed is the default action


Intrepid has made it very easy to add choices for removable media thru file management -> media. You can add either a default.desktop (from 'Open with other application'  or custom definition (from 'use a custom command')

As far as r. click 'open with' or the left d.click default you can "add' an app. to a line if the .desktop is in your path (/usr/share/applications  or ~/.local/share/applications

It's far better to use the the right click 'open with' or 'open with other application' to add choices.

As far as 'custom definitions' type of .desktop (userapp) the only practical way is thru the r. click. (the .desktop is created that way.

Even though intrepid has made things easier there still are advantages to using a copy .desktop method when wanting to use an app in a particular situation with a custom command or script when needed.

In the case of XMMS the .deb I installed didn't install a xmms.desktop hence the need to use a 'custom definition' (userapp)


Here's an example for hardy though the basics still apply to intrepid, easier to see specifics than explain here

basic's, mplayer ex.
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by celem on 2008-12-31
I removed F-Spot and installed Picassa for use as my photo manager on my Ubuntu 8.10 system. Picassa is an integrated-wine based program and it's install didn't create any entry in /etc/gnome/defaults.list, /home/user/.local/share/applications, etc. Can anyone shed light on how to populate Picassa so that it will be the preferred application when a SD card is inserted or a camera is connected?

FYI - the command in the menu is "/opt/google/picasa/3.0/bin/picasa".

---

### Post by celem on 2009-01-02
FYI - I solved the problem with Picasa - see my post at:
[http://tinyurl.com/a2b7e4](http://tinyurl.com/a2b7e4)

---

### Post by texla on 2011-01-19
doublepost

---

### Post by texla on 2011-01-19
double post - delete

---

### Post by texla on 2011-01-19
> **mc4man said:**
> 
go to home folder -> .local/share/applications/mimeapps.list.
Look for this line - 'audio/x-vorbis+ogg='
The first listed app is the default.

For example mine is 
audio/x-vorbis+ogg=kde-amarok.desktop;vlc.desktop;
(amarok is the default, vlc is an option from the right click -> open with menu.



This worked for me to set Banshee as my default player in Lucid. 
I just put the banshee code in front of the Vlc player code for wav and  also for mpeg files and now it will open as default.  Banshee seems like  a cool player, too.  No other approach worked so thanks for this 3 year  old post!  =D>

---

