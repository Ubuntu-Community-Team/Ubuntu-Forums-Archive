---
title: "Ibex: The configuration defaults for GNOME Power Manager have not been installed"
date: 2008-11-13
forum: General Help
---

### Post by richardwooding on 2008-11-13
Hi,

I have just done a routine update of Ubuntu Intrepid Ibex 8.10

After the first reboot when using Gnome you receive this error message:

(Just after playing Gnome startup sound)

The screen is blanked out (cursor is still visible), which did not happen before, and this error message pops up.

"The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."

Only the message was visible, and the rest of gnome was not visible and usable.

Thinking that the problem was with the gnome-power-manager I attempted this:

"apt-get --reinstall install gnome-power-manager"

Now the behaviour is as follows, I log into Gnome, I hear the startup sound, the screen blanks with the cursor still not visible. Gnome is still not usable.

Regards
Richard Wooding

---

### Post by terazen on 2008-11-22
Posting here because I think we're both needing the same thing.  I'm trying to reinstall the gnome-power-manager for a different reason.  I can't do `dpkg --configure` or `dpkg --purge` because of dependancies of the desktop.

I imagine I could install kde, then purge/reinstall the gnome stuff, but I'm hoping there is another option?

---

### Post by zenarcher on 2008-11-27
I just received two new Dell Mini 9's, yesterday and have been trying to do a clean install of Ubuntu 8.10 on them, using a USB jump drive....and I'm getting the same error when I try to install.  At the moment, I'm stuck with the Dell version of Ubuntu 8.04.  That's not good, as none of the Ubuntu repositories work, so I can't install packages I want, either.

When I attempt a fresh install, I am able to choose the install language, then as I try to move to the next step, I get the same error, then a black screen, just with the mouse pointer.

Has anyone figured a way around this issue?  Or a way to do a fresh install?

Thanks,
zenarcher

---

### Post by kitara on 2008-12-23
I have also been hit by this issue.  I just went through the Wubi install on my hp mini 1030 NR to set up dual boot with Windows XP.  Luckily, have not configured all that much since install (been less than a day).  I was installing Adobe Flash through FireFox when my system locked up.  The only way to do anything (as far as this newbie could tell) was to power cycle. 
 
My experience is the same with the blank screen but for the cursor and error messages.  I also had messages for update notifier and evolution-alarm-notifier tcp/ip errors.

If I was more savvy, more invested, or patient I would seek help - but I am pursuing a fresh install as i type from my Macbook

---

### Post by icheyne on 2009-02-01
```
sudo dpkg --configure -a
``` fixed it for me.

---

### Post by ersatzryan on 2009-02-05
I was getting configuration defaults not set for gnome-power-manager errors and it would hang when i tried to shutdown. So i tried to reinstall the g-p-m pkg and that didn't work cause it errored when it was trying to do the config so i tried to reinstall the gnome-session and g-p-m and now its really broken. I can't log in unless under gnome-fail safe session when i log in it just hangs. and if i do dpkg --configure -a it errors saying it can't do anything about g-p-m, gnome-session, and ubuntu-desktop cause there are dependency errors

---

### Post by cariboo on 2009-02-05
Start in recovery mode and at the menu drop to a root prompt, then type:

```
dhclient eth0
```

substitute your network device for eth0. Now that you have network access at the prompt type:

```
apt-get install -f
```

this should update some missing dependencies. Once the command has finished at the prompt type:

```
apt-get update && apt-get dist-upgrade
```

Hopefully the upgrade wiil finish this time.

If you have any more errors you may have to do the above again.

Jim

---

### Post by kartz on 2009-02-11
hi all!!!!!!!am new to ubuntu
am also getting the  same error even after tried wit cariboo907 commands
help me regarding tis problem

---

### Post by snowho148 on 2009-02-14
> **icheyne said:**
> ```
sudo dpkg --configure -a
``` fixed it for me.

I also got the error message and was not able to bring up firefox or pidgin... this fixed my issue too. Thanks!:)

---

### Post by itmanvn on 2009-04-23
> **icheyne said:**
> ```
sudo dpkg --configure -a
``` fixed it for me.

thank you man!!!:lolflag:

---

### Post by inventorM on 2009-05-28
I had the same problem with Ubuntu 9.04.
Manually creating the directory ```
/var/lib/gconf/default/
``` fixed my problem.
I figured this out by looking at the error message that Synaptic displayed on the console.

---

### Post by SurferGTO on 2009-11-15
i cant do sudo dpkg --configure -a, i recieve a messsage in terminal stating status area database is locked by another process. 

just installed 9.10 and everything other than my wallpaper is gone. why does this happen every freakin time i upgrade its a PITA. i cant activate my NVIDIA driver, so i cant run extra desktop effects, my sound isnt working... ugh.. i love ubuntu but i hate fixing it every damned install

---

### Post by SurferGTO on 2009-11-15
i also cant run synaptic package manager.

---

### Post by ed12348 on 2010-02-03
None of the solutions here worked for me, i'm using karmic, I in the end just reinstalled the desktop including gnome.

```
sudo apt-get --reinstall install ubuntu-desktop
```

The only things I lost were my WiFi settings, didn't even have to set my custom theme again.

Hope this helps somebody :D

---

### Post by abohanon06 on 2010-02-13
I am having the same problem, were do i go to try sudo dpkg --configure -a?

---

### Post by Jeff Anthony on 2010-05-02
> **abohanon06 said:**
> I am having the same problem, were do i go to try sudo dpkg --configure -a?

Press Ctrl+Alt+1, enter your credentials and you can use this terminal to run the command lines.

---

### Post by mrcash on 2010-05-28
Fixed this error...  space issue in root volume as outlined at:
 
[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)
 
 
Hope this helps

---

### Post by billjoie on 2010-08-27
Same for me. This was just because my root was full. I had accidently copied 50 GB in /media/. So I typed Ctrl-Alt-F2, logged in, found the culprit data, and removed it with rm -Rf. End of story. Thanks to mrcash for indicating what this obscure error message might mean.

---

### Post by travisp on 2010-08-30
I'm getting the error message in the subject line of this thread when I try to log in to Gnome. I'm given an ugly gray box that asks me to log in, but it fails every time. I'm logging in to the command prompt screen via Ctrl+Alt+F1 and deleting & uninstalling all I can. I even cleared out /var/log and it still won't log me in to Gnome. df -h says I have 2GB free on my hard drive, so clearly there are some unaccounted for files or processes eating up my drive space. I noticed a lot of large files in /var/ and other root level directories but don't know enough about what I can safely delete or not. I'm running Ubuntu 10.04 on an IBM ThinkPad T43 if that helps.

---

### Post by rajayoganand on 2010-11-09
Hi,

We have solved this issue in one of the Laptop.

The problem was with Hard disk space. The / (root) partition was almost full.

Thanks

---

### Post by Weidbrewer on 2010-12-18
I am having this problem for the second time, myself.  Currently running 10.04 64-bit.

[Last time]("http://ubuntuforums.org/showthread.php?t=1561214"), I futzed around a bit, and it went away itself.  No idea why.  This problem seems to arise after using my TV tuner in MythTV...I'm guessing something is going on there.

I've tried a lot of the suggestions above with the exception of the ones pertaining to the full /root directory.  I have certainly gotten pop-ups tonight that have said that.  Now for the question that I've been mentally cringing to ask since I started typing this:  How do I A.) examine the root partition (I've seen talk about it in other threads, but haven't been able to do it) and B.) how do I clean it out?

I said that I was cringing above, because I have this habit of asking questions that people think I should know the answers to, and then I just get a text-based beating.  ;)  

Now, assuming I can get answers to A and B, point C is:  How do I keep this from happening?  Obviously, not knowing how to check my /root directory, I'm certainly not intentionally adding things to it.  Can it be made bigger?  Are there files that are going here that shouldn't?

Any help you can give would be greatly appreciated as Saturday night is the one night a week I ever get to use this machine.  Thanks in advance!


EDIT:  Now, is there a difference between the protect root *folder* I have and the root *partition?*   That might be some of my confusion.  If by root *partition*, we mean the hard drive my OS is on, then there is another symptom:  The space on that drive keeps bouncing back and forth between 3.5GB free and 4 _***KB***_ free, without rhyme or reason between boot-ups.  (Problem has just been happening tonight since I ran the video card.

---

### Post by ampallang on 2010-12-18
> **billjoie said:**
> Same for me. This was just because my root was full. I had accidently copied 50 GB in /media/. So I typed Ctrl-Alt-F2, logged in, found the culprit data, and removed it with rm -Rf. End of story. Thanks to mrcash for indicating what this obscure error message might mean.

Can you tell me how you did it? I have this problem, i dont have any space on my computer! but i just cant find what command to use to free up some space!!!!

---

### Post by Weidbrewer on 2010-12-18
> **ampallang said:**
> Can you tell me how you did it? I have this problem, i dont have any space on my computer! but i just cant find what command to use to free up some space!!!!

Well, at least I'm not alone.

---

### Post by oldos2er on 2010-12-18
There are some suggestions on how to recover disk space here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Weidbrewer on 2010-12-19
> **oldos2er said:**
> There are some suggestions on how to recover disk space here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Hey, thanks for that link.  It didn't end up helping me in this instance, but I've got it bookmarked for the future.  In my case, the commands either didn't work, or I was getting a segmentation error (supposedly from my repos.)  Eventually, I realized that life was short, and doing a reinstall was the way to go.  Really wish I knew what caused this so that I won't have it happen again the future.  I think I'm just going to stay away from my TV tuner card for now.

---

### Post by harirarn on 2011-08-16
I got a similar problem in my Ubuntu 11.04. The problem occured because the filesystem was out of memory. I logged in through terminal and deleted some files. It started working properly again.

---

### Post by Weidbrewer on 2011-08-16
Wow...I was upgrading that machine over the weekend and thought, "I wonder why I don't use my TV tuners anymore..."

Seeing this thread again, I now remember.  Never did find out what happened and why - and more importantly, how to stop it from happening again.  So, I don't watch TV on my computer anymore.

---

