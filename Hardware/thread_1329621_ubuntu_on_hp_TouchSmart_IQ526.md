---
title: "ubuntu on hp TouchSmart IQ526"
date: 2009-11-17
forum: Hardware
---

### Post by matt_knelsen on 2009-11-17
hey all,

i have a project in which i am considering a touchscreen computer running ubuntu. at first, i've looked at [hp touchsmart IQ526]("http://www.amazon.com/TouchSmart-IQ526-Desktop-Processor-Premium/dp/B001N2MZZW"), but i don't have much of a preference, as long as i am able to get the touchscreen functionality working. as i'm an ubuntu newbie, i would like to know if there's any touchscreen computer or tablet pc that works with ubuntu and also if there's a digital keyboard avaliable. many thanks!

---

### Post by Favux on 2009-11-17
Hi matt_knelsen,

Welcome to Ubuntu Forums!

There are multiple touchscreen tablet pc's and computers working in Ubuntu.  However multi-touch support (gestures) is just being added for linuxwacom.  You can get one finger touch for the N-trig digitizer too, although there is some work almost ready with gestures.  So it really depends on the exact hardware.  And you have to research it carefully.

There are several onscreen keyboards.  CellWriter may be the best because it has letter recognition.

I hope this helps.

---

### Post by matt_knelsen on 2009-11-18
hi Favux, thanks for your reply,

to my project, complex gestures are not so important, i just would like to be able to use the ability to click using finger pressure, and maybe do some window dragging, but that's about it. so, i just wonder if the hp model i've cited above can have its touchscreen property activated in ubuntu, as i said, considering only my projects needs. 

i'll probably ask hp about this, though i would doubt they will give me any decent answer. but thanks for your reply anyway, i'll research some more. cheers,


matt

---

### Post by Ayuthia on 2009-11-18
I am thinking that the TouchSmart IQ526 is most likely using the NextWindow hardware.  There is a person in the [TouchSmart forums]("http://www.touchsmartdevzone.com/forum/thread/1876/Linux-Forums/") that has the IQ506 and it has the NextWindow hardware and in Linux, it would be using the evtouch driver.

The poster in that thread seemed to have some problems getting it to work, but on the links the he provided, it does seem to work on 8.10.

If you do talk to HP, you might want to ask which digitizer it uses for the touchscreen.  It looks like HP uses N-Trig, Wacom, and NextWindow.  The N-Trig (The HP tx2 series) does not work out of the box, but with some patches it will accomplish your needs.  The TX2000 series and the dv3 series use the Wacom version (Favux, correct me if I am wrong about this).  The TX2000 series has the one-finger touch and the dv3 series has at least two fingers.  Wacom does provide open-source drivers for them, but the dv3 series is pretty new and the code is currently in the development stages (which are available through the linuxwacom site).

In my opinion, the Wacom ones are supported better in Linux.  I currently have the tx2 version with the N-Trig and it works well for me, but I created my own driver and kernel module patches to get two-finger touch to work.  N-Trig has not provided any assistance in Linux as of yet.  Unfortunately, I have very little experience with the HP desktop version.  I would love to get one, but my wife sees how much I work on my laptop and will most likely never let me have one...

---

