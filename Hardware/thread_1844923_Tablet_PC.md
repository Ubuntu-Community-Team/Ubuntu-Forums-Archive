---
title: "Tablet PC"
date: 2011-09-16
forum: Hardware
---

### Post by Joejo on 2011-09-16
I just picked up the Thinkpad X61 tablet and installed Ubuntu 11.04. Everything works out of the box so far. The digitizer works fine, I installed cellwriter and xournal and they work great. But I am having trouble trying to get the automatic screen rotation to work and also the buttons on the on the bezel near the monitor that switches the screen to landscape and back. I tried downloading and installing Magick-Rotation but it wouldnt install and I tried to follow the manual install and I just couldnt handle it. 

Is there a simpler way or anyway to get it to it to work?

---

### Post by Favux on 2011-09-16
Hi Joejo,

You could just try the automatic rotation script which is method 2 on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

What are you doing and what happens when you?:
```
tried downloading and installing Magick-Rotation but it wouldnt install
```
What error is it giving you?

---

### Post by Joejo on 2011-09-16
Well, I never downloaded and installed a bz2 file before, so I found instructions that told me to extract it and put the extracted file into my home folder, go into it and find the installer file. I did all of that but nothing happens. In fact the action just freezes up.

---

### Post by Favux on 2011-09-16
So you right clicked on the download tar and told it to 'extract here' wherever you downloaded it.  Then you:
> Drag and drop the magick-rotation folder onto 'yourusername' in the left column of 'Places' (/home/yourusername).  If it asks if you want to replace the magick-rotation folder say "Yes to all".  To install open the folder and right click on 'magick-rotation' and select 'Properties'. Then click on the 'Permissions' tab. Verify "Allow executing file as a program" is checked, if not check it, and close. Now double click on 'magick-rotation' and choose 'Run'.
but double clicking on the uncompressed magick-rotation file in the magick-rotation folder now located at /home/yourusername/magick-rotation causes a freeze?  In the folder with the other files is there a file called *firstrun*?

---

### Post by Joejo on 2011-09-16
Yes, there is a file called first run. When I open it, there is nothing showing up on the text editor.

---

### Post by Joejo on 2011-09-16
Everything works out of the box fine, the digitizer and I installed Xournal and Cellwriter. I just want to be able to get the tablet keys on the bezel to work (the screen rotation butotn, tool box, the ESC and the scroll/enter button) which I imagine there is some sort of keyboard input for and I would like to get it to reconize the automatic rotation also, being able to turn the tablet and it moving along with the position its in. 
I am new to Ubuntu and I when I look at the script and directions I get confused, it looks overwhelming.

---

### Post by Favux on 2011-09-16
Hi Joejo,

The firstrun file is suppose to be empty.  It is what triggers the installer.  Once the installer finishes it disappears so the installer isn't triggered again.

I think that because you're new to linux you're suffering from a little bit of information overload.  Don't worry, give yourself a little time to get more familiar with linux and it'll shake out.  Just skim through things a few times until it starts making sense and your eyes stop glazing over.  The README is long because I tried to make it "complete", but not hard.  My guess is you aren't making the magick-rotation file executable.

This won't help the information overload any but you should know about the thinkwiki.  This page is for the X61t:  [http://www.thinkwiki.org/wiki/Category:X61_Tablet](http://www.thinkwiki.org/wiki/Category:X61_Tablet)  As you can see it is a little dated but it has lots of information.  You should be able to get the bezel keys working.  There's a more recent thread on the Ubuntu forums where someone posted scripts for the X200t bezel keys and so on that may help too.

For a while IBM/Lenovo had a program where they were giving Thinkpad tablets to linux developers.  The developers would figure out how to make everything work and post it on the Thinkwiki.  So Thinkpad owners were the envy of other tablet users.

---

### Post by Joejo on 2011-09-17
I went to the thinkwiki and some of the other links you sent, I was able to get it to rotate through the terminal, I tried to go through the steps to set up the rotate button on the bezel but it wouldnt work, also tried to put in the autorotate and set it up with the startup programs but when I restarted the laptop the rotate button and the autorotate didnt work. Am I missing something?

---

### Post by Favux on 2011-09-17
It could be that the way the bezel buttons are being declared has changed in the last few releases.  I know it has for my tablet PC and I still haven't quite figured out the changes in the stack as you can see on the Rotation HOW TO.

Linuxd00 has a HOW TO for the bezel buttons and stuff for the X201:  [http://ubuntuforums.org/showthread.php?t=1656632](http://ubuntuforums.org/showthread.php?t=1656632)  I don't know how similar your X61t would be.  But it would give you something to compare the thinkwiki instruction/scripts with and see if you can spot what's changed.  Admittedly a little advanced.  If you're lucky they might work for you as is.

---

### Post by Joejo on 2011-09-17
Ok, so the rotation button on the bezel is working now, and it rotates correctly, but now the digitizer pen is mirror to the arrow. Is there a way to calibrate?

---

### Post by diasf on 2011-09-17
It's a known bug on wacom drivers, happened to me. Check the magick-rotation quests page, there's a working patch there

---

