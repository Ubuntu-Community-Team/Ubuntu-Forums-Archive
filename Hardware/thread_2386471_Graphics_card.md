---
title: "Graphics card"
date: 2018-03-06
forum: Hardware
---

### Post by rakeshvz on 2018-03-06
best fellow linux fans
I have a problem that I can not figure out
I had an older version of ubuntu running but there was no support for that anymore
now I have updated the version to ubuntu mate 16.04 clean installation
everything seems to work fine just not my video card
I have a dell optiplex 3020 intel-i3  business version
with a g-force g210 video card also have a hd5450 card
but with all two cards it does not go well
if I open a web page and then reduce the page the old image stays on the screen until I click with the mouse on it or I see all pixels in edges


what I have tried so far to make it work
kernel upgraded to 4.15.7-041507 generic
driver from X.Org X Server upgraded to nvidia gt210 driver in menu driver


what else can I do to get it running smoothly?
are there special driver required?

this is how i see it  left side wont go away
[https://preview.ibb.co/daXAf7/20180306_141235.jpg](https://preview.ibb.co/daXAf7/20180306_141235.jpg)

---

### Post by tinylagarto on 2018-03-07
Can you try to disable the compositor from the Mate control center, looking into something like window manager preferences. 
Report back and we can try another compositor like Compton or Compiz if you still want some effects.

---

### Post by monkeybrain20122 on 2018-03-07
You need some special tweaks for optimus system (hybrid with an intel and a Nvidia card) There are many tutorials on the internet regarding optimus on Linux, most involve something called bumblebee (though I think Nvidia now has some support for Optimus on Linux so Bumblebee may no longer be needed) Check out a more recent tutorial and see if it makes sense (maybe read a few and do some thinking before you actually attempt anything, avoid tutorials that are > 3 years old) Since I have never had the misfortune to work with an Optimus machine I can't tell you more.

---

### Post by deadflowr on 2018-03-07
HD5450?
AMD Radeon HD5450?

---

### Post by monkeybrain20122 on 2018-03-07
> **deadflowr said:**
> HD5450?
AMD Radeon HD5450?

Missed that. It makes no sense.

---

### Post by rakeshvz on 2018-03-09
nice follow some tutorials al seems to work spotless for now 
super thank you it helped for my
this little bit of info really needed

i got some spare card 
nvidia g210 
Ati hd5450 
I have a Dell PC
more does not fit mini atx pc

---

### Post by deadflowr on 2018-03-09
What tutorial?

---

### Post by mörgæs on 2018-03-09
Good, please mark the thread solved.

---

