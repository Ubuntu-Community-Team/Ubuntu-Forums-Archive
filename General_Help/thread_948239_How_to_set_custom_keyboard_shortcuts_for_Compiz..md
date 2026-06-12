---
title: "How to set custom keyboard shortcuts for Compiz."
date: 2008-10-15
forum: General Help
---

### Post by MasterNetra on 2008-10-15
For a good while I have been wondering how to setup custom shortcut keys to programs in Gnome for Ubuntu 8.04 - 8.04.1. Well after seeing a how to, for metacity i begin snooping around trying to see if their was a compiz (Compiz-fusion) alternative to it. Low and behold there is! In this tutorial i will go through how to setup the gnome system monitor to be brought up with Ctrl+alt+delete.

So lets get started shall we?

 
*(If you at some point freed up ctrl+alt+del already or plan to set the system monitor's keyboard shortcut to something else then feel free to skip number 1.)*

1.
   a. Make sure you go into System->Preferences->Keyboard Shortcuts
   b. Scroll down until you see the shortcut for your Logout and change it
      to something else. For me i set it as Ctrl+Alt+E.

2. Press Alt+F2 to bring up the "Run Application" box and type in 
   "gconf-editor" (without the " of course) and press enter.

3. Go to Apps->compiz->general->allscreens->options

4. 
   In the upper left window of the box you will see a list of options and such. Here what you will want to do is set but the commands for the keyboard shortcuts as well as the key shortcuts themselves. Lets start by adding in the system monitors address. 
   
Go down to "Command0" double click on in and in value place of the popup box enter the system monitors link which is "gnome-system-monitor".
*Now you might wonder why start at 0 and not 1,3,5, etc? Well i tried that but it seems if any of the previous are disabled then Ubuntu doesn't look passed it. So start at the earliest blank.*

5.
  Now that we have the address in lets setup the shortcut key!
Scroll down to "run_command0_key" and again double clicked on it. In its value box enter "<Control><Alt>Delete" *Note: the <> tell the system that the key needs to be held and having them around the last key will cause it not to work for whatever reason. And yes you could do something like <Control><f>r or <a><s>d Just also note that using the shift key may change the value of anykey that would normally have its value changed by shift. ex. instead of putting <Control><Shift>2 you may need to place <Control><Shift>@ *

6. Quit the Configuration editor and the keyboard shortcut should now be ready to go. No logout is required!

---

