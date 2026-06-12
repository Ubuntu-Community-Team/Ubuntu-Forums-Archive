---
title: "[SOLVED] Amarok sound issue, very annoying..."
date: 2008-08-11
forum: General Help
---

### Post by lovhorror on 2008-08-11
Alright, so when I was running amarok, didn't touch a thing, and it crashed. So I start it back up and it says > Amarok currently cannot play MP3 files.

So I click the button that says install mp3 support and it asks for my password, I give it and it does some stuff before telling me 
> 
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

So I click Okay. Now it says > There was an error installing MP3 support. You need to install the package "libxine1-ffmpeg" manually.

So I open a terminal and do the following...

> cory@lovhorror-desktop:~$ sudo apt-get install libxine1-ffmpeg
[sudo] password for cory: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.11.1-1ubuntu3) but 1.1.11.1-1ubuntu3.1 is to be installed
E: Broken packages
cory@lovhorror-desktop:~$ sudo apt-get install libxine1-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I ask you, wise people of the Ubuntu help forums, what the hell is wrong with this situation?

---

### Post by Gatesgamer33 on 2008-08-11
[SIZE="2"][FONT="Lucida Sans Unicode"]Perhaps you should go into synaptic and "Force Version"?[/FONT][/SIZE]

---

### Post by lovhorror on 2008-08-11
I'm not familiar with this (I've never heard of Force Version) and I don't undestand what you mean. Can you be a bit more specific?

---

### Post by lucaa on 2008-08-12
hi lovhorror, hi everybody, here's how it is:

the libxine1-bin has been upgraded to a new version, namely 1.1.11.1-1ubuntu3.1 by a security update a couple of days ago, but not its plugins too, which is the case of libxine1-ffmpeg -- the one used to play mp3 files in amarok.
libxine1-ffmpeg is still in version 1.1.11.1-1ubuntu3 which requires libxine1-bin version 1.1.11.1-1ubuntu3 **exactly**, not higher. That is why you cannot install libxine1-ffmpeg anylonger and libxine1-bin is at the newest version.

The only solution to get this working through the package manager is to force the version of libxine1-bin to a lower version (err, I seem to not find that button in adept but in synaptic you just select the package in the list and go to Package -> Force version), the problem stays though since this wants to uninstall some other programs, amongst which amarok too :(. You could uninstall them as required and then reinstall them once libxine1-bin is at the desired version.

The only clean solution is to wait until libxine1-ffmpeg gets updated too (or pressure the developers to do it faster -- as a developer though, I wouldn't advise you to do that :P )

Happy coding / using ubuntu

---

### Post by lucaa on 2008-08-17
Here's how I fixed it in the end (a couple of minutes ago):

I went to repository management (File -> Manage Repositories in Adept and Settings -> Repositories in Synaptic) and checked, in the "Updates" tab, the "Important security updates" checkbox which had a pretty odd state (not checked but not unchecked either). Reloaded package list and voila, libxine-ffmpeg 1.1.11.1-1ubuntu3.1 was there, ready to install and play mp3s in my Amarok.

Update: make sure that in the "Third-party software" tab you have "Important security updates" checked (anyway, the setup you had when you got the first update, the one for libxine1-bin should do it).

Now why where the repositories configs like that on my machine, I wouldn't be able to say...


Happy listening! 
And join the amarok users group on last.fm: [http://www.last.fm/group/Amarok+Users](http://www.last.fm/group/Amarok+Users)

---

### Post by Milambar on 2008-08-22
Awsome. I'd been bashing my head against this problem myself for the past WEEK.

Your solution solved it perfectly.

<3

---

### Post by Milambar on 2008-08-22
Double post, my apologies.

---

### Post by meeotch on 2008-09-17
I hate to post without adding any real value... But holy ****, you rock!  This was the only answer I was able to google, and it fixed me right up.

As an aside: if linux is ever going to make it on the desktop, it's going to have to stop cryptically breaking itself for cluebies like me who aren't doing anything more complex than hitting the "update" button to stay, er, up-to-date.

---

### Post by mb_webguy on 2008-09-17
> **meeotch said:**
> As an aside: if linux is ever going to make it on the desktop, it's going to have to stop cryptically breaking itself for cluebies like me who aren't doing anything more complex than hitting the "update" button to stay, er, up-to-date.

You mean unlike in Windows, when an automatic update of Office caused my installation of Windows to crash repeatedly until I booted into safe mode and did a system restore, then had to repeat the process the next day after the system reinstalled the update -- which I had no clue was causing the problem until I started reading posts online of other people having the same problem?

---

