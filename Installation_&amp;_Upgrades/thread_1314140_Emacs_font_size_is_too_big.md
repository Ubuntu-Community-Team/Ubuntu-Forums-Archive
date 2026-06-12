---
title: "Emacs font size is too big"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by projectshave on 2009-11-04
Updated to Ubuntu 9.04 and now Emacs 23.1 displays fonts incorrectly. The font looks ok, but it is much larger than it should be. For example, at size 9 it looks like size 14. Every other application (for example, gedit) draws the fonts just fine. How can I get Emacs to draw the fonts at the right size? I don't even know where to start debugging this. 

I've installed emacs-snapshot, emacs23 and I rebuilt it from source. I rebuilt the font cache (fc-cache). In every case it draws the fonts too large. I'm using size 6 right now, which looks like size 9. How can I fix this? 

I've attached a snapshot that shows Emacs (left, green background) and gedit (right, white background) with the same font size. Emacs is much larger than gedit. 

Thanks.

---

### Post by JJRye on 2009-11-04
I have something similar when I run emacs under VMWare. Are you also running VMware?  If so, take a look at [http://communities.vmware.com/thread/140113]("http://communities.vmware.com/thread/140113") 

emacs and a few other programs actually pay attention to the stored dots-per-inch value as reported by, for example, xdpyinfo.  When VMWare resizes the screen, the stored DPI value gets mangled; "dots" are calculated using the *initial* screen resolution but "per inch" uses the newly *modified* screen dimensions.  I have not found a clean solution to this issue, but one clumsy workaround is to hardwire the Ubuntu VM screen to match dimensions of the physical screen *at bootup time* as follows: 

Previously my gdm logon screen was 800x600 instead of the 1920x1200 that the post-logon X session occupies - changing the logon screen to 1920x1200 "fixes" the issue.  This was hardwired by inserting
   xrandr -s 1920x1200
just before the final 
   exit 0
line in /etc/gdm/PreSession/Default

Anyone that has a better solution, including advice on the above workaround, please chime in!

---

### Post by projectshave on 2009-11-05
@JJRye: Thank you very much for your response. Yes, I am also running Ubuntu within VMWare. I had some weird problems upgrading to Player 3.0 and changed my resolution to 800x600. The GDM logon screen was very small, but it resized the screen properly once I logged in. So I thought everything was fine until I ran Emacs and got the giant font problem.

After many failed attempts to reset my GMD logon screen to the proper size, I finally found an older copy of xorg.conf somewhere and used that. It worked! My logon screen is a decent size, and now Emacs displays the fonts with the correct size, AFAIK. 

I've attached my xorg.conf. When I inspected the X log file (/var/log/Xorg.0.log) it skips lots of different resolutions and finally settled on 800x600 as the default. Now it goes to 1440x900, though I need to adjust it to my laptop's rez 1600x900. You should look at your X log to see what is going on.

---

### Post by Ian Kelling on 2009-11-14
Same issue with vmware. I found your xorg.conf to help, but not completely. When resizing the vm, it still changes the font size in emacs. The problem is particularly unusable with latex-preview. The solution I found was to use virtual box instead. Its also free software :)

---

### Post by aaron on 2010-05-28
I'm running Ubuntu 10.04 as a VMware Workstation v7.1 guest. It has the same problem with detecting DPI size, and the emacs font size freaks out.

Several approaches did not work, including using xrandr to set dpi or fbmm at gdm start. For awhile I set the Emacs font size to 3(!) but, yeugg.

To fix the issue I had to generate an xorg.conf file, at set DisplaySize to the screens actual dimensions in mm. Emacs was able to calculate the display font sizes correctly after that. 

Uninstall vmware-tools first, it interferes with the Xorg config process. It can be reinstalled at the end.

Stop the x server (note this kills your desktop, so save whatever you are working on):
```
sudo /etc/init.d/gdm stop
```

you may need to press ctrl-alt-f1 to get a login prompt, this is your usual login/password. 

```
sudo Xorg -configure
```

This will create a file "xorg.conf.new" in your home folder, it auto detected all the correct settings for me. Copy the new file to: /etc/X11/xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

In the Monitor section, add a line:
DisplaySize x y

where x y are the dimensions in mm of your screen. This can be surprisingly hard to find, I had to calculate mine by looking up the monitors pixel pitch from the manufacturer (.2505 mm) and multiplying by the horizontal and vertical resolution (2560 and 1600), which gave 641 and 400 mm respectively.

```
sudo /etc/init.d/gdm start
```

note: if you install vmware-tools after doing the above steps, you will need to reinstate xorg.conf. Auto-resizing works fine after doing this: sudo mv /etc/X11/xorg.conf.BeforeVMwareToolsInstall /etc/X11/xorg.conf

---

### Post by PatCasey on 2010-06-09
I'm running under vmware too and have the same problem though I haven't had a chance to try the solutions mentioned here.  My solution was a little easier for me though others may not like it quite as well.  

I found that the emacs22-gtk package doesn't have this problem. So whatever is ultimately causing it, it is something that changed between emacs22 and emacs23.  I found that since I really don't need the new features in 23 all that much (at least I don't think I do yet, heh), this is a quick fix to it too, at least for as long as they keep 22 in the supported tree.

I hope this helps.

---

### Post by jpkotta on 2010-06-09
You can set the DPI after the X server is started with xrandr:
```
xrandr --dpi 96 # or 72 or some other value
```

When I tried this, it didn't seem to affect any running programs, but it did affect programs started after the change (including emacs), and the output of xdpyinfo.

---

### Post by jskeioriwyue on 2010-06-13
> **aaron said:**
> 

Uninstall vmware-tools first, it interferes with the Xorg config process. It can be reinstalled at the end.



How do you uninstall vmware-tools?

---

### Post by zuikway on 2010-06-14
generating xorg.conf with added line under Monitor:
DisplaySize 521 324
worked for my Dell 2407 monitor (0.27mm dot pitch)

update, actually these still don't get correct display size even though the numbers are correct.

Thanks

---

### Post by CommentsConcerns on 2011-01-13
I figured that that this actually have something to do with the

HorizSync
VertRefresh

Setting these to the correct refresh rate of you monitor should be able to fix the problem...at least for me it did.

I've also attached my xorg.conf for those who want to look at it.

EDIT: I updated my xorg.conf file so it is set to the same as my Ubuntu install that's not on VMWare and the output for Emacs is the same, not something with huge font size...

---

