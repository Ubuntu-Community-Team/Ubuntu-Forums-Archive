---
title: "synaptics touchpad pasting problem in firefox"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by closetosomethingreal on 2007-11-21
i have the strangest problem in ubuntu 7.10. my synaptics touchpad works perfectly, but when i tap the right corner (only at a very specific spot) in firefox, whatever text is copied to the clipboard is pasted into the address box and the link begins to load. ive had this problem with multiple versions of firefox, so i think its a synaptics issue. who in their right mind would want this as a feature! for example, if i have the word "monkey" copied to the clipboard, if i accedentally tap that part of the touchpad, my browser goes to monkey.com. :confused:

---

### Post by gfixler on 2007-11-22
What's happening there is the default behavior when you have text selected, and then middle-click (with a mouse) on the icon in the address bar, or simply middle-click on an inactive area of a web page, like in the background, or even just anywhere in a new, blank window, or tab.

Try this:

- open a new tab, and in it, go to the address:

about:config

(no http, www, or anything else) - and hit enter. That brings up all your current config settings. In the Filter: box, type:

middle

This chops the list down to just things with middle in the name. Look for the option called:

middlemouse.ContentLoadURL

Double-click it to toggle it to false. See if that fixes the problem. If not, you can try toggling false these other settings in about:config:

browser.tabs.opentabfor.middleclick
middlemouse.paste

Good luck!

---

### Post by closetosomethingreal on 2007-11-24
worked like a charm! how you guys know the answers to really strange problems like that ill never know.

---

