---
title: "How do i force 1024x768@85Hz on my monitor?"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Kattspya on 2005-04-12
I am totally new to GNU/linux I have been using it for maybe two three hours and installed it yesterday

This is my problem:
I can not change my refresh rate from gnome. So I naturally searched the forums and wiki and got some tips. They didn't work.
I tried editing my xorg.conf file and raise the maximum allowed refresh rate. That didn't make any differance so I decided to get nasty and forced it to use 84-85Hz (wasn't sure if setting only one value would **** something up) and removed all resolutions besides 1024x768. This only made my screen go into 640x512@85Hz and also made everything blurry. So i reverted back to my old .conf file and now im back at where i started. I would like to know how to force my monitor to values i know it can handle.
The monitor is a 17" Nokia 700c

I would really like to learn Ubuntu and 60Hz seriously impairs my ability to do so.
Thanks in advance /Kattspya

EDIT: Typo
EDIT1:Changed name to indicate problem solved

---

### Post by heimo on 2005-04-12
You should probably try these lines in xorg.conf Monitor section:
```

HorizSync       30-72
VertRefresh     50-150

```

or you can also try uncommenting (putting # at the beginning of line) both lines and letting autodetect handle (didn't work for me). What are your current values?

---

### Post by Kattspya on 2005-04-12
My current values are:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

```
But I don't see how this matter since I know my screens capabilities and want to drag x.org kicking and screaming to the right refresh rate and resolution. To clarify: I want to know how to setting the screen to 1024x768@85Hz I don't care if i cant change resolutions atm.

I will try your values and autodetect (commenting out) and report back.

EDIT:
Hey! That (changing values) worked like a charm! Thanks alot! Forgive my sceptisicm. 
I have some questions though:
Why didn't it work to force it to 85?
Can you point me to any documentation to how the xorg.conf values are interpreted? 


Woho my head ache is gone!
 :grin:

---

### Post by heimo on 2005-04-12
It was probably the HorizSync line, not the VertRefresh line that did the trick. There is something called "mode lines", stuff like this:
```
Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
``` 
that is matched against your xorg.conf's Monitor section. If there's no matching modelines for your desired resolution, you won't get that resolution. You could actually make "custom" mode line just for your monitor (to get all out of it), but it's easier to just set those two lines and let the xorg choose for you.

Oh... Here it goes: Type 
```
gtf 1024 768 85

EDIT: or even further: 
gtf 1024 768 89

```
And paste the output to your monitor section. You'll get 1024x768@85Hz.

---

### Post by heimo on 2005-04-12
Oh, and in some case it helps to bring up the lower limit of VertRefresh to force higher refresh rate. I just put 1440x1050@88Hz modeline into my xorg.conf and 88 as the lower limit of VertRefresh and I got just the screen mode I wanted... Go too high and you'll probably get "out of sync" or something like that (hopefully).

Also the image quality can go down if you try to drive too much of your CRT (I'm sure you knew that, but I'm always trying to write not just for the person, but other forum members too).

Cheers!

---

### Post by Kattspya on 2005-04-13
Ok, thanks alot!

My reason for switching to GNU/Linux was not that i had any problem with my WinXP but to learn how linux works so just pasting a command and having it work is not enough for me. I want to know why a command does something not just **that** it does something. That's my major problem with most HOWTO:s they just tell you how to do something not how  and why it works. 

Again, thank you.

---

### Post by heimo on 2005-04-13
> My reason for switching to GNU/Linux was not that i had any problem with my WinXP but to learn how linux works so just pasting a command and having it work is not enough for me. I want to know why a command does something not just that it does something. 

That's hacker spirit! Knowing the technology inside out - not just what to do, but also understanding why it works the way it does. And when you understand how it works and you can change it, you can make it to do just what you want. "There's no spoon."* 


*) Quotation / movie reference. [http://www.imdb.com/title/tt0133093/](http://www.imdb.com/title/tt0133093/)

---

### Post by ecerutti on 2008-06-12
Another way is adding this line in your xorg.conf file

> SubSection "Display"
[INDENT]Depth 24
**Modes "1024x768"**[/INDENT]
EndSubsection

---

