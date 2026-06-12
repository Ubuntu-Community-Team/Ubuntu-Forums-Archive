---
title: "[SOLVED] Screenllet Issues -- Three of 8 Not Starting"
date: 2008-07-25
forum: General Help
---

### Post by Mgiacchetti on 2008-07-25
OK I have two Ring Sensors, a DigiClock, My IP and Windowlist that starts at login... Trash MainMenu and VolumeControl do not start at login.  I have them set to but they just dont want to.   They dont show up in running sessions.  They are in the Startup Programs list, along with the others.

What can i do to correct this issue??

Also: on another note, (seperate problem not high importance)
Some screenlets, when set to "always above" decide to be below other windows.

and Window List still likes to disappear when you rightclick.

again... This is not as important as the three that dont want to start at login

---

### Post by rune0077 on 2008-07-25
You shouldn't add them to your startup list, I think. Instead, open the screenlet manager, select the screenlet in question, and check the "Auto start on login" box, and they should launch everytime the screenlet daemon loads.

---

### Post by Mgiacchetti on 2008-07-26
> **rune0077 said:**
> You shouldn't add them to your startup list, I think. Instead, open the screenlet manager, select the screenlet in question, and check the "Auto start on login" box, and they should launch everytime the screenlet daemon loads.

The problem therein lies when I click the "auto start on login" box it adds the selected screenlet to the startup list.

---

### Post by Mgiacchetti on 2008-07-26
also the following are in the startup list in preferences > services

MainMenuScreenlet        doesnt work
myIPScreenlet               works
RingSensorsScreenlet     works
VolumeControlScreenlet  doesnt Work
WindowsListScreenlet      Works

the following are NOT in the startup list
Digiclockscreenlet           Works
TrashScreenlet                Doesnt Work


Also the following show up in sessions
digitalclockscreenlet
myipscreenlet
windowlistscreenlet
ringsensorsscreenlet

these are all on and working, however the following do not show up in the sessions tab
MainMenuScreenlet
VolumeControlScreenlet
TrashScreenlet

And these are also on and running currently.

So my question, why, when i check the "auto start on login"  does it not work for the above three, why, when i start all the screenlets i want running, do all but these three show up in the sessions tab, why do i have to manually start these three screenlets.

if they shouldnt be in the startup tab, then why when i remove them do they fail to start???

---

### Post by rune0077 on 2008-07-26
Hmm, maybe they should be in the startup list, if they're added there manually. I don't have any screenlets start up automatically, so I just have the Screenlet Daemon listed, and I just assumed it kept track of which should be started and which shouldn't. 

Maybe try to run the screenlets that don't startup manually. Make sure they are listed in running sessions, then click the "save session" button (under the session options tab).

---

### Post by Mgiacchetti on 2008-07-26
ok these are the screenlets that are running 
Main Menu
Volume Control 
Trash
My IP
DigiClock
RingSensors (two Instances)
Windowslist

These are the ones that show up in the running sessions 
digitalclock
myip
windowlist
ringsensors

screenlets-daemon

so if i click "remember session" it does not remember that I have three other screenlets running, because it doesnt see them running.

---

### Post by Mgiacchetti on 2008-07-26
I have attached a screenshot of what I am talking about.

---

### Post by rune0077 on 2008-07-26
That's pretty weird. I'm afraid I'm at a loss here. I have all my screenlets controlled from the sidebar-screenlet. My only advice is, that you try to use that, since it will autostart all screenlets associated with it once you launch it, and it works really flawless. You can always just set the sidebar as transparent if you don't want to have to look at it.

You can get the sidebar here: [http://www.gnome-look.org/content/show.php/Screenlets+0.1.2?content=82586](http://www.gnome-look.org/content/show.php/Screenlets+0.1.2?content=82586)

That's a pretty round about way to do it, but it's all I can think of.

Oh, do you have the latest version of screenlets, or is it just the one from the repo? Maybe if you don't have the latest version, grab it (also from gnome-look) and see if this issue has been fixed.

---

### Post by Mgiacchetti on 2008-07-26
-removed by op-

---

### Post by Mgiacchetti on 2008-07-26
so no one knows how to fix this?

and btw --  yes i do have the latest version, the rev. i forget which, but it says that 2.10 cant install because i have a later version.

---

### Post by Mgiacchetti on 2008-07-27
^bump^

---

### Post by Mgiacchetti on 2008-07-27
Found out what the problem was...


If you run a screenlet and want it to autostart every login, DO NOT SELECT THE "autostart every login"  UNTIL YOU HAVE STARTED THAT SCREENLET.  You will never be able to autostart that screenlet until you full remove --purge screenlets, then del all files with screenlets in the filename, then install screenlets.


Have verified this twice myself.

---

