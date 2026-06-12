---
title: "Video issues"
date: 2008-11-19
forum: General Help
---

### Post by UncleJoey on 2008-11-19
So I upgraded from 7.10 to 8.10 tonight. Not I am having the same issues before which i had fixed with this:

[http://ubuntuforums.org/showthread.php?t=751661&page=2](http://ubuntuforums.org/showthread.php?t=751661&page=2)

In that thread theres is a terminal command(gksudo gedit /etc/X11/xorg.conf) which opened up what I needed to alter. Now in 8.10 I don't see a Depth number using that code. 

I am still on that ECS motherboard and had everything working with 7.10(all hardware driver free install). 

Thanks in advance for any help. This is my mom's PC and she really likes Ubuntu...so i like to keep her up to date with the newer releases.

---

### Post by lakersforce on 2008-11-19
> **UncleJoey said:**
> This is my mom's PC and she really likes Ubuntu...so i like to keep her up to date with the newer releases.

Because of that, I would suggest you use a stable LTS release. Makes life easier for her. She's not in need of a bleeding-edge release!

---

### Post by Peter09 on 2008-11-19
Totally agree with Lakersforce, I'm keeping the people who I support firmly fixed on Hardy. They Browse and email. Hardys fine for them. They would not notice the difference if they upgraded apart from the pain for both of us.

---

### Post by prshah on 2008-11-19
> **UncleJoey said:**
> So I upgraded from 7.10 to 8.10 tonight. Not I am having the same issues before which i had fixed with this:

[http://ubuntuforums.org/showthread.php?t=751661&page=2](http://ubuntuforums.org/showthread.php?t=751661&page=2)

In that thread theres is a terminal command(gksudo gedit /etc/X11/xorg.conf) which opened up what I needed to alter. Now in 8.10 I don't see a Depth number using that code. 


From 8.04 onwards, the xorg.conf file has been marginalised, and will be ignored altogether from some future release onwards.

Currently, settings in xorg.conf are respected, but there are no default settings in it.

However, you can make the DefaultDepth change as in your previous thread, and it will be taken into account when you restart X.

Look for a section like (Your names will vary) :```
Section "screen" #
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
[color=red]                Depth   24[/color]
                Modes           "1024x768@60"   "1280x960@60"   "800x600@60"    "1280x1024@60"  "800x600@56"    "640x480@60"
        EndSubSection
EndSection

```

And then change the "24" in the  Depth line  to "16".

Note that using 16bit depth will affect video playback if you have Compiz enabled (dot-grid-pattern will appear on all videos).

If you have difficulties finding the relevant section, post your entire xorg.conf file here. You can copy and paste it, or, if you want to attach it as a file, you will first need to compress it```
tar cf ~/Desktop/xorglog.tar /var/log/Xorg.0.log
``` This will create a "xorglog.tar" file on your desktop, which you can attach and upload here.

---

