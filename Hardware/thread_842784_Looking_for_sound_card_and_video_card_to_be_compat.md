---
title: "Looking for sound card and video card to be compatiable with Ubuntu..."
date: 2008-06-27
forum: Hardware
---

### Post by PsychedelicWonders on 2008-06-27
I was on newegg.com about to buy the rest of my system componets and I was reviewing my sound card...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829102016](http://www.newegg.com/Product/Product.aspx?Item=N82E16829102016)

And alot of the reviews state this is not compatible with linux.

How do i tell if a sound or video card is going to be compatiable with linux?

I am looking for a 7.1 pci express card for sound.  Im looking to stay around $40-$50 for the card.

Also, with 7.1 sound cards... I plan on hooking up my home theater to this system... so does that mean I can do 5 speakers for the home theater system and still have 2 "front" speaker outputs for 2 small speakers for the computer?

How does that work?

Still up in the air about the video card.

I want to run 2 "monitors", one 22" monitor and one 40" tv.

I understand with a dual video card you can run both tv and monitor, but they will view the same thing right?

Is there any way to have the tv view one thing while the monitor is viewing or doing something else?

Can a system run two "monitors" running independent things?  i.e. i want to surf the net on the monitor while i watch a movie on the tv?

---

### Post by PsychedelicWonders on 2008-06-27
bump

---

### Post by PsychedelicWonders on 2008-06-28
bump

---

### Post by starcannon on 2008-06-28
Nvidia for the vid card

Anything AC97 compliant for the sound card.

---

### Post by PsychedelicWonders on 2008-06-28
thanks.

What about my dual monitor, yet separate functions questions?  Is this possible?

Where do I find in the specs of a sound card if it is AC97?

---

### Post by starcannon on 2008-06-28
The Nvidia 7950gt currently one of my favorite cards, I actually have a pair of them sli'd together, if you don't want to spend this kind of cash don't worry, there are cheaper Nvidia cards that support dual monitors, this will at least give you something to read on and know what features to look for.[http://www.newegg.com/Product/Product.aspx?Item=N82E16814143071](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143071)

Oh wow, 8800gt for less money than a 7950gt even comes w/free winders game, and its an xfx which is what I've been using and had no problems with:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150252](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150252) 
Oh sweet heres a BFG 8800gt for $180... ruh roh I might have to buy parts, I'm feelin the itch,
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814143118](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143118)

But even an Nvidia 8400 gs supports dual monitors and is a very respectable card. [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121240](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121240)

Most sound cards are AC97 compliant. If I were in the market and ready to drop a c-note on a sound card I'd shop here first: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) that way I know I'd have the most trouble free experience possible.

GL man, lucky devil, I love building new systems, or even upgrading my old ones.

Oh and googling around it looked like the X-FI sound cards can be a dog in heat to get working, just a heads up.

---

### Post by PsychedelicWonders on 2008-06-28
can you actually run 2 different video cards and view two different applications at the same time on 2 different monitors?  Is that possible?

Or just a mirrored image of each other with the dual video card?

---

### Post by markbuntu on 2008-06-29
M-audio revolution is the sound card you want. it works out of the box and has the highest quality sound. SB cards will just give you headaches. You don't really need pci-express for sound, plain old pci is plenty fast for any sound application. Consider that the highest quality sound is 196kb/s and you can't tell the differnece between that and 48k/s unless you have a $zillion sound system and are a professional audio engineer. Pci-express sound cards are just useless hype to make you spend more money on crap that makes no difference.

Yes, you can run two different video cards with two different monitors showing different apps but do not mix and match the cards. You can also extend your desktop across two monitors with one video card and run separate apps on each one in full screen.

The latest ati linux drivers provide crossfire support but I don't know if that supports more than two monitors yet but it will support mixing two newer ati cards, even if one is integrated into the motherboard. If I had the room, I would get another ati card and see if I could get 4 monitors to work.

---

### Post by PsychedelicWonders on 2008-06-29
> **markbuntu said:**
> M-audio revolution is the sound card you want. it works out of the box and has the highest quality sound. SB cards will just give you headaches. You don't really need pci-express for sound, plain old pci is plenty fast for any sound application. Consider that the highest quality sound is 196kb/s and you can't tell the differnece between that and 48k/s unless you have a $zillion sound system and are a professional audio engineer. Pci-express sound cards are just useless hype to make you spend more money on crap that makes no difference.

Alright, does everyone sell these M-audio revolution cards?

This is my game plan with the audio...

I want to hook up a home theater system with 5 speakers itself and 1 subwoofer.  

But I would also like to have 2 speakers that are by my monitor for "computer speakers"

Should I get a 7.1 sound card then?

Can I run 2 additional "front/main" speakers on a 7.1 card?  Do I understand the concept properly?

> Yes, you can run two different video cards with two different monitors showing different apps but do not mix and match the cards. You can also extend your desktop across two monitors with one video card and run separate apps on each one in full screen.

Now that I think about it, after i read the way you explained it... I'm not asking for anything different.

Perhaps just to start I shall get a regular video card, and later when I add the flat screen tv as another monitor, I shall get the same card again.

But when you have 2 separate video cards... does the computer look at it as 2 seaparate monitors... or 1 big monitor like when using a dual video card?

Any suggestions on a video card that will work in linux, for $75 or less that will run HD fairly well?

Is there a particular brand I should stick to?

> The latest ati linux drivers provide crossfire support but I don't know if that supports more than two monitors yet but it will support mixing two newer ati cards, even if one is integrated into the motherboard. If I had the room, I would get another ati card and see if I could get 4 monitors to work.

What is crossfire support?

---

### Post by markbuntu on 2008-06-29
5.1 surround is two front speakers and two rear speakers and a middle/sub speaker. 7.1 adds side speakers. You can set them up however you want. Yo can sent the 5.1 surround out the spdif port on the card and hook up speakers to the regular outputs also. I am not sure that the m-audio card has a spdif plug so you should check that out.


Your best bet would be to get one really good video card that had two dvi outputs. Nvidia and ati make some pretty good ones that sell for about $70-100. Intel video is better supported in linux with open drivers but I don't know much about them so I can't help you there.

Crossfire is an ati thing so you can link two ati cards together so they run in sync and share rendering tasks. It is a very new thing in their linux drivers but has been around for windows for a while.

---

### Post by imolafem on 2008-06-29
> **markbuntu said:**
> M-audio revolution is the sound card you want. it works out of the box and has the highest quality sound. SB cards will just give you headaches. You don't really need pci-express for sound, plain old pci is plenty fast for any sound application. Consider that the highest quality sound is 196kb/s and you can't tell the differnece between that and 48k/s unless you have a $zillion sound system and are a professional audio engineer. Pci-express sound cards are just useless hype to make you spend more money on crap that makes no difference.

Yes, you can run two different video cards with two different monitors showing different apps but do not mix and match the cards. You can also extend your desktop across two monitors with one video card and run separate apps on each one in full screen.

The latest ati linux drivers provide crossfire support but I don't know if that supports more than two monitors yet but it will support mixing two newer ati cards, even if one is integrated into the motherboard. If I had the room, I would get another ati card and see if I could get 4 monitors to work.
Markbuntu, I like the reivews on the M-audio revolution card on newegg.com.  Does it work well for you on Kubuntu 8.04?  Does anyone else have experience with this card on Kubuntu 8.04?  Replies welcome...

---

### Post by PsychedelicWonders on 2008-06-29
> **markbuntu said:**
> 5.1 surround is two front speakers and two rear speakers and a middle/sub speaker. 7.1 adds side speakers. You can set them up however you want. Yo can sent the 5.1 surround out the spdif port on the card and hook up speakers to the regular outputs also. I am not sure that the m-audio card has a spdif plug so you should check that out.

newegg only has one M-Audio card and it is 5.1.  So youre saying there are other out ports on the card that will allow me to hook up additional speakers?

I looked in the specs for the spdif, but didnt see anything, but I could be looking at the wrong thing.

Let me know what you think...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829121122](http://www.newegg.com/Product/Product.aspx?Item=N82E16829121122)


> Intel video is better supported in linux with open drivers but I don't know much about them so I can't help you there.

You totally lost me here... what was this in reference to?

Thats what I'll do then, get one really good dual video card.

Do video cards ever combo up with Tv Tuner cards and do an all in one?

Or do you have to/is it best to have these two cards separate?

---

### Post by PsychedelicWonders on 2008-06-30
bump

---

### Post by PsychedelicWonders on 2008-06-30
Alright ive found a couple of video cards...

For an ATI card I found...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102726](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102726)

or for an Nvidia card I found...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049)

Which one do you guys think? 

I'm leaning more towards the Saphpire..

Both have 2 dvi ports.  So instead of hooking up my 40" flatscreen by means of hdmi, i should do dvi?

Will that give me better clarity?

---

### Post by PsychedelicWonders on 2008-07-01
bump

---

### Post by dogscoff on 2008-07-01
>> Intel video is better supported in linux with open drivers 
>> but I don't know much about them so I can't help you there. 

> You totally lost me here... what was this in reference to?

This is about the different kinds of free software, about open source, and about licensing. It's a political/ideological point (and as such is likely to cause some passionate conversation). 

In brief, and trying not to be too controversial:

The drivers for the Intel cards are open source. That means that you (or anyone else in the world) can read the source code to see exactly how it works. If you want you can even modify the code to change the functionality of the driver or update it to work with some future version of linux, or even port it to some other operating system altogether. Even if you don't do these things for yourself, it's important that other Linux users can, because as long as they have the code, linux ppl everywhere will continue to update and improve it as long as required, without any further action required from Intel. There are whole armies of people doing this kind of thing all the time, often for free, and without them there would be no Linux, no Ubuntu.

Nvidia make drivers for their graphics cards to run under linux. I run a Nvidia card myself and it works beautifully under Ubuntu. These drivers are free as in "free of charge" but not free as in "free to do whatever you like with". They just release compiled drivers. This means you can't see the source code, so you can't see exactly what's going on in there and you are completely dependent on NVidia to produce secure, stable code and keep updating the drivers. If for some reason Nvidia stopped providing this service tomorrow, then Linux users with Nvidia cards would be in trouble, because drivers inevitably need updating. Of course as customers who have paid good money for our Nvidia hardware, we could certainly argue that they have a duty to keep providing this service, but big companies often make unpopular decisions, and sometimes they go out of business altogether. (Not that I think Nvidia will do so in the near future, but it's never impossible)

A lot of Linux users don't worry too much about this distinction between open and closed source drivers, but to others it's very important. The vast majority of Linux software is both free as in beer and free as in speech. Linux and it's community is built upon it. However most (but not all) agree that Nvidia's choice to release binary-only drivers is better than releasing nothing at all...

*** disclaimer ***
The above is a gross simplification of quite a complex issue, and I'm certainly not an expert on it. If you want to learn more, the web is a great place to look. Searches to get you started might include "gnu gpl" and "free as in speech / beer"
*** /disclaimer ***

---

### Post by PsychedelicWonders on 2008-07-01
ahh I understand now.  Good info.

Any one have opinions on the 2 video cards I linked to above?

Im going with the Sapphire card I think unless someone has a reason i should not?

thanks.

---

### Post by PsychedelicWonders on 2008-07-01
bump on video card selection

---

### Post by PsychedelicWonders on 2008-07-02
**sound card question...**

newegg only has one M-Audio card and it is 5.1. So youre saying there are other out ports on the card that will allow me to hook up additional speakers?

I looked in the specs for the spdif, but didnt see anything, but I could be looking at the wrong thing.

Let me know what you think...

[http://www.newegg.com/Product/Produc...82E16829121122](http://www.newegg.com/Product/Produc...82E16829121122)

**Video Card question:**

Which one and why?

For an ATI card I found...

[http://www.newegg.com/Product/Produc...82E16814102726](http://www.newegg.com/Product/Produc...82E16814102726)

or for an Nvidia card I found...

[http://www.newegg.com/Product/Produc...82E16814500049](http://www.newegg.com/Product/Produc...82E16814500049)

---

### Post by starcannon on 2008-07-02
Right now its very difficult for me to advise Nvidia over ATi, a month ago I would have, but word on the interweb is that ATi has stepped up their Linux game and excellent drivers are now available or imminently available. 

I've used Nvidia since the great ATi 9700pro debacle a few years ago, but times have changed, AMD bought ATi, and evidently have every intention of matching or beating Nvidia's support under Linux.

I like that 8600gt for the money though, very nice for $76.00, I also very much like the Nvidia Settings manager, in my opinion it makes dual monitors a piece of cake, but I've never tried to do what your attempting, I merely made 2 monitors into one big monitor.

---

### Post by stchman on 2008-07-02
> **PsychedelicWonders said:**
> I was on newegg.com about to buy the rest of my system componets and I was reviewing my sound card...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829102016](http://www.newegg.com/Product/Product.aspx?Item=N82E16829102016)

And alot of the reviews state this is not compatible with linux.

How do i tell if a sound or video card is going to be compatiable with linux?

I am looking for a 7.1 pci express card for sound.  Im looking to stay around $40-$50 for the card.

Also, with 7.1 sound cards... I plan on hooking up my home theater to this system... so does that mean I can do 5 speakers for the home theater system and still have 2 "front" speaker outputs for 2 small speakers for the computer?

How does that work?

Still up in the air about the video card.

I want to run 2 "monitors", one 22" monitor and one 40" tv.

I understand with a dual video card you can run both tv and monitor, but they will view the same thing right?

Is there any way to have the tv view one thing while the monitor is viewing or doing something else?

Can a system run two "monitors" running independent things?  i.e. i want to surf the net on the monitor while i watch a movie on the tv?

The SB X-Fi sound cards are not very Linux friendly.  Creative has had this card for over three years and just a beta driver.

I would recommend an Audigy sound card.

For video the Nvidia 8800GT is a great card and works very well with hardy.

ATI cards still have some compatibility issues with Linux.

---

### Post by PsychedelicWonders on 2008-07-02
So I should go with the sapphire card then?

the Nvidia Settings manager, in my opinion it makes dual monitors a piece of cake

Does ATI have a similar settings manager that is easily usable?

---

### Post by PsychedelicWonders on 2008-07-02
im so confused.  one guy says nvidia is better supported, another one says ATI is better.

which is which here?

I'm leaning towards the sapphire card.

will i have any problems with that one?

---

### Post by Brebs on 2008-07-02
> **markbuntu said:**
> M-audio revolution is the sound card you want. it works out of the box and has the highest quality sound. SB cards will just give you headaches.
Well, [here's my experience in several links](http://forums.gentoo.org/viewtopic-p-4192284.html#4192284) - and I've done the research and own the cards, plus decent speakers.

---

### Post by PsychedelicWonders on 2008-07-03
bump

---

### Post by PsychedelicWonders on 2008-07-04
any more clarification?

ATI or Nvidia?

---

### Post by starcannon on 2008-07-05
For best out of the box experience, go with Nvidia, if your an Open Source or nothing kinda guy and don't mind really having to get your hands dirty go with ATi.

Since your here, asking the questions your asking, I would highly recommend Nvidia. 

Just my 2 cents, I'm not dogging ATi, I'm not dogging FOSS, I'm just trying to stear a newbie towards the most pain free experience that my experience has to offer.

GL

P.S. oh and I almost forgot, avoid the X-fi sound card, that thing is a headache, it can be made to work, but why put out the effort when there are so many to choose from that "just work out of the box"; heres a nice list to choose from:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
enjoy, and as always,

GL

---

### Post by PsychedelicWonders on 2008-07-07
thats what im looking for.  being totally new to linux, i want as easy and as little tweaking as possible.

this is the nvidia then...

[http://www.newegg.com/Product/Produc...82E16814500049](http://www.newegg.com/Product/Produc...82E16814500049)

Thanks.

Now that is tackled... what about a good sound card for 30-40$?

something that will allow me to run 5.1 & 2 extra computer speakers

---

### Post by PsychedelicWonders on 2008-07-07
Everything else is taken care of...

But what about a good sound card for 30-40$?

something that will allow me to run 5.1 & 2 extra computer speakers

And something that is ready to install and run with out tweaking?

i'm not looking to produce professional music, but do want my music and movies to sound great.

---

### Post by PsychedelicWonders on 2008-07-10
> **markbuntu said:**
> Yes, you can run two different video cards with two different monitors showing different apps but do not mix and match the cards. You can also extend your desktop across two monitors with one video card and run separate apps on each one in full screen.

What advantages are there to running a video card with 2 dvi outputs compared to just using 1 regular video card and splitting it up on 2 monitors as you mentioned above?


> The latest ati linux drivers provide crossfire support but I don't know if that supports more than two monitors yet but it will support mixing two newer ati cards, even if one is integrated into the motherboard. If I had the room, I would get another ati card and see if I could get 4 monitors to work.

Is it only possible to run 4 monitors via Ubuntu with ATI, or can you also achieve the same success using Nvidia?

---

