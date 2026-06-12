---
title: "i need help ASAP my pc keeps shuting it self off!"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by charmint on 2007-12-21
help! my pc keeps shuting it self off. this problem first started with windows xp and i just completly switched to ubuntu and its still happening. it happened so many times i know when it shuts down. it shuts down when ever so much data is running or being downloaded. why is this happening and how do i stop it? i also noticed before it shuts down on ubuntu it says something about bios battery reading level low and then turns off. i thought maybe my battery was bad so i tryed to use my laptop with just the power cable pluged it and it still shut down on me. could something be wrong with my hardrive? i continue to hear the harddrive making so loud noise. i need my laptop for school and work please help asap

---

### Post by finferflu on 2007-12-21
I think your machine is overheating. Are you leaving room for the fans to cool it down?

---

### Post by charmint on 2007-12-21
i have a table top fan i bought aimed right at my laptop when ever i'm using it to cool it down, so dont believe its a over heating issue

---

### Post by finferflu on 2007-12-21
I don't want to push this too much, because surely I'm no expert, but do you think that is enough? Could there be something obstructing ventilation?

---

### Post by charmint on 2007-12-21
concidering its snowing here and my homes heater needs fixing, i would say yeah its enough. nothing blocking the small @$$ air vent on my laptop. as i send above, it only happens when downloading and some much data has been ran for a while.

---

### Post by finferflu on 2007-12-21
Ok ok, well, as I said I'm not a techie, so that is as far as I can go... I hope somebody else will turn up here...
I think if you can copy verbatim the error you get in Ubuntu before it shuts down it will be a lot helpful.

---

### Post by heidfirst on 2007-12-21
Take a look at the messages file in /var/log and see if there are any error reported relating to either the hard drive /dev/hda (ide) or /dev/sda (sata).

Also check for messages relating to eth? 

Post any errors and we might be able to provide some more help.

Gordon

---

### Post by charmint on 2007-12-21
no errors in log...hmm well i had problems with this laptop since the day i bought i (may 2005) but wal-mart wouldnt take it back. my advice to everyone NEVER BUY A TOSHIBA SATELLITE FROM WAL-MART THEY BEEN SETTING IN STORAGE COLLECTING DUST. AND IF YOU DO BUY ONE FROM THERE GET THE EXSTEND WARRENTY!

---

### Post by hessiess on 2007-12-21
> i also noticed before it shuts down on ubuntu it says something about bios battery reading level low and then turns off

the bios battery is not the same as the laptop battery, it is a little button bettery (round flat thing) underneth one of the covers, you need to change this;)

if it was also hapaning in windows its almost 100% a hardwere problem

the bios settings are stored in the cmos, this is memory that needs a small electrical current to store the data. the button battery provides this current when your computer is unplugged, it also powers the system clock

---

### Post by kellemes on 2007-12-21
> **finferflu said:**
> I don't want to push this too much, because surely I'm no expert, but do you think that is enough? Could there be something obstructing ventilation?

I think it's a good question..
I had this problem some time ago.. shutting down etc..
I found out temperatures reached 70+ Celsius.
My proc-vent had been covered in dust from years of use without cleaning the housing.
Well, just a thought..

By the way, it's snowing a little in Amsterdam. :popcorn:

---

