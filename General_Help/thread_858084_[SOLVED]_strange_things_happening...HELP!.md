---
title: "[SOLVED] strange things happening...HELP!"
date: 2008-07-13
forum: General Help
---

### Post by senewag on 2008-07-13
I am stuck, any help would be really appreciated!
Looking at System Monitor, the "file systems" tab, show that my /dev/sbdb2  is 100% full up (which it can't be).
Total=148GiB  Free=34MiB  Avail=0bytes  Used=148GiB
Total should equal Free+Used.  So it looks like my system has got it's tail in a twist somehow.  Before thisevening it was just fine.
Now, when I boot up all this happens:
(1) Firefox won't start (although Gimp and Thunderbird will)
(2) This message pops up "the panel encountered a problem while loading "OAFIID:TomboyApplet. Do you want to delete the applet from your configuration"
(3) Gnucash:  "file type gcashdata_1 is unknown".  This is the main gnucash file which should be a Gzip file but is now 0 bytes and a text file.
(4) the computer will only turn off by using the button on the box.

I am hoping that the above 4 errors may be all related but I would sure appreciate any help out there or hints.

---

### Post by Gunman1982 on 2008-07-13
Could you open a console and run the command 'du -h --max-depth=1' that will go through your home directory and tell you how many megabytes are used there.

---

### Post by senewag on 2008-07-13
Thankyou Gunman1982
This command shows a total of 46 Gigabytes. (mainly 7.5Gigs for photos and 37 Gigs for movies)

---

### Post by rylangrayston on 2008-07-13
i am having similar problems 

a message saying -The panel encountered a problem while loading "OAFIID:TomboyApplet". would you like to delete it? apears every time i restart my computer even if i click delete.

firefox flashplayer will not play or load more then a few seconds before jumping to the beginning 

apon restart the desktop loads some of my icons slightly off screen 
as if the screen were 40 pixls larger

when i click the shutdown icon on the panle the panle disapears and  no shutdown option splash screen apears

if i hit the power button at any time the computer beeps and shuts down
emediatly  (i just have to push it not hold it like a hard boot)

i thought i also had no space but then used  sudo rm -rf /home/username/.local/share/Trash/ 
to delete some files with only root access 

also fire foxes back buton is always greyed out

i also had dual monitos runing off of a nvidia 8500 gt
and that stopped working to. after disabiling the propriatary nvidia  driver 
and restarting i still have all the problems above

 i will be here at my 
computer all day today so reply fast and so will I
thanks !

---

### Post by rylangrayston on 2008-07-13
well i found a solution all tho it is very obscure 

apon start up I pressed the escape key to get the grub boot loader options

then piked the first recovery mode option 

a menu apears and I chose dpkg  to repair packages then , to fix the x server i chose xfix and  finaly chose normal restart

apon restart every thing worked 

In my case I would guess that it was the x server that fixed the problem
as i had been using sudo nvidia-settings alot and i dont think dpkg did any repairs.
Hope that helps !

---

### Post by senewag on 2008-07-14
Thankyou Rylangrayston for your message. Your computer obviously has the same symptons/problem as mine, I tried what you did on three past recovery options but it didn't work for me.
My computer has always been well behaved and I love Ubuntu until everything went wrong the other evening.
In summary:
(1)When the login page comes up, it appears different in resolution and centred but it's hard to say how without comparing.
(2) I get the "OAFIID: TomboyApplet. Do you want to delete the applet from your configuration" message upon start up.
(3) When starting Firefox, it flickers for a microsecond then disappears. (Gimp and Thunderbird run okay).
(4) System Monitor reports my sbdb2 disk as being 100% full which it aint.
(5) When I want to close down/restart the computer, I click on the red log-off button which causes my panel to disappear.  I touch the power button on the box, and the computer shuts down immediately.
None of these things have happened before.
Also my main gnucash file (gcashdata_1) is now empty (don't know if this is related (luckily backed up).

So, if anyone can help me, I would be so grateful.

---

### Post by The Cog on 2008-07-14
I believe that EXT2 reserves a small percentage of disk space for use by root.This is done to ensure that root can log in even when all other users cannot because the disk is full. It may explain why you appear to have a few megs of space but still have disk full problems.

---

### Post by senewag on 2008-07-15
CONFESSION
==========
Well, I have solved the problem.
A month ago I was playing with backups, and forgot that I had set "SimpleBackup" to run automatically doing an incremental backup daily and a full backup every 21 days.
Writing to /var/backup.
That was fine... as I had next to nothing on /home  until I transferred all my photos and videos from Windows to Ubuntu..... then SimpleBackup went into full swing and last sunday the full backup did the damage.

Great to be up and running again, and thanks to all for the hints and help.

---

