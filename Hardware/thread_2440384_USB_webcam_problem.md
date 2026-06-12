---
title: "USB webcam problem"
date: 2020-04-09
forum: Hardware
---

### Post by Timothy Taylor on 2020-04-09
I am trying to get a Trust "Chat & VOIP" USB webcam working on my Fujitsu Lifebook P701 laptop, which is running MATE 18.04.

The webcam is recognised:

> ls /dev/video*
/dev/video0

lsusb lists it as:

> Bus 005 Device 003: ID 093a:2600 Pixart Imaging, Inc. Typhoon Easycam USB 330K (newer)/Typhoon Easycam USB 2.0 VGA 1.3M/Sansun SN-508


Cheese says "no device found".
Skype seems to find something, but can't get any video from it.

Any ideas?

---

### Post by mörgæs on 2020-04-10
Does guvcview recognise the camera?

---

### Post by Timothy Taylor on 2020-04-10
> **mörgæs said:**
> Does guvcview recognise the camera?

I've just installed guvcview and yes, it does.  
Video is very slow and steppy though. 

Still no joy with Cheese or Skype. 
Skype lists the webcam as "USB Camera (093a:2600)" but still no video.

---

### Post by mörgæs on 2020-04-11
Is Guvcview better if you close it and open it again?

---

### Post by Timothy Taylor on 2020-04-11
It seems to be about the same.

Can you tell me how to get  this camera working with Skype?

---

### Post by mörgæs on 2020-04-11
I don't use Skype so I can't give a precise answer, sorry. 
Just trying to diagnose if it's a hard- or software error.

---

### Post by Timothy Taylor on 2020-04-11
I have discovered something interesting.

I tried the webcam with my desktop system which is also running MATE 18.04 and get the same results.
I then tried it with my old laptop, which still runs MATE 16.04 and the webcam works fine!

It seems that there is some issue with video in 18.04 ?

---

### Post by mörgæs on 2020-04-12
Good find. 
How does a live boot of [20.04]("http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/") work on the same computers?

---

### Post by Timothy Taylor on 2020-04-12
> **mörgæs said:**
> How does a live boot of [20.04]("http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/") work on the same computers?

Exactly the same.

---

### Post by mörgæs on 2020-04-12
More information would make it easier for people to provide an answer.

What is the same? Are you saying that Skype, Cheese and Guvcview work in 16.04 and 20.04 on the old computer but not on the two other?

Please provide data for all combination of (hardware, OS, application).

---

### Post by Timothy Taylor on 2020-04-13
> **mörgæs said:**
> More information would make it easier for people to provide an answer.

What is the same? Are you saying that Skype, Cheese and Guvcview work in 16.04 and 20.04 on the old computer but not on the two other?

Please provide data for all combination of (hardware, OS, application).

Sorry, I meant that 20.04 behaves exactly like 18.04 = no Skype or Cheese video on either the P701 or desktop.  I didn't try Guvcview with 20.04.

I was setting up the P701 for my partner to connect with her daughter on Skype during the lockdown.
It is clear that neither 18.04 nor 20.04 would allow this webcam to work with Skype, so I installed MATE 16.04 over 18.04 and have Skype video working fine.

I initially tried my old "iBall" webcam but bought the "Trust" Easycam because I thought the iBall was broken.
Now I find that both actually work fine.  I am at a loss to understand how something that worked perfectly up to 16.04 became broken in 18.04 - and even remains so in 20.04.  Very disappointing.
:-(

Thanks for your time and advice.

---

### Post by mörgæs on 2020-04-14
Mate 16.04 is unsupported so you should be aware of the risk. Try to run ```
ubuntu-support-status
``` and see for yourself.

I don't have any good explanation for why the camera has stopped working in the later releases. When development of 20.10 begins it would be great if you could discuss the problem in the development forum and possibly create a bug report. It's too late for 20.04.

---

