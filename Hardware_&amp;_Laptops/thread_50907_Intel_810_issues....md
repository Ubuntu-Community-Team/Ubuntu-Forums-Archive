---
title: "Intel 810 issues..."
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by jpkaytrosh on 2005-07-21
I installed Hoary, and I can't move my resolution above or below 1024x768, and I'm having rendering issues. Window dragging leaves copies of the window all over the place as I move it (I forget what that's called.) Rendering is slow, and scrolling is sometimes bad.

I tried self-editing my xorg.conf to allow extra resolutions, but it didn't work.

Any help you could offer with either or both issues would be appreciated.

Thanks.

---

### Post by damonw5 on 2005-07-21
[QUOTE=jpkaytrosh]I installed Hoary, and I can't move my resolution above or below 1024x768, and I'm having rendering issues. Window dragging leaves copies of the window all over the place as I move it (I forget what that's called.) Rendering is slow, and scrolling is sometimes bad.

I tried self-editing my xorg.conf to allow extra resolutions, but it didn't work.

Any help you could offer with either or both issues would be appreciated.

Thanks.[/QUOTE]
 Try putting your 1280x1024 at the BEGINNING of EVERY one of those lines listing the displays under the "screen" section. As I remember it tries each resolution in order, starting with the first listed. Example:

SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480" 
EndSubSection

This should get you started. Any other ideas about the rest of the problems?

---

### Post by Omnios on 2005-07-21
Don't have a lot of experience with that card or the res issue other than mods to xorg.conf. I found using sudo " dpkg-reconfigure xserver-xorg " outside of dgm usefull as it is a set up program for keyboard mouse and graphics card and monitor. dpkg is probably the easiest to do as you go through the screens and tick the reses you want with using the space bar. Now the second part I had some of the problems you explained with the window streaking etc wich I solved by lowering color to 16 instead of 24 and dont realy notice any quality or color difference.

 Also there are some realy good articles in the forum on how to set up intel chips with drivers and set up tweeks. Actualy read a real good one a few weeks ago where the guy was getting amazing performance for a intel

 Hope that helps a bit
Cheers

---

### Post by jpkaytrosh on 2005-07-22
I resolved my problems for the most part, and am now running comfortably -- just like to thank y'all for your help!

JPGK-

---

