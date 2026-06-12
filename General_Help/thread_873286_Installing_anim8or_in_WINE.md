---
title: "Installing anim8or in WINE ?"
date: 2008-07-28
forum: General Help
---

### Post by zakiya on 2008-07-28
I have the Anim8or.exe on the desktop, but unsure how to install this in Wine. I found some up-to-date instructions but according to them I should have a Wine File Browser in my Applications->Accessories which I don't.
Gutsy btw,
Thanks for any help.

---

### Post by Taxman415a on 2008-07-28
I think the browser you are referring to is in Applications -> Wine -> Browse C:\ Drive, but it only browses what's already installed in Wine. But without knowing what instructions you read, it's hard to tell. The Wine menu will only exist once you have Wine installed.

The general way to install something in wine is to open a terminal and cd to the directory that the .exe file is in then type wine Anim8or.exe for example. If you're running Hardy you can also just double click on the .exe file if you already have Wine installed.

---

### Post by zakiya on 2008-07-30
Thanks for that, just upgraded to Hardy and double-clicking the .exe works as it should, however I'm not sure that it is working properly, I've only watched a demo, but Anim8or gui doesn't look like I was expecting, and I can't get it to do what it should.
Does anyone know whether it works properly in Wine on Hardy?

---

### Post by Taxman415a on 2008-07-30
Wine's application database is the place to look for how well supported an app is. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1537](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1537)  should be a working link for the Anim8or page. Basically it just doesn't run perfectly under wine. You could ask the developer to try to improve it's performance under wine or use an alternative native linux app such as blender or something else that fits the bill for you.

---

### Post by zakiya on 2008-07-31
Yes thanks, have realised there is a separate forum here on WINE topics too. Although the wine app database gives anim8or on hardy a bronze, doesn't seem to work at all for me...oh well will give blender a go, or may have to dual boot xp.

---

### Post by Taxman415a on 2008-07-31
If you really need it, you can run XP in Virtualbox or VMware, KVM, etc. Runs surprisingly well.

---

### Post by zakiya on 2008-07-31
Didn't realise you could do that, will read up on those aswell then, I wonder if that would use up alot more cpu power trying to run 3d modelling program like that? (and whethet my laptop would run noticeably slower - it's has pretty good specs but still...)
Thanks alot for your help Taxman415a :)

---

### Post by Taxman415a on 2008-07-31
Yeah, it will definitely take more resources and it won't be speedy, but it should work. Depends a bit on the graphics card needs of the program though I guess. And it definitely needs a decent amount of RAM. In the end you'll probably be happiest if you learn blender. It's got a reputation for being a bit hard to learn, but it's supposed to be improving. There seems to be a lot of good documentation for example: [http://wiki.blender.org/index.php/Main_Page](http://wiki.blender.org/index.php/Main_Page)
And you're very welcome

---

### Post by zakiya on 2008-07-31
Hmm yes I think I will just start learning Blender. I'm doing an opengl paper at university and we have to be able to load in 3d objects to our programs - they suggested anim8or (as it's supposed to be easier to learn I think) but as the focus is on the programming and not learning an animation program I'm sure they only expect us to produce basic stuff anyway.
Having said that I'd like to extend my learning beyond the scope of the paper as I'm finding the graphics programming really enjoyable, and I would like to stick with linux, so I guess learning Blender well would be a good investment of my time.
:)

---

