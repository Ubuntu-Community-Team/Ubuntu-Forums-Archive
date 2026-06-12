---
title: "ATI HD4550 Annoyance"
date: 2009-08-18
forum: Hardware
---

### Post by chrishoyle on 2009-08-18
Hi all,

Just wondering if anyone can shed any light on this minor annoyance i have.

First a bit of backstory:

In the 6 months that i have started using linux i have successfully set up an ubuntu server that serves out multimedia to my home network using samba. the idea being that a computer of some description (windows or linux) can plug into the LAN socket in any room in our house and watch films, listen to music or view photos. for the lounge i have built a dedicated media "client" using xubuntu and xbmc to access the server. At the moment we have an ageing analogue tv in the the lounge so i picked the ATI HD4550 card which has a tvout socket and also a DVI connection should we wish to upgrade our television to HD in the future.

I have successfully got the media client to work access everything in as reasonable quality as you would expect from an analogue tv, however just post boot the screen becomes a garbled mess which clears when xubuntu's X server loads and then the screen becomes clear again. I suspect this is something to do with the boot process using a different resolution or refresh rate until the xserver loads and uses the settings i have specified in the xorg.conf file.

does anyone know of anyway to change the resolution/refresh rate during boot? or suggest another reason why this might happen?

thanks in advance

Chris

---

### Post by chrishoyle on 2009-08-19
bump it up:)

---

### Post by chrishoyle on 2009-08-19
am i going to have to put this on the "too difficult" pile? :)

---

### Post by chrishoyle on 2009-08-20
i can't belive that nobody knows anything about this subject.

---

### Post by nomnomnom on 2009-08-20
> **chrishoyle said:**
> Hi all,

Just wondering if anyone can shed any light on this minor annoyance i have.

First a bit of backstory:

In the 6 months that i have started using linux i have successfully set up an ubuntu server that serves out multimedia to my home network using samba. the idea being that a computer of some description (windows or linux) can plug into the LAN socket in any room in our house and watch films, listen to music or view photos. for the lounge i have built a dedicated media "client" using xubuntu and xbmc to access the server. At the moment we have an ageing analogue tv in the the lounge so i picked the ATI HD4550 card which has a tvout socket and also a DVI connection should we wish to upgrade our television to HD in the future.

I have successfully got the media client to work access everything in as reasonable quality as you would expect from an analogue tv, however just post boot the screen becomes a garbled mess which clears when xubuntu's X server loads and then the screen becomes clear again. I suspect this is something to do with the boot process using a different resolution or refresh rate until the xserver loads and uses the settings i have specified in the xorg.conf file.

does anyone know of anyway to change the resolution/refresh rate during boot? or suggest another reason why this might happen?

thanks in advance

Chris

Install startupmanager from Synaptic. It will be installed in one of the System menus. Open it and change the 640 option to a resolution close to your monitors, and change the color depth from 8 to 24 bit. Then close startupmanager and reset, see if that helps. You can always change it back.

P.S: Sorry for the slight vagueness, but I'm using Windows ATM, and can't think straight! :P

---

### Post by chrishoyle on 2009-08-20
nomnomnom you ubuntu genius you!

it worked great with a couple of adjustments and messing around.

Thanks for the suggestion.

Chris

---

