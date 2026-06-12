---
title: "Dell 640m/e1405 + Windows Rebate/Refund"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by TheVeech on 2007-01-29
My laptop finally died on Saturday night after years of service, so I'm in the market for a new one.

If money was no object, I suppose I'd get a Thinkpad, but it is, so I'm thinking about getting a Dell 640m/e1405.  My dead laptop had integrated graphics and started to struggle recently (with multimedia-intensive websites).  The Dell has integrated graphics, too, but is this really an issue for a non-gamer?  Specifically, would I be restricted in being unable to use eye-candy?

And what are these machines like to actually use day-to-day?  Are there better alternatives (the small form-factor isn't essential)?

Finally, what's the situation re: getting a rebate/refund for not using Windows or negotiating with the outlet before purchase?  It's pretty ridiculous if I have to buy something I don't want and won't use.  I've emailed Dell UK, but had no response.  Are they under the thumb?  If not, how much can I expect to save?

**Proposed spec:**
Intel® Core™ 2 Duo Processor T7200 (2.0 GHz, 4 MB L2 cache, 667 MHz FSB)
14.1" UltraSharp™ Wide Screen WSXGA (1440x900) TFT Display with TrueLife
1024MB 667MHz Dual Channel DDR2 SDRAM (2x512)
160GB (5,400 rpm) Sata Hard Drive
Fixed Internal 8X DVD+/-RW Drive
9 Cell, 80Whr Lithium Ion Primary Battery
Intel Pro Wireless 3945 802.11a/b/g Mini PCI Wireless LAN Card for Core 2 Duo Processors

Thanks all.

---

### Post by tschneiter on 2007-02-01
Hey there-
I just got through an Ubuntu install on a new 640m with the following specs:
1.83ghz core 2 duo
1024mb ram
120gb hdd
intel 950 integrated graphics
dell draft-n wireless (stupid choice, I know.)
1440x900 widescreen
A08 bios

I could not get the Bluetooth working (then again I didnt try too hard), nor the media card reader. I had to start by installing dapper in safe mode, followed by upgrading to Edgy. The video was taken care of with 915resolution. The wireless card in mine is based on the broadcom chipset, so I used ndiswrapper to get wireless working (relatively well). I installed the 686-smp core to get support for the core 2 duo.

My biggest frustration dealt with acpi. When I shut the screen, it wouldnt turn back on when opened until I hacked a script together to do so. Hibernation worked, but I couldnt for the life of me get sleep mode to work. I actually succeeded in getting it to go all the way into sleep mode once (complete with throbbing power LED), but couldnt get it to come back to life after that. When I messed with the configuration enough for it to come back to life from sleeping, it wouldnt actually go all the way into sleep mode, thus still wasting power and generating heat. Since this is something I rely on (I am on the go a lot, need my battery to last a long time w/out plugging it in, thus need sleep to work), I was forced to switch back to windows for now.

I was able to run Beryl quite well. I turned off blurring since it generated some lag, but everything else worked flawlessly. 

Long story short, I wish I could have gotten sleep to work, and I wish other ACPI functions worked properly out of the box. Other than that though, the install was pretty smooth.

---

