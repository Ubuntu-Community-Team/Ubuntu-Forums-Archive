---
title: "Wont do 1280x960 !"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by Rudis on 2005-09-27
Hi, i have a problem.. in Windows i can run 1280x960 in 72hz !
but in Ubuntu the highest resolution i can run is 1024x768 !
and it feels kinda clumsy !
and in windows i can run 1600x1200 in 60hz !


Here is my log file: [http://home.bip.net/e_erik/xorg.log](http://home.bip.net/e_erik/xorg.log)
and my config: [http://home.bip.net/e_erik/xorg.conf](http://home.bip.net/e_erik/xorg.conf)

Thanks for any help with this !

---

### Post by mlomker on 2005-09-27
Thanks for posting the logs, that was smart.

```

(WW) NVIDIA(0): Not using mode "1280x960" (width 1280 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)

```

Try commenting out the line that says DPMS by putting a **#** in front of it.  Your monitor is reporting to the driver that it can only do 1024.  You might have to create something called a **modeline**, but try commenting it out first.

---

### Post by Rudis on 2005-09-27
Still just get 1024x768.. [http://home.bip.net/e_erik/xorg.new.log](http://home.bip.net/e_erik/xorg.new.log)
thats the logfile from this session ! with that line commented !

Thanks !

---

### Post by mlomker on 2005-09-27
Look at [this link.]("http://lists.suse.com/archive/suse-linux-e/2003-May/0142.html")

Add this to your Driver's section:

```

Option "UseEdidFreqs" "1"

```

---

### Post by Rudis on 2005-09-27
do you mean Device section ? or the Monitor Section ??

---

### Post by mlomker on 2005-09-27
[QUOTE=Rudis]do you mean Device section ?[/QUOTE]

Yup.  I just searched Google with that error message.  Take a look at the link.

---

### Post by Rudis on 2005-09-27
Still same problems, didnt fix anything. shouldnt i try to enter the H-sync and V-sync value for my monitor ? Proview Ta-772 (dont know any of those two)

---

### Post by mlomker on 2005-09-27
Did you try the second command in that link?

```

Option "SoftEDID" "1"

```

If that doesn't work then you'll need to start experimenting with modelines...can be a lot of trial and error.

They look like this:
```

 Modeline 	"1280x960" 83.20 1280 1296 1552 1664 960 960 967 1003

```

You can see where they go [here.]("http://www.viajes-abaco.com/8880/xf86config-4_xine.htm")

---

### Post by Rudis on 2005-09-27
Still didnt fix it... but what does the 83,20 stands for ? not the hz ? the monitor can only do 1280x960 in 72 hz.. or doesnt it have anything to do with that ?

---

### Post by mlomker on 2005-09-27
That's something called a pixel clock.

Try:

```

Modeline "1280x960"  124.54  1280 1368 1504 1728  960 961 964 1001  -HSync +Vsyn

```

There's a number of [online generators]("http://www.sh.nu/nvidia/gtf.php") and tons of stuff in Google.  I'm afraid I can't help you too much more...it's just trial and error at this point.

With that particular generator you'll need to be sure to rename the output to "1280x960" in the begining.

---

### Post by Rudis on 2005-09-27
I think you can help me a little bit more ! 

Parse error on line 70 of section Modes in file /etc/X11/xorg.conf
        "+Vsyn" is not a valid keyword in this section.

Should i change +Vsyn to my Vsync ?? or +MY_Vsync ?!

---

### Post by jute on 2005-09-27
Yes, you should.

---

