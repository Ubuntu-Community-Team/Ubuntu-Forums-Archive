---
title: "laptop freezes with ati driver and compiz"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by tschuliaen on 2008-01-06
Hello

I'm finally asking here after many days of trying and googling...

I have a Samsung Laptop with Dual 2.13 and a ATI X700 Mobility. I'm using Ubuntu 7.10 Gutsy

Compiz works fine with the open source ati (radeon) drivers however the system often randomly freezes when the desktop effects are enabled! This means I can probably work for 2 minutes or up to 2 hours but somehow I always need to shut down my pc the hard way because Ctrl+Alt+F1 or Ctrl+Alt+Back wont respond although I can still move the mouse but the screen is completely frozen:(

Therefore I installed the fglrx drivers (Catalyst 7.12) which worked alright for Games etc. but of course I had the known issues of a very laggy system with really slow scrolling etc. when compiz enabled...

So now I switched back to the open source drivers and I'm wondering what else I could try or upgrade to get away these random freezes, which seem to happen when some kind of compiz animation takes place but this could be a coincidence...

Here an extract out of my xorg.conf:
```
Section "Device"
	Identifier	"ATI Technologies Inc M26 [Radeon Mobility X700]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AccelMethod"    "XAA" # or EXA <-- EXA does not work at all!
        Option          "ColorTiling"    "on"
#       Option          "EnablePageFlip" "true" <-- did not change anything
#       Option          "AccelDFS"       "true" <-- did not change anything
        Option          "TripleBuffer"   "true"
        Option          "DynamicClocks"  "on"
        Option          "DMAForXv"       "true"
	Option		"monitor-VGA-0" "monRight"
	Option		"monitor-LVDS" "monLeft"

EndSection
```

The freeze has nothing to do with my configuration with xrandr with two monitors...it happens with only one the exact same way just not as often.

Would there be solutions such as newer kernels or ati (radeon) drivers or something else? Where could the freeze be logged?

Thanks a lot...cheers!

---

### Post by cornelius2 on 2008-01-06
I think your bug is this:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/108527](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/108527)
Look at the very bottom for some suggestions.

---

### Post by tschuliaen on 2008-01-07
> **cornelius2 said:**
> I think your bug is this:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/108527](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/108527)
Look at the very bottom for some suggestions.

Yes this seems to be the error. I only had a very quick look at it and could read that the error did not happen with the restricted drivers I already tried...

Well in the meantime I tried the newer [XorgOnTheEdge]("https://wiki.ubuntu.com/XorgOnTheEdge") drivers and the error hasnt happened since! Even with 2 screens and various 3D applications running I could not reproduce the freeze! :)

I guess I will have to test for another while but until now the problem seems perfectly solved!

---

### Post by tschuliaen on 2008-01-07
GRMPF:mad:

Bad message: My compiz with XorgOnTheEdge drivers still freezes. It happened twice today! So the problem still exists:( My impression yesterday night proved wrong!

Hope someone can help...thanks

---

### Post by tschuliaen on 2008-01-13
well...bumping this up because the freezes still happen several times a day!

---

### Post by raanan on 2008-02-01
HI, 

Did you have this solved ? 

I have the same thing happening with a thinkpad t43p laptop. 

Raanan

---

### Post by tschuliaen on 2008-02-02
> **raanan said:**
> HI, 

Did you have this solved ? 

Raanan

No unfortunately not quite: my laptop still freezes from time to time...it has been getting better recently with the newer xorg driver...however i can never be 100% sure that my presentation would work etc...

cheers tschuliaen

---

### Post by erfahren on 2008-02-02
if what you work on is critical - just stop using desktop effects

I ended up just not using Compiz-Fusion altogether. Got to be a hassle disabling it if I wanted to use Blender or something.

the novelty wears off after awhile anyway - trust me!

---

### Post by tschuliaen on 2008-02-02
> **erfahren said:**
> the novelty wears off after awhile anyway - trust me!

haha true! We can do without most of the features, however I just like the Mac-way of having a dock bar  and just move the mouse to one corner and - wush - see an overview / expose of all apps! Well I'm lookin forward to Xorg 7.3 in hardy heron. Hopefully this next release won't crash NO MORE:)

---

