---
title: "Audio Errors"
date: 2010-03-15
forum: Hardware
---

### Post by Goveynetcom on 2010-03-15
My sound card 82801I (ICH9 Family) HD Audio Controller, works fine but I need to use headphones to stop bothering those around me. My headphones and speakers both output sound at the sametime... It makes my headphones useless...

How would I configure this?

Also, the driver I am using is the default one for it.

---

### Post by dmzamora on 2010-03-16
I have the same issue with my laptop. The laptop speakers work, the headset works, but when I plug the headset, both laptop speakers and headset are working.

I have Ubuntu 9.10 installed in my Dell Vostro 1014 (N series).

---

### Post by leorolla on 2010-03-16
Did you try Sound Preferences->Output->Connector and choosing Headphones ?

---

### Post by Goveynetcom on 2010-03-18
> **leorolla said:**
> Did you try Sound Preferences->Output->Connector and choosing Headphones ?
Well, I have Sound and Pulse Audio preferences.
I checked under Sound, and it doesn't show up.
It does work, but the list never shows it, it just displays my internal speakers.
Pulse Audio has no setting for it either.
I am at a loss, I do not know what to do...

---

### Post by norseman-has-a-laptop on 2010-03-18
i had the same problem what i did was use a different output for my headphones lol

---

### Post by Goveynetcom on 2010-03-18
> **norseman-has-a-laptop said:**
> i had the same problem what i did was use a different output for my headphones lol
So what did you output to?
Another audio card?
My laptop only has one I can use.

---

### Post by norseman-has-a-laptop on 2010-03-18
no just a different head phone port loli have two on my laptop

---

### Post by Goveynetcom on 2010-03-18
> **norseman-has-a-laptop said:**
> no just a different head phone port loli have two on my laptop
I have 4 USB ports, external monitor support, HDMI output, but no 2 headphone slots?
What is wrong with HP!
guess I am stuck with this problem till I figure a way around it.

---

### Post by norseman-has-a-laptop on 2010-03-18
mines is an hp it must be alil older or newer tho because i have two slots for head phones

---

### Post by norseman-has-a-laptop on 2010-03-18
> **norseman-has-a-laptop said:**
> mines is an hp it must be alil older or newer tho because i have two slots for head phones
you have an extra usb slot tho so that could be it

---

### Post by Goveynetcom on 2010-03-18
> **norseman-has-a-laptop said:**
> you have an extra usb slot tho so that could be it
That could be a problem or an answer???

---

### Post by norseman-has-a-laptop on 2010-03-18
lol not sure buddy

---

### Post by Goveynetcom on 2010-03-18
> **norseman-has-a-laptop said:**
> lol not sure buddy
I was thinking of trying an external card to see if I could a response, but I am broke :p...
So, I think I'll just keep trying to fix it when I have the time.

Thanks for your help though norseman

---

### Post by norseman-has-a-laptop on 2010-03-18
yeah weell im sure if i actually fiddle farted around with it i could give you steps but i have school tomorrow grrrr

oh and please call me fritz

---

### Post by Goveynetcom on 2010-03-18
> **norseman-has-a-laptop said:**
> yeah weell im sure if i actually fiddle farted around with it i could give you steps but i have school tomorrow grrrr

oh and please call me fritz
lol, k fritz. Call me Govey.
Not the proper place for this, but I can't VM yet!
I have school tomorrow too, but I'll fiddle with it tomorrow.

I'll update this thread with any new info.

---

### Post by norseman-has-a-laptop on 2010-03-18
sounds good 
imma subscribe

---

### Post by leorolla on 2010-03-18
> **Goveynetcom said:**
> Well, I have Sound and Pulse Audio preferences.
I checked under Sound, and it doesn't show up.
It does work, but the list never shows it, it just displays my internal speakers.
Pulse Audio has no setting for it either.
I am at a loss, I do not know what to do...

Just to figure out what is happening, you may remove pulseaudio, reboot, and try to mute the main speaker at alsamixer, while seting volume for the headpohne.

---

