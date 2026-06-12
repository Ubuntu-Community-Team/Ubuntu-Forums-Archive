---
title: "compiz prob..."
date: 2008-09-06
forum: General Help
---

### Post by yogen on 2008-09-06
heyy guys...i just heard about the compiz...and im so impressed that i couldnt wait for trying it...

but during installations...
refering this site
([http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml))

i am getting a error...saying that this is a broken package...i have followed most of this steps...so will it affect my ubuntu...i hav updated it by these commands...and after executing these commands..i learnt that gnome users had to do somthing else...so im am but worried...though i think this shouldnt cause any problem...!!!

CODE
wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)

CODE
sudo apt-key add DD800CD9.gpg

Now click the "Close" button on the Software Sources window and you will be asked if you want to reload the information about available software, so click the "Reload" button and wait for the window to disappear.

Copy/Paste the following lines in the terminal window:

CODE
sudo apt-get update

sudo apt-get -y upgrade

help me guys...i am just a week old ubuntu freak...!!!

---

### Post by Jack M. on 2008-09-06
That guide is outdated - Compiz's effects are now included in Ubuntu by default. All you need to do is go to System > Preferences > Appearance, then the 'Visual Effects' tab, and select 'Normal'. (If there's a message about installing restricted drivers, do so then restart.) That should do it! For security, you also should undo the changes mentioned in that guide. Run:
```
sudo apt-key remove DD800CD9.gpg
```
in a terminal, and also go to System > Administration > Software Sources and remove any entries in the 'Third-Party Software' tab.

---

### Post by overdrank on 2008-09-06
Moved to  Desktop Effects & Customization

---

### Post by yogen on 2008-09-06
okay...but i wanted the 3d cubes...which is the effect of compiz-advanced...what about that?

---

### Post by Victormd on 2008-09-06
then you need to install compizconfig settings manager. Open a terminal and type:
```
sudo apt-get install compizconfig-settings-manager
```
Or search for it in synaptic package manager...
NOTE: this is assuming that your video drivers are properly installed and Jack M.'s suggestion did not return any error messages (i.e., restricted drivers, etc.).

Then go to SYSTEM>PREFERENCES>COMPIZCONFIG SETTINGS MANAGER and you'll be able to set everything up there.

---

### Post by Infinite Indefinite on 2008-09-06
> **yogen said:**
> okay...but i wanted the 3d cubes...which is the effect of compiz-advanced...what about that?

To get 3d cubes working try this:

1) Increase the number of desktop workspaces to 4.  (Right click on the desktop workplaces - they should be next to the trash.)

2) Go to System > Preferences > Advanced Visual Effects (or CompizConfig Settings Manager).  Click General Options.

Go to the Desktop Size tab, and ensure that horizontal desktop size is set to four.  I kept Vertical Virtual Size and Number of Desktops at one.

Click Back.

3) In the Desktop section, enable Desktop Cube and Rotate Cube.

4) Make sure you've got Compiz working.  Check System > Preferences > Appearances and select Custom.


Close, logout and login, and you should be able to rotate the cube.

---

### Post by RampageUT on 2008-09-06
Thanks for the help, was having similar problem and this worked for me.

---

### Post by yogen on 2008-09-06
thnx a lot dude...it has worked...but just one more problem...
my cube just has 4sides...neither top nor bottom...searched a lot in preferences, but didnot find anything...can you help me with this too...im sure you would...!!!

---

### Post by Infinite Indefinite on 2008-09-06
Try this:

1) Go to Advanced Visual Effects / CompizConfig Settings Manager

2) Go to the Utility Section and enable CubeCaps

3) Now open CubeCaps and click the Behaviour Tab

4) Enable 'Scale top image' and 'Scale bottom image'.

Now click back, and see if everything is ok.

---

### Post by RampageUT on 2008-09-06
> **Infinite Indefinite said:**
> Try this:

1) Go to Advanced Visual Effects / CompizConfig Settings Manager

2) Go to the Utility Section and enable CubeCaps

3) Now open CubeCaps and click the Behaviour Tab

4) Enable 'Scale top image' and 'Scale bottom image'.

Now click back, and see if everything is ok.


This didn't do it either.

---

### Post by Infinite Indefinite on 2008-09-06
Ok, see if the following are enabled in CubeCaps > Behaviour

Draw top face
Draw bottom face
Scale top image
Scale bottom image
Clamp top face image to border
Clamp bottom face image to border

Enable all of those, enable CubeCaps, and then try it.

---

### Post by RampageUT on 2008-09-06
> **Infinite Indefinite said:**
> Ok, see if the following are enabled in CubeCaps > Behaviour

Draw top face
Draw bottom face
Scale top image
Scale bottom image
Clamp top face image to border
Clamp bottom face image to border

Enable all of those, enable CubeCaps, and then try it.
I didn't realize that it works with the mouse. I'm not sure its supposed to work with the arrow keys.

---

### Post by Victormd on 2008-09-06
> **yogen said:**
> thnx a lot dude...it has worked...but just one more problem...
my cube just has 4sides...neither top nor bottom...searched a lot in preferences, but didnot find anything...can you help me with this too...im sure you would...!!!

Are you talking about having a workspace on the top and bottom caps? If so, I don't think you can do this... If not, then I think Infinite Indefinite's suggestions should cover your issue. Let us know if it worked.

---

