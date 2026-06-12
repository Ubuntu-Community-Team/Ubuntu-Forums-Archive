---
title: "Screen Brightness Control"
date: 2011-12-28
forum: Hardware
---

### Post by mcmike389 on 2011-12-28
I am a Linux newbie (I am a Windows admin and SQLServer DBA - don't hurt me), and I am hoping that someone here can help me or guide me to the right place.  I recently installed Ubuntu on a Dell laptop (with an Intel 945gm graphics chip), and after about a week of using it upgraded to 11.10.  Since the upgrade, every time it comes back from suspend mode the screen brightness is turned all the way down.  I found the Screen Brightness control so I can fix it when it happens, but it is annoying.  

After finding the control, I discovered that it does not work correctly--all the way to the left is very dim, and all the way to the right seems to be full brightness, but in between the brightness level jumps around.  One notch to the left of full brightness is almost as dim as all the way to the left, and one notch further to the left is about 50% brightness.  

I searched on Google and found a few people reporting the screen being dim after suspend, but they were for older versions of Ubuntu or seemed to be slightly different symptoms, and none had any solutions.  If this were happening on a Windows machine, the first thing I would check is if the video drivers were up-to-date, but I don't know how to do that on Ubuntu (I searched the Ubuntu website, and the most comprehensible instruction I found was "ask in the Forum".)  Is it safe to download the latest Linux driver from Intel's website, or is there a Ubuntu-specific file I should use?

---

### Post by MoreOrLess on 2011-12-28
On a laptop, the brightness is generally controlled by ACPI (and the video driver doesn't affect it, although it can probably do brightness corrections). What model laptop do you have?

---

### Post by mcmike389 on 2011-12-28
Dell Latitude D620

---

