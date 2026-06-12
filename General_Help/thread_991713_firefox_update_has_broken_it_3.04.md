---
title: "firefox update has broken it 3.04"
date: 2008-11-24
forum: General Help
---

### Post by dredwerker on 2008-11-24
Hi all,

Firefox 3.04(or update to) is driving me insane.

[LIST=1]
[*]I cant reload a page
[*]I can't press back - so I only can ever have one page
[*]The home page only ever goes to mozilla
[/LIST]
These things make it completely broken I am having to use epiphany at the moment.

I tried 3.1 beta 1(from tombuntu) and the home page bug is fixed but this update has made it secure (I guess) but unusable.

I dont have any add-ons anymore as i have uninstalled them all.
The only things that are installed are from the repositories. 

Please help coz I have a freezing intrepid and a broken firefox its making my windows laptop look so stable its unreal.

TIA
Dred

---

### Post by blazemore on 2008-11-24
Go to Synaptic or whatever it is you Kde people use. Find every package with Firefox in its name, and Completely Remove it (not just remove, you need to purge all settings as well).

Then do
```
sudo apt-get install firefox
```

Unfortunately, you'll have to reinstall all your extensions, re-remember all your passwrds, basically, it'll be like it was the first time you ran it (because it is).

---

### Post by dredwerker on 2008-11-24
> **blazemore said:**
> Go to Synaptic or whatever it is you Kde people use. Find every package with Firefox in its name, and Completely Remove it (not just remove, you need to purge all settings as well).

Then do
```
sudo apt-get install firefox
```

Unfortunately, you'll have to reinstall all your extensions, re-remember all your passwrds, basically, it'll be like it was the first time you ran it (because it is).

Thanks for the quick reply :)

I have taken it completely out in Adept (kde's synaptic). I have also done an apt-get remove... and reinstall a couple of times.

Where are the settings held that i need to get rid of? If I do a locate firefox there are loads of places it holds stuff.

---

### Post by blazemore on 2008-11-24
if you do locate firefox, it's mainly icons and stuff.
The settings directory is ~/.firefox

```
rm -rfv /home/yourname/.firefox
```

But that's not the point.
Try
```
aptitude search firefox
```
Look for anything with an i next to it, (which means installed0.
Then do
```
apt-get purge package1 package2... etc
```

---

### Post by dredwerker on 2008-11-24
> **blazemore said:**
> if you do locate firefox, it's mainly icons and stuff.
The settings directory is ~/.firefox

```
rm -rfv /home/yourname/.firefox
```

But that's not the point.
Try
```
aptitude search firefox
```
Look for anything with an i next to it, (which means installed0.
Then do
```
apt-get purge package1 package2... etc
```

I have tried this a couple of times now just to make sure and it still knows that I have Adblocker installed so it cant be gettting rid of old icons. There must be other directories I need to get rid of.

---

### Post by blazemore on 2008-11-24
Are you sure you removed Firefox?
Use Synaptic, I can help you with that
```
sudo apt-get install synaptic -y && sudo synaptic
```

Then use Synaptic to "Completely remove" it, because I don't know if Inept does it properly.

---

### Post by blazemore on 2008-11-24
Or, might this work? I'm not on linux atm so I don't know the proper syntax, but:
```
sudo rm -rfv ('locate firefox')
```
Might pass the results of locate firefox to the rm -rf command (v just means "list every file you're deleting")

---

### Post by detroit/zero on 2008-11-24
The folder is named [COLOR=Blue]~/.mozilla[/COLOR] Inside this folder is another one named [COLOR=Blue]firefox[/COLOR]. From there, your profile folder is what you'll want to delete; it should be named [COLOR=Blue]xxxxxxx.default[/COLOR], where xxxxxxx is some gibberish.

---

