---
title: "graphics stutter with wow on ubuntu 11.04"
date: 2011-08-01
forum: Hardware
---

### Post by mangusb1 on 2011-08-01
I tried posting this earlier but couldnt find it so I'm trying it again. I have a Gateway 465-e Intel Core Processor Duo laptop which I downloaded Ubuntu 11.04 and its working fine. Installed Wine w/ Winetricks and downloaded World of Warcraft trial and it downloaded great. Problem is when I start up the game it has major graphics stuttering to the point that I cant get past the login screen. The laptop has a Intel 945 graphics chipset. Checked the glxinfo on rendering in the terminal and received a "yes". Not sure what the next step would be or if its even workable on this laptop. Anyone have any ideas as to what I can do at this point?

---

### Post by akoskm on 2011-08-01
> **mangusb1 said:**
> I tried posting this earlier but couldnt find it so I'm trying it again. I have a Gateway 465-e Intel Core Processor Duo laptop which I downloaded Ubuntu 11.04 and its working fine. Installed Wine w/ Winetricks and downloaded World of Warcraft trial and it downloaded great. Problem is when I start up the game it has major graphics stuttering to the point that I cant get past the login screen. The laptop has a Intel 945 graphics chipset. Checked the glxinfo on rendering in the terminal and received a "yes". Not sure what the next step would be or if its even workable on this laptop. Anyone have any ideas as to what I can do at this point?

Have you tried to start Wow.exe with -opengl parameter?

---

### Post by mangusb1 on 2011-08-01
added (SET gxApi "opengl") into config.wtf file and it eliminated the stutter but now the graphics are replaced with a black screen with white lettering.

---

### Post by mangusb1 on 2011-08-01
added this into the config.wtf:
SET gxApi "d3d"
SET ffxGlow "0"
Background graphics returned although still stuttering very badly but was able to log in. It took a extremely long time to complete the login to the character screen. Not really playable at this point.

---

### Post by akoskm on 2011-08-02
> **mangusb1 said:**
> added this into the config.wtf:
SET gxApi "d3d"
SET ffxGlow "0"
Background graphics returned although still stuttering very badly but was able to log in. It took a extremely long time to complete the login to the character screen. Not really playable at this point.

Have you tried this page: h[ttp://www.wowwiki.com/Wine_troubleshooting]("http://www.wowwiki.com/Wine_troubleshooting").
Anyway, are you sure that Intel 945 is enough for this game?

---

