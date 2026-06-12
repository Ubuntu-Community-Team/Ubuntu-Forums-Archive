---
title: "Graphic Card issue? or something else..."
date: 2011-05-21
forum: Hardware
---

### Post by Xinu38 on 2011-05-21
Hi, I installed 10.10 on my laptop last weekend, and i must say, it works almost perfectly. Running it on a Compaq Presario CQ56. Everything works up to the point of small glitches with windows/videos. For instance, if i go to hulu.com, where the words come up on the front page to show you what the picture is about, i get black squares instead. Also some videos will have like a a small 10x10 box just flickering in the middle of the video.

The other side of this, buttons will disappear as well, i was on a site and i would try to click a button, but it will turn into a grey box upon hovering with the mouse, and it will not click the link unless i refresh and try to click it faster then the grey box appears. i got some screen shots of what i mean as well. 

im sure all i need to do is install a driver, but i am not experienced enough to know what to do exactly. or even if that is the problem. 

I have an Intel GMA 4500M stock card in this laptop. I dont know how to get the driver for it...if i need it, but here is the lspci 
```
stoke@stoke-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```theres my graphics card just in case.

i could say its my browser, but it also happens when i hit applications, the buttons wont appear unless i hover over them. 

The grey box is supposed to have the description of the picture.
[IMG]http://i2.photobucket.com/albums/y41/Xinu38/Screenshot-9.png[/IMG]

The applications dont appear unless i hover over them here
[IMG]http://i2.photobucket.com/albums/y41/Xinu38/Screenshot-10.png[/IMG]

The 20 buttons to add toppings to the pizza disappear upon mouse hover.
[IMG]http://i2.photobucket.com/albums/y41/Xinu38/Screenshot-1-2.png[/IMG]

is this a graphics driver issue or something else im unaware of? Thanks

---

### Post by Xinu38 on 2011-05-22
This also happens in 11.04. tested on both. anyone have an idea?

---

### Post by diazlg on 2011-05-25
I also have a problem with mi  Intel Corporation 4 Series Chipset Integrated Graphics Controller. when I run compiz -check (see [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)) it says that I need to update my video card driver controller. But I don't know where to find one. I've checked Intel page, but didn't find anything that seems to work, I'm a very new user of Ubuntu 11.04 and have no idea of what to do to find and install a proper video card drive. If anyone could help me, I'll be really grateful.

note: I've run compiz -check for solving a problem concerning my windows title bar disappearing. I've checked others solutions for that problem but anything posted seems to work for me, now I have the opportunity to try another solution, and seems to be to update my video card driver.

Thanks

---

