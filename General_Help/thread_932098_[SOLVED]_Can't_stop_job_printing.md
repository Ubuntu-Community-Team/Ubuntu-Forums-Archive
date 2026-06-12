---
title: "[SOLVED] Can't stop job printing"
date: 2008-09-28
forum: General Help
---

### Post by Camilia on 2008-09-28
I have installed hplip but it is not showing.  Thus went to admistration - printer. Marked stop job and apply. Still printing. Marked stop printer and apply.  Still printing.

Got message Not published see server settings.
In settings
Location empty.
url hp:/usb/Deskjet_3900?serial=CN5CM1M2WY04DF

I  unplugged the printer.  Plugged computer back in and printer wouldn't print another job. Restarted  computer and it restarted print the job I wanted to stop. Now just have to let it print until it is finished

What else can I do so that in the future I can stop a job from printing after it is started?  For I may accidentally started printing to many pages and want to stop the job.

---

### Post by Sef on 2008-09-28
> I have installed hplip but it is not showing. Thus went to admistration - printer. Marked stop job and apply. Still printing. Marked stop printer and apply. Still printing.

How did you install it?  If from the repositories, then go to system > preferences > main menu > preferences > check the box next to hplip (if it is not there, please let us know.

How are you connected to the printer: network or direct?

If you can't stop a print job, then turn off the printer for about 30 seconds.

---

### Post by ad_267 on 2008-09-28
I've had the same sorts of problems. Try going to [http://localhost:631/admin](http://localhost:631/admin) and cancelling the jobs from there.

You can also try deleting the files in /var/spool/cups

---

### Post by Camilia on 2008-09-28
How did you install it? If from the repositories, then go to system > preferences > main menu > preferences > check the box next to hplip (if it is not there, please let us know.

I installed in the repository. It shows it as being installed. I have uninstalled and reinstalled.  I don't see hplip there.

/var/spool/cups.   Where do I paste this or where do I find this?  What is this?

---

### Post by ad_267 on 2008-09-28
> **Camilia said:**
> 
/var/spool/cups.   Where do I paste this or where do I find this?  What is this?

That's a location in your file system. You need to be the root user to view the files though. Try deleting the job from the CUPS web interface at [http://localhost:631/admin](http://localhost:631/admin) first.

That should work but if it doesn't you can press Alt-F2 and then run "gksu nautilus" and enter "/var/spool/cups" into the location bar then delete the files in there. That is the location where CUPS (Common Unix Printing System) stores the jobs to be printed. I'm not really an expert at this so I'm not sure if it's a good idea.

---

### Post by Camilia on 2008-09-28
The job has finished printing. Just need to know what I do if this occurs again.

Seems easier to just go to  [http://localhost:631/printers/](http://localhost:631/printers/).  

I miss being able to us hplip. It has been gone since I reinstalled using the ubuntu disk.  I reinstalled for surfing the web was getting very slow.  Wasn't certain if it was a virus issue or computer bogged down by additions via the synapse.

This mourning I see alert that printer is out of paper.  I went to 
[http://localhost:631/printers/](http://localhost:631/printers/)  and saw I have 3 jobs waiting to be printed. Clicked stop job and was prompted for user name and password.  I put in user name and password I use to log in and nothing and was again prompted for password so I put ubuntu  user name and password and blank page. The jobs are still there.  

Pressed Alt-F2 clicked terminal and location bar and pasted /var/spool/cups.  Got message You do not have the permissions necessary to view the contents of "cups.  So again I unplug it to see if it will reset itself. I had it unpluged for a long time.  Still it prints the jobs.

How are you connected to the printer: network or direct?  The printer is connected to the computer via sub.

Finally got logged in to CUPS and got all of the jobs canceled.

---

