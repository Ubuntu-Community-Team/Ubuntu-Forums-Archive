---
title: "[SOLVED] .kss files in regular ubuntu"
date: 2008-09-01
forum: General Help
---

### Post by Crushyerbones on 2008-09-01
Hi, I've recently fallen in love with kannasaver. Is there a way to use it as a regular screensaver without switching to kubuntu?

---

### Post by y-lee on 2008-09-01
hmm interesting. Looking around i [found]("http://ubuntuforums.org/archive/index.php/t-239543.html")

> Wanted this myself. The solution:

I'm assuming you've got xscreensaver running rather than the gnome screensaver. See this post:
[http://www.ubuntuforums.org/showthread.php?t=195557&highlight=xscreensaver+default](http://www.ubuntuforums.org/showthread.php?t=195557&highlight=xscreensaver+default)
Once that's done the rest of this should work fine:)

Make sure you have the language pack installed.
sudo apt-get install language-pack-gnome-ja

Install the screensaver packages.
sudo apt-get install kanjisaver
sudo apt-get install kannasaver

Go to your home directory.
cd

Open the xscreensaver config file.
gedit .xscreensaver

Add the following two lines under the "programs:" section.

- kanjisaver.kss --root \n\
- kannasaver.kss --root \n\

When you open up xscreensaver they should now appear in the list. Although the preview window in xscreensaver doesn't work it will work when you press the preview button.

You won't be able to edit the settings using xscreensaver. You'll have to do it through the command line:

kanjisaver.kss --setup
kannasaver.kss --setup

And a window will open where you can adjust the settings.

I haven't tried any of that but hopefully that will help :)

---

### Post by Crushyerbones on 2008-09-01
It all works. Somehow... I get an error message on kannasaver :p But it's just an error message that goes away after a while, nothing major :lolflag: I think the screensavers are gnome's weakness at this point. They've just been going downhill ever since I became a Linux geek :(

---

### Post by Zeppelin! on 2010-09-02
Actually, I'm having an issue with this setup. I followed the above instructions to the letter, and all went well. I could see it in the xscreensaver demo thing, and they would play, with their respective error messages.

Recently, I came back having left my computer to see it was running Kanjisaver - now, I'm not ready for Kanji, so I want to stick to Kannasaver. I open up Xscreensaver and scroll down to the Ks. Neither of them are there. I open ~/.xscreensaver - for some reason, they aren't in the program section, I readd them to lines, complete with -root and an appropriate selection of tab and space to line up \n\. Satisfied with my work, I save and close the .xscreensaver file and load up demo mode again. They're not there. I open .xscreensaver - they're still there, I try adding a second - to -root, still nothing.

I really have no idea what to do about this.

---

