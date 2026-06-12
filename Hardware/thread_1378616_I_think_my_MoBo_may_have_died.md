---
title: "I think my MoBo may have died"
date: 2010-01-11
forum: Hardware
---

### Post by madsporkmurderer on 2010-01-11
I returned to uni today and found that I could not get a network connection, further investigation has revealed some signs that I might have other problems.

The network socket/cable definitely work as a friend plugged her laptop in and it worked fine; when I plug in with my onboard ethernet nothing observable happens- not even the little green/orange lights.

When trying to boot into live disks to troubleshoot I've had a selection of worrying errors (lots if i/o ones and not found type ones (caused by the i/o problems?)) that stop it booting both from a 9.10 live disk and an old slackware based live distro that I had lying around.

When booted into the installed 9.10 it seems to work except the network (from what little I've done- it'll open amarok and play music alright, and let me have a play with the network settings to no avail)

I transported it chucked in a bag with a load of cables etc and no side on the case, meaning physical damage isn't out of the question; although I have had the MoBo out and can't see any obvious damage.

I've left it running memtest which when I left didn't show any errors- I assume if this continues it is a near guarantee that the ram is ok (and presumably the north bridge as well). Do the symptoms sound like a mobo problem? If so is there anything I can do short of replacing it (I'm not afraid to do a bit of bodging/something which may or may not work if it's broken anyway)? Is it likely to have taken any other components down with it?

The board is a GIGABYTE GA-N650SLI-DS4L; I've had a quick look on ebuyer and they don't sell them any more, nor do they seem to sell any SLI boards under a couple of hundred quid- I'm sure I didn't pay anything like that for it a couple of years ago.

Thanks a lot,
Mike

---

### Post by cascade9 on 2010-01-12
I/O errors and dead ethernet...hmm, its sure possible that something has gone wrong. 

Memtest running OK means you should have good RAM, chipset (basic functions anyway) and CPU. 'Should' being the opterative word. 

As for a replacement motherboard- I dont know the UK buying scene, so I dont know where to go. But from a look at ebuyer, it seems that they only stock the 'top end' nVidia LGA775 SLI chipsets (790i). If you can find a 750i SLI board, it should be a lot cheaper. IIRC _some_ Itnel 975x chipsets support SLI, but I would check before buying (of course, if you haven't got SLI, dont bother, just get any old LGA775 motherboard....but I assume you have SLI) 

You might find it cheaper to import if you can find something locally. Heres what newegg has in 750i-

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131232R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131232R)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131232](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131232)

---

### Post by madsporkmurderer on 2010-01-12
Thanks for that, unfortunately bad news- memtest has started finding errors. After about 18hours and 15 passes it had 76 errors; they seem to be mostly in the first 2GB stick, but a few in the other one. I assume the errors are too intermittent to swap the sticks to narrow the issue down to being the ram or mobo?

I don't strictly have SLI, but do have 4 monitors which requires 2 cards therefore 2 big PCI-e sockets.

Is this going to be some kind of horrible replacing things just to see if that fixes it? If that is the case would it end up paying the overcharging professionals because I wouldn't have to buy all the components to troubleshoot?

Thanks a lot,
Mike

---

### Post by cascade9 on 2010-01-13
> **madsporkmurderer said:**
> Thanks for that, unfortunately bad news- memtest has started finding errors. After about 18hours and 15 passes it had 76 errors; they seem to be mostly in the first 2GB stick, but a few in the other one. I assume the errors are too intermittent to swap the sticks to narrow the issue down to being the ram or mobo?

ITs going to be very hard to narrow things down without parts to swap in/out, sorry to say. Maybe somebody has a different idea, cause I've almost always got parts to swap around so thats the way I do it anyway. 

> **madsporkmurderer said:**
> I don't strictly have SLI, but do have 4 monitors which requires 2 cards therefore 2 big PCI-e sockets.

You should be able to run 1 card in PCI-E and another in PCI. If you've already to 2 PCI-E cards your happy with, then it would cost similar amounts to but a new  card a single PCI-E slot compared to 2xPCI-E slots. I'd keep what you have.  

> **madsporkmurderer said:**
> Is this going to be some kind of horrible replacing things just to see if that fixes it? If that is the case would it end up paying the overcharging professionals because I wouldn't have to buy all the components to troubleshoot?

Yeah, sorry to say, it very well could be. Personally, I do all my own computer hardware work, so I never have to pay some zitty kid silly amounts of money to poke at hardware. I actually enjoy poking around, so for me its a win/win. But if you dont enjoy it, or dont have (some) degree of skill then t could cost you more than buying a new computer. 

You might be better off getting a new machine. Or replacing the main system stuff and keeping your cards. Hardware is_very_ cheap now, and you would probably get a performance upgrade into the bargin.

---

### Post by madsporkmurderer on 2010-01-13
I do normally do all my own building/fixing- I'm also geeky enough to enjoy it :D the reason I considered a proffessional is that if the dodgy mobo has damaged the ram which then damages the new mobo costing me new ram plus 2 new mobos (or similar) it could end up being expensive; if it breaks some overcharging ripoff merchant's components it's not my problem. That said would it cost less to just replace mobo,ram & cpu (and possibly psu?)?

Or am I being overcautious about components damaging each other? I've heard stories about one of the main components going which can lead to the death of other components, is this common enough for me to not just try a new mobo?

You mention pci graphics, I was under the impression that it was good as phased out years ago simply due to a major bottlekneck on the pci bus; is it still a realistic option?

Thanks a lot,
Mike

---

### Post by madsporkmurderer on 2010-01-13
I piece of good news for once- after a bios reset and running on only 1 stick of ram memtest seems to be giving good results; it's been running about 3 hours (about 5 passes I think) and hasn't found any errors yet. Roughly how long should I leave it before I can be fairly sure that the ram/cpu are fine?

Network is still not responding at all, and I haven't tried a live boot yet; I would guess that there is something wrong on the southbridge meaning mobo replacement, but at least it looks like ram and cpu should be reusable.

Thanks,
Mike

---

### Post by cascade9 on 2010-01-13
> **madsporkmurderer said:**
> I do normally do all my own building/fixing- I'm also geeky enough to enjoy it :D the reason I considered a proffessional is that if the dodgy mobo has damaged the ram which then damages the new mobo costing me new ram plus 2 new mobos (or similar) it could end up being expensive; if it breaks some overcharging ripoff merchant's components it's not my problem. That said would it cost less to just replace mobo,ram & cpu (and possibly psu?)?

Or am I being overcautious about components damaging each other? I've heard stories about one of the main components going which can lead to the death of other components, is this common enough for me to not just try a new mobo?

I've heard similar tales, and truthfully they are rare. If your worried, yuo could just take your RAM to (some) computer shops, a lot of them have RAM testers that can tell you within munites if your RAM is fine, damaged or dead. In the instance I've heard those tales its either been a caused by a  _major_ issue like the power supply giving to many volts, or....er......well, below. 

I've actually had bad RAM kill my RAM slots. It was a very old pentium 1 motherboard, with 72pin (fast page/EDO) and 168pin (SD ram) slots. The SD ram slots were very tight, and one day while mucking around with RAM, and in a hurry, I pulled a tiny capacitor of the RAM while removing it. When I put it back in, my RAM wasnt detected. I changed RAM, still not working. After given both RAM sticks a lot of eyeball work, I realised what had happened. I was _not_ a happy camper. Going from 48MB (16MB EDO and 32MB SD) to 16MB (just my EDO) was painful. Win98SE hated me LOL.

One reason why I was happy to see heatspeaders become common with DDR1, and almost standard on DDR2. Its really hard to rip a cap off, or physically damage the RAM when there is nice heatsinking on the RAM.  

> **madsporkmurderer said:**
> You mention pci graphics, I was under the impression that it was good as phased out years ago simply due to a major bottlekneck on the pci bus; is it still a realistic option?

For gaming or serious 3D work? Nope, PCI is far to limited. For just general display duties, media playing or even hardware decoding (VDPAU) it works fine. 



> **madsporkmurderer said:**
> I piece of good news for once- after a bios reset and running on only 1 stick of ram memtest seems to be giving good results; it's been running about 3 hours (about 5 passes I think) and hasn't found any errors yet. Roughly how long should I leave it before I can be fairly sure that the ram/cpu are fine?

Network is still not responding at all, and I haven't tried a live boot yet; I would guess that there is something wrong on the southbridge meaning mobo replacement, but at least it looks like ram and cpu should be reusable.

Umm...depends on who you talk to. I've normally run Memtest overnight 'just to be sure'. Id check the otehr stick (single mode) as well. Its possible that your motherboard has lot dual channel RAM as well as network,and that could make Memtest give you one stick as bad. 

BTW, even if your RAM is bad, I would guess your CPU should be fine. Its booting, etc. 

*scratches head* Im not quite sure where to go from there. You've got a few choices. 

1- buy all new. Expensive, and leaves a bad taste in my mouth (and possibly yours)

2- get a new motherboard, cross fingers. 

3- take it into a shop, and ask them to change over to a new board.   

I'd probably check all your voltages in the BIOS, or with a multitester. A RAM test on the machine the shops use would be something else I would do, if they dont charge too much for the service. If your RAM is fine, then probably everything else, apart from your board, is as well. 

If thats fine, to be honest, I would risk a new motherboard. A cheap socket775 board would probably cost less than most shops would charge per hour, and they would probably charge more than 1 hour.

Just what I would do, dont think that is automatically the best choice for you ;)

---

