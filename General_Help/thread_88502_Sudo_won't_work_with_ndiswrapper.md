---
title: "Sudo won't work with ndiswrapper"
date: 2005-11-10
forum: General Help
---

### Post by Tha1 on 2005-11-10
I'm trying to install ndiswrapper.I unpacked the tar file but,if I want to install,making in the console:
"make"
he gives me an error saying "command not found". I followed the instructions on the NdisWrapperUbuntuHowTo,and in the ndiswrapper site,but I can't move on without installing,bcoz it gives me this error,even if I call sudo.Any sugestions? :(

---

### Post by rcerreto on 2005-11-10
It looks you didn't install 'make'. It's not installed by default, neither are the gcc C compiler and several other things needed to buid sw from source.

At a minimum:

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

---

### Post by Lambert on 2005-11-10
It's in a repository and there's an easier way to install unless you need the most recent version. (not sure what's in the repo compared to newest version)

You will want to go to the wiki (link at top of page) type synaptic in the search box. You'll see a link to 'synaptichowto' click on there. This explains how to install apps via synaptic. Notice the link in the page for adding repositories, also important.

If you don't have any internet access on the machine it won't work. I believe ndiswrapper is on the disk (could be wrong). put your disk back in the cdrom and open up synaptic. Click reload and look for ndiswrapper.

You may also want to look [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=85378&highlight=ndisgtk") for a graphical interface to ndiswrapper. Again, you will need some kind of internet access though to access the repositories and install this app.

---

### Post by teaker1s on 2005-11-10
if you want to compile you will also need 'build-essential' and a suitable compiler

---

### Post by Tha1 on 2005-11-10
I did it!! it was like **rcerreto** said. I only had to install make and it worked. But now when i try to install wpasupplicant with:

sudo apt-get install wpasupplicant

he gives me an answer saying that wpasupplicant could not be found. What am I doing wrong?? :???:
If worth notice,i have the latest stable release of Ubuntu and I'm trying to do this for a SpeedTouch121g as my wireless adapter.

---

### Post by RAOF on 2005-11-10
Works fine here.  It's in the universe repository, though.  Do you have those extra repositories enabled?  ([Here's a guide]("http://help.ubuntu.com/starterguide/C/ch02.html"), if you don't)

---

