---
title: "TV tuner problem"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by ry_ry on 2005-09-16
Hi.

I've got a Wintv with FM radio PCI card. It has the bt878 chip. I downloaded xawtv and it kept giving a video overlay error and would not work.

So I tried TVTime and that did work, but the picture looked fuzzy and there were these static lines jumping around at the bottom of the picture.

So I decided to try Zapping and I was able to get a good picture on it, but if I choose the Overlay function, Zapping gives an error: "Cannot start video overlay zapping_setup_fb failed". And if I choose Preferences options, the whole Zapping application totally freezes and I have to force kill the program. If I choose Capture mode it works just fine except for the freezing part with Preferences.

Since two of the programs give a video overlay error, what is a video overlay error and is there anyway to correct it?

Also does anyone else have Zapping totally freeze up when you choose Preferences option? Is this just a bug?

I believe the version is Zapping .9.2.

So far I've uninstalled xawtv and tvtime and I'm hoping to fix these two errors in zapping since I liked it better than the other two.

Any help or advice would be great. :)

---

### Post by ry_ry on 2005-09-16
Here's a little more info.

When I issue the command "zapping" in the terminal I get this message:
** (zapping:9393): WARNING **: GConf key '/apps/zapping/plugins/deinterlace/method' is unset and has no default. Schemas incomplete or not installed?

What does that mean? Zapping still works, except for the video overlay error and the Preferences lockup.

And here is what I get when I run xawtv from the terminal:
xawtv -hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.10-custom)
looking for available devices
port 67-67
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (Hauppauge (bt878))
    flags: overlay capture tuner

:~$ xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.10-custom)
WARNING: v4l-conf is compiled without DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to typ e FontStruct
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument

What does this mean?

As stated before, Zapping does work, except for the Overlay mode brings a video overlay error, and clicking on Preferences will crash Zapping.

Xawtv does not work at all, and gives the above error messages, so I uninstalled it with synaptic.

TvTime does work but the picture quality is not that good, so I uninstalled it with synaptic also.

So I guess I'll keep using Zapping even with these 2 bugs unless someone has a solution to the 2 errors I get. I saw that at sourceforge there is a new Zapping .9.7cvs version. Can I just download that and install it or do you have to do some special compiling or something?

---

### Post by ry_ry on 2005-09-18
Update:

Well as long as I don't click on the Overlay Mode option and I don't click on the Preferences options then Zapping appears to work just fine. I'm throwing this one up to it being just bugs in this version of Zapping, unless someone else knows otherwise. So far, everything else works just fine and the picture is great.

Later.

---

### Post by tesna on 2005-09-18
have you tried tvtime ? I like it more than xawtv because I always have a problem with xawtv.

---

### Post by ry_ry on 2005-09-19
[QUOTE=tesna]have you tried tvtime ? I like it more than xawtv because I always have a problem with xawtv.[/QUOTE]

Yeah, I tried TvTime but as I stated above, the picture was kind-of fuzzy/blurry and there was a static section of the screen at the bottom which was really annoying.

So far, Zapping gives me a great picture and besides the two minor bugs as described above, it works great.

Thanks anyway. :)

---

### Post by Mustard on 2005-09-19
> :~$ xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.10-custom)
WARNING: v4l-conf is compiled without DGA support.
WARNING: couldn't find framebuffer base address, try manual
configuration ("v4l-conf -a <addr>")
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to typ e FontStruct
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument

Hmmmm..exact same error I am getting with xawtv lately.  I've been trying to work out how to find the framebuffer address, but I haven't had much luck.

I had xawtv working perfectly on one incarnation of ubuntu, but my latest install is giving me some grief.

This is my output:

```
mustard@slave:~$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
WARNING: v4l-conf is compiled without DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
```

---

### Post by nikhil84 on 2005-09-19
I have hoary...i tried getting my pixelview bt878 based card to work on it....both tvtime and zapping only shows the last channel i had set it to (in win)...scanning n changing channels doesn't work in both, i get b/w pics no matter what the format is...and audio doesn't work.
Any suggestions from anyone?

---

### Post by jflassche on 2005-09-22
Hi Ry_ry (and others),

Turns out that if I start Zapping in a console (ie $> zapping -d), select preferences
and press ctrl+c in the console several times, it actually opens - and works!
The console reports: 
oss.c: Unknown recording source 0x00000001 reported

Also I compiled Zapping 0.9.7cvs3 and the problem still exists.

---

