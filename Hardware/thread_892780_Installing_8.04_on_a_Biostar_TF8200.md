---
title: "Installing 8.04 on a Biostar TF8200"
date: 2008-08-17
forum: Hardware
---

### Post by alfiee on 2008-08-17
Lose gui while installing Kubuntu 8.04 onto Biostar TF8200 A2/A2+.  I get a terminal instead and no directions what to do.  Any ideas?

---

### Post by finito on 2008-08-17
Try typing start x or startx I don't remember.

You to login to terminal before you can do this though.

---

### Post by Kevbert on 2008-08-17
It may be a graphics card problem.  What's your display card ?

---

### Post by alfiee on 2008-08-17
Using vidio that is onboard TF8200

---

### Post by finito on 2008-08-17
well did you try?

---

### Post by alfiee on 2008-08-17
Sorry machine not here at home.  Will try tomorrow

---

### Post by Kevbert on 2008-08-18
It uses nVidia based graphics ?

---

### Post by celem on 2008-09-18
I have loaded Ubunti 8.04 on my Biostar TF8200 A2+, also Mint and a few others trying to get it to work correctly. Sabayon Linux works the best on this motherboard. Ubuntu and Mint share the same video problem, including Ubuntu Intrepid Ibex Alpha 5. If you load the proprietary drivers as prompted by the little pop-up icon you will trash the system, requiring a reload. It screws up X so that the screen is  just bands of colors. If you load the patch directly from nVidia as directed by nVidia's instructions, you will also trash the video. If you load the patch directly from nVidia but using the instructions found in the forum, the graphics works perfectly until the first update from Ubuntu when the video will again be trashed. I gave up and loaded Sabayon which handles the video and almost everything else perfectly. I say almost because Sabayon and EVERY Linux distribution, including Ubuntu, fail to properaly handle the ALC888S audio with the nVidia chipset as implemented on the Biostar TF8200 A2+. The result with every distribution is audio with scratchy noises and reverberation. I had to disable the on board ALC888S and install a sound card. Until Ubuntu can correctly handle the geforce 8200 video I'll stick with Sabayon and by then it may be too late as Sabayon is pretty darn good.

On a positive note, I just noticed that Intrepid Ibex Alpha 6, which was just released, says the following, so it is probably worth one more try: "X.Org 7.4, the latest stable version of X.Org, is available in Intrepid. This release brings much better support for hot-pluggable input devices such as tablets, keyboards, and mice. At the same time this will allow the great majority of users to run without a /etc/X11/xorg.conf file."

I should add that I run Ubuntu 8.04 on my laptop where it works great.

---

