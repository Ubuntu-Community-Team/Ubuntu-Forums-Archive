---
title: "Kiba dock Intrepid Ibex?"
date: 2008-11-05
forum: General Help
---

### Post by saggitheman on 2008-11-05
Hi.

I'm using Intrepid Ibex, but i can't get Kiba-dock to work. Anyone knows how to. Answer in an easy way pleas!?

---

### Post by paul.roberts20 on 2008-11-05
I just followed a guide on these forums, and it's working fine for me, i'll post a link asap.

EDIT:

here is the link
[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")

---

### Post by saggitheman on 2008-11-15
I'v done that, but when i types kiba-dock in terminal i get this messege...
What can i do?


'root@Dell:/home/aleksander# kiba-dock

** (kiba-dock:26603): WARNING **: Error (plugin-loader.c @ line 665):
	Failed to open Plugin Directory '/usr/local/lib/kiba-dock/global_plugins': Error opening directory '/usr/local/lib/kiba-dock/global_plugins': No such file or directory

	For a core dump, run kiba-dock with --g-fatal-warnings

---

### Post by MasterPoulos89 on 2009-04-03
Hello.
I have been using the kiba-dock for a couple of months now and been using Linux for at least a year now. Since I'm learning more and more about Linux I thought why not make a script for myself that downloads the latest kiba-dock and compiles and installs it. So thats what i did and i will upload it to this post for those who don't know how to compile or those who just want a quick way to install kiba-dock.

Just download and extract the tar file in a directory where you want to leave it. Do not delete it after install because if you want to update it you will want to uninstall it first and you need the source file to uninstall it.

To install just double click the "Install Kiba-Dock" file and select run in terminal. Then you may need to type your password when asked. When its finished look in accessories and you should find kiba-dock and kiba-dock settings.

To update just click the "Update Kiba-Dock" file and it will uninstall kiba-dock and download the most updated version and compile and install.

I added an x64 bit script because I just realised there is a proper way to install it on x64 bit. After extracting the file you will see an x86 and x64 folder. If you don't know the difference just choose x86. It should still work the same. It has for me anyway.

This script now also installs the akamaru folder in jaunty but it gives a message "auto config not using gettext" even if gettext is installed. It still installs though.

Thats All......Hope this helps.

---

### Post by MasterPoulos89 on 2009-04-03
Just like to add You still need to add the start up session for kiba dock manually. To do so just go to preferences-sessions and click add, name it anything you want and where it says command type: kiba-dock

no caps in the command

---

### Post by MasterPoulos89 on 2009-05-14
This script also works in Jaunty but the 'akamaru' folder doesn't install. Kiba-Dock still seems to work exactly the same so its not a big deal but I can't see why that part wont compile.

---

### Post by MasterPoulos89 on 2009-05-26
I updated the script to install the "akamaru" in jaunty but it gives a message "autoconfig not using gettext" even if gettext is installed. It installs anyway so I don't know if it matters.

If anyone knows then help out.

Also many talk about these crazy features that I never saw kiba-dock do. maybe someone knows why it can't be done any more or is there something missing?

---

### Post by steigerjb on 2009-05-26
> **MasterPoulos89 said:**
> I updated the script to install the "akamaru" in jaunty but it gives a message "autoconfig not using gettext" even if gettext is installed. It installs anyway so I don't know if it matters.

If anyone knows then help out.

Also many talk about these crazy features that I never saw kiba-dock do. maybe someone knows why it can't be done any more or is there something missing?

does this help you any MasterPoulos89 ?:
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

Maybe you can figure out what mattgaunt is doing different from you and you can update your script.

Then post on the thread :D

---

### Post by MasterPoulos89 on 2009-05-26
> **steigerjb said:**
> does this help you any MasterPoulos89 ?:
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

Maybe you can figure out what mattgaunt is doing different from you and you can update your script.

Then post on the thread :D


mattgaunt's post is actually the one I used to make my script. I saw the youtube vid from mikibg's post but I don't know if he is claiming that his works like that.

My script does everything the post says to do. I want someone to confirm that they know that Kiba-Dock has such features.

I guess most of the features are there. The stack feature I think is when a folder and its sub folders show in the dock similar to osx except when you try to use it it crashes and prob few others.......I don't know how the icons are supposed to fly around the desktop but that doesn't bother me. But if they are possible features I would still like to know how to get them working.

---

### Post by MasterPoulos89 on 2009-07-04
All the kiba-dock problems a had in this tread are now solved.

See this thread [http://ubuntuforums.org/showthread.php?p=7551073](http://ubuntuforums.org/showthread.php?p=7551073)

For my new script see this thread [http://ubuntuforums.org/showthread.php?t=1203969](http://ubuntuforums.org/showthread.php?t=1203969)

---

### Post by lonewaster on 2010-05-08
> **MasterPoulos89 said:**
> Hello.
I have been using the kiba-dock for a couple of months now and been using Linux for at least a year now. Since I'm learning more and more about Linux I thought why not make a script for myself that downloads the latest kiba-dock and compiles and installs it. So thats what i did and i will upload it to this post for those who don't know how to compile or those who just want a quick way to install kiba-dock.

Just download and extract the tar file in a directory where you want to leave it. Do not delete it after install because if you want to update it you will want to uninstall it first and you need the source file to uninstall it.

To install just double click the "Install Kiba-Dock" file and select run in terminal. Then you may need to type your password when asked. When its finished look in accessories and you should find kiba-dock and kiba-dock settings.

To update just click the "Update Kiba-Dock" file and it will uninstall kiba-dock and download the most updated version and compile and install.

I added an x64 bit script because I just realised there is a proper way to install it on x64 bit. After extracting the file you will see an x86 and x64 folder. If you don't know the difference just choose x86. It should still work the same. It has for me anyway.

This script now also installs the akamaru folder in jaunty but it gives a message "auto config not using gettext" even if gettext is installed. It still installs though.

Thats All......Hope this helps.

thanks for the little bit of bishy bashy there man, very useful.
I fall into the "too lazy to do it manually/by self" :lolflag:

if there was a +rep system on ubuntuforums.org then i would +rep you:guitar:

cheers!!

***-darksider-***

---

