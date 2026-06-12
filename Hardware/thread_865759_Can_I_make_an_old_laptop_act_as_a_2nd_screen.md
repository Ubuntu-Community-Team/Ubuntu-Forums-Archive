---
title: "Can I make an old laptop act as a 2nd screen?"
date: 2008-07-21
forum: Hardware
---

### Post by Roasted on 2008-07-21
I have an old Sony Vaio sitting on my desk. It doesn't even have a network jack. Not even a modem jack. The battery is shot so it has to be plugged in 247 to even work. Unplugging the power to it acts the same as a desktop - instantly shuts off.

But, it has a VGA plug. I'm running a 22 inch LCD widescreen via DVI, and it has an output for VGA too... I'm wondering, if I plug in a VGA cable from my monitor to the old Sony, can I get it to run as a 2nd screen?

---

### Post by krsmit0 on 2008-07-21
maxivista will do it in windows,

read this, it might give you a place to start.

[http://blogs.msdn.com/jonathanh/archive/2004/10/07/239645.aspx](http://blogs.msdn.com/jonathanh/archive/2004/10/07/239645.aspx)

---

### Post by Roasted on 2008-07-21
I currently have Gutsy on this laptop. It's downright useless to me, unless I can make this work, so whatever OS I need to install to make it work I can do.

Is there anyway to do it with Gutsy? 


I have Hardy Heron 64 bit on my desktop.

---

### Post by kevmitch on 2008-07-21
You might want to check out xdmx (X distributed multihead xserver) that should be in the repositories. You'll likely have to have it and an xserver installed on the laptop as well as your main computer. It should allow you to link up the two xservers if I understand it correctly. I have yet to set this up myself, so hopefully, if I can't help you muddle through it, there's someone else who has some experience with it.

---

### Post by Roasted on 2008-07-21
I installed xdm (only thing that appeared in repos) but I have nooo clue how to get to it.....

---

### Post by kevmitch on 2008-07-21
Here's someone who's done it on ubuntu through GDM. 
[http://blogs.unbolt.net/index.php/brinley/2007/09/17/simple_xdmx_setup_with_gdm]("http://blogs.unbolt.net/index.php/brinley/2007/09/17/simple_xdmx_setup_with_gdm")

This makes me kind of curious to try it out now.

---

### Post by zxscooby on 2008-07-21
YES!!!
[http://www.instructables.com/id/Laptop-Converted-to-2nd-Monitor/](http://www.instructables.com/id/Laptop-Converted-to-2nd-Monitor/)

---

### Post by kevmitch on 2008-07-21
Mmm. It looks not to exist in hardy. You can find it in gutsy though. My suspicion is that it is not compatible with newer versions of xorg. 
[http://packages.ubuntu.com/search?suite=gutsy-updates&keywords=xdmx](http://packages.ubuntu.com/search?suite=gutsy-updates&keywords=xdmx)

---

### Post by Roasted on 2008-07-21
scoob - I'm sorry, was that link supposed to contain directions to instruct me how to configure my machine to recognize the laptop as being a 2nd monitor? Cause, uh, I don't see any.

---

### Post by zxscooby on 2008-07-21
yea , it has like 9 steps.

I just remembered reading that article on digg a while back , never tried it,
looks like it kinda sucks. my bad.

---

### Post by kevmitch on 2008-07-21
I think that the only relevant information is that maxivista will run under wine. The brevity with which that is mentioned suggests that it "just works". I'm kind of sceptical though . . .

---

### Post by Roasted on 2008-07-21
I figured ubuntu-ubuntu would be easier to deal with than ubuntu-windows.

I can throw XP on it for sure, but I wouldn't mind keeping ubuntu on it to get a 2nd monitor working.

---

### Post by kevmitch on 2008-07-21
Then I would pursue the xdmx route. I agree you will probably have fewer headaches keeping it Linux-only. That said, I don't think xdmx will be headache free. The fact that it isn't in hardy is not a good sign.

---

### Post by kevmitch on 2008-07-21
Reading again more carefully, you do indeed say that the laptop has gutsy on it. Was it on the gutsy laptop that you were unable to find "xdmx", or on an other system using hardy? 

"xdm" is not what you're looking for, that's the X display manager (basically a more bare bones version of GDM).

---

### Post by Roasted on 2008-07-21
Hardy = Desktop.
Gutsy = Laptop.

I simply want the laptop to act as a 2nd monitor. It serves no other purpose and has no potential besides this. So if this could work, it'd be pretty badass. I wonder if there's any other alternative?

---

### Post by kevmitch on 2008-07-21
Short of pulling out the screen of the laptop and somehow converting the proprietary connection to DVI, i think xdmx is your best bet. You could either a) download and install the xdmx .deb directly and try installing and setting it up b) downgrade the desktop to gutsy, or c) add the gutsy repositories to your sources.list on the desktop so you can get xdmx and downgrade your xserver if necessary. Of course this this last would not be the official way to do things, but it is the way I would do it, then again, I have nerves of steel.

---

### Post by kevmitch on 2008-07-21
Here's a bug report that suggests it is indeed possible to get things working in hardy. It's also got a few useful links.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/242191](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/242191)

---

### Post by Roasted on 2008-07-22
I was informed about "synergy." 

Can I use dual screen with synergy?

Note - My graphics card has VGA + DVI output. DVI is to my 22" widescreen. I was going to use the VGA for the laptop.

Installing i386 Hardy Heron on the laptop now... however the laptop has ZERO network connections. Nothing. Not even a modem connection.

---

### Post by Roasted on 2008-07-22
Aight, screw it. I'm done with the laptop.

New question.

Running a GeForce 6600 256mb. DVI + VGA output.

Running the DVI to a 22 inch LCD widescreen. I had planned on running the VGA to the laptop.

What do ya say we run VGA to a 17 inch CRT I have sitting around? How would I get dual screen configured then when using a regular CRT as the secondary monitor?

edit - I installed the nvidia settings manager. I can get the CRT monitor to respond, but only if it takes over as primary monitor. It leaves my LCD in standby mode. Somehow, it's just not getting the hint that LCD=1, CRT=2.

---

### Post by kevmitch on 2008-07-23
You're probably going to have to get an nvidia guru to help you out with that one. Using the nvidia driver is essentially using an entirely different program from the standard xorg. I do however know enough to say that you want to be looking at something called twinview. 

Regarding synergy, it will only share the keyboard and mouse. That said, now that I think about it you could have the laptop connect to your main computer via xdmcp and then run synergy between the two xservers. You would not be able to move widows from one screen to the other, but your mouse and keyboard would work on both servers and everything would be running on the desktop.

---

### Post by Roasted on 2008-07-23
synergy - yeah, but it also works across the network. I didn't realize that. This laptop doesn't even have a modem port on it... so network access is out.

I've been checking craigslist for a cheap lcd panel, like a 15 or 17 inch that somebody is dumping off for 30 bucks or less. We'll see what I can find.

What's better? To use the xorg route, or the nvidia route? I'll do whatever is simplest + more efficient at getting this done. I just googled a bit and that's what I found with multiple screens on the hardy:guide.

---

### Post by kevmitch on 2008-07-23
Oh, well if the laptop doesn't have any network ports then its pretty useless no matter how you cut it, barring of course some DIY modding of the graphics connector. 

If you have an nvidia card, using the "nvidia" xserver video driver will give you better graphics performance than using the open source "nv" driver.

---

### Post by Roasted on 2008-07-23
Meh, throw the laptop idea out. It'll just sit here, offering no purpose to me whatsoever from here on out.

But, I would like to make use of the VGA port on my graphics card I'm not using, and perhaps this old CRT I got sitting around...

But why is it when I open nvidia settings and detect both monitors, that the 2nd monitor is the one that takes over, leaving my primary LCD to be turned off with no signal? :( What am I doing wrong?

---

### Post by krsmit0 on 2008-07-23
synergy will allow you to control both computers with one mouse and one keyboard.  it will not extend you desktop.

---

### Post by Roasted on 2008-07-23
> **krsmit0 said:**
> synergy will allow you to control both computers with one mouse and one keyboard.  it will not extend you desktop.

Again...

Synergy requires a network connection. The laptop has no network connection. That idea is out...


I hooked up the CRT and messed with the settings some more. I used twinview. There is a setting, which has the options "above, below, right of, left of, center, absolute" etc... Which one should each monitor be set to?

Also - Something I noticed is, when I adjust my monitors accordingly (which isn't correct to what I want) I end up with an extended desktop...

I want to have dual screen like I did with XP before. It allowed me to drag a window to the second monitor. If I maximized that window, it would maximize to that second display. Not across both displays.

Anybody know the settings I need?

---

### Post by Roasted on 2008-07-24
Any ideas? All I'm looking for is the appropriate settings for a nvidia card with dual screen. In the nvidia settings manager, I have no idea what should be what... anybody with a dual screen setup with nvidia, I'd love to hear from you.

Also, does anybody have any recommendations on what I can do with an ati card? I was tinkering around with dual screen on my laptop, which runs an ati card. Any input?

---

