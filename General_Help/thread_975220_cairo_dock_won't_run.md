---
title: "cairo dock won't run"
date: 2008-11-08
forum: General Help
---

### Post by razy60 on 2008-11-08
Hi, got a minor problem with Cairo dock. I had it running fine for a while, but it kept opening over the system tray so i decided to move it the side of the desktop. when I did it became very unstable, wouldn't react to the mouse correctly sometimes stayed visible plus various other problems so i decided to uninstall it then reinstall it, did that now all that i get is the icon in system tools which when clicked does nothing.
I've tried to load  it various ways using package manager and terminal but still nothing, tried the uninstall in terminal just tells me that it isn't installed.
i have compiz working fine got mac4lin working fine just this one final thing to fix then I'm happy(until the next bit of decoration).
I'm using 8.04
any help much appreciated
Cheers
Raz

---

### Post by eternalnewbee on 2008-11-08
Press ALT-F2 and enter ```
cairo-dock
```

---

### Post by jtdgrz on 2008-11-08
If you installed it using the package manager, open up Synaptic and make sure it is actually installed.  If it is. mark it for complete removal and then reinstall.

---

### Post by razy60 on 2008-11-08
cheers for the answers.
> Press ALT-F2 and enter 
cant do that at this time as pc is down, but when i did it before it reported that it isn't installed.

> If you installed it using the package manager, open up Synaptic and make sure it is actually installed. If it is. mark it for complete removal and then reinstall. 
done that a couple of times it seems to remove it, but when i go back to check and to try and reinstall it is there but unchecked.

cheers 
Raz

---

### Post by razy60 on 2008-11-09
used alt-f2; came up;
 could not open location 'file:///home/razy/cairo-dock'
the location or the file could not be found.

this i'm hopping indicates that the files are not loaded(this is because i have removed them from my pc)

just reloaded cairo dock still no joy, alt-f2 indicates that there are no themes loaded.

---

### Post by eternalnewbee on 2008-11-09
I'm not sure, but you could try: ```
sudo apt-get install cairo-dock
```
And then, install succeeded, press ALT-F2 and enter
```
cairo-dock
```

---

### Post by razy60 on 2008-11-09
finally had it with trying to install cairo dock.

 pc was playing up so reinstalled 8.04 hardy, means having to reload compiz, mac4lin, and cairo dock, but hay thats what pc's are for.
 
 Also trying to load hardy on my laptop at the same time using unetbootin then going to load up all the visual goodies.

 Whats the betting i turn my laptop into a pile of molten plastic.:lolflag:

---

### Post by BunnyGirlDoom on 2008-11-19
> **eternalnewbee said:**
> I'm not sure, but you could try: ```
sudo apt-get install cairo-dock
```
And then, install succeeded, press ALT-F2 and enter
```
cairo-dock
```

This worked for me - Thanks!

---

### Post by eternalnewbee on 2008-11-19
You're welcome.

---

### Post by JuL.LeVi on 2008-11-19
Hi RAzy60,

All you have to do is :

- Go to "HOME" , View >> show hidden files
- Open ".config" folder , then Delete "Cairo Dock' folder
- After that, Open your Terminal , and type this command ( optional ) :
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

- Now, you can reinstall it by following the method in its homepage , or through synaptic or Terminal ( It's up to you )

Hope this help you,

JuL

---

