---
title: "TV Tuner"
date: 2008-08-13
forum: General Help
---

### Post by PCessna on 2008-08-13
Hey all,

Sorry to spam, But I also need help with a TV Tuner for that comes, same one in general, going a search on Gateway's site will get you models and stuff, here's some details.
```
http://support.gateway.com/s/VIDCARD/STB/V00704/V00704nv.shtml
```

That's all I can get, I'm so sorry but their site is so confusing, does anyone know a program I can try, already tryed meTV and says effortlessly I have no TV tuners, Anyone know what I can try, It's for Windows Vista or something like that label, so I may have to just boot into vista to watch TV, but that'd be ok

Thanks
-PCessna

---

### Post by PCessna on 2008-08-13
> **PCessna said:**
> Hey all,

Sorry to spam, But I also need help with a TV Tuner for that comes, same one in general, going a search on Gateway's site will get you models and stuff, here's some details.
```
http://support.gateway.com/s/VIDCARD/STB/V00704/V00704nv.shtml
```

That's all I can get, I'm so sorry but their site is so confusing, does anyone know a program I can try, already tryed meTV and says effortlessly I have no TV tuners, Anyone know what I can try, It's for Windows Vista or something like that label, so I may have to just boot into vista to watch TV, but that'd be ok

Thanks
-PCessna
... bump

---

### Post by derrick81787 on 2008-08-13
> **PCessna said:**
> Hey all,

Sorry to spam, But I also need help with a TV Tuner for that comes, same one in general, going a search on Gateway's site will get you models and stuff, here's some details.
```
http://support.gateway.com/s/VIDCARD/STB/V00704/V00704nv.shtml
```

That's all I can get, I'm so sorry but their site is so confusing, does anyone know a program I can try, already tryed meTV and says effortlessly I have no TV tuners, Anyone know what I can try, It's for Windows Vista or something like that label, so I may have to just boot into vista to watch TV, but that'd be ok

Thanks
-PCessna

TV Time is a nice little program for watching tv.  I think you can install it by running:
```
sudo aptitude install tvtime
```

Give that a try, but if Ubuntu thinks you don't have a tuner card installed, then you may need to look into configuring it with v4l (video for linux).

- Derrick

---

### Post by PCessna on 2008-08-14
> **derrick81787 said:**
> TV Time is a nice little program for watching tv.  I think you can install it by running:
```
sudo aptitude install tvtime
```

Give that a try, but if Ubuntu thinks you don't have a tuner card installed, then you may need to look into configuring it with v4l (video for linux).

- Derrick

Thanks,  I will try and edit this post with results.

---

### Post by PCessna on 2008-08-14
> **PCessna said:**
> Thanks,  I will try and edit this post with results.

Nope, I don't know where to look for v4l, tried searching but nothing has come up so far, I'll keep searching but a liunx would be highly appricated,I will also look  at my settings in Windows to make sure nothing is wrong.

---

### Post by PCessna on 2008-08-14
> **PCessna said:**
> Nope, I don't know where to look for v4l, tried searching but nothing has come up so far, I'll keep searching but a liunx would be highly appricated,I will also look  at my settings in Windows to make sure nothing is wrong.

bump.. It says no video device or no drivers or something. Thanks for help, I'll be willing to tell you anything else with a terminal command or asking.

---

### Post by derrick81787 on 2008-08-14
> **PCessna said:**
> Nope, I don't know where to look for v4l, tried searching but nothing has come up so far, I'll keep searching but a liunx would be highly appricated,I will also look  at my settings in Windows to make sure nothing is wrong.

Sorry for the late reply. I've been at work.

If you want to look into tvtime, here's a link to their web site [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/) .  It has some helpful information there.

There's also the v4l wiki here [http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page) .  Hopefully, this will be of some help.

- Derrick

---

### Post by PCessna on 2008-08-14
> **derrick81787 said:**
> Sorry for the late reply. I've been at work.

If you want to look into tvtime, here's a link to their web site [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/) .  It has some helpful information there.

There's also the v4l wiki here [http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page) .  Hopefully, this will be of some help.

- Derrick

This is the most confusing son of a **** I've ever seen in my whole life, I don't know where to get or how to do? Bleh...heeeee D: :mad:

---

### Post by PCessna on 2008-08-15
> **PCessna said:**
> This is the most confusing son of a **** I've ever seen in my whole life, I don't know where to get or how to do? Bleh...heeeee D: :mad:

Help me please.

---

### Post by PCessna on 2008-08-15
> **PCessna said:**
> Help me please.

help me    please

---

### Post by PCessna on 2008-08-16
> **PCessna said:**
> help me    please

bump 3....

---

### Post by kb7ypf on 2008-08-16
HI-

Maybe a fix to your problem..........

Have you tried VLC media player?  That is what I use and it works great even with my limited NVIDA Geforce 6150LE graphics card. 

To get it working...........VLC:
Click on File
Click on Open Capture Device
Click on PVR and hit OK.

If this works for you, let me know and I will post how to change the channels which is very easy.

Hope it works out.

Dick

---

### Post by PCessna on 2008-08-16
Sigh, Dick, Thanks for your help, But it didn't seem to work, However if anyone needs to know, I'll gladly go right now and get my specific Video card model from NVIDIA, :)

```
Unable to open 'pvr://'
Unable to open 'pvr://'
```

---

### Post by kb7ypf on 2008-08-16
Poor sigh,  once you have VLC open and you clicked on File, Open Capture Device, you should have 6 tabs at the top.  All I have to do is click on the PVR tab and then click OK on the bottom right OK button.  

Sorry it did not work out.  

Dick

---

### Post by kb7ypf on 2008-08-16
BTw, I have VLC version:  VLC media player 0.8.6e Janus (wxWidgets interface)

Dick

---

### Post by kb7ypf on 2008-08-16
BTw, I have VLC version:  VLC media player 0.8.6e Janus (wxWidgets interface)

Dick

---

### Post by PCessna on 2008-08-17
> **kb7ypf said:**
> BTw, I have VLC version:  VLC media player 0.8.6e Janus (wxWidgets interface)

Dick

:( same version *sigh*

---

