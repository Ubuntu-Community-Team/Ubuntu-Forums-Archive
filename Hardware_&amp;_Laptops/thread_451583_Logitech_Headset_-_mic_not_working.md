---
title: "Logitech Headset - mic not working"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by waylow on 2007-05-22
Hey there

I have managed to get my logitech headset to play sounds (changed setting in prefecences) but the mic isn't working.
(works with XP)

does anyone know how I can get it working?
update driver? punch it a couple times? make a voodoo doll?

---

### Post by waylow on 2007-05-24
solved it - (for anyone who is searching for a solution)

updated the drivers for my sound card (Realtek)

then installed ALSA

all seems to work now

(it was much easier than learning voodoo)

---

### Post by Caro_CR on 2007-05-25
Maybe you can give some specific steps to do that. I have the same problem but I don't understand what you did to fix yours. Can you do that?

I have a genius headset 
a sigmatel stat (integrated for inspiron)

my mic works with windows for the same laptop

---

### Post by waylow on 2007-05-25
I went to the website for my sound card

(Realtek) and downloaded the AC'97 drivers for Linux 

your card is a sigmatel?

try 
there website
or google search
[http://www.google.com.au/search?hl=en&q=sigmatel+inspiron+driver+linux&btnG=Search&meta=]("http://www.google.com.au/search?hl=en&q=sigmatel+inspiron+driver+linux&btnG=Search&meta=")

ALSA is a sound mixer - so I could check all the levels

(made sure that the capture volume was turned up and not muted)

let me know how you go :)

---

### Post by scottfinman on 2007-06-01
Battled this problem myself and this solution worked for me:

[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

Edit: The instructions were not applicable when taken verbatim (earlier version of ALSA perhaps?), however, toggling the settings where it suggests did indeed do it on my system.

---

### Post by waylow on 2007-06-02
Although I do have it working now I have noticed that some programs don't like to play the audio through the headphones (eg amarok)

still messing around with a few things -  I think that might have done the trick 
(click space in ALSA to make sure it's enabled)

thanks

---

