---
title: "Sony Vaio sony vgnfz18m... compatibility ?"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by leo80s on 2007-07-26
hello everybody,

i've decidec to bought this notebook:

[http://vaio.sony.es/view/ShowProduct.action?product=VGN-FZ18M&site=voe_es_ES_cons&category=VN+FZ+Series](http://vaio.sony.es/view/ShowProduct.action?product=VGN-FZ18M&site=voe_es_ES_cons&category=VN+FZ+Series)

(It seems it's an "italian" model but it's quite equal than VGNFZ18L in England...  ([https://www.sonystyle.it/SonyStyle/catalog/setCurrentItem/(z_cua_accArea=z_cua_specs&xcm=PCM_b2ccrmstandard&z_cua_add=z_cua_fullspecs&layout=15_108_60_54_109_113_2&uiarea=2&ctype=areaDetails&next=seeItem&carea=43BAE0537FEF00AA000000002BC29B85&order=null&citem=43BAE0537FEF00AA000000002BC29B854610C5FDC02E0069000000002BC29B71&z_cua_sel_acc=)/.do](https://www.sonystyle.it/SonyStyle/catalog/setCurrentItem/(z_cua_accArea=z_cua_specs&xcm=PCM_b2ccrmstandard&z_cua_add=z_cua_fullspecs&layout=15_108_60_54_109_113_2&uiarea=2&ctype=areaDetails&next=seeItem&carea=43BAE0537FEF00AA000000002BC29B85&order=null&citem=43BAE0537FEF00AA000000002BC29B854610C5FDC02E0069000000002BC29B71&z_cua_sel_acc=)/.do)))

Before to bought it I need to know if anyone else has tried to installa Ubuntu on it and I'd like to know what does it work and what not!
Can anyone helps me, please????

thanx
Leo

---

### Post by abnerion on 2007-07-29
Hi,

I have a sony vaio FZ18M and Ubuntu 7.04 feisty and works fine !

- For the web cam u need the driver "r5u870" modified (see [http://ubuntuforums.org/showthread.php?t=289836&page=9]("http://ubuntuforums.org/showthread.php?t=289836&page=9"))

NOT WORKING:
- MIC
- Jack for earphones
- modem
- Memory Stick PRO card reader.

Anybody knows how to make this hardware to work on ubuntu? Any help will be apreciated!

( Thanks to Ubuntu team for this splendid O.S. !! )

---

### Post by David A Knight on 2007-07-29
Not much use but to get the headphones (based off what worked for my fz11m)  "working" try

create / add to /etc/modprobe.d/sound


options snd-hda-intel model=vaio probe-mask=1

then reboot / rmmod and modprobe -a snd-hda-intel

that should make the headphone socket work, although it won't turn off the speakers.

---

### Post by leo80s on 2007-07-30
what do you mean with MIC? microphone?!?!
and what about the HDMI out? does it work?
and do hibernate/suspension work?

thanx Leo

---

### Post by leo80s on 2007-07-31
up?

---

### Post by wieman01 on 2007-07-31
> **leo80s said:**
> what do you mean with MIC? microphone?!?!
and what about the HDMI out? does it work?
and do hibernate/suspension work?

thanx Leo
I got a Sony Vaio VGN and suspend & hibernate are no problem at all. Nor are widescreen and sound.

---

### Post by abnerion on 2007-08-11
Hey !

First of all, thxs wieman01. Your post make my headphones jack to work ! (but speakers keep working at the same time like does with you :( )

Suspend & Hibernate works also in FZ18M. But I don't know if HDMI works I didn't tested.


(And yes.. when I said MIC I meant microphone)


bye!

---

### Post by thecec on 2008-03-11
Hi all,

I have a FZ21M. Everything apart for suspend and hibernate is working fine.

I had to do some fixes for sound and webcam anyway. I wrote a small guide for this so if anyone needs help, just have a look at [http://atelier.inf.unisi.ch/~rigottifr/fz21m.php](http://atelier.inf.unisi.ch/~rigottifr/fz21m.php)
 
Can the guys that have suspend and hibernate working  give me some hints please?
When I try to suspend, it sleeps ok, but then when I try to resume, the screen is not woken up anymore. Any ideas?

Thx a lot

Cec

---

### Post by wieman01 on 2008-03-11
I cannot help you there I am afraid. It just worked out of the box.

---

### Post by thecec on 2008-03-12
Hey wieman could u please send me a copy of your  /etc/default/acpi-support file?
Maybe my version of the file is broken or is missing something.

Are u running compiz?

And another thing, are u by any chance using   uswsusp ?

Btw thanks a lot for ur fast reply, I really appreciate this

Thecec

---

### Post by abnerion on 2008-03-12
Hi !

FZ21M has a NVIDIA graphics card? Are you using the "oficial" or "ubuntu" module? I recomend to use the "oficial", it works better for me. (A llitle bit more FPS and better multimunitor support with "nvidia-settings" tool, nvidia power management, etc.)

(nowadays I haven't ubuntu installed in my laptop (SONY VAIO FZ18M) because I can't read MemorySticks, the sound is not working fine and the powermanagment is wasting my battery life, I will be in W vista until, may be, ubuntu 8.04 release) 

P.D.: Sorry for my english, I'm spanish and I'm writting quickly

cu

---

