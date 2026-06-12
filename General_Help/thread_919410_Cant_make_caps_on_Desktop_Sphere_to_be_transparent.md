---
title: "Cant make caps on Desktop Sphere to be transparent?"
date: 2008-09-13
forum: General Help
---

### Post by PsychedelicWonders on 2008-09-13
Alright I need to figure out how to make these squares transparent in my desktop Sphere... anyone have any suggestions?

---

### Post by mike1234 on 2008-09-13
> **PsychedelicWonders said:**
> Alright I need to figure out how to make these squares transparent in my desktop Sphere... anyone have any suggestions?

 This site is a pretty good "how to".

 [http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

M.

---

### Post by mb_webguy on 2008-09-14
> **mike1234 said:**
> This site is a pretty good "how to".

 [http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

M.

I don't think I see anything on that page that answers his question.  (And btw he's using the most recent version of Compiz.)

---

### Post by mike1234 on 2008-09-14
> **mb_webguy said:**
> I don't think I see anything on that page that answers his question.  (And btw he's using the most recent version of Compiz.)

Set **Desktop Cube &#8594; Transparent Cube &#8594; Opacity During Rotation** to **85.0000** (or what suits you best) I use compiz - fusion.

M.

---

### Post by PsychedelicWonders on 2008-09-14
hmm.  I've been through everything.

I'm sure its something easy and simple like me not having a box unchecked.

I've fiddle and faddle with everything I see that relates to a cap or a bottom.

Still stumped.  This is going to look really sweet once I get this figured out...

---

### Post by mb_webguy on 2008-09-14
> **mike1234 said:**
> Set **Desktop Cube &#8594; Transparent Cube &#8594; Opacity During Rotation** to **85.0000** (or what suits you best) I use compiz - fusion.

M.

Yes, but that doesn't answer his question.  He doesn't want the Cube Caps to be drawn at all.  

Hey Psychedelic...  Are you sure on the Cube Reflection and Deformation plugin, the Cube Caps tab, that you have Draw Top Face and Draw Bottom Face unchecked, and the color opacity for both set to 0?  And also in the Desktop Cube plugin, the Appearance tab, that you have the desktop color opacity set to 0?

---

### Post by PsychedelicWonders on 2008-09-14
> **mb_webguy said:**
> Yes, but that doesn't answer his question.  He doesn't want the Cube Caps to be drawn at all.  

Hey Psychedelic...  Are you sure on the Cube Reflection and Deformation plugin, the Cube Caps tab, that you have Draw Top Face and Draw Bottom Face unchecked, and the color opacity for both set to 0?  And also in the Desktop Cube plugin, the Appearance tab, that you have the desktop color opacity set to 0?

Yes they are unchecked, but I dont see where exactly you make the "Draw Top & Bottom Face" allow me to set the opacity?

Perhaps that is the issue?

Here is what my screen looks like...

ALright I also checked the Desktop Cube Plugin and the Desktop color was set to 50, so when I set it to 0, they turned black...

---

### Post by PsychedelicWonders on 2008-09-14
damn it, I thought I found out the problem, but it didnt help.

Under Cube Caps, Top & Bottom colors, the opacity was set to max at 255.

I lowered both to 0, yet still are black?

---

### Post by mike1234 on 2008-09-14
> **PsychedelicWonders said:**
> damn it, I thought I found out the problem, but it didnt help.

Under Cube Caps, Top & Bottom colors, the opacity was set to max at 255.

I lowered both to 0, yet still are black?


 What about your theme colors? Under emerald you can modify themes. I'm curious if this has any effect on it. Even if you modify and save the theme, you can always revert back to the original look. Have you tried a different theme?

M.

---

### Post by PsychedelicWonders on 2008-09-14
hmm.  Thats a good question, as you can see, my theme is pretty much black, but then again, the cube cap squares didnt turn black until I dropped the opacity from 255 to 0.

So that would tell me that it wouldnt have anything to do with it?

Or perhaps 0 is defaulting to black because of my black theme?

---

### Post by PsychedelicWonders on 2008-09-14
here are 4 screen shots of all of the things were working on...

---

### Post by PsychedelicWonders on 2008-09-14
no dice, changed my theme and still have the black boxes.

---

### Post by mb_webguy on 2008-09-14
Other than the unfortunately visible cube caps, you've done a great job on your desktop, by the way.  

:guitar:

---

### Post by PsychedelicWonders on 2008-09-14
yes, thanks a lot.  I'm really really impressed with how much you can change Linux to your likings.

I will never go back to windows.

Don't get me wrong, I will always keep it just because sometimes you just need it, but god, Linux is absolutely amazing with its customizing.

It does look pretty rad doesnt it?  :D

Once I get rid of the last few of these icons, my desktop will be totally clean and everything will sit on a dock that disappears until I scroll my mouse over it.  nice.

Now once I get my desktop settings set exactly right, I am going to need to figure out how to back up my OS's so that I dont have to go through all of this.

I already plan to back up my 2nd hdd with a 3rd one via RAID to backup all of my media and data, but thats a whole nother thread.  :)

---

### Post by mike1234 on 2008-09-14
> **PsychedelicWonders said:**
> 

 I am going to need to figure out how to back up my OS's so that I dont have to go through all of this.

I already plan to back up my 2nd hdd with a 3rd one via RAID to backup all of my media and data, but thats a whole nother thread. :)


 I use aptoncd to create backups.  I don't know if all app settings are retained but I don't see why it wouldn't copy config files. You can add additional items to your cd. 

M.

---

### Post by PsychedelicWonders on 2008-09-14
Ehh I'm really trying to get away from cds, thats why I have 3 hdds as it is.

I guess I'll just get a 4th hdd and back up my OS hdd on there like I am doing my 2nd data hdd onto a 3rd.

It's alot, but gotta be safe and dont want to deal with cds anymore.

---

### Post by PsychedelicWonders on 2008-09-14
I'm thinking about setting my defaults back to original in compiz, if I cant get rid of these squares, that would drive me completely nuts and just ruin the over all look of things.

It's a lot of work, but perhaps my only option.

Perhaps I will put this in the compiz effects or special effects section.

---

### Post by PsychedelicWonders on 2008-09-15
Ive gone through these two plugins over and over and clicked and unclicked everything, but to no avail, still no dice.

Could my theme some how be influencing it like someone else suggested before?

I went to themes and selected an entirely different theme and it seemed to have changed my desktop, so I would assume it would have changed the squares, but they didnt.

I dont know, this just doesnt make any sense.

---

### Post by PsychedelicWonders on 2008-09-15
this was suggested by a fellow over on compiz-fusion forums...

HeyPsychedelicWonders,
If I Understand you correctly, you want "no" image at all on the caps and have them be tranpsarent as well!?
If so, the first thing to do is to open the cube refection and deformation plugin.
The Appeareance pull down and for Cube top colour and Bottom colour click the color swatch button and push the opacity slider down to 0.
Then open up gimp create an image 1024x1024 and transparent. 
To do this go to File ... New...when the dialog opens type in 1024x1024 and under "Advanced Options" in that dialog, "Fill with" choose transparency, and save as png or jpg whatever your preference. Make sure that the Image plugins are all enabled.
Save the file where you want it then go back into the Deformation plugin andthe Appearance Pull down and insert that transparen image into the Top image files and Bottom Image Files fields.
That should do it.

I wont be able to try it till later tonight when i get home

---

### Post by PsychedelicWonders on 2008-09-16
Success!!

---

