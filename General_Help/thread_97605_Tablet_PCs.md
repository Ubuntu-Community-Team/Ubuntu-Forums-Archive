---
title: "Tablet PCs?"
date: 2005-12-01
forum: General Help
---

### Post by Dgurion on 2005-12-01
Well, My friend has a Tablet PC its a Toshiba something or other, but its not very new, maybe a year old... So I was wondering if linux is able to support the tablet functions of the laptop... Is there a notetaking application sorta like the windows OneNote? Can you move the mouse with the pen/stylus thingy?

---

### Post by basketcase on 2005-12-01
I've got a protege 3500 at home, I could try a live cd on it when I get home.

---

### Post by bb002 on 2005-12-01
Yeah Tablets are supported. I have a Gateway M275 running Ubuntu 5.04 Hoary with everything working. Breezy however hates my Gateway only the audio card works out of the box and I can't get anything else to work after days of meddling. Not even the onboard NIC worked and I've never seen linux fail to use a NIC properly. Though breezy runs perfectly on my desktop, just hates my laptop.


The Gateway M275 has a serial tablet screen and not a usb one like most of the howto's out there are for. So getting the tablet to work took quite a while since I didn't know what device my tablet was located on and I was a complete noob. I eventually found it on /dev/ttyS1 and getting it to work after that took minutes.

---

### Post by Dgurion on 2005-12-01
[QUOTE=basketcase]I've got a protege 3500 at home, I could try a live cd on it when I get home.[/QUOTE]

That would be really awesome, thanks.. Well, I think thats what Im going to do is try a live CD on his.. 

What kind of software would you guys recommend? Like a notetaking application?

---

### Post by bb002 on 2005-12-05
Well, to be completely honest. I use GIMP. Most of my notes are small and temporary so GIMP does just fine for me. I haven't really look into a true note taking application.

Doing a synaptics search by description for "tablet" yielded nothing useful. Probably why I ended up using GIMP in the first place.

Any application for Linux usually doesn't have binaries and you have to compile it yourself. So be prepared. Now you've gone and sparked my interest in a true note-taking app. I'll keep you posted.

---

### Post by 23meg on 2005-12-05
I'm using a Toshiba Tecra M4 convertible with Breezy, and was able to get all tablet functions including pressure sensitivity in GIMP working quite easily. I can assist anyone having issues with their tablets.

The notetaking application I'd recommend would be Gournal, which is very similar to Microsoft Journal. It works great.

---

### Post by chuvisco on 2005-12-17
I've been using Windoze Journal on my Toshiba Portege 3500 for about a year, and I think one of the biggest advantages of a tablet PC over pencil and paper is the ability to cut, paste, and move things around.  But I also want my work to look good.  I have Gournal, Jarnal, and Gsumi installed on my computer, but I am still using the GIMP because it supports pressure sensitivity and allows me to cut and paste.  Gournal is a good program, but it's not pressure sensitive and doesn't allow cut and paste.  Jarnal has some tools for moving things around, but it doesn't support pressure sensitivity.  Gsumi does support pressure sensitivity and even filters down from a higher resolution (so your writing doesn't look pixelated), so it looks great, but it only has black (pen) and white (eraser).  It also doesn't allow cut and paste and only one page (file) can be open at a time.  If the features of Gsumi and Gournal could be merged, that would become a really nice program.  That's just my take.

---

