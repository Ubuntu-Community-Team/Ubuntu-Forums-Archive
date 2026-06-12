---
title: "Canon iP1500 PIXMA inkjet printer"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by walterius on 2006-06-10
Linux doesn't see it and none of the Search-here-for-your-linux-printer guides even mention it.

Is there anything I can do? :-k 

I'd hate to think I wasted my fifty bucks. Such a nice little printer. Cheap ink, too.

Walterius

---

### Post by Dr. Nick on 2006-06-10
If your just looking for a driver to use try the included bjc-7000 drivers. They seem to be pretty basic drivers that work on a wide range of canons.

---

### Post by walterius on 2006-06-10
Thank you, Dr. Nick. I did as you suggested.

I got to the point in the printer setup dialog where it asks for a "PPD" file. What's that? Where is it?

Walterius
Confused in Fort Lauderdale

Entirely OT: And how do I set up one of those cool profiles preferably with picture that accompanies many posts?

---

### Post by paulvandenberg on 2006-06-10
I shelled out 29 euros for Turboprint. Their package includes drivers for a slew of printers. You can try it first without buying, but anything better than draft prints with the Turboprint logo on it until yo install a license key. I have a PIXMA iP2000 and Turboprint works great with it. The address is [http://www.turboprint.de](http://www.turboprint.de) (german) or [http://www.turboprint.info](http://www.turboprint.info) (english).

---

### Post by razahel on 2006-06-10
[QUOTE=paulvandenberg]I shelled out 29 euros for Turboprint. Their package includes drivers for a slew of printers. You can try it first without buying, but anything better than draft prints with the Turboprint logo on it until yo install a license key. I have a PIXMA iP2000 and Turboprint works great with it. The address is [http://www.turboprint.de](http://www.turboprint.de) (german) or [http://www.turboprint.info](http://www.turboprint.info) (english).[/QUOTE]

do you have the printer on your usb port andtestet to print 4 on 1 page?
please tell me if it works,because mine does not.

regards
razahel

---

### Post by paulvandenberg on 2006-06-10
I never tried printing 4 on 1 page. My printer is connected to my kids' Win 98 computer and I print to it rhough Samba.

---

### Post by razahel on 2006-06-10
[QUOTE=paulvandenberg]I never tried printing 4 on 1 page. My printer is connected to my kids' Win 98 computer and I print to it rhough Samba.[/QUOTE]

ok thx, anyway poor me because i need this feature and cups will not do it.

---

### Post by Dr. Nick on 2006-06-10
[quote=walterius]Thank you, Dr. Nick. I did as you suggested.

I got to the point in the printer setup dialog where it asks for a "PPD" file. What's that? Where is it?

Walterius
Confused in Fort Lauderdale

Entirely OT: And how do I set up one of those cool profiles preferably with picture that accompanies many posts?[/quote]


Hmm for this I assume you are using gnome and the System-Administratin-printing dialog. I dont have my printer hooked up to this computer but these steps should still be pretty accurate.

Step 1 of 3

I assume you know this part, If your printer is on a USB port (should be if possible for initial setup, I would avoid network printer at this point if possible. Network printer isnt much different, Its just another variable and oppurtunity for errors. If your printer is hooked up locally and is not detected at all here then thats a probles, one I have never faced and dont know how to fix

Step 2 of 3

If you choose the autodetected printer in step 1 or correctly specidied the uri to a network printer then Pick Canon from the top dropdown list, scroll down and choose the first bjc7000 you see. The driver should then read High Quality Image (gutenprint). Then press foward. The install driver button is not needed here. That is needed if you find a ppd ( printer driver file) online and save it to your system.

Step 3 of 3

Just customize to your liking and hit apply.


OT asnwer. Hit your User CP buttom on the dark brown bar under forum navigation. Look at it to set that stuff up. The picture is the avatar and the other stuff appears in various parts of the CP

---

### Post by razahel on 2006-06-11
fist: printer is visible via autodetection
sec: tried gutenprint driver its the same result
third: i can not really customize linking because choosing /dev/usblp0 link in debian does not work anymore only usb://Canon/...

here is what the gnome interface says after trying to print with the bjc3000/bjc4000 driver:
Unterbrochen: /usr/lib/cups/backend/http failed

---

### Post by walterius on 2006-06-11
Dr. Nick,

Thanks to u i am making progress. I much appreciate your help.

I edited my profile.

I added the Canon iP1500 PIXMA printer, using the suggested BJC-7000 driver. (There is no iP1500 driver and the Canon site does not list one for linux.)

I tested printing with a simple gedit text file.

o Print preview works perfectly. Looks really cool.
o Nothing prints. Printer icon appears, then goes away, no printing.

---

### Post by Dr. Nick on 2006-06-11
Just saw this [http://ubuntuforums.org/showthread.php?t=93265&highlight=ip1500](http://ubuntuforums.org/showthread.php?t=93265&highlight=ip1500)
That is another thread about the ip1500 with a  install script that supposedly works. I cant test it out since mine is a different model, but it may be worth a shot, If it doesnt work they will probably be more knowledgeable then me.

---

