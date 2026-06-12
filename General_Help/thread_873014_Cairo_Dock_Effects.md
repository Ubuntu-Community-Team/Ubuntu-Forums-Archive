---
title: "Cairo Dock Effects"
date: 2008-07-28
forum: General Help
---

### Post by nkri on 2008-07-28
Hey everyone.

I recently installed Cairo dock and have it configured the way I like, but I want to know the location of the file that defines what the effects do.  Coming from OS X, I want to use the bounce effect, but I hate the way it "squeezes" down before jumping up and want to change it.

I searched everywhere in the configuration files (/usr/share/cairo-dock and ~/.cairo-dock), and even the source code, but couldn't find how to customize this:(.

And, yes, I have already checked the configuration GUI; there's nothing in there about customizing the effects, just which ones to use.

Does anyone know at least where the file is, if not how to edit it?  I'm thinking it might have something to do with Compiz, but can't be sure without help.

Thanks!
-nkri

---

### Post by seamustry on 2008-07-28
yeh i've been trying to configure cairo dock too (using the mac os x theme)..

want to know how to change the icons and how to show text above icons...

---

### Post by nkri on 2008-07-28
> **seamustry said:**
> yeh i've been trying to configure cairo dock too (using the mac os x theme)..

want to know how to change the icons and how to show text above icons...

To change icons: right click on the icon you want to change and click "Modify this launcher."

Where it says "Image's name or path," click open and navigate to the icon you want.  Then click Okay and it should be changed.

> *how to show text above icons...*
Do you mean show only the selected icon's text?  If so, right click anywhere in the dock>Cairo-Dock>Configure.

Once there, go to the System tab and under Labels, check the box that says "Show label of the currently pointed icon only."


So, anyone know how to modify the effects:)?
-nkri

---

### Post by seamustry on 2008-07-29
yeah i did what you said for showing labels but it's still not showing the text...can you point me to somewhere to make our own cairo dock theme?

---

### Post by fabounet on 2008-07-30
in this theme the size of the text is set to 0 (to not show labels), so set it up to a non-zero value (like 14)

---

### Post by nbayiha on 2008-07-30
Do someone know how to make cairo-dock start automatically one i log in ?

Edit : i found it , To start the dock when you boot up your pc, go to &#8220;system -> preferences -> sessions&#8221;, press &#8220;add&#8221; and in the middle field enter &#8220;cairo-dock&#8221; .

---

### Post by seamustry on 2008-07-30
> **fabounet said:**
> in this theme the size of the text is set to 0 (to not show labels), so set it up to a non-zero value (like 14)

thanks but i can't find that in the config. menu...can you tell me how to change the size?

---

### Post by fabounet on 2008-07-31
switch to the "advanced mode" in the config panel (9 tabs instead of 2)
this parameter is in the "Icons" tab, in the "Labels" paragraph, if I remember correctly.

---

### Post by seamustry on 2008-07-31
thanks i got it now!

---

### Post by nkri on 2008-08-20
bump

---

