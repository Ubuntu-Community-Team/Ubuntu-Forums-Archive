---
title: "Certain keys not working on Dell inspiron 1501"
date: 2012-05-25
forum: Hardware
---

### Post by nullz on 2012-05-25
I recently uninstalled windows (half an hour ago) and installed the lastest version of Ubuntu. I didn't see any laptop versions so I figured the desktop version is what I wanted..

My keys worked fine in windows (I was backing everything up and browsing web before uninstall.) When it asked for me to name my pc + my name+ password I couldn't use the "asdfjkl;" keys. G and H worked fine and all other keyboard keys work. The letters aren't showing up as if I had numlock on either and it is off.

I am wondering if it could be scroll lock? I cannot seem to use my Fn key or my windows key (didn't expect to) to try and turn Fn off. Holding in and pressing the num/scroll lock button only activates/deactivates num lock.

This is my first experience with linux/unbuntu and it seems to be a rocky start. Any help will be greatly appreciated!


I am using a dell inspiron 1501 and installed ubuntu 12.04 x64 desktop version.

---

### Post by ahallubuntu on 2012-05-25
I know it sounds like coincidence, but it sounds like your keyboard has failed.  I have had laptop keyboards do things like you describe; replace the keyboard and the problem is fixed.

Any chance you have your old Windows disc?  You boot it and just drop into a recovery console or command prompt and see if you can type on those keys (this won't install anything; when you shut down your hard drive will still have Ubuntu).  

If you can still type when booting Windows, then the keyboard is clearly OK.  If not, replace the keyboard.

FYI, I've put Ubuntu on a number of Dell laptops with few or no issues, certainly not one like yours.  I had had Ubuntu on my Inspiron 1545 for years.  (I did have a keyboard fail a few months ago; after replacing it, keys have been perfect).  I have not used the latest 12.04 LTS version much but I did boot it on my 1545 and all the keys worked fine.

---

### Post by ahallubuntu on 2012-05-25
FYI, you would be slightly better off with the 32 bit version of Ubuntu on this laptop.  The main advantages of a 64 bit OS are addressing more than 4GB of RAM and having large processes - and your 1501 maxes out at 2GB of RAM.  So there is really no benefit to a 64 bit OS and possibly some detriment in your case.

I am not saying the 32 bit version should fix your key issue, just an aside.

---

### Post by Enigmapond on 2012-05-25
Agreed. I have currently 3 Inspirons running 12.04 and have never had a keyboard issue since 8.04. Dell is pretty hardy with Ubuntu...I would have the keyboard checked...sounds like a hardware issue.

---

### Post by nullz on 2012-05-25
> **ahallubuntu said:**
> I know it sounds like coincidence, but it sounds like your keyboard has failed.  I have had laptop keyboards do things like you describe; replace the keyboard and the problem is fixed.

Any chance you have your old Windows disc?  You boot it and just drop into a recovery console or command prompt and see if you can type on those keys (this won't install anything; when you shut down your hard drive will still have Ubuntu).  

If you can still type when booting Windows, then the keyboard is clearly OK.  If not, replace the keyboard.

FYI, I've put Ubuntu on a number of Dell laptops with few or no issues, certainly not one like yours.  I had had Ubuntu on my Inspiron 1545 for years.  (I did have a keyboard fail a few months ago; after replacing it, keys have been perfect).  I have not used the latest 12.04 LTS version much but I did boot it on my 1545 and all the keys worked fine.


SOB, lol. I guess my keyboard took a crap between me turning the laptop off and me sticking the ubuntu cd in D: It is just a simple remove keyboard, stick new one in? I'll look into replacing it, for now I will just use my wireless usb mouse/keyboard, for my laptop, lol. Thank you, hardware would have been my last suspect considering I was just using it.

---

### Post by Enigmapond on 2012-05-25
They are pretty easy to replace. You can do it yourself if not under warranty. There are instructions all over the web. The keyboard is only a $20-$35 item.

---

### Post by ahallubuntu on 2012-05-25
Please verify if you haven't already that your keyboard has in fact failed by booting a Windows CD as I suggested.  Don't replace the keyboard until you've verified that it's really bad.

It may seem intimidating to replace your laptop keyboard, but I have done a few of them.  After turning off the power and removing the battery, open the screen as wide as it will go, then pry off the top bezel that the power button is under with a small flat screwdriver.  (I have an old E1505 that is very similar to your 1501 and have opened it up a few times.)  Then you'll see the 2 or 3 screws at the top that hold the keyboard in.  Remove those, then you have it free but still have to remove the ribbon cable which varies by the model.  You may have to lift up a little latch to release the ribbon cable or slip the cable in another way.  It varies.

FYI, Dell almost certainly has a service manual on their website for the 1501 - it should describe exactly how to replace the keyboard.

---

### Post by ahallubuntu on 2012-05-25
I usually buy new laptop keyboards on eBay for about $15.  The important thing is to verify that it's EXACTLY the right keyboard.

---

### Post by RISHIKESHGAWADE on 2012-06-04
I have the same model and same version of Ubuntu. I am facing problem with only 'V' key. I have to press it really hard to function. it works perfectly fine on windows partition of the same machine. Thu it is not the hardware issue...
One more interesting thing is that when i switch to devnagari keyboard, the same key doesn't work at all or even if it works, shows english letter V, and rest of the letters in devanagari

---

