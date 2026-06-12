---
title: "Intel 945GM graphics problems"
date: 2009-02-26
forum: Hardware
---

### Post by Jakey_TheSnake on 2009-02-26
Running 8.10 on an Acer Aspire one netbook. 

Transparency and all desktop effects have gone - read below. 

So I hooked my laptop up to my 19" monitor at home using a VGA cable, then went into System > Preferences > Screen Resolution, enabled the monitor's display and turned off the laptop's. After disconnecting and changing back to my default screen res setting (i.e. laptop on, no external monitors) all of my transparency and desktop effects settings have gone (e.g. wobbly windows, desktop cube, transparent terminal and cairo dock). 

Apparently this means my laptop isn't actually using my graphics card, or something similar?

fglrxinfo outputs this:

```
jake@jake-laptop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

---

### Post by Jakey_TheSnake on 2009-02-26
bump.

---

### Post by Jakey_TheSnake on 2009-02-27
bump.

---

### Post by stim on 2009-02-27
1. Install compiz fusion icon if you don't have it already

```
sudo apt-get install fusion-icon
```

2. Set it to run at startup.
System->Preferences->Sessions-->add
In the 'command' field type "fusion-icon"

3. Log out and log back in, you should have a blue icon with a mouse pointer in your notification area .

4. Right click the icon, go to "select window manager" and choose "compiz".

5.Right click the icon again, choose "reload window manager".

6. See if the problem is fixed.

I have a 965 and its a little wonky sometimes with dual monitors.

---

### Post by Jakey_TheSnake on 2009-03-07
No joy unfortunately.

---

