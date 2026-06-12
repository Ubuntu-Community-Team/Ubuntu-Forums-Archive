---
title: "applications gone after install?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Nico0020 on 2009-10-30
Since the official upgrade method caused me MANY problems this time around I decided to just do a fresh install on the partitions.  My home folder is a separate partition than my ubuntu install so I did not have to worry about loosing my stuff.  

Anyways after the install, my programs in my applications list are all gone.  If I go into my home folder and do ctrl-h I can still see the hidden folders for the applications.  are the settings just saved in my home where the actual programs are saved in my ubuntu partition?  Is there anyway to generate a list of what I already had an reinstall it all automatically?  

Also when I view the hidden folders in my home folder I can see alot of old programs I dont use anymore.  Is there any way to see what all is installed and clean up all that stuff, or do I just need to delete them manually?  Nothing shows up when I use the janitor which I thought would help.  

Finally programs that were installed not from the repos but from debs I got from websites, whats is the easiest way to purge those (for example I tried out the desktop hulu player and want to remove it, but dont know how)

I know a lot of questions, but I am still a newbie lol.  Thanks!

---

### Post by cgb on 2009-10-30
The files in your home folder are just the configuration files, this does not mean the applications are installed.  If you did a fresh install you will need to install these applications again.  Also, if some of these configuration files are no longer needed it is definitely safe to just delete them now since the applications do not even technically exist on your computer.  Dont think there is any way to automatically install all these applications just based on what you have in the home folder but someone might prove me wrong.

---

### Post by mikewhatever on 2009-10-30
You've done a clean install, so all the non-default programs are not in the menu because they aren't installed. Installing them should be easy if they were from the repositories. The hidden folders you see in your home directory are not where programs get installed, these are just configuration folders. You can safely delete those you don't use.

---

### Post by Nico0020 on 2009-10-30
cool, thanks for the quick replies.  Glad to hear I can clean that stuff out.  I have read a few times that people use a script that makes a list of the stuff they installed before they do a clean install that makes it easy to get all the stuff back on your system you had before, but you have to use it before the install.  anyone know anything about that for the next time I might have to do a clean install?

---

