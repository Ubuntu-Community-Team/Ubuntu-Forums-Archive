---
title: "unity, tends to lock-up, problem"
date: 2015-11-17
forum: Hardware
---

### Post by yonnie on 2015-11-17
Using Zotac Zbox nano and the latest 14.04 unity version (kick panel across the top and apps on left of screen?)  The wife likes to play the candy crush game on facebook, after an hour or so the system seems to lock-up.  Mouse moves around but can't select anything, keyboard is unresponsive, even pressing the off switch on nano does not start a shutdown sequence.  You have to hold the power switch down until the nano shuts down forcefully.  This has been an ongoing issue since installation many months ago, when did LTS14.04 come out?  Since then.  Just the unity seems to lock up, can't seem to resolve it.  Not totally sure if it's a lock-up as the mouse still moves.


I have another Zotac zbox nano running KDE, never have an issue, runs great.  I have other Zotacs running KDE and xubuntu, same problems as kde--none!:D

---

### Post by Dreamer Fithp Apprentice on 2015-11-17
Seems to me Unity is probably the culprit. It is a resource hog. Heck, KDE isn't light, but Unity is a supersize osmium anvil hung around your computer's neck.

I don't know if it is relevant on a Unity system, but I've gotten big performance boosts and dramatically reduced crashing/hanging/bogging down on 2 different systems by purging apt-xapian-index and manually rm'ing it's cache in  /var/cache. It didn't seem to break anything.

You might want to look at Lubuntu or even plain Openbox for a real lightweight system.

Some people here get real huffy about any hint the flagship product is less than perfect, but I calls 'em as I sees 'em.  Any of this may or may not help in your case, but I think it is worth giving thought to.

---

### Post by yonnie on 2015-11-18
I've been noticing it keeps saying things are up to date but at same time saying there are updates waiting.  Then I find it doesn't have room in /boot because it doesn't clean out the old stuff to make room for the new.  apt-get autoremove doesn't work sometimes along with many of the other suggested commands.  Pretty obvious the update mechanism does not work properly.

This system was chosen for my wife to use as it seemed the easiest to learn to use for her.  She couldn't seem to get KDE.  Lubuntu I use on all my older systems, it doesn't seem very stable with Office and printing controls.  This is most important feature for using Ubuntu in the first place is for the printing controls and printer support.  This machine is very important for printing forms and labels.

I'm a bit loathe to remove apt-xapian until I can understand more about it.  It sounds like a major part of the update mechanism.  Zbox nano seems to run very well on ubuntu, quite snappy, replacing an entire tower with a tiny little box the size of a 5-1/4" older style HDD.  I doubt I'll ever go back to buying towers, this small form-factor makes them obsolete.

Everything but this stupid candy crush game works well.  The OS is easy to teach, easier than win95. It would be nice to get a handle on what about candy crush causes the lock-up.  Possibly a script?  (mouse still moves)

---

### Post by Dreamer Fithp Apprentice on 2015-11-28
> **yonnie said:**
> when did LTS14.04 come out?Year '14, month 04. Ubuntu "version numbers" are really release dates. They put 'em out on schedule, ready or not.> **yonnie said:**
> I've been noticing it keeps saying things are up  to date but at same time saying there are updates waiting.
Exactly how does it say that? In a terminal enter```
sudo apt-get update
``` and enter your password. After it returns a prompt enter```
sudo apt-get dist-upgrade
```Post the entire output from both commands.> **yonnie said:**
>  Then I find it doesn't have room in /bootRunning out of drive space can cause all sorts of errors, often without useful, or even accurate, error messages. In a terminal enter```
df -h
```and post the output. Always check for this when you get weird errors that make no sense.
> **yonnie said:**
>  it doesn't clean out the old stuff to make room for the newExactly what old stuff are you speaking of? Old kernels and corresponding headers and so on? You can enter this in a terminal```
sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
``` and then enter your password or, if you have synaptic you can look them up and purge them with that. Just make sure you don't purge the one your are currently running. I think by default it is set to retain one or two old ones but you can change that or purge them manually.
> **yonnie said:**
> apt-get autoremove doesn't work sometimes along  with many of the other suggested commands.You'll need to post  the exact output of failing commands if anyone is to be able to suggest  why they aren't working. Some commands that might help:```
rm -f  ~/.xsession-errors.old
sudo rm -f /root/.xsession-errors.old
find ~/.thumbnails -xdev -type f -exec rm -f -v {} \;
sudo find /root/.thumbnails -xdev -type f -exec rm -f -v {} \;
sudo find ~/.cache -xdev -type f -exec rm -f -v {} \;
sudo find /root/.cache -xdev -type f -exec rm -f -v {} \;
sudo find /var/cache/debconf -xdev -type f -exec rm -v {} \;
sudo find /var/cache/apt -xdev -type f -exec rm -v {} \;
sudo find /var/cache/apt-xapian-index -xdev -type f -exec rm -v {} \;
sudo  apt-get clean
```You might want to install bleachbit. It can help  clean up easily. k4dirstat is really good for seeing where the drive  space went and finding that DVD iso you accidentally downloaded to  /some/directory/you/would/never/look/in/. You might want to check the  size of /var/log/* and ~/nohup.out
If you keep data files in ~/ or  some other system partition, fslint is a great program to check for  duplicate files. For that matter, that's true even if you keep your data  on a seperate partition like a sane person, but filling up a data  partition won't crash you.
> **yonnie said:**
> most important feature for using Ubuntu in the  first place is for the printing controls and printer support.If I  were to write down everything I know about printing, the file might  take as much as 3 bytes.> **yonnie said:**
> I'm a bit loathe to remove apt-xapian until I can  understand more about it.Look it up with synaptic. Synaptic is a  GREAT gui app for browsing the repositories. I think it may have been  dropped from the default installation, but you can always install it.   Also look in Wikipedia.> **yonnie said:**
> It sounds like a major part of the update mechanism.Not at all. More like a convenience thing.

 > **yonnie said:**
>  It would be nice to get a handle on what about candy crush causes the lock-up.  Possibly a script?Quite possibly. Firefox extension NoScript could fix that, but it will take some study to get it working the way you want. The extension Flashblock or one of the ad blocking extensions might do it with less work. There are all sorts of Firefox (or maybe better Palemoon) extensions that might be good for this.

---

### Post by yonnie on 2015-11-29
You mind if I print this out and save for reference?  I haven't been back to this post for awhile as I couldn't find it, thanks for posting.  You have listed a lot of good stuff to try.  Yes I like Synaptic, though quite often the descriptions tend to be annoyingly circular and vague.  I've tried flashblock and it leaves a lot of websites inoperable with warning complaints about flash not working and messages about needing to install flash.  Since an update last week the computer with the problem has not locked-up.  The code guru's may have fixed it.

when I wrote apt-get autoremove doesn't work sometimes, is because when /boot gets full of old vmlinuz files, autoremove doesn't seem to clean it out and I have to go in manually and delete files.  This is true for all ubuntu derivatives, /boot fills up to where the update mechanism crashes and Muon usually gives no error msg, sometimes it reports the software is up to date and then in the kick panel a msg appears that says there is a security update.  then if I go and run Synaptic, I'll discover that /boot is too full to perform updates.  The last time I did this I deleted one too many and created a dependency problem

---

