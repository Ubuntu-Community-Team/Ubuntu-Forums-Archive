---
title: "Where is thunderbird?"
date: 2005-11-14
forum: General Help
---

### Post by edross on 2005-11-14
I've used synaptic to install Thunderbird mail client.  (Can not seem to get the pop support on Evolution to work).  Everything seems to have installed ok, but I don't know where it is or how to start it.  

Yes I am somewhat new to Linux, - this seems like it should be an easy thing to do.

I guess this is true of most of the items I install this way.  Sometimes they show up on the menus, sometimes they don't and I never know where they are installed.

---

### Post by brim4brim on 2005-11-14
I think it should be in /usr/bin

POP support works in Evolution I got my gmail working with it perfectly.  Thunderbird should have installed a shortcut in the applications->internet menu, you may need to refresh the panel or log out and log back in before it'll appear in the menu.

---

### Post by kperkins on 2005-11-14
If you installed it with synaptic it should show up in your menus under Internet.  If not just type in thunderbird on the commandline, and it should start up.
(You can add a shortcut on your panel by right clicking on it and choosing add to panel, and clicking on add application and looking for it under Internet{or if you can't find it, go back and click on custom application launcher, type in thunderbird for the title and thunderbird for command and browse for an icon})

---

### Post by Jens Willem on 2005-11-14
Sometimes when you install an app it doesn't show up in the menu until it is refreshed. Open a terminal and enter "killall gnome-panel". This should work. If not, follow the instructions above to create a shortcut.

---

### Post by evilberg on 2005-11-14
[QUOTE=kperkins]If you installed it with synaptic it should show up in your menus under Internet.  If not just type in thunderbird on the commandline, and it should start up.
(You can add a shortcut on your panel by right clicking on it and choosing add to panel, and clicking on add application and looking for it under Internet{or if you can't find it, go back and click on custom application launcher, type in thunderbird for the title and thunderbird for command and browse for an icon})[/QUOTE]

Though use "mozilla-thunderbird"

---

### Post by kperkins on 2005-11-14
[QUOTE=evilberg]Though use "mozilla-thunderbird"[/QUOTE]
:oops: Shows how often I start mozilla-thunderbird from the commandline. :D ](*,) (Why use mozilla-thunderbird, and not mozilla-firefox? I don't understand the rationale behind that.)

---

### Post by webguy on 2005-11-20
I've got Ubuntu 5.10, using apt-get or synaptic, mozilla-thunderbird is not available. How can I install it other than downloading the tar.gz file from the mozilla.org website?

Thanks

webguy

---

### Post by rcerreto on 2005-11-20
[QUOTE=webguy]I've got Ubuntu 5.10, using apt-get or synaptic, mozilla-thunderbird is not available. How can I install it other than downloading the tar.gz file from the mozilla.org website?

Thanks

webguy[/QUOTE]

How strange, it's in the standard repositories.
Then you should be able to get it via apt-get/synaptic
check /etc/apt/sources.list
maybe there's something wrong there.
Just in case, remember to run

sudo apt-get update

to reload the packages list

---

### Post by tim15856 on 2005-11-21
It should be listed under "Add application".

---

### Post by webguy on 2005-11-21
I checked the default sources.list file, it had alot commented out. I uncommented them and ran apt-get update. I was able to install Thunderbird 1.0.7

Thanks

Webguy

---

