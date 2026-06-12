---
title: "HP dv6000 and the dream of SVideo (i945)"
date: 2008-05-17
forum: Hardware
---

### Post by ASULutzy on 2008-05-17
So I've been using Ubuntu on my desktop for maybe a year now and have loved it, I haven't booted into Windows on that desktop in about 6 months. 

Recently I picked up an HPdv6000, because there was a really nice deal on it, and I've gotten almost everything to work right out of the box (wireless needed some ndiswrapper tinkering, but eh, no big deal there)

Everything works pretty flawlessly, the VGA port works to extend my desktop, but no matter what I do I can't even get it to output ANYTHING to my TV through SVideo. This is really upsetting because this laptop came with a remote to control media players, and honestly Windows Media Center is the only reason left I have to boot into Windows. I've set elisa up on the laptop and everything would be perfect if I could get it to display to my TV.

I've tried install grandr, and I saw a little howto using a script called switchmon, but all that seems to do is crash my X...

If anyone has any idea how I could my Svideo to work properly I would be very happy as I would no longer have to use Windows! (It does work in Windows)

Thanks so much in advance!

---

### Post by ASULutzy on 2008-05-17
I may just go visit Radio Shanty today and buy a VGA -> Svideo converter, maybe that'll solve my problems

---

### Post by ASULutzy on 2008-05-17
Going to go ahead and give this a bump.

Anyone gotten Svideo to work with an Intel x3100 (i945 I believe)

Specifically I have an HP dv6000

---

### Post by gforster on 2008-05-17
I was just looking into this for my dv6000 (dv6607nr to be precise). It is an AMD with an nvidia card and I got it working by installing nvidia-settings and using that, it worked beyond perfectly. This is the first time I've gotten s-video working correctly with ubuntu.

of course, i don't know how that will help with intel.

---

### Post by ASULutzy on 2008-05-18
Heh, yea, I don't know if that will be the solution for me```
ryan@lappy:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

Thanks for the response though.

It's weird, under system->preferences->screen resolution, it sees that another monitor type device is attached, but it never actually outputs to it regardless of what I do. The weird thing is if I set my laptops resolution to 1280x800 (its native resolution) and the tv's resolution to 800x600, what happens is that my laptops resolution stays at 1280x800, although a lot of things (like the gnome panels) act as though I've only got 800 pixels, ie the top gnome par doesn't stretch across the entire screen, it only goes 3/4 of the way over and then stops.

Radio shack didn't have the vga -> svideo converter cable like I had hoped, and I'm still looking for a way to solve this, any help is still greatly appreciated.

---

### Post by ASULutzy on 2008-05-18
and again, I can connect another monitor using the VGA output, it's just the svideo that is giving me the problem

Can anyone make a reasonable prediction on whether or not I'll be able to output to the TV if I purchase one of those little cables that converts VGA to svideo?

---

### Post by ASULutzy on 2008-05-18
Going to try one last bump in the hopes that someone with the same Intel card I have notices

---

### Post by ASULutzy on 2008-05-18
Here's the output of xrandr --verbose if it helps```
ryan@lappy:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
	Identifier: 0x4b
	Timestamp:  24854
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
LVDS connected 1280x800+0+0 (0x4e) normal (normal left inverted right x axis y axis) 331mm x 207mm
	Identifier: 0x4c
	Timestamp:  24854
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	EDID_DATA:
		00ffffffffffff0006af748100000000
		01100103802115780a1cf59758508e27
		27505400000001010101010101010101
		010101010101c71b00a0502017303020
		36004bcf100000180000000f00000000
		00000000000000000020000000fe0041
		554f0a202020202020202020000000fe
		004231353445573038205631200a0043
	BACKLIGHT_CONTROL: kernel
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 10 (0x0000000a) range:  (0,10)
  1280x800 (0x4e)   71.1MHz -HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.4KHz
        v: height  800 start  803 end  809 total  823           clock   60.0Hz
  1280x800 (0x4f)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x50)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x51)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x53)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
TV connected (normal left inverted right x axis y axis)
	Identifier: 0x4d
	Timestamp:  24854
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	BOTTOM: 37 (0x00000025) range:  (0,100)
	RIGHT: 46 (0x0000002e) range:  (0,100)
	TOP: 36 (0x00000024) range:  (0,100)
	LEFT: 54 (0x00000036) range:  (0,100)
	TV_FORMAT: NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL         
  1024x768 (0x8f)   26.9MHz
        h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   24.0KHz
        v: height  768 start  769 end  800 total  801           clock   30.0Hz
  800x600 (0x90)   17.0MHz
        h: width   800 start  801 end  864 total  896 skew    0 clock   19.0KHz
        v: height  600 start  601 end  632 total  633           clock   30.0Hz
  848x480 (0x91)   14.5MHz
        h: width   848 start  849 end  912 total  944 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
  640x480 (0x92)   11.3MHz
        h: width   640 start  641 end  704 total  736 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
```

---

### Post by ASULutzy on 2008-05-18
Pretty one sided convo here, but I think the driver just has a bug in it.

Can anyone with the same card as me confirm they've gotten S-video to work in Ubuntu? Otherwise I'm going to file a bug report.

---

### Post by TBOL3 on 2008-05-18
Hay, I haven't tried since gutsy, but I haven't got it to work either.  But why do you want it to work so badly, svideo doesn't work very good.  No audio, and a bad resolution, and slow frame rates.  (But, hay, if you get it to work, tell me how, I want to give it a try.  Watching elisa on the tv would be cool).

Oh, I am on the dv6626us, which has the same graphics card as you.

Edit:  After looking at the time stamps, I conclude that you're a bit long winded.  I would wait at least a few hours, to a day or two, to re-ask the question.

---

### Post by ASULutzy on 2008-05-18
Well, I'm trying to update as I try new things, and let's be honest, if something falls off the first two pages, it's not getting read. I'm not really giving meaningless bumps, I'm posting new stuff like the output of xrandr --verbose.

As far as why I want to use it, well I have an audio hookup to my TV and a 1TB hard drive on my desktop filled with media. When I boot to windows I simply hook the laptop up to the TV using S-video and the audio converter I have, and stream whatever media from there I want onto my TV. My laptop came with a remote which enables me to navigate Windows Media Center from the comfort of my couch and play whatever movie/TV show I want.

In Ubuntu, an application by the name of Elisa performs pretty much exactly the same as Windows Media Center, and the laptop media remote works out of the box with it. The only problem of course is that I can't get anything to output to my TV through S-video. This means I have to reboot and load Windows everytime I want to watch media from my media drive on my TV. This isn't very convenient, and if S-video worked in Ubuntu on my card I wouldn't need to do that.

Moreover, what does it matter why I want it to work? The important thing here is that it doesn't. I'm not a Linux expert, but it seems weird to me that xrandr --verbose identifies the TV correctly and all of its supported output modes, but that no matter what I do I can't actually output to the TV.

Still looking for help :)

edit: And of course I understand the limitations and shortcomings of S-video, but until I get enough cash saved up to buy a TV that has VGA input, it's the only choice I have

---

### Post by gforster on 2008-05-22
Hey, I just want you to know that I am regularly checking this thread as I have had s-video troubles in the past. Unfortunately, I don't know enough to be able to help you out. I am looking into different things for you though.  I'll let you know what, if anything, I turn up.  

Don't give up - I understand the frustration of having your thread knocked down onto pages further back.

---

### Post by ASULutzy on 2008-05-22
Yea, I don't think this is going to get fixed till xorg-xserver-video-intel gets updated. It's got to be a driver bug.

---

