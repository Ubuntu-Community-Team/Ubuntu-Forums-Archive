---
title: "Can't get my Philips Webcam running"
date: 2005-02-02
forum: Hardware &amp; Laptops
---

### Post by Shambler on 2005-02-02
Hello,
I own a Philips FunCam (a.k.a. Philips DMVC 300K), but I can't get it working.
Ubuntu just mentions some USB-Device but no video device. Also,  Gnome-Meeting just recognizes my Hauppauge tv card...
It sucks a little bit, because whenever I want to do some video conferencing, I have to  boot Windows. And this is the last issue forcing me sometimes to boot Windows.

---

### Post by Shambler on 2005-02-03
*push*

---

### Post by Shambler on 2005-02-06
Nobody can help me?

---

### Post by toujours on 2005-02-06
I'm under Hoary (since Friday) and I too have webcam woes.

I downloaded a kernel module for my quickcam express (qc-usb or something like that), tried to compile and load it, but failed miserably. It works in xawtv (which you should install as a test), but with errors, and gnomemeeting is a miserable failure. I read lotsa stuff about this :

- In Warty SIS USB controllers don't work with the hotplug module (Bugzilla bug 1971). Needs a kernel upgrade. That's why I went to Hoary.

- Gnomemeeting has a bug that stops Logitech quickcams from being used (philips uses same chips I believe). I read this in the module's documentation. Try this link : [http://sourceforge.net/projects/qce-ga/](http://sourceforge.net/projects/qce-ga/)

Do a search in these forums for webcam+philips for example or webcam+quickcam for other threads and stories of woe...

Otherwise, I'm afraid I a bit of a big noob and can't help more than that.   :-(

---

### Post by trash on 2005-02-26
just about to read the link you posted toujours, but ya it does seem to be Gnomemeeting... I just upgraded to Hoary tonight(ZERO problems!:D )... cam works fine with camstream and xawtv but in gnomemeeting audio works fine but video driver is a no go... the exact oposite of what I had in Warty.
merci pour la link!

---

### Post by trash on 2005-02-26
Ok, this is kinda strange but Xawtv kept refering to v4l not v4l2 so i browsed synaptic Hoary universe/multi and found v41 not installed... I installed it and now I have working sound and video on my USB quickcam 3000 pro.... select v4l in gnomemeeting to, instead of v4l2.

hope this helps!

---

### Post by Shambler on 2005-02-27
I can't see a package named "v41" or "v4l" and I have universe/multiverse in my repositories...

---

### Post by doitashimashite on 2005-02-27
The package is called "libpt-plugins-v4l"

---

### Post by Shambler on 2005-02-27
Ok, but do I have to load a module afterwards? Because in Gnomeeting when I select v4l, only my Hauppauge tv card is recognized...

---

### Post by trash on 2005-02-27
sorry about that, I should have been a little more specific!
If you're not sure what you are looking for in synaptic, do a search with 'name and description'.

---

### Post by Shambler on 2005-02-27
I know that and it is already installed, but not working. See my last post...

---

### Post by trash on 2005-02-27
i'm not sure, all i can think is your cam isn't detected.

do you have the cam driver installed?
have you tested your cam with xawtv?

---

### Post by Shambler on 2005-02-27
Do I have to install a cam driver? I thought that every usb camera is recognized automagically??

---

### Post by trash on 2005-02-27
there are some issues with some phillips cams, i was lucky with mine. You'll need to do a search to see if yours is or not. Sorry i can't help ya more but I haven't had that much experience with cam drivers.
there is a wiki about webcams and links to drivers, you may need to check up on your cam specs.

---

### Post by john_walsh54 on 2005-06-15
I could only get my webcam on Ubuntu 5.04 to work when I installed libpt-plugins-v4l. I re-ran the configuration druid in GnomeMeeting and on the Video page, there were two options; v4l and v4l2. When I selected v4l, I was prompted to select "740" which configured the driver for the webcam.
I was pretty confident it would work because before the install, I ran the following commands in Terminal;
john@ThinkPad:~$ gst-launch-0.8 v4lsrc ! xvimagesink
RUNNING pipeline ...
john@ThinkPad:~$ gst-launch-0.8 v4l2src ! xvimagesink
RUNNING pipeline ...
ERROR: from element /pipeline0/v4l2src0: Could not get/set settings from/on resource.
Additional debug info:
v4l2_calls.c(60): gst_v4l2_get_capabilities: /pipeline0/v4l2src0:
Error getting /dev/video0 capabilities: Invalid argument
ERROR: pipeline doesn't want to play.
For the first gst command (gst-launch-0.8 v4lsrc ! xvimagesink) a window appeared with the webcam running. The second gst command seems to had an error similar to GnomeMeeting i.e. it cannot find /dev/video0
Maybe your xawtv card is causing a problem. Have you tried to take it out to see if GnomeMeeting will work.

---

### Post by twisted_steel on 2005-07-25
Shambler: any luck getting the 300K working?  I just got one for free from Comcast :)

---

### Post by wrega on 2005-08-11
[QUOTE=twisted_steel]Shambler: any luck getting the 300K working?  I just got one for free from Comcast :)[/QUOTE]

Hi there! Sorry by disturbing you but I just got that Philips Funcam from Ebay. Unfortunelly, tha seller sent me without the softwares... I contacted him, but he has thown it away... I've tried Philips Support but they only have the drivers... it works as a webcam but not like a camera...
Would it be too much if I ask you to send me a copy of it to my email (if larger than 10Mb, please rip it to different packs) address? Thanks for your attention!
[email]BrunoAntoniazzi@yahoo.com.br[/email]

---

### Post by Shambler on 2005-09-17
@twisted_teel: nah, how about you?

---

