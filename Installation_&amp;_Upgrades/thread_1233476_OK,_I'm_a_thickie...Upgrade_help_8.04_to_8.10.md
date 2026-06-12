---
title: "OK, I'm a thickie...Upgrade help: 8.04 to 8.10"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by SlayBeau on 2009-08-06
I am running Heron on a Dell Mini that I bought last year for fieldwork duty in south India.  I mostly love it, but enough issues have presented themselves that I wish to upgrade to Ibex, then to Jackalope, etc.  I had planned on doing this while in India, but my internet connection was spotty at best.  Here's my problem:

Based on the Upgrade Notes at [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades), I had at one time changed my admin preferences to show normal releases when available: eg.Start System/Administration/Software Sources...click on Updates tab, etc.  I had done this in India, but fell so far behind on normal updates that I never had a chance to get them all (a requirement for upgrading the distro, yes?).  Once I finally had caught up with the updates and tried to get the new distro, I couldn't.  No matter how often I update, I never get the message that a new release is available.  When I try to change software sources, this is all I get:

[IMG]http://farm4.static.flickr.com/3455/3795671635_5b59104652.jpg[/IMG]

As you can see, I no longer even get the option for release upgrades, or tabs for Ubuntu Software or Statistics.

I have no problem admitting that I'm a bit thick on this one.  I'm not quite a Linux newb, but obviously enough of one to be stymied by this.

System is a tiny Dell Mini, 16GB, no cd drive option to do a fresh installation without getting my hands on an external.  Any ideas?

---

### Post by slakkie on 2009-08-06
If you have a internet connection do this:

```

echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
sudo aptitude update && sudo aptitude safe-upgrade

# Do the actual upgrade
sudo do-release-upgrade
# Or 
sudo update-manager

```

Now you will enter the upgrade process to 8.10 and then you can upgrade to 9.04

This is the sources.list I have on 8.04, maybe it helps.

```

deb http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://nl.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy universe
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://nl.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by SlayBeau on 2009-08-07
Once I typed in sudo update-manager I got a parsing error.  Can you still lend a hand to a doofus?  Sorry for the scrolling below:

root@root:-~$ sudo update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 109, in <module>
    app.main(options)
  File 
"/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 
1067, in main
    self.check_metarelease()
  File 
"/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 
1054, in check_metarelease
    self.options.use_proposed)
  File 
"/usr/lib/python2.5/site-packages/UpdateManager/MetaReleaseGObject.py", 
line 47, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelase, useProposed)
  File 
"/usr/lib/python2.5/site-packages/UpdateManager/Core/MetaRelease.py", 
line 70, in __init__
    parser.read(self.CONF)
  File "/usr/lib/python2.5/ConfigParser.py", line 267, in read
    self._read(fp, filename)
  File "/usr/lib/python2.5/ConfigParser.py", line 490, in _read
    raise e
ConfigParser.ParsingError: File contains parsing errors: 
/etc/update-manager/release-upgrades
    [line 10]: 'Prompt-normal\n'

---

### Post by slakkie on 2009-08-07
You entered Prompt**[COLOR="Red"]-[/COLOR]**normal, should be Prompt**=**normal

edit the file

nano /etc/upgrade-manager/release-upgrades

and correct the mistake

---

### Post by SlayBeau on 2009-08-07
OK, I'm more than a little lost now.  I see my mistake, but given the tiny size of the mini's screen i can hardly fault myself for mistaking a [COLOR=Red]= [COLOR=Black]for a [COLOR=Red]-[COLOR=Black].  But as for the editing...

I'm tinkering with config settings, right?  So I'd need to use gedit to open the file (I don't recognize 'nano' as a command function, so it must be part of the file name, or am I even thicker than I originally thought?).  However, this is a function I never used in the field since I couldn't afford to botch things beyond my own meager abilities.  So when I enter "sudo gedit [file name]" I get two empty gedit tabs, viz:

[IMG]http://farm4.static.flickr.com/3550/3798196478_c7e54b131f_m.jpg[/IMG]

Uh...do I simply enter in the proper command line, i.e. 
[/COLOR][/COLOR][/COLOR][/COLOR]echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
sudo aptitude update && sudo aptitude safe-upgrade

[COLOR=Red][COLOR=Black][COLOR=Red][COLOR=Black]or is there more to it than that?
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by drs305 on 2009-08-07
> **SlayBeau said:**
> 
I'm tinkering with config settings, right?  So I'd need to use gedit to open the file (I don't recognize 'nano' as a command function, so it must be part of the file name

nano is a text editor that can run in terminal. If you use it, you will eventually wonder how you get out of it. CTRL-X, then "y" or "n" to save/not save and exit. 

> 
So when I enter "sudo gedit [file name]" I get two empty gedit tabs
When opening an editor you must provide the full path as well as the command unless you are already in the correct directory/folder. If the file doesn't exist in the current folder and you haven't told the editor where the file is, the editor will open a new file with the same name in whatever directory you issued the command.
So the proper way of opening gedit in this case would be:
```
gksudo gedit /etc/upgrade-manager/release-upgrades
```

> 
Uh...do I simply enter in the proper command line, i.e. 
```
echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
sudo aptitude update && sudo aptitude safe-upgrade
```

Yes. The first line will automatically add the line  "Prompt=normal" to the file /etc/update-manager/release-upgrades

---

### Post by slakkie on 2009-08-07
It will add the line, but the format of the file is corrupt.

You could remove the -a flag from the tee command, which will also fix the error, but you will lose the comments in the release-upgrades file.

```

echo "Prompt=normal" | sudo tee /etc/update-manager/release-upgrades
sudo aptitude update && sudo aptitude safe-upgrade
sudo update-manager

```

---

### Post by snowpine on 2009-08-07
Hi SlayBeau, are you using the special Dell-branded Ubuntu that comes pre-installed on the Dell Mini? If so, 8.04 is the newest version available; Dell has chosen to stick with the LTS (long term support) version that is supported through April 2011.

Many Dell Mini users (including myself) have decided to overwrite this "Dellbuntu" with a newer release. You will have to do a fresh reinstall, and how well it works depends on which model you have. Jaunty works okay with my Mini 9, but I have heard the Mini 10 and 12 have some graphics issues with Jaunty that you may want to research if applicable.

If you installed "regular" 8.04 yourself, please disregard this post. :)

---

### Post by SlayBeau on 2009-08-07
> **snowpine said:**
> Hi SlayBeau, are you using the special Dell-branded Ubuntu that comes pre-installed on the Dell Mini? If so, 8.04 is the newest version available; Dell has chosen to stick with the LTS (long term support) version that is supported through April 2011.




Yargh!  Once upon a time I swore I would never use Dell again, but the dang Mini was just what I needed for fieldwork and the deal was just too good (my wife swears by Dell and needed a new laptop herself.  Anyway, enough meaningless details about me...

I *do* have Dellbuntu, and my only serious issue with it is the cursor jumping when text editting.  I am writing my dissertation, so I do a LOT of text editing.  And it has surpassed annoying and moved on into blow my brains out.  What little research I was able to do on the bug while in India suggested that Jackalope had fixed that issue if Ibex had not.  Hence the desire to update. I wanted to try to update because I have a preternatural fear of data loss during a fresh install, and these are my dissertation notes I am talking about after all.

Should I chose to fresh install (or do you know of a cursor jump fix for Heron), what would be the best way to go about it on a tiny, rom-less laptop?  The last time a experimented with Ubuntu I burned an iso onto a cd and installed from that.  Not really an option on the Mini (and it is a 9, so...)

Finally, I thought that maybe Dell had, in fact, "frozen" the Mini to 8.04 because it was the LTS.  The I thought, "why would they do that?  Linux is meant to be tinkered with and improved constantly.  If I wanted firm stability I would have stuck with the dark overlords."  Effing Dell.

---

### Post by slakkie on 2009-08-07
I dunno, but can't you point your repo's to the official Ubuntu repo's and go from there?

---

### Post by snowpine on 2009-08-07
I am not sure if the package gsynaptics is available in 8.04? It is a GUI application to set the touchpad preferences. If you can install it (sudo apt-get install gsynaptics) you can easily change the setting to disable the trackpad while you're typing.

Should you decide to switch to 9.04, lots of reading material here: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

As far as Dell's decision to stick with 8.04, I won't try to defend it, but I will point out that Dell is primarily a hardware company and probably doesn't have the resources to develop a new OS every 6 months.

---

### Post by snowpine on 2009-08-07
> **slakkie said:**
> I dunno, but can't you point your repo's to the official Ubuntu repo's and go from there?

That would be a recipe for disaster, since the Dell version has a completely different kernel and architecture (lpia), as well as a number of non-standard packages developed specifically for/by Dell (the user interface, for one thing).

---

### Post by slakkie on 2009-08-07
then you are ******** indeed.

---

### Post by SlayBeau on 2009-08-07
No, they certainly don't.  but since Linux is a user supported and developed OS, why would they even try.  If they are going to offer it as an option, do so with a caveat emptor clause and leave it at that.  Stupid Dell.

Also, thanks for the ubuntimini link.

---

### Post by snowpine on 2009-08-07
I understand your disappointment completely (I deleted Dellbuntu 8.04 from my mini within 15 minutes) but also feel obligated to point out Ubuntu 8.04 Hardy Heron is an excellent operating system with full support through April 2011. If they sold the mini with 9.04, it would only be supported through Oct. 2010.

---

