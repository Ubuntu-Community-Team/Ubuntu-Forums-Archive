---
title: "Tom Tom Home under Wine"
date: 2009-05-05
forum: Hardware
---

### Post by AlmaTlust on 2009-05-05
I tried to use Tom Tom HOME under wine. It installs o.k. and works well, but cannot connect to my Tom Tom ONE 3rd edition. I did look for a solution. My guess so far: TomTom HOME looks for a specific drive name to connect to. As names are handled diferrently under linux, it can't find the gps device. If there would be a way to assign the right name to the gps device, the Home application might actually find and connnect to it... Any hints, guesses, how-to's, procedures on how to proceed?

---

### Post by kay-man on 2009-05-05
I don't have a tom-tom myself, but if it's true that t looks for a specific drive you should be able to set this using the Wine coniguration panel.

I'm not at my linux box rigt now, but i believe it's called winecfg.

Anyway, there is a tab there that allows you to set drive mappings.

More fundamentally, you're right that windows and linux handle devices differently, but on Windows there's no way to predict the drive name that gets assigned to the device. You might have all kinds of card readers, cameras and what not connected which would influence the letter that gets assigned. It must be more sophisticated than that.

---

### Post by AlmaTlust on 2009-05-05
> **paulklos said:**
> 
More fundamentally, you're right that windows and linux handle devices differently, but on Windows there's no way to predict the drive name that gets assigned to the device. You might have all kinds of card readers, cameras and what not connected which would influence the letter that gets assigned. It must be more sophisticated than that.
When connecting the GPS under windows, it gets its drive letter (which as you said is assigned depending on a number of things), but it also has its own name (the one you would assign to a drive on windows with the "rename" option). I think it's this specific name that HOME is looking for, but under linux this name does not show up - at least not for wine.

---

### Post by kay-man on 2009-05-05
I checked the wine app DB, where results with the tom tom one software seem to be mixed.

Maybe this entry is helpful to you: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5367&iTestingId=13398]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5367&iTestingId=13398")

Since I don't actually have the device this is pretty much the end for me.

Good luck!

---

### Post by asnd16 on 2011-04-30
Booo still in Ubuntu 11.04 no support . . still no update in Wine

---

