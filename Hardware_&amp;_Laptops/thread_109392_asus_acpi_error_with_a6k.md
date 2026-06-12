---
title: "asus_acpi error with a6k"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by farfargoth on 2005-12-28
I have a problem that is more irritating than anything else. I have a Asus a6book with ubuntu 5.10 installed and whenever I use kde it will pop up with a grey box once a minute or something like that. The box says "No primary screen" or something like that and disappears within a second. 
When I check out dmesg it's flooded with messages saying something like
```
[somenumber.someothernumber]Asus ACPI: Error reading display status
```
this led me to belieive that there is something wrong in the asus_acpi module, and wouldn't you know, when I did 
```
sudo modprobe -r asus_acpi
```
the annoying box disappeared and the dmesg-messages numbers stopped increasing. Does anyone have a permament solution for this that will still let me use acpi?

---

### Post by dedefus on 2006-01-02
i have the same problem with laptop ausu a3l. would be nice to know how to avoid this problem. what more a i have another problem, that is like every 5minutes there is a box on the screen saying "Display changed: LCD status On/Off". i would be thankful if someone knows how to solve one or both problems. ty

---

### Post by luxir on 2006-01-02
> I have a problem that is more irritating than anything else. I have a Asus a6book with ubuntu 5.10 installed and whenever I use kde it will pop up with a grey box once a minute or something like that. The box says "No primary screen" or something like that and disappears within a second. 

I had a similar problem with my Asus A3E. I fixed it by following the instructions in [http://de.wikibooks.org/wiki/Asus_W3N-Kompendium:_Kubuntu](http://de.wikibooks.org/wiki/Asus_W3N-Kompendium:_Kubuntu)  (in german):

```
sudo nano /usr/share/services/kded/kmilod.desktop
```

change to:

```
X-KDE-Kded-autoload=false
X-KDE-Kded-load-on-demand=false
```

This fixed it permanently for me.

---

### Post by farfargoth on 2006-01-04
thanks for the tip... I'm going to test it in a couple of hours when i get back to my laptop... Up until now I had placed the line 
```
modprobe -r asus_acpi
```
in my kdm startupscript, wich I didn't really like...

---

