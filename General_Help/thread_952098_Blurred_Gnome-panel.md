---
title: "Blurred Gnome-panel?"
date: 2008-10-18
forum: General Help
---

### Post by dozersmasher on 2008-10-18
Ok, if you have ever seen Windows Aero:
[IMG]http://images.pcworld.com/news/graphics/133191-aero.jpg[/IMG]
You may have noticed a slight blur or other distortion in the transparent part of the window.


Is there any way to do this with gnome-panel?

---

### Post by dozersmasher on 2008-10-18
I seem to have solved my own problem.
I just opened this picture into GIMP:
[IMG]http://upload.wikimedia.org/wikipedia/en/9/93/Windows_Vista_Open_Dialog.png[/IMG]

Then cut out a small section of the titlebar.
The result is this:
[IMG]http://dl.getdropbox.com/u/249397/aero2.png[/IMG]

Which may be a bit hard to see.

Earlier, I had this:
[IMG]http://dl.getdropbox.com/u/249397/aero.png[/IMG]
But the cutoff was too noticable.
Here is a current screenshot.

[IMG]http://dl.getdropbox.com/u/249397/aeroeffect.png[/IMG]

---

### Post by aschwerin.moses on 2008-10-18
im sure u have compiz... select the BLUR plugin in it.. and that should give u the blur effect for gnome.. 

ps: ur video card has to support blur

---

### Post by davbren on 2008-12-08
I would also like to know this. As far as I can see. The blur plugin only blurs the title bars...

Method:

Open Compiz-config

Go to the "Opacity, Brightness and Saturation" section

In the "Window specific settings" box click new

In here type "(name=gnome-panel)" w/o quotes and choose the desired opacity 

*[COLOR="Red"](NB: The blurring works better if the panel pic is opaque to begin with)[/COLOR]*

Click Close.

Now check the "Blur Windows"

In the "Blur Windows" section there is an "Alpha blur" box.

In this box type "(name=gnome-panel)" w/o quotes

In the "Blur Filter" drop-down menu, select "Gaussian"

Select the desired amount using the slider below it.

And Voila! that should give you a nice "vista-esque" blur on your panel!

---

### Post by dungpt on 2009-05-07
> **davbren said:**
> I would also like to know this. As far as I can see. The blur plugin only blurs the title bars...

Method:

Open Compiz-config

Go to the "Opacity, Brightness and Saturation" section

In the "Window specific settings" box click new

In here type "(name=gnome-panel)" w/o quotes and choose the desired opacity 

*[COLOR="Red"](NB: The blurring works better if the panel pic is opaque to begin with)[/COLOR]*

Click Close.

Now check the "Blur Windows"

In the "Blur Windows" section there is an "Alpha blur" box.

In this box type "(name=gnome-panel)" w/o quotes

In the "Blur Filter" drop-down menu, select "Gaussian"

Select the desired amount using the slider below it.

And Voila! that should give you a nice "vista-esque" blur on your panel!

doesn't work with me.
i can blur unfocus windows, but i can't blur my panel.

---

### Post by dungpt on 2009-05-09
i can't use alpha blur in 9.04.

---

