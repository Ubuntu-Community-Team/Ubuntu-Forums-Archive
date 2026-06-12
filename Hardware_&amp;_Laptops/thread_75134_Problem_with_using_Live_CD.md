---
title: "Problem with using Live CD"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by Single on 2005-10-13
I started the installation with "live noapic nolapic" but the screen became blank when it reached to the point when I can hear the boot sound. I tried to randomly move and click my mouse, and I could hear the respond sound :s , but the screen was blank.

This is the first time I try using Ubuntu. Please help :) 



Spec:

Acer TravelMate 4103WLMi
Pentium M 1.8G
15" widescreen
ATI Radeon X700
1GB DDR2

---

### Post by civilwarlord on 2005-10-13
I'm going to guess that you may need to add a "vga=" line when you boot from the cd.

640x480 vga=769
800x600 vga=771
1024x768 vga=773
1280x1024 vga=775
1600x1200 vga=796

try choosing which resolution you want, and add the vga= line

example:  linux vga=773

It's worth a try.

---

### Post by John.Michael.Kane on 2005-10-13
also vga=792

---

### Post by Mashang on 2005-10-13
I think you are mistyping your labtop model it shoudl be Acer TM 8103 and if that is the case none of the "vga" parameters worked for me ( I have 8104 basically same as 8103 but 2.0Ghz ) anyhow if you want to try ubuntu on it good luck ....
I am working on it found some cool stuff on the net none really help me .. 
just install the ubuntu and configure xorg.conf
under "device" add the line 
' Option        "MonitorLayout"       "LVDS,AUTO" '

I hope that helps !

---

### Post by Joenco on 2005-10-14
Hello,

I also have a acer widescreen which is 1280 x 800.
Which settings should I use?

Thank you,

---

### Post by Single on 2005-10-14
> I think you are mistyping your labtop model it shoudl be Acer TM 8103 and if that is the case none of the "vga" parameters worked for me ( I have 8104 basically same as 8103 but 2.0Ghz ) anyhow if you want to try ubuntu on it good luck ....
I am working on it found some cool stuff on the net none really help me ..
just install the ubuntu and configure xorg.conf
under "device" add the line
' Option "MonitorLayout" "LVDS,AUTO" '

No, my model is definitely 4103WLMi

I have installed Ubuntu, but still the same problem...blank screen.
I can only use console ctrl+alt+f1 since that is the only way I can see something. But what commands do i need to use to find and open the file and edit it?

---

