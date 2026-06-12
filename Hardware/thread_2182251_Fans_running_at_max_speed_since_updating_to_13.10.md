---
title: "Fans running at max speed since updating to 13.10"
date: 2013-10-20
forum: Hardware
---

### Post by Shahin_Mameghani on 2013-10-20
I'm on an Asus UX32VD running 64-bit Ubuntu 13.10. I had no issue with the fans when I was on 13.04 but  since two days ago when I upgraded to 13.10, my slim, little ultrabook sounds like a vacuum cleaner and it's not even warm! The fans stop at times, for maximum 30 seconds before starting again, and they're always running on full speed, there is no middle ground.  Does anybody have similar issues or know how to solve it? I appreciate all the help I can get.

---

### Post by stnhlnd on 2013-10-22
[FONT=arial][SIZE=3]Hi Shahin, I have the exact same problem on 32-bit Ubuntu 13.10. My UX32VD runs it's fan at full speed or full stop.[/SIZE][/FONT]

---

### Post by walterorlin on 2013-10-22
Can you run the ```
top
``` command to see if it is using nearly 100 perecent processor?

---

### Post by Henri_Seppnen on 2013-10-24
I have had the same problem about 4 times (during 1 year with ubuntu 13.04). Sensors shows that the left fan runs at full speed when temperatures get over 48 C.

After restarting few times the problem disappeared. I contacted Asus support and they proposed to send the computer to service, but I did not do that since the problem disappeared.

---

### Post by mikkro on 2013-10-28
Dear guys,
have the same problem on Ubuntu 13.04 and 13.10. This problem occurs only in a standalone installation, if I dated up from Ubuntu 12.04 the fans worked normal. But the way to update from ubuntu 12.04 to 13.04 and than to 13.10 was to long for me. The standard solutions which I found on the net did not worked.
Last Saturday the problem still occurs an I was very frustrated, so I started a firmware update for my p7p55d asus mb on 03:20 a.m.. But the whole procedure did not solve the problem. Short time before I wanted to shutdown the piece of ellectronically scrap I found a usage from a german user which have the same problem with elder ubuntu releases too. He could solve this problem as he installed the proprietary ATI driver for his gpu.
Ok, I am using an nvidia gpu, but I have nothing to loose. I installed the current nvidia driver via synaptic, rebooted and now - heavently silence.
The fans a running on a normal level.
Oh, before I forget it, the pc is running with a tripple boot. Windows 7 and 8 are running on the hardware too and the fans were ran normaly from the first boot on them.
I hope I could give you a hint.

Regards
purpletux

---

### Post by Henri_Seppnen on 2013-11-04
The problem with left fan (dedicated to graphigs) appears every now and then (twise in a month) both after and before upgrading to ubuntu 13.10. I noticed that the trigger level for temperatures (I use 'sensors' command in terminal) is about 48 C when left fan starts to run at full speed. Normally temperaturs should be about 60 C. However, when I started firefox with command 'optirun firefox' in terminal,  left fan stopped and temperatures are now normal 60 C. It seems that something is wrong with the integrated display drived or hardware but GT620M is working correctly.

I am quite a new with Ubuntu and I don't know if this bug should be reported to someone?

---

