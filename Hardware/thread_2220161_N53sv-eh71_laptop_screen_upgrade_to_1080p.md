---
title: "N53sv-eh71 laptop screen upgrade to 1080p"
date: 2014-04-26
forum: Hardware
---

### Post by clusterpenguin on 2014-04-26
Hello All,

I have a challenge for you. I am hoping to upgrade my laptop screen to a full 1080p screen. The problem is that my laptop did not come with a 1080p display. I've tried a simple swap and it didn't *quite* work.

The low down:
My laptop is a Asus 53sv-eh7**1**
The 1080 screen I have is for a Asus 53sv-eh7**2**
From all the research I have done, I know that the Nvidia card (540m) will support 1080 content. I know that the laptop specs between the 71 and 72 are almost identical. (The only difference being the screen resolution.) And I am 90% sure that the motherboards are the same for both laptops. (N53sv)

The symptoms/problem analysis: 

NOTE: Link to pics can be found down below.

When I hook up the 1080p display
 1. It displays readable content 
2. Windows recognizes it as a 1080p display
3. the "blacks" are off color. Sometimes when the screen power cycles (via wake form sleep or on boot) the blacks will be a faint green or blue or red.
4. Everything feels "fuzzy." If I had to guess, I would say that the screen is displaying 1366x168 content evenly across a 1080p screen...but without "stretching" the content. It's like looking at a 1080p display through a high density bug screen.
5. All of these strange color problems happen even in the BIOS so it's not directly related to a driver problem.

I have every confidence that we can get this to work. :D

Pics! (The camera didn't capter the problem very well, but hopefully this gives you a small idea.)
[http://imgur.com/a/LR9Wu](http://imgur.com/a/LR9Wu)

---

### Post by clusterpenguin on 2014-04-27
Is this the best place to put this thread? I was hoping to find someone who know a lot about how displays work and was willing to help me out. Maybe someone who works on the Ubuntu display drivers?

---

### Post by daniel142 on 2014-05-01
Just out of curiosity, how much more did the one that came with the 1080p display cost? And was it worth it? :D I have no idea what the problem is, I can't really tell from the pictures. But I'll have to guess there is something wrong with your display, I once fixed a projector were the red/green/blue had gotten out of sync, LCD dosen't work like that but it sounds like it could be some damage. Does your computer have a HDMI port? If you plug it inn to a 1080p TV and use dual screen or switch displays, do you get the same problems then?

---

### Post by clusterpenguin on 2014-05-01
Hey Daniel, 

Thanks for replying.

> **daniel142 said:**
> Just out of curiosity, how much more did the one that came with the 1080p display cost? And was it worth it? :D 
I got the eh71 (non-1080p version) because it was  the only one available at the time and was a good price. :D

> **daniel142 said:**
> I have no idea what the problem is, I can't really tell from the pictures. But I'll have to guess there is something wrong with your display, I once fixed a projector were the red/green/blue had gotten out of sync, LCD dosen't work like that but it sounds like it could be some damage. Does your computer have a HDMI port? If you plug it inn to a 1080p TV and use dual screen or switch displays, do you get the same problems then?
  
The native  display looks fine with the origninal 1366x168 display, it's only when I  switch it out for the 1080p display that all the color and pixle  problems occur. I  plugged in my laptop to our 1080p TV via HDMI and everything works  without a problem. So it can handle 1080p and it can display it  properly, as long as it's displaying and external source. What I need  to do now is find a way to get it working on the native laptop screen. 

maybe there is a manufacturing setting/switch that needs to be toggled...

---

### Post by MartyBuntu on 2014-05-05
You cannot "upgrade" to 1080p.

The screen resolution is graphics card driven. There is no software "enhancement" to increase a hardware limitation like the one you seek.

---

### Post by QIII on 2014-05-05
> Ok, How about a **$25 amazon gift card **to the person who helps me get a working solution. 

How about "No, not on this Forum, and don't make an offer like that again."

---

### Post by clusterpenguin on 2014-05-06
> **MartyBuntu said:**
> You cannot "upgrade" to 1080p.

The screen resolution is graphics card driven. There is no software "enhancement" to increase a hardware limitation like the one you seek.

Ok, but I know that the graphics card can drive a 1080p screen. I have connected the HDMI output to a 1080p screen and it works, and the other vitiation of my laptop N53sv-eh7**2** has the same GPU, so I thought the difference might be some low level code that is pre-bios or some chip set change that connects the display to the graphics card...

---

### Post by clusterpenguin on 2014-05-06
> **QIII said:**
> How about "No, not on this Forum, and don't make an offer like that again."

Hey man, sorry. I didn't know this was against the rules. No prob, won't do it again. Thanks for the warning.

---

### Post by clusterpenguin on 2014-05-06
If the N53sv-eh7**1** and N53sv-eh7**2** have the same specs except for the difference of the 1080p screen, what components/BIOS code would change between the two laptops?

---

### Post by Cluster Penguin on 2014-05-12
Just has a though. Could it be that the display they sent me was a bad one?

---

### Post by p__wack on 2014-08-20
Hey Cluster Penguin, I did the same (similar laptop and another screen vendor) and got the same results, how did you finally resolve it?

PS: the problem is OS independent by the way

---

### Post by Manuel110 on 2014-09-14
> **p__wack said:**
> Hey Cluster Penguin, I did the same (similar laptop and another screen vendor) and got the same results, how did you finally resolve it?

PS: the problem is OS independent by the way

Hi, I have read somewhere that you should also replace the cable that connects the screen to the mobo with Another one that supports full hd. It is called lcd lvds cable. Here is an example [http://www.asusparts.eu/en/Asus-14G22101600V](http://www.asusparts.eu/en/Asus-14G22101600V)
And of you search into the website you will see that there are two different cables for hd or full hd.
Please let me know if it works because i would also like to upgrade my n53 screen.

---

