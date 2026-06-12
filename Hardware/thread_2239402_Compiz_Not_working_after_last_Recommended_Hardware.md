---
title: "Compiz Not working after last Recommended Hardware Update"
date: 2014-08-13
forum: Hardware
---

### Post by Bill Dubinski on 2014-08-13
Good Day
Thank you in advance for your time. 

This post may be long, I am a fairly descriptive person.

About a week ago I opened the update manager and it said on the top of the "normal" available updates, "New Hardware Updates Available" and a button to install. 

I was very skeptical to push the button due to issues I had before. I will post the out put of $ lspci so you know what my video card is before explaining my past problem. 

$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

Before the "new Hardware Update", (about 6-7 months ago) if I opened up the "Additional Drivers" dialog, it gave me the choice of driver version 304 and driver version 331 and said (recommended) beside it. 
At that time, driver 304 was activated. I took it upon myself to activate 331 at that time because Ubuntu said it was recommended. After my next restart it loaded into terminal mode even before going to the GRUB screen. 

At that time, I had to figure out from my laptop how to roll back FROM driver 331 back TO 304. (Caps not meant for yelling). 

Just the other day after hitting that button to "upgrade" the hardware, it did the update, then I noticed I lost Compiz and all window manager and had to roll back to Metacity. 
Then I went into the "additional drivers" dialog again, and noticed it REMOVED driver 304 and only left me with 331, but it did NOT activate it.

At this point, I am afraid to activate it due to my issues and it loading into terminal mode before, in which I forgot the terminal prompts to roll back to 304, but 304 is not even an option anymore according to the additional drivers dialog. 

And I am not sure if I can re-download it again or how to. I am sure the command is something like sudo apt-get install (something).  

So I have a few questions and concerns because it seems like I am not running a video card driver here which is why Compiz is not working. 
I am running Precise (12.04) GNOME 3 (GNOME 2 Fallback or Classic) if that info matters. 

But my concerns are what will happen if I activate driver 331?
Will it or could it boot in terminal mode again like last time?
And can I re-install driver 304 prior to "trying" 331?
Or the face that it now says "Post release updates" now instead of "Recommended" mean maybe there was a fault in the previous version and they fixed it?
Or any other suggestions will be appreciated here because I do like to "keep updated" with updates, but I do understand problems happen which is why I choose to hit the upgrade button.
And could anybody tell me why I might have had the problem before when activating 331 and it loading into terminal mode.

Thank you all for your time, again, I am sorry for the long post, but I like to include detail so the story is clear to the reader and avoid having to comment back and fourth with what I left out.

Also, on my laptop which had a ATI video card, in the update manager on that computer also running 12.04 has a hardware update. 
What is with that hardware update in the first place? Why on both a PC w/ an NVIDIA and an ATI?
I am just afraid on it starting in terminal mode by taking the (recommended suggestions)
On my laptop running the ATI the driver its using says (experimental)  and is the driver it was using by default when Installed just like driver 304 on the NVIDIA PC

---

### Post by slooksterpsv on 2014-08-13
Best guess for the last part is it may be a community driver and not one from like AMD or nVidia, I could be wrong so don't quote me on that.

Now as for the other, lets check a few things, you have an nVidia GeForce 210, lets see if 331 supports that card.. it should. I found a link that they use the xorg edgers ppa for the drivers - they may differ from official repos support wise, but it may be worth a shot.

Now what will happen if you try to activate it? Well 1 of 3 options:
1 - it works
2 - it doesn't and you go to terminal
3 - it does and doesn't work

Compiz generally relies on the graphics card to do most of it's graphical processing, hence why compiz fails to load. Try this link, add the edgers ppa and try those ones, its worth a shot as they're also using a GeForce 210 =P

[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

---

### Post by Bill Dubinski on 2014-08-14
Thank you slooksterpsv for replying. 

Yes, the site does list 331 as the recommended driver as well as it did from day one when I started using 12.04. 
But like I said, when I switched to to it from 304 it re-started in terminal mode. 

Now this time since the "update".

My problem or worry is if I activate it and it does start in terminal mode again like it did last time I applied the previous version of 331, I think I am screwed because it does not let me have 304 again and all attempts to re download it are failing either from the terminal (saying command not found when I throw the command 

```
$ sudo apt-get install nvidia-304.
```

My attempts are also failing when I try in Synaptic. It gives me the listing for the nVidia 304 driver, it lets me install it, but does not allow me to see it in the additional drivers dialog.

Sorry for this black bar text. Not allowing me to fix it. 

My fear is if I activate it and it starts in terminal mode, I have nothing to fall back to and it will not log me on or let me get past terminal mode and I am not sure if $ sudo apt-get purge nvidia-* will work at least to get me past terminal mode and back into Ubuntu with no video card driver running like now. 

What do you think my options are if I get the guts to activate it and it goes to terminal mode?

---

### Post by Bill Dubinski on 2014-08-14
I am sorry for that white text block. It was a black block and readable when I was typing it. Just highlight it as you were to copy it and it will highlight in another color to read.

---

### Post by coffeecat on 2014-08-14
> **Bill Dubinski said:**
> I am sorry for that white text block. 

Somehow you managed to enclose some of your text between  [noparse][COLOR=#ffffff] and [/COLOR][/noparse] BBCode tags, #ffffff being white! I've fixed it for you.

---

### Post by Bill Dubinski on 2014-08-14
Thank you Coffee Cat. Yes, that is what happened after copy and pasting code from a website. 
I did not know you can type in HTML to change the font color. Well, maybe I can't but you can ;-).

---

### Post by coffeecat on 2014-08-14
> **Bill Dubinski said:**
> I did not know you can type in HTML to change the font color. Well, maybe I can't but you can ;-).

Not html, but BBCode, and you can do it too:

[http://ubuntuforums.org/showthread.php?t=2054969&p=12231647#post12231647](http://ubuntuforums.org/showthread.php?t=2054969&p=12231647#post12231647)

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

If you use the advanced editor, many of the toolbar buttons will insert formatting BBCode for you. If you experiment with the preview button without actually posting, you can find out a lot about how the BBCode works. Switch your message editor to source mode with the _A/A_ button in the toolbar first though to be able to see the actual BBCode.

And rather than drag this thread off-topic, I'll end by wishing you good luck in finding a solution!

---

### Post by Bill Dubinski on 2014-08-14
> **coffeecat said:**
> Not html, but BBCode, and you can do it too:

[http://ubuntuforums.org/showthread.php?t=2054969&p=12231647#post12231647](http://ubuntuforums.org/showthread.php?t=2054969&p=12231647#post12231647)

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

If you use the advanced editor, many of the toolbar buttons will insert formatting BBCode for you. If you experiment with the preview button without actually posting, you can find out a lot about how the BBCode works. Switch your message editor to source mode with the _A/A_ button in the toolbar first though to be able to see the actual BBCode.

And rather than drag this thread off-topic, I'll end by wishing you good luck in finding a solution!


I get it now, thank you for your time

---

### Post by grahammechanical on 2014-08-14
> [COLOR=#000000]So I have a few questions and concerns because it seems like I am not running a video card driver here which is why Compiz is not working. [/COLOR]
[COLOR=#000000]I am running Precise (12.04) GNOME 3 (GNOME 2 Fallback or Classic) if that info matters. [/COLOR]

Have you accepted the hardware update? Please run

```
lsb_release -a
```

That will tell you which version of Ubuntu 12.04 you have. The upgrade will change things to 12.04.5. You will get the same Linux kernel and Xserver as in 14.04 but it will still be 12.04 and it will be supported until April 2017. If you have 12.04.2 or 12.04.3 or 12.04.4 then although Ubuntu will be supported until April 2017 the Linux kernels in those versions will no longer be supported.

I am running 14.04 and Nvidia 304 is still available in Additional Drivers. It has not been dropped. Another thing. You must be running a video driver or you would not be seeing what you are seeing. When we deactivate the proprietary video driver then the open source video driver takes over automatically.

Here is something that you could try. At the Grub menu select recovery mode and at the recovery mode select Resume. Does that get you to a working desktop? From my experience de-activating a proprietary video using Additional Drivers does not remove the code from the file system. Purging it would remove but additional drivers should let you re-install it.

Here is my take on your situation. You do or you don't. It is your choice. I much prefer Nouveau. You could try this

to restart unity

```
setsid unity
```

to restart unity by restarting compiz

```
setsid compiz --replace
```

to reset compiz, first

```
sudo apt-get install dconf-tools
```

and then

```
dconf rest -f /org/compiz/
```

[https://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/](https://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/)

Regards.

---

### Post by Bill Dubinski on 2014-08-14
> **grahammechanical said:**
> Have you accepted the hardware update? Please run

```
lsb_release -a
```

That will tell you which version of Ubuntu 12.04 you have. The upgrade will change things to 12.04.5. You will get the same Linux kernel and Xserver as in 14.04 but it will still be 12.04 and it will be supported until April 2017. If you have 12.04.2 or 12.04.3 or 12.04.4 then although Ubuntu will be supported until April 2017 the Linux kernels in those versions will no longer be supported.

I am running 14.04 and Nvidia 304 is still available in Additional Drivers. It has not been dropped. Another thing. You must be running a video driver or you would not be seeing what you are seeing. When we deactivate the proprietary video driver then the open source video driver takes over automatically.

Here is something that you could try. At the Grub menu select recovery mode and at the recovery mode select Resume. Does that get you to a working desktop? From my experience de-activating a proprietary video using Additional Drivers does not remove the code from the file system. Purging it would remove but additional drivers should let you re-install it.

Here is my take on your situation. You do or you don't. It is your choice. I much prefer Nouveau. You could try this

to restart unity

```
setsid unity
```

to restart unity by restarting compiz

```
setsid compiz --replace
```

to reset compiz, first

```
sudo apt-get install dconf-tools
```

and then

```
dconf rest -f /org/compiz/
```

[https://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/](https://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/)

Regards.



Good Day, Thank you for your help 
The out put of 
```
~$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
```



This is interesting because when I open "additional drivers" it lists only one driver which is 331, but there is no green dot next to it, it is grey. And at the bottom left just above the help button it says "this driver is not activated". On the bottom right above the close button is another button that asks me if I want to activate it. 
But in the listing of drivers it only lists the unactivated 311. This is what gave me the impression no driver was activated.

Is there a way in the terminal to see what video card driver is being used?

I have a working desktop now because to my knowledge and based upon the info above that I provided, I think that I am not running a driver or the working driver is not listed in the additional drivers dialog. 
I mentioned that I am afraid to activate 311 due to problems about 7/8 months ago when I activated 311, it booted into terminal mode and from that terminal mode, had to figure out how to roll back to 304 which I was running up until the "new hardware update" about a week ago. So I am afraid of activating 331 now which always was the (recommended driver). 

I have a working desktop now, plus I am running GNOME 3 (GNONE 2 session fallback or classic) But do you mean Unity that runs behind GNOME by asking me to "restart unity? or if I plan to activate 331 and have a problem?

I have dconf already installed. I even just checked and it is there. I installed it when installing compiz after I upgraded from 10.04 Lucid right at the time Lucid lost support.
Or do you mean I have to "upgrade" dconf tools after the hardware update? And that is why compiz is not working?
But what throws me for a loop is why does the "additional drivers" so no active driver? That is confusing.

---

### Post by slooksterpsv on 2014-08-14
i couldn't say on the last q? I use terminal heavily for installing software and checking if things are working.

If you have the same problem above, you can purge the packages and if it created an xorg.conf in /etc/X11/xorg.conf  you can remove that file restart and it should load back like when you first initially installed.

---

