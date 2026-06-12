---
title: "[SOLVED] Eye of Gnome Filtering?"
date: 2008-10-24
forum: General Help
---

### Post by kaspar_silas on 2008-10-24
Hi all,

I made a simple PGM image of a few rows of differing grey levels. 

When I open it in Gwenview it looks correct. However opening the same file in the gnome viewer only shows a filtered image. I attached a screen shot showing the filtering.

Anyone know why this is or more importantly how to stop it?

---

### Post by kaspar_silas on 2008-10-27
Hi,

Could someone else just confirm this filtering effect.


Copy the following text into a file called "test.PGM"

```
P2
5 10
10
0 0 0 0 0
5 5 5 5 5
0 0 0 0 0
5 5 5 5 5
0 0 0 0 0
5 5 5 5 5
0 0 0 0 0
5 5 5 5 5
0 0 0 0 0
5 5 5 5 5 
```



Then view the PGM file with eog (gnome's image viewer) and compare it to the same file viewed with gwenview or gimp or something like that.

---

### Post by kaspar_silas on 2008-11-07
Really? No one knows. Didn't expect that.

Well it doesn't really matter. I just switched to gqview for now. Still if anyone works out how to solve this eog thing or even knows why it happens let me know. 

Gracias

---

### Post by Yashiro on 2008-11-07
I cut out your banded image. Saved it as .pgm in Gimp.
Opened fine in Eye of Gnome. Changing preferences in eog made no difference to the output on screen at any time.

A problem with your .pgm export and not EoG's import?

---

### Post by kaspar_silas on 2008-11-11
Sorry I didn't notice your reply. Thanks for replying but I think you aren't doing the same thing as me. When you say "you cut out my banded image" do you mean you screen captured, cropped and used gimp to save the result as a .pgm. 

As if that is the case you probably saved an image a few hundred rather than a few pixels wide. I suspect my problem is due to an anti aliasing feature so you won't see it on that scale. 

I can't be doing the exporting wrong as I am not exporting. I am forming the .pgm by hand. If you type the code in the second post into a blank file and save it as .pgm then you have a tiny pgm image file.

I also don't think it's a problem with the import as no matter how I alter the image it always looks okay at a distance. However if you zoom into the actual pixels they are blurred. So as I said I suspect this is anti aliasing of some sort but I want to know how to turn it off.

---

### Post by Yashiro on 2008-11-11
I produced your second file as  you stated.

When opened in EoG:

a) If Smooth images when zoomed is enabled: You have black bands accompanied by a gradient between each band.

b_If Smooth images when zoomed is disabled: You have black and grey bands. Flat alternating bands with no gradient.


Gimp displays the second image, type b). You have smooth images enabled in EoG OR somehow your EoG build has it permanently enabled despite what you apply in the preferences screen.

---

### Post by kaspar_silas on 2008-11-12
Totally overlooked that option.

Much oblidged

---

