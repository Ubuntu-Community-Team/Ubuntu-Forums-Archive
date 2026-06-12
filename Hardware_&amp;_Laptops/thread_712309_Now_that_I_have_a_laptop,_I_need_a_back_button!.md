---
title: "Now that I have a laptop, I need a back button!"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by adamprawitz on 2008-03-01
I have an eee pc.  Its running Gutsy.  It has the standard two button mouse, pressing both emulates the middle click.  But what it is missing is a back button.  I am all too used to the back button on my desktop mouse.

Any ideas on how to set one of the keyboard keys to act as a back button?

---

### Post by Anthony M on 2008-03-01
Do you mean a back button as in web browsing...? if so, thats easy

---

### Post by adamprawitz on 2008-03-02
> Anthony M  	
Re: Now that I have a laptop, I need a back button!
Do you mean a back button as in web browsing...? if so, thats easy

That is exactly what I mean!  Please give me some direction!  :]

---

### Post by Anthony M on 2008-03-03
Not sure about other browsers, but in Firefox the backspace key will act as a 'back' button.

Hope that helps!

---

### Post by coggins on 2008-03-03
> **Anthony M said:**
> Not sure about other browsers, but in Firefox the backspace key will act as a 'back' button.

Hope that helps!

That is true in windows, but seemingly not in Ubuntu.  To set firefox to have the backspace key perform the back function, type about:config into the address bar.  Filter for browser.backspace_action and change the value to 0 (zero).

---

### Post by Anthony M on 2008-03-03
> **coggins said:**
> That is true in windows, but seemingly not in Ubuntu.  To set firefox to have the backspace key perform the back function, type about:config into the address bar.  Filter for browser.backspace_action and change the value to 0 (zero).


That's odd. Mine has always worked in Ubuntu, without changing any settings.

---

### Post by adamprawitz on 2008-03-03
Thank you for your help Anthony, but it still does not work.  I tried it on my desktop, and it works perfectly.  But the same setting on my laptop, and backspace does nothing.  Any other ideas?

---

### Post by coggins on 2008-03-03
Unfortunately, I haven't installed Gutsy on my eeepc, so I can't check this out exactly.
I can only imagine that the particular build of firefox you are using does not have this properly implemented.  

Other shortcuts for Back that may work:

Alt + Left Arrow  (on gutsy you might have to use the left alt, but on the eeepc it's still doable with one hand.

Shift + Scroll Down (tricky on the eeepc but maybe you can master it.)

---

### Post by coggins on 2008-03-03
You could try the [keyconfig]("http://extensionroom.mozdev.org/more-info/keyconfig") extension.  It's pretty old, but it seems to work.

---

### Post by adamprawitz on 2008-03-03
Thanks coggins!  I like the shift scroll, (I usually use a usb mouse).  Also, on my setup at least, I can use the right or the left alt with the directional keys.

Thanks again for making my browsing experience a little easier!

---

### Post by Jetjoint on 2008-03-10
Or you can just change the setting in Firefox.

In the address bar type 

```
about:config
```

Go to the "browser.backspace_action" line

Click on the line and enter a value of 0.

Your backspace button will now act as a backpage button.

---

