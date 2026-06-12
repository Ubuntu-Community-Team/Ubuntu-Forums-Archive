---
title: "Benefits of 64bit over 32bit"
date: 2009-05-11
forum: Hardware
---

### Post by thomasboleyn on 2009-05-11
Hi there, I am fairly un-savvy with pc hardware and don't understand a great deal about its inner workings, but am wondering whether it would be beneficial in any way for me to install a 64-bit version of a linux distro on my Sony Vaio VGN-NS20S/S ([http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-NS&m=7291&=0&=VGN-NS&=7291](http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-NS&m=7291&=0&=VGN-NS&=7291)).
I understand that with a Core 2 Duo processor I can hypothetically run a 64-bit OS, it's just I have never done so before, and have heard that you need 4 gigs of memory to really see any benefits (this laptop has 3). Would it be as simple as just burning a 64-bit version of a distro and installing it as I would a 32-bit one? 

Any help would be greatly appreciated.

---

### Post by Peter09 on 2009-05-11
In general a 64bit O/S is used when you need to address more than 4GB. However I use a 64 bit O/s on a machine with 2GB, I feel that it provides a small (marginal) measure of performance gain for no real loss.

So my moto was if you can why not.

---

### Post by roger_1960 on 2009-05-11
Hi

Yes, just burn the 64 bit version and install as usual.  You probably wont see the difference, but it should be a little quicker with intensive graphics and processing apps.

---

### Post by thomasboleyn on 2009-05-11
> **roger_1960 said:**
> Hi

Yes, just burn the 64 bit version and install as usual.  You probably wont see the difference, but it should be a little quicker with intensive graphics and processing apps.

Awesome, I'll try it out when I get home. I currently dual boot Windows 7 and Ubuntu Jaunty, both 32-bit, will this just be added to the initial grub menu as another OS would?

---

### Post by Peter09 on 2009-05-11
No reason why not :)

---

### Post by coffeecat on 2009-05-11
Just to add that I bought myself the identical laptop two or three weeks ago and I'm extremely pleased with it. Jaunty is running well on it. **Everything** 'just works' including the webcam. Well - I haven't tried the dial-up modem yet. :wink:

I went for the 32-bit version but I agree with the others. Just burn the 64-bit CD and install away.

One tip if you want to shrink the Vista partition. You probably know not to do that with Gparted, not if you want to boot into Vista again that is. You need to use the partition resize tool in Vista itself. However, when I tried this, Vista wouldn't reduce itself down to less that about 150GB, which is ridiculous. I tried [this guide]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"), but I couldn't get it to work for me. What I eventually did (which is probably safer than some of the tips in that guide) was to shrink the Vista C: partition to 150GB within Vista, leaving the rest of the HD unallocated. Then I ran the Vaio restore utility to reinstall Vista to the 150GB partition. After which Vista let me shrink it down to the 90GB I wanted. :roll: Then I was able to create another NTFS partition for shared data and my Linux partitons and install Jaunty.

Enjoy your Vaio.

**Edit:** just seen your second post which you posted as I was posting. Yes, I see you're running Windows 7, so my comments about shrinking Vista don't apply, but I'll leave them up anyway. Did you zap the Vaio restore partition as well as the Vista one, or did you just overwrite Vista with 7?

---

### Post by thomasboleyn on 2009-05-11
> **coffeecat said:**
> Just to add that I bought myself the identical laptop two or three weeks ago and I'm extremely pleased with it. Jaunty is running well on it. **Everything** 'just works' including the webcam. Well - I haven't tried the dial-up modem yet. :wink:

I went for the 32-bit version but I agree with the others. Just burn the 64-bit CD and install away.

One tip if you want to shrink the Vista partition. You probably know not to do that with Gparted, not if you want to boot into Vista again that is. You need to use the partition resize tool in Vista itself. However, when I tried this, Vista wouldn't reduce itself down to less that about 150GB, which is ridiculous. I tried [this guide]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"), but I couldn't get it to work for me. What I eventually did (which is probably safer than some of the tips in that guide) was to shrink the Vista C: partition to 150GB within Vista, leaving the rest of the HD unallocated. Then I ran the Vaio restore utility to reinstall Vista to the 150GB partition. After which Vista let me shrink it down to the 90GB I wanted. :roll: Then I was able to create another NTFS partition for shared data and my Linux partitons and install Jaunty.

Enjoy your Vaio.

**Edit:** just seen your second post which you posted as I was posting. Yes, I see you're running Windows 7, so my comments about shrinking Vista don't apply, but I'll leave them up anyway. Did you zap the Vaio restore partition as well as the Vista one, or did you just overwrite Vista with 7?

Yes I did, I couldn't stand the annoying Vaio firmware. I use GParted to delete partitions whenever I need to, and Bootrec with Fixmbr using the command prompt from the Windows 7 disc to repair afterwards whenever I play around. Windows 7 recognised all the drivers for everything when I installed it, instant aero, very impressive, you should give it a whirl.

On a seperate note, have you noticed that the fan is quite loud?

---

### Post by coffeecat on 2009-05-11
> **thomasboleyn said:**
> Yes I did, I couldn't stand the annoying Vaio firmware.

Yes, I know what you mean. :(

> **thomasboleyn said:**
>  Windows 7 recognised all the drivers for everything when I installed it, instant aero, very impressive, you should give it a whirl.

I've put W7 RC on one of my desktops, and very impressed with it I am - though I hate to say it. I might try your suggestion. When you say that it recognised all the drivers, do you mean to say the special Fn key combinations work? I was impressed by the way W7 autodetected my hardware and installed all the drivers for me. Almost as good as Linux. :p

> **thomasboleyn said:**
> On a seperate note, have you noticed that the fan is quite loud?

Yes, although it's not noticeable all the time. I guess it's varying depending on CPU load. I get the impression that it's better in Jaunty (against Vasta that's not surprising), but I haven't stressed the system with video encoding or something similar yet. Might be worth trying.

As an afterthought, if you go into your local Comet, they might have out a demo machine of a related model, the [VGN-NS20E/P]("http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-NS&m=7158"). It's worth a look because the photo in that link doesn't do it justice. You have to see it in the flesh to appreciate the sheer undiluted horror of that particular shade of pink. :shock:

---

### Post by thomasboleyn on 2009-05-11
> **coffeecat said:**
> Yes, I know what you mean. :(



I've put W7 RC on one of my desktops, and very impressed with it I am - though I hate to say it. I might try your suggestion. When you say that it recognised all the drivers, do you mean to say the special Fn key combinations work? I was impressed by the way W7 autodetected my hardware and installed all the drivers for me. Almost as good as Linux. :p



Yes, although it's not noticeable all the time. I guess it's varying depending on CPU load. I get the impression that it's better in Jaunty (against Vasta that's not surprising), but I haven't stressed the system with video encoding or something similar yet. Might be worth trying.

As an afterthought, if you go into your local Comet, they might have out a demo machine of a related model, the [VGN-NS20E/P]("http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-NS&m=7158"). It's worth a look because the photo in that link doesn't do it justice. You have to see it in the flesh to appreciate the sheer undiluted horror of that particular shade of pink. :shock:

I do quite a bit of encoding and converting movies to .wmv, as I have an Xbox 360 and a big flatscreen tv, so with Windows media centre I can watch films I download on it as it uses the Xbox as an extender. The fan does get very loud when encoding, it's just when it's idle it still seems quite loud. I guess I'm just sensitive to fan noises! (my old Vaio PCG-K215Z sounded like an absolute beast when it was on it's last legs).
I haven't seen it in pink, though I knew it was available. I really like how it looks sort of like the unibody macbook, and has a nice keyboard. I really can't stand cheap looking keyboards.

---

### Post by HavocXphere on 2009-05-11
> **thomasboleyn said:**
> have heard that you need 4 gigs of memory to really see any benefits (this laptop has 3). 
The main benefits lie in media processing, specifically video. There is a lengthy article about x64 on phoronix. btw I'm running x64 on a box with 2gb RAM. The gain in processing media is made with or without 4gb. It's kinda the other way round: If you have >4gb then you need x64 to see all the RAM...but having <4gb does not mean you can't run x64.

> **thomasboleyn said:**
> Would it be as simple as just burning a 64-bit version of a distro and installing it as I would a 32-bit one? 
Yes. I didn't notice any difference in installing x64 this time round. That being said, there can always be some weird issue that pops up unexpectedly due to certain hardware combinations.

---

### Post by coffeecat on 2009-05-11
> **HavocXphere said:**
> there can always be some weird issue that pops up unexpectedly due to certain hardware combinations.

[Yes, indeed.]("http://ubuntuforums.org/showthread.php?t=1155878") :( (Although not relevant to this thread.)

---

### Post by stchman on 2009-05-11
You paid for a 64 bit processor, why not use it to it fuller potential.

Kind of like getting a ZR-1 Corvette to drive to the mall.  Will it do it, yes, but better for the race track.

---

### Post by thomasboleyn on 2009-05-13
> **stchman said:**
> You paid for a 64 bit processor, why not use it to it fuller potential.

Kind of like getting a ZR-1 Corvette to drive to the mall.  Will it do it, yes, but better for the race track.

I've got it all up and running perfectly on a dual boot with Windows 7. Haven't encountered any problems whatsoever, though to be fair I have only installed things from repos and haven't compiled or used debs yet. Can feel a slight performance boost but need to do some video converting or something to see how that goes.

---

### Post by HavocXphere on 2009-05-13
> **coffeecat said:**
> [Yes, indeed.]("http://ubuntuforums.org/showthread.php?t=1155878") :( (Although not relevant to this thread.)
Admittedly I'm not to well informed on the nVidia front. Its good that you mentioned this...might save someone grief.

---

