---
title: "Atom N2800 &amp; 12.04"
date: 2012-06-26
forum: Hardware
---

### Post by tpprynn on 2012-06-26
I've done a bit of reading up on this almost by accident as it hadn't occurred ot me there'd be a problem. I've been on the verge of getting a new laptop or more likely a netbook with the best possible spec for one of those.

The Atom N2800 seems some improvement on what my two previous netbooks had and may well be right for my purposes even if I have to forego using Ubuntu with it. After four years of on/off Ubuntu use I'm very satisfied with my desktop pc running 64 bit 12.04 and hoped I could have something very similar to use in libraries and cafes. It seems though that at present the N2800 cpu will not work properly with Ubuntu, limited to Unity 2D, though the actual spec of the chips suggests its integrated graphics will be the best yet on a netbook. I imagine this is not permanent but I wondered how I would make myself properly aware of this issue in an ongoing way or have some testing input if useful - where do you look, who do you contact/ volunteer with?

I'd been asking about the Novatech N1 today, which has this cpu and is available without an OS. Having not touched Windows for a couple of weeks I don't fancy scuppering my decisiveness by installing Windows 7 on a netbook while I wait for Ubuntu/Linux to become N2800-friendly. I imagine the N570 already works to some extent but the N2800 seems sufficiently improved that I don't want to risk a compromised purchase just because it works but isn't a sufficient improvement on what I had last. I've done quite a bit of faffing with different laptops in the last year and would rather just get on and have the thing as a constant, in no need of being replaced for three years and a fairly low maintenance tool.

Thanks.

---

### Post by tpprynn on 2012-06-29
Apparently Asus have now brought out an 11.6 inch netbook with this chip and Ubuntu 12.04. So a driver can't be a problem can it, unless someone wants hard-line open source?

Maybe Asus will have the driver online for the rest of us?

---

### Post by rg4w on 2012-06-29
I believe there's a driver in development for 12.10 which should handle the graphics in the D2700 and D2800, though my information is scant so it would be good to get confirmation from someone here who knows what they're talking about. :)

But FWIW, just last week I built a system using a D2700 and Unity 2D was quite enjoyable.  In fact, aside from the missing drop shadows on the window borders the only thing I missed was being able to resize the width of the Launcher; in most other respects Unity 2D has gotten close to parity with 3D, not a bad implementation for systems that don't yet have good drivers.

---

### Post by tpprynn on 2012-06-29
That's good news, I suppose it's inevitable that they'll get round to the driver. 

I think you could get your drop shadows by turning the Metacity compositing on with gconf-editor by the way - I'm sure I did that when I tried Unity 2D a while back. Should make 2D look a bit 'warmer'. I imagine this function will be available in some way all the while Unity/ Ubuntu is still using Metacity.

---

### Post by Yellow Pasque on 2012-06-29
Avoid "Cedarview"/GMA3600 graphics like the plague (unless you never want to run 3D). It's another crappy Imagination Technologies/PowerVR GPU.

I can't remember who said it or the exact wording, but I think this meme is fitting:  "Imagination Technologies - what a perfect name. If you want a fully-working GPU in Linux, you'll have to imagine it."

---

### Post by rg4w on 2012-06-29
> **tpprynn said:**
> I think you could get your drop shadows by turning the Metacity compositing on with gconf-editor by the way - I'm sure I did that when I tried Unity 2D a while back. Should make 2D look a bit 'warmer'. I imagine this function will be available in some way all the while Unity/ Ubuntu is still using Metacity.
Great tip - thanks.

---

### Post by lmsart on 2012-07-04
> **tpprynn said:**
> I've done a bit of reading up on this almost by accident as it hadn't occurred ot me there'd be a problem. I've been on the verge of getting a new laptop or more likely a netbook with the best possible spec for one of those.
 
The Atom N2800 seems some improvement on what my two previous netbooks had and may well be right for my purposes even if I have to forego using Ubuntu with it. After four years of on/off Ubuntu use I'm very satisfied with my desktop pc running 64 bit 12.04 and hoped I could have something very similar to use in libraries and cafes. It seems though that at present the N2800 cpu will not work properly with Ubuntu, limited to Unity 2D, though the actual spec of the chips suggests its integrated graphics will be the best yet on a netbook. I imagine this is not permanent but I wondered how I would make myself properly aware of this issue in an ongoing way or have some testing input if useful - where do you look, who do you contact/ volunteer with?
 
I'd been asking about the Novatech N1 today, which has this cpu and is available without an OS. Having not touched Windows for a couple of weeks I don't fancy scuppering my decisiveness by installing Windows 7 on a netbook while I wait for Ubuntu/Linux to become N2800-friendly. I imagine the N570 already works to some extent but the N2800 seems sufficiently improved that I don't want to risk a compromised purchase just because it works but isn't a sufficient improvement on what I had last. I've done quite a bit of faffing with different laptops in the last year and would rather just get on and have the thing as a constant, in no need of being replaced for three years and a fairly low maintenance tool.
 
Thanks.
 
Ditto...I'm in the same boat, in fact, I decided not to wait for the ASUS with the N2800 and 2MB Ram coming out 4th quarter - so I bought the HP just for the purpose of installing Ubuntu... Any idea when they'll get to the upgrade? Any way to get an email when it's ready? Actually, any ideas would be helpful... Wonder if I shouldn't downgrade to Windows 7 starter in the meantime...

---

### Post by lmsart on 2012-07-04
> **tpprynn said:**
> I've done a bit of reading up on this almost by accident as it hadn't occurred ot me there'd be a problem. I've been on the verge of getting a new laptop or more likely a netbook with the best possible spec for one of those.


Just thought I should say that when I first read your note, I was truly discouraged and sad that I had just bought the new HP Mini with the Atom N2800, 2GB of RAM, and Windows 7 Home Premium...

But I thought I would try installing Ubuntu anyway. I used the Windows installer and I have to say, so far, so good. In fact, it is incredibly quick. I'm not sure, as I am not a well seasoned computer person, if I have something different in this configuration, but it is working perfectly....so far. Not sure if you like HP's - I really didn't, but the Mini that I bought was easily configured - and I didn't have to rip open an ASUS to add RAM, or wait 'till 4th quarter for the 2GB RAM configuration...

Anyway, just wanted to mention that Ubuntu is working beautifully on the N2800...I am going to use it for a few days, and then I'd like to take out Windows 7 completely, if I can figure out how to do it...

Hope this helps...

---

### Post by tpprynn on 2012-07-06
Is that including the effects and shadows, or Unity 2D? And the correct screen resolution? Are menus and programs all opening smoothly? I'm not expecting it to behave as well as my desktop pc but wouldn't like to use it if it was like myold single core netbook.

I've seen that the next Linux kernel*** adds support for the n2600 and n2800. I'm hoping to buy my machine today so that'll be good if it's all going well already.

***Already available at [http://www.kernel.org/](http://www.kernel.org/) if you don't mind compiling, but not the one offered by the Ubuntu repository just yet and which you probably have installed.

---

