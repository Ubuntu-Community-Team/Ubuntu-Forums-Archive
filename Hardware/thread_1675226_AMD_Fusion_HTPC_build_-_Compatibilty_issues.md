---
title: "AMD Fusion HTPC build - Compatibilty issues?"
date: 2011-01-25
forum: Hardware
---

### Post by AirBiscuit on 2011-01-25
I'm on the brink of building a new mini-itx HTPC to run XBMC under  Ubuntu. I currently use Ubuntu 10.10 on an Acer laptop, without issue,  and also have a Windows PC for gaming.

My proposed build includes the (as yet unreleased) Asus E35M1-I deluxe ([http://www.bit-tech.net/hardware/motherboards/2011/01/04/amd-zacate-mini-itx-motherboards-preview/3](http://www.bit-tech.net/hardware/motherboards/2011/01/04/amd-zacate-mini-itx-motherboards-preview/3)).  Am i likely to encounter any driver issues with this system? I'm  particularly interested in this board because of the Wi-fi/bluetooth,  amongst other things, and i'd rather have them integrated on the  motherboard, than have several USB dongles sticking out of my new  machine. 

The other option is to use an Intel I3 (clarkdale) on the Gigabyte GA-H55N-USB3 board ([http://www.bit-tech.net/hardware/motherboards/2010/06/15/gigabyte-ga-h55n-usb3-mini-itx-motherboard/1](http://www.bit-tech.net/hardware/motherboards/2010/06/15/gigabyte-ga-h55n-usb3-mini-itx-motherboard/1)), and i'm guessing i'll not have any issues there...

So what does everyone reckon?

---

### Post by cascade9 on 2011-01-25
I wouldnt trust a 'preview' review at all. Pretty hard to know what will end up on the fianl board, if it comes out. With no hardware specs listed, they could put a whole bunch of linux-unfriendly things on there. 

If its not filled with nasty hardware, it could be a good base for a HTPC. Only problem is that the CPU (probably) wont have enough power to decode HD content. So you would probably have to get a video card. 

The i3 should have enough power to decode HD, but even then its more expensive to use a CPU to decode than to use a GPU. A cheap nVidia GPU will do VDPAU just fine, will use less power and create less heat than CPU HD decoding. 

IMO you would probably be better off getting a microATX case and motherboard (almost all the ITX cases I've seen have horrible clearance problems, a general lack of airflow, and ITX has far less choices in the motherboard department). 

I'd also have a good look at AMD if you do decide to get a system with a socketed CPU. An Athlon II X2 245 costs abotu half as much as an i3 , and only a bit more than the cheapest LGA 775 chips. They would probably haev enough power to decode 1080p HD just on the CPU alone, and with a VDPAU nVidia GPU the athlon II X2 has more than enough power for a HTPC.

---

### Post by AirBiscuit on 2011-01-25
Thanks for the reply!

> **cascade9 said:**
> I'd also have a good look at AMD if you do decide to get a system with a socketed CPU. An Athlon II X2 245 costs abotu half as much as an i3 , and only a bit more than the cheapest LGA 775 chips. They would probably haev enough power to decode 1080p HD just on the CPU alone, and with a VDPAU nVidia GPU the athlon II X2 has more than enough power for a HTPC.

I'm actually a bit of an AMD fan, and the Athlon 245 in the processor i use in my PC. This is partly the reason i'm holding on to see how the Fusion will be - otherwise i'd have bought the I3 by now. Also, the I3 has good onboard graphics, which i gather the AMD boards lack.

Thanks for the advice ref. an ATX system, but I'm pretty much set on the Mini-ITX form factor. It'll be going in the bedroom, so i want it as small as possible really. As such, i won't have room for a separate graphics card. 

Can you be a little more specific about decoding HD video content? Do you mean ripping, or streaming? I don't understand... (I'm not too experienced in these matters.)

---

### Post by cascade9 on 2011-01-25
Sory about changing the order from what you posted, but it makes more sense this way.
 
> **AirBiscuit said:**
> Can you be a little more specific about decoding HD video content? Do you mean ripping, or streaming? I don't understand... (I'm not too experienced in these matters.)

AFAIK, if you stream video from one computer to another it just sends the file. I could well be wrong on that, I dont do much streaming. 

When you play HD (or 'normal' video content, or even audio) the file needs to be decompressed and/or decoded. That can be done either by the CPU, or by a GPU. VDPAU is the nvidia hardware video decoding (most nvidia 8XXX cards, and all the later cards have support), XvBA is ATI (HD 4XXX and later cards supported). There is also VAAPI, which can be used by some intel chips, and can be used as a backend for XvBA and VDPAU. 

From what I've seen, VDPAU is well sorted out, XvBA is....buggy.....and thats being nice, and VAAPI I dont know much about. 

The advantage to hardware video decoding is that it lowers he CPU use a huge amount, as the CPU isnt doing the work anymore. GPUs are much better at decdoing video, and use a lot less power to do it than a CPU. 

> **AirBiscuit said:**
> I'm actually a bit of an AMD fan, and the Athlon 245 in the processor i use in my PC. This is partly the reason i'm holding on to see how the Fusion will be - otherwise i'd have bought the I3 by now. Also, the I3 has good onboard graphics, which i gather the AMD boards lack.

Intel graphics generally arent that good. The new 'sandy bridge' (LGA 1155) CPUs might be better than normal, but the older LGA 1156 intel video is pretty lame. 

The ATI onboard video found on most microATX AMD motherboards (and some of the mini ITX motherboards) is better in general than intel video, but ATI isnt the best for GPU hardware video decoding. 

There is at least one MiniITX with nVidia onboard video if you really wanted onbaord video and AMD.  

> **AirBiscuit said:**
> Thanks for the advice ref. an ATX system, but I'm pretty much set on the Mini-ITX form factor. It'll be going in the bedroom, so i want it as small as possible really. As such, i won't have room for a separate graphics card. 

Mini ATX isnt that much bigger than mini ITX. But if you really want the smallest size possible then I understand mini ITX. 

As for a video card, you might be suprised. Lots of the mini ITX cases have a an expansion sot for video cards. Some of them only take half height cards, bu thats not really a problem, you can get half-height cards that do VDPAU easily.

---

