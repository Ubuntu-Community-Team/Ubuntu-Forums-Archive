---
title: "Built In Speakers Vs. Headphones"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by JPMaximilian on 2006-08-25
Normally, if you plug in headphones, the built in speakers should be disabled.  However, on my acer travelmate 2440 running dapper, when I plug in the headphone jack, the built in speakers continue to work.  Is there a way to disable the built in speakers when the headphone jack is in use?  Thanks.

---

### Post by JPMaximilian on 2006-08-26
Bump

---

### Post by JPMaximilian on 2006-09-02
Bump

---

### Post by freyes on 2006-09-02
I saw this on a Dell laptop, this happens when the turn-off of the speakers is made by software (module, driver), so you must search some configuration in the module used by the sound card.

I'll try to find the configuration used that time to fix this.

good luck.

---

### Post by CELI-Nux on 2006-09-03
This is the default configuration if you are using Gnome (i.e.: Ubuntu).  Here's a walkthrough:

* Go to "Application - Accessories - Alacarte Menu Editor";
* Select "Sound & Video" down the left side list;
* Check "Volume Control" in the right side pane;
* Click the "Close" button (bottom-right).

Then:

* Go to "Application - Sound & Video - Volume Control" (newly added from previous step);
* Select "Edit - Preferences" from the top menu bar;
* In the list, check "Headphone jack Sense" and "Close";

Now:

* Click on the "Switches" Tab;
* Check the "Headphone jack Sense" radio button (newly added from previous step).

There you go - you should now have a fully functional headphone jack. Unfortunately, I haven't found a way to sync the "Master" volume control of my laptop speakers with the headphone volume.

Take care.

---

### Post by iLoVe.cF- on 2006-09-05
ehh.. not kinda right after my experience..

This is a problem with " HDA-intel" soundcard stuff.. dont know much about it..

Its realtek codec or something..

You have to update alsa driver you can download drivers from [www.realtek.com](www.realtek.com) or .tw dont remember.. 

You have to download drivers from realtek or something.. im having truble with the same problem .. and im probaly gonna be up all night trying to solve it ^^

Pm me if u got any info about it..

Btw i got an asus A3E just so you know we got the same problem and its most likely same fix ..

---

### Post by JPMaximilian on 2006-09-06
There is no option for headphone jack sense for me.  Thanks though.

---

### Post by JPMaximilian on 2006-09-07
Is there a way to just disable the laptop speakers.

---

### Post by StarQuake on 2006-09-07
> **CELI-Nux said:**
> Unfortunately, I haven't found a way to sync the "Master" volume control of my laptop speakers with the headphone volume.


Try clicking with your right mouse button on the speaker in your panel. Then choose preferences. Then you can select 2 tracks to bundle them. Click close.

Now you can adjust them both using your mousewheel while hovering over the speaker icon.

(I sometimes forget windows does not do that)

---

### Post by iLoVe.cF- on 2006-09-07
its not that he is pointing to..

Hes talking about that sound dont work out of the jackplug but our built in speakers make sound.. atleast for me..

I have tried several how to's but dont understand it good.. but...

If anyone have intel-hda sound ( i got Alc880 chipset)

Other alc8xx use same fix as far as i know..

On the fixes i have seen ppl have managed to work it out.. but im too new to understand their how to..

Any high linux users/ or users got it working.. plz post it !!!!

---

### Post by RafRaf on 2006-09-09
Great tip StarQuake!

Now there is only a little annoying thing: if I adjust the volume with the keyboard shortcut (I use alt-arrow up) then the headphone volume does not change..wierd.

---

### Post by CELI-Nux on 2006-09-09
> **StarQuake said:**
> Try clicking with your right mouse button on the speaker in your panel. Then choose preferences. Then you can select 2 tracks to bundle them. Click close.

Now I really feel stupid!!!  Where is the "speaker in your panel" or how do I put it there???  I'm blind here ](*,) 

Regards

---

### Post by RafRaf on 2006-09-10
Right click on your gnome pannel, select Add to pannel and choose the Volume control applet in the list.

---

### Post by CELI-Nux on 2006-09-12
> **RafRaf said:**
> Right click on your gnome pannel, select Add to pannel and choose the Volume control applet in the list.

Did just that but no "2 tracks" preferences option for my Intel 82801DB-ICH4 (with Alsa mixer) :-(  Unless anyone as an additional hint???

Regards

---

### Post by elodsson on 2006-11-20
Hi...uh... i don't even know if i'm knocking on the right door... (if not, please redirect me)
I have an Asus A3E laptop with ubuntu on it. It did recognize my Intel soundcard, the voice is functioning perfectly (almost... it's not as loud as in windoze), but my jackplug is not working properly. If i plug my headphone jack in (wich is perfectly functioning), the built in speakers do shut up, but there's not a single sound in the headphones. I have tried it with other speakers, several different headphones, but as conclusion i think something has to be set up somewhere in the software. Anyone any idea...???
Thanx, and sorry for my language-problems...

---

### Post by elodsson on 2006-11-21
Still needing an answer... please...

---

