---
title: "Yet another resoultion problem"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by hongkonguk on 2005-06-23
Hi. I am an absolute n00b at Linux (first ever attempt to use it even) and I have the same resolution issues that a lot of folks are having. I have done a search on these forums and tried to edit the config files like they all seem to suggest. Unfortunately I cant seem to even see the file mentioned never mind edit it. Can anyone shed some light on why I cant,or even give me a step-by-step walkthrough cos if I cant get a decent resolution (640*480 just isnt good enough and is the maximum at the moment) I may have to revert back to windows....(terrible isnt it)

Cheers in advance

---

### Post by frodon on 2005-06-23
can you post your xorg.conf file ?

---

### Post by !nkubus on 2005-06-23
Well, as per you mention in your post, since you don't know where the files are sitting.

open a text editor : gedit(ubuntu) or kwrite(kubuntu) and open the file located at :
/etc/X11/xorg.conf  

and copy the content here so we can try to resolve your issue.

also it would be a great idea to put your system spec like:

Laptop or Desktop
processor speed/model
Ram
video card model  and ram(very important)
Screen model (also very important)

looking forward to help you :)

cheers

---

### Post by hongkonguk on 2005-06-23
Right. Thanks for your help so far. I have sussed what I was doing wrong (trying to use gedit when I have Kubuntu...DOH!!) and I have managed to change the resolution.

However,now I have a different problem. The screen looks all squashed. I assume I will need to input the screen measuments to resolve this (could be seriously wrong here....but like I have mentioned before-n00b)

Here is what it says in my Monitor section of that file....:

Section "Monitor"
 Identifier "DELL E773p"
 Option  "DPMS"
HorizSync 30-98
 VertRefresh 50-160
EndSection

Hope we can sort this out.... Thanks for the help so far guys. It really is apprieciated. :)

---

### Post by hongkonguk on 2005-06-24
Right. Heres the current situation. I can set the screen res to 800*600 and it looks 'normal'. If I try and set it any higher it develops black borders on the side and pinches narrow in the sides.

Any ideas?

---

### Post by frodon on 2005-06-24
you can try to add this line in the monitor section, it specify the optimum resolution for this screen :   ```
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
```

Sorry if it doesn't work but i have no other idea for the moment.

---

### Post by hongkonguk on 2005-06-25
[QUOTE=frodon]you can try to add this line in the monitor section, it specify the optimum resolution for this screen :   ```
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
```

Sorry if it doesn't work but i have no other idea for the moment.[/QUOTE]
 Thanks for the suggestion but it doesnt seem to be working. Also,even though I set the resolution at 800*600 and apply the changes when i start up again it sets up at 1024*768 with the screen all messed up again...

Bizarre

---

### Post by Zeroedout on 2005-06-25
my guess, having some f-ed in the head dell montitor too, is that you ahev to also enter the DispSize option, go to the dell website, and look up your monitor, and look for the screen size and place that in the xorg.conf . Dell's documentation is surprisingly thurough. Post back if you can't figure it out, and i'll tell you the exact commands to place in the xorg.conf

---

### Post by hongkonguk on 2005-06-27
I was editing the settings in the config file and went to re-boot and then found it wouldnt boot into Kubuntu at all. :roll: 

So I have had to revert my computer into a one OS system for the time being. I have no idea what went wrong or why my computer had trouble displaying above 800*600. Looking through a lot of the posts similar to this one I noticed a lot of the people having trouble are Dell owners. Is this a coincidence? Or is it just that Dell shift a lot of pc's?

Anyway,I will be trying a few live cd versions of Linux until I can find a distro that work with my setup. Thanks to those that tried to help. If anyone who has a similar problem and found a distro that worked or a cure I would be very interested to hear it.

Cheers to all.

---

### Post by Zeroedout on 2005-06-27
[QUOTE=hongkonguk]I was editing the settings in the config file and went to re-boot and then found it wouldnt boot into Kubuntu at all. :roll: 

So I have had to revert my computer into a one OS system for the time being. I have no idea what went wrong or why my computer had trouble displaying above 800*600. Looking through a lot of the posts similar to this one I noticed a lot of the people having trouble are Dell owners. Is this a coincidence? Or is it just that Dell shift a lot of pc's?

Anyway,I will be trying a few live cd versions of Linux until I can find a distro that work with my setup. Thanks to those that tried to help. If anyone who has a similar problem and found a distro that worked or a cure I would be very interested to hear it.

Cheers to all.[/QUOTE]

did you try putting in your horizsync, vertrefresh and dispsize in the xorg.conf? That's what fixed it with my dell moniter

---

### Post by Gezzer on 2005-06-27
[QUOTE=hongkonguk]Right. Thanks for your help so far. I have sussed what I was doing wrong (trying to use gedit when I have Kubuntu...DOH!!) and I have managed to change the resolution.

However,now I have a different problem. The screen looks all squashed. I assume I will need to input the screen measuments to resolve this (could be seriously wrong here....but like I have mentioned before-n00b)

Here is what it says in my Monitor section of that file....:

Section "Monitor"
 Identifier "DELL E773p"
 Option  "DPMS"
HorizSync 30-98
 VertRefresh 50-160
EndSection

Hope we can sort this out.... Thanks for the help so far guys. It really is apprieciated. :)[/QUOTE]

i have a dell E771p

and the xorg-conf file looks like this

Section "Monitor"
 Identifier "DELL E771p"
 Option  "DPMS"
HorizSync 30-70
 VertRefresh 50-90
EndSection

---

### Post by hongkonguk on 2005-06-28
[QUOTE=Zeroedout]did you try putting in your horizsync, vertrefresh and dispsize in the xorg.conf? That's what fixed it with my dell moniter[/QUOTE]

I did yes. It made no difference whatsoever. While it made it so I could select above 640*480 it would not let me display 1024*768 properly. I get getting a squashed screen and black bars at the side... ](*,)

---

### Post by Zeroedout on 2005-06-28
hongkonguk, change your xorg.conf  to read: 

Section "Monitor"
  Identifier "DELL E773p"
  Option  "DPMS"
 HorizSync  30 - 70
  VertRefresh 50-160
DisplaySize  397 383
 EndSection


if you're wondering where i got the info, on the dell page about your monitor [http://support.dell.com/support/edocs/monitors/e773p/English/spec/spec.htm](http://support.dell.com/support/edocs/monitors/e773p/English/spec/spec.htm) 
Hope this helps.

---

