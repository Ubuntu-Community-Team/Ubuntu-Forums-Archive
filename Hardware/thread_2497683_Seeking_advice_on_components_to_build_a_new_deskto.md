---
title: "Seeking advice on components to build a new desktop PC."
date: 2024-05-14
forum: Hardware
---

### Post by satimis on 2024-05-14
Hi all,

I'm prepared to build a new powerful desktop PC.

[B][COLOR="#FF0000"]Configuration
=============[/COLOR][/B]
1) CPU - AMD Ryzen 9 5950X (16C 32T)

2) Mobo - ASUS PRIME X570-P
[https://www.asus.com/hk-en/motherboards-components/motherboards/prime/prime-x570-p/](https://www.asus.com/hk-en/motherboards-components/motherboards/prime/prime-x570-p/)
(I don't need WiFi)

3) Video card - NVIDIA Corporation TU116 [GeForce GTX 1650 SUPER] (rev a1) (already available)

4) Display - Dell 32" 4K display (already available)

5) RAM - 64G DDR4

6) Hard drive for running OS, Oracle VirtualBox and other software - 2TB PCIe Gen4, dual M.2, HDMI SSD

7) Hard drive for data storage - 4TB WD magnetic hard drive (already available)

8) Power Supply - Corsair CX550M (already available)

The PC is solely for daily working.  

Comment and suggestion are welcome.  Thanks in advance.

Regards

---

### Post by currentshaft on 2024-05-14
1>2

---

### Post by MAFoElffen on 2024-05-17
+1 on a good, quality PSU to support your nVidia GPU and future upgrades. Good to have a good foundation, that you don't have to worry about.

Computer Case. That depends on preference. You already chose an ATX form factor MB... I would choose something that has good air flow and room for expansion. I am used to lots of fans to cool things down, but I am used to white noise.

For VM Hosting, you said Oracle VirtualBox... But I would look into KVM. I went from VirtualBox to KVM over a decade ago and have never regretted it. So much more that you can do, with lots less problems.

You said "Work"... You didn't say what field, and any business type programs you need to support, printing requirements. Do you have to do Video conferencing? VPN for remote connection security? Other support for that Job? Or is it mostly WP, Spreadsheets, and correspondence?

Do you need to connect into your company's infrastructure as a remote worker? Or completely stand-alone? Sometimes with the first, they have their own minimum requirements set in their IT policies needed for that connection.

4K displays are great if you have to have multiple windows up at a time, but then I had to use a different cursor them because the mouse cursor was so small, I would lose it on the screen.

---

### Post by satimis on 2024-05-20
Hi all,

Lof of thanks for your advice,

I'll use this PC for daily working as well as Home Theatre PC.  I need a powerful PC for daily working.

How to Build a Home Theater PC
[https://www.logicalincrements.com/articles/build-pc-home-theater](https://www.logicalincrements.com/articles/build-pc-home-theater)

I need a powerful sound card, not the built-in sound card on the motherboard, with audio-out for connecting my Energy subwoofer and another audio-out for connecting my Wharfedale column speakers.

Please advise.  Thanks

Regards

---

### Post by MAFoElffen on 2024-05-20
I have this card: [https://www.amazon.com/ASUS-XONAR-SE-Channel-Compatibility/dp/B07HCX1NY9?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&psc=1&smid=ATVPDKIKX0DER](https://www.amazon.com/ASUS-XONAR-SE-Channel-Compatibility/dp/B07HCX1NY9?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&psc=1&smid=ATVPDKIKX0DER)

I thought about using this: [https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Filter-Chain#virtual-surround](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Filter-Chain#virtual-surround)
And using the fiber s/pdif cable, connecting to this:
[https://www.amazon.com/Denon-AVR-S760H-7-2-Channel-Theater-Receiver/dp/B09HY24XVW/ref=asc_df_B09HY24XVW/?tag=hyprod-20&linkCode=df0&hvadid=693470127118&hvpos=&hvnetw=g&hvrand=15214112979427326046&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033512&hvtargid=pla-1444950093326&psc=1&mcid=3c1486466a6a35b2a6f27cdc8cb22f11&gad_source=1](https://www.amazon.com/Denon-AVR-S760H-7-2-Channel-Theater-Receiver/dp/B09HY24XVW/ref=asc_df_B09HY24XVW/?tag=hyprod-20&linkCode=df0&hvadid=693470127118&hvpos=&hvnetw=g&hvrand=15214112979427326046&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033512&hvtargid=pla-1444950093326&psc=1&mcid=3c1486466a6a35b2a6f27cdc8cb22f11&gad_source=1)

If I had the money to spend on that...

---

### Post by falloutboy2 on 2024-08-26
> **MAFoElffen said:**
> I have this card: [https://www.amazon.com/ASUS-XONAR-SE-Channel-Compatibility/dp/B07HCX1NY9?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&psc=1&smid=ATVPDKIKX0DER](https://www.amazon.com/ASUS-XONAR-SE-Channel-Compatibility/dp/B07HCX1NY9?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&psc=1&smid=ATVPDKIKX0DER)


A couple of questions...

Are you running Ubuntu 24.04
Have you had any problems with that card under 24.04
Is it able to do 5.1 under Ubuntu and is there any special mucking around required.

Personally I am not a fan of ASUS after many years of being a loyal customer and getting expensive garbage in the way of hardware but if it fits the bill and it fully works I'd be interested in knowing.

---

