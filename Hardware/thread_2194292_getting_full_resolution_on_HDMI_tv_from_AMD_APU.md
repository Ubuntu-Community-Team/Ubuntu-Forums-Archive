---
title: "getting full resolution on HDMI tv from AMD APU"
date: 2013-12-17
forum: Hardware
---

### Post by ratdog on 2013-12-17
Hello,  I have Ubuntu 12.04 running on my home media center and cannot setup my display to use all of the available screen on my HDMI tv.  

The JVC tv that I am using as a display has an uncommon resolution of 1366x768.  This resolution is not an option I can choose in 'Displays' (I currently have 1920x1080 selected, which looks OK but leaves a border of black pixels around the screen.  This is the screen that I use to watch movies and I would like the display to be as large and clear as possible.

Should I be using a special driver for my APU with Radeon HD 6410D?  In 'additional drivers' it says the FGLRX graphics driver is activated but not currently in use.

Thanks for your help!

---

### Post by JDorfler on 2013-12-17
Can you go to your terminal emulator and type in;

```
fglrxinfo
```

You should get something like this;

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series       
OpenGL version string: 3.3.11399 Compatibility Profile Context

If this doesn't show or just do it anyway, type in;

```
sudo aticonfig --initial
```

Or 

```
sudo amdconfig --initial
```

Something else you might want to do would be;

```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

Then, again;

```
sudo aticonfig --initial
``` or ```
sudo amdconfig --initial
```

Another thing you might want to try so you can get as much video decoding off your processor and on your Radeon HD is to;

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```

All this can be found [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") for further help and reference.

I hope this helps.

---

### Post by efflandt on 2013-12-18
Typically the closest resolution you can get in Linux would be 1360x768 which should work fine. Regardless of resolution does your HDTV itself have any setting to fill the screen? On my LG a setting called "Just Scan" tries to fill the screen with whatever digital signal it is receiving, and on Samsung I think it is called appropriately "Fill Screen".

---

### Post by ratdog on 2013-12-18
OK,

Here is the output from fglrxinfo:

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6410D
OpenGL version string: 4.2.12217 Compatibility Profile Context 9.00.11
```

Do amdconfig and aticonfig do the same thing?

I'd love to learn why I'm entering those commands...  Will these allow me to select the proper resolution?

Thanks for putting up with this novice.

Edit:  I see from the link that installing the packages in your last command will activate hardware accelaration.  Sounds like a good thing....

---

### Post by JDorfler on 2013-12-18
AMD bought ATI years ago.  Mostly AMD has replaced anything that says ATI with AMD, including their software.  However, sometimes there are still legacy commands, settings, and software that still say ATI.  Aticonfig and amdconfig should do the same thing.

---

### Post by ratdog on 2013-12-19
Thanks for the help.

Unfortunately I've still not achieved my screens native resolution.

In the Binary Driver how-to that you linked to I did try to fix my underscan issue with this command they recommended.

```
sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
```

That ended up giving me overscan and the edges of the screen disappeared.

I then figured out that I could fix that issue in Catalyst Control Center under the adjustments tab.  However,  now when I reboot the display defaults back to the overscan situation.  The tutorial didn't explain what other values to try or how to undo their command.

Since your 'amdconfig --initial' command didn't do anything for me, I kept searching and found [this]("https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions") tutorial.  Their instructions did give me a resolution close to my native resolution (cvt 1366 768 60 gave me a 1368x768_60.00 modeline) but when I try to switch to that option I just get a blank screen and then it switches back to my current settings.

I found another promising tutorial[ here]("http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/"), but I'm afraid to eliminate all of my other resolution options as the 1368x768_60.00 doesn't work the way I'm trying currently. 

Any more suggestions for getting the best picture from my 1366x768 resolution HDMI TV?  BTW my computer currently wants to default me to the 1920x1080 resolution, which actually looks OK.  Wouldn't the picture be more precise if the output matched the actual native resolution of the display?  Thanks!

---

### Post by Willyweasel on 2014-01-08
I have a hd 7870 and a 32" Emerson hdtv with the resolution set at 1080p and this works for me.
```
sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,5
```

---

