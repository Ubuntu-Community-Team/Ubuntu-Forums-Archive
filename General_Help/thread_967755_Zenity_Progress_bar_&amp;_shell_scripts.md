---
title: "Zenity Progress bar &amp; shell scripts"
date: 2008-11-02
forum: General Help
---

### Post by Tapas Pain on 2008-11-02
I have a question about Zenity progress bar. Is there a way to make it show the actual progress of a task? I've just started learning how to program shell scripts, so I did a basic one to create a tarball, move it, and then copy another backup file. I've seen various zenity progress scripts on the Web, and imported the ideas from them, but I can't figure out how to make Zenity show the true progress of the task. Can anyone offer any suggesitons please? Here is the script:

#!/bin/bash

echo "Do you want to run the backup script (y/n)?"

read answer

if [ "$answer" = "y" -o "$answer" = "yes" -o "$answer" = "Y" -o "$answer" = "Yes" -o "$answer" = "YES" ]; then
echo "Standby ... user files are backing up. Finished product will be on //media/disk."

else exit

fi

(
echo "10" ;
echo "# Compressing tarball ..." ;
cd //home/tapas
tar -czvf my_tarball.tar.gz *
echo "20" ;
echo "# Tarball compression complete" ;
echo "60" ;
echo "# Moving tarball" ;
echo "70" ;
mv -v my_tarball.tar.gz -t //media/disk
echo "# Removing original tarball file" ;
echo "85" ; sleep 1
echo "# Backing up personal log" ;
echo "90" ;
echo "# Standby ... backing up personal log."
cd //home/tapas/Documents
cp -v personal.log personal.backup
echo "# Script is finished."
echo "100" ;
) |
zenity --width=400 --height=100 --progress --title="User Profile Backup" --text="Backing up your data now..." --percentage=0 --pulsate

if [ "$?" = -1 ] ; then
zenity --error \
--text="Update canceled."
fi

---

### Post by LinuxPS2 on 2008-12-15
hrm, not sure - I have been having trouble with it myself - can't seem to figure out how to pipe dd into it and it show the percentage - just ends up showing the text from the dd output in the "text" area of the progress dialog, this happens even when I define the "text" parameter and since I am using dd to make an image from a disk the output is very large and makes the progress dialog extend past my screen boundaries (also even when width is defined)... hrm... maybe there is another way to graphically represent the percentage from a dd command (and not one of the text-based representations)...

you sir have had much more success than I with zenity...

---

### Post by stupid_user on 2008-12-16
@Tapas Pain as far as a progress bar there is the app called bar that you can pipe things through.  I haven't tried it though, so I can't vouch for its usefulness.

Explanation here:  [http://fosswire.com/2007/08/10/command-line-progress-bar-a-progress-bar-for-dd/](http://fosswire.com/2007/08/10/command-line-progress-bar-a-progress-bar-for-dd/)

@LinuxPS2 I was imaging a 200GB partition the other day and found that the tools ddrescue and dcfldd both give indications of how much data is moving.
I found them extremely useful, as I waited two days before giving up on dd and realizing that it wasn't working the way I wanted.

cheers

---

### Post by LinuxPS2 on 2008-12-16
yeah I have used dcfldd a good bit but I am just using dd to backup blu-ray .iso's and just the need the progress bar for a graphical frontend to the script - I myself don't care about knowing the progress but I have been trying to make a script that is mostly point and click for others... got it all working except the progress bar so now it just says "This may take several hours, the disk will eject upon completion"... oh well...

---

### Post by Tapas Pain on 2009-06-14
Thank you all.  I've been away for quite a while, and honestly after a week or two from posting it, I didn't think anyone was going to reply.  I should know better 8-)
Again, thanks guys, for all your input.

---

