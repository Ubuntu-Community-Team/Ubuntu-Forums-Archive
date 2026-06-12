---
title: "anyone use wireless mouse?"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by woedend on 2005-07-26
not really ubuntu specific, but ive always used a wired optical mouse and loved it.  yesterday i bought  a kensington wireless optical mouse.  It's horrible to me...the movement is very choppy, i keep passing things up.  its not terrible, and most people wouldn't notice in general, but coming from a perfectly smooth one to this is a little annoying. are most wireless mouses like that?  my wired one was silky smooth...then again it was a logitech.

---

### Post by heimo on 2005-07-26
I'm using the cheapest Logitech cordless desktop I could find and I love it. Everything works except one multimedia key (Calculator, it doesn't give any keycode). Mouse is fine, but I haven't got used to those expensive models. Not jerky, not silky smooth - fine for everyday use.

Try moving the receiver (if you already haven't tried this). I doubt it would be any irq-problem, unlikely. But it never hurts to check /var/log/messages for any errors.

---

### Post by woedend on 2005-07-26
thank you for your reply...let me clarify.  my first one wasn't expensive...the standard red logitech that was around for years that I can't seem to find anymore.  Any standard ps2 mouse has a pretty standard/smooth movement.  With this new mouse...i barely move my mouse and it kinda skips instead of having moving smoothly...as in its not as responsive.  I was just wondering if all wireless mice were like this or if i got a crappy model.

---

### Post by heimo on 2005-07-26
If you can, try it on another computer. It sounds like it could be just crappy or broken, or you may have wrong mouse protocol and or other settings for it. You should probably check what you have in /etc/X11/xorg.conf on section InputDevice (Driver "mouse") on the line with Protocol - I have a section like this:
 ```
Section "InputDevice"
		Identifier	  "Configured Mouse"
		Driver		  "mouse"
		Option		  "CorePointer"
	    Option		  "Device"			    "/dev/input/mice"
	    Option		  "Protocol"			  "ImPS/2"
	    Option		  "ZAxisMapping"		  "4 5"
EndSection

``` 

Mine is PS/2, but I think some USB mice emulate PS/2. You could try values like auto, Microsoft, Logitech, USB - or other valid values.

Check this thread for some advice:
[http://ubuntuforums.org/showthread.php?t=22203](http://ubuntuforums.org/showthread.php?t=22203)

---

### Post by Curlydave on 2005-07-26
You'll find that most cheaper wireless mice have issues such as lag, choppiness, etc.

That being said, I'm currently using a (wireless) Logitech MX1000, (omg laser!!!!) and it's the best mouse I've used.

---

### Post by woedend on 2005-07-26
thanks for the great replies guys.  I realized that my brother had a top of the line microsoft optical wireless and it still had some chop to it also.  So, I went to get the aforementioned 1000 logitech...looked and felt great...on sale for 49 dollars but...sold out.  out of curiosity...does the lazy wireless mouse have that same delay after it's been 'sleeping' that takes it a few seconds to wake up?  I settled for the mx516 i think it was, a wired optical mouse from logitech..same price and I love it...now to program these buttons!  thanks again guys for the support.

---

### Post by Curlydave on 2005-07-26
[QUOTE=woedend]thanks for the great replies guys.  I realized that my brother had a top of the line microsoft optical wireless and it still had some chop to it also.  So, I went to get the aforementioned 1000 logitech...looked and felt great...on sale for 49 dollars but...sold out.  out of curiosity...does the lazy wireless mouse have that same delay after it's been 'sleeping' that takes it a few seconds to wake up?  I settled for the mx516 i think it was, a wired optical mouse from logitech..same price and I love it...now to program these buttons!  thanks again guys for the support.[/QUOTE]

Nope, no delay that I know of. The microsoft wireless mice, like you mentioned do have a reputation for mouse lag. It's too bad they didn't have the MX1000 in stock, but the MX518 is also an excellent mouse.

---

### Post by mrguytx on 2005-07-27
[QUOTE=woedend]thanks for the great replies guys.  I realized that my brother had a top of the line microsoft optical wireless and it still had some chop to it also.  So, I went to get the aforementioned 1000 logitech...looked and felt great...on sale for 49 dollars but...sold out.  out of curiosity...does the lazy wireless mouse have that same delay after it's been 'sleeping' that takes it a few seconds to wake up?  I settled for the mx516 i think it was, a wired optical mouse from logitech..same price and I love it...now to program these buttons!  thanks again guys for the support.[/QUOTE]

I have a wireless mouse and it works great, but yeah, it does "go to sleep" like you mentioned and I have to move it a few times to wake it up, or scroll wheel it once.

The only time I had problem with jerky motion was when I bought a new desk and neeeded to readjust the receiver on the back of the pc to a different angle.

---

### Post by djheadley on 2005-07-28
I am using a Logitech wireless mouse and I haven't had any problems with any Linux distro I've tried.  I haven't noticed it "going to sleep" but I've gotten in to the habit of shaking the mouse when I come back and the screen saver is on.

DJ

---

### Post by NorthCoast on 2006-11-11
I tried the Targus wireless rechargable mouse and hate it.  I have to resync it at every boot and it suddenly goes away and I have to resync it again.

My old Logitech wireless mouse works a treat.  The USB cabled receiver isn't as portable as I like so I tried the Targus with the little USB dongle but like I said it isn't working very well.

---

