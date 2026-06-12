---
title: "Desktop Effects Not Working in Ubuntu"
date: 2008-07-15
forum: General Help
---

### Post by Krispy Kreme on 2008-07-15
I have an Acer 5570Z laptop with Intel graphics and after I updated the Kernel my desktop effects stopped working. I get a "desktop effects could not be enabled" error. Here is the output of my Compiz file:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

I've looked around the net and haven't been able to fix it. Help?

Edit: Problem's been fixed, nevermind!

---

### Post by handsomeDave on 2008-07-17
run the compiz-check script and post what it says

```
wget http://blogage.de/files/4359/download -O compiz-check
chmod +x compiz-check
./compiz-check
```

---

### Post by Unwired on 2008-07-17
Same problem here, I have ATI Xpress 200M, according to compiz-check my system passed every test but if I tried to run the effects it says that my xorg-display is not enabled. But the problem here is that I can't enable it....

Any help will be gladly appreciated....I am an ubuntu user but I am a newbie to this customation...:)

---

### Post by stitchmysmile93 on 2008-07-17
Have you guys tried installing your graphics drivers with envy it works great on this end...

---

### Post by handsomeDave on 2008-07-17
what does
```
 glxinfo | grep vendor
```
give you?

---

