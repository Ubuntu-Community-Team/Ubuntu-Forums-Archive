---
title: "How do I put JPEGS into my Wallpaper folder?"
date: 2008-11-18
forum: General Help
---

### Post by the lemming on 2008-11-18
I have a couple of images that I would like to use as wallpaper and to keep things nice and tidy I have tried to put those images into the Wallpaper folder.

Problem is that I don't have permision to do this.  Could somebody please tell me how I can put images into my usr / share/ wallpaper folder?

Cheers

---

### Post by Therion on 2008-11-18
You could actually move files into that folder by opening a Terminal and using```
sudo nautilus
``` or, if you just want to use additional pics as your desktop wallpaper, you can put the files anywhere you want, right-click on your desktop, click on "Change Desktop Background" and navigate to the picture you want to use without having to move the actual .jpg file.  If you DO move the picture though, you'll lose it as your desktop wallpaper.  For this reason I usually just create a new folder, specifically for wallpaper pics, in my /home directory.

---

### Post by the lemming on 2008-11-18
> **Therion said:**
> or, if you just want to use additional pics as your desktop wallpaper, you can put the files anywhere you want,

I'd quite like to put those images into the Wallpaper folder to keep things tidy.  Unfortunately I am scared of the Terminal and I don't know how to use it so I'd appreciate advice on how to do this with as little contact with it.

Cheers

---

### Post by Therion on 2008-11-18
> **the lemming said:**
> I'd quite like to put those images into the Wallpaper folder to keep things tidy.  Unfortunately I am scared of the Terminal and I don't know how to use it so I'd appreciate advice on how to do this with as little contact with it.

Cheers
Well you're going to have to pick your poison, then, because it's one or the other.  

Using Wallpaper folder = a tidy outcome but using the Terminal.

Not using the Wallpaper folder = no tidy outcome but you avoid using the Terminal.

Using the Terminal is easy, really.  Just open it up and use Copy and Paste to enter the command I gave you (the sudo nautilus part).  

All that does is open Nautilus (the default file browser in Ubuntu) but with "Super User" privileges; which is the only way you're going to get pics into the folder you want.  I trimmed down the Terminal aspect as much as possible - it's one cut and paste and then using the file browser like you normally would.  The only other route would be to change permissions on the folder you want to use and *that* would require even MORE use of the Terminal.  

Creating an additional folder might be your most comfortable option.  Just make a new folder in your Home directory, call it "Wallpapers" or "Wallpaper Pics" and put all your new-found wallpapers in it.  Easy peasy.  

Or come to the dark side and learn to use the awesome power of... The Terminal!

You know you want to...

---

### Post by the lemming on 2008-11-19
Thanks for the informative reply.  I must have done something wrong at my end because when I cut and Paisted your command I got an error message.

I must have set up my Root account wrong or I've forgotten the password for it, which isn't a good idea.

I'll try again after work.

Cheers

---

### Post by kerry_s on 2008-11-19
> **the lemming said:**
> I'd quite like to put those images into the Wallpaper folder to keep things tidy.  Unfortunately I am scared of the Terminal and I don't know how to use it so I'd appreciate advice on how to do this with as little contact with it.

Cheers

press alt+f2 type> gksudo nautilus /

---

### Post by eternalnewbee on 2008-11-19
You could also create a wallpaper folder in your Home directory. That's what I do.

---

