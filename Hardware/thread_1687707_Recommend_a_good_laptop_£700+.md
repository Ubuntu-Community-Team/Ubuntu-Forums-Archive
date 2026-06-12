---
title: "Recommend a good laptop? £700+"
date: 2011-02-14
forum: Hardware
---

### Post by themusicalduck on 2011-02-14
I had just bought a Toshiba L670-18E, but the keyboard and trackpad has already packed up, the screen isn't particularly good and it generally feels very cheap. I've only had it a few weeks, so I'm getting a full refund on it.

So I'm looking for something else instead. I want something with good build quality and a decent keyboard, an actually good screen - something that matches the Samsung screens I have for my Desktop which are great.

Ideally I want something with NVidia graphics too. This seems to be the most difficult thing to find, since the majority use ATI for some reason.

I thought of getting a Dell XPS 17, but after looking at reviews and searching a bit, two of the complaints are the screen in particular and the keyboard being cheap has been mentioned once or twice too.

I've heard good things about Thinkpads, but again they all seem to use ATI and are quite expensive too. I'd love to buy a Macbook, but when I compare the price to the specs, it seems too much like it's just a big con.

I really want to get the right laptop this time and not have to go through sending it back, so if anyone knows anything that might suit me well I'd love to hear what it is.

Cheers.

---

### Post by realzippy on 2011-02-14
*Ideally I want something with NVidia graphics too. This seems to be the most difficult thing to find,...*

Harder to find is a nvidia gpu laptop that has a BIOS switch for the hybrid graphics,without you are lost,since there is no nvidia driver for
hybrid graphics.
Beware of the [Optimus]("http://ubuntuforums.org/showthread.php?t=1657660") trap and google "nvidia optimus linux"...
btw,the Intel integrated graphics core of an I3 CPU runs 3D
pretty fine.

---

### Post by themusicalduck on 2011-02-14
> **realzippy said:**
> Harder to find is a nvidia gpu laptop that has a BIOS switch for the hybrid graphics,without you are lost,since there is no nvidia driver for
hybrid graphics.

That's a shame.. quite a few laptops have that feature and look quite useful.

I think I may give up on NVidia graphics. I'd still like something with good build and a good screen though.

---

### Post by lukeiamyourfather on 2011-02-14
> **themusicalduck said:**
> 
I've heard good things about Thinkpads, but again they all seem to use ATI and are quite expensive too.

You get what you pay for. I ***love*** my ThinkPad and will probably never buy any other brand laptop ever again.

---

### Post by themusicalduck on 2011-02-15
> **lukeiamyourfather said:**
> You get what you pay for. I ***love*** my ThinkPad and will probably never buy any other brand laptop ever again.

Which model do you have out of interest?

---

### Post by mastablasta on 2011-02-15
you didn't say what you plan to do with it, but only that keyboard and monitor are of great importance to you.
 
anyway what is wrong with ATI? and have you considered HP? they have some laptops preloaded with OpenSUSE. only i think they use ATI cards.
 
ASUS had some notebooks with nvidia inside.
 
are you searching for 17" or 15"?

---

### Post by realzippy on 2011-02-15
*..anyway what is wrong with ATI?*

If I compare the 3D performance ATI/free driver and Intel Integrated
graphics here (ok,the ATI laptop is old, 9700mobility graphics),the Intel graphics runs circles around the ATI.

---

### Post by themusicalduck on 2011-02-15
mastablasta - I'll probably use it for doing general work, audio work (with Win7 probably), watching films and casual gaming (on Linux mostly, some on Win7 maybe).

The Toshiba laptop had ATI and it worked OK. There were a few glitches in some Wine games (but not in native games actually) and in desktop compositing. Also there was very bad screen tearing. But admittedly I had seemed to have gotten rid of most of the tearing with a fix posted on UbuntuGamer recently that meant using the latest ATI driver. I just have a bit more confidence in NVidia cards since my gtx260 works so well in my desktop PC.

If Intel graphics are good enough to watch HD video and play some games (like Amnesia, Savage2) then I think I'd be probably be happy with that. I have never used a PC with integrated graphics so it's hard to know how well they really perform.

I'm now considering getting a Thinkpad T510 with integrated Intel graphics. It's a shame Optimus isn't supported well or I would happily have got the model up.

I was looking for 17" but thinking of going for a 15" instead for a bit more portability.

---

### Post by mastablasta on 2011-02-15
> **realzippy said:**
> *..anyway what is wrong with ATI?*
 
If I compare the 3D performance ATI/free driver and Intel Integrated
graphics here (ok,the ATI laptop is old, 9700mobility graphics),the Intel graphics runs circles around the ATI.
 
Ehm those drivers are reverse engineered it's a miracle they work as they do :-) New laptop with new ATI card would use AMD/ATI proprietary drivers. they should work just fine especially since plenty of them ship with Linux preinstalled. On a bit older Inspirons 15 there was even an Ubuntu preinstalled with ATI card.
 
anyway ATI opened up now a bit as well it's just that community made drivers need time to catch up.
 
>  
If Intel graphics are good enough to watch HD video

I though that's what HD stands for :-)
 
> 
and play some games (like Amnesia, Savage2) then I think I'd be probably be happy with that. I have never used a PC with integrated graphics so it's hard to know how well they really perform.

 
Don't know about amnesia but i think Savage should work. I mean, Intel came a long way. It's still not as good as AMD or nVidia, but stil... for occasional game it should be fine.
 
 
I on the other hand have my eye on laptop with ATI, only no money :-) why? well for example with latest Ubuntu release AMD actually worked in sync with cannonical to make Proprietary drivers in time for new release.

---

### Post by cascade9 on 2011-02-15
> **realzippy said:**
> *..anyway what is wrong with ATI?*
 
 If I compare the 3D performance ATI/free driver and Intel Integrated
 graphics here (ok,the ATI laptop is old, 9700mobility graphics),the Intel graphics runs circles around the ATI.
 
Aside from mastablastas point on the closed source/open source drivers, comparing a 9700M (feb 2004) to a far more modern video chip is pretty pointless. 

The same 9700M would be totally outclassed classed by any newer AMD/ATI GPU, even the most lowend model. 

> **mastablasta said:**
> I though that's what HD stands for :smile:

It does...but the way that things work on windows is not the same as with linux. 

With windows, VAAPI (or whatever the windows version is called) works out of the box, no need to play with any settings. With linux, you'll ave to at least poke at things a fair bit to get VAAPI going. To be honest, I'm not even sure how well VAAPI runs with intel these days anyway.....

> **themusicalduck said:**
> If Intel graphics are good enough to watch HD video and play some games (like Amnesia, Savage2) then I think I'd be probably be happy with that. I have never used a PC with integrated graphics so it's hard to know how well they really perform.

The iX series generally have enough CPU grunt to do HD decoding on the CPU, with no VAAPI. The main exception is the 'UM'  ultra-low power models, they just dont have enough MHz to decode HD on the CPU AFAIK. 

If VAAPI works, even the UM models should decode HD smoothy...I think. 

I can only guess on if amnesia or savage 2 would work. IMO Amnesia should (minimum requirements for video is a FX series nVidia, and they are very old, Geforce 6 is recommended). Savage 2..you might be pushing it, recommended cards are Geforce 7800+ or Radeon X1900+.

---

### Post by themusicalduck on 2011-02-15
It looks like the model with the Optimus NVidia graphics may be bios switchable. In which case I could go for that model and have NVidia only selected for Ubuntu, which would suit me pretty well assuming it has vdpau and reasonable 3D support.

Does anyone know if this wouldn't work for any reason?

---

### Post by cascade9 on 2011-02-15
If there is a BIOS switch, it should be fine...provided that the manufacturer doesnt disable that in a future BIOS update (dells done that before, they will do it again). 

BTW, IIRC at some of the i7 models ([SIZE=-1] i7 720QM) [/SIZE]have no intel HD video, so if you are looking for a farily fast laptop they might be your best bet. Its a real pain though, there is a very similar model (i7-620M) that does support optimus, so I'd be very careful checking. You dont want to be caught out with an optimus laptop.

---

### Post by lukeiamyourfather on 2011-02-15
> **themusicalduck said:**
> Which model do you have out of interest?

The model I have is probably not well suited for your needs, but I have an X61. If you've used a ThinkPad then you know why they are excellent, if you haven't then here are a few of my observations about ThinkPad laptops in general. The build quality is top notch (large metal hinges for screen, magnesium chassis, durable keys and buttons, spill protected keyboard, etc.), most include the keyboard LED light at the top of the monitor (very useful!), most include fingerprint readers for authentication, their included software is useful and there isn't any crapware (if you use Windows) and their support is great.

---

