---
title: "This morning update has slowed my computer down horrendously."
date: 2008-07-29
forum: General Help
---

### Post by portach king on 2008-07-29
Hi guys,
So I updated this morning while browsing only to find this evening when I arrived home that the performance of my laptop has suffered greatly. Have other people also reported this. I cant even watch youtube without it stuttering all over the place.

---

### Post by Diabolis on 2008-07-29
Maybe something is using intensively your cpu. Type this to see which process are using more your cpu:
```
top
```

Type **q** to exit.

---

### Post by portach king on 2008-07-29
xorg is using 50+%

Addition: It seems to spike the most when I start to download anything, but also at other random events

---

### Post by Diabolis on 2008-07-29
Probably the update messed with your graphics card configuration and is not doing its job, so the cpu is making all the rendering.

So a good start would be to start troubleshooting that.

This bug might be related to your problem:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/178400](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/178400)

---

### Post by portach king on 2008-07-29
Thanks for your help Diabolis. My card is an ATI card though, so how would I go about "troubleshooting"?

---

### Post by Diabolis on 2008-07-29
See if your card appears in the bug reports, to see if its already reported.

Check that its correctly installed with the right drivers.

Check if you have direct rendering.
```
glxinfo | grep rendering
```

Check your **fps**.
```
glxgears -info
```

---

### Post by Diabolis on 2008-07-29
Apparently my guess was correct, someone already had this problem with a ATI card.

[http://ubuntuforums.org/showthread.php?t=847186&highlight=xorg+high+cpu+usage](http://ubuntuforums.org/showthread.php?t=847186&highlight=xorg+high+cpu+usage)

---

### Post by portach king on 2008-07-29
I'm quite sure the correct drivers are installed. It was absolutely fine up to this morning.
Direct rendering is running, and my fps is averaging at about 1040fps

---

### Post by portach king on 2008-07-29
I'm afraid that didn't help. It seems to be an issue directly related with downloading. Youtube plays fine when the whole video is loaded but stutters while downloading. :(

---

### Post by portach king on 2008-07-29
I've just realized that I'm having the same problem I had two months ago with Ubuntu in which the only solution was to reinstal 8.04 from scratch! Thanks for your help Diabolis. 
I have to be honest though, I am furious. This is the third time I've had to reinstall Hardy! And it's the third time because of the same issue, some update screwed up my wireless. I'm truly getting sick of this. I'm using a Linux friendly Edimax Usb dongle, I bought it so that it would provide easy wireless with Ubuntu, however it's been anything but! I'm not sure what to do. Obviously I now have to sit through another install followed by a large system update. It's totally ridiculous!

---

### Post by Diabolis on 2008-07-29
> **portach king said:**
> I'm afraid that didn't help. It seems to be an issue directly related with downloading. Youtube plays fine when the whole video is loaded but stutters while downloading. :(

Well if you have time, keep on tracking the issue. Go to other websites to see of they are slow too. If its just Youtube, maybe its a problem with your web browser and/or its plug-ins.

However, I still think its a video card problem.

> I've just realized that I'm having the same problem I had two months ago with Ubuntu in which the only solution was to reinstal 8.04 from scratch! Thanks for your help Diabolis.
I have to be honest though, I am furious. This is the third time I've had to reinstall Hardy! And it's the third time because of the same issue, some update screwed up my wireless. I'm truly getting sick of this. I'm using a Linux friendly Edimax Usb dongle, I bought it so that it would provide easy wireless with Ubuntu, however it's been anything but! I'm not sure what to do. Obviously I now have to sit through another install followed by a large system update. It's totally ridiculous!

I used to do the same thing, went through several reinstalls. But that helped, I got to know more about my own pc. Kind of knowing what it likes and what not. So now I know how to get it up and running after almost any problem I find with it and linux.

---

### Post by Cloggy on 2008-08-29
Is there any way to uninstall the updates?
Having a similar issue. All new to Ubuntu and Linux. Installed 8.04 last night and worked a charm on my NEC laptop. Very impressed with it. Then I installed the updates which were available according to the little icon in the top information bar. There were 106 updates available. Impressed with the download speed and installation times. However after installing the updates I have lost my wireless internet connection and everything has slowed down to a crawl. How can I uninstall these updates? The plan is to then reinstall them one at a time to see which one (or ones) is the culprit.
Thanks guys and gals for any help you may be able to provide to a complete Linux novice. So please try and explain in simplest terms possible.

---

### Post by Cloggy on 2008-08-31
Happy to say my issues appear to be fixed. Reinstalled the system but did not install the updates. All was fine, until I went to a webpage which needed Java installed. As soon as I did this the whole system slowed down, lost my wireless connection and goodness knows what else. Reinstalled the system from scratch again, did some more research and found I could install all these third party apps like Java, Flash etc. from the Ubuntu site. Did this from the terminal using the instruction on the site and no more problems since. All works as it should. Very happy with my new Ubuntu install.

---

