---
title: "ATI catalyst 9.4 installation issues"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2009-05-18
I guess ill have to rewrite again cuz the thread is way back there now cuz of many ppl posting and i still need help..

I wasnt happy with the compatible stable drivers for ubuntu when i used wine to play a game. Everthing is fine, just way too laggy.

I decided to download from AMD the latest drivers for my HD 3850, the version 9.4 for the catalyst drivers. Its a .run file.

I had the old drivers installed still. (Installed with envyng btw).

And I typed sudo sh ./THE_WHOLE_FILE_NAME.run 

Everything got setup. but when i tried to use the Ati control center it doesnt works at all. It says that linux catalyst drivers bla bla bla failed to initialize and it was asking me to download the appropiate drivers for my card or do aticonfig.

I did both things, downloaded and picked myself the drivers, installed it agian and nothing. I used on terminal the sudo aticonfig --initial .. then it says that it couldnt find screen whatever. I read in aticonfig that if i have this prob then i might wanna do sudo aticonfig --initial -f.

Seems that it saved a backup whatever of some file. Then i did sudo aticonfig --initial again. And seemed that there was no problem this time. I then tried to start control center again and still nothing. The same message pops up. I cant play now nothing.

Then someone told me to revert all the changes. And use go to system--administration-- hardware drviers. There is a driver in there.. i did enable before uninstalling by the way cuz i thought it was that the problem.

But it seems not, and by the way i dunno how to revert the changees. I got alot of debs generated all over my home folder .. I jsut uninstall the drivers from envy.

at this point it seems that having the drivers installed from envy and having the drivers from "hardware drivers" disabled everything is slow .. even moving windows.. when i enable it i cant go to high resolutions.. and i guess not even to play a crap....

i dunno its a whole mess i did .. and ubuntu doesnt seems to install even the drivers on envy .. i dunno what to do .. is there a recovery mode in here like in windows to revert back the changes? i need help badly with the latest drivers..

---

