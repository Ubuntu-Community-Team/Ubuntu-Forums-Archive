---
title: "Multiple graphics drivers for mobile hdd."
date: 2009-02-10
forum: Hardware
---

### Post by ApatheticLoser on 2009-02-10
Hello! I'm trying to get my full install of ubuntu 8.10 gnome on a usb drive to have both of the proprietary drivers for ati and nvidia installed. I'm currently using switchconfig with reasonable success to switch between nvidia/intel/vesa ndiswrapper/linux wireless drivers. The usb's main purpose is to be a recovery from any system, but I also want to be able to load a comfortable display/hardware set up from about 10 different PC's, and so far this is my only big hick-up.

If I install ati, it deletes my nvidia driver, and vis versa.

Anyone have any ideas?

---

### Post by tturrisi on 2009-02-11
Use the vesa driver, it will work w/ almost all display adapters.  Else you'll need a script to detect the adapter and load the correct driver.

---

### Post by ApatheticLoser on 2009-02-17
I would use vesa, but its too limiting in terms of display.

I'm not sure I understand what you mean by detach the adapter? These are different computers that I'll be moving my usbHD between. Also, the main issue I am having, is the two different drivers will not co-exist on the same system, even wanting to only use one at a time.

---

### Post by ApatheticLoser on 2009-02-18
Maybe if you could give me more of an understanding of what you were implying.

---

### Post by ApatheticLoser on 2009-02-25
Bump. I could really use help with this. I have no fear of losing this install, as I could always just try again, so please, any suggestions.

---

### Post by ApatheticLoser on 2009-03-15
I suppose I should just give up hope on finding a solution to my situation.

---

