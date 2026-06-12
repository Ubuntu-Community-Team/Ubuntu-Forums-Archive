---
title: "Thinkpad OneLink Pro Monitor Detection issue"
date: 2015-03-12
forum: Hardware
---

### Post by SwitchBlade on 2015-03-12
I have a Lenovo Thinkpad Yoga and have recently purchased the OneLink Pro dock for it ( [http://shop.lenovo.com/us/en/itemdetails/4X10E52935/460/6D501EE899104FF9A362D739642CFC27](http://shop.lenovo.com/us/en/itemdetails/4X10E52935/460/6D501EE899104FF9A362D739642CFC27) ).  Part of the reason for purchase was that it offered dual monitor outputs (DVI and DP) so that I could run two monitors and simply need to connect a single cable to my laptop.  Unfortunately this doesn't seem to be working in Ubuntu Gnome.  Both outputs seem to be seen by xrandr as the same one.  A list of xrandr devices on my laptop shows:

eDP1 - My laptop's screen
DP1 - both the DVI and DP outputs on the OneLink Pro
HDMI1 - The laptop's HDMI output
HDMI2 - No idea what this one is, there's no other HDMI output on the laptop or on the OneLink Pro
VIRTUAL1 - I'll take a stab in the dark as some form of virtual screen, nothing ever shows as connected to it.

I've tried various using HDMI and VGA adaptors in the DVI port on the OneLink Pro but they still identify as DP1.  I've only got one lead for the Displayport port to convert to HDMI, so not much fiddling I can do with that.

I can happily extend over 3 displays in Ubuntu Gnome if I use one monitor from the OneLink Pro, one on the onboard HDMI and use the laptop's screen for the third.  This is nice, but my plan was to just plug the laptop into the OneLink Pro and use my two monitors with it as if using a desktop, FWIW the USB, audio and ethernet on the OneLink Pro all work fine.

If I boot into Windows 8.1, that happily sees both monitors connected to the OneLink Pro as separate monitors so I can extend over the three screens with only the cable from the OneLink Pro connected.  So it does work in the manner I expect, it's just that Ubuntu Gnome isn't detecting the outputs on the OneLink Pro correctly.

Does anyone have any ideas or thoughts as to something to try that may help?  Any further information that can help just ask.

---

### Post by SwitchBlade on 2015-03-14
Answering my own question here for the benefit of any others who may find it in a search.  It turns out that the 2 ports being seen as the same by xrandr was actually a clue.  The OneLink Pro seems to be a DisplayPort Multi-stream hub, support for which only arrives in kernel 3.17.  So testing with Ubuntu 15.04 Beta sees everything working as it does in Windows.

---

