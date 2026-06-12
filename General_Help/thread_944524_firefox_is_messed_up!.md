---
title: "firefox is messed up!"
date: 2008-10-11
forum: General Help
---

### Post by douggiephresh on 2008-10-11
The update manager updated firefox, and now its all screwed up! For starters, it doesnt allow me to use the "back" button, it opens up to the "thank you for installing firefox" page every time i open it, i cant download anything and it runs through some sort of check when i try to open firefox. What is going on!?

---

### Post by aysiu on 2008-10-11
I don't know what's going on, but let's see if it's related to your profile.

**Step 1**
Close Firefox

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
firefox -profile-manager
```

**Step 3**
Create a new temporary profile and use it

**Step 4**
See if there's a difference and let us know

---

### Post by pd71sat on 2008-10-11
> **aysiu said:**
> I don't know what's going on, but let's see if it's related to your profile.

**Step 1**
Close Firefox

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
firefox -profile-manager
```

**Step 3**
Create a new temporary profile and use it

**Step 4**
See if there's a difference and let us know

I tried this to see if creating a new profile would change why Firefox does not 
activate the "Check for Updates" menu item under "Help", and it did nothing other 
just bring up the usual firefox browser.

How could this be? I downloaded firefox 3.03 and manually installed. 
Thanks for any insights on this.

---

### Post by pd71sat on 2008-10-11
I just checked another thread and the command is:-
> firefox -P
Ran the command and deleted the "default" profile and created a brand new one.
Same results, no activation of the "Check for Updates" menu item under "Help".

Can anyone tell how to get firefox to automatically check for updates and then allow
me to install on demand?

---

### Post by pd71sat on 2008-10-11
> **pd71sat said:**
> I tried this to see if creating a new profile would change why Firefox does not 
activate the "Check for Updates" menu item under "Help", and it did nothing other 
just bring up the usual firefox browser.

How could this be? I downloaded firefox 3.03 and manually installed. 
Thanks for any insights on this.

Ok started firefox with sudo:->  sudo firefox and the menu was active. I clicked and it went and checked for updates and it said 
that there was none. Firefox 3.03 is up to date. Now I know how to set firefox 
checking for updates - at least on demand, but not automatically.

---

### Post by aysiu on 2008-10-11
Please don't ever run *sudo firefox*

If you are using Firefox downloaded from the Mozilla website, you can update it with the command ```
gksudo firefox
``` and if you're using Firefox from the Ubuntu repositories, you should update with Ubuntu's Update Manager.

Running *sudo firefox* is a great way to screw up permissions on your Firefox preferences.

---

