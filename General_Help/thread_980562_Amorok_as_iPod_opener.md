---
title: "Amorok as iPod opener"
date: 2008-11-12
forum: General Help
---

### Post by lsutiger on 2008-11-12
I haven't been able to get a full answer to this question. It should not involve any scripts.

I had to reinstall 8.04 not to long ago. I had Amarok to open by default when I plugged in my iPod before. Now Rhythmbox opens. I removed Rhythmbox. How do I get Amarok to open when I plug in my iPod?

---

### Post by prshah on 2008-11-13
> **lsutiger said:**
> I had Amarok to open by default when I plugged in my iPod before. Now Rhythmbox opens. I removed Rhythmbox. How do I get Amarok to open when I plug in my iPod?

Are you running Gnome or KDE? In the case of Gnome, open System-Preferences-File Management-Media-Music Player and select the software you would like to use with your music player.

If you can't find "File Management", press Alt+F2 and give the command
```

nautilus-file-management-properties
```

Open the tab "Media", and under "Music Player" change from "Open RhythymBox music player" to "Ask what to do" (or other suitable option).

Don't know what to do in the case of KDE, I'm sorry.

---

### Post by swisscow on 2008-11-13
I wish to do the same as the OP but when I follow the above instructions , under music player I have "no applications found" and the box is greyed out. any suggestions?

---

### Post by mc4man on 2008-11-13
> I haven't been able to get a full answer to this question. It should not involve any scripts.

that is quite easy to do but in 8.04 when Amarok is set to auto run and connect upon plugging in the ipod I don't like or think it connects properly when using the default launch command. (amarok %U
The use of a simple script as the Exec= for Amarok and creating a new amarok-ipod.desktop does it properly.

Without it amarok will load all of your tracks into a single playlist

See here for my preferred method

[http://ubuntuforums.org/showthread.php?p=5562637#post5562637](http://ubuntuforums.org/showthread.php?p=5562637#post5562637)

I will edit in the method of adding amarok to the music player drop down *without using a script* in a bit here though I don't  use it.


to simply add amarok as a default music player choice

to not be redundant to preferred method (and save some typing) first go to ...preferences -> media -> music player and choose 'do nothing'. Close out.  Then re open ...preferences -> media -> music player and set back to 'rhythmbox'.

Doing this assures you have the proper folder (.local/share/applications), a mimeapps.list file inside, and the proper line to edit (x-content/audio-player=rhythmbox.desktop;

run
```

gedit ~/.local/share/applications/mimeapps.list
```

Add this **to the end** of x-content/audio-player= line (no space between existing entry(s)

```
kde-amarok.desktop;
```

go back to preferences and change default to amarok.

Amarok will open and connect (must have been configured for ipod previously) and load all your tracks and start playing'

I quess though you could just clear the playlist though as I mentioned i prefer other method.

---

### Post by lsutiger on 2008-11-15
Thanx a bunch mc4man!!!

---

