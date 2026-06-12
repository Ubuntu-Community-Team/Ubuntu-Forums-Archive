---
title: "Breezy i915 weird 3D problems"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by Burkey on 2005-11-09
Well, Breezy setup the video card on my laptop the same as Hoary did.. mostly, but I seem to have a major problem.

3D Acceleration!  And before anyone asks, yes Direct Rendering is on, glxgears spits out around 1200fps.

Enemy Territory however will not use 1024x768 and instead goes black with the music still playing before showing me an 800x600 screen in the bottom left hand edge of my 1024x768 LCD panel.  Yes xorg.conf has modes from 640x480-1024x768 in it.

If I then start a game, the 800x600 game-screen runs really well, fast+smooth, so the 3D is working.

The next problem comes from World of Warcraft under Cedega, it is very slow!  as in the login screen running at like 1fps.  The stupid thing is the new Cedega 5.0 3D tests all pass ok.

I am sure this must effect more than just me, but either people with desktops just buy an nVidia and people with laptops often don't bother to play games.

I do have an amd64 with an nVidia that runs games awesome but I travel a lot and do not want to abandon my games while away.. especially since I have a 3/4 weeks out on work coming up.

---

### Post by tflovik on 2005-11-09
I'm having similar problems with my Dell Inspiron 6000(i915).
I think the problem lie in xorg. 6.8.2 use the i810 driver, but when 6.9/7.0 comes it will support the i915 driver. I read this on xorg's homepage. I hope that Dapper will use the next xorg.

---

### Post by Burkey on 2005-11-09
Interesting, I am on a Latitude D410.

I don't think it is a i810 problem actually, I know the newer drivers will hopefully be better but it used to run ok on Hoary under the i810 driver.

I actually wonder about the screen changes being related to randr extensions or something as I had experience that about 2 or 3 laptop's ago with an ATI, but it has RANDR and it all seems fine.

What has me stumped is how the same version of Cedega that used to work does not (makes me think display driver/xorg) but Enemy Territory runs with hardware acceleration, however cannot set 1024x768.

---

### Post by Burkey on 2005-11-09
Come on, surely there are others out there....

Does anyone know then how to allocate more than the default 8Mb RAM?  Perhaps through a Grub mtrr paramter?

---

### Post by igor4u on 2005-11-10
I have Sony FS115MR and have problem with resolution using Nvidia driver.
Only 1280*768 instead 1280*800. But with nv driver its okay. Maybe the problem with X.org? :???:

---

### Post by Burkey on 2005-11-10
Possible, but I still tend to think it is something else in the Distro setup, I am pretty sure even on Hoary with all up to date software the x.org version was actually the same.

---

### Post by zonk on 2005-11-10
Hi Burkey.


If you have the i915 Graphic-chipset take a look at that page:

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

I think the driver distributed with Breezy are not working properly with that chipset. not really sure, but I had a simillar problem on my LG LW40 and the new driver solved it.

Or take a look at this page, which is about ubuntu on a dell latitude 610:

[http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/](http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/)


I would be glad if I could help a little.


zonk

---

### Post by Burkey on 2005-11-10
I think I got the new drivers installed but have noticed no difference!  But I am not sure if it is installed right.. glxinfo still says

```

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.3.2

```

Yes, Direct rendering is on... but the snapshot I downloaded was i915-20051107-linux.i386.tar.bz2.tar

Did you're string change?

---

### Post by Burkey on 2005-11-10
*BUMP*

Anyone?  Is this a Breezy bug or just me being unlucky?

---

### Post by no1wantdthisname on 2005-11-13
I have the same problem.  Trying to run warcraft III just shows a black screen.  Also, video files sometimes have weird colors so that I have to reboot or alt+ctrl+backspace.  

Glxinfo and all the other vid tools show that direct rendering is enabled.  And, with glxgears I'm getting 1500+ fps.    

I've tried installing the the drivers from dri.freedesktop.org and they've only made things worse.  Direct rendering didn't work until I did something (I forget what) and even then I experienced the same problems mentioned before.

So I decided to see if other distros have the same problem.  Suse 10.0 works perfectly.  I can run warcraft 3 without problems and video files don't seem to have the weird colors anymore.  But meh, I've gotten used to Ubuntu.  I'm not sure what is different between the 2 distros.  I've installed the vanilla kernel 2.6.14 to see if that was the problem (Ubuntu uses kernel 2.6.12, while suse uses 2.6.13), but I still see the same video problems (as well as some new problems :???:).  

Anyone have any ideas?

---

