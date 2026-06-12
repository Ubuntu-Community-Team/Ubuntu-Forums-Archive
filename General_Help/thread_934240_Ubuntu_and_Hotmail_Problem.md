---
title: "Ubuntu and Hotmail Problem"
date: 2008-09-30
forum: General Help
---

### Post by ankitn on 2008-09-30
It seems microsoft has upgraded hotmail and the new version it not completely working on my system (Firefox 3.0.3 and Ubuntu 8.0.4). Even though I can log in and browse, move and delete the files. But I can't send messeges because the text editing pane is disabled.

I tried to switch back to the classic layout setting by clicking the "choose perfect view" on the main page" then I clicked "Personalize your view now!" but this new page just says  "Unknown page". 

Any ideas?

---

### Post by gleble on 2008-09-30
What GUI are you using?

---

### Post by ankitn on 2008-09-30
Gnome

---

### Post by Bobthegoldfish on 2008-10-01
I was able to get the pane turned back on by going to about:config in Firefox and changing 

general.useragent.vendor

to a blank value. Restart Firefox and log in to Hotmail. The pane should allow you to edit with it.

---

### Post by ankitn on 2008-10-01
Thats works except when I restart the browser general.useragent.vendor is reset to "Ubuntu".

---

### Post by ankitn on 2008-10-05
Any ideas?

---

### Post by tonybaqain on 2008-10-05
i tried it at my Firefox 3.0.3 and it went successfully, try upgrading your firefox to this version, it was realeased in updates a few days ago. use your update manager.

after update try changing the value to null string, and test it.

have fun :)

---

### Post by ankitn on 2008-10-05
Already using 3.0.3 and it still doesn't work.:(. Any ideas why Ubuntu would keep changing the null string everytime I restart firefox?

---

### Post by PocketDog on 2008-10-05
Tried using the User Agent switcher plugin?

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by ankitn on 2008-10-12
> **PocketDog said:**
> Tried using the User Agent switcher plugin?

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)


No, I tried the addon it has no effect.

---

### Post by rugbeeprop on 2008-11-04
I tried general.useragent.vendor and it works.

---

### Post by amrlinuxroot on 2010-07-17
add this o try it out:

    * Configure your network settings to use the IP addresses 8.8.8.8 and 8.8.4.4 as your DNS servers or
    * Read our configuration instructions. google dns its will fix the prb

---

