---
title: "Spore?"
date: 2008-09-22
forum: General Help
---

### Post by claymater on 2008-09-22
Does anyone know how to get spore to work in ubuntu with 1GB of ram?

---

### Post by tuxxy on 2008-09-22
I think it runs to an extent under WINE although last I heard there were problems trying to run anything after the tribal stage, hopefully this has improved since, check the compatibility list at wineHQ

---

### Post by claymater on 2008-09-22
> **tuxxy said:**
> I think it runs to an extent under WINE although last I heard there were problems trying to run anything after the tribal stage, hopefully this has improved since, check the compatibility list at wineHQ

Ok thanks :)

---

### Post by mb_webguy on 2008-09-22
I'm not sure about the 1GB of RAM part, but have you tried installing the latest version of Wine from the [Wine HQ]("http://www.winehq.org/") website, and following the suggestions on the [Wine AppDB page for Spore]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652")?

---

### Post by claymater on 2008-09-22
> **mb_webguy said:**
> I'm not sure about the 1GB of RAM part, but have you tried installing the latest version of Wine from the [Wine HQ]("http://www.winehq.org/") website, and following the suggestions on the [Wine AppDB page for Spore]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652")?

Well I am downloading the .iso image now So I can see if it will work (and it is the reloaded version) and if I can get it to work then ill buy it.

---

### Post by mb_webguy on 2008-09-22
It has a gold rating on the Wine AppDB website, so assuming you're running the right version of Wine and possibly install a patch, it should run fairly well.

---

### Post by claymater on 2008-09-22
> **mb_webguy said:**
> It has a gold rating on the Wine AppDB website, so assuming you're running the right version of Wine and possibly install a patch, it should run fairly well.

Sweet! but with 1GB?

---

### Post by HangMan101 on 2008-09-22
Well i got it working on hardy.

[LIST]
[*]!save all open documents or any thing that should not get lost
[*]i installed wine form the ubuntu repository
[*]i added a source to the packet manager (see: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb))
[*]Open your packet manager and let it refresh
[*]Close it and start ubuntu update.
[/LIST]

now you should be able to start spore,
if your graphics freakout close spore if possible, or use crtl+alt+backspace

open wine config and enable virtual desktop(just to make you able to configure spore) 1024*786  should do. 
start it again. 
now if you are able to see spore's galaxy configure it to a usable resolution and !window mode!
close spore and disable virtual desktop in wine config

start spore and it should work, it did for me.

if it does not work, please open the terminal and goto the Sporebin folder
and type:
wine SporeApp.exe -safe

if it does not run. let us know the wine terminal output. and specially the "file not found" lines (fixme lines can mostly be ignored)

---

