---
title: "Disable monitor sleep during video playback!"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by KitChy on 2007-06-08
Okay so my problem basically is that whenever I go to play a video using VLC on Feisty the monitor goes to sleep after around 20mins even though I've got the function turned off in the "screen saver" section. Anyone know how to prevent this from happening?

---

### Post by KitChy on 2007-08-30
All right guys, I might have found a solution to this problem.

Try editing your /etc/X11/xorg.conf and add the following lines:

```

Section "ServerFlags"
#other options can go here
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection
```

```

Section "Monitor"
#other options can go here
Option "DPMS" "false"
EndSection
```

I added them two to my file and they work a charm!

---

### Post by chriseo22 on 2007-08-30
A much easier way to Enable and Disable this with one button is usinging Power Manager Inhibit Applet 2.18.2.  Just right click on your panel -> then click Add to Panel... -> The button should be in the System and Hardware section.  I put the button down at the bottom next to the recycle bin so when I am going to be watching a video weather in VLC or on YouTube I just click it and it disables all power saving.
[ATTACH]42103[/ATTACH]

Chris

---

### Post by RageOfOrder on 2007-08-30
> **chriseo22 said:**
> A much easier way to Enable and Disable this with one button is usinging Power Manager Inhibit Applet 2.18.2. 

Chris

Much easier. I prefer not to have DPMS on, ever, so I just threw 
xset -dpms
into my KDE startup script.

---

### Post by KitChy on 2007-08-30
Now you tell me...

:rolleyes:

---

