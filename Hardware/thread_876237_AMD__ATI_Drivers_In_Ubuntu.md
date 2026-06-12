---
title: "AMD / ATI Drivers In Ubuntu"
date: 2008-07-31
forum: Hardware
---

### Post by theflamingchicken on 2008-07-31
As I'm building a new computer to primarily run Ubuntu, I couldn't help but notice how well AMD / ATI's support for Linux has progressed since I built my last one. While I plan on dual booting with Windows for games, I'm wondering exactly what works and what doesn't with the new AMD / ATI drivers (specifically with the HD 4850).

I'm only really looking for four things:
1) Multihead Display
2) Multimedia (Movies)
3) Desktop Effects
4) Wine

Is it worth making the switch from NVIDIA just yet?

---

### Post by Bablefish on 2008-07-31
If your going to have a 64 bit CPU you will have no problem installing ATI drivers

---

### Post by markbuntu on 2008-07-31
There is still the issue of windowed video flickering when compiz is enabled with the ati drivers but that should be fixed when they start using dri2 in a few months. Other than that, which is really just a minor annoyance easily avoided, the ati drivers work great and are getting better all the time. The latest 8.7 now supports crossfire and multiple cards.

ATI expects to have their linux drivers on par with their windows drivers within the next 6 months.

---

### Post by theflamingchicken on 2008-07-31
I'd love to just wait a few months and see how things pan out, but I'm sort of in a rush to build this machine for college, so I'm content to deal with a few issues. I just don't want to run into some deal-breaking disaster that makes me shake my head and wish I'd stuck with NVIDIA.

The HD 4850 is priced about the same as the 8800 GT and according to phoronix, it's supposed to be awesome and stuff, but I've read plenty of complaints about the current state of ATI's drivers (e.g. no Wine support yet).

---

### Post by sloggerkhan on 2008-07-31
> **theflamingchicken said:**
> As I'm building a new computer to primarily run Ubuntu, I couldn't help but notice how well AMD / ATI's support for Linux has progressed since I built my last one. While I plan on dual booting with Windows for games, I'm wondering exactly what works and what doesn't with the new AMD / ATI drivers (specifically with the HD 4850).

I'm only really looking for four things:
1) Multihead Display
2) Multimedia (Movies)
3) Desktop Effects
4) Wine

Is it worth making the switch from NVIDIA just yet?

Currently no linux driver does quality accelerate decode of formats other than mpeg-2, so make sure you have a good enough CPU to decode hi-def in formats like mp4 family or divx for now, but with ATI I think you get great rendering. Ati + opengl overlay = crystal clear video and sub rendering and scaling, but higher cpu load and no compiz until dri2, Ati + xv overlay = good video, less cpu load, and seems to work with compiz for me.

Overall, Ati is now pretty easy to deal with.
Download driver, make package option for ubuntu, install the deb files and you're good to go.

If I were to buy a gpu today, I'd but an Ati card.

Re wine, I have mixed results with wine but I couldn't blame that on Ati drivers. Some things, such as warcraft 3 work great, deus ex works great, other stuff doesn't always or has glitches. Eve online had font problems, but otherwise worked. Some things just don't install. However, I can't blame this on the Ati driver. Wine is just hit or miss overall, especially if you don't have some stupid dll that's needed and can't get it installed right.

---

### Post by theflamingchicken on 2008-07-31
I think an overclocked q6600 shouldn't have too much trouble with that. 

I guess my main concern is AMD / ATI not following through on their promises and getting stuck with a gimp GPU. But I like what I'm hearing so far.

What exactly would I be stuck without if I went with ATI and how long should I expect to wait for "full" support?

---

### Post by markbuntu on 2008-07-31
dri2 is promised very soon, possibly this fall. Anyway, ati has vastly improved their support for linux since being aquired by amd which has always had a strong commitment to the linux community. They have released their card specs to the open source driver writers and are directly supporting the radeon open driver effort. 

I would expect that once dri2 comes out, ati will far surpass nvidia in this department. Besides, nvidia drivers are still dogs when to comes to 2D acceleration and their commitment to open source/linux is certainly lagging behind ati now.

---

### Post by theflamingchicken on 2008-07-31
How are the radeon open drivers faring against the proprietary Catalyst drivers? I've read the open source ones are more stable or better with 2D or something, but nobody was real specific.

---

### Post by markbuntu on 2008-08-01
It seems that the "Radeon" open source driver is working better with 2D and is more stable than the ati proprietary fglrx driver for a number of cards. My impression from reading posts here in these forums is that the 1300 - 1600 series and all older cards seem to work better with Radeon than fglrx. It seems that since ati has opened up with its info to the Raden driver developers, progress has been rapid. 

However, there are some IP issues. ATI does not control all of the code used to write its drivers and so is unable to release all the information due licensing issues. ATI is trying to work around this issue and is also working to not be caught up in this in the future. Many of these problems stem from ATI activities before it was aquired by AMD after which we have seen a wholesale turnaround in support for the open source commmunity.

I would expect that as the Radeon driver develops full suppport for various cards, ati will drop them from fglrx so it can concentrate its efforts on the bleeding edge while keeping some support for those caught in the IP trap until the Raden devs can reverse engineer them. This strategy makes sense for both ati and everyone else, users, devs, IP owners, everyone. The Radeon open driver effort is lead by Novell with financial and other support from ATI. At least that is how I understand it.

---

### Post by theflamingchicken on 2008-08-05
I just read on the Phoronix site that X.Org 7.4 will not have DRI2. They did not specify as to when DRI2 will actually be released, but some are speculating as long as a year or two. Exactly what does this mean to the future of AMD / ATI drivers for Linux?

---

### Post by Rob-e on 2008-08-05
wow, this thread is just what i was looking for

the other day i popped in an ati card and was like "hey theres 3d?!" and yeah, this is good, i will def get an ati card now with their open source driver







:popcorn:

---

### Post by fizur2002 on 2008-08-26
where can one attain the open source driver and how well does it perform in games using wine?

---

### Post by spandanj on 2008-09-11
***Can someone please summarize the future of ATI driver?***

1) when will Compiz + open GL playback be **flawless?** (yes, FLAWLESS)

(FLAWLESS = no tearing, outsync, pixels, cpu overload and YES many opengl applications simultaneously, perfect anti-aliasing for all applications)

***Can someone also explain the difference between ubuntu restricted driver and ATI driver from ATI website?***

1) does Ubuntu's restricted driver keep up with the changes ATI makes to the driver on their website?
2) is my current restricted driver as good as current ATI driver from website?
3) which one should I use now? in future?

Thank you

---

### Post by sloggerkhan on 2008-09-11
Ubuntu restricted driver's version is frozen with feature freeze. The one on ATI's website is updated ~1 time a month. 

DRI 2 is what should allow for both Open GL + Compiz. There is some talk of a special hastened release of the next x server to get it out before december, but don't know how real that is. (It would be in the latest x now, but there was some sort of intel initiated gallium-tungsten module change dealy.)

Because you can can make *.debs from ati website drivers, I say use them over ubuntu packaged ones if you go for fglrx 'cause ati makes significant improvements in many of their releases. 

If you have x1900 or older, it might be better to stick with open source, though I've always used flgrx with my x700. It used to be that the open source driver for it had texture problems with a couple games and had reduced framerates. I haven't used the open source driver for it recently enough to say if that's still the case.

---

### Post by spandanj on 2009-05-19
what's the best driver for ati radeon mobility x1400 256mb? Is it:

1) Ubuntu's Restricted driver
2) latest ATI driver from ATI website
3) open source driver 

If it's (3) open source, how do I install that. I currently have (1).

thanks.

---

### Post by jhenkins on 2009-06-02
Only the supplied RADEON driver works with the X1400. I've tried to install the latest ATI proprietry driver on Jaunty, but there seems to be no more support for the R500 series cards. I've been trawling the net now for almost a month, but cannot get any sensible answer to this problem. So yeah, sticky wicket! Just to clarify, this is ***not*** an Ubuntu problem, although it is a show-stopper for me. This is squarely ATI's fault, and I invite them to fix this quickly.

---

