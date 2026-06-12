---
title: "Help with Firefox please"
date: 2008-11-05
forum: General Help
---

### Post by DB2602 on 2008-11-05
Hey, I was having trouble with the dodgey new hotmail which changed itself automatically.  I thought downloading the new firefox (as recommended) would help.  I downloaded it and then checked on here on how to install etc - via terminal etc.  Now when I try to open firefox I get: Failed to execute child process "firefox" (No such file or directory)

Could somebody please help me to fix this.

The worst part is that the Hotmail problem seemed to fix itself.

Not sure how I even got onto the internet this time?

Be gentle, I'm a bit of an Ubuntu dummy but giving it a go.

Cheers,

DB

---

### Post by Yashiro on 2008-11-05
Because we have no idea what you have done to your system...

I'd open synaptic package manager and re-install. 

firefox (firefox-3.0)
firefox-gnome-support (firefox-3.0gnome-support)

---

### Post by DB2602 on 2008-11-05
Thanks Yashiro - did that but still nothing.

DB

---

### Post by DB2602 on 2008-11-05
Anyone?

I deleted it and reinstalled it and it still says: Failed to execute child process "firefox" (No such file or directory)

Tried typing firefox into terminal - it tells you to type sudo &^%$ etc.

I do that and its says Firefox is already installed and is the latest version.

Any ideas?

DB

---

### Post by nickstephens on 2008-11-05
Had exactely the same hotmail-derived problem. Although tempted to write caring message to hotmail explaing why I think they should not force developments on clients in a windows fashion, in instead spent a day or so fixing the problem on my machines. 

On the hardy machine it is simply a case of reinstalling, covered in another thread which I will try and find again now. 

On the Gutsy 7.10 machine after getting gran paradiso first (didn't think that much of that so i hope it still has a way to go) I tried numerous methods. As pointed out on the ubuntzillla (or however it is spelt) page there is a problem with ff3 incorperating ff2. You need to purge or similar ff2. After backing up the mozilla files I found one of the easier ways was to uninstall completely ff3 (which I could not get to work) and the previous ff2. I then reinstalled ff3 only! I then did a system restart. There are some parts missing from this install, including some of the graphics for gnome, so i reinstalled the firefox-gnome-support (which insists on installing previous ff components). After a system restart I get ff3 working all well and good. 

There is a catch that I have lost the pretty shortcut on the toolbar to the help files for some reason during the ff2 uninstall (which in my case were all in french and considering I can't speak french no use to me personally). I have not found any other problems though, and I do have ff3 which does work with hotmail. Somebody with more knowledge than me needs to check which processes I lost during uninstall and reinstalling the packages but all seems fine so far. 

Hope this helps
Nick

---

### Post by DB2602 on 2008-11-05
Thanks Nick but same story.

Might have to stick with thie epiphany as a browser - seems to go ok.

Cheers,

DB

---

### Post by Yashiro on 2008-11-05
Sorry to hear that. Following some of the "this is how you install Firefox" guides can often leave people with broken machines.

Seems like the only fix is to try and undo some of the damage if you can, and find a working guide that doesn't involve '500 steps to hose your machine'.

Additionally you don't need a new version of Firefox to use Hotmail. 
- Open about:config in the address bar.
- Search for useragent
- Remove the word Ubuntu from any of those strings, or replace it with Firefox. It's usually only in  general.useragent.vendor I think.
- Close the browser.

Open hotmail and just ignore the warning screens that pop up and continue on.

---

### Post by Yashiro on 2008-11-05
Two alternative Firefox based browsers.

[http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt](http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt)

[http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by sdowney717 on 2008-11-05
you can also run epiphany gnome browser and it works well.

---

### Post by Yashiro on 2008-11-06
Just a thought. The Firefox install in Ubuntu relies the Xulrunner framework.

Try re-installing all Xulrunner (1.9, 1.9gnome support) packages from the Hardy main repository.

---

### Post by DB2602 on 2008-11-06
Hey thanks guys, Have been using Epiphany and it's been goin ok.

Hotmail is still busted though.

Might try the xulrunner option mentioned earlier.

Cheers,

DB

---

