---
title: "Very New"
date: 2005-11-07
forum: General Help
---

### Post by ESPOiG on 2005-11-07
im new... well not very new to linux... i have used linux at times but never really got the hold of it.

i wuld like yo know how exactly do i update a program like... say Firefox... say it is version 1.0.6 and 1.0.7 is the one i want to replace it with... in windows (sorry) but u can unistall and then install the newer version of it over the top of sum older files and basically replace.

but how do i do sumtin like that in linux... cuz im stumped if anything. so what im saying is how do i unistall a program and then install the newer version of it

or even better like i said im new where shuld i install programs... eg (prog files) cuz im confused and wuld like to know thx

ill be askin heaps of q's im guessing

---

### Post by varunus on 2005-11-07
Well, the standard Ubuntu way to install programs is the Synaptic Package manager.

Ubuntu and Windows take two different approaches to installing program.  Ubuntu uses what's called a repository; its an online database of a bunch of programs that can all be downloaded and installed with one click.  Try going to Applications->Add Applications, and you'll see what I mean; all of these programs are in the repository.

However, not all programs are shown there.  For full control, go to System->Administration->Synaptic Package Manager.  This will show all of your packages along with the ability to upgrade them when a new version is put into the repository.

The Ubuntu backports project is the project responsible for keeping the newest packages in Ubuntu.  However, I don't think the Breezy backports project is yet underway, so you'll have to wait...you can always install things manually/the windows way if you want to, but then your system gets a lot more cluttered...Synaptic is just so much neater, since you can uninstall everything from there too.

What program are you looking for the newest version of?  Firefox is 1.0.7 on my Ubuntu stock breezy install...

Also, a question...have you enabled the extra repositories?  (Universe, Multiverse, etc)?  These let you have a *lot* more software in the respositories, including most codecs.

You may want to try Automatix or Easy Ubuntu, they automate a lot of the most common software installs (check them out in the "customization tips and tricks" section of the forum).

---

### Post by steve.horsley on 2005-11-07
Replacing firefox may not be that easy. I tried un-installing the stock firefox because I wanted to install the latest beta, but the synaptic package manager said I couldn't do that without uninstalling the entire ubuntu desktop. No thanks! So I installed a second version of firefox leaving the old one there.

This is how I did it.

Download the firefox tar.gz. The very latest right now is [http://download.mozilla.org/?product=firefox-1.5rc1&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-1.5rc1&os=linux&lang=en-US)
which is v1.5 release candidate 1.

Unpack this file:

$ tar xfz firefox-1.5rc1.tar.gz

This creates a directory called firefox. Copy it to /opt, an action that requires root privilege:

$ sudo cp -r firefox /opt/firefox1.5-rc1

Now you can delete the local directory you just unpacked:

$ rm -rf firefox

**Make sure that no other instances of firefox are running before you continue**.
Now run the new firefox as root, just the once. I understand that It must do this to have rights to create some extra files in /opt...:

$ sudo /opt/firefox1.5-rc1/firefox

Exit that and try as a normal user:

$ /opt/firefox1.5-rc1/firefox

If you like, you can create a launcher for this, or edit the properties of the existing launcher on the toolbar. 

Or you can replace the symlink in /usr/bin to your old firefox with a link to your new one. This will make all the other launchers and application links to firefox use the new version. First, just have a look and see that the firefox file in /usr/bin is a link to the actual application that is located elsewhere:

$ ls -l /usr/bin/firefox

Delete the old link:
$ sudo rm /usr/bin/firefox

Create the new link
$ sudo ln -s /opt/firefox1.5-rc1/firefox /usr/bin/firefox

Hope that all makes sense

Steve

---

### Post by varunus on 2005-11-07
The ubuntu-desktop package is not the whole desktop.  It is, if you look at it in synaptic, just a meta-package; it installs the basic desktop, and can be removed safely afterwards.

So yes, you can remove firefox...I'm in fact running on a system without ubuntu-desktop right now (I got cpufreqd instead of powernowd from synaptic, uninstalling the desktop package).

---

### Post by steve.horsley on 2005-11-07
[QUOTE=varunus]The ubuntu-desktop package is not the whole desktop.  It is, if you look at it in synaptic, just a meta-package; it installs the basic desktop, and can be removed safely afterwards.

So yes, you can remove firefox...I'm in fact running on a system without ubuntu-desktop right now (I got cpufreqd instead of powernowd from synaptic, uninstalling the desktop package).[/QUOTE]

I just looked at the properties of ubuntu-desktop in synaptic, and see exactly what you mean. It's just a set of requirements with no content of its own. Thanks for the tip.

Steve

---

