---
title: "Display problems with laptop. Need HELP!!"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by nat21 on 2007-06-07
Hi,

I just installed Xubuntu 7.04 on an old Dell Inspiron 8000 laptop with an ATI Mobility M4 video card. The install went fine, but when it boots up, my display is split vertically into 3 sections. I've included a photo I took of the screen.

Anyone know how to fix this?? It was working fine under WinXP so I know it's not a hardware problem.

Thanks, Nathan.

---

### Post by Workinman57 on 2007-06-07
My C840 GeForce440 64 mg memory does a similar display. I have a 15 inch screen I get a Full GUI and the start of one below it pluss streaming olored lines on right side about 2 inches wide. Happens when I change video driver to the Nvidia Factory Driver from the "NV" driver which seems to work fine except no beryl. FreeSpire Install does same as it uses Restricted driver. I belive chages to the display xorg config will fix but I dont know what to change.

---

### Post by firdooze on 2007-06-08
what resolution are you using? try changing the resolution of your screen

---

### Post by nfoav8or on 2007-06-10
In regards to the Inspiron laptop, you can make the screen "one" again by pressing FN and F7. This will not fix the resolution issues but rather make it so you can sanely apply changes to xorg.conf with an editor.

I've had to go in and manually change the file using this post:

[http://ubuntuforums.org/showthread.php?t=167670&highlight=Inspiron+8000]("http://ubuntuforums.org/showthread.php?t=167670&highlight=Inspiron+8000")

pay special attention to the user psyke83. his changes to the xorg.conf file are the only ones I needed to make to have a full desktop with 1400x1050 res.

---

### Post by Workinman57 on 2007-07-04
If you hook an external monitor to the laptop do the hold FN  press F8 to switch to the external monitor it comes acrossed clean then switch back and LCD on laptop will be straight as soon as you re boot you will be back to square one. At least you can use a straight desktop to work out the problem. I alsp have an 8000 with ATI video. Have you noticed the cd rom no longer works after install? or is it just me?

---

