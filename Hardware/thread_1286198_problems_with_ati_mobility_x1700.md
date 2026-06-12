---
title: "problems with ati mobility x1700"
date: 2009-10-08
forum: Hardware
---

### Post by razzix on 2009-10-08
Hello all. I am having some driver issues with my laptop(asus g2p with ati mobility x1700). I am a bit of a newbie to linux but this is not my first install. About a year ago I was running hearty heron on this same laptop but had to go back to windows for work purposes. Back then I was using WINE to get my gaming fix. I was able to play world of warcraft, half life 2, doom 3, and several others(most of them are on the platnum list for compatibility with WINE). Now that my job no longer requires the laptop etc, I am free to finally go back to ubuntu. 
  After installing hearty and upgrading my way to jaunty about 2 weeks ago I am running into some major issues. I first noticed it when I was playing around with compiz's cube desktop. all the outside edges were jagged as opposed to the last install almost a year ago where everything was smooth and pretty. also video codecs look like trash for no reason. no big deal tho right? I can deal with it, so i just kept truckin along until it came time to get a little gamer fix. using both stable and beta versions of WINE I am unable run any of the supported platnum games that work right out of the box. the unifying errors recieved seem to be along the same lines. "unable to initilize 3d acceleration" -- "No compatible 3d hardware" -- etc. 
  The only thing that I can think of after trying both stable and beta versions of WINE (with days worth of tweaking) and multiple games all on the platnum list, is a driver issue of some kind. If I were in teh windohs I would just go to device manager and begin troubleshooting, but alas I do not know what the Ubuntu equivalent is (or if there even is one). With my limited linux experience I have so far tried to adding various ATI drivers from the add/remove software interface. I remembered that jockey used to manage my proprietary driver in hearty so I went there. No dice. It now recognizes my modem which is an improvement over a year ago but thats not my problem. Jockey isnt showing my x1700. Tried removing and re-adding jockey to no avail. 
  Am I stuck going back to windohs just to get my 3D acceleration back? I was previously able to run all the games I have been testing on hearty so I am hoping not. I came here as a last resort after a fair bit of lurking over the past week and a half. Google and Search are my friends :P but have turned up nothing but 3yr old articles that are of little to no help. Is this a common problem? Does anyone have a solution? Or a direction for me to travel in?
 
 
Thank you in advance for any help you are able to give :)

---

### Post by Yellow Pasque on 2009-10-08
The newer Catalyst drivers (Catalyst 9-4 or later, the only ones you can use with Jaunty without downgrading the Xserver) do not support older ATI cards.

Even with the opensource drivers, you should still be able to do 3D games unless they require OpenGL 2 or later (which WINE may). Anyway.. if you had proprietary drivers installed before, make sure you follow this guide to purge them completely: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by razzix on 2009-10-08
> **Temüjin said:**
> The newer Catalyst drivers (Catalyst 9-4 or later, the only ones you can use with Jaunty without downgrading the Xserver) do not support older ATI cards.
 
Even with the opensource drivers, you should still be able to do 3D games unless they require OpenGL 2 or later (which WINE may). Anyway.. if you had proprietary drivers installed before, make sure you follow this guide to purge them completely: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
 
 
 
So is this a recomendation to take it back to 8.04? If thats the case, I can live with that. Is there anything I will be needing to do to enable OpenGL(2.0+) or will it just come with the appropriate driver? Any guides or pointers in the direction of where I need to head for best performance with the mobility x1700 or are drivers just drivers in this aspect?

---

