---
title: "Trust mouse/presenter issue"
date: 2010-01-13
forum: Hardware
---

### Post by balilu on 2010-01-13
I have recently bought [this]("http://trust.com/products/product.aspx?artnr=16449") mouse/presenter (w/t trackball instead of wheel)(Trust 16449) from trust. It acts as a normal mouse when on desk and uses the track ball as a wheel. and when i pick it up the track ball becomes the mouse movement and i have easy access to the 2 back buttons as seen on the below pic

[IMG]http://www.trust.com/_images/products/500/16449-4.jpg[/IMG][IMG]http://www.trust.com/_images/products/500/16449-3.jpg[/IMG]

My issue is how the 2 back buttons work. Since im using my pc on a bed i dont have any hard surface so ill be using it mostly in my hand using the trackball (with my thumb) to move the pointer on the screen and i would like for the back buttons to function as my left and right click but they work as next & prior.

I have tried many ways to fix this but it seems that the buttons on the back are read as keyboard buttons. 

This is my xev output when on desk:

> 
Left Button = Button 1
Right Button = Button 3
Middle Button = Button 2
Trackball Up = Button 4
Trackball Down = Button 5
Trackball Left = Button 6
Trackball Right = Button 7
Back Button 1 = Keycode 112 (Prior)
Back Button 2 = Keycode 117 (Next)


And this is my xev output when in my hand:

> 
Left Button = Button 1
Right Button = Button 3
Middle Button = Acts as Keycode 9 (Esc) & If i press it again acts as Keycode 71 (F5) (and the esc again and goes on)
Trackball = Works in moving my mouse pointer
Back Button 1 = Keycode 112 (Prior)
Back Button 2 = Keycode 117 (Next)


Any Ideas how i can make the back buttons work as left and right click? And also if possible have my middle button work always the same as a middle button?

Note: Im running Kubuntu Karmic but this is not exactly a linux issue since i've tried it on a friends pc (Win 7) and it acts the same.

Sorry for the long post but i wanted to make sure i explained everything i can. Hope somebody can help me

---

### Post by balilu on 2010-01-14
anyone???

---

