---
title: "Transparent Cube Caps in Ubuntu 8.10 Intrepid Ibex"
date: 2008-11-28
forum: General Help
---

### Post by drelyn86 on 2008-11-28
If you're like me, you like having your cube caps transparent (I know, it's not an important issue in life, but stay with me). With the new version of Compiz that's included in Ubuntu 8.10, things are quite different. Sure, they've added some new features to the cube, but how do we make the caps transparent? It used to be much easier. 
--------------

The fix I have here is pretty simple...

Open GIMP. 

File > New. 

Size doesn't matter (in this situation), but I made it 640 x 480 anyway. Click the "Fill With:" dropdown menu and choose "Transparency". Click OK. 

[IMG]http://i486.photobucket.com/albums/rr229/drelyn86/Screenshot-CreateaNewImage.png[/IMG]

Once that's done, just go to File > Save. Just remember where you save it, of course... and save it in PNG format. I named mine "transparent.png" and saved it in my "Pictures" folder. 

Open compizconfig-settings-manager, and go into the "Cube Reflection and Deformation" settings. 

Stay in the "Cube Caps" tab, and take a look at the "Behavior" settings. Just make sure the first two are checked. 

[IMG]http://i486.photobucket.com/albums/rr229/drelyn86/Screenshot-CompizConfigSettingsMana.png[/IMG]

Now the appearance settings... make sure the opacity for the top and bottom colors are 0. 

[IMG]http://i486.photobucket.com/albums/rr229/drelyn86/Screenshot-PickaColor.png[/IMG]

Delete any pictures that are in the top and bottom image files, and put in the absolute pathname to the image you created in GIMP. 

[IMG]http://i486.photobucket.com/albums/rr229/drelyn86/Screenshot-CompizConfigSettingsM-1.png[/IMG]

That's it! Now your life is truly better.

[IMG]http://i486.photobucket.com/albums/rr229/drelyn86/Screenshot.png[/IMG]

---

### Post by amiller2571 on 2008-11-28
That's pretty nice I would have never though of doing it that way.

---

### Post by eternalnewbee on 2008-11-28
I find this post very useful indeed. Thank you):P

---

### Post by mue on 2009-06-23
Oh yeah :)

---

### Post by balampixan on 2009-07-01
Hi, thanks for the advise, I did it and works nice!!!!
However, I cannot make the cube's walls transparents and I cannot make the water efect with the waves as you have shown in you pictures, can you help me?

---

