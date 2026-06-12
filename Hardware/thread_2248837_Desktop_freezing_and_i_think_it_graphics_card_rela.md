---
title: "Desktop freezing and i think it graphics card related"
date: 2014-10-17
forum: Hardware
---

### Post by Tabb on 2014-10-17
Just did a fresh install of Ubuntu 14.04. I had Xubuntu running before but it crap.
When i was running xubuntu my pc was freezing alot, with the new install its lasts alot longer (i can actually do homework).

From what i gather its Graphics card related. I have a nvidia GeForce GT 430 put in there. 
The rest of my pc specs are:
32bit intel core 2 quad Q6600 @ 2.4GHz
3Gb memory
When i go to system settings - overview the graphics card shown is Gallium 0.4 on NVC1 (I assume this is the built in one)

Now ive downloaded the right driver for the nvidia card.(from nvidia website). and now im trying to install a .run file.
ive tried the 'Allow executing file as program' and double click method. it just opens up gedit which then crashes.

ive also tried the terminal method of

[LIST=1]
[*]Open a terminal (Applications->Accessories->Terminal).

[*]enter cd /home/user/Downloads

[*]enter chmod +x some-app.run
[*]enter ./some-app.run
Which then comes up with 'permission denied' so i tried this:



[LIST=1]
[*]**if** step 4 fails with a message including 'permission denied', try entering sudo ./some-app.run (you will need to enter your password for this).

Which also doesn't work.

Im abit stuck now so any help would be appreciated.
Thanks.

[/LIST]

[/LIST]

---

### Post by Vladlenin5000 on 2014-10-17
You can install the proprietary nvidia driver at System Settings > Software&Updates and the rightmost tab "Additional Drivers".
You can't run the nvidia's script with X running in the terminal environment. You would need to open a console, stop lightdm (or other) and only then run the script. The good news is you don't need it as explained above.

---

### Post by Tabb on 2014-10-17
Well after many hours i figured out the manual way of doing it. I guess it was a good learning experience. But thank you very much anyway, if only i'd known sooner haha

PROBLEM SOLVED!

---

### Post by Vladlenin5000 on 2014-10-17
I'm glad it's working now and no doubt it was a much more enriching experience doing it the way you did.
Keep rockin'on :guitar:


Please use the thread tools to mark this one as solved so other can benefit.

---

