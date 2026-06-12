---
title: "Can't set HDTV to 1920x1080"
date: 2009-12-29
forum: Hardware
---

### Post by tobz1000 on 2009-12-29
I'm trying to use my 1080p TV as a second viewport for my laptop, but in Display Preferences it doesn't display resolution options above 1360x768. I was wondering if there was something I could change in xorg.conf to set it to 1920x1080, but it seems I don't have an xorg.conf file, and to my knowledge I'd have to kill X to create one. In case I was going down the wrong path entirely I thought it'd be best to post here first.

I'm using a fairly limited integrated graphics chipset (Intel GM4500, 64MB) so I suppose this could be the problem?

I've also connected to a very similar TV before whose max resolution was 1360x768, so I guess there's a chance it thinks it's the same tv and is therefore using the same settings (both show up as 'LG Electronics 52"', when in fact they're 32" TVs).

If anyone had any ideas I'd be very grateful.

---

### Post by tobz1000 on 2010-01-01
bump? :)

---

### Post by nerd6 on 2010-03-02
My TV is the same - 1366 x 768 is the max resolution using a VGA connection.  If I want 1920 x 1080, I have to use HDMI.  This might just be a limitation of VGA connections.

---

### Post by solitaire on 2010-03-02
i can get 1920x1080 through my VGA.
What card do you have and what drivers are you using?
It might be a limitation of the driver.

---

### Post by delectate on 2010-03-02
as far as i know

some tv don't have 1920*1080 resolution

they use lower resolution instead of 1920*1080

what's your video card?if nvidia,try set it in nvidia-settings

---

### Post by anderlan on 2010-07-23
I am also having the same problem.  I am using the current (2010-7-22) proprietary nvidia driver suggested by 10.04.  I have a 6200LE PCIexpress card.  Toshiba hdtv, and yes I know it does 1080p, duh.  I've had it running with earlier Ubuntus but I can't remember what I did at the moment.  Besides, the set up may have changed, so I'm looking for the generic answer "add modes to ubuntu" again.

---

