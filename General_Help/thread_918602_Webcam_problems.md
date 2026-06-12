---
title: "Webcam problems"
date: 2008-09-13
forum: General Help
---

### Post by xsilvergs on 2008-09-13
Hi, I'm still quite new to Ubuntu but trying hard.

I'm using Intrepid (8.10) and having problems with my Philips SPC300NC webcam.

lsusb shows
Bus 001 Device 002: ID 0471:0326 Philips SPC 300NC PC Camera

Skype  shows SPC 300NC (/dev/video2)

If I do Test in Skype the light on the webcam comes on and the video runs in Skype but the picture is green, noisy and scrolling.

If I try Cheese I get a colour bar test card and the light on the webcam does not come on.

Can anybody help please as this is the only bit that doesn't work.

Thank you.

---

### Post by xsilvergs on 2008-09-13
For added info:

Just tried a Trust Sacec@m 380 which by all reports don't work. It didn't.

Also tried another camera and from lsusb I get

Bus 001 Device 003: ID 0c45:60c0 Microdia PC Camera with Mic (SN9C105).

I get the same results as the Philips SPC300NC, a "screen of noise" with Skype and a screen of colour bars with Cheese.

Camorama starts with a "Unable to capture image".

Any help would be appreciated.

---

### Post by swisscow on 2008-09-13
Have you tried with Hardy, as Intrepid is still in the early stages?

also have a look (and if I can find the link I'll post it) for a list of supported cameras - there is usually some helpful information there.

A search for Ubuntu supported webcams may find it

---

### Post by cariboo on 2008-09-13
You can get a driver for your webcam here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

But it doesn't build with the latest kernel. It will build properly with 2.6.24.19

Jim

---

### Post by xsilvergs on 2008-09-13
@ swisscow. I started with Hardy which worked ok (didn't try webcams with it) but upgraded to Intrepid not realizing what I was doing. I'm a beginner you see.

@ cariboo907. I wish I'd stayed with Hardy.

Is it easy to go backwards or should I just wait for Intrepid to catch up?

The webcam thing is not a big deal, I thought it would be nice to have it when talking to my elderly farther with Skype, but I'm not too worried if the camera doesn't work.

Thanks for any info.

Can anybody recommend a webcam that works with Intrepid?

---

### Post by swisscow on 2008-09-14
Just out of interest, how are you finding Intrepid?

As for a webcam, I bought a Logitech Quickcam E3500 Plus and it worked out of the box, except with skype but thats because I am using the 64 bit

---

### Post by xsilvergs on 2008-09-14
swisscow

Intrepid seems ok, the network setup is a little different, but once I worked out how to make the settings and set the default network that worked ok.

I've had a few error messages at startup, one to do with the Trash bin I think and another for something else. For both of these I've let it send an error message.

A few icons are different and I'm sure they've changed with each update, and there's been a few! Just like Windozs dare I say.

As this is really my first serious attempt to get away from Windows perhaps this is the norm? I only had Hardy for a week so can't really compare.

---

### Post by swisscow on 2008-09-14
Hey thanks.

The different versions seem to change slowly, but steadily - for the better IMHO. I'm looking forward to Intrepid but I'll hang on until the release I think.

As for breakages, well Intrepid is pre-release so expect some problems. As for Ubuntu in general, you can split the problems you have into those ones caused by user lack of knowledge and those with the software at fault.

Both of these are fixable - the first with experience and the second the clever people fixing them.

Stick with it, and don't expect it to act like Windows. It is actually a lot less hassle and a lot more solid once you get used to it.

---

### Post by jespdj on 2008-09-14
If you're new to Ubuntu then it's probably best to use Hardy (8.04) for now. Intrepid Ibex (version 8.10) is going to be officially released at the end of October (that's why it's called 8.10: 8 = 2008, 10 = October).

You should really be using Intrepid at the moment only if you want to help develop and test the new version of Ubuntu. You can expect a lot of things to not work properly at the moment with Intrepid, because it's not finished.

There's no easy way to downgrade from Intrepid to Hardy - you'll have to reinstall Hardy.

---

### Post by xsilvergs on 2008-09-14
Jespdj, thanks for info. it's not long till the end of October so I'll stick with Intrepid as the camera thing is not a real problem to me and the other things I require work ok.

Thanks.

---

