---
title: "Possible new sound card"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by yousillygoose on 2008-02-11
Hey all.  This may indeed be my first post.  I have been running Ubuntu for probably about 3 months and am slowly getting used to it.  I have a Dell Inspiron 1720 and I am looking to buy a new sound card for it. I wanted to buy new speakers and I would prefer more than 2 channel speakers.  That being said for more than 2 speakers I need a better sound card.  I was wondering if anyone could recommend a sound card (5 or 7 channel) that runs well in ubuntu.  Before I go out and spend the money I thought polling the audience (that's you!) about your experiences with laptop sound cards and ones that are either supported in linux or have easy work around to make them work.  Thanks all.

Thanks all for building Ubuntu.  Open source is like organic food- it is slowly going to become a trend!

ysG

---

### Post by sgleo87 on 2008-02-11
I'm exactly in the same situation....also need a 5.1 surround sound card for my laptop so I can hook up my surround sound speaker system but I don't have any idea which ones would work in Ubuntu. The only thing I have heard so far is that the Creative X-fi cards are not supported so the X-fi notebook sound card for the express slot will probably not work in Ubuntu. Hoping to get some feedback soon on sound cards that work.

---

### Post by yousillygoose on 2008-02-11
well, we will both hopefully get help than  :)

---

### Post by jrusso2 on 2008-02-11
These work well and the price is reasonable.

[http://www.turtlebeach.com/products/mtgoddl/home.aspx](http://www.turtlebeach.com/products/mtgoddl/home.aspx)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829118109](http://www.newegg.com/Product/Product.aspx?Item=N82E16829118109)

---

### Post by yousillygoose on 2008-02-11
those arent laptop cards are they?

---

### Post by sgleo87 on 2008-02-11
no they are not....although I noticed Turtle beach does make a 5.1 sound card that you hook up to a USB port [http://www.turtlebeach.com/products/audio-advantage-srm/home.aspx](http://www.turtlebeach.com/products/audio-advantage-srm/home.aspx)
Does anyone know if that one works in ubuntu?

---

### Post by yousillygoose on 2008-02-12
That would be nice having a usb one.  I wonder if there is a downfall of usb ones.  If they are less quality  or anything

---

### Post by sgleo87 on 2008-02-12
yeah I've been wondering about that too. I mean for laptops the only options are a sound card for the express slot or a usb sound card but I don't know if there is a difference in sound quality and how those two compare to regular sound cards like the ones mentioned above.

---

### Post by yousillygoose on 2008-02-13
Yea, I sometimes regret having only a laptop

---

### Post by ÜbuntuMensch on 2008-02-13
I have the Inspiron 1420 and can confirm that the expresscard 54 soundcard by creative is "not supported." Creative seems to be having some driver issues in general...

but if you want to know what will work on Ubuntu/Linux, try checking the Alsa sound card matrix: 
[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

start googling usb audio interface. Something will pop out at you.

I'm using an M-Audio mobile pre usb. It's okay, lots of ins- and outs-  but larger than I really want for portability. Though it is one of the few that is usb-powered, so no extra cord.

A PCMIA card should give you faster data transfer than USB, and firewire faster than that. But unless you're doing multi-track recording that isn't so much of an issue. 

with a laptop, size is key, and I almost wish I'd gone something low-end and simple like this: [http://www.musiciansfriend.com/product/Behringer-UCONTROL-UCA202-USBAudio-Interface?sku=702540]("http://www.musiciansfriend.com/product/Behringer-UCONTROL-UCA202-USBAudio-Interface?sku=702540")

bummer, really, about the expresscard slot on these machines. What to do with them?

---

### Post by yousillygoose on 2008-02-13
I'm not entirely sure how to read that matrix (gosh, I'm such a noob).  That pci express card, is that the slot on my laptop that has a little plastic card holding the spot in it.  It has a little button that you can remove the plastic card easily?  Also, the usb device that you posted, that is only 2 channel, correct?  Thanks a lot

---

### Post by sgleo87 on 2008-02-13
> **yousillygoose said:**
>  That pci express card, is that the slot on my laptop that has a little plastic card holding the spot in it.  It has a little button that you can remove the plastic card easily?
Yes that's the express card slot ;)

And yes, I think you are right, both the M-Audio and the Behringer sound card in the link are only 2.0 so it doesn't really solve our problem.

I'm still trying to figure out this matrix thing too but I think all the sound cards listed in the vendors section are supported. Also at the top it says "All USB devices that are standards compliant will work" so does that mean pretty much all USB sound cards will work???

---

### Post by ÜbuntuMensch on 2008-02-14
Yeah, in theory the usb soundcards should not require a driver. Most of them state that in their descriptions.

as for 5.1, they are out there:

this one from NewEgg: [http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101")

is probably as cheap as it gets.

terratec makes some...[http://www.lhdigital.co.uk/product_info.php?language=en&currency=USD&products_id=93627]("http://www.lhdigital.co.uk/product_info.php?language=en&currency=USD&products_id=93627")

looked really good to me.

The Matrix shows all the audio card producers by name and then within each company it lists all their products, so you find the one you think you like by googling around and then double check on the matrix to know if it is suported by Alsa (the default audio drivers on Ubuntu).

---

### Post by yousillygoose on 2008-02-14
And are usb one's lower quality?

---

### Post by ÜbuntuMensch on 2008-02-14
not by virtue of being USB.

You get better sound quality out of a USB port than you do from your headphone jack.  That's really what we're talking about here.

---

### Post by sgleo87 on 2008-02-14
I searched for USB sound cards at Amazon and Newegg and the only 5.1 usb sound cards I could find is the GWC card from the link above and a Zalman sound card [http://www.newegg.com/Product/Product.aspx?Item=N82E16829101151&ATT=29-101-151&CMP=OTC-pr1c3grabb3r&nm_mc=OTC-pr1c3grabb3r&cm_mmc=OTC-pr1c3grabb3r-_-Sound+Card-_-Zalman+Tech+Co.++Ltd-_-29101151](http://www.newegg.com/Product/Product.aspx?Item=N82E16829101151&ATT=29-101-151&CMP=OTC-pr1c3grabb3r&nm_mc=OTC-pr1c3grabb3r&cm_mmc=OTC-pr1c3grabb3r-_-Sound+Card-_-Zalman+Tech+Co.++Ltd-_-29101151). The Terratec sound card would be a great option but I can't find it anywhere to buy here in the U.S. other than directly from Terratec but they charge $30 for shipping. The Zalman sound card seems pretty similar to it though.

The Zalman sound card is around $55 while the GWC is only $22...is there going to be a noticable difference in audio quality between the two or why is there this big price difference? Quality is definitely important to me so I would be willing to spend up to $100 if it is worth it.
None of these cards are listed in the matrix but I hope they will still work in Ubuntu...

---

### Post by sgleo87 on 2008-02-18
bump

---

### Post by Saxis on 2008-02-22
I know at least the V1S has S/PDIF. I'll be plugging mine into a TOSlink adapter and run an optical cable to my amp/receiver, which has DTS. Probably the easiest way to get surround, but also probably not the most practical if you don't already have a theater system.

---

### Post by oldsoundguy on 2008-02-22
Saw a mention of Behringer as a sound card above.  They are noted for reverse engineering products made by others and then bringing them out onto the market. (doing that generates equipment that is not reliable.)  I never liked their pro audio equipment, so using anything  made by them would not be in my future.

Turtle Beach has been mentioned.  They do NOT have their own drivers for Linux, but they publish a list at their site of 3rd party drivers that have been tested BY them.  The sound is VERY good, and at least they tip their hat to Linux rather than turn their back such as is done by Creative.

But an EXTERNAL USB card of any kind is going to be a total crap shoot.  
Also remember that Gazintas = Gazoutas.  IF you only have 2.0 or 2.1 capability on that laptop, any 5.1 or higher is going to be GENERATED 5.1 and will NOT be true surround.  Yes, the speakers will WORK, but they are only going to get a stereo signal.  There may be some external cards that WILL find the 5.1 source from the playback media, but you will be hard pressed to find one and when you do, it will not be cheap simply because the demand is not there
Most that go full blown sound do so on desktops, where flexibility is the norm.

---

### Post by sgleo87 on 2008-02-22
> **Saxis said:**
> I know at least the V1S has S/PDIF. I'll be plugging mine into a TOSlink adapter and run an optical cable to my amp/receiver, which has DTS. Probably the easiest way to get surround, but also probably not the most practical if you don't already have a theater system.

I don't have a home theater system...I have surround sound speakers from Logitech (Z-5450). I don't think there is a way to hook those up through the S/PDIF port, or is there?

> **oldsoundguy said:**
>  IF you only have 2.0 or 2.1 capability on that laptop, any 5.1 or higher is going to be GENERATED 5.1 and will NOT be true surround.  Yes, the speakers will WORK, but they are only going to get a stereo signal.  There may be some external cards that WILL find the 5.1 source from the playback media, but you will be hard pressed to find one and when you do, it will not be cheap simply because the demand is not there
Most that go full blown sound do so on desktops, where flexibility is the norm.

Yes, I know if I only have a 2.0 sound card in my laptop that it will not be true surround sound....that is the whole reason why I want an external 5.1 sound card.
Don't all external surround sound cards, that you can hook a 5.1 speaker system up to, generate true surround sound? (like for example the Zalman sound card I mentioned above)

---

### Post by oldsoundguy on 2008-02-22
unless your source is READABLE as surround, no add on will be able to create ACTUAL surround.  You will get a very weak approximation.

As I said, gusintas=gozoutas  What goes in comes out.

Think about if you have a mono source and play it on a stereo .. you will get sound from both speakers, but it will be identical.

---

### Post by sgleo87 on 2008-02-22
> **oldsoundguy said:**
> unless your source is READABLE as surround, no add on will be able to create ACTUAL surround.  You will get a very weak approximation.

As I said, gusintas=gozoutas  What goes in comes out.

Think about if you have a mono source and play it on a stereo .. you will get sound from both speakers, but it will be identical.

what do you mean by source? I know music is only recorded in stereo so unless I have a movie with surround sound playing then I will not get true surround sound no matter what sound card I have. Is that what you meant by that or are you talking about the sound card?

---

### Post by oldsoundguy on 2008-02-23
hoooo kaaayyy ... source=what is being PLAYED, be it a digital file from the hard drive or a web source or a DVD or a CD  Can be music, video, whatever. (and some music is now recorded in 5.1 in case you haven't heard it yet.)

No matter the source, if the computer itself is not capable of putting out 5.1, the only thing you will  get is STEREO.  Buying an external device to drive a 5.1 speaker system from a stereo source  will still get you only STEREO.  But out of 5 speakers and a sub .. and good chance the center front speaker will wind up being a MONO source and really muddy it up.

Standard output from most computers, laptops included is ANALOG not digital unless there is a card installed (I have such).  So there is no way to translate it into 5.1.  Even if the internal system is kicking out a digital stereo .. source not withstanding.   Unless the card or computer says 5.1 or higher OUT or digital DIN out that is 5.1 (your manual will tell you that)  No way .. 5.1, only stereo.

---

### Post by sgleo87 on 2008-02-23
Ok...I got that. To get surround sound you need 3 things: A source that is recorded  in 5.1, a sound card that can put out 5.1, and a 5.1 speaker system. So if I have a movie playing with surround sound, an external 5.1 usb surround sound card hooked up to my laptop, and my 5.1 speaker system hooked up to the card, I should get surround sound right?

btw this is my internal sound card in my laptop: Realtek ALC662 (intel hd audio) [http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=37&Level=5&Conn=4&ProdID=144](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=37&Level=5&Conn=4&ProdID=144) but my guess is that the internal sound card does not matter once you hook up an external one since the laptop will just be using one sound card.

---

### Post by oldsoundguy on 2008-02-23
YEP, you got the picture now.  NOW, if your external USB 5.1 plug in system comes with software that will take your source (drive whatever) and impress that signal digitally 5.1 on to the USB feed when activated, you WILL have 5.1 DIGITAL sound.  THEN you will need a 5.1 amplifier that will change that digital signal back to analog (what I use) .. speakers are analog devices.  They respond to sine wave signals and not digital signals ... (or that USB device will have to be the D/A converter to drive a straight ANALOG system.)

For others following this thread .. I use 5.1 for simplification .. 6.1 and 7.1 and THX are the same issues.

---

