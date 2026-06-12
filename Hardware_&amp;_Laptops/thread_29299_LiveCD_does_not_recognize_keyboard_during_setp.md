---
title: "LiveCD does not recognize keyboard during setp"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2005-04-23
I was able to boot live vga=771 (or whatever the suggested numbr is) and it worked fine, but once I got to the window to select my language, I was not able to use the keyboard to select a language.

Any ideas?

I'm using a [HP Pavilion zv6005US](http://www.circuitcity.com/ccd/productDetail.do?oid=120278&com.broadvision.session.new=Yes&com.broadvision.session.new=Yes&BV_UseBVCookie=No&ct=0&BV_SessionID=@@@@0827353802.1114297791@@@@&BV_EngineID=ccccaddehejekfkcfngcfkmdffhdffo.0)

I'm using the AMD64 Live CD.

---

### Post by NickB on 2005-04-24
I'm in the same boat.  Let me know if you get it working!

Nick

---

### Post by OneSeventeen on 2005-04-25
Still trying.  HP says all my hardware is ready for a 64 bit OS, so I don't see it being a driver issue.

I'm thinking we need to find a proper boot command to enable the keyboard.

---

### Post by NickB on 2005-04-25
I have been using this line:

live noapic nolapic vga=791

The keyboard doesn't appear to die until d-i starts up; if there was a way to specify everything you needed without accessing the debian installer, I suspect it might work.

Nick

---

### Post by OneSeventeen on 2005-04-27
[QUOTE=NickB]I have been using this line:

live noapic nolapic vga=791

The keyboard doesn't appear to die until d-i starts up; if there was a way to specify everything you needed without accessing the debian installer, I suspect it might work.

Nick[/QUOTE]
 I've been using a similar line myself, and it definitely looks to be an issue once the debian installer starts.

I might check a few debian boards as well, because I'd really like to put ubuntu on this system.  I like the ideaology behind ubuntu, and if it works well, I could see offering it to clients as an alternative for small businesses.

Definitely let me know if you find the solution!

**EDIT:**
I read somewhere that typing on the keyboard during startup and system device probing can help.  It didn't work for me, but I just thought it might for you, so who knows?

---

### Post by NickB on 2005-04-28
This is interesting... my keystrokes queued up during boot, and then got translated into the debian installer, but once the buffer was emptied, I couldn't type anymore.  I tried just pressing return over and over, but it didn't advance the installer screens any.

Nick

---

### Post by NickB on 2005-04-28
OK, I got it to boot all the way to X, less mouse support (which was expected; need to compile a driver for the touch pad).  I did it by using "6" as the return key.  Why?  I don't know.  I randomly pressed keys until I got something.

The problem is still the keyboard, even beyond that.  atkbd complains that it doesn't understand the keys I'm pressing, so there must be something that can be passed at boot time for the module to recognize the keyboard.  Or at least there should be. 

Hope that gives you someplace to work from.

Nick

---

### Post by NickB on 2005-04-29
I got it working, with only vga=791 as the boot option.  Just mash the keyboard until it starts working.  A lot.  Get a bunch of keys with your hand.

Hopefully this is fixed in a later kernel.

Nick

---

### Post by NickB on 2005-05-04
After much experimenting, you can reset the atkbd driver by pressing the fn+left shift keys together.  Keyboard works after that.

Nick

---

### Post by OneSeventeen on 2005-05-04
[QUOTE=NickB]After much experimenting, you can reset the atkbd driver by pressing the fn+left shift keys together.  Keyboard works after that.

Nick[/QUOTE]
Wo0t!

Still got a ways to go to get it running nice and smoothly, but man, that fn+left shift thing did the trick!

Now the question is, how many combinations did you try until you figured that one out?!

**Edit:**
Oddly enough the touchpad worked great while it was first starting up, now I've just got the "Ubuntu: linux for human beings" splash on my screen, as though it should start popping up icons as it loads stuff...  

So this took me one giant leap forward, but still no desktop :(

---

