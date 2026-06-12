---
title: "Mount Western Digital My Book Live NAS?"
date: 2010-10-22
forum: Hardware
---

### Post by Spinland on 2010-10-22
As per the subject, I recently ordered the 2TB Western Digital My Book Live NAS.  I will certainly get good use out of it via my Windows 7 graphics work station, but if possible I'd like to be able to mount it via my wife's Ubuntu 10.10 machine so I can send her backups thereto.

A forum search turned up:

[http://ubuntuforums.org/showthread.php?t=1228900&highlight=western+digital+nas](http://ubuntuforums.org/showthread.php?t=1228900&highlight=western+digital+nas)

I'm frankly confused by the response, because the WD link mentioned there just tells how to install the client software in Windows and seems to have nothing to do with Linux.

Does anyone have experience and advice to share for accessing this model NAS from Ubuntu?

Many thanks in advance!

---

### Post by oracle2b on 2010-10-22
I don't own this device but since it's a NAS you should still be able to connect to it. Try connecting to the drive by using the following address in your web browser: [http://mybookworld/](http://mybookworld/) or [http://WDShareSpace/](http://WDShareSpace/).

If you have the devices ip address then  to Application –> Ubuntu Software Center. Next, type ‘pyneighborhood’ in the search box, then select pyNeighborhood and click Install. you could open up a terminal and run > sudo apt-get install pyNeighborhood

After installing, go to Applications –> System Tools –> pyNeighborhood

Go to the edit -> preferences and Make sure SMB is enabled

home panel and Right-click ‘Groups’ then select ‘Scan using msbrowse’,
your nas should appear. 

For a complete backup setup follow [this guide]("http://www.howtogeek.com/howto/29518/how-to-backup-your-linux-pc-with-simple-backup/").

hopes this helps

---

### Post by Spinland on 2010-10-23
Wow, that's exactly the kind of sage advice I was hoping for, thanks!  I'm still a Linux noob; I'm doing a lot of research and learning a lot, but there's just so much out there it's easy to get lost and/ or overwhelmed. I really appreciate you distilling that down for me. :guitar:

---

### Post by coffeecat on 2010-10-23
@Spinland, I have the 1TB WD Mybookworld NAS and very well it works in Ubuntu too. However, picking up on oracle2b's post....

> **oracle2b said:**
> I don't own this device but since it's a NAS you should still be able to connect to it. Try connecting to the drive by using the following address in your web browser: [http://mybookworld/](http://mybookworld/) or [http://WDShareSpace/](http://WDShareSpace/).

This doesn't work for me. I get a couple of sites on the big wide internet. To get to the admin panel of the mybookworld, you need to log into your router and find which local ip address it has been assigned. Usually something like 192.168.1.5. Then you simply type that IP address in the firefox address bar and you are presented with the WD administrator login. Once you've logged in you might want to set a static IP address under 'network'. Or you can do this in your router admin panel. I've set mine to 192.168.1.100 to be memorable.

Once you've set up some smb/Windows shares, you could access them the way oracle 2b suggests...

> **oracle2b said:**
> After installing, go to Applications –> System Tools –> pyNeighborhood

Go to the edit -> preferences and Make sure SMB is enabled

home panel and Right-click ‘Groups’ then select ‘Scan using msbrowse’,
your nas should appear. 

I've never used this, because there is another, possibly simpler, way. Install the package 'samba' with Synaptic or Software Centre, restart the computer and you should see mybookworld in Places > Network. Double-click on it, choose your share, type the password for the share and that should be it.

---

### Post by JoeFree on 2010-11-09
coffeecat, thanks for posting the solution!  Installed Samba, restarted and VOILA - my MyBookWorld is now visible.  I can finally access my music with Ubuntu!

\\:D/

---

### Post by Shadius on 2012-06-18
Would this apply to my situation here: [Setting up WD My Book Live]("http://ubuntuforums.org/showthread.php?t=2005593")?

---

