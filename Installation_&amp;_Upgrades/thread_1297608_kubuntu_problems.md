---
title: "kubuntu problems"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by curtk69 on 2009-10-21
installed 9.04 on my compaq presario 2100.
this laptop is fairly old. 2001- 2003 about so i am happy most things work but there are some nagging problems that have startd recently.

1. most files wont open directly from firefox downloadss no matter what type they are.
it always asks which application then lists only folders not any apps to choose to open the file.
so i have to manually open amarok for eg. to open a music file, search for the file then click it.

2. in firefox only 4 recently opened sites will showup in the dropdown list of urls and to blue out the url and start typing a new one i must clicl the ubuntu symbol several times

3.my wireless hookup messed up ahile ago now i can only connect directly to the modem and about the same time the kde wallet and etho one popup screens start coming up everytime i reboot.
i am hardwired so i dont need a popup asking me to connect o wireless anymore since it wont work anyways and whats the kde wallet for?

4. my thunderbird acount receives email but keeps asking for a password to send outgoing mail. i thot i used the same password the sasktel.net email provider gave me but it doenst seem to work and no password box appears in the outgoing server settings?

5. this computer has an athlon xp 2400 and 576 mb ram so it shud be pretty snappy and fast correct? but it seems no faster than windows xp ?

---

### Post by curtk69 on 2009-10-21
plus i cant find how to change screensavers or desktop background.
i found n tried installing a new theme but it didnt seem to take and theres no option for screensavers?

also the automatic update thing always shows 4 updates that fail or cant be installed plus when it does install other updates it always ends with an error message so i dont know if it actually installed?

can i get my blackberry storm to hookup to kubuntu?

i wish i could have dualbooted my windows xp with this kubuntu but the options while installing either were not clear or didnt give me a dualboot or partitioning option

---

### Post by wandalalakers on 2009-10-22
Try using Kubuntu 8.04 or Linux Mint 5 KDE to see if you have better luck.

---

### Post by dazer26 on 2009-11-05
I have Kubuntu 9.10 installed on my presario 2100, same as yours.  I had 9.04 installed before, with little problems.  I had issues with grub2 and 9.10 on that laptop, so if I were you I wouldn't try 9.10 just yet.

1. This is kinda strange, most stuff I download in firefox I can double click from the download list and start up in the proper apps.  Try going into system settings, go to the advanced tab and click on file associations.  See if everything is set up properly in there.  Or see if Konqueror works better (or google chrome).

2. Not sure what the issue is here, again try Konqueror or Chrome.
you can download chrome here, it's still in development for linux so there could be some bugs, but it actualy runs great for me.
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

3. I hate the KDE wallet personally.  I think it is there for enchanced security, but it reminds me of vista like pop-ups every time you try and do stuff.  I'v never tried to remove the wallet before, but i'd imagine it would break a lot of kde stuff.

4. Don't use a mail program, can't help ya there sorry.

5. I upgraded my presario 2100 to 1gig (max amount you can put in it) but it seemed to run pretty well with 512 before.  Turn off the desktop effects if you want it to be snappier.  I personally leave them on(just nothing too fancy), but the 3d graphics on that laptop arn't the best.

6. To change the wallpaper, right click anywhere on the desktop and go to desktop settings.  You can also change the theme there.  These desktop settings arn't in the system settings as you would think, something they should fix. For screen savers, you do go into the system settings, then  click on Dekstop, and on the left hand side you should see Screen Saver.
 
7. Kpackagekit can't do certain upgrades, it's some kind of bug, I think it may be fixed in 9.10, but i'm not sure.  Instead of using the kde package manager, use synaptic(install it from kpackagekit).  It is supposed to be for gnome, so it looks a bit out of place in KDE but it works great.  When you open it up for the first time, hit refresh, then mark all upgrades, then apply.  After that you will see that kpackagekit doesn't have any upgrades for you anymore.

8. Never had a blackberry, so no clue.

9.  I dual boot with my Desktop comp. no prob, haven't tried on the 2100 tho.  Mine only has a 40 gig HD, so there isn'a a whole lot of room for 2 OS's.  Either way to dual boot you have to have windows installed first, then install Kubuntu.  It should give you the option to resize your HD (backup first!) and istall Kubuntu beside windows.


edit: One thing I forgot about this laptop.  I'm not using the internal wireless either, I got a pcmcia card instead.  There is some sort of glitch between using a wireless card like that and running on battery power that locks up the computer.  It's an acpi issue and booting with noacpi fixes it, but then you can't see your battery life or cpu temp...it's very annoying.  Runs great plugged in tho.

---

