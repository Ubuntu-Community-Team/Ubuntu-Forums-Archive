---
title: "System won't boot with RAM clock above 2400MHz"
date: 2020-10-21
forum: Hardware
---

### Post by jcdenton1995 on 2020-10-21
Hello all,

Asus ROG Strix X570-I
G-Skill Trident Z Neo DDR4 3600 32GB
Ryzen 3400G
Ubuntu 20.04 LTS

I'm not sure if this is the best place for this but there are some helpful people here so I will give it a go! Basically my computer won't boot when the RAM is clocked at anything over 2400MHz, If I go above this it will very briefly load the login screen before either abruptly changing to a green screen, or less frequently the login screen will just go all crazy (you know the sort of crazy I mean).

The limiting hardware is the Ryzen 3400G which only supports memory speeds up to 2933MHz, both the motherboard and the RAM modules support at least 3600MHz (or MT/s, whatever). I have enabled the only DOCP memory profile which is 3600MHz, and then manually set the memory frequency to 2966MHz or less, I have also tried manually setting the memory frequency and voltage. In either scenario I cannot successfully boot with the memory frequency set to more than 2400MHz. I also updated my firmware as the version that came with the board was a few versions old.

If anyone more knowledgeable has any suggestions they would be appreciated! :p

---

### Post by CatKiller on 2020-10-21
The strict answer is that only the default speed is actually within specification, and only particular modules that are on the QVL have been tested to work when overclocked.

However, loosening the latency requirements may help, and it's easier to keep two modules running fast than four.

---

### Post by jcdenton1995 on 2020-10-21
> **CatKiller said:**
> The strict answer is that only the default speed is actually within specification, and only particular modules that are on the QVL have been tested to work when overclocked

My particular modules product number is on the QVL for the motherboard, more by luck than design as this is the first I have heard of it, but they are there. It seems kind of funky that they shouldn't work at higher speeds considering all the hardware supports it, I did wonder if it was a Linux issue...

---

### Post by Yellow Pasque on 2020-10-21
> I did wonder if it was a Linux issue
Set the DOCP and boot into Memtest. If Memtest checks out, it may be an OS-specific problem. If Memtest fails, you are looking at a hardware issue. You can also try one stick at a time if you don't feel like bothering with Memtest.
You could also try setting speed/latency manually in case the mobo is not detecting the settings properly. Finally, you could try a small RAM and/or CPU voltage bump to see if that helps.

---

### Post by jcdenton1995 on 2020-10-21
> **Yellow Pasque said:**
> You could also try setting speed/latency manually in case the mobo is not detecting the settings properly.

I have tried setting the speed and voltage manually but when I did so I didn't manually set the timings, as I'm not quite sure what they should be. I'll have a look online at how I would set about calculating them

 > Finally, you could try a small RAM and/or CPU voltage bump to see if that helps.

Do you mean 1.35v plus? that is the maximum that the BIOS states you should use, but I know people go higher, I'm loathe to push it higher myself at the moment as I really don't know what I'm doing with it and don't want to break my RAM :)

Also yes I will look into Memtest!

---

### Post by Yellow Pasque on 2020-10-21
If it's this kit, it's rated to run at full speed at 1.40V anyway:
[https://www.gskill.com/specification/165/326/1562839114/F4-3600C14Q-32GTZN-(EOL)-Specification](https://www.gskill.com/specification/165/326/1562839114/F4-3600C14Q-32GTZN-(EOL)-Specification)

---

### Post by jcdenton1995 on 2020-10-22
> **Yellow Pasque said:**
> If it's this kit, it's rated to run at full speed at 1.40V anyway:
[https://www.gskill.com/specification/165/326/1562839114/F4-3600C14Q-32GTZN-(EOL)-Specification](https://www.gskill.com/specification/165/326/1562839114/F4-3600C14Q-32GTZN-(EOL)-Specification)

Very close, but it's this kit, and is only rated to 1.35v. Furthermore the BIOS apparently wont allow me to bump it above 1.35v at all...

[https://gskill.com/specification/165/326/1562840525/F4-3600C18D-32GTZN-Specification](https://gskill.com/specification/165/326/1562840525/F4-3600C18D-32GTZN-Specification)

---

### Post by jcdenton1995 on 2020-10-22
So I set the DOCP profile and then manually turned the memory frequency down to 2933MHz and ran MemTest for a total of four, passes and after about seven hours it reported no errors. I also tried setting the timings manually and loosening them by a couple of units each but still the same symptoms when I try to boot. I can't boost the memory voltage any more than 1.35 as the BIOS won't allow it. The only thing I haven't tried is boosting the CPU voltage as I'm unsure how much to increment it by.

I'm considering downloading and booting Windows to see if it has the same issue, at which point if it does I can start by contacting ASUS/G.Skill/AMD (I'm not sure who would actually be best, probably ASUS) and seeing what they have to add...

---

### Post by CatKiller on 2020-10-22
> **jcdenton1995 said:**
> My particular modules product number is on the QVL for the motherboard, more by luck than design as this is the first I have heard of it, but they are there. It seems kind of funky that they shouldn't work at higher speeds considering all the hardware supports it, 

If it's on the QVL but doesn't actually work at the speed it's supposed to, I would return it as faulty. 

> I did wonder if it was a Linux issue...

It wouldn't be a Linux issue as such, since it's hardware doing hardware things, but Linux does sometimes expose flaws in hardware implementations that manufacturers haven't bothered to test for. Some Ryzen platforms always returning -1 as their "totally random" number comes to mind.

---

### Post by Yellow Pasque on 2020-10-22
> **jcdenton1995 said:**
> So I set the DOCP profile and then manually turned the memory frequency down to 2933MHz and ran MemTest for a total of four, passes and after about seven hours it reported no errors.

Why did you turn it down to 2933? The idea was to test it at 3600.

---

### Post by CelticWarrior on 2020-10-22
According to the [motherboard's specifications]("https://www.asus.com/Motherboards/ROG-Strix-X570-I-Gaming/specifications/"), some memory modules can indeed work at higher speeds but that won't happen OOB, it needs over-clocking.

> [COLOR=#A0A0A0][FONT=&quot]2nd Gen AMD Ryzen&#8482; and 3rd Gen AMD Ryzen&#8482; with Radeon&#8482; Graphics Processors[/FONT][/COLOR]
[COLOR=#A0A0A0][FONT=&quot]2 x DIMM, Max. 64GB, DDR4 3600(O.C.)/3466(O.C.)/3400(O.C.)/3200(O.C.)/3000(O.C.)/2933/2800(O.C.)/2666/2400/2133 MHz Non-ECC, Un-buffered Memory *[/FONT][/COLOR]

Without OC any RAM there with your CPU+GPU - 3rd Gen Ryzen with Radeon GPU - will work at 2666MHz. Any higher and if supported by the RAM (it is) in your particular hardware configuration is only achievable by enabling OC in the motherboard, i.e., "auto" settings, the default, can't be ised. How to do that should be explained in the user's manual.

---

### Post by jcdenton1995 on 2020-10-22
> **Yellow Pasque said:**
> Why did you turn it down to 2933? The idea was to test it at 3600.

My processor only supports RAM speeds up to 2933MHz, so I thought I would just get lots of errors if I ran it at the full 3600MHz?

---

### Post by Yellow Pasque on 2020-10-22
> **jcdenton1995 said:**
> My processor only supports RAM speeds up to 2933MHz

Sorry, I misread your post. I thought Ubuntu would start correctly at 2933. Officially, the max speed is 2933, but these CPU's are known to go higher without issue, which is why kits that can be "overclocked" by simply flipping on XMP are widely available. My 2400G (same official 2933 limit) works fine with the 3200 kit I got.
The fact that Memtest ran okay at 2933 suggests it may be related to the OS. I think trying out Windows (even if you just boot into the installer and don't install it because you don't have a license) is a good idea.
Trying out Xubuntu 20.10 on a LiveUSB is also a good idea: [http://cdimage.ubuntu.com/xubuntu/releases/groovy/release/xubuntu-20.10-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/groovy/release/xubuntu-20.10-desktop-amd64.iso.torrent)

---

### Post by jcdenton1995 on 2020-10-22
> **Yellow Pasque said:**
> Sorry, I misread your post. I thought Ubuntu would start correctly at 2933. Officially, the max speed is 2933, but these CPU's are known to go higher without issue, which is why kits that can be "overclocked" by simply flipping on XMP are widely available. My 2400G (same official 2933 limit) works fine with the 3200 kit I got.

Maybe I'll push it further once I get it going, I'm still in that stage of the computer being quite new so I'm being all soft on it, but it's only a matter of time before that wears off!

> The fact that Memtest ran okay at 2933 suggests it may be related to the OS. I think trying out Windows (even if you just boot into the installer and don't install it because you don't have a license) is a good idea.
Trying out Xubuntu 20.10 on a LiveUSB is also a good idea: [http://cdimage.ubuntu.com/xubuntu/releases/groovy/release/xubuntu-20.10-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/groovy/release/xubuntu-20.10-desktop-amd64.iso.torrent)

This was my plan for Windows as I thought another Distribution would essentially be the same deal due to also using the Linux kernel, although I appreciate there are many versions / custom kernels. I'll try Xubuntu now to see how that fairs and report back!

**Edit: Xubuntu also won't boot, guess it's time to parley with the dreaded windows... briefly. **

---

### Post by CatKiller on 2020-10-22
> **jcdenton1995 said:**
> I'll try Xubuntu now to see how that fairs and report back!

For a test that would show you whether it's an issue that's been fixed by newer kernels, trying to boot a 20.10 image would be more indicative than a different flavour of 20.04.

---

### Post by Yellow Pasque on 2020-10-22
> **CatKiller said:**
> trying to boot a 20.10 image would be more indicative than a different flavour of 20.04.

That's why the link I provided was for 20.10.

---

### Post by jcdenton1995 on 2020-10-23
> **Yellow Pasque said:**
> That's why the link I provided was for 20.10.

> **CatKiller said:**
> For a test that would show you whether it's an issue that's been fixed by newer kernels, trying to boot a 20.10 image would be more indicative than a different flavour of 20.04.

So after reading your comments I realised that I actually booted Xubuntu 20.04.1 LTS, so I followed Yellow Pasque's link and got the latest release. Unfortunately my PC won't boot that at all, the boot screen (I'm sure there is a technical term) basically told me that the compressed initramfs had some junk in there and also an init process couldn't be found. I did check the sha256sum and it matched but I cant rule out user error here (me).

Anywho tried booting the Windows 10 x64 installer and it boot's fine with the ram set at 2133MHz but wouldn't play ball at 2933MHz with DOCP. So I think I'm going to take your advice CatKiller and contact G Skill, possibly exchanging it for another set or just getting a refund. A bit of a bummer because it means I'll need to pick up some cheap modules just to slap in the PC to keep it going.

I guess before I do all that I'll check it's seated properly, but I'm 99% certain it is :(

**Edit: **So I checked the QVL for both the motherboard and the memory modules while I was writing out an E-mail to G Skill, I don't know how I got it wrong earlier in the thread, but neither component is on the QVL for the other. There are many almost identical modules on the QVL for the board, but only one entry in the entire list is a 2x 16GB pair like mine, which seems significant. Likewise the QVL for the modules lists the E-ATX and ATX iterations of the same board, but not the ITX version. I suppose this means I can't complain, which I'm not as at least now I can be confident I have a (slightly) incompatible product as opposed to a faulty one!

I have messaged G Skill technical support anyway so *if* I manage to sort it I will update for any future lurkers.

---

