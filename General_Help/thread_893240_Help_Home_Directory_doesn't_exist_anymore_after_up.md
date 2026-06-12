---
title: "Help: Home Directory doesn't exist anymore after update from 7.10 to 8.04"
date: 2008-08-18
forum: General Help
---

### Post by NuxIT on 2008-08-18
Hi, I'm having problems after upgrading from 7.10 to 8.04. I had this issue reported here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/249340]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/249340")

I managed to get around this by running:
sudo dpkg --configure -a

I ran this command after hitting alt-ctrl-f1 and logging in to a terminal using my username styles. Now, when I try and log in it gives me error:
"Your home directory does not appear to exist. Do you want to log in with the / (root) directory as your home directory?"

If I say yes it just gives me a bunch of errors and goes back to the ubuntu splash login screen. I tried failsafe boots and telling it to repair broken packages but nothing is working. I also tried booting into gnome instead of KDE but no workie.

I don't know what happened. Can anyone help? I did manage to get into the new 8.04 load with my styles username a few times after running the sudo dpkg --configure -a command. It loaded the desktop correctly and everything with my styles username.  But then I was trying to get my atheros wireless working and that's when it lost my home directory again. Thanks for any suggestions/ideas.

EDIT:
I think I messed it up more by doing this:
sudo mkdir /home/styles
sudo chown -R styles:styles /home/styles

I can now get into the GUI desktop but now my files are gone. If I do a locate styles it will show all my old files but they aren't actually there. Any ideas? Did I loose all my files?

EDIT (AGAIN):

Well this is VERY strange. I rebooted multiple times and now all the sudden my old desktop showed up with all the files.. What the heck! I guess I'll back up my files while I have a chance. I guess I should have been happy with my working wireless in 7.10 with WEP mode. I wanted WPA to work and thought 8.04 might do the trick with my Thinkpad t60 with atheros wireless card. Well, I've tried a lot of stuff to get the wireless working and now I can't even revert back to a working WEP connection. Kinda sucks but at least I didn't loose all my files.

---

### Post by prince_niceguy on 2008-08-19
can you post your /etc/fstab file and also which partition your home directory was installed on. Was it same partition as the root partition or was it another partition in itself?

---

