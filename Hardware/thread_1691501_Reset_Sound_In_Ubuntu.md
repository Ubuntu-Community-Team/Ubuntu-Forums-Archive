---
title: "Reset Sound In Ubuntu"
date: 2011-02-20
forum: Hardware
---

### Post by de1337ed on 2011-02-20
Hey Guys,

My mic in ubuntu wasn't working, and (because I'm new to linux) I sort of messed up the sound settings alot. How do I reset my sound settings back to the factory default (Like back to the Ubuntu 10.10 64bit default)? I have the installation cd and everything, but I dont want to loose my files and other packages I downloaded. Thank you.

---

### Post by chessnerd on 2011-02-20
Sadly there is no "factory reset" or "system restore" when it comes to sound in Ubuntu. What you have to do to reset the sound depends on how much you did. 

If you installed/removed a bunch of packages to try to fix your issue, you'll need to remove/reinstall those installed packages. Don't worry if you don't remember exactly what you did, the Synaptic Package Manager has a history of every package you've removed or added under File > History. After this, you will likely need to reboot.

If you changed sound settings, going to the sound preferences should allow you to fix those issues. Every system is different, so let us know what options are available under the Hardware and Output tabs.

If you did anything else, let us know so we can tell you how to revert it.

Lastly, don't fret. I've messed up a lot of settings in Ubuntu from time to time (okay, I do it all the time :P) but rarely am I forced to do a full reinstall.

---

### Post by de1337ed on 2011-02-20
Well how do you completely remove all the audio software from your computer, then reinstall the pulseaudio driver? will that work?

---

### Post by chessnerd on 2011-02-20
> **de1337ed said:**
> Well how do you completely remove all the audio software from your computer, then reinstall the pulseaudio driver? will that work?

That bad? :shock:

It's okay... I've done worse. I usually fix the issue by going to Synaptic and undoing what I've done.

So, start by opening up the Synaptic Package Manager (System > Administration). From there you have two options, I would advise the first, but the second should work too.

Option 1: Go to File > History and take note of everything you've installed that deals with audio. Type the names of those packages into the search box and mark them for removal. Apply the changes. Close Synaptic and run the command sudo apt-get autoremove and also run sudo apt-get autoclean to get rid of the rest of the stuff.

Option 2: Type "audio" into the search box. Now, to the left of the Package column are two small columns, one with an "S" and one that's blank. Select the "S" column to order your packages based on what's installed. Note anything that doesn't have a little Ubuntu logo in it's row. Mark them for removal. Repeat until everything without that logo is marked, taking note of the dialogs that come up. Do read the dialogs to make sure that you aren't accidentally removing programs you want (although you should be able to get them back later) and make sure that you aren't removing anything important (if it has "ubuntu" in the package name, it's probably important). Apply the changes. Close Synaptic and run the command sudo apt-get autoremove and also run sudo apt-get autoclean to get rid of the rest of the stuff.

After doing either option, re-open Synaptic and search for pulseaudio. Install the pulseaudio package. Reboot.

As long as you don't accidentally remove something really critical to the system (which isn't likely, but is possible) you should now have sound back to (pretty much) the way it was when you started out.

---

### Post by de1337ed on 2011-02-20
I tried what you told me, and I have my sound back (my mic doesn't work for skype, and if you have a solution that would be great. Trying to fix that is what got me in this mess). Anyway, If you were wondering, this was the tutorial i followed: 

[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)

Now, im trying to install this libcanberra pack (ubuntu certified) because I think its necessary but it was removed in the process of using that tutorial. I keep getting this error message: 
Unresolved Dependencies:
libcanberra-pulse:
  Depends: libcanberra0 (=0.25-0ubuntu1) but 0.25-0ubuntu2~audiohacks1 is to be installed

Also, instead of have the nicer sleeker volume control icon in the top right corner whenever i change the volume with my keyboard, I have the following: 
[IMG]http://img560.imageshack.us/i/issue1.png/[/IMG][IMG]http://i54.tinypic.com/2w7r4vd.png[/IMG]

anymore ideas?

---

### Post by de1337ed on 2011-02-20
*bump* sorry, still need a suggestion. thank you.:popcorn:

---

### Post by chessnerd on 2011-02-21
So you used that blogspot post to remove pulseaudio. Neat, I have a friend who's struggling with pulseaudio who I can show that too. 

Okay, here is the problem:

> Go into System>Adminitstation>Software Sources>Other Software Tab>Add

**Paste this into the APT Line: ppa:dtl131/ppa**

In terminal type:

sudo apt-get update

**sudo apt-get install gnome-applets gnome-media gnome-settings-daemon libcanberra0**

You installed the libcanberra0 from a different repository. Go back to the software sources and uncheck that repo. Then, remove libcanberra0 and try to install libcanberra-pulse after that. It should work then.

Also, you can run this command:

```
sudo apt-get install libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol 
```

Which would do the reverse of the purge command you ran earlier.

As for the volume indicator, I'll need to look into that. However, at the moment, I'm a bit busy. Doing these couple fixes could fix the volume indicator, but if it doesn't I'll look into what package you need to install or what setting you need to change.

Let us know if there is anything else you are having trouble with.

---

### Post by de1337ed on 2011-02-22
I think uninstalling and reinstalling libcanberra did something to my ubuntu, because now I just cant boot into it period. -_-. So, I'm using my windows right now. Can you guide me through restoring my ubuntu so its useable again? I'm seriously just considering formatting and reinstalling ubuntu at this point, but I would rather try other options first. Please respond as soon as possible. Thank you :)

edit;;;
by hitting ctrl + alt +f1 and going into the terminal at the start, i tried to to do sudo apt-get install -f and i get a lot of errors involving gstreamer, audio packages, and how it wants to install gnome-canberra and stuff. It keeps saying that I can't fetch them. Also, it keeps saying that it can't fetch from ppa.launchpad.net. I don't know what to do! please help

---

### Post by de1337ed on 2011-02-22
*Bump* again. I really need this to be fixed. Thank you.

---

### Post by chessnerd on 2011-02-22
> **de1337ed said:**
> by hitting ctrl + alt +f1 and going into the terminal at the start, i tried to to do sudo apt-get install -f and i get a lot of errors involving gstreamer, audio packages, and how it wants to install gnome-canberra and stuff. It keeps saying that I can't fetch them. Also, it keeps saying that it can't fetch from ppa.launchpad.net. I don't know what to do! please help

It is difficult to connect to a wireless network via command line, so if you are trying to use a wireless connection, you'll either need to Google how to do that, or, and I would advise this, switch to an Ethernet cable and then try sudo apt-get install -f again. 

If you are already using a wired connection, then apparently networking was damaged and, at that point, I think that the only way to fix it would be with a reinstall or, if you can get into Gnome, you can put in the install disk for Ubuntu and use System > Administration > Software Sources to choose the install disk as your repository to try the repair.

---

