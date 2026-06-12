---
title: "How to use a Wiimote to control Rhythmbox"
date: 2011-03-24
forum: Hardware
---

### Post by Emilie on 2011-03-24
[Edit: updated for Natty]

Did you ever wish you could have a remote control for your computer?  Especially if it is acting as a music player, having to walk over to it in order to change the volume, track, or to pause the music is annoying.  Well, if you have a wiimote, you can!  Quickly and easily.

**Prerequisites:**
- a wiimote
- functional bluetooth
- rhythmbox

**Steps:**

[LIST=1]
[*]Install wiican software
[*]Set up a udev rule so that any user can use wiican
[*]Create a wiican script to control rhythmbox
[*]Connect your wiimote to wiican
[*]Set up gnome so wiican is started each time you login
[/LIST]
**1. Install wiican software**

[*** New Instructions, updated for Natty, simpler]
- First install the Getdeb Repository PPA [http://www.getdeb.net/](http://www.getdeb.net/) (Learn how to install applications from this web site by [clicking here]("http://www.getdeb.net/updates#how_to_install"))-
- go into synaptic, refresh/reload the sources
- search for wiican
- install it!

[Old instructions, only use if the new ones don't work]
- Run the following lines from a terminal:```
sudo add-apt-repository ppa:wiicanteam/ppa

```(Maverick users must do the following three steps, Lucid users can skip them)
- Now open up synaptic and go to configuration->repositories
- Find the wiicanteam line (not the source code entry) in other software and click "edit"
- Change "maverick" to "lucid" (there is no version for maverick at the time of writing).  Save and close synaptic.

- Now run the following lines in a terminal:```
sudo apt-get update
sudo apt-get install wiican
```**2. Set up a udev rule so that any user can use wiican**
- from a terminal, run "sudo gedit /etc/udev/rules.d/76-wiican.rules"
- copy in the following code:```
KERNEL=="uinput", MODE:="0666"
```- save the file and reboot
[B]
3. Create a wiican script to control rhythmbox
[/B]- From a terminal, run "wiican"
- A small little wiimote will appear in your panel.  This means wiican is running.
- Right-click on the wiimote icon and selected preferences
- Uncheck the Mouse and Neverball boxes, unless you plan on using your wiimote for those.
- Click the "new" button on the left
- Type in "Rhythmbox" for the name, leave the description blank
- Copy the following into the mapping box, note there is a return character after the last line:```
Wiimote.A        = KEY_PLAYPAUSE
Wiimote.Up        = KEY_VOLUMEUP
Wiimote.Down    = KEY_VOLUMEDOWN
Wiimote.Left        = KEY_PREVIOUSSONG
Wiimote.Right    = KEY_NEXTSONG
Wiimote.Minus    = KEY_LEFT
Wiimote.Plus    = KEY_RIGHT
Wiimote.Home    = KEY_MUTE
Plugin.led.Led1    = 1

```- AGAIN: There **MUST** be a newline after the last entry.  Wiican will crash otherwise.
- Click Ok, make sure Rhythmbox is checked and click Save.

**4. Connect your wiimote to wiican**
- Now left click on the wiimote icon.  Choose "Rhythmbox"
- It will show you a message telling you to push the 1 and 2 buttons on your wiimote, do so.
- The LEDs on your wiimote will flash for a bit, Wiican should connect to your wiimote, and then you should see the first LED remain solid.  You are now connected
- If Rhythmbox is running, test it out! Left, and Right will go to next/prev tracks.  Up and Down will adjust the volume.  A will play/pause, + and - will fast-fwd/rewind, and home will mute.  Yay!
- (note all the wii button presses should work when rhythmbox is minimized EXCEPT fast-forward and rewind, for that, rhythmbox needs to be open and the cursor needs to be over top of the progress bar, this is because of how rhythmbox deals with ffwd/rewind)

**5. Set up gnome so wiican is started each time you login (optional)**
- if you want wiican to run each time you login, go to System->Preferences->Startup Applications
- click Add
- For the name put "Wiican", for the command put "wiican" (note the command must be in lowercase), for the description, but whatever you like.  Click save.
- Make sure your new Wiican item is in the startup list and is checked.  Click close.

Tada!  That's it! Enjoy your new wiimote power!  If you want to make your own mappings, consult the following files:
 - possible actions: [http://abstrakraft.org/cwiid/browser/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/wminput/action_enum.txt)
 - possible wiimote inputs: [http://abstrakraft.org/cwiid/browser/doc/wminput.list](http://abstrakraft.org/cwiid/browser/doc/wminput.list)

I hope this works for you as easily as it did for me (except figuring out the Wiican needs a blank line at the end of it's scripts).  Also, my desktop is in french so if I say things like "Click Preferences", on your desktop it might say "Settings", so use your imagination :)

Enjoy!

---

