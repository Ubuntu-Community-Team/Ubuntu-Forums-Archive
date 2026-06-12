---
title: "calibrate monitor"
date: 2015-01-11
forum: Hardware
---

### Post by Andi_GreyScale on 2015-01-11
Seems silly, not knowing how to, but I can't remember how I did it in 12.04 and I'm on 14.04 now. 

I used the search function and didn't find anything that actually satisfies my dilemma. 

I've got a Samsung 27", if that matter.

---

### Post by Andi_GreyScale on 2015-01-11
Am I sol then?

[IMG]http://i.imgur.com/ssjx7W1.png[/IMG]

---

### Post by Andi_GreyScale on 2015-01-12
This really is a problem, any kind of help would be great. My .jpg images are way darker than my .png images and that's a serious issue for me.

---

### Post by weatherman2 on 2015-01-13
Now that is odd.  I can't imagine why that would have anything to do with calibration, unless the JPEG images are heavily compressed or not exactly the same as the PNG files.

I have done only a crude calibration of my monitor by adjusting the gamma using a grey card as a reference.

---

### Post by aljosa2 on 2015-01-13
hi,
same problem here (ubuntu 14.04.1) with both notebooks, Asus N750JVT-4069H and Asus X750JN-TY027H.

---

### Post by buzzingrobot on 2015-01-13
Google 'Argyll CMS'.

Profiles generated in Windows can be used in Ubuntu, in my experience.

I am not aware of any vendors selling a hardware/software calibration kit for Linux, as they do for Windows.

---

### Post by efflandt on 2015-01-14
Are you sure that the original images are not different? Are you saying that if you open a png in gimp, save or export it as jpg, it ends up darker?

I initially calibrated my 32" LG 1080p HDTV using DVE (Digital Video Essentials on DVD or BluRay) by adjusting the TV itself (which with digital color is primarily just brightness/contrast adjustment). And I calibrated my Lexmark color laser (adjusting defaults in its hardware), so printed reference images photorealistcally matched their appearance on my screen.

I looked at a few images that I have as both png and more compressed jpg, and the jpg images appear to be just slightly darker, but it is more that the lossy compression mottled the colors with pixelated light and dark dots that looked dirty, especially near dark text or other transitions on a very light grey background. But it really seemed that the colors, especially very light grey tones, were smoother and cleaner and lines and text were crisper with a bit more contrast in the lossless png. So maybe it depends how much compression is used for jpg, because you lose detail when using high lossy jpg compression.

---

### Post by w-andrew-keech on 2015-01-15
if anyone in this thread is looking for direction on what is needed, check out the Argyll CMS website. at a minimum you will need to find a colorimeter for calibrating an output device like a tv or lcd monitor.

---

### Post by Enigma12 on 2015-01-19
From what I have read, the Pantone Huey can be used with Linux. Possibly the Huey Pro as well. Got one, but I haven't bothered setting it up yet. 

For a visual calibration, I use a perfectly neutral grey image and adjust the monitor to make it look as neutral as possible. That's good enough for my needs.

---

### Post by Andi_GreyScale on 2015-01-21
> **efflandt said:**
> Are you sure that the original images are not different? Are you saying that if you open a png in gimp, save or export it as jpg, it ends up darker?

I initially calibrated my 32" LG 1080p HDTV using DVE (Digital Video Essentials on DVD or BluRay) by adjusting the TV itself (which with digital color is primarily just brightness/contrast adjustment). And I calibrated my Lexmark color laser (adjusting defaults in its hardware), so printed reference images photorealistcally matched their appearance on my screen.

I looked at a few images that I have as both png and more compressed jpg, and the jpg images appear to be just slightly darker, but it is more that the lossy compression mottled the colors with pixelated light and dark dots that looked dirty, especially near dark text or other transitions on a very light grey background. But it really seemed that the colors, especially very light grey tones, were smoother and cleaner and lines and text were crisper with a bit more contrast in the lossless png. So maybe it depends how much compression is used for jpg, because you lose detail when using high lossy jpg compression.

My exported .jpg images appear lighter than my exported .png images now that I've done another fresh install of 14.04

I don't change them in any other way, so the original images are the same.

---

### Post by Andi_GreyScale on 2015-01-21
> **Wayne_Terrebonne said:**
> From what I have read, the Pantone Huey can be used with Linux. Possibly the Huey Pro as well. Got one, but I haven't bothered setting it up yet. 

For a visual calibration, I use a perfectly neutral grey image and adjust the monitor to make it look as neutral as possible. That's good enough for my needs.

May I ask what image you used? =)

---

### Post by Enigma12 on 2015-01-22
> **Andi_GreyScale said:**
> May I ask what image you used? =)

It's one that I made myself years ago, long before I even considered trying Linux or even had a colorimeter, but I needed something to judge and adjust my monitor. 

Did a copy light setup of a Kodak 18% gray card with a digital camera, of course. In Photoshop, I did a strong Gaussian Blur to make it perfectly even throughout, then checked the readings with the Info and neutralized it with Levels. 

If I hadn't had a gray card, I would have photographed a heavy overcast sky or other flat gray subject very out of focus and done the same Photoshop things to it. Gimp can do those Photoshop tweaks.

---

