---
title: "Editing your favorites in Netbook-Launcher."
date: 2009-09-05
forum: Hardware
---

### Post by TH3_D0ct0R on 2009-09-05
Alrighty so as I was searching around the gconf-editor and i found the favorites part of the netbook launcher. 

A little backstory.

Now I was having some problems. I love the Joliclouds Prism apps and their ability to one click install. [[COLOR="Blue"]Click here to check it out.[/COLOR]](http://www.jolicloud.com/) 
But I think the NBR's new interface ( the one on 9.10 is gorgeous, and I was not willing to wait for Jolicloud to change their's so I went and got the Alpha 5.
Then I missed my Newsmap Prism app, the Netvibes app, the XKCD prism app, and many more. So I decided to make a prism app myself 
> no difficulty at all, just enter the url and bam you have an app, if you want help juss pm me 
I successfully made the Hulu app, except I couldn't access it (note: conveniently) through the NBR launcher. So while I was looking for ways to edit the icons of the prism apps currently in the repo's (i.e. Gmail, Twitter, Facebook, because they looked horrible scaled to size for the NBR). I found the favorites part of the gconf-editor 
```
**apps>netbook-launcher>favorites**
``` 
after you get there you will find all of the different apps on your favorites section in the netbook-launcher. I edited the desktop_file where for cheese (mainly because i didn't use it) to this  ```
**desktop_file | /home/username/Desktop/Hulu.Desktop**
``` to the shortcut where my prism app is. 
ok so if this doesnt make sense im sorry... just say something and i'll try to explain it works wonderfully for me... :)


Th3_D0ct0R

---

### Post by wpf999 on 2009-09-15
Hi,
I'm using UNR 9.10 and am having probs changing Favorite icons. I used the webfav in Firefox to create favorites on the desktop but they all have default icons.
On 9.4 I just went into main menu ancd changed the icons there. However, the main menu in 9.10 doesn't show Favorites.
Any idea how to cutomise the icons in 9.10?
Thanks in advance.
P.S. I also tried from Gconf editor, as you suggested, but there isn't an option for changing the icon.

---

### Post by TH3_D0ct0R on 2009-09-15
well the way I did it was to right click on the desktop icon and then select properties and click on the icon in properties and it will let you select a new icon for it. 

Now this wont work for the icons in the window-picker cuz im sure that has something to do with the scaleables folder in pixmaps. And if i ever feel like getting around to it ill try and look it up. 

If you are looking for good looking icons the best i can give you is to google it. 

I'm sorry if this is not understandable, I just woke up and am still kinda tired. :) but hopefully this helps if it doesn't just let me know and ill get on explaining it better. or someone else will :).

Th3 D0ct0R

---

### Post by wpf999 on 2009-09-15
Hi,
As far as I can see, in Ubuntu Netbook Remix there's no option to do that when you right click on an icon in Favorites.
All I can see is Open and Remove.

---

### Post by TH3_D0ct0R on 2009-09-15
I thought you made desktop shortcuts. I meant go to the desktop and right click on the icon there. So go to the files and folders tab and browse to the desktop right click the icon there.

---

### Post by wpf999 on 2009-09-15
Thanks for replying. I've just tried that but there are no icons there, even if I show hidden files. :-( It's also strange that Favorites isn't showing up in the main menu.

---

### Post by TH3_D0ct0R on 2009-09-15
hmm yea i have no idea. well if you can find where the favorite is stored you can edit it from there. I have never dont the whole favorites thing. there are alot of things not perfect with this Netbook remix but there are so many things that are amazing. :) im sorry. if i get around to it today i will try the favorites thing and see if i can get it to work

---

### Post by wpf999 on 2009-09-15
OK. Thanks for trying. I'll see if I can find out where favorites are stored too.
I agree with you: UNR 9.10 is great!

---

### Post by LoSt180 on 2009-11-03
I found where the favorites are hidden. Go to your home folder and show hidden files. Navigate to ~/.gconf/apps/netbook-launcher/favorites/
There is a %gconf.xml file, open it in gedit, and you can reorder the entries.

I'm not sure how to edit the icons of the launchers like in the menu list, but I did notice that for everything you add to favorites (ie., clicking the little plus sign), it creates an entry in ~/.local/share/applications/ and that xml file links back to there.


After some additional digging, you can right-click the .desktop file (in the folder above) select properties and customize the icon from there.

---

### Post by tc24 on 2009-11-04
Hi.

I've got a problem with a rather annoying blank space that has shown up on my Netbook favourites menu.  It's like an icon should be there, and isn't and it has left a gap which I can't get rid of. 

I'm at work at the minute but once I get home I will be scrabbling about in the favourites file to see what is lurking in there to cause my phantom blank space.

Thanks for discovering it's location:D..I did have a little poke around but wasn't successful and I'm rather new to ubuntu.

---

### Post by LoSt180 on 2009-11-04
looks like you can change the order in gconf-editor instead of fudging around with that xml file.

---

### Post by tc24 on 2009-11-04
Yup..that did the trick, folks.  I found the offending bit of info in the apps folders in the Favourites folder.  Was a shortcut I'd made to a folder on the second ssd.  I just edited it out and my blank space took a walk after a reboot.  

Cheers for the info :)

---

### Post by LoSt180 on 2009-11-04
> **tc24 said:**
> Yup..that did the trick, folks.  I found the offending bit of info in the apps folders in the Favourites folder.  Was a shortcut I'd made to a folder on the second ssd.  I just edited it out and my blank space took a walk after a reboot.  

Cheers for the info :)

A simple logout/login fixes the entries as well, so you don't have to do a full reboot.

---

### Post by moodle on 2009-11-08
The folder ~/.gconf/apps/netbook-launcher/favorites/ doesn't exist on my computer!  Any other ideas for editing the favorites?

---

