---
title: "Unable to play music CDs in Ubuntu Studio 8.04"
date: 2008-08-19
forum: General Help
---

### Post by ashlonfolk on 2008-08-19
I have just installed Ubuntu Studio 8.04 on two of my laptops. I have tried to play a music CDs on both but it won't work, instead telling me that no data can be found. The drive appears, and I can see the files in it, but when I go to play them in a player it says it can't find any data. 

I have tried with a range of standard and burnt CDs and the result is the same.

I formerly had a Dapper install on one of the laptops for around 2 years with no such problems. 

Interestingly, the other laptop had SimplyMEPIS on it, and it had been having similar problems playing CDs as of late as well. Early on they played, but recently they stopped working. Perhaps due to a bad upgrade?

Any ideas?? Any fixes??

Thanks in advance for any help :KS

---

### Post by Gondee on 2008-08-19
Try ```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by ashlonfolk on 2008-08-19
Yeah, I've already done that.

Here's the error I get when I click on 'Audio Disc' in the 'Places' file of the Main Menu:

> Error

Could not open location 'cdda://hdc/'

There was an error launching the default action command associated with this location.

If I go into the home folder, and double click on 'Audio Disc' from the side menu in there, I can see all the files. When I double click on one, it opens up Totem Movie Player, but then gives me the following error:

> 
An error occurred

Stream contains no data.

I just tried opening one of the files in Kaffeine instead and this came up:

> Kaffeine-Xine...
Ok.
KDE...
Found version: 3.5.9
Ok.WIN32 Codecs...
No WIN32 codecs found in /usr/lib/win32. You're not able to play Windows Media 9 files, newer Real Media files and some less common formats. Download the codecs here: [http://www.mplayerhq.hu](http://www.mplayerhq.hu).
libdvdcss...
Ok.
DVD Drive...
Ok.
DVB-Device...
No DVB-Devices found. The DVB related functions will be hidden.
Distribution...
Ok.
RESULT: Found some problems, but nevertheless Kaffeine may work.

So that explains part of the problem maybe - that the files on the CDs are .wav

I know I can play .mp3s that are already on my computer - I'm not sure about ones on CD. I'm not sure about other types of audio files either.

I guess I'll try visiting [http://www.mplayerhq.hu](http://www.mplayerhq.hu) and see what I can find to fix the lack of Win32 codecs...

---

### Post by ashlonfolk on 2008-08-19
Ok, sorted it out.

I did go to [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/) but it was all a bit too complicated for me. 

I typed this into terminal, to try downloading mplayer through there instead:

> 
sudo apt-get install mplayer

The player installed but the problem wasn't fixed.

I then decided to try typing this, to download the w32 codecs directly:

> 
sudo apt-get install w32codecs

And it worked! CD's with .wav files now play in Kaffeine.

I still can't open Audio CDs from the 'Places' folder in the Main Menu, however. I still get the error with the default action command associated with the folder?

---

### Post by Djunky11 on 2008-08-21
Hi I am also experiencing the same problem, and I am using a PC.  I've tried multiple players with different codecs and am still unable to play CDs. My files are apparently .ogg format but I've had no such luck in playing them using multiple methods described by others.

---

### Post by ashlonfolk on 2008-08-21
Hi,

You should try pasting this command into terminal, and press enter:

> sudo apt-get install w32codecs 

This sorted the problem for me in terms of playing .wav files (which seem to be what most CDs contain). I'm not sure about the .ogg problem though - perhaps start a new thread on that one? Someone might know a command to fix that problem.

My ongoing problem is that in my main menu, under 'places', the button that is supposed to link to my CD drive doesn't work. I'm not sure how to fix that - still looking.

---

