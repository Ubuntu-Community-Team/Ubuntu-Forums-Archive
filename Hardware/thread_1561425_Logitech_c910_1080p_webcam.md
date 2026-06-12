---
title: "Logitech c910 1080p webcam"
date: 2010-08-26
forum: Hardware
---

### Post by dillzz on 2010-08-26
Has anyone used this webcam on ubuntu?  

[http://www.newegg.com/Product/Product.aspx?Item=N82E16826104385](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104385)

It seems to be supported under UVC, but I cannot find any details on what is supported; for example HD recording etc.  Any input is appreciated!

---

### Post by jimestesphl on 2010-08-26
I just got one of these cameras and it works beautifully in Ubuntu 10.04.  All I've done so far is use Skype but it works well.

---

### Post by dillzz on 2010-08-27
I was reading that it does not have hardware encoding for HD.  What kind of resolution are you pulling using UVC?

[http://en.wikipedia.org/wiki/USB_video_device_class](http://en.wikipedia.org/wiki/USB_video_device_class)

---

### Post by dillzz on 2010-08-27
I was reading that it does not have hardware encoding for HD.  What kind of resolution are you pulling using UVC?

[http://en.wikipedia.org/wiki/USB_video_device_class](http://en.wikipedia.org/wiki/USB_video_device_class)

---

### Post by ptihibou on 2011-02-26
I just got a Logitech C910 webcam, but I am not sure if I should keep it or not. It works well under Kubuntu 10.04 and Skype. I also tried it with Cheese and it works beautifully. I was able to change the definition under Cheese.

The only problem occurs when restarting the computer with the webcam plugged in the USB port. I get an NTDLR is missing message as if the computer was starting under Windows and not Kubuntu. I have to unplug the webcam and restart to be able to go to Kubuntu. If I then replug the webcam at this stage, it works well.

Did anyone experience the same problem?

---

### Post by ptihibou on 2011-03-01
I realized I did not phrase well my problem. It should have read as follows:

The only problem occurs when restarting the computer with the C910 webcam  plugged in the USB port. I get an NTDLR is missing message as if the  computer was starting under Windows and not Kubuntu. I have to unplug  the C910 webcam replug my old webcam and then restart to be able to go to Kubuntu. If I then replug the  C910 webcam at this stage, it works well.

I also found the explanation to all this

I had forgotten that I had installed Kubuntu from a bootable usb stick and therefore I had changed the BIOS accordingly. For whatever reason (??) after I had plugged and unplugged the C910 webcam, the computer when booting was looking for a usb bootable and even though the C910 was unplugged something was left behind (??) which prevented it to look for the next available boot drive ie the HDD and therefore got the NTDLR is missing message.

I therefore went to the BIOS and changed it to boot first from the HDD and now, with the C910 plugged in I was able to start under Kubuntu. As I said before the C910 works well under Skype and Cheese.

---

### Post by jsfitz54 on 2011-05-03
I'm also looking for explicit directions on how to install this webcam with 11.04.
 
I am a noob with Ubuntu and need lots of help.
 
If anyone could help, it would be greatly appreciated.

---

### Post by IcarusR on 2011-05-03
It should work out of the box. Install Cheese, it's in the repos, plug webcam in, launch cheese & see if it works.

---

### Post by ugmoe2000 on 2011-05-11
> **jsfitz54 said:**
> I'm also looking for explicit directions on how to install this webcam with 11.04.
 
I am a noob with Ubuntu and need lots of help.
 
If anyone could help, it would be greatly appreciated.


Like most hardware in Linux it's plug and play (thanks-be to the kernel developers). Plug it in... installed -- fin. If you want the added features from the bloatware that logitech packages with it unfortunately you're out of luck as logitech does not develop-for/support Linux for this product.

---

### Post by meerding on 2011-08-13
I've just started with Ubuntu (newbe) and run 11.04. with Logitech C910.
The Camera works fine, but cant't get the built-in Mic working even with ALSA settings adjusted. Can anyone suggest the necessary steps or probably causes, please?

---

### Post by trungvkvk on 2011-08-13
can I  join the topic?.
 I am a newbie so do not know what is involved to learn.
 thanks

---

### Post by to_lazy_to_google on 2011-08-30
ahhhm no it does not work o_O

That webcam should be able to send 30fps in a 1920x1080 resolution and it makes barely 2 fps under linux. So stop telling people it works -.-

---

### Post by mike4ubuntu on 2011-10-06
yeah, in Maverick, I can only get about 10-13 Frames per second with HD 720 resolution.  With HD 480 resolution I can get up to about 30 FPS.  Is it any better in Natty?  I suppose it's an issue with the driver.

---

### Post by SMut on 2011-11-06
> **to_lazy_to_google said:**
> ahhhm no it does not work o_O

That webcam should be able to send 30fps in a 1920x1080 resolution and it makes barely 2 fps under linux. So stop telling people it works -.-

There is a difference between people, who know what they are doing and those who plug in a devive, start an application and start complaining if it does not work as expected.

It works perfectly, I tested it in my laptop (DualCore Pentium, Ubuntu), MiniDesktop (ViaEpia with Lubuntu) and a Quad-Core machine with Mediabuntu running and it works perfectly, but I had to adjust my settings, especially input and output devices. Cheese does not work in higher solutions and does not support fast framerates, so use guvcview instead.

---

### Post by SMut on 2011-11-06
> **mike4ubuntu said:**
> yeah, in Maverick, I can only get about 10-13 Frames per second with HD 720 resolution.  With HD 480 resolution I can get up to about 30 FPS.  Is it any better in Natty?  I suppose it's an issue with the driver.

With guvcview I can use it quite nicely with HD 720 solution (okay, tested on a quad-core machine), so what's needed is a uvc driver update to support this camera better.

I don't need those high resolutions for Jabber-Chat with video calls or to record a video for my blog and the quality is perfect, so I just wait.
Use guvcview to record your videos in lesser resolution and have a peek after recording - looks good enough to me.:P

---

