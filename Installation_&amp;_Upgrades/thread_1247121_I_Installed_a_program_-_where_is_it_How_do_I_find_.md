---
title: "I Installed a program - where is it? How do I find it?"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by martydavis on 2009-08-22
I installed "Bible-kjv-text" via synaptic package manager and it said it installed successfully.  It is not listed anywhere in my applications drop down list. A search of my filesystem shows "bible-kjv-text" and "bible-kjv" directories are in /usr/share/doc.  Seems to be just a bunch of gz files.  How do I run the program or know it is installed like synaptic says it is?

Thanks,

---

### Post by stlsaint on 2009-08-22
use the whereis cmd!

---

### Post by drs305 on 2009-08-22
You can use the whereis command as suggested above. You can also type: **which bi** and then tab twice, which will bring up all the installed apps which start with **bi**. The, once you see your package, type it again using the full name: **which <appname>** and you will get the run command.

You can also look through synapatic to find the installed name. When you find the app, highlight it, select Properties from the top menu, then Installed Files to see where the actual files are stored.

You can make a shortcut/launcher once you have the run command from the "which" results discussed first or the appname found in /usr/bin if there is one there (the run command would be **/usr/bin/<appname>**, for example: /usr/bin/gimp

---

### Post by 0faber on 2009-08-22
The problem is it's a compressed text file, not a program. You need the program bible-kjv to search and display text (along with bible-kjv-text -- the actual text itself, which you just downloaded). Just go back to synaptic and get it. You'll be fine.

---

### Post by martydavis on 2009-08-22
I found bible in the /usr/bin directory.  Ran "./bible" and got the first verse.  Right arrow brings on the next verse.  I installed "bible-kjv" with synaptic when I got the "bible-kjv-text" package and it installed successfully according to synaptic.  Anybody know where the front end program to this is?

I also installed "verse", but it isn't giving me a daily verse like it is supposed to either.  Anybody know where it is also?

Thanks

---

### Post by 0faber on 2009-08-22
Where's the front end? Don't know. I'm baffled now. 

If you go back to Synaptic and search for bible-kjv, does it list it as installed?

---

### Post by martydavis on 2009-08-22
yes, it shows it installed.  Earlier this morning I reinstalled it and it was successful the second time too.  If it doesn't put it in the applications drop down where else would I find it to run it?

---

### Post by 0faber on 2009-08-22
I don't know. I'll try installing it myself and see what happens.

---

### Post by 0faber on 2009-08-22
OK. Looks like this is command-line only program. You can get more information about the program by typing [FONT="Courier New"]man bible[/FONT]<enter> in the terminal, and run it by typing [FONT="Courier New"]/usr/bin/bible[/FONT]<enter>. I think you did that already. You can improve on the one-verse-at-a-time out by typing [FONT="Courier New"]/usr/bin/bible -f [/FONT]instead.

It looks like gnomesword, a Bible study program designed for the GNOME interface, also in the repositories, might be a better bet. Has the text of the Bible in several translations, lets you take notes, and evidently, a graphical interface.

Sorry this took so long.

---

### Post by martydavis on 2009-08-22
The description of the program made it sound like a KJV bible program with concordance, but the man pages show it as a text program as you found.

Thanks for your assistance.  I'll have a look at gnomesword.

Thanks again.

---

