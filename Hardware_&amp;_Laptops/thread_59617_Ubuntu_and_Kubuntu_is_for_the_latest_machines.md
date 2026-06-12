---
title: "Ubuntu and Kubuntu is for the latest machines"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by John.Michael.Kane on 2005-08-24
So ubuntu is only going to work on the latest and greatest machine. it seems every post on here has some user with a 64bit rig or the latest intel machine and its working. if its not working then everyone jumps in and helps. seems those with outdated laptops need not look for help . i dont get this.. so unless you have two thousand or four thousand dollar rigs ubuntu and kubuntu is not for you. people who are fed up with using ms programs and the os it's self, and choose to use this progam i guess they should understand that if their machine is old dont look for help. everyone for themself figure it out on your own then post how you did it ..

---

### Post by s_p_a_r_k_y on 2005-08-24
The problem being with that companies don't release drivers for linux so they have to be written by the community. THus the common machines/devices will often be supported because someone bought it who knows how to write drivers. Realy old laptops, before many used Linux often don't have drivers as you can't write a driver for a device you don't have and probably the most recent devices may not be supported unless they use common chipsets. Just how it is unless companies start to wise up and release to the linux community open source drivers when they release products

---

### Post by John.Michael.Kane on 2005-08-24
I guess if you say so.  everyone says this os works right out the box and it does not people should post things like this just to promote this os. then when someone comes here for help they make it seem like they need to be running windows i mean come-on not everyone wants to run that os. i know it takes effort to get linux going  but  if theres a problem one would think the place that made it orforum that knows it can help..

---

### Post by macgyver2 on 2005-08-24
[QUOTE=SD-Plissken]So ubuntu is only going to work on the latest and greatest machine. it seems every post on here has some user with a 64bit rig or the latest intel machine and its working. if its not working then everyone jumps in and helps. seems those with outdated laptops need not look for help . i dont get this.. so unless you have two thousand or four thousand dollar rigs ubuntu and kubuntu is not for you. people who are fed up with using ms programs and the os it's self, and choose to use this progam i guess they should understand that if their machine is old dont look for help. everyone for themself figure it out on your own then post how you did it ..[/QUOTE]
I don't see where you're coming from with this.  I specifically remember responding to a problem someone was having on an old machine with *only 32MB* of memory.  I also remember another thread where 4 or 5 people jumped in to discuss running Ubuntu on a five-year-old laptop.  I myself am typing this from a machine with an 800MHz processor and 128MB of memory.  I'd also be willing to bet there are people who have bleeding-edge systems who might not find the help they need right away.

---

### Post by John.Michael.Kane on 2005-08-24
Ok good for you yet i have seen you help not with the isses i have posted. like i said  you help a select few... ubuntu is for new machines plain and simple..

---

### Post by s_p_a_r_k_y on 2005-08-24
SD, I don't think thats the issue. People help when they think they can help the situation. If someone wants help for a machine I have no idea about I don't think i can help unless its a general problem. Many people here in the forums are recent converts (last 2-3 years I would suspect) thus old laptops probably arne't our strengths. Everyone wants to help, but just making blind suggestions often frustrates people and doesn't help in the end so if no one has an answer they may leave it for others to solve. I don't see how ubuntu would be different from other distributions as it uses a relatively new kernel which supports both old and newish hardware. Most other major distros are using a kernel either a few months older (debian) or newer (fedora), there isn't much disparity amongst them

---

### Post by John.Michael.Kane on 2005-08-24
s_p_a_r_k_y i'm not trying to start a fight. i'm just fed up with things after being a ms user off and on im just sick and tired plus being up till 3am trying to figure out this ubuntu os and still in the end having to format and install xp  it's a pain in the you know what..

---

### Post by s_p_a_r_k_y on 2005-08-24
SD, the last thing anyone wants or needs is a fight. I understand the staying up till 3am to well and also hate it. So what I did was just look for devices that would work under linux and ended up buying network cards that would work now. Then in a year or two when my internal one was supported sold the external one to someone who was in the same boat as me (just 2 years later). A computer wihtout internet may not be very useful these days so ya may want to do that.

---

### Post by macgyver2 on 2005-08-24
[QUOTE=SD-Plissken]Ok good for you yet i have seen you help not with the isses i have posted. like i said you help a select few... ubuntu is for new machines plain and simple..[/QUOTE]
I just hadn't happened to come across your original thread asking for help.  There are a *lot* of threads to read.  I probably don't read more than 5% of them myself.  But now that I saw this one I looked at your other posts and found your original post.  So, now I joined in the thread to try to help you with your problem (though I must say s_p_a_r_k_y was doing an great job already).

I think I've started four threads since I came onboard the forums last month.  Three have yet to be answered. :) Not a big deal.

---

### Post by locutus42 on 2005-08-25
[QUOTE=SD-Plissken]s_p_a_r_k_y i'm not trying to start a fight. i'm just fed up with things after being a ms user off and on im just sick and tired plus being up till 3am trying to figure out this ubuntu os and still in the end having to format and install xp  it's a pain in the you know what..[/QUOTE]

SD,
  It's a tough road to go down when you not only are just learning GNU/Linux but you also have old hardware. There's just alot to go through and doing it in writing/forums makes it even tougher for both the helper and the helpee.

The only thing I can recommend is to try the various LiveCDs to see which one supports the most features of your system and then try installing it to see if there's enough to start messing around. since you say you have and old laptop, I would recommend Knoppix( possibly something around v3.4 ). And you'll want try getting the system to use a lighter weight desktop( other than KDE or Gnome ). If you try Knoppix, you can hit the F2 key at the bootup prompt to see what options are available( desktop= ).  And since you say you have an old laptop, it might not boot from CD and that's another reason for the Knoppix 3.4 version since it has a way to make boot floppies. Otherwise, there is something called Smart BootManager( [http://btmgr.sourceforge.net/about.html](http://btmgr.sourceforge.net/about.html) ).
Once installed to the HD boot sector, it will manage your partitions and can typically boot CDROMS. You'll want to make sure you tell your OS installation to make the partition bootable and not install grub/lilo to the boot sector.

Another option would be to call or email the Linspire, Xandros, etc vendors and see if they'll support your laptop. it might cost a few bucks but they tend to be eager for sales since they are getting paid for what they do.

BTW, there are laptops on the market now in the $500 range and new desktop systems( w/Linux pre-installed ) for under $200( Fryes/Outpost.com and Walmart.com ). That might give you a platform to learn on as you work on getting the laptop configured.

disclaimer: my opinions and should be taken as suggestions only. YMMV

---

### Post by John.Michael.Kane on 2005-08-25
@locutus42

My laptop Spec's
Acer Travelmate 290 with centrino 1.3ghz 512 ddr 333 mem can go to 2gig
40gig hd samsung with 8meg cache
toshiba dvd-rw drive
Realtek RTL8139 Family PCI Fast Ethernet NIC 10/100
1394 Net Adapter via ochi 1394 host controller
Intel(R) PRO/Wireless LAN 2100 3B Mini PCI Adapter wi-fi b only
Pcmcia ENE CB1410 card bus controller
Agere Systems AC'97modem
SMSC IrCC (Infrared Communications Controller)
RealTek AC'97audio
Intel Extream Graphics 64mb ram

You tell me is this machine really really that old that it should not be suported..

I like my laptop that i have thank you!!!

---

### Post by Chuckaluphagus on 2005-08-26
[QUOTE=SD-Plissken]@locutus42

My laptop Spec's
Acer Travelmate 290 with centrino 1.3ghz 512 ddr 333 mem can go to 2gig
40gig hd samsung with 8meg cache
toshiba dvd-rw drive
Realtek RTL8139 Family PCI Fast Ethernet NIC 10/100
1394 Net Adapter via ochi 1394 host controller
Intel(R) PRO/Wireless LAN 2100 3B Mini PCI Adapter wi-fi b only
Pcmcia ENE CB1410 card bus controller
Agere Systems AC'97modem
SMSC IrCC (Infrared Communications Controller)
RealTek AC'97audio
Intel Extream Graphics 64mb ram

You tell me is this machine really really that old that it should not be suported..

I like my laptop that i have thank you!!![/QUOTE]

Your laptop is practically identical in specifications to mine (I have an Asus M3Np with a slightly faster processor, otherwise essentially the same).  It was the middle of the road for last year's models, and Ubuntu Linux runs perfectly on it.  The issues aren't caused by the age of your notebook; a Centrino-platform system can hardly be thought of as old or obsolete.    

I checked the threads you started, it certainly looks as if you've had a number of responses from people trying to offer assistance.  You should be able to iron out any problems you're having soon enough.  Good luck with it.

---

### Post by John.Michael.Kane on 2005-08-27
I must say i was wrong with this post Ubuntu runs wonderfully on this laptop minus someminnor issuses that i have yet to see a fix for. will try to post those issuse inside anoter post i had done before. i will only add this run only what you need you can really get this os small and tight by doing that... Mods or addmin you can lock or delete this post and im sorry for jumping on this os like i did..

---

### Post by TimelessRogue on 2005-08-27
Hmmm ... your contention re: Ubunto only meant for newer rigs doesn't seem quite right.  See my post under "HP with Ubunto".  Mine is definitely an older machine and Ubunto installed beautifully with absolutely no problems other that configuring a couple of things like the modem, wireless and network.

By the way, this a Pavilion n5000 Model GE with AMD Athlon XP 1100 on an Omnibook N32N-736 board with a Phoenix GE.M1.03 bios, 512 megs of memory, Trident Video Accelerator CyberBlade-XP display, ESS ES56CVM-PI Data Fax Voice Modem , Accton EN2242 Series MiniPCI Fast Ethernet Adapter with a Memorex USB mouse (plus the mouse pad).

Nonetheless, sorry to hear about your experience, but the answers to all your problems are out there somewhere ... on these forums.

---

### Post by Galoot on 2005-08-27
Glad you stuck it out through the frustration and got it all worked out.

---

### Post by John.Michael.Kane on 2005-08-27
@Galoot It's alot of reading but its worth it to be free of the beast that was running on my machine before...

@s_p_a_r_k_y and macgyver2 Thanks guys i have more to learn and read but man what diffrence this is.. im a convert for sure..

---

