---
title: "Best strategy to upgrade from 8.04 to 9.10"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by jeanrouche on 2009-11-11
Hello,

I am a beginner...

I have already done a full rsync of my home directory to an external drive.

1. Do I have to proceed by successive steps : 8.04 to 8.10 to 9.04 to 9.10 and the a restore of my home directory if needed... And how can I go from 8.04 to 8.10, etc. ?

2. Is it better to make a new "fresh" install of 9.10 without format the home directory? Knowing that in case of trouble I still have the back-up. 

3. Or is it better to format the home directory during the install of 9.10 and then to restore one by one the personal directories (and sub-directories) such as Documents, Photos... What happens with the mails (Thunderbird and Evolution)? Is it a specific way to restore the mails, the contacts, the calendars, etc.

Is there aspects that is important to know before to begin ?

Thank you for your help,

Jean
Belgium

---

### Post by howefield on 2009-11-11
You could take the upgrade path, which would mean incremental steps, ie 8.04 > 8.10 > 9.04 > 9.10. This would be very time consuming and more likely to run into problems than a straight reinstall of 9.10.

In your circumstances, I'd do a fresh install, download any updates, install relevant programs, restore /home from your backup and you should be good to go. 

All your email and settings are contained in your home folder, so assuming you have it all backed up, including the hidden folders, you shouldn't lose anything.

---

### Post by jeanrouche on 2009-11-11
Thank you for your answer.

Can I consider that the technical content of the Home directory does not change with the successive releases ?

By example, if I restore the mail directories '.evolution', or '.thunedrbird', etc, can I be sure that I will not have compatibility problems when the last version of Evolution will try to use the data from 8.04 ? Well I am really not sure to explain my concern correctly (let's say in correct English!)

Finally I think about another possibility : I could also consider to wait for the next LTS 10.04... with two possibilities : a unique upgrade or a fresh install. Could it be a better idea ? But I know I should like to discover 9.10, this question is just for my curiosity...

Than you again,

Jean

---

### Post by howefield on 2009-11-11
> **jeanrouche said:**
> Can I consider that the technical content of the Home directory does not change with the successive releases ?

By example, if I restore the mail directories '.evolution', or '.thunedrbird', etc, can I be sure that I will not have compatibility problems when the last version of Evolution will try to use the data from 8.04 ? Well I am really not sure to explain my concern correctly (let's say in correct English!)

You are very clear and explain perfectly. 

There is always risk when upgrading/updating software that some unforseen issue crops up. It cannot be entirely ruled out, but what's the worst thing that could happen ? You have your backups, so you would install the last known working version.

> Finally I think about another possibility : I could also consider to wait for the next LTS 10.04... with two possibilities : a unique upgrade or a fresh install. Could it be a better idea ? But I know I should like to discover 9.10, this question is just for my curiosity...

A plausible idea, you would be able to directly upgrade from 8.04 to 10.04 (without the incremental versions in between) given that both are LTS releases.

You might also consider testing the new version in a Virtual Machine via something like virtualbox, and give it a good testing before committing your real hardware to it.

Either way, good luck :)

---

### Post by jeanrouche on 2009-11-11
Hello,

I have taken time to try 9.10 with a live-CD. It's OK. Then, let's start for the 9.10!
Thank you again for your help, best regards,

Jean

---

### Post by ssulaco on 2009-11-11
> **jeanrouche said:**
> 
Finally I think about another possibility : I could also consider to wait for the next LTS 10.04... with two possibilities : a unique upgrade or a fresh install.
Ive been real happy with Jaunty,everything just worked,but i did a fresh install,like you,Im considering waiting for Lucid Lynx (LTS)
3 year service and would do a clean install also...Im not looking for the latest and greatest just want stability.

---

### Post by jeanrouche on 2009-11-11
Yes I know, always the choice to do at every release. I was, I am always, very satisfied with the Heron... but sometimes the curiosity is there.

Anyway it was a nice exchange of opinions !  Jean. :)

---

### Post by raymondh on 2009-11-11
> **jeanrouche said:**
> Yes I know, always the choice to do at every release. I was, I am always, very satisfied with the Heron... but sometimes the curiosity is there.

Anyway it was a nice exchange of opinions !  Jean. :)

After doing this since version 7 .... and going through the tweaks for Karmic, I have come to the conclusion that the normal 6-month releases are a test-of-sorts for the next LTS version.  Something like ... "let's include the pluses of these 6-month versions and incorporate them in the upcoming LTS".

I too have been happy with hardy.  As well, I have been curios with intrepid, januty and now Karmic.  I have Hardy on a main, production laptop and will upgrade that to the next LTS.  My netbook (currently with intrepid and jaunty) will also be upgraded to the LTS and that'll be it until 2013.  My test machine (currently with Karmic and jaunty) will remian a test machine so I can practice my tweaking skills when I feel like it.

Nice exhange of ideas.

---

### Post by justaguy168 on 2009-11-11
> **howefield said:**
> In your circumstances, I'd do a fresh install, download any updates, install relevant programs, restore /home from your backup and you should be good to go. 

 
I am a newbie. What is meant by a fresh install? How does one do that? I am trying to do something similar but installing over another distro of Linux. [Click here to see my post in the install forum]("http://ubuntuforums.org/showthread.php?t=1111020"). I do not have anything significant to save on the existing installation. 
 
Please point me in the right direction so I can RTFM.
 
Thank you.

---

### Post by howefield on 2009-11-11
> **justaguy168 said:**
> What is meant by a fresh install?

It means a clean install., as opposed to upgrading what you already have.

You say you have nothing significant on the drive you want to use, just have a second think about that, eg you might have email you want to save, or passwords ect. If that is the case, save to an external source, usb memory stick, cd, whatever.

Then load up the Ubuntu live cd and choose Install Ubuntu, the only "tricky" part is deciding what you want to do with your partitions, you can tell the installer to use the whole disk and simply get on with it, however, I'd recommend creating a seperate /home partition. This will make future installs easier but mean you need to go into manual partitioning during the install process.

Have a look at the Ubuntu Partitioning video at screencasts.ubuntu.com

---

### Post by raymondh on 2009-11-11
> **justaguy168 said:**
> I am a newbie. What is meant by a fresh install? How does one do that? I am trying to do something similar but installing over another distro of Linux. [Click here to see my post in the install forum]("http://ubuntuforums.org/showthread.php?t=1111020"). I do not have anything significant to save on the existing installation. 
 
Please point me in the right direction so I can RTFM.
 
Thank you.

Read you other post in another thread.  If you plan to just sole-boot, you can choose "USE ENTIRE DISC" in step 4 of the installation process.  Here's a quick run-through:

-  Download and burn to CD your preferred Ubuntu version.  You'll get what's called a LiveCD
-  Boot into the LiveCD (that's changing the BIOS order at start-up to make sure the CD drive boots first instead of the HD)
-  One of the options is to "Check CD for defects"
-  If no defects, "TRY UBUNTU WITHOUT ANY CHANGES" first.  That is known as a live session which will allow you to check if that Ubuntu version works well with your system.  Check Fkey functionality, sound, wifi, keyboard, etc. etc.  Play around with it (live session).
-  When satisfied, and whilst still in live session, on the desktop is an option to install
-  Go through the 1st few steps.  When you get to step 4, choose "USE ENTIRE DISC" since your goal stated in previous thread is to sole-boot.
-  Continue with the install process.
-  If you are unsure, you can quit anytime.  The last opportunity to quit is in step 7.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

There is no need to install a /boot because you plan to sole-boot.  A /boot is a workaround/needed if you plan to install Ubuntu in a location much further than what your BIOS can handle.  It is also needed if you plan to "specialize" booting various linux distros ... which neither you plan to do.

I am not familiar with CentOS so I cannot say if its' config files, settings, etc. will agree/match with Ubuntu.  That said, I would back-up your personal files elsewhere first. 

If you decide to create a separate /home (*which I strongly suggest in order to retain settings, config files, etc. should you ever need to re-install Ubuntu in the future*) , or do some pre-partitioning before installing, post back.  

Better yet, create a thread and I'll follow there ..... that way we don't hijack this thread  :)

Back up first.

---

### Post by DJonsson2008 on 2009-11-11
Its good to think about what is driving the upgrade, hardware compatibility, features you can't live without, fixed bugs,
new software.... 

My production machine remains Xubuntu/Ubuntu 8.04 so far 99% of everything works. My test machine that has 9.04 on it does accept the Nvidia drivers from a fresh install but I don't see a significant difference there, otherwise and have not had the 2 free afternoons yet to fully restore it to match my old installation and break it in. 

I've tried numerous times the upgrade from 8.04>8.10>9.04 and there were
issues, more issues than I've yet had time resolve. Needless to say
it was not a toggle switch. 

With any OS update>upgrade things can go smooth and there can be kinks,
if you don't have time to burn, or don't have a machine to experiment
on - consider any upgrade a gamble. Its also possible to clone your
installation and upgrade on that, giving you a fall back if things
go wrong. Considering the price of 2nd hand hard drives today balanced
against 2-4 days of hacking on an update consider your choices. LTS makes a sensible investment because often times stabilizing one of these updates will take a while, and if you have a long-term dividend
from that to look forward to -- all the better.

---

### Post by paynek716 on 2009-11-13
> **howefield said:**
> I'd recommend creating a seperate /home partition. This will make future installs easier but mean you need to go into manual partitioning during the install process.

I recently upgraded from 9.04 to 9.10. No technical problems but everything is S-L-O-W. I am considering a clean install of 9.10 to speed things up, otherwise will revert to 9.04 and wait for the next LTS.

Manual partition is not a problem as I dual boot with Vista, and I plan to backup /home before the clean install of 9.10. What I don't want to do is reinstall non-default apps after the clean install. Will some record of those installed apps be kept in my /home backup?

---

### Post by audiomick on 2009-11-13
> **paynek716 said:**
> 
Manual partition is not a problem as I dual boot with Vista, and I plan to backup /home before the clean install of 9.10.

If home is already on it's own partition, back it up of course, but if you mount it without reformatting during your fresh install, it should all just come back.

>  What I don't want to do is reinstall non-default apps after the clean install. Will some record of those installed apps be kept in my /home backup?

As far as I know, the files about installed apps are not in your home folder. The apps are there for all users, so info about them can't be in your personal folder where no-one else can get to them.
What you will have in your home folder is obselete configs for apps that aren't there anymore.
This goes as far as a starter that I had installed in the panel disappearing after a new install using and old /home, then  magically reappearing some weeks later when I got around to re-installing the program.

---

### Post by paynek716 on 2009-11-13
Is there a way to backup what I have installed and restore those settings after a fresh install?

---

### Post by howefield on 2009-11-13
> **paynek716 said:**
> What I don't want to do is reinstall non-default apps after the clean install. Will some record of those installed apps be kept in my /home backup?

Yes, but most of them will be easily identifiable by the name of the folder.

eg, pidgin is not the default instant messenger on 9.10 so won't be installed unless you do so manually, if you had pidgin configured previously, you will have a .pidgin folder in /home.

You can delete this folder or simply choose not to copy this folder back after your reinstall.

Hope this makes sense.

---

### Post by howefield on 2009-11-13
> **paynek716 said:**
> Is there a way to backup what I have installed and restore those settings after a fresh install?

Not entirely sure what you mean, try reading this page, does it help ?

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Unless you have cleared them out, your .deb package downloads will be found in /var/cache/apt/archives. You could back this folder up and copy them back after you install. 

Your settings will be in your /home folder.

---

### Post by paynek716 on 2009-11-14
That is EXACTLY what I want, a record of what packages I have added since the initial installation and a way to restore those packages to a new installation of Ubuntu.

thanks!

---

