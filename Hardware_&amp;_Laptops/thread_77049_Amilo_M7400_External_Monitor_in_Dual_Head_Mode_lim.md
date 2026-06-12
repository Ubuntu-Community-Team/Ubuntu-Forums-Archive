---
title: "Amilo M7400: External Monitor in Dual Head Mode limited to 1024x768"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by Andres on 2005-10-16
The i810 driver doesn't seem to completely support the graphics chip of Fujitsu-Siemens Amilo M7400 notebooks. Although the problem is not new, I couldn't find a solution yet.

From the [Debian Mailing List]("http://lists.debian.org/debian-x/2005/09/msg00253.html"):
> I confirm the occurence of this kind of behaviour in a different laptop:
Fujitsu-Siemens Amilo M7400 with the same Intel 855GM graphics. However,
I use the standard resolution of 1024x768 on the internal LCD and want
1280x1024 on the external CRT, but cannot get any higher than 1024x768,
even though 1280x1024 works fine in that certain other OS.

The problem looks exactly the same in  (Xorg.0.log included in full
below too):
(II) I810(1): Not using mode "1280x1024" (no mode of this name)
(1280x1024,ExternalTFT) mode clock 100000MHz exceeds DDC maximum 110MHz

I did not need to use 855resolution to set the resolution of the
internal display, but I could use it to check that there is a 1280x1024
video mode in the video bios; output of 855resolution -l is included as
well.

Usage of a Modeline did not help either; I also did quite some research
to check my xorg.conf (included too) was set up correctly. Doing that I
discovered that several people had their external CRT output restricted
to 1024x768, so I assume the problem may actually be more widespread.See mailing list for Xorg.conf and Xorg.0.log. 1280x1024 and higher resolutions work on the external monitor as long as the internal tft isn't activated. Does anybody know a workaround?

---

### Post by nkemer on 2005-10-24
hi, i have fujitsu amilo pro with i855 card and  i can not set up dual head with it.Could u sent your xorg file to  help me,please?
thank you

---

### Post by Andres on 2005-10-24
If you don't need more than 1024x768, you can find a working xorg.conf in [the mailing list posting]("http://lists.debian.org/debian-x/2005/09/msg00253.html").

---

### Post by Tydirium on 2005-12-14
Hi Andreas, 

I have the same problem with an Amilo Pro Notebook and haven't found any solutions yet either. 

One could be 855-resolution, if the vbios does not come with a 1280x1024 resolution: 
[http://perso.wanadoo.fr/apoirier/](http://perso.wanadoo.fr/apoirier/)


This was no solution for me either. 
If you came up with a solution in the meantime, it would help me a lot, if you could share it. 
Thanks.
Carsten

---

### Post by Andres on 2005-12-14
I wish I had found a solution in the meantime, but I wasn't successful at all. 

Johannes &#9472; I quoted his posting from the Debian Mailing list &#9472; wrote (rough translation):
> I guess the Windows Intel driver provides the video bios with special modelines for the external monitor, but it seems that these modelines aren't part of the video bios. That's similar to the problem with the internal displays of some widescreen notebooks that can be solved by 855resolution. Apparently 855resolution only provides modelines for the internal display (if there's a distinction between internal and external?) or at least can't perform whatever trick the Windows Intel driver performs.

Therefore I assume that the problem could be solved by modifying 855resolution in such a way that it performs exactly the same trick as the Windows driver does -- however that trick may look like.
Does anyone know more about this?

---

### Post by pgf on 2005-12-15
[QUOTE=Andres]1280x1024 and higher resolutions work on the external monitor as long as the internal tft isn't activated. Does anybody know a workaround?[/QUOTE]

are you implying that the higher resolution works if the internal screen
is not activated?  how does one force active/inactive for the internal
screen?  i have an asus z33a, and under debian sarge the keyboard button
for switching to external worked fine, but under breezy, the key seems
to do nothing.  in other words, i can't switch monitors anymore.  is there
a command-line way to do this?

interestingly, i can get 1280x1024 on the LCD screen if i log in on a
console window and run "startx -- :1" in order to start a second X server.
but i still can't get bigger than 1024x768 on the :0 (gdm controlled) screen.
(and since i can't get activate the external monitor, i don't know if it works
there or not.)

paul

---

### Post by Andres on 2005-12-15
> are you implying that the higher resolution works if the internal screen is not activated? Yes.

> how does one force active/inactive for the internal screen?My notebook doesn't have a key to switch between the internal and the external display so the only way I know about is editing the xorg.conf file.

---

### Post by nekr0z on 2006-06-05
Hello guys!

I'm quite new to Linux, and this here is the only thread I have found for Amilo M7400 on thi forum, so maybe you could help me a little or just point to some manual or a place I could get help in...

I've just installed Kubuntu Dapper on Amilo M7400. Still cannot configure dual        head,but that's ok, I'll just try to follow what is written in this thread. More confusing is: I can't get no support for left-panel keys, as well as all the Fn+ combinations, such as volume control and stuff.

More of a problem is the non-working of the bult-in card reader, which I need badly. I'm not even sure, where to dig for solution, so any help is extremely welcome!

More questions to come, but these ones are of highest priority.

---

### Post by Andres on 2006-06-05
[QUOTE=nekr0z]I can't get no support for left-panel keys, as well as all the Fn+ combinations, such as volume control and stuff.

More of a problem is the non-working of the bult-in card reader, which I need badly.[/QUOTE]
I have been using Ubuntu on a M7400 for quite some time and I didn't get these two things to work either. I don't care about the additional keys and key combos but the card reader would be nice to have. Sadly it seems to be Windows-only. If you find some workaround please let me know.

---

### Post by nekr0z on 2006-06-06
Well I added M7400 to the wiki hardware support page at [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu) so we can write HOWTOs for people having problems. Think it's a good idea to have all things in one place.

---

### Post by nekr0z on 2006-06-06
By the way, I got the additional keys working. The solution is in the thread I mentioned.

---

### Post by slx on 2006-09-25
I have exactly the same problem as Andres.

Do anyone have a solution?

---

