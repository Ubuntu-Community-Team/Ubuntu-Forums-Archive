---
title: "Help with choosing Ubuntu compatible laptop"
date: 2016-04-30
forum: Hardware
---

### Post by UtnubuLap on 2016-04-30
Hey!

I'm planning on getting a new laptop and I want to run Ubuntu on it.

I am rather clueless when it comes to Linux, however I did use Ubuntu for some time, 5 years back. That time I installed Ubuntu on a primitive Lenovo laptop, and encountered problems with wifi, sound, touchpad, and a few other minor things. I did manage to fix all the issues with the help of people at #ubuntu@freenode, but I would like to avoid similar problems this time around. Due to this, I started looking at laptop's with Ubuntu pre-installed (Dell, ThinkPenguin, System76, etc), but most of them were overspec'ed and expensive in regards to my needs, and did not deliver with a Norwegian keyboard.

I am looking for a 13" laptop, which is 100% compatible with Ubuntu/Linux. (Hardware/drivers) It will be used for basic tasks mostly: Mail, inet browsing, document creating (OpenOffice/Libre/Similar), listening to music, watching 720p+ youtube video's without stuttering. Some other tasks I might dabble with: Watching 1080p .mkv, GIMP, some sort of video editor to create small video's with. (Nothing too fancy.) For this reason I am looking for something rather cheap. I won't do high end image or video editing and I won't play any game.

If anyone knows of the "perfect" machine for me let me know. Here are the one's I'm looking at right now.


Option 1:

Dell Inspiron 15 3000 Serie
[http://www.dell.com/no/p/inspiron-15-3552-laptop/pd?oc=cn55210&model_id=inspiron-15-3552-laptop](http://www.dell.com/no/p/inspiron-15-3552-laptop/pd?oc=cn55210&model_id=inspiron-15-3552-laptop)

Comes with Ubuntu pre-installed and has a Norwegian keyboard. However I am unsure if it can do what I wish for due to the processor and other spec's. I think this might be a bit under spec'ed. Any thoughts? If it is able to do the tasks I mentioned above without much of a hassle I might get it, regardless if it is 15".



The following laptop's come with Windows: (Reasonable laptops? How do I know if Ubuntu will run right away?)

Option 2: (Cheap)

Lenovo Ideapad 100S 14" bærbar PC (sølv)
[http://www.elkjop.no/product/data/barbar-pc/LE80R9001AMX/lenovo-ideapad-100s-14-barbar-pc-solv](http://www.elkjop.no/product/data/barbar-pc/LE80R9001AMX/lenovo-ideapad-100s-14-barbar-pc-solv)

Option 3: (Cheap)

HP Stream 13-c102no 13.3" bærbar PC (blå)
[http://www.elkjop.no/product/data/barbar-pc/HP13C102NO/hp-stream-13-c102no-13-3-barbar-pc-bla?scid=Pricecomparison2989](http://www.elkjop.no/product/data/barbar-pc/HP13C102NO/hp-stream-13-c102no-13-3-barbar-pc-bla?scid=Pricecomparison2989)

Option 4:

HP Pavilion x360 13-a221no
[https://www.proshop.no/Baerbar/Pavilion-x360-13-a221no/2532473](https://www.proshop.no/Baerbar/Pavilion-x360-13-a221no/2532473)

Option 5:

Lenovo E31-70 13.3" HD

Either:

[https://www.proshop.no/Baerbar/E31-70-80KX/2537934](https://www.proshop.no/Baerbar/E31-70-80KX/2537934)
128GB SSD

or

[https://www.komplett.no/product/866203/pc-nettbrett/baerbar-pc/ultraportable/lenovo-e31-70-133-hd#](https://www.komplett.no/product/866203/pc-nettbrett/baerbar-pc/ultraportable/lenovo-e31-70-133-hd#)
500GB Hyrbid

Any help would be greatly appreciated.

If this is in the wrong sub forum, sorry and please move.

---

### Post by Benjamin_Goldstone on 2016-04-30
I would Reccomend System 76. Very Reliable and Compatible with ubuntu preinstalled [URL="http://system76.com"]http://system76.com

[/URL]

---

### Post by oldfred on 2016-04-30
Do you really need a laptop?

I just retired my 10 year old laptop & built a SFF desktop with Intel i5, no video card. Works great with Ubuntu.
But I am retired and do not a need a portable system anymore. Might borrow my wife's Ipad if portable system really needed for short time.

And laptops are not ergonomic if used a lot. Screen is too small, keyboard too high, and screen too low if just on table. 

Any bleeding edge system whether laptop or desktop will likely have more issues. Video & wifi chip are the most important things to check for compatibility.

All new systems are UEFI which is more complex than the old BIOS as it is both and you have many more settings since you have UEFI settings & BIOS settings. 

Do not go too cheap. Intel has done no favors with some Bay Trail chips.
 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail) 

And AMD video is in flux as they are changing from proprietary video to the open source video, but some chips so not yet work well with the open source driver.
      
 The fglrx driver is now deprecated in 16.04, use radeon and amdgpu 
   AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)

---

### Post by Bucky Ball on 2016-04-30
I have an HP Stream 11 which runs Xubuntu-core 16.04 LTS faultlessly. It 'just worked' and installed with ease. :)

Not sure if the specs of the Stream 13 are similar and can't help much with the rest. I hear Lenovo is friendly from what I've seen on here and the net so right track there.

If you have Intel integrated graphics 99% of the time it works OOTBox, but what I generally advise is make sure you've nailed the graphics (particularly if you are using a separate graphics card) and wireless compatibilty and know they are going to work. Sometimes the BIOS can make it tricky, but oldfred knows more about which models pose problems there, perhaps. ;)

They would be my three points of interest. Other than that, most just work.

---

### Post by Jack Harper on 2016-04-30
Go for Dell, they are usually quite compatible and often come with Ubuntu, Asus is a good choice as well, I owned two Asus laptops and recently bought a third, never had problems with them, avoid AMD graphic cards if possible, Nvidia is your best choice. Dell and Asus are also the most reliable in my experience, buying System76 is also great. I would go for a Dell with Nvidia in your place, not too expensive, good quality and Ubuntu compatible, plenty of models to choose from too, they also usually come with 3 year warranty.

---

### Post by mörgæs on 2016-05-01
Is the old Lenovo out of the question? If it's still alive then please post the specifications and we might be able to bring it back into service.

---

### Post by UtnubuLap on 2016-05-02
Thanks for the replies!

@ Benjamin_Goldstone

Their cheapest has more power than I need, and is more expensive than similar laptop's I can get in the store here. Additionally I would have to get a Norwegian keyboard, shipping cost and pay an additional 25% in import cost. So it's a no go for me. Looks nice though!

@ oldfred

Yeah, it has to be a laptop as I travel all the time.

Thanks for the info.

@ Bucky Ball

Sounds good. I believe the internals between the 11" and 13" are the same. Why Xubuntu-core? Does it stand no chance running Ubuntu? Also, are you able to watch HD youtube clips for example?

@ Jack Harper

Been looking at Dell as well, however they are massively overpriced in Norway. Asus laptop's don't like me, so will stay away from those.

@ mörgæs

It works, the hardware is just too slow.

---

Haven't really gotten any further in my search. Still want a 13" laptop for it's mobility, but still looking at 15,6" laptops.

Option 1:
Dell Inspiron 15 3000-serien
[http://www.dell.com/no/p/inspiron-15-3552-laptop/pd?oc=cn55210&model_id=inspiron-15-3552-laptop](http://www.dell.com/no/p/inspiron-15-3552-laptop/pd?oc=cn55210&model_id=inspiron-15-3552-laptop)
2700 NOK

Pretty bad, but at least Ubuntu is pre-installed.

Option 2:
HP 15-ac181no 15.6" bærbar PC (sort)
[http://www.elkjop.no/product/data/barbar-pc/HP15AC181NO/hp-15-ac181no-15-6-barbar-pc-sort](http://www.elkjop.no/product/data/barbar-pc/HP15AC181NO/hp-15-ac181no-15-6-barbar-pc-sort)
3690 NOK

Intel Core i5, 4 GB DDR3 - Really cheap, but 15.6" is a pain, if it was 13.3" I'd buy it in an instant.

Option 3:
HP Stream 13-c102no 13.3" bærbar PC (blå)
[http://www.elkjop.no/product/data/barbar-pc/HP13C102NO/hp-stream-13-c102no-13-3-barbar-pc-bla](http://www.elkjop.no/product/data/barbar-pc/HP13C102NO/hp-stream-13-c102no-13-3-barbar-pc-bla)
1995 NOK

Cheap, but will probably regret it when I want more than 2 tabs open in inet browser.

Option 4:

Lenovo E31-70

Either:
3999 NOK - 128 SSD
[https://www.dustinhome.no/product/5010932479/e31-70](https://www.dustinhome.no/product/5010932479/e31-70)

or

NOK 4295 - 500 HDD (8GB eMMC)
[https://www.komplett.no/product/866203/pc-nettbrett/baerbar-pc/ultraportable/lenovo-e31-70-133-hd](https://www.komplett.no/product/866203/pc-nettbrett/baerbar-pc/ultraportable/lenovo-e31-70-133-hd)

Will probably get the one with SSD if I go for this, which seems to be where I am heading.

Option 5:
HP Pavilion x360 13-a221no
[https://www.proshop.no/Baerbar/Pavilion-x360-13-a221no/2532473](https://www.proshop.no/Baerbar/Pavilion-x360-13-a221no/2532473)
NOK 3464

Not in store atm.

---

Pretty much looking at the same laptop's, but not too happy about any of them.

Hope to come across an HP Pavilion 13 with Core i3-5th gen, 4 GB ram, 500gb hdd (or 128 ssd), and no x360/2-in-1 screen feature to ~3500-4000 NOK, which I have seen one vendor have, but they were out of stock now and aren't taking any more in.

Dell seems to be the only manufacturer in Norway who pre-installs Ubuntu, and they either do it on terrible machines, or on good ones and overprice them.

Please close this thread, I don't see myself getting anywhere. I'll just be on the lookout for a: 13" laptop with a decent design, decent guts at a decent price. HP Pavilion 13, seems to be it for me, perhaps the Lenovo I mentioned above.

Thanks for the help!

---

### Post by mörgæs on 2016-05-02
> **UtnubuLap said:**
> It works, the hardware is just too slow.


Or maybe the software is. I find the latter more likely. 
Anyway, your decision.

---

### Post by Bucky Ball on 2016-05-02
> **UtnubuLap said:**
> @ Bucky Ball

Sounds good. I believe the internals between the 11" and 13" are the same. Why Xubuntu-core? Does it stand no chance running Ubuntu? Also, are you able to watch HD youtube clips for example?

Run whatever you like. I haven't used Ubuntu in years and if you want to get the most out of one of these lower spec machines Ubuntu is not the greatest choice on any of them, not just the HP Stream. But yea, would run Ubuntu fine I'd think (although I'm not sure about Ubuntu's Unity 3d, I think that's what it is). Have a look on the net. Seems to be plenty of others running it on the Stream. 

Watch/stream Youtube or whatever HD you like. Basically, I use it with Skype, Thunderbird, Firefox, Libreoffice Writer and not much else. It's my traveling machine but I also use it sometimes round the house or when I want to access something quickly. The 11 is pretty small so wouldn't want to be doing a 10,000 word essay on it. My eyes would bleed out! :)

I never really bought it for that and haven't got the youngest eyes anymore, but the 13 would be better and you may have better eyesight than I. ;)

---

### Post by him610 on 2016-05-02
> I would Reccomend System 76. Very Reliable and Compatible with ubuntu preinstalled

+1 Owner of a System76 laptop for 2-1/2 years now. Never a problem. Definitely would be my No1 consideration if I decided to buy another laptop.

---

### Post by UtnubuLap on 2016-05-22
@ mörgæs

You are probably correct, but it always was slow from the very first day and only 11", which I can't type on for too long. I will probably install Ubuntu on it, but I want a little bit larger laptop as well as the keyboard is too cramped.

@ Bucky Ball

Went to the store and tried the HP Stream 13. I've ended up discarding it from my options.

Might have been Windows, but it lagged severely after just 3 tabs were opened. Not sure if Windows was the issue, the specific laptop, if too many people testing it had broken it, or if 3 tabs open is what it is supposed to do.

@ him610

I would get one, but they don't seem to ship to Norway, and if they did, I would have to pay 25% in import tax. Also it would come with a US keyboard and power adaptor.

If they could install a Norwegian keyboard and provide a Norwegian power adaptor, and perhaps send it and lable it as a "Gift" or something I would get it. ^^ The additional 25% just makes it too expensive for me.

---

I've managed to limit my option down to a single laptop now:

Lenovo E31-70
Core i3 8GB 128GB SSD 13.3"
4 490 kr
[https://www.dustinhome.no/product/5010901144/e31-70](https://www.dustinhome.no/product/5010901144/e31-70)

In my opinion it's perfect when it comes to specs vs price. However since I have not had a Lenovo laptop before I am a bit worried about the robustness of it. A lot of Lenovo laptop seems to be pourly put together, except the more expensive models.

Flexing keyboard (E31-80 13.3" - identical casing to the one I am considering): [https://www.youtube.com/watch?v=DtoKLxkify4&t=2m33s](https://www.youtube.com/watch?v=DtoKLxkify4&t=2m33s)
Flexing keyboard: [https://www.youtube.com/watch?v=7pjkpIOZ3bg](https://www.youtube.com/watch?v=7pjkpIOZ3bg)
Keyboard not registering unless hit dead on (Problem with lot's of models): [https://www.youtube.com/watch?v=OTB_T0qML60](https://www.youtube.com/watch?v=OTB_T0qML60)

Also the travel of the right click and left click is deep/far, which worries me. Not sure my finger will fit there. ^^

Problem (E31-80 13.3" - identical casing to the one I am considering): [https://www.youtube.com/watch?v=DtoKLxkify4&t=1m59s](https://www.youtube.com/watch?v=DtoKLxkify4&t=1m59s)

Should this make me reconsider getting the Lenovo E31-70? Ubuntu working on it flawelessly? Anyone here  have the Lenovo E31-70, and can confirm the keyboard and trackpad does not have these  issues?

(I'll probably make a new thread since the thread title is not as relevant as it was, and I'm more curious about the actual details of one laptop now.)

Thanks for the responses! Appreciate it!

---

### Post by UtnubuLap on 2016-05-22
As a side not I discovered Entroware while searching for other pre-installed Ubuntu distrubutors. Seems excellent, however import tax is still a problem, as well as keyboard and power adaptor. Good alternative for Brits.

---

### Post by sudodus on 2016-05-22
The Lenovo E31-70 seems to have Intel graphics which will usually work with linux.

Do you intend to dual boot with Windows? It is hard to know if there are complications with UEFI.

I haven't got that model, and the best feedback, of course, would be from someone with that particular computer, who has tried linux.

Have you searched the internet for it? ***Lenovo E31-70 linux*** brought me to for example this link: [http://forums.bodhilinux.com/index.php?/topic/13241-lenovo-e31-70-feedback/](http://forums.bodhilinux.com/index.php?/topic/13241-lenovo-e31-70-feedback/)

---

### Post by UtnubuLap on 2016-05-22
@ sudodus

No, I do not intend to dual boot. I plan on wiping Windows off. Should this make things with UEFI less complicated? (I assume so. However I am a rookie, and am not sure at all.)

Yeah, I've googled the laptop in general and the laptop with linux. I've read the page you linked. However I feel there isn't much info regarding this laptop out there, both when it comes to the potential flexible keyboard and installing Ubuntu. Apparently a review site got the laptop with Ubuntu pre-installed, so this leads me to believe all should be good, but I'd love to hear from someone here who can also cconfirm wiping Windows and installing Ubuntu is a rather hassle free activity. Only one site mentioned that the keyboard on the particular model was flexing a bit. If it's just a bit, I might get it, however if the keyboard flexs like in the video above, I won't be getting it.

Thanks for your reply! Appreciate it!

---

### Post by sudodus on 2016-05-23
Yes, it is less complicated to have Ubuntu without Windows. (Depending on the implementation of the UEFI system) probably you have a choice between UEFI and CSM (a mode emulating old BIOS). But the links I saw indicate that booting is not a problem. Graphics is not a problem. You probably need a proprietary driver for wifi, but it is a well known method, and should work well.

If you want a better quality of the mechanical components, I think it is an alternative to buy a used (second hand) ***professional class*** computer. There is another advantage too: Linux has had time to make hardware drivers that work well with computers that are a couple of years old :-)

In your neighbour country my family has bought laptops that work well with Ubuntu from [this company](https://www.inrego.se/webbshop). Probably there is a similar company in your country. Otherwise you can check the possibility to import a ***used*** computer. It might be possible without paying import tax, or to pay the value added tax (mervärdesskatt) in *your* country, not in mine.

---

### Post by mörgæs on 2016-05-23
> **UtnubuLap said:**
> 
You are probably correct, but it always was slow from the very first day and only 11", which I can't type on for too long. I will probably install Ubuntu on it, but I want a little bit larger laptop as well as the keyboard is too cramped.


I understand the need for a bigger screen but still the old one is worth a try with Lubuntu (not Ubuntu).

---

### Post by Bucky Ball on 2016-05-23
> @ Bucky Ball

Went to the store and tried the HP Stream 13. I've ended up discarding it from my options.

Might have been Windows, but it lagged severely after just 3 tabs were opened. Not sure if Windows was the issue, the specific laptop, if too many people testing it had broken it, or if 3 tabs open is what it is supposed to do.

I run Xubuntu on mine and have ten or so tabs open at a time without issue. Wouldn't have any idea how it runs Windows. Got rid of it immediately.

---

### Post by UtnubuLap on 2016-05-30
@ sudodus

Thanks for the info!

@ mörgæs

Installed Ubuntu 16.04 LTS on it, worked, but lagged a bit. Then installed Ubuntu 16.04 LTS Server just for experimenting. Will try Lubuntu as you suggested next. Thanks for the tip!

@ Bucky Ball

Yeah, probably just Windows (and people testing out the show model) slowing it down.

---

I have bought a laptop now. A HP ProBook 430 G3, I have a couple of questions which I have written in a new thread:[**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=504316")

[http://ubuntuforums.org/showthread.php?t=2326258](http://ubuntuforums.org/showthread.php?t=2326258)

This thread is pretty much obsolete now, please close it. :)

Thanks everyone for the help provided and sorry about the endless nagging!

---

### Post by Bucky Ball on 2016-05-30
> **UtnubuLap said:**
> 

This thread is pretty much obsolete now, please close it. :)

We rarely close them. Please mark the thread as 'solved' from 'Thread Tools' at the top right of the page and this will serve the same purpose. 

Good luck.

---

### Post by UtnubuLap on 2016-05-30
@ Bucky Ball

Alright. Done. :)

---

