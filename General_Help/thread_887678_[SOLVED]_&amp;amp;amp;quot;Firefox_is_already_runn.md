---
title: "[SOLVED] &amp;amp;amp;quot;Firefox is already running&amp;amp;amp;quot; even after reboot"
date: 2008-08-12
forum: General Help
---

### Post by Piraja on 2008-08-12
Dear all,

I keep getting the error message when I try to open Firefox:

[INDENT]**Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.**[/INDENT]

This happens even after rebooting the system. 

What have I done to deserve this? That is, what did I do previously? Well, I succesfully (through trial and error) created a separate home partition just a few hours ago (see the excellent Psychocats tutorial: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)) to my external USB hard drive (500GB HDD containing one ntfs partition and two Linux partitions, i.e. Ubuntu Hardy at sdb4 and separate home at sdb2) plus the swap partition. I mean, the problem started after that latest endeavour. I have no idea whether it has anything to do with the problem. Maybe, since booting the older kernel does not help.

Another problem that I encountered at the same time is that "Add/Remove applications" started crashing after it reloads the latest package information. Just dies off. Neither Firefox nor the Add/Remove application are shown by using "ps -A" in terminal.

I had to boot into WinXP (on the internal HDD) in order to post this. That feels so bad for a fresh Ubuntu addict!

Any ideas?

---

### Post by Ryadt on 2008-08-12
Try ```
killall firefox
```
and then try re-launching firefox.

---

### Post by DJ_Peng on 2008-08-12
I've run into this before, especially if our cat unplugged the power strip from the wall or the circuit breaker tripped while I had Firefox open. Go into your profile folder and see if you have a file called .parentlock and if you do delete it and try launching Firefox. Sometimes if Firefox sees that file it won't launch again because it thinks you already have Firefox open. Which is dd, because I can be in Firefox and accidentally click on my launcher again and it will simply open another window.

---

### Post by lukjad on 2008-08-12
What I do is go to System->Administration->System Moniter. I then look for the Firefox process, select it and click end process.

---

### Post by aysiu on 2008-08-12
You can also try ```
killall firefox-bin
``` if *killall firefox* doesn't work.

---

### Post by Piraja on 2008-08-12
Thanks for your suggestions. I suppose it should be obvious that Firefox is not running after a reboot (or am I missing something here?), so that "killall firefox" gives just "firefox: no process killed".

The situation is actually quite interesting. It's not Firefox, after all, but the whole Gnome desktop seems messed up. Many applications, such as the graphical Add/Remove application (which I already mentioned) no not behave as they should (the other graphical Synaptic app works fine), or Seamonkey which I managed to install but which does not start at all. For example, if I try to open System > Preferences > Appearance, the theme thumbnails are laid over with big question marks and after a few seconds I get an error message (see below*). When I copy the error message and paste it into a Gedit document, I cannot save the text document into my home folder (see below**), but I can save it to the NTFS partition on the external HDD.

This said: Could it somehow be a file permissions issue? Making the separate home partition required some tweaking with regard to permissions; actually I think I made a mistake in editing the fstab file, but I could fix the problem and figure out the right permission settings (I think).

Or could the problems have begun when I (stupidly) fiddled around with a splash image tarball (I never learn not to do some impatient moves, as it seems): I copied grub-splahsimages into the NTFS partition and (my goodness you might say!) extracted one of them there... not really knowing if that would be harmless... and it just might be that it was not, because that was the first time I got the error message that I also received when trying to open System > Preferences > Appearance (see above, and below*).

I am actually writing this from my external HDD Ubuntu now (instead of the internal HDD WinXP or my Ubuntu laptop), but not from my own user home account (I figured out that I might try the "family account" instead). And it seems that here, at the other home account, everything works fine!

Well, perhaps I'll try to dig into the hidden files on my personal Home folder... Or rather, backup the personal files and just delete the account and recreate it from the scratch. Luckily I created another Administrator account before the problems started. But can I delete my own account, being the default user/administrator? Or perhaps I should just give up and reinstall Ubuntu. It's not such a big deal, since I created the separate home partition today and did the whole USB-HDD installation just a couple of days ago. Not much to lose, that is.

In any case, could it be that the idiotic messing around with the splashimage package caused the whole turmoil on my desktop?

___

* Error message: "The application "gnome-appearance-properties" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application." (There were also a "Details" section, I'll post it in another post soon... could not copy-paste and save it at my own user account).

** Hmm... I seem to have lost the screenshots and error messages, precisely because I could not save them. I will try again, though... so hang on if you will...

---

### Post by aysiu on 2008-08-12
It very well could be a file permissions issue. I would try ownership before messing with permissions, though (not everything in your home directory is supposed to have the same permissions, but they are supposed to be owned by you). ```
sudo chown -R *username*:*username* /home/*username*
``` By the way, it's very possible that Firefox is still running, even after a reboot, especially if Gnome is saving your session from last time. Please try ```
killall firefox-bin
```

---

### Post by Piraja on 2008-08-12
Thanks to all and very special kudos to aysiu! As you suggested, here's the magic spell that cleaned up the whole desktop environment:* 

```
sudo chown -R username:username /home/username

```

I never thought that e.g. Firefox could be up and running after reboot (well, the killall commands returned "no process killed"; perhaps this was also due to the ownership issue?).

Here is a little more information for those who might find this thread and aysiu's advice by searching for keywords or phrases, i.e. the error message I got (you other adventurers might want to copy-paste it for reference):

```
The application "gnome-appearance-properties" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application. DETAILS: No database available to save your configuration: Unable to store a value at key '/desktop/gnome/font_rendering/antialiasing', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/metacity/general/theme' set in a read-only source at the front of your configuration path

```

* To put it in more graphical terms, here's a screenshot (sorry, I seem to have pasted the error message twice into the text editor):
[http://www.aijaa.com/v.php?i=2519743.png](http://www.aijaa.com/v.php?i=2519743.png)

Cheers!

---

### Post by Piraja on 2008-08-13
Just one more thing...

[EDIT: I moved the followup question to a new thread, since this has nothing to do with the original title "Firefox is already running" etc. New question: [http://ubuntuforums.org/showthread.php?p=5579641#post5579641](http://ubuntuforums.org/showthread.php?p=5579641#post5579641).]

---

### Post by Mgiacchetti on 2008-08-13
> **aysiu said:**
> You can also try ```
killall firefox-bin
``` if *killall firefox* doesn't work.
blah thats what i meant   kudos

---

