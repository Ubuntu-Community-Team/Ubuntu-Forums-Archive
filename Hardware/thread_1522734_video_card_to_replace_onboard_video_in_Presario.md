---
title: "video card to replace onboard video in Presario"
date: 2010-07-02
forum: Hardware
---

### Post by Chuck_N on 2010-07-02
hi,
I have a compaq presario SR1503WM. The onboard graphics is not working well.
GLfiles won't run. And computer blacks out randomly, maybe once an hour.

I would like to buy a PCI video card to replace onboard graphics.

How do I find out what cards will do a good job with Ubuntu 10.04 LL in this machine?

Don't need super performance; would like to keep the cost under $50.

Thanks, CHuck

---

### Post by Chuck_N on 2010-07-06
hello,

I have a compaq presario SR1503WM. The onboard graphics is not working  well.
GLfiles won't run. And computer blacks out randomly, maybe once an hour.

I would like to buy a PCI video card to replace onboard graphics.

How do I find out what cards will do a good job with Ubuntu 10.04 LL in  this machine?

Don't need super performance; would like to keep the cost under $50.

Thanks, CHuck

---

### Post by cascade9 on 2010-07-07
I'm not 100% convinced its the video causing your problems, but sometimes you just have to try something and hope.....

Probably your best bet would be this (a PCI nVidia 8400GS)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814134073](http://www.newegg.com/Product/Product.aspx?Item=N82E16814134073)

BTW, link to the prouct specifications for anybody else viewing this thread- 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775)

---

### Post by Chuck_N on 2010-07-11
> **cascade9 said:**
> I'm not 100% convinced its the video causing your problems, but sometimes you just have to try something and hope.....
Probably your best bet would be this (a PCI nVidia 8400GS)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814134073](http://www.newegg.com/Product/Product.aspx?Item=N82E16814134073)
BTW, link to the prouct specifications for anybody else viewing this thread- 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775)

You're right Cascade, I may be wasting money.  But I ordered this card and it should be here Monday.

Where do I find info on how to install it ?

---

### Post by Chuck_N on 2010-07-12
okay, I received my GeForce 8400GS.
I did a GOOGLE and a Ubuntu search and can't find info on how to go about installing it, and disabling the onboard graphics.  Can someone point me in the right direction?

thanks, chuck

---

### Post by cascade9 on 2010-07-13
This could be interesting.....

I cant find any guides on the net, so I'm taking an educated guess. 

1st off, you should try to get into the BIOS. Hit the 'del' key as the computer is booting up. When you get in there, you will probably need to poke around fair bit to find the ioptino you are looking for. 

It should be labeled something like 'video initalise'. Or halfa  dozen other names. :| Sorry I can be more exact. 

What you need to see it the ability to cheange the video from 'onboard' to PCI slot'. The only hint I have is that if the option is there, it will probably be under the 'advanced' area. 

If there is an option to set the video from 'onboard' to 'PCI', then you can move on to teh next step. 

If that option is missing, it might still be possible to get the PCI card going, by blacklisting the i845 video. Hopefully it doesnt come to that. If you cant find the option, stop there and dont try to go any futher along. 

If you do have the option, now comes the screwdriver bit. Unplug the power, then take the cover off the case. Find a free PCI slot, the further away from any other PCI cards the better. BTW, if there is a PCI modem installed and you dont use dial-up, its not a bad idea to remove the modem and install the video card in the slot the modem was in.

Firmly and slowly insert the video card into the PCI slot. Replace the screw that holds the card in place, then replace the case cover. Reattach the power cord, and boot up. Go back into teh BIOS, then change the video from 'onbaord' to 'PCI'. Save and exit. 

Now, when the computer reboots move the VGA cable from the onbaord video output to the VGA output on the newly installed card. 

Your computer should now boot into linux, using the new card. Then go system-> administration-> hardware drivers, and get the nvidia drivers for your card (should be version 195.xx).Reboot, and your done! 

Good luck ;)

---

### Post by Chuck_N on 2010-07-13
this might be more than interesting........

instructions with the card (in maybe 8 languages) include nothing but "connect it up and go"

I'll take a look at BIOS and see what I can find.

---

### Post by Chuck_N on 2010-07-13
okay, I got into BIOS, Advanced..........
right now, Primary Video Adapter is set to PCI, not  Onboard.  I find that confusing.
Onboard video memory size is set to 8MB not 1 MB.
I did not find a  i845
Onboard 1394   is set to Enabled
Looks like 1394 is for Firewire or a SoundCard. I have neither. Should I disable it ?

---

### Post by AltomineUK on 2010-07-13
Hello there,

I use the 8400M GS on my laptop (which would be the mobile version, with reduced clock speed) and would like to say that it is a very good entry level card which is great for HD playback and casual photo/video editing as well as gaming. Proprietary drivers for this card should be available in your Linux system, that works!

As for changing your card on your computer, cascade9 has pretty much got it right, although you don't have to fiddle around in the BIOS until after you have made the change. You can use the BIOS to check everything....
Just unplug all the cables connected to your PC, take out one of the panel casings, find that PCI express slot, plug it in and go! (take care not to build up static!!!)

 May I point out that some motherboards automatically make the switch from onboard to discrete graphics upon detection. For example, in my case, I changed to an 6200 GS on my old desktop without mucking around the BIOS (although I had to make a check to make sure it was initialised properly).

---

### Post by Chuck_N on 2010-07-13
okay, I unplugged, took out the modem card, put the new video card in a different slot, cuz it would not fit well right by the wall.  Hooked up and started up.
Boot page okay.  GRUB page okay.
then many white-on-black lines looking like

14.857150    c0101 ald sys_execve + 0x2d/0x70

14.857224    c03530ca ?strncpy_from_user + 0x32/0x77

etc.

mouse and keyboard remained active, but I had no idea what I could/should do.....

not too sure what to try now...........

reminder, the BIOS video adapter already reads PCI not Onboard.

I am typing this from a different computer.     -Chuck

---

### Post by Chuck_N on 2010-07-13
was there some reason to follow this, literally
    [COLOR=Red]
Now, when the computer reboots move the VGA cable from the onbaord video output to the VGA output on the newly installed card[/COLOR].

I mean, I switched to the card b4 I booted.  Any problem with that?


So, since it blows up, I can't follow this instruction

[COLOR=Red]Your computer should now boot into linux, using the new card. Then go system-> administration-> hardware drivers, and get the nvidia drivers for your card (should be version 195.xx).Reboot, and your done! [/COLOR]

---

### Post by Yellow Pasque on 2010-07-13
So are you logged into a terminal? If so:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04)

---

### Post by cascade9 on 2010-07-14
> **AltomineUK said:**
> As for changing your card on your computer, cascade9 has pretty much got it right, although you don't have to fiddle around in the BIOS until after you have made the change. You can use the BIOS to check everything....
 Just unplug all the cables connected to your PC, take out one of the panel casings, find that PCI express slot, plug it in and go! (take care not to build up static!!!)
 
 May I point out that some motherboards automatically make the switch from onboard to discrete graphics upon detection. For example, in my case, I changed to an 6200 GS on my old desktop without mucking around the BIOS (although I had to make a check to make sure it was initialised properly).
 
 No PCI-e slot in this machine. ITs nowhere near new enough....
 
 I perfer doing the BIOS stuff before installing the card, and that is what I advise other people to do. If you know that the compuer will initilise the PCI video, and you've set it to that, then you can install the card, start and get the video on teh card from the get-go. If there is no way to initilise the video card, and you change over and hook up the VGA/DVI cable to the card (which is logical IMO) then in at least some cases you wont get any video at all..... 
 
 > **Chuck_N said:**
> okay, I got into BIOS, Advanced..........
  right now, Primary Video Adapter is set to PCI, not  Onboard.  I find that confusing.
  Onboard video memory size is set to 8MB not 1 MB.
  I did not find a  i845
  Onboard 1394   is set to Enabled
  Looks like 1394 is for Firewire or a SoundCard. I have neither. Should I disable it ?
  
  I've seen i845 chipsets come with onboard, AGP and PCI as the 'default' display adapter. From what I know, in most cases if the motherboard fails to find the a video card on whatever the defualt setting is, it tries the others. 
  
  I'm not suprised you dont find 'i845' mentioned in the BIOS. Its the chipset, it just happens to have the video 'card' intergrated in the chipset. If there was no way to make the PCI video card default in the chipset, blacklisting i845 *should* allow you to use the video card. Not that is an issue...thankfully. I've never had to blacklist anything yet, so I'm not up on doing that. ;) 
  
  1394 should be firewire. If you dont have any firewire devices, you can safely disable it. I tend to disable as much as possible in the BIOS (thinks like serial ports, parallel ports, sound if I'm using sound card, etc) to make booting slightly faster, load less modules in the OS, etc.. You dont have to do that, its just my perfered way of doing things. 

> **Chuck_N said:**
> okay, I unplugged, took out the modem card, put the new video card in a different slot, cuz it would not fit well right by the wall. Hooked up and started up.
Boot page okay.  GRUB page okay.
then many white-on-black lines looking like

14.857150    c0101 ald sys_execve + 0x2d/0x70

14.857224    c03530ca ?strncpy_from_user + 0x32/0x77

etc.

mouse and keyboard remained active, but I had no idea what I could/should do.....

not too sure what to try now...........

reminder, the BIOS video adapter already reads PCI not Onboard.

I am typing this from a different computer.     -Chuck

Well, you are getting the boot page and GRUB, which is good. I hope that Temüjins advice work (thanks BTW) 

It might not load to a console automatically....and since I havent tried this with ubuntu, I'm not sure it will work, but with some other distros if you hit "ctrl + alt + F1" you should drop down to a console. 

> **Chuck_N said:**
> was there some reason to follow this, literally
    [COLOR=Red]
Now, when the computer reboots move the VGA cable from the onbaord video output to the VGA output on the newly installed card[/COLOR].

I mean, I switched to the card b4 I booted.  Any problem with that?


So, since it blows up, I can't follow this instruction

[COLOR=Red]Your computer should now boot into linux, using the new card. Then go system-> administration-> hardware drivers, and get the nvidia drivers for your card (should be version 195.xx).Reboot, and your done! [/COLOR]

Blame me for wording that badly. You didnt have the 'boot then move the cable over' Sorry about that misunderstanding. 

I spose I should have said "Firmly and slowly insert the video card into the PCI slot. Replace the screw that holds the card in place, then replace the case cover. Reattach the power cord, and boot up. Go back into the BIOS, then change the video from 'onbaord' to 'PCI'. Save and exit.

Now, while the computer reboots move the VGA cable from the onboard video output to the VGA output on the newly installed card."

If Temüjins adviced doesnt work....I'd try a liveCD. I'm pretty certain that your issue is because ubuntu is trying to find i845 video, and since it cant find one its having a little bit of a freak out.

---

### Post by AltomineUK on 2010-07-14
> **cascade9 said:**
> No PCI-e slot in this machine. ITs nowhere near new enough....
 
 I perfer doing the BIOS stuff before installing the card, and that is what I advise other people to do. If you know that the compuer will initilise the PCI video, and you've set it to that, then you can install the card, start and get the video on teh card from the get-go. If there is no way to initilise the video card, and you change over and hook up the VGA/DVI cable to the card (which is logical IMO) then in at least some cases you wont get any video at all..... 
 
 
  
  I've seen i845 chipsets come with onboard, AGP and PCI as the 'default' display adapter. From what I know, in most cases if the motherboard fails to find the a video card on whatever the defualt setting is, it tries the others. 
  
  I'm not suprised you dont find 'i845' mentioned in the BIOS. Its the chipset, it just happens to have the video 'card' intergrated in the chipset. If there was no way to make the PCI video card default in the chipset, blacklisting i845 *should* allow you to use the video card. Not that is an issue...thankfully. I've never had to blacklist anything yet, so I'm not up on doing that. ;) 
  
  1394 should be firewire. If you dont have any firewire devices, you can safely disable it. I tend to disable as much as possible in the BIOS (thinks like serial ports, parallel ports, sound if I'm using sound card, etc) to make booting slightly faster, load less modules in the OS, etc.. You dont have to do that, its just my perfered way of doing things. 



Well, you are getting the boot page and GRUB, which is good. I hope that Temüjins advice work (thanks BTW) 

It might not load to a console automatically....and since I havent tried this with ubuntu, I'm not sure it will work, but with some other distros if you hit "ctrl + alt + F1" you should drop down to a console. 



Blame me for wording that badly. You didnt have the 'boot then move the cable over' Sorry about that misunderstanding. 

I spose I should have said "Firmly and slowly insert the video card into the PCI slot. Replace the screw that holds the card in place, then replace the case cover. Reattach the power cord, and boot up. Go back into the BIOS, then change the video from 'onbaord' to 'PCI'. Save and exit.

Now, while the computer reboots move the VGA cable from the onboard video output to the VGA output on the newly installed card."

If Temüjins adviced doesnt work....I'd try a liveCD. I'm pretty certain that your issue is because ubuntu is trying to find i845 video, and since it cant find one its having a little bit of a freak out.

Hmmm..... the 8400 GS has two versions: a PCI-e and PCI compatible ...... connecting the card to any lower spec slots will cause errors... 

 If you are talking about  older PCs with no PCI-e or PCI then I would recommend something that will use an AGP slot, as this is commonly found on old PCs. (Each slot has its name written right next to them on the motherboard.)

And no, I did not have to do any setup on the BIOS settings for the motherboard to automatically make the change from onboard to PCI.  I only checked it to make sure.

---

### Post by cascade9 on 2010-07-14
> **AltomineUK said:**
> Hmmm..... the 8400 GS has two versions: a PCI-e and PCI compatible ...... connecting the card to any lower spec slots will cause errors... 

 If you are talking about  older PCs with no PCI-e or PCI then I would recommend something will use an AGP slot, as this is commonly found on old PCs. (The names of all these slots can be found on the motherboard right next the slots.)

And no, I did not have to do any setup on the BIOS settings for the motherboard to automatically make the change from onboard to PCI.  I only checked it to make sure.

You cant connect a PCIe card to a non-PCIe, slot, etc.. Well, you might be able to with a deremel and/or a hamer. ;) 

This computer has PCI slots, but no AGP, and the card is PCI. Thats why I put a link to the specs in my 1st post here, so people didnt suggest things that wont work. Here it is again-

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775)

PCI is on far more computers than AGP, it appears well before AGP and has continued far after AGP got discontinued. I've never yet seen a motherboard with AGP that doesnt have PCI slots. 

These days PCI cards are a better choice for non-gamers than AGP. You can only get (new) very obsolete nVidia AGP cards (they did go to 7XXX with AGP, but trying find even a 6XXX nVidia AGP card new these days...), and borderline obsolete ATI cards. 

You might not have had to play with the BIOS, but have you tried on an i845? I doubt it. I have (there are 2 i845 motherbaords sitting around here). Newer compuiters react VERY differently to older computers as far as that sort of thing goes....

---

### Post by AltomineUK on 2010-07-14
> **cascade9 said:**
> You cant connect a PCIe card to a non-PCIe, slot, etc.. Well, you might be able to with a deremel and/or a hamer. ;) 

This computer has PCI slots, but no AGP, and the card is PCI. Thats why I put a link to the specs in my 1st post here, so people didnt suggest things that wont work. Here it is again-

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775)

PCI is on far more computers than AGP, it appears well before AGP and has continued far after AGP got discontinued. I've never yet seen a motherboard with AGP that doesnt have PCI slots. 

These days PCI cards are a better choice for non-gamers than AGP. You can only get (new) very obsolete nVidia AGP cards (they did go to 7XXX with AGP, but trying find even a 6XXX nVidia AGP card new these days...), and borderline obsolete ATI cards. 

You might not have had to play with the BIOS, but have you tried on an i845? I doubt it. I have (there are 2 i845 motherbaords sitting around here). Newer compuiters react VERY differently to older computers as far as that sort of thing goes....

Mate, please read carefully what I posted before commenting on them.... whereabouts in my post did I say that you can mix and match your PCI and PCI-e and AGP connections. Please don't be silly....hammers can only do one thing to your graphics card... break it.

Yes, i'm aware of the capabilities of the Accelerated Graphics Ports but AGPs have some capable advantages over a PCI. However, I will admit to the fact that I wasn't aware of the PC specification that you had kindly posted.....sorry and therefore AGP is out of question in this post.

As for finding an AGP, you'll be surprised at the availability of such cards. I found loads on Amazon...(ranging from the entry level 6200 to 6800s as well as high end 7XXX series) Obviously you are underestimating the AGP. The only reasons for discontinuity is because PCI has better availability on PCs and it is very flexible when used with multiple PCI and AGP cards. 

  Finally, even for non-gamers, PCI-Express is way better than PCI (unless the motherboard does not support PCI-e). Even AGPs can perform better than a PCI. AGPs provide a dedicated bandwidth compared to PCI bus. I am sure you know that even PCI is a bit outdated and entry level PCI-e cards are inexpensive.

And please don't doubt....my old PC runs on a Pentium 4 as well....

---

### Post by Yellow Pasque on 2010-07-14
> **AltomineUK said:**
> old PC's (9-10 years old) all have AGP as well PCI.
I've seen plenty of computers like the OP's where they have an Intel IGP and no AGP slot (to cut costs). Don't make ASSumptions ;)

---

### Post by cascade9 on 2010-07-14
> **AltomineUK said:**
> Mate, please read carefully what I posted before commenting on them....

Not being rude, but for somebody to say this, but totally miss the post where the motherboard specs were posted is amusing :P 

> **AltomineUK said:**
> whereabouts in my post did I say that you can mix and match your PCI and PCI-e and AGP connections. Please don't be silly....hammers can only do one thing to your graphics card... break it.

Have a re-read of what you said- 

> **AltomineUK said:**
> Hmmm..... the 8400 GS has two versions: a PCI-e and PCI compatible ...... connecting the card to any lower spec slots will cause errors... 

I was just stating in a semi-joking manner that it would be impossible to conenct at PCI card to a non-PCI slot without doing some serious 'mods' that would kill the poor thing. (though it would fit into an ISA slot, but it wouldn't actually connect) 

> **AltomineUK said:**
> Yes, i'm aware of the limited capabiities of the Auxiliary Graphics Ports but old PC's (9-10 years old) all have AGP as well PCI. I can only assume the reason for you not having seen one ever in your life is because you haven't owned a motherboard that has one. However, I will admit to the fact that I wasn't aware of the PC specification that you had kindly posted.....sorry

No, they dont all have AGP as well as PCI. Lots of motherboards with PCI and no AGP. (and the motherboard that Chunk_N has is just one example) 

what I was saying is what I said- I've never seen a motherboard with an AGP that doesnt have PCI slots as well. If you can find my a motherboard pic, or even specs, that does have an AGP but no PCI sots I'll be impresed ;) 

As for "haven't owned a motherboard that has one" (and I assume that you mean AGP) LMAO. I've got 5+ of them here, now. 

> **AltomineUK said:**
> As for finding an AGP, you'll be surprised at the availability of such cards. I found loads on Amazon...(ranging from the entry level 6200 to 6800s as well as high end 7XXX series) Obviously you are underestimating the AGP. 

AGP nVidia cards only go to 7600GT/7800GS. I wouldnt have called the 7600 seires 'high end' even when new (that would have been 7800GT and higher, the 7600s are 'midrange' cards). The 8XXX cards actually suport VDPAU, where the 7XXX cards dont. Which is why I believe that for a non-gamer, PCI nVida cards are better than AGP nVidia cards.  

True, there are 7600GTs on amazon...for aprox $60+. A 7600GT AGP isnt going to do anythign that a PCI 8400 wont do for desktop use, and it will eat more power, and create more heat. As for the 7800GS- I found 1, and its $250. Which is a sick joke. 

[http://www.amazon.com/256-A8-N506-AX-e-GeForce-7800-256MB-EVGA/dp/B003LLQYRI/ref=sr_1_1?s=pc&ie=UTF8&qid=1279101078&sr=1-1](http://www.amazon.com/256-A8-N506-AX-e-GeForce-7800-256MB-EVGA/dp/B003LLQYRI/ref=sr_1_1?s=pc&ie=UTF8&qid=1279101078&sr=1-1)

I never check amazon, and while there are more AGP cards there than I thought there would be, I'd call the 7XXX nVidia cards at *least* slightly obsolete. Not quite as badly obsolete as the 6XXX, FX and lower cards that are all over newegg in AGP though. 

> **AltomineUK said:**
> And finally, even for non-gamers, PCI-Express is way better than PCI (unless the motherboard does not support PCI-e). I am sure you know that even PCI is a bit outdated and entry level PCI-e cards are inexpensive.

Yeah, I know, and I've told that to Chunk_N in a different thread. PCIe 8400s are about 1/2 the cost of a PCI 8400. Since his motherboard only has PCI slots, its academic anyway.....

---

### Post by AltomineUK on 2010-07-14
> **cascade9 said:**
> Not being rude, but for somebody to say this, but totally miss the post where the motherboard specs were posted is amusing :P 



Have a re-read of what you said- 



I was just stating in a semi-joking manner that it would be impossible to conenct at PCI card to a non-PCI slot without doing some serious 'mods' that would kill the poor thing. (though it would fit into an ISA slot, but it wouldn't actually connect) 



No, they dont all have AGP as well as PCI. Lots of motherboards with PCI and no AGP. (and the motherboard that Chunk_N has is just one example) 

what I was saying is what I said- I've never seen a motherboard with an AGP that doesnt have PCI slots as well. If you can find my a motherboard pic, or even specs, that does have an AGP but no PCI sots I'll be impresed ;) 

As for "haven't owned a motherboard that has one" (and I assume that you mean AGP) LMAO. I've got 5+ of them here, now. 



AGP nVidia cards only go to 7600GT/7800GS. I wouldnt have called the 7600 seires 'high end' even when new (that would have been 7800GT and higher, the 7600s are 'midrange' cards). The 8XXX cards actually suport VDPAU, where the 7XXX cards dont. Which is why I believe that for a non-gamer, PCI nVida cards are better than AGP nVidia cards.  

True, there are 7600GTs on amazon...for aprox $60+. A 7600GT AGP isnt going to do anythign that a PCI 8400 wont do for desktop use, and it will eat more power, and create more heat. As for the 7800GS- I found 1, and its $250. Which is a sick joke. 

[http://www.amazon.com/256-A8-N506-AX-e-GeForce-7800-256MB-EVGA/dp/B003LLQYRI/ref=sr_1_1?s=pc&ie=UTF8&qid=1279101078&sr=1-1](http://www.amazon.com/256-A8-N506-AX-e-GeForce-7800-256MB-EVGA/dp/B003LLQYRI/ref=sr_1_1?s=pc&ie=UTF8&qid=1279101078&sr=1-1)

I never check amazon, and while there are more AGP cards there than I thought there would be, I'd call the 7XXX nVidia cards at *least* slightly obsolete. Not quite as badly obsolete as the 6XXX, FX and lower cards that are all over newegg in AGP though. 



Yeah, I know, and I've told that to Chunk_N in a different thread. PCIe 8400s are about 1/2 the cost of a PCI 8400. Since his motherboard only has PCI slots, its academic anyway.....

And once again you have refused to read my posts thoroughly...... I had clearly apologised for my poor observational skills and for some reason you have found that rude (please don't ask further questions on that matter...I am begging you to read first...) 

As for your academic decisions, again did I not mention that PCI-e should only be used "unless the mother board does not support PCI-e...". Although you made an excellent choice, I believe you were simply stating the obvious.

I think different amazon market places have different selections. For example the top end AGP model for the 7-series GPU available here is the 7950 GT. AGP was phased out after the 7XXX series and no, I never called any 7600's as high end (please read again...it's making me cry...) 

As for the 7-series being out of date, the Playstation 3 uses a 7800GTX that's been modified and re-branded as the RSX ( before you argue that this is not relevant, please look at the PS3 as a computer system.)

[http://www.amazon.co.uk/nVidia-GeForce-Graphics-Graphic-adapter/dp/B002I9FGTQ/ref=sr_1_1?ie=UTF8&s=electronics&qid=1279102049&sr=8-1](http://www.amazon.co.uk/nVidia-GeForce-Graphics-Graphic-adapter/dp/B002I9FGTQ/ref=sr_1_1?ie=UTF8&s=electronics&qid=1279102049&sr=8-1)

There is a reason for all the heat and power consumption. 7600GT is far more powerful than 8400 and will do more than just the desktop. And, obviously you should only choose a card that suits you. No point buying a $250 card if you just want to play flash games. I only stated all those GPUs to show the availabilities of the AGP. If you had read my first posts AGP was just an alternative option and I had shown my support for the 8400 GS.

Finally, you are simply replying to quickly before I edit my posts so some of those quotes you have quoted are out of date, so please read it again.

 And this post is turning into a GPU comparison site rather than being helpful to the man who has the problem, so moving to a different thread was a good move.

---

### Post by AltomineUK on 2010-07-14
> **Temüjin said:**
> I've seen plenty of computers like the OP's where they have an Intel IGP and no AGP slot (to cut costs). Don't make ASSumptions ;)

I'm not ASSuming -_-. There are many many many different computers that exists in this world, so you will find a lot of things missing and appearing in different models.... If you have only seen IGP ONLY models, fair enough....

---

### Post by Chuck_N on 2010-07-14
oh my looks like I have a lot to go through
and today is a bit busy for me.

well, from the bottom up.....

I rebooted and found the same thing:  through GRUB okay, then pages of that white text on black, as I referred to b4.   Following that the keyboard is completely active b ut I can get nothing to happen,  including    ctrl-alt-F1     I tried   ctrl-alt-everything and nothing happens.

---

### Post by Chuck_N on 2010-07-14
> **Temüjin said:**
> So are you logged into a terminal? If so:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04)

I guess not...........  I get just so far .....


If I get only to the GRUB menu,  then all the white lines on black,

how could I  "log into a terminal" ?

---

### Post by Chuck_N on 2010-07-14
I disabled 1394.


Now I put live CD in, and booted,  hit ESC

Ubuntu started up and gave that screen with one silly symbol at bottom middle
                          keyboard      =     man in circle

I hit space, as I've done b4

I then get  my  many pages of  white  text, and nothing more   

keyboard is NOT active,  cursor is rapid flashing at screen bottom

---

### Post by Chuck_N on 2010-07-14
[[COLOR=Red]QUOTE=AltomineUK;9587396]Hmmm..... the 8400 GS has two versions: a PCI-e and PCI compatible ...... connecting the card to any lower spec slots will cause errors... 

 If you are talking about  older PCs with no PCI-e or PCI then I would recommend something that will use an AGP slot, as this is commonly found on old PCs. (Each slot has its name written right next to them on the motherboard.)

And no, I did not have to do any setup on the BIOS settings for the motherboard to automatically make the change from onboard to PCI.  I only checked it to make sure.[/QUOTE][/COLOR]  

this cptr has three PCI slots. They are labeled  PCI slot 1,   PCI slot 2,  PCI slot 3.  What is AGP?

 I removed the modem card from slot 3.  I had some trouble trying to place the new video card in slot 3, by the wall, so I installed it in slot 1.  Should I relocate it?   -chuck

---

### Post by Chuck_N on 2010-07-14
> **cascade9 said:**
> 

Yeah, I know, and I've told that to Chunk_N in a different thread. PCIe 8400s are about 1/2 the cost of a PCI 8400. [COLOR=Red]Since his motherboard only has PCI slots, its academic anyway...[/COLOR]..

yep; now back to my machine.................

---

### Post by Chuck_N on 2010-07-14
okay, I moved the card to slot2
boot results the same; got to GRUB
got the white-lettered messages; many pages
    with rapid flashing cursor at the bottom;
no keyboard action; flashing capsLock and ScrollLock

tried again with  LiveUbuntu CD boot; same results

---

### Post by AltomineUK on 2010-07-14
Hello,

AGP is a discontinued bit of port/bus interface technology that was once found on motherboards. It came after the PCI. I am told your motherboard does not have an AGP slot so you don't have to worry about it.

I have just looked at your motherboard diagram it looks kinda old. It doesn't matter which PCI slot you plug in your graphics card into. So long as it says "PCI" and has the right number of pins it will work. 

May I ask you one thing? Can you successfully get to the GRUB menu before you start seeing all those flashes and colours or does it flash straight after it shows the BIOS screen without entering the GRUB menu? If you have answered this question in your posts, I am sorry I missed it......i'm a bit confused at the moment :S 

BTW The "Man in the Circle" symbols shows up when the PC is about to start loading the Linux kernel and boot Ubuntu.

---

### Post by Chuck_N on 2010-07-14
[COLOR=Red]> **AltomineUK said:**
> Hello,



May I ask you one thing? Can you successfully get to the GRUB menu before you start seeing all those flashes and colours or does it flash straight after it shows the BIOS screen without entering the GRUB menu? If you have answered this question in your posts, I am sorry I missed it......i'm a bit confused at the moment :S 

BTW The "Man in the Circle" symbols shows up when the PC is about to start loading the Linux kernel and boot Ubuntu.[/COLOR]    

started up.
Boot page okay.  GRUB page okay.
then many white-on-black printed lines looking like

14.857150    c0101 ald sys_execve + 0x2d/0x70
14.857224    c03530ca ?strncpy_from_user + 0x32/0x77
etc.

mouse and keyboard remained active, previously,  but lately have not.
the caps lock and scroll lock lights are flashing

Same things happen when I boot from liveCD

---

### Post by Chuck_N on 2010-07-14
sure would like to get this fixed today.  I have time to stay with it now.

and I'm getting  real tired  of this  Win2000 laptop.    :P

---

### Post by Chuck_N on 2010-07-14
hello................  anybody out there?

I spent some time looking up  capslock and  scrolllock  flashing;  didn't find out much.....

looks like it might mean various things; unsuccessful system loading for one.

not sure what to try next.

---

### Post by Yellow Pasque on 2010-07-14
Since you can access GRUB, can you boot to recovery mode?

---

### Post by Chuck_N on 2010-07-14
> **Temüjin said:**
> Since you can access GRUB, can you boot to recovery mode?

I selected  Recovery Mode
got my pages of white text on black background, having references to
error code
unpack,
node_mask
handle_fault
spin_lock_irq
etc.
then flashing cursor at the bottom with active keyboard....

---

### Post by Yellow Pasque on 2010-07-14
> I spent some time looking up capslock and scrolllock flashing
Kernel Panic. [http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/](http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/)

At this point, I am thinking bad card or you may not have a sufficent power supply.

---

### Post by Chuck_N on 2010-07-14
I connected my vga cable to my old Dell Inspiron that I've been using all day.
Windows 2000

what do you think?

worked like a champ. Didn't have to do a thing.  my Dell monitor looks wonderful.

Then I connected to the old connector on my Presario, the machine we're working on, to see if I can get output still from the onboard video.

Now I get NOTHING from that connection; black screen only.  I can't think of anything we've done that should make this happen.

Now I'm connected back to the new video card;  I got the many lines of white text, followed by a flashing cursor; active keyboard.

Would insufficient power cause the white lines of text like this?

Is anyone around that can look at the computer specs and indicate if this card would cause us to have insufficient power?

---

### Post by Chuck_N on 2010-07-14
okay, I need new advice and direction.

I removed the card altogether.  Now I can boot as I have for months, with the vga plugged in for onboard graphics.

Just a possibility: when I install the card there is a plugin line for the fan which is already plugged into the card itself. Am I supposed to pull this connector off, and plug it in on the motherboard somewhere?

How do I proceed here otherwise?  Call NewEgg for help or return?  Call Compaq for help?
Call GeForce?  Or what?

---

### Post by Yellow Pasque on 2010-07-15
This is your PSU: [http://www.power-on.com/atx12vem300bt.html](http://www.power-on.com/atx12vem300bt.html)
Considering that it's a generic 300W with only 15A on the 12V line, and you have a 3GHz Prescott core CPU, your PSU may very well be the problem.

Is there any way you can try the card in your Windows machine and use a LiveCD to see if the kernel panic occurs there?

---

### Post by cascade9 on 2010-07-15
> **Chuck_N said:**
> Then I connected to the old connector on my Presario, the machine we're working on, to see if I can get output still from the onboard video.

Now I get NOTHING from that connection; black screen only.  I can't think of anything we've done that should make this happen.

That happened because when your computer booted, it initalised the PCI video card, and since there was a video card present, it never turned on the intergrated video. 

> **Chuck_N said:**
> Now I'm connected back to the new video card;  I got the many lines of white text, followed by a flashing cursor; active keyboard.

Would insufficient power cause the white lines of text like this?

Is anyone around that can look at the computer specs and indicate if this card would cause us to have insufficient power?

If you've got a power problem, it tends to not cause this sort of thing. It can do, and dodgy hardware can be very hard to diagnose......very hard to know for sure without physical access, some tools and some experience. 

There should be enough power, but as power supplies age, the output they can oprovide drops, and that could be causing your problems (and it could have been the source of your instability all this time).

---

### Post by Chuck_N on 2010-07-15
[COLOR=Red]> **Temüjin said:**
> This is your PSU: [http://www.power-on.com/atx12vem300bt.html](http://www.power-on.com/atx12vem300bt.html)
Considering that it's a generic 300W with only 15A on the 12V line, and you have a 3GHz Prescott core CPU, your PSU may very well be the problem.

Is there any way you can try the card in your Windows machine and use a LiveCD to see if the kernel panic occurs there?[/COLOR] 

I do not have access to a second desktop, unfortunately, to test  if the card is bad.

I have no other cards or equipment installed in this computer. Could you be more exact  on the math; do I have insufficient power ?

The card is a PCI nVidia 8400GS  [http://www.newegg.com/Product/Produc...82E16814134073]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814134073")

according to THIS site,  [http://www.altex.com/%2FEVGA-e-GeForce-8400GS-512MB-PCI-Graphics-Card-512P1N724LR-P147810.aspx]("http://www.altex.com/%2FEVGA-e-GeForce-8400GS-512MB-PCI-Graphics-Card-512P1N724LR-P147810.aspx")
  **Requirements **
[LIST]
[*]Minimum of a 350 Watt power supply.    -  (Minimum recommended power supply with +12 Volt current rating of  18 Amps.)
[/LIST]


The link to the computer specifications - 

[http://h10025.www1.hp.com/ewfrf/wc/d...product=501775]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00363478&tmp_task=prodinfoCategory&lc=en&dlc=es&cc=pe&product=501775")

---

### Post by Chuck_N on 2010-07-16
I guess the links I gave didn't do so good for information.

From the label on my machine,

The power supply is  Bestec  atx-250-122-D

output is 250 watts max


and the card is a PCI nVidia 8400GS  which,

according to THIS site,  [http://www.altex.com/%2FEVGA-e-GeFor...R-P147810.aspx]("http://www.altex.com/%2FEVGA-e-GeForce-8400GS-512MB-PCI-Graphics-Card-512P1N724LR-P147810.aspx")
  **Requirements **
[LIST]
[*]Minimum of a 350 Watt power supply.    -   (Minimum recommended power supply with +12 Volt current rating of  18  Amps.)
[/LIST]
the +12 volt appears to say 14 amps.



I believe I cannot drive this video card with this power supply.  Do you concur?

---

### Post by cascade9 on 2010-07-18
250watts is a bit small...still, apart from the aging of the power supply it should run, the 8400GS dont use much power at all. 

Then again, you've been having problems for ages Chunk_N, its more than possible that your power supply has been the cause, the extra power draw of the 8400GS compared to the onboard i845might have been enough to move things from freezing to kernel panics. :(

---

### Post by Chuck_N on 2010-07-18
> **cascade9 said:**
> [COLOR=Red]250watts is a bit small...still, apart from the aging of the power supply it should run, the 8400GS dont use much power at all. [/COLOR]
Then again, you've been having problems for ages Chunk_N, its more than possible that your power supply has been the cause, the extra power draw of the 8400GS compared to the onboard i845might have been enough to move things from freezing to kernel panics. :(

I think a bit small, is like a little bit pregnant.  You either are, or you're not.

The card requires a powersupply of 300 or 350 watts, depending on where I looked.

How do I go about ordering a 350-watt supply that fits, and will work in my
Compaq Presario  SR 1503 WM ?  I think the machine is worth one more gamble.....

---

### Post by BritishEmperor on 2010-07-18
Wow!!! That PC is OLD!!!! I would probably get something well below an 8400 for something like that...... 

  But don't trust my words.....Research loads before choosing......

---

### Post by Chuck_N on 2010-07-18
you know, maybe what I need is a new BAREBONES with a good mobo and powersupply
and put my old DVD and other peripherals in there

---

### Post by BritishEmperor on 2010-07-18
> **Chuck_N said:**
> you know, maybe what I need is a new BAREBONES with a good mobo and powersupply
and put my old DVD and other peripherals in there

Lol I was gonna suggest that....

---

### Post by Chuck_N on 2010-07-18
hmmmmmm
hold that thought.
just stopped at STAPLES; they think the powersupply may be the culprit all along;
talked me into trying a 350w supply.  Easy install and test.
If it works fine then I'll install the video card.
If that then works, and I have good output, and no blackouts,  I'm home.
Else, it's the mobo, and I return the ps and videocard and think barebones.............

---

### Post by Chuck_N on 2010-07-18
okay guys, I need some serious help now...........

I had my fun; the power supply is installed: all fivehundred wires of so.  Just kidding.
Anyways, new for me; had me sweating.  But I earned my PowerSupply Merit Badge.

NOW...... ran fine for 1/2 hour or so. MAYBE no more blackouts.  Fingers crossed.
(and it is hard to type that way    8-)   )   However I got into the graphics-intensive GLS? screen saver, and it still blows up the system.

SO, I installed the graphics card.  Still, like b4, I get toGRUB okay, then a pause and lots of white text error messages, just as b4.  I powered down, connected blue video cord to the onboard but left the video card installed. Then I get no video.

Apparently something needs to be done to install that video card and get it to work.  Recall please that the BIOS already says to use the video card.

H E L P .....

---

### Post by cascade9 on 2010-07-18
> **Chuck_N said:**
> I think a bit small, is like a little bit pregnant.  You either are, or you're not.

The card requires a powersupply of 300 or 350 watts, depending on where I looked.


More like 'does this car put out 120 horse power, or does it not'? Maybe it did when it left the factory, but given a few tens of thousands kilometres (opps, miles) some bad petrol (opps, gas) and its not going to output the 120 it said in the sale brochure. 

Same thing happens to power supplies, given a few years, the capacitors start to get a bit old, and the power level avaible drops. 

As for the 300-350 minimum power supply, that is in part because of the way that power supplies 'age' and partly because some power supplies just put on a sticker saying whatever they think will sell that month.....nVidia set the minimum power supply levels with that in mind. 


> **Chuck_N said:**
> NOW...... ran fine for 1/2 hour or so. MAYBE no more blackouts.  Fingers crossed.
(and it is hard to type that way    8-)   )   However I got into the graphics-intensive GLS? screen saver, and it still blows up the system.

I would guess that is the i845 video bug. It shouldnt be the power supply. ;) 

Have youm tired turning off the screensaver and seeing if your old freezing problem comes back? If it doesnt, then I think that you've been having power supply issues all along. 

> **Chuck_N said:**
> SO, I installed the graphics card.  Still, like b4, I get toGRUB okay, then a pause and lots of white text error messages, just as b4.  I powered down, connected blue video cord to the onboard but left the video card installed. Then I get no video.

Back to kernel panics then I guess. 

You could try running from the liveCD, it might not help...but it should do. If you do have issues with the computer going into kernel panics/error messages with the liveCD then there might well be some problem with i845 + nVidia 8400 (its not a common combination). 

You're not having an easy time of things Chunk :(

---

### Post by Chuck_N on 2010-07-18
[COLOR=Red]Back to kernel panics then I guess. 
You could try running from the liveCD, it might not help...but it should do. If you do have issues with the computer going into kernel panics/error messages with the liveCD then there might well be some problem with i845 + nVidia 8400 (its not a common combination). 
You're not having an easy time of things Chunk

[COLOR=Black]Yes, let's assume new power supply is fine.

How do I find out about this potential conflict with i845 and nvidiaa 8400 ?

If I have video card IN but connected instead to onboard video, I get nothing to monitor.

With video card connected, if I go to boot menu and select DVD boot (Ubuntu),
  I get the screen with   keyboard  and  man-in-circle  at the bottom (I forget what that's called)   then if I hit  spacebar  as I have b4, I'm in trouble....pages of error messages in white on black.   
[/COLOR][/COLOR]

---

### Post by Chuck_N on 2010-07-18
I found this in a discussion group; is it any help ?

**  Xorg fails to start when using the nvidia kernel module **

 [link to this item]("http://fedoraproject.org/wiki/Common_F11_bugs#nvidia-vmalloc") - [Bugzilla: #489078]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=489078") 
Some users have reported that when attempting to use the "nvidia" kernel module (either the official installer or kmod-nvidia*) Xorg will fail to start properly. The end result, Fedora 11 boots to a black screen. Inspection of dmesg may reveal many messages similar to: 
 $ dmesg | grep vmap
vmap allocation for size 4198400 failed: use vmalloc=<size> to increase size.
vmap allocation for size 4198400 failed: use vmalloc=<size> to increase size.
A workaround is to add an entry to your kernel line in /etc/grub.conf that includes the amount of video memory on your nVidia card, for example for a 128 MB Geforce 8400 GS you would append the following: 
 vmalloc=128MB

---

### Post by Chuck_N on 2010-07-18
I found this midway through this thread. **_ I have not yet done anything about a driver _**(see the red section). If I read it correctly, it seems I can't do it ; when I boot up I can't get into the BIOS with the video card in.I'm really confused.
Is this of help ?:

Unplug the power, then take the cover off the case. Find a free PCI slot, the further away from any other PCI cards the better. BTW, if there is a PCI modem installed and you dont use dial-up, its not a bad idea to remove the modem and install the video card in the slot the modem was in.

Firmly and slowly insert the video card into the PCI slot. Replace the screw that holds the card in place, then replace the case cover. Reattach the power cord, and [COLOR=Black]boot up. Go back into the BIOS, [/COLOR]then change the video from 'onbaord' to 'PCI'. Save and exit. 

[COLOR=Red]Now, when the computer reboots move the VGA cable from the onbaord video output to the VGA output on the newly installed card. 

Your computer should now boot into linux, using the new card. Then go system-> administration-> hardware drivers, and get the nvidia drivers for your card (should be version 195.xx).Reboot, and your done! [/COLOR]

---

### Post by cascade9 on 2010-07-18
> **Chuck_N said:**
> [COLOR=Red][COLOR=Black]How do I find out about this potential conflict with i845 and nvidiaa 8400 ?[/COLOR][/COLOR]
 
 I checked around before I even suggested a 8400GS, I found nothing...I will have another look though. 

> **Chuck_N said:**
> I found this in a discussion group; is it any help ?

**  Xorg fails to start when using the nvidia kernel module **

 [link to this item]("http://fedoraproject.org/wiki/Common_F11_bugs#nvidia-vmalloc") - [Bugzilla: #489078]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=489078") 
Some users have reported that when attempting to use the "nvidia" kernel module (either the official installer or kmod-nvidia*) Xorg will fail to start properly. The end result, Fedora 11 boots to a black screen. Inspection of dmesg may reveal many messages similar to: 
 $ dmesg | grep vmap
vmap allocation for size 4198400 failed: use vmalloc=<size> to increase size.
vmap allocation for size 4198400 failed: use vmalloc=<size> to increase size.
A workaround is to add an entry to your kernel line in /etc/grub.conf that includes the amount of video memory on your nVidia card, for example for a 128 MB Geforce 8400 GS you would append the following: 
 vmalloc=128MB

Nice try, but no. That bug should only have affect people who actually got the nVidia drivers installed. 

> **Chuck_N said:**
> I found this midway through this thread. **_ I have not yet done anything about a driver _**(see the red section). If I read it correctly, it seems I can't do it ; when I boot up I can't get into the BIOS with the video card in.I'm really confused.
Is this of help ?:

Unplug the power, then take the cover off the case. Find a free PCI slot, the further away from any other PCI cards the better. BTW, if there is a PCI modem installed and you dont use dial-up, its not a bad idea to remove the modem and install the video card in the slot the modem was in.

Firmly and slowly insert the video card into the PCI slot. Replace the screw that holds the card in place, then replace the case cover. Reattach the power cord, and [COLOR=Black]boot up. Go back into the BIOS, [/COLOR]then change the video from 'onbaord' to 'PCI'. Save and exit. 

[COLOR=Red]Now, when the computer reboots move the VGA cable from the onbaord video output to the VGA output on the newly installed card. 

Your computer should now boot into linux, using the new card. Then go system-> administration-> hardware drivers, and get the nvidia drivers for your card (should be version 195.xx).Reboot, and your done! [/COLOR]

The reason why I told you to do it that way (check BIOS for PCI video initialisation, install the card, go back into BIOS, change to PCI video, reboot, move VGA cable) is because of pervious experience. I've had some peopel get into some odd positions from doing things different ways (the most common being the classic 'I installed the card, I pluged my VGA cable in, now I dont get any picute but the fans and stuff seem to be all working'). 

There are other reasons, but I'm to lazy to type them unless you really want to know. 

As for the video card/BIOS thing, its pretty easy once you get your head around it. 

If the BIOS is set to 'onboard' it (should) always boot with video running through the motherboard VGA port. 
If the BIOS is set to 'PCI' but there is no video card present, the video still goes though the motherboard VGA port. 
If the BIOS is set to 'PCI' and there is a PCI card present, all the video goes through that card, and teh onboard video is disabled.

You should be able get into the BIOS with the video card installed, no problems.

---

### Post by Chuck_N on 2010-07-19
I'm frustrated; maybe you are too.  Please try to stay with this....

If I understand correctly you would like me to repeat that same sequence:[COLOR=#000000][FONT=arial]
[/FONT][/COLOR][COLOR=#000000][FONT=arial]
[/FONT][/COLOR][COLOR=Red]Unplug the power, then take the cover off the case. Find a free PCI slot, the further away from any other PCI cards the better. BTW, if there is a PCI modem installed and you dont use dial-up, its not a bad idea to remove the modem and install the video card in the slot the modem was in.

Firmly and slowly insert the video card into the PCI slot. Replace the screw that holds the card in place, then replace the case cover. Reattach the power cord, and [/COLOR] [COLOR=Red]boot up. (A) _Go back into the BIOS, then change the video from 'onbaord' to 'PCI'. Save and exit. _

[/COLOR]  [COLOR=Red](B) Now, when the computer reboots move the VGA cable from the onbaord video output to the VGA output on the newly installed card. 

Your computer should now boot into linux, using the new card. Then go system-> administration-> hardware drivers, and get the nvidia drivers for your card (should be version 195.xx).Reboot, and your done! [/COLOR]


The problem is, once I get to point (A) (underlined) I can get into BIOS. There the Primary Video Adapter has always been set to PCI.  Incidentally, the Onboard Video Mem Size is set to 8 meg, only other option is 1 meg. I could find no mention of PCI device or memory allocation for PCI device.  Also Onboard 1394 is disabled (a change I made last week.) I think that is of no import here.
Now in the next paragraph, part B, when I reboot, at what point should I move the video cable to the new card?

---

### Post by cascade9 on 2010-07-19
> **Chuck_N said:**
> I'm frustrated; maybe you are too.  Please try to stay with this....

Understandable. I'm not the person with a computer thats playing silly buggers, that I find annoying...this is fairly distant, not in my face, so I really dont get that bothered by it. 

> **Chuck_N said:**
> If I understand correctly you would like me to repeat that same sequence:[COLOR=#000000][FONT=arial]
[/FONT][/COLOR][COLOR=#000000][FONT=arial]
[/FONT][/COLOR][COLOR=Red]Unplug the power, then take the cover off the case. Find a free PCI slot, the further away from any other PCI cards the better. BTW, if there is a PCI modem installed and you dont use dial-up, its not a bad idea to remove the modem and install the video card in the slot the modem was in.

Firmly and slowly insert the video card into the PCI slot. Replace the screw that holds the card in place, then replace the case cover. Reattach the power cord, and [/COLOR] [COLOR=Red]boot up. (A) _Go back into the BIOS, then change the video from 'onbaord' to 'PCI'. Save and exit. _

[/COLOR]  [COLOR=Red](B) Now, when the computer reboots move the VGA cable from the onbaord video output to the VGA output on the newly installed card. 

Your computer should now boot into linux, using the new card. Then go system-> administration-> hardware drivers, and get the nvidia drivers for your card (should be version 195.xx).Reboot, and your done! [/COLOR]


The problem is, once I get to point (A) (underlined) I can get into BIOS. There the Primary Video Adapter has always been set to PCI.  Incidentally, the Onboard Video Mem Size is set to 8 meg, only other option is 1 meg. I could find no mention of PCI device or memory allocation for PCI device.  Also Onboard 1394 is disabled (a change I made last week.) I think that is of no import here.
Now in the next paragraph, part B, when I reboot, at what point should I move the video cable to the new card?

1394 should make no difference at all. ;) 

No need to go through that whole sequence again. I just posted that as a '1st up' set of instructions. 

To make it easier for you, think of it like this- setting the video to 'PCI' is like a switch. If the switch is 'on' (video is set to PCI, and you have a PCI video card) then everything goes through the video card- from BIOS to booting. (well, not booting properly in this case, mores the pity). 

So as soon as you install the card, hook the VGA cable up to the card, you wont get any video from the motherboard. 

If you've tried with a liveCD and you still get the errors, then I dont think there is much you can do right now as far as the video card goes (but I'll think about it for a while, I'm kind of stupid today, bad sleep last night). You might want to try without the video card, disable screensavers (or set the screensaver to a blank screen, none of this graphical stuff) and see if you still get the freezing problem that started all this.

---

### Post by Chuck_N on 2010-07-19
I had a short-sleep night too.....

we seem to be going in circles.
I have not installed a driver.
If I have the 8400 card in, power on, I get to BIOS, then GRUB, then panic pages. No go.

How about if I take the card out, boot using onboard video. Can I somehow get the drivers installed, THEN put the 8400 card in?

---

### Post by cascade9 on 2010-07-20
> **Chuck_N said:**
> I had a short-sleep night too.....

we seem to be going in circles.
I have not installed a driver.
If I have the 8400 card in, power on, I get to BIOS, then GRUB, then panic pages. No go.

I dont think that you are going to have any lucj with running the 8400GS from the HDD with your current install. 

About all you can try is a liveCD and see if you still get errors. 

> **Chuck_N said:**
> How about if I take the card out, boot using onboard video. Can I somehow get the drivers installed, THEN put the 8400 card in?

You cant install the drivers without the card installed, but a modified version might be possible.

Boot with the card installed, go into BIOS, change from 'PCI' to 'onboard' and then see if it starts (BTW, when you boot with the card in, video should appear on the cards VGA port, but if you can change the video to 'onboard' it should change to the motherbaord VGA port when you reboot. Should, but I've seen i845 chipsets get that wrong in the past)

---

### Post by Chuck_N on 2010-07-26
okay, I give up
the video card and the power supply are being returned.

I'll consider this pursuit dead, not closed.

---

