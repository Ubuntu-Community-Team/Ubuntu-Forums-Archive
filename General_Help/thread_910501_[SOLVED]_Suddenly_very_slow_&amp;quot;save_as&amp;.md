---
title: "[SOLVED] Suddenly very slow &amp;quot;save as&amp;quot; menu"
date: 2008-09-04
forum: General Help
---

### Post by lariosa42 on 2008-09-04
Hello,
I am fairly new to Ubuntu.  A few days ago, something strange started to happen.  When I hit "Save As" in a program (Firefox, OpenOffice, etc.), the window goes gray for about 30 seconds while the "Save as" window loads.  This has never happened before.  I can hit "Save" with no problems.  At first, I thought this would be minor annoyance, until I realized how often I hit "Save As."  I can hardly get any work done!  Any suggestions?

The only changes I have made recently to my computer that I can think of has been installing some new libraries trying to get my graphics card to work.  I have also posted about this here:  [http://ubuntuforums.org/showthread.php?t=832253](http://ubuntuforums.org/showthread.php?t=832253).

Thank you in advance for your help.

---

### Post by lariosa42 on 2008-09-11
Hello?  Anybody out there?

---

### Post by lariosa42 on 2008-10-07
I haven't had any replies in almost a month, so I thought I would be more specific about the problem I'm having.

In any program, when I do File-->Save as, the "Save As" window comes up, but has no text in it.  It takes about 30-45 seconds to load.  During this time, I can use any other program, but the one stuck in "Save as" is effectively frozen.  This doesn't happen with any other menu option.  For example, File-->Save works normally.  (I'm running Hardy 8.04.)

If anyone could help with this somewhat crippling problem, I would really appreciate it.

---

### Post by lariosa42 on 2008-10-10
Well, I'm sorry to say that the amount of help on my question has been very disappointing.  Nobody even asked for more information.  I will look for help elsewhere.

---

### Post by lukjad on 2008-10-10
Sorry to hear that. I just saw it as it was at the top of the heap. Did you have any updates? Also, how old is your PC?

---

### Post by lariosa42 on 2008-10-10
Oops, I forgot to hit reply (I'm not sure how to delete this message).  Please see reply below.

---

### Post by lariosa42 on 2008-10-10
> **lukjad007 said:**
> Sorry to hear that. I just saw it as it was at the top of the heap. Did you have any updates? Also, how old is your PC?
Thank you for responding! =)

My PC is a Dell Inspiron E1405 running Ubuntu 8.04 Hardy. It's about two years old. I had been running Hardy just fine for a few months, and then this slow "Save as" problem started. It was right around the time I was installing a lot of updates, codecs and other things trying to get my video card and video players working correctly. I am not sure if that caused the problem as I didn't try "Save as" for at least a few days afterwards (also, like the newbie I am, I didn't think of keeping track of what I was installing).

This problem has been occurring in the same way ever since, in OpenOffice, Firefox, Winefish, GIMP, etc. The only program I have noticed that it doesn't happen in is Kile.

Sorry if my last message seemed harsh, I was just getting frustrated. Your help is greatly appreciated!

---

### Post by lukjad on 2008-10-10
Try opening the Terminal and opening a program. start up a program that you noticed the problem using the "Save As" button. Then, make a minor but distinct change in a file and choose "Save As". Paste the output here. 

Just a thought, but this may be a hardware problem.

---

### Post by Sycron on 2008-10-10
Try the live cd and see if your problem persists.

---

### Post by lariosa42 on 2008-10-11
Hello, thanks for the replies.  There doesn't seem to be any additional output when I run a program from the terminal and hit "Save as."  The problem is also not fixed by running through the terminal.  

However, "Save as" works just fine when I run off the Live CD.  

Also, there has been no problem if I just use "Save."  Once a file is saved with "Save as" (which takes about 30 seconds), I can "Save" it all I want.

---

### Post by lukjad on 2008-10-11
Alright, with Sycron's great idea, we can now assume it's not the hardware at fault here. Back up your home folder to an external media like an external hard drive or USB key or burn it to a CD/DVD and then delete the contents of your home folder. Then, make a new document and save it. Close it and then make a change and click "Save As". Tell us if the problem  persists. If it doesn't, then it was just a misconfiguration somewhere. If the problem is still there then we will know that it is something to do with the installation.

---

### Post by lariosa42 on 2008-10-12
> **lukjad007 said:**
> ...it's not the hardware at fault here. Back up your home folder to an external media like an external hard drive or USB key or burn it to a CD/DVD and then delete the contents of your home folder. Then, make a new document and save it. Close it and then make a change and click "Save As". Tell us if the problem  persists.

Hmmm... sounds like a good idea, but my home folder is over 75 GB.  I appreciate the suggestion, but is there maybe a slightly more workable way that won't require burning 15 DVDs?

---

### Post by earthpigg on 2008-10-12
is there anything new and/or unusual in your "places" thing on the left side of the "save as" window?

did your home folder go from a small size to to ~75 gigs right around the time this started? (ie, you moved all your movies and such into your home folder just prior to this starting)

if not:
in regards to backing up your home folder... i think you can leave the multimedia, movies, mp3s, pictures, etc in place and just backup/delete the rest, such as the hidden folders that contain settings information.

---

### Post by lariosa42 on 2008-10-12
Brilliant!  It's fixed! =)

I looked at the "Places" panel on the left side of the "Save as" menu.  In this menu under "Bookmarks" was EVERY music album I have (somewhere around 650 albums).  I never use "Bookmarks," so I never noticed this (I don't know how they got in there either).  Whenever I would hit "Save as," all 650 bookmarks had to be loaded into the side panel, which obviously caused a massive slow down.

For reference for others, to delete the bookmarks, open a Nautilus window (type "nautilus" in the terminal).  Then from the menu: Bookmarks-->Edit Bookmarks and click the "remove" button in the window that appears (yes, I clicked it 650 times).  Problem solved!

Thank you to everyone who replied on this question.  I feel like I have my computer back!  Go Ubuntu, and go Ubuntu Forums!

---

