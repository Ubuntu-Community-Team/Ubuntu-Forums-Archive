---
title: "Sound works at startup, then nothing"
date: 2009-06-05
forum: Hardware
---

### Post by schwim on 2009-06-05
Hi there everyone,

I've got a machine that I put dropped a soundblaster card into so I wouldn't have to mess with the onboard sound.  When I start up the machine, it plays the welcome sound during the start of the desktop session, but when I try to do anything else(music, web, etc.), I can't get anything out of it.

I opened volume prefs and enabled all sliders on the alsa tab, pushing them all up, but I still can't get any sound out of it.

If I open sound preferences, the test sounds work when everything is set to "auto".  Going into amarok though, I can't get a peep out of it.

I'm fresh out of a fedora install that was using this setup successfully, so I know that the card is a-ok, but am not sure how to get Ubuntu to use it.

Thanks for any help,
json

---

### Post by vinutux on 2009-06-05
i experienced same prob on my friend's system with soundblaster 5.1 soundcard. But i can successfully solved it .... with playing aroun sound preferences in taskbar.....................

---

### Post by schwim on 2009-06-05
Well, I think I've got the sound working ok, but now I'm wondering if Amarok is a "clean" version?  I can listen to the internet feeds, but none of my local media(mp3's).

The configuration menu is barren and doesn't seem to show anything concerning allowed formats.

---

### Post by vinutux on 2009-06-05
use [COLOR="Green"]Banshee[/COLOR] ---a nice music player

type this in termianal    [COLOR="Red"] sudo apt-get install banshee[/COLOR]

home page [URL="http://banshee-project.org"]http://banshee-project.org
[/URL]


                              or 

songbird  an alternative to itunes

Download from getdeb here is link [URL="http://www.getdeb.net/app/Songbird"]http://www.getdeb.net/app/Songbird
[/URL]

home page [http://getsongbird.com/]("http://getsongbird.com/")

---

### Post by schwim on 2009-06-05
Thanks very much for that.  I used Songbird on my Win machine so tried to stay with that, but I used the script provided at help.ubuntu.com which errored out on my attempt.  I didn't know about the deb package.

Thanks again for all your help :)

---

### Post by vinutux on 2009-06-05
welcome welcome................

anyway what scrip u used ? ..............for what ?


2. Deb is nothing just same as .exe in windows ubuntu use .deb format for installing programs.


..............And song bird is not availabel in deb format from official site so download from here [URL="http://www.getdeb.net/app/Songbird"]http://www.getdeb.net/app/Songbird
 [/URL]

---

### Post by schwim on 2009-06-05
I tried using the .sh script from [this page](https://help.ubuntu.com/community/Songbird) of the Ubuntu community help site, which failed.

The .deb installed fine, however and I'm happily tapping my toes to some tunes :D

thanks,
json

---

