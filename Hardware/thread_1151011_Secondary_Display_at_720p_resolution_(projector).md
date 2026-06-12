---
title: "Secondary Display at 720p resolution (projector)"
date: 2009-05-06
forum: Hardware
---

### Post by Entilzha on 2009-05-06
Hi guys,

I'm trying to get Ubuntu to recognize my projector at it's native resolution. I'm using Jaunty at an IBM T60 laptop (ATI video), in combination with a Mitsubishi HC1500 projector which is 720p. I use a regular VGA cable for the connection.

When I go to System-->Preferences-->Display, it actually recognizes the extra monitor as Monitor: Mitsubishi. The regular one for my laptop is also there and is called Monitor: Laptop 15". The weird thing is that I can set the laptop monitor to 720p resolution, but NOT the projector. Also, if I set 'Mirror screens', the option disappears completely. Now my question is how do I get Ubuntu to do 720p over my projector?

I found a modeline with the MythTV guys: 
## Doesn't claim to support native (1280x720) over VGA, but it does just fine
# ModeLine "720p" 74.25 1280 1392 1448 1650 720 722 728 750

However, I dont know where to put this so it works. I tried some places in xorg.conf that made sense to me, but so far no show. Any advice?

---

### Post by Entilzha on 2009-05-08
Is there a better place to ask this question?

---

### Post by DJYoshaBYD on 2009-05-08
not really.. it just takes forever to get an answer here sometimes..

do you have the newest ATI driver installed and functional? If you do, then you should use the ati config tool to do it.. not the gnome display manager..

I do it with my laptop all the time.. it works well...

i have noticed ALOT of bugs in jaunty, as opposed to 8.04.1 and 8.10.. even now, on a desktop, i use 8.04.1 and thats it, as it works on everything i have installed it on... maybe try using 8.10..

WHOA.. actually, thats your problem.. haha.. They dont have an ATI driver for Jaunty yet... at least I dont think so.. if you do not have the correct proprietary ati driver, half of the shi+ never works.. lol.. Nvidia usually works well with the open source driver, but nothing beats the proprietary driver..

so yeah.. look up to see if they have it for jaunty yet, which im pretty sure they do not.. if they dont, then you will need to downgrade to either 8.10 or 8.04.. i suggest hardy (8.04), as it has given me the most success with everything from wireless, to NTFS, to media, etc etc etc

---

### Post by Entilzha on 2009-05-08
Yeah you are right. Actually it warned me the fglrx wouldnt work anymore after upgrading. However I figured this would just hit the hardware 3D acceleration which I don't use anyway.

All the basics seem to work ok, just the available resolution on the extra monitor is messed up.

---

### Post by DJYoshaBYD on 2009-05-08
yeah.. screw jaunty for now.. just revert back to 8.10 at least.. you can always make your system look dope with themes, backrounds, etc... plus, all your stuff will work without faill.. I was going to upgrade my laptop to jaunty, and, after reading, and trying it on a test system, i just recommend against it.. strongly.. lol

---

