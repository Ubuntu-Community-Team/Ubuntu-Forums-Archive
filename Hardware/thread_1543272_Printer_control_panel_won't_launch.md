---
title: "Printer control panel won't launch"
date: 2010-07-31
forum: Hardware
---

### Post by scoopjones on 2010-07-31
I'm having a problem getting the printer control panel to launch. It will start up briefly, then disappear. I went to the Terminal and executed "gnome-control-center", and this was the error message that resulted: 

gnome-control-center: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/librsvg-2.so.2)
 gnome-control-center: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/librsvg-2.so.2) 
 gnome-control-center: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/librsvg-2.so.2) 
 gnome-control-center: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/librsvg-2.so.2) 
 gnome-control-center: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libgsf-1.so.114) 
 gnome-control-center: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libgsf-1.so.114)
 gnome-control-center: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libcroco-0.6.so.3) 

Can anyone translate this for me?  Thanks.  Evan

---

### Post by lidex on 2010-07-31
On my system libxml2.so.2 is located in /usr/lib/ and it's just a link to the current version. A work-around might be to create a link in /usr/local/lib/, but I gotta wonder how it got into this state. Is this lucid? Try re-installing gnome-control-center (purge it first).
```
sudo apt-get purge gnome-control-center
```
```
sudo apt-get install gnome-control-center
```

---

### Post by scoopjones on 2010-08-04
I tried that and it didn't help unfortunately. The solution that did work was to download libxml2 and simply reinstall it. I didn't uninstall the previous version because it would have uninstalled every other program that depended on it (that's just about EVERY program). It's now functioning. Thanks for the suggestion.

---

