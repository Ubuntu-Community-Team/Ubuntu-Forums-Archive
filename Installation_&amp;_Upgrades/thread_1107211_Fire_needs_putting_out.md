---
title: "Fire needs putting out"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Langstracht on 2009-03-26
I hope someone can tell me what's going on here and, perhaps more importantly, how to fix it.

I have installed Firefox 3 on three occasions.  Each time, to my knowledge error free.

And, indeed, Synaptic confirms that 3 is installed.  And still when I start FF, whether by icon or command line, I am greeted with version 2.

Help!  Someone please ...  Anyone ....

---

### Post by LiamWilson on 2009-03-26
Maybe it is actually 3, but it's just telling you it's 2? Just an idea..

---

### Post by mikey.duhhh on 2009-03-26
Uninstall firefox 3.  Uninstall firefox 2.  reinstall firefox 3

test to see if there are any other firefox installations by typing firefox at the command line.  ```
sudo killall firefox
``` if something shows up.  
Then try```
 sudo find / -name firefox*
```.  If something is still there complain again here.

---

### Post by Langstracht on 2009-03-26
oh that this were simple.

I un-installed "3" and supposed that "2" would show up now as installed - and therefore now uninstallable - in Synaptic.  Alas not.  Synaptic (still) shows no icons for "2".

And, when I went to the system to open Firefox so as to report this turn of events ... it's "not there".

And so I have had to install 3 again to be able to send this message.

Back to the advice - uninstall 3.  No prob - it shows up on Synaptic.

                   - uninstall 2.  Sorry, but how?

---

### Post by Langstracht on 2009-03-26
Oh ... and I should have said, the 3 that I had to install again ... shows up  as 2 in "About Mozilla Firefox"!

---

### Post by ajgreeny on 2009-03-26
I can not see why it should make any difference, but nevertheless, try renaming your *~/.mozilla* folder (hidden in your home) as *~/.mozillaold* and open firefox again to see if it is still telling you it's version 2.  Could be there is something corrupt in the config that causes the problem.

---

### Post by Langstracht on 2009-03-26
O.k.

Shut down Firefox, re-named mozilla to mozillaold, started up FF again.

Asks me where I want to import profiles from ... and then proceeds to welcome me to Firefox 2.  Version subsequently confirmed by "About Mozilla Firefox".

So, understandably I think, (although it changes nothing of import) I re-named mozillaold back to mozilla.

???

---

### Post by tech_penguin on 2009-03-26
What is the output of the command:

ls -la /usr/bin/firefox*

---

### Post by Langstracht on 2009-03-27
~$ ls -la /usr/bin/firefox*

lrwxrwxrwx 1 root root 20 2007-02-19 08:29 /usr/bin/firefox -> /opt/firefox/firefox
lrwxrwxrwx 1 root root 31 2009-03-26 15:22 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.7/firefox.sh
lrwxrwxrwx 1 root root 11 2009-03-26 15:22 /usr/bin/firefox.ubuntu -> firefox-3.0

---

### Post by ajgreeny on 2009-03-27
I suspect ypu have in the past installed a version of firefox other than from the repos which is showing in the line
```
lrwxrwxrwx 1 root root 20 2007-02-19 08:29 /usr/bin/firefox -> /opt/firefox/firefox
```
suggesting an old version in /opt as well as the new version in /bin.  If I'm right you need to remove the old version, but how you do that will depend on how it was installed in the first place, I think.

---

### Post by Langstracht on 2009-03-27
I may well have done an "ill-advised" installation.  But it would have been a l-o-n-g time ago and I have no idea how.

So!  I certainly hope someone knows how to get rid of it because I sure don't.

---

### Post by ajgreeny on 2009-03-27
Do you remember installing from a tarball or perhaps from a .bin file from mozilla itself?  I am not sure how the site presents the user with downloads though I am aware that they come as an archive.  You could try simply renaming the binary in */opt/firefox/firefox* as */opt/firefox/firefox~* and seeing if that stops the old version starting.  It would at least be a workround, even if it doesn't really solve the underlying problem.
```
sudo mv /opt/firefox/firefox /opt/firefox/firefox~
```

---

### Post by Langstracht on 2009-03-27
I'm sorry to say that I haven't the foggiest idea how I (indeed if I - as opposed to clicking an icon) installed this rogue version.  You'll have seen the folder is dated February 19, 2007.  Heck I can't even remember March 19, 2009!

However, that said, I did as you suggested and changed opt to ~.  Result?  Trying to open Firefox results in the not-at-all-helpful "Could not launch application.  Failed to execute child process "firefox".  (No such file or directory)".

Evidently, problem or not, my machine is determined to go to the opt folder.

Happily - I think - erasing the "~" has returned me to the original problem.

Any thoughts.

---

### Post by ajgreeny on 2009-03-27
Ok, I'm beginning to get the drift, and though it may end up leading you up the garden path again, have a look at this site which talks about the install of FF in ubuntu using the tarball from mozilla, and also shows how to remove it and then reset the link you have in /bin to the binary you did have in opt/firefox/firefox.
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
Good luck, I hope this helps this time!

---

### Post by Langstracht on 2009-03-28
Thanks for the link.

I've read ... and read ... and read it and I'm not at all sure how to interpret it.

Do you think I should be doing/trying the last two steps (i.e. Delete the Firefox directory and Move your old profile back to its place) or what would you recommend?

I know you don't have access to my machine but your guess will be a whole lot more likely to be the right one than mine.

Sorry for my stupidity and ESPECIALLY for your continuing interest.

---

### Post by Langstracht on 2009-03-28
I meant to especially THANK YOU for your continuing interest.

(gulp!)

---

### Post by Langstracht on 2009-03-28
Just this minute received notification from my Update Manager that firefox and firefox 3.0+nobinonly v3.08 (together with 8 library updates and 2 xulrunner) is ready for installation.

Whaddya think?  Letting them install is going to make matters even worse?  Or potentially fix the problem?

I won't let the installation proceed until I hear from you.  And maybe not even then ... depending on what you respond.

---

### Post by ajgreeny on 2009-03-28
If it were me I would do the part of the procedure shown below, then reinstall firefox 3 with synaptic or apt-get and hopefully all will be well again.  Let's face it, it will not make matters any worse.  It does show the difficulties you can sometimes get into by using unusual methods of installation in a system that has its own dedicated manner of doing such things.

**Removing**

 If for some reason you want to undo the installation and revert back to the standard Ubuntu Firefox, here's how: 

[LIST]
[*]Restore the symbolic links: sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
[*]Restore your old profile: I'm not sure this will be needed as you may already ghave got rid of the old backup folder and will not be able to do this.  Give it a try anyway, you should be able to see if you have the backup folder made all that time ago when you installed the unusual way, and the worst that can happen is that you lose your bookmarks, so make sure you do a backup of them before you do anything to remove any ~/.mozilla foldersmv ~/.mozilla ~/.mozilla.manual.download
mv ~/.mozilla.backup ~/.mozilla
[*](optional) Delete the firefox directory: sudo rm -r /opt/firefox
[/LIST]

---

### Post by Langstracht on 2009-03-29
Sorry I wasn't able to act on your advice yesterday, too busy with the local Earth Hour initiative.

However first thing today I keyed all the commands - all working except, as you predicted, "mv ~/.mozilla.backup ~/.mozilla".

And then ... and then ... clicking on the FF icon ... opened up 3.07 and welcomed me.  And I didn't even lose the bookmarks!

I've now also done yesterday's updates.  And so life is good once more.

And all thanks to you.  Thank you SO MUCH for "holding my hand" in this.  I was totally stumped.  Still am actually.  But the problem is gone.  

Thanks.  And cheers!

---

### Post by ajgreeny on 2009-03-29
Great!  Glad it all worked eventually.  Whether this was the easiest way to get where you wanted I really don't know, but you're there now, so let's hope things now keep working.

---

