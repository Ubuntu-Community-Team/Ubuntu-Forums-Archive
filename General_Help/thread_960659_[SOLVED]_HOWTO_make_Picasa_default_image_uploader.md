---
title: "[SOLVED] HOWTO: make Picasa default image uploader"
date: 2008-10-27
forum: General Help
---

### Post by tedmcdonald on 2008-10-27
Howdy Folks

Currently when I plug in a camera, F-Spot starts downloading images.

However, I would prefer to have Picasa do this.

How do I set it so that Picasa does it?

Thanks.

---

### Post by mgmiller on 2008-10-27
Open System > Preferences > Removable Drives and Media.  The first tab is the camera tab.  It will have a check box and a command to start f-spot.  Change the command to picasa.  (Kind of a vague answer, as I don't know the exact command for picasa, but at least this is where you put it once you figure out what it is)

Edit:
I just tried entering picasa from the command line and it opened picasa, so if you just change the command as noted above to picasa, it will start the program.  Then just click the import button in the upper left corner.

---

### Post by tedmcdonald on 2008-10-27
This is weird, I did as you suggested and went to Open System > Preferences > Removable Drives and Media and put picasa in there instead of f-stop (actually I think it was picasa already).  

However, when I plug my camera card into the USB ImageMate CF card reader, F-stop immediately opens up and starts downloading images.

Any idea why that would happen?

Thanks in advance.

---

### Post by mgmiller on 2008-10-27
You said you were plugging in your camera.  The instructions I gave you will work if you attach your camera (assuming it's supported) via USB cable to the computer.

You are actually inserting an SD card in a card reader.

The following is not real intuitive (what are the Gnome devs smoking?):

Open your home folder.
Click on Edit > Preferences
Go to the Media tab.
Click the drop down next to photos and change it to what you want.

In Hardy, I think there was a limitation on what you could put in there.  In Intrepid you can put anything.  You may need to tell it to do nothing but have the "Browse Media when inserted checkbox marked so at least you can browse the pictures on the card.

That should do it.

---

### Post by tedmcdonald on 2008-10-27
Oh yes, this is much better.

I have done what you said, but I had three options:

1.  Open F-Spot
2. Open Folder (I think with a Nautilus icon)
3. Do nothing

I didn't see anyway to pick a different application.

Best Regards, BFT

---

### Post by Locke_99GS on 2008-10-27
You should have the option to "Open with other Application" on that list in Nautilus' preferences. Mine does. If you do, have it open Picasa from there.

---

### Post by mgmiller on 2008-10-27
Once you have set the option to do nothing as in my last post, when you insert the card, a window should open showing you the files.  Right click one of the jpegs and go to the "Open With" tab and select picasa from there.  If it isn't in the list, click the Add button and pull it off that list.  From then on any jpeg will open with picas by default.

You will still need to import all the pictures into picasa.

I think this would be a lot easier if you just hooked up the camera via USB cable and let picasa pop up and then click the import button.

---

### Post by tedmcdonald on 2008-10-27
Howdy mgmiller

That works.  Thanks.

I take the card out of the camera to save batteries.  I don't have a power adatper for the camera.

Best Regards, BFT

---

### Post by mgmiller on 2008-10-28
> That works.  Thanks.

I take the card out of the camera to save batteries.  I don't have a power adatper for the camera.

You're welcome.  

I understand the battery thing.  If it ran down while transferring, it would be bad.

Don't forget to mark this thread as "solved" by going to the thread tools at the top and clicking solved.

Also, if you would click the "thank you" gold star next to one of my helpful posts, I would get a valuable credit suitable for framing or wrapping fish.  :lolflag:

---

