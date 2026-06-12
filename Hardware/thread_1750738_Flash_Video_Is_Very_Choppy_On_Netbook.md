---
title: "Flash Video Is Very Choppy On Netbook"
date: 2011-05-05
forum: Hardware
---

### Post by WhiteNoiseParser on 2011-05-05
Ok, I am running an HP Mini 210. It has a Intel Atom 1.6ghz processor, 1 gb of ram. 

I try to view Hulu at full screen and even 280p the video is noticeably choppy. It does the same on YouTube. 

I am now on Xubuntu 11.04 thinking that would fix the problem but it hasn't. I have looked under restricted drivers and didn't see one for my graphics driver. Intel(R) Graphics Media Accelerator 3150 is my graphics driver. I do understand that it is a low powered graphics card but I didn't have this problem on XP. I have been thinking about putting an extra gig of ram in, but I don't know if that will do any good.

I am just wondering if anyone else has had the same problem with their netbook and what they did to make their graphics card to run more smoothly?

---

### Post by randallecook on 2011-05-10
I am also getting choppy Flash video on an ASUS Eee 1215T netbook running Ubuntu 11.04 Natty Narwhal. I installed the proprietary drivers (I think), but the frame rate is annoyingly slow. Poor flash performance has always been a problem with Linux. Can anything be done? I have heard of Flash-Aid and FlashVideoReplacer. How well do these work?

---

### Post by mudyf0x on 2011-05-10
go into packet manager nd search for flash and download adobe flash i have it on lubuntu 11.04 and on my AAO 1gb and its smooth on youtube etc

---

### Post by NahsiN on 2011-05-24
@Whitenoisepaper I had the same problem with my Acer Aspire one netbook Model AOA D260. Did a clean install of 11.04 and the flash was very choppy just like you said. Disabling Hardware acceleration in flash helped a little bit. But what solved the problem for me was flash aid addon for firefox. It did something and now my flash is working much better. Seeking can be a bit slow in fullscreen sometimes but the video is smooth. Try installing flash aid addon for firefox and see if it works for you.

@randlecook flash aid works to solve this annoying problem!

They have really screwed up this time with Ubuntu 11.04. Everything is just broken!

---

### Post by angryfirelord on 2011-05-24
Try viewing it in the Chromium browser. It may be a flash problem dealing with Firefox. Keep in mind that Flash is a proprietary application and as such, bug fixing is only limited to what Adobe wants to do.

Also, you may want to install and use unity-2d (you'll have to select it in the login manager). This will relieve some of the CPU/GPU strain that may be causing flash and other apps to run slow. I found this worked much better on my netbook.

---

### Post by mp3droid on 2011-10-05
@angryfirelord - thank you!! great advice. I'm on an acer inspire one D150 and it made a HUGE difference for me going to unity 2d. I was in the process of looking for another linux distro before I came acorss this post. Thanks!!

---

