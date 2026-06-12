---
title: "F-stop still default for media cards??"
date: 2008-09-21
forum: General Help
---

### Post by bunntybrad on 2008-09-21
Hi there I have been thru the posts and have done the change to make gthumb load when I plug my camera in ! Yeah and thank you for that.

The question is about the next step in getting rid of F-stop
When I take the media card out of the camera and plug it into my card reader F-stop is still the default program, there are NO choices to choose something else as near as I have found to date.

Does anyone know where to change this so I can choose the program of my choice to manage my media cards? I would like gthumb to open the media card from the reader as well as from the camera, ( i dont always have the cable handy for the camera) 
Thanks in advance.

Brad

---

### Post by bunntybrad on 2008-09-26
Wondering if anyone has managed to accomplish making Gthumb open media card when put into a reader? (instead of fstop) 

Thanks

This is the command i have in " SYSTEM/Preferences/Removable Drives and Media/Digital Camera"  gthumb --import-photos

opens gthumb when camera connected but not when media card inserted into a reader.
 thanks
Brad

---

### Post by mc4man on 2008-09-26
I don't have a card reader so hard to tell. See if when you go to file management -> media and change the action for 'photos' to 'open folder' or 'do nothing' if it affects what happens when you insert card in reader.
*If it does* it will be easy to create and set a gthumb option.

This is what is associated with that setting ('photos'
> x-content/image-dcf=gthumb.desktop;f-spot-import.desktop; 


see screen

---

### Post by bunntybrad on 2008-09-29
Thanks tons Mc4man, That is the section i needed. it does control the card reader from there. I had not been in that area yet, found some other stuff too that was on my mind.
You say it will be to easy to create a gthumb option??  Are you able to continue the educating??
I assume the piece of code you provided needs to be put some where some how ;O) 
"x-content/image-dcf=gthumb.desktop"  Thanks again for taking on this question for me.
Brad

---

### Post by mc4man on 2008-09-30
This will be very easy though we need to find out if gthumbs default launch command is suitable. That command is gthumb %U.
The gthumb1 you saw in my screen is using gthumb --import-photos.

While a little of below may be unnecessary if you do it every will work out (due to I'm never online when you are  


So we'll try gthumb %U first.

So to prep things do this (even if redundant.
Go to file management -> media and change everything in the first 4 option boxes to either another app or open folder. Then close out. Then open fm. -> media again and switch everything back. (just making sure you have a mimeapps .list and proper line. (actually giving you a few 'extra' lines if you are inclined to add dvd or cd player choices

I'm posting a screenshot (1) from a recent install that has almost nothing set or added so it will be sparse, probably similar to yours.

Go to home folder -> .local -> shared -> applications and see if there is a gthumb image viewer icon there. If it's** not there** run this

```
cp /usr/share/applications/gthumb.desktop ~/.local/share/applications/gthumb.desktop
```

If it **is there** or after above then open mimeapps.list (just double click on it)
and look for this line
> x-content/image-dcf=f-spot-import.desktop;
and add gthumb.desktop; to it. Needs to be exactly like this

```
x-content/image-dcf=f-spot-import.desktop;gthumb.desktop;
```
Notice no spaces and ends with a ;

Now go back to fm -> media and choose gthumb (if you go back to mimeapps.list you see gthumb.desktop has now moved in front of f-spot - the list is dynamic, hence no room for 'format' mistakes (current default choice is listed first

This will give you gthumb running off of gthumb %U. 
If that's unsuitable we can make a 2nd one but the name has to be different. (both the name of the copied .desktop and the **name shown inside** the .desktop. Based on thread linked below that shows theory/methods to make almost anything a default choice with any available launch command.


If %U doesn't work right, then the method is below or I'll post some stuff you can copy and paste if your not 100% clear. I'm thinking that for a 2nd .desktop (if needed) ```
Exec=gthumb --import-photos
```.

If you need to try, follow the mplayer instr. starting at the cp. command( and note how you must change the **destination** name of the .desktop slightly - something like gthumb-card.desktop. Also the internal name (gthumb1 would suffice

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by bunntybrad on 2008-10-01
That was Extremely clear and precise!! Thank you so much for taking the time to get me thru that. 
I assume similar steps can be followed for other photo programs I see alot of posts inquiring  about such things. 
Fstop is no longer a default on my machine I look forward to doing the same on the laptop too.
Thanks again for the GREAT help. 
Photo work is pretty much my primary computer work, so this has made me a very happy Ubuntu user!
Cheers
Brad

---

