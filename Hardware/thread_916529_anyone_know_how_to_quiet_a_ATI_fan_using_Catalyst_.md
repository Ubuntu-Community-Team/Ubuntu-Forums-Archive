---
title: "anyone know how to quiet a ATI fan using Catalyst drivers?"
date: 2008-09-11
forum: Hardware
---

### Post by kraymore on 2008-09-11
I have a ATI card that uses the Catalyst drivers and I was wondering if there was anyway to quiet the fan on it?  

its too loud to be comfortable with, and while I wouldn't want it to overheat, I also do not want it running as loud as it is now.  

its a ATI FireGL v7200.  I thought maybe changing to fglrx would quiet the fan, fglrx wouldn't render my screen in a acceptable resolution, and was still loud.  radeonhd, worked, but was loud.  I'd really accept any solution that would allow it to run the fan not at full speed which i believe is what it is doing at all times.  

thank you

---

### Post by Labello on 2008-11-10
I have got an ATI FireGL 5200 and i have got the same Problem. 

I am on Intrepid and with the restricted Drivers the GPU-Fan is running with 100% all the time, while the Opensource-Drivers that are used by the Live-CD-Session work very well without any Problems just not as fast as fglrx.

---

### Post by zaobz on 2008-11-10
How about adjusting the card's clock?

aticonfig --lsp ;Check the NUMBER of the mode you want

aticonfig --set-powerstate=NUMBER

---

### Post by Labello on 2008-11-10
> **zaobz said:**
> How about adjusting the card's clock?

aticonfig --lsp ;Check the NUMBER of the mode you want

aticonfig --set-powerstate=NUMBER

thanks! but is there any command that shows me the corrently set values for those properties?

---

### Post by Skripka on 2008-11-10
> **Labello said:**
> thanks! but is there any command that shows me the corrently set values for those properties?

Whichever entry has a star (*) next to it is your current powerstate.

---

### Post by Yashiro on 2008-11-10
**aticonfig --odgt**
*returns card type and current core temp*

**aticonfig --pplib-cmd "set fanspeed 0 XX"**
*sets fan speed percentage. aticonfig --pplib-cmd "set fanspeed 0 60" sets it to 60% for example.*

Should work on any Catalyst package with a version of 8.6 or greater.
Tested here on 8.9.

---

### Post by zaobz on 2008-11-11
> **Yashiro said:**
> **aticonfig --odgt**
*returns card type and current core temp*

**aticonfig --pplib-cmd "set fanspeed 0 XX"**
*sets fan speed percentage. aticonfig --pplib-cmd "set fanspeed 0 60" sets it to 60% for example.*


Didn't know you can also adjust the fan speed directly :)
Just wondering though, what happens if you set the fan speed too low and the card becomes really hot? Will it scale up automatically to cool it down?

---

### Post by 4-Ever-Euphemistic on 2008-11-11
You can just just press FN and F10 to play it in quite mode!

The fan totally switches off!


Furthermore,parden my ignorance,but what is the software ATI used for?

Ever since I got my laptop I never setted it up.

Enlighten me please!

Cheers!

---

### Post by Skripka on 2008-11-11
> **zaobz said:**
> Didn't know you can also adjust the fan speed directly :)
Just wondering though, what happens if you set the fan speed too low and the card becomes really hot? Will it scale up automatically to cool it down?

I never played with it...I'd wager, considering the primitive state of their drivers--in your scenario, your card would fry.

---

