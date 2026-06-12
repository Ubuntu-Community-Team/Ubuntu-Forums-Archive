---
title: "Fanless low cost hardware?"
date: 2016-06-08
forum: Hardware
---

### Post by SimonHGR on 2016-06-08
Hi all, I have a slightly specialized need, and I'm hoping someone might be able to help.

I need a computer, powerful enough to grab an audio stream via USB from a standard audio device (Ubuntu supports the device just fine, that's already proven). I need to store the audio as a simple data stream (I could store it in raw for all I care, I can encode it late, and I'm sure I can find a disk big enough for 30 minutes worth).

The catch is, I want to be able to do this in total silence. The fans on my current laptop (which has an i7 processor) are making an annoying noise that's just audible in the quiet patches of what I'm recording. In support of this silence, I aexpect to use an SSD, not a "spinning rust" drive.

Oh, you might be about to suggest I buy a dedicated audio recorder, but, I also need this silent machine to run a simple word processor, or similar, which will drive a teleprompter, so, even if I had silent recording, I'd still need a silent prompter system...

Can anyone suggest, preferably low cost, hardware that I can get that will do this, and run Linux? I was thinking about one of the Chrome books, but I have zero experience with them, don't know if they accept Linux installation easily, or ... well, you know the issues one can have with specific hardware and Linux sometimes. So, any suggestions / experiences would be very welcome.

TIA!

---

### Post by henrIsider on 2016-06-09
[COLOR=#000000]any intel SoC device that can run windows will do i suppose, by that i mean an intel [FONT=arial]Z3735F and 2 or 4GB ram like the acer sw5, you might run into problems if you need internet frimware drivers, esp realtek. but you can dualboot under windows, with chromebooks you need something like [/FONT][/COLOR]https://github.com/dnschneid/crouton

---

### Post by Bucky Ball on 2016-06-09
I have an HP Stream 11 which would do the job I'd think. 32Gb eMMC card, no hard drive and no fan. Silent. Barely even gets warm. Stick a 32Gb USB3 dongle in it, or a 1Tb hard drive, and record away. They're about AU$280 here (Australia). An RPi would probably do the job. They're less than AU$100, and would run a simple word processor, like Leafpad. 

No need for whacking huge machine specs and loads of RAM. All you're doing is recording an audio stream to a USB3 dongle. Incidentally, the HP Stream runs Libreoffice just fine also (and Firefox, VLC, Youtube ... etc.).

---

### Post by sudodus on 2016-06-09
I have an Intel NUC with Intel i3. It has a fan, which does not make much noise, but is not silent. With an atom processor the power used is small enough to run without a fan. See for example this link,

[https://www.quietpc.com/sys-ultranuc-atom](https://www.quietpc.com/sys-ultranuc-atom)

I think but I am not sure that the atom processor is powerful enough for your purpose.

-o-

The following one looks better, but is also more expensive

[http://www.cirrus7.com/produkte/cirrus7-nimbini/overview](http://www.cirrus7.com/produkte/cirrus7-nimbini/overview)

---

### Post by SimonHGR on 2016-06-09
Wow, thanks guys, looks like there are some awesome possibilities suggested here. Searching for Z3735F led me to the "Intel compute stick" for US$59 which seems like an intriguing option (with Ubuntu 14.04 preinstalled). A Raspberry Pi is a fascinating idea too, and the HP stream.

I realized I overlooked one really important requirement. I need two display ports. One for the "normal" video out so I can read my scripts when doing screencapture type stuff, and the other drives the teleprompter, and must be mirror imaged. For that, sudodus's suggestion looks promising, but I really can't have any fan at all, no matter how quiet. My condenser microphone picks up everything and has a phenomenally intrinsic low noise floor which is bugging me greatly to waste with a noisy environment.

I suppose another possibility is just some really long cables, and put everything in the next room. Hmm, sometimes it's better to take a pencil into space than to invent a space pen ;)

Anyway, I've not finished investigating these suggestions, and I'll take more if they're on offer, but I think I certainly have something to be working with from these, thanks all!

---

### Post by sudodus on 2016-06-09
An alternative is to get a video splitter - an adapter with one input port and two output ports (with identical signals). But it might be cheaper and is definitely more convenient, if your computer has two video ports, or would it be enough with a laptop or similar with a built in screen and a port for an external monitor?

---

### Post by Bucky Ball on 2016-06-09
> **sudodus said:**
> ... or would it be enough with a laptop or similar with a built in screen and a port for an external monitor?

Sounds like a plan. The Stream has one HDMI out _only_. No other vid out.

---

### Post by SimonHGR on 2016-06-14
More good ideas, thanks. So long as the device is silent, I guess I only need one "external" video output. I can use the device's screen for the second display, even if it's fairly small. However a splitter unfortunately won't work in this particular requirement, since one output must be mirror image for the teleprompter. I can do that easily with xrandr but do need to have a separate device output for it. But the built in screen should suffice for the "normal" presentation.

---

### Post by jake-swensen on 2016-06-14
USB to VGA/DVI/HDMI adapter might provide additional video output.  For example:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812200149](http://www.newegg.com/Product/Product.aspx?Item=N82E16812200149)

---

### Post by mastablasta on 2016-06-15
there are various ITX boards available online and also small devices people use as media centers (the small celerons that are SoC) that will be capable, have no fan, room for disk inside and quite often, multiple display ports.

i saw very cute HP mini pc's but i don't know if they have fan inside or not. the CPU's are those low powered ones with U in the end.

anyway this is some advice for quiet media centers: [SIZE=2]http://mymediaexperience.com/updated-htpc-recommendations/
[/SIZE]
have a look here for example: [SIZE=2]http://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20160615022827&SearchText=+Intel+Celeron+C1037U
[/SIZE]
many of such systems have onlinereviews. so if oyu see one you like search for review. some of those sold are actually of amazing quality given the price.

like this one (never mind the chinglish): [SIZE=2]http://www.aliexpress.com/item/2015-New-Single-Board-Computer-Mini-Desktop-Z3735f-Mini-PC-X30-N2930-N2930-1-83GHZ-Support/32444788695.html?spm=2114.10010108.1000014.7.mpEIUV&scm=1007.13338.33346.0&pvid=52e753e3-ce4e-44be-9a83-323af7ac7496&tpp=1
[/SIZE]
dual port VGA+HDMI. no fans. SSD drive (4GB, 64 GB SSD, i34010U) for 182 USD and says free shipping to my country. 

looks good, seler rating is descent.

---

