---
title: "Pixma MG8220 - doesn't print photo"
date: 2012-05-07
forum: Hardware
---

### Post by Lubelaczek on 2012-05-07
My Pixma MG8220 is working well if I print simple doc from word or other app (using 12.04 64bit). If I paste photo into word doc it prints it with no problems. However if I try to print same photo from gimp or directly from its location (from file manager) it wakes up printer, it looks like is preparing to print but nothing is coming out. Then printer simply "pretends" that everything went well (no error messages) and goes to standby mode after usual time.
Does anyone experience similar behavior? What could be a problem, any ideas?

---

### Post by Lubelaczek on 2012-11-19
I did not do any research on this problem hoping that next release will solve it. Unfortunately it is not different with 12.10 and Gimp-2.8.
Any idea what could be the problem?
Any one with this printer maybe (Canon MG8220)?
Does it work for you?

---

### Post by pdc on 2012-11-20
which printer driver are you using? 

Canon provide a deb packaged driver for the 8200 series

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100396202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100396202.html)

---

### Post by Lubelaczek on 2012-11-20
Sorry, but where and how I can check my driver ver. I am not that deep into linux yet. Honestly I am quite "green" in this area. Doing upgrade from 12.04 to 12.10 I assumed that all drivers will be updated to latest possible/recomended. Am I wrong?

P.S.
Just after posting this I found some info that says: clearing EXIF data from file/picture that has to be printed may resolve problem. I did not try this yet. Have to wait few hours. I am at work now, away from the printer.

---

### Post by pdc on 2012-11-20
> which printer driver are you using? 

...........what I meant was............when you go to print, you select a listed printer........eg HP1234 or Fuji veracity or Canon MG2160 or gutenprint or foomatic ............... meaning what is listed in your printer options.......

.....I am guessing you don't have the Canon printer installed; I would recommend you do ...........

get it from the link here that is also in the previous post

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100396202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100396202.html)

it comes down as a [COLOR="SeaGreen"]cnijfilter-mg8200series-3.60-1-deb.tar.g[/COLOR]z 

....leave the printer [COLOR="Magenta"]turned off[/COLOR] before you start downloading....

1) If you select to download;

2) and select the "open with archive manager" option;

3) and then right-click on the [COLOR="SeaGreen"]cnijfilter-mg8200series-3.60-1-deb[/COLOR] file it shows you ......

4) and select **[COLOR="Blue"]EXTRACT[/COLOR]** and choose your desktop as the place to extract to ...when you click to do it ..it will then offer to show you the files it has extracted; say yes to this;

5) you should then see an [COLOR="Magenta"]install.sh[/COLOR] script

6) double-click on it......the view that is in the thumbnail that I enclose below should be seen.......

7) choose [COLOR="Magenta"]run in terminal[/COLOR].........a terminal will open.......the install script should do things for you; it will likely ask you to turn the printer on after the script starts running, and if your printer has a wifi or usb connection choice, it will ask you which you want.......

8) it should all be configured then ............

---

### Post by Lubelaczek on 2012-11-20
I do have Canon listed in print dialogue while in GIMP or any other app.

I tried to follow your procedure (thank you) however it doesn't look like changes anything. I went all the way to step 7, clicked "run in terminal" and it appeared for fraction of second then disappeared. No questions or any other activity.

When I go to (System Settings)Details/All Settings/Printers there is Canon only and properties seemed to be ok. See attachment. Yet it does not print from GIMP but perfectly ok from LibreOffice Writer (screenshot form GIMP) at the same time. I am going to remove exif data from file created in GIMP and try to print it. We'll see...

P.S. (next morning)
I did download them again this morning and tried to repeat whole procedure. Since 7:00 AM I'm working and have no access to that printer. But the good news is it asked me for admin pass and went to install process. Hope the fact that I stopped in the middle will not mess it up.

---

