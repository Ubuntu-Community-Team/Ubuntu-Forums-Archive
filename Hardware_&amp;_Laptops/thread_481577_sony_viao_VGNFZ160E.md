---
title: "sony viao VGNFZ160E"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by tich on 2007-06-22
hi.

i am looking around for a new notebook and the sony viao is a pretty nice looking machine but i can't seem to find anything about whether ubuntu is compatible with it.

i would love to hear how easy or complicated it is to get ubuntu up and running on the vaio series (preferably the VGNFZ160E) from anyone that has/is using one.
...or if anyone has stumbled across a resource that may be helpful please post a link!!

thanks  ;)

---

### Post by whayong on 2007-06-22
Until someone replies with real time experience with this model, all we can say is it a hit and miss kind of thing.  My Vaio took Fiesty in pretty well.  A couple things that might make getting it up and running "fully" are:

1.) Built in camera - I'm not sure if Fiesty has drivers for this, maybe someone here will chime in.
2.) Wifi - I didn't see what specific chipset the wifi card is using and if Ubuntu supports it, I'm ASSuming it's an intel since it a Sony so you might be good here.

Other then that, the hardware listed in sony.com for this laptop looks like it would work just fine, but again, I think it's a hit and miss thing and we'll only know for sure until you try it, or someone else that has the same model trys it.

---

### Post by kerry_s on 2007-06-22
sony is very propriety, you would be better off with a regular system like hp, dell, etc...

the biggest problem is drivers. they don't share nothing so till some one hacks a driver your stuck, the newer the less likely it is well supported if it is supported at all. i have a old vaio pcg-f430, i mean it's from way back, 450mhz 64ram stock and the fn keys don't work, now mine is old and there is no support for simple buttons, what do you think the odds are for a new system, do you think any kind of drivers have made it into the kernel?

---

### Post by kd7jkt on 2007-06-22
I'm using a VAIO VGN FJ250P which I got used. I started with Dapper and went up to Feisty. So far I have had few problems with it, I will list them:

1. The Webcam was not recognised until Feisty was installed, now it works fine  with Ekiga and also Xsane. I did at one time have to get a driver from France, unfortunately I no longer have the URL (my bad). Note, it did work OK off the 7.04 live CD using those drivers.

2. The DVD-RW was not mounting properly until the Feisty installation, now works fine. This turned out to be a permissions issue.  

And some further comments:

3. This one has all Intel for video, audio, chipsets, etc. The i810 video driver performs very well with Open GL 3d acceleration.

4. If you have the ipw2200 Intel wireless LAN chip, you are in luck. This is well supported in Feisty.

As always, YMMV

Jim

---

### Post by IntuitiveNipple on 2007-07-18
> **kerry_s said:**
> sony is very propriety, you would be better off with a regular system like hp, dell, etc...

the biggest problem is drivers. they don't share nothing so till some one hacks a driver your stuck, the newer the less likely it is well supported if it is supported at all. i have a old vaio pcg-f430, i mean it's from way back, 450mhz 64ram stock and the fn keys don't work, now mine is old and there is no support for simple buttons, what do you think the odds are for a new system, do you think any kind of drivers have made it into the kernel?
I suspect the work I'm currently doing on a comprehensive Sony Notebook Control driver based on my reverse-engineering the Windows driver for all Sony notebooks might be of interest to you.

See the thread: [Calling all Vaio owners](http://ubuntuforums.org/showthread.php?t=465491)

---

### Post by Cavalier1723 on 2007-07-18
I have an FZ190 CTO configured with Blu-ray and Nvidia

If you have both of these you will probably have the same problems I did/do

There is a problem in installation where you get that dreaded tty error, you can work around it and X will have a problem launching but you just have to edit xorg.conf and change nv to vesa. 

Current problems I know of with my 190 CTO:
Function keys dont work
Suspend/Resume problems
Problems recognizing cd drive. You can work around this but I cant get DMA to yet work
Motion eye camera. (can probably work around this, havent tried)
Headphone jack doesn't work (I believe it will work with the newest ALSA drivers from cvs but i cannot yet get them to compile)
Wireless (It partially works with NDISWrapper but with this I can't boot with my wireless card enabled or it freezes. It also cuts off every once in a while. I tried the intel wireless driver but had problems with that too)

So yeah theres definitely some problems..
cool laptop though :)

---

### Post by blenzi on 2007-08-17
Which version of Ubuntu are you using, Cavalier? 64 or 32-bits? And what did you do to Vista?

I am considering installing Feisty, because I had those problems with FZ-190 running Dapper live, so I am virtualizing it for the moment.

---

### Post by astarem on 2007-11-10
> **tich said:**
> hi.

i am looking around for a new notebook and the sony viao is a pretty nice looking machine but i can't seem to find anything about whether ubuntu is compatible with it.

i would love to hear how easy or complicated it is to get ubuntu up and running on the vaio series (preferably the VGNFZ160E) from anyone that has/is using one.
...or if anyone has stumbled across a resource that may be helpful please post a link!!

thanks  ;)


Hi,

I have installed gutsy (x86-64 edition) on my VGNFZ160E a couple of days ago. It is my first linux experience and until now everything went okay.

I had to do a couple of edits after installation:

1. graphics driver for intel 965 is blaclisted and therefore compiz fusion cannot be enabled without configuring the engine to skip the blaklist check, which is pretty easy and there are guides for it... however, video does not work when compiz is enabled, which can be solved by installing xgl.

2. the earphone jack and built in mic do not work after install either. but there is a howto for hda intel sound and following it solves the problem.

3. i'm still looking for a way to enable the webcam...

4. fn keys, except for the mute key, don't work either and i'm looking for a solution for it too. 

These are the only problems I encountered until now and I am satisfied with ubuntu. I hope this helps you decide...

---

