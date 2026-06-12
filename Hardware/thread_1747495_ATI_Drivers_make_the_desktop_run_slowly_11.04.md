---
title: "ATI Drivers make the desktop run slowly 11.04"
date: 2011-05-02
forum: Hardware
---

### Post by ravij96 on 2011-05-02
I hope this is in the right section.  Ok the ATI drivers for the Radeon HD 3200 makes the desktop run slowly.  If i remove the drivers it works fine. Can anyone help ?

---

### Post by ghostborg on 2011-05-03
Ubuntu 11.04 Natty. HD 3200 onboard graphics Gigabyte MB.
I'm currently using the proprietary drivers from Additional drivers.
I don't know if this helps but my system suffered choppy video playback and I found a site that said to turn off Sync To VBlank in CompizConfig Settings Manager. It's under General then OpenGL.
I also turned on Enable Tear Free Desktop in the Catalyst Control Center.
I am having a problem with my video corrupting when I watch a full screen video within the browser and when I switch back from full screen it crashes. Still have sound. Only way out is to push the reset button. I'm using a DVI connection to my monitor. I did not have this problem prior to 11.04.
I have not had much luck with ATI over the years so I'm considering buying an Nvidia card.

---

### Post by ravij96 on 2011-05-04
I changed it to Ubuntu classic with no effects and no more lag :).

---

### Post by juliobahar on 2011-06-28
Here might be something that can help speeding up your ATI 3200 HD driver.

install ccsm (compizConfig Setting Manager), and run it.
1- under the OpenGl section uncheck "Sync to VBlank"
2- under the Composite section uncheck "Detect Refresh Rate"

I hope this would help.

---

