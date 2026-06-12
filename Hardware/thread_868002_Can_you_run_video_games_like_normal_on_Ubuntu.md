---
title: "Can you run video games like normal on Ubuntu?"
date: 2008-07-23
forum: Hardware
---

### Post by PsychedelicWonders on 2008-07-23
Do games install and play like they do in windows in Ubuntu?

---

### Post by tuxxy on 2008-07-23
Yes, aslong as they are compatible and your video drivers are working correctly.

---

### Post by pmlxuser on 2008-07-23
> **tuxxy said:**
> Yes, aslong as they are compatible and your video drivers are working correctly.

and of course if you are talking about windows based games you do it through WINE. but if you are talking about linux games then as above ;)

---

### Post by Daelyn on 2008-07-23
> **PsychedelicWonders said:**
> Do games install and play like they do in windows in Ubuntu?

NO. Most games are made for Windows only. 

Sometimes you can use them with a "translation layer" like the linux program called "wine", but, if it works or not you will have to check in their database on [www.winehq.org](www.winehq.org)

There are others like "cedega" but I do not have any personal experience with it.

Games made for linux, or having a linux installer (which only a very select few have), will mostly install and run just fine like any normal windows game would. 

All problems or queries regarding windows games in linux should be taken on the [www.winehq.org](www.winehq.org) homepage or the other translation layer homepages.

---

### Post by tuxxy on 2008-07-23
Yes sorry, I did mean compatible as in will WINE run the game which is usually the case for windows games.

---

### Post by PsychedelicWonders on 2008-07-23
What exactly is a "translation layer"?

And what is so different in the code to write the game for windows that it wont work with Linux?

The one game I am most concerned about is Warcraft III - is this going to be an easy one to play on Ubuntu with minimal tweaking?

Will I need to run this in wine?

Doesnt Wine give alot of error messages and problems?

---

### Post by tuxxy on 2008-07-23
[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

According to the DB yes it will run but without cut-scenes

---

### Post by justin whitaker on 2008-07-23
> **PsychedelicWonders said:**
> What exactly is a "translation layer"?

Wine and it's siblings translates Microsoft specific calls and translates them into something that Linux can understand. It's not as simple as it sounds. For example, audio calls made by the game to DirectX would have to be translated into something ALSA or Pulse Audio can handle.

> And what is so different in the code to write the game for windows that it wont work with Linux?

Proprietary code, and calls to the underlying OS, are the two biggest reasons why games can't "just work" in Linux. 

> Doesnt Wine give alot of error messages and problems?

No. Not anymore.

---

### Post by PsychedelicWonders on 2008-07-23
> **tuxxy said:**
> [http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

According to the DB yes it will run but without cut-scenes

What are "cut-scenes"?

and what is "DB"?

---

### Post by ilrudie on 2008-07-23
> **PsychedelicWonders said:**
> What are "cut-scenes"?

and what is "DB"?

Cut-scenes are the videos that play in between levels or when you do something in game (kill a hero, or a boss, etc...).

DB = database.  Its a bunch of information about programs and how well they work in wine.

---

