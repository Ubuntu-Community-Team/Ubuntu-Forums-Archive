---
title: "webcam not working - hp pavilion"
date: 2008-04-25
forum: Hardware
---

### Post by poopdog on 2008-04-25
I open up cheese, but all I get is a test pattern and some static in the bottom right.

Is there a known incompatibility with the Pavilion?

edit:  HP Pavilion dv6000

---

### Post by Ayuthia on 2008-04-25
Can you post your information from lsusb?  If I recall correctly, there are two types of webcams on the Pavilion.

---

### Post by poopdog on 2008-04-26
> **Ayuthia said:**
> Can you post your information from lsusb?  If I recall correctly, there are two types of webcams on the Pavilion.

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000 


If we can figure this out, my kids will love you more then they love me. :)

My sister has a mac, and they love the webcam app.

---

### Post by elektriks on 2008-04-26
just buy new camera :)

---

### Post by poopdog on 2008-04-26
> **elektriks said:**
> just buy new camera :)

It's built into my laptop.

It worked fine with Vista, but Vista didnt work :D

---

### Post by linuxwizard on 2008-04-26
Hello poopdog
This is your webcam > Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd  > listed here as supported > [http://wiki.mediati.org/Supported_Devices](http://wiki.mediati.org/Supported_Devices) > this is the driver you need > [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation).

---

### Post by poopdog on 2008-04-26
> **linuxwizard said:**
> Hello poopdog
This is your webcam > Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd  > listed here as supported > [http://wiki.mediati.org/Supported_Devices](http://wiki.mediati.org/Supported_Devices) > this is the driver you need > [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation).

I performed all this, didn't get any errors, but Cheese still has the test pattern...

---

### Post by linuxwizard on 2008-04-26
Have you tried using your webcam with another application or program ?

---

### Post by poopdog on 2008-04-26
> **linuxwizard said:**
> Have you tried using your webcam with another application or program ?

No, I haven't tried any other programs.

I'm not even sure what other programs there are...

Really, I'm not interested in a webcam.

I just wanted the Cheese program so my kids could take silly pictures of themselves.

If it doesn't work, that's fine. I was just curious if anyone had come across this and worked out a solution.

Like I mentioned before, it worked in Vista, but I installed XP as soon as I could and the camera hasn't worked sense.

So really, it's not like I've lost some critical functionality.

I just thought it'd be fun to play with...

Is there a comparable program to Cheese, or are the rest of the apps basic webcam type stuff?

---

### Post by linuxwizard on 2008-04-26
Look at Camorama can be installed through repo. Their are some special effects you can use.

---

### Post by drpaul on 2008-04-27
I've just checked my dv6000 [I have the other webcam model]. It used to work fine with cheese. It doesn't now. Looks like some "recent" update broke it.

With any luck they fix it soon. I'ld write a bug report, but I don't think I could make it coherent. :-(

que sera

Paul

---

### Post by poopdog on 2008-04-27
> **linuxwizard said:**
> Look at Camorama can be installed through repo. Their are some special effects you can use.

Camorama says: "Could not connect to video device (/dev/video0). Please check connection."

---

### Post by linuxwizard on 2008-04-28
Hi poopdog
Not sure what else to say. I gave you the link to the driver you needed for your webcam and you installed that. Why you are having issues with both Cheese & Camorama I am not sure. They are the only 2 appls. I know that has effects in them. If you still want to see if the cam works try Ekiga, but it does not have any special effects.

---

### Post by bullring on 2008-04-28
I'm having the same problem with the ry5u870 drivers.  When I open gstreamer properties in my terminal I can get the webcam to work fine, but my changes in gstreamer properties are not saved when I close it. I will continue to try and find the problem.

```
# gstreamer-properties
```

---

### Post by poopdog on 2008-04-28
> **bullring said:**
> I'm having the same problem with the ry5u870 drivers.  When I open gstreamer properties in my terminal I can get the webcam to work fine, but my changes in gstreamer properties are not saved when I close it. I will continue to try and find the problem.

```
# gstreamer-properties
```

Hey, I saw myself for the first time in nearly a year!

Doing that test seemed to work.

So, what's the next step to get Cheese going?

---

### Post by zach382 on 2008-04-29
Look for something along the lines of "defalut programs" in preferences and make sure in webcam  you have v4l2 as the default for webcam.

---

### Post by niaz on 2008-05-01
i am getting this same problem with my hp dv1000. i have the r5u870 driver install fine and the cam works with ekiga, skype and gstreamer-properties. but i only get the color pattern with cheese and the same error with camorama.  
under preferences i only see preferred applications but htat doesnt have anything about webcams or video for linux (v4l2)

anyone else have any suggestions?

---

### Post by poopdog on 2008-05-03
> **niaz said:**
> i am getting this same problem with my hp dv1000. i have the r5u870 driver install fine and the cam works with ekiga, skype and gstreamer-properties. but i only get the color pattern with cheese and the same error with camorama.  
under preferences i only see preferred applications but htat doesnt have anything about webcams or video for linux (v4l2)

anyone else have any suggestions?

I cannot get this to work at all.

---

### Post by lswest on 2008-05-03
i have a Chicony Electronics Co., Ltd webcam integrated in my HP dv6545EG, and it works fine in Cheese and aMSN (only two apps i ever use it in).  Yours should work after installing the driver that was posted above (or enabling it if it is already installed).

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

### Post by aquamammal on 2008-12-21
Hey Charlemagne,


I have the r5u870 driver, but my computer seems not to even see my webcam.

Any suggestions?


Thanks.

---

### Post by andre_ant on 2010-06-13
i have a hp pavilion dv6920ei can anyone help me,really this is my first time on ubuntu?how do i know which driver i need?

---

### Post by Rusty au Lait on 2010-06-18
Same problem your having Andre_ant. I read the posts and tried to go to that wiki web site with the drivers. It's no longer there. I have not given up the search yet. If I find it I'll post.

---

