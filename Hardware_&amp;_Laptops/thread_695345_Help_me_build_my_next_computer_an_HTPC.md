---
title: "Help me build my next computer an HTPC"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by PsychedelicWonders on 2008-02-12
Altight everyone, I have the following components I am going to buy very shortly to build a new computer to install Ubuntu on.

Tell me what you think of what I have, and if you can suggest anything else, or better around the same price range.  

I plan on using this as an everything in one.  Im going to have it ran to a big screen TV.  I will run Ubuntu on its own hard drive A and then I want to put all pictures, videos and songs etc on hard drive B, which will then be backed up on C with RAID. (I do need a card for this right?)

I also plan on hooking up a receiver, speakers and sub-woofer to use it as the HT aspect of it.  What do I need to intall into the computer to be able to do this?  Just the sound card I have listed below?

I also want a TV tuner to be able to record like a tivo, if anyone can suggest a good one of those.

Total as of now it will cost 470 -  I would really like to keep the core parts around this ballpark.  (not including the case or the multimedia software/remote.)

[http://www.newegg.com/product/product.aspx?item=N82E16813131043](http://www.newegg.com/product/product.aspx?item=N82E16813131043)

[http://www.newegg.com/product/product.aspx?item=N82E16819115015](http://www.newegg.com/product/product.aspx?item=N82E16819115015)

[http://www.newegg.com/product/product.aspx?item=N82E16820211066](http://www.newegg.com/product/product.aspx?item=N82E16820211066)

[http://www.newegg.com/product/product.aspx?item=N82E16822144122](http://www.newegg.com/product/product.aspx?item=N82E16822144122)

[http://www.newegg.com/product/product.aspx?item=N82E16822144701](http://www.newegg.com/product/product.aspx?item=N82E16822144701)

[http://www.newegg.com/product/product.aspx?item=N82E16822144122](http://www.newegg.com/product/product.aspx?item=N82E16822144122)


Thanks.

---

### Post by PsychedelicWonders on 2008-02-13
anyone?

---

### Post by theacoustician on 2008-02-13
You might get some better responses if you had an admin move this to the Mythbuntu forum ([http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)).  There's even a very long thread that I started on that motherboard you selected.

To quickly answer some of your questions:
1. What's with the multitude of different HDDs?  Just get a small one to run the OS and two of the same kind to store your movies, pictures, etc. and run that in RAID 1.  You don't need a card to do that, but there are advantages to using one.

2. You don't need anything to hook this up to your receiver.  The onboard sound on the motherboard has analog and digital sound out on the motherboard.

3. For a TV tuner, I'd suggest a HDHomeRun.  Anything by Hauppauge would be the next choice.

4. If you want to be able to decode HD MPEG4 AVC (ie H.264) or HD VC-1 material, you'll need a faster processor.  I'm sure you'll be able to handle MPEG2 HD content, and possibly 720p MPEG4/VC-1, but there is absolutely no way you're going to decode 1080p with that.  If you just want SD material, you're straight.

5. What about a case and remote?  Those aren't free, but you don't want to go over ~470?  I would think to get a decent case, power supply, and remote with IR receiver, you're looking at a minimum of another $100.  You shouldn't need to spend anything on software if you use Mythbuntu or any other Myth distro.

6. No disc drive?  I would think you'd want to at least pick up a DVD drive for a HTPC.

---

### Post by PsychedelicWonders on 2008-02-13
So what processor will i need to get to run HD MPEG4 AVC (ie H.264) or HD VC-1 material?

What kind of material comes in that format?

Also what advantages are there to using an actual raid card?

I have a case picked out, I may change it up but I am more worried about having the internals set up right.

The remote, I think I was going to go with the Soundgraph iMon if it is compatible with Ubuntu.  

As far as a CD/dvd burner player, I think I was goign to get a sony one taht was around $30.

As far as teh different hdd, how large of a drive would I need to run my OS?  80 gig is too much I take it?

I will get a 3rd hard drive at a later time for the RAID setup, but I want to get the RAID system set up now so that I can just easily add the 3rd hdd later.

---

### Post by theacoustician on 2008-02-13
> **PsychedelicWonders said:**
> So what processor will i need to get to run HD MPEG4 AVC (ie H.264) or HD VC-1 material?

What kind of material comes in that format?

Also what advantages are there to using an actual raid card?

I have a case picked out, I may change it up but I am more worried about having the internals set up right.

The remote, I think I was going to go with the Soundgraph iMon if it is compatible with Ubuntu.  

As far as a CD/dvd burner player, I think I was goign to get a sony one taht was around $30.

As far as teh different hdd, how large of a drive would I need to run my OS?  80 gig is too much I take it?

I will get a 3rd hard drive at a later time for the RAID setup, but I want to get the RAID system set up now so that I can just easily add the 3rd hdd later.

1080 material in MPEG4 AVC and VC1 comes from Blu-ray/HDDVD rips and from some recorded broadcasts, mainly the BBC for now.

Hardware RAID is much more resiliant and reliable than software RAID.  However, if you're just mirroring drives, there probably is no advantage for one over the other.  I mention the drives because you have 2 80 gig drives and 1 250 gig drive.  I was just a little confused over what you wanted to accomplish with that, unless its just a cut and paste error.  80 gig is more than enough for a OS drive.  You could probably get away with a 16gig SSD if you're interested.

---

### Post by PsychedelicWonders on 2008-02-13
Ahh I would def like to be able to play blu-ray, but how much is a processor that is able to do so?  If it is quite a bit, I may just wait to upgrade that later when I obtain a blu-ray drive when they become more affordable.

Other than mirroring drive, what else is RAID used for that a card would come into play?

On the 2 80g hdd, that was just a copy and paste error, sorry.  I plan on doing 2 250g once I get some more money to do so.

My other reasoning in using an 80g hard drive is to partition it in half, one for Ubuntu and the other for windows in case there are some programs that wont run properly on the ubuntu side.

But is there perhaps a chance of the windows partition getting viruses and spyware and then transfering them over to the Ubuntu partition and ruining the hdd?

Idealy I would like 2 hdd for each OS, but I don't believe there is enough hdd space in the HTPC case I want.

is the iMon remote compatible with that MythTv?  Ive heard good things about Myth and I have heard alot of bad things.  Why is there still so many bugs in it, just because it's so new?

---

### Post by miesnerd on 2008-02-13
2 things:
1.Personally, if I were buying ram for a new computer (which I did just a month ago-- got an ASUS M2a-vm mobo) I would utilize the mobo's ability to upgrade. With that in mind, I would buy 2x2 sticks of ram, shell out the extra $45. But that's just a pref.
2. Per my experience with my asus mobo, I would recommend downloading the latest bios in case you need to update it.  After I installed my ram, I was having all sorts of probs, and when i updated the bios all probs were resolved.

---

### Post by PsychedelicWonders on 2008-02-14
Anyone have a suggestion for a processor that will handle blu-ray?

I will upgrade to the extra 2g of ram perhaps now, but for sure in the near future.

---

### Post by PsychedelicWonders on 2008-02-17
I have been thinking about this blu-ray situation a lot lately.

Right now it stands that I can get that great processor for $184 and then a full dvd/cd burner and reader for probably $30.  So thats a grant total of about $215 to complete that setup.

How much of a price boost would it be in going to a processor that can handle blu-ray and a dvd/cd drive that can read them?

If the cost is too high I will probably wait till the later part of this year and just upgrade those two parts when the prices drop and I have more cash flow.

Also, what do I look for in a video card?  I don't need anything super fantasitic and really want to keep the price less than $100 (Preferably $75)  I figured 256mb with 128-bit would do the job?  Or do I need something better?  Mind you I do plan on hooking this up to a flat screen, so I am going to need one is HDMI capable right?

What is this other stuff I see associated with video cards, core clock, GDDR, pci express, does any of this really apply to what I'm looking for?

---

### Post by PsychedelicWonders on 2008-02-17
[http://www.newegg.com/product/product.aspx?item=N82E16819115029](http://www.newegg.com/product/product.aspx?item=N82E16819115029)

That is the new model of my processor I think, it's only $7 more and much faster.

Someone even reviewed it and said they got this processor so they can view blu-ray.

Is this processor in fact rated for blu-ray play?

---

### Post by PsychedelicWonders on 2008-02-17
Regarding the DVD/CD player/burner

Do I want it to be IDE or SATA?  What is the pros and cons of either or?

I think I read some where that someone couldnt play regular cd's because it was a SATA drive, does that make sense?

These are the two ive come to conclusion with..

Depending on which way is better either the IDE (PATA) or the SATA, it's between the following two ASUS..

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827135148](http://www.newegg.com/Product/Product.aspx?Item=N82E16827135148)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827135156](http://www.newegg.com/Product/Product.aspx?Item=N82E16827135156)

Or the following samsung...

[http://www.newegg.com/product/product.aspx?item=N82E16827151154](http://www.newegg.com/product/product.aspx?item=N82E16827151154)

What do you guys think and why?

Thanks for all of the help, I really appreciate it.  I need to get this going ASAP so I can finally install Ubuntu!

---

### Post by PsychedelicWonders on 2008-02-17
And for a power supply, hows this...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007)

Not looking for anything fancy, but good quality with a decent price.

---

### Post by PsychedelicWonders on 2008-02-17
Anyone?  Is there perhaps a better forum to put hardware spec questions in?

---

### Post by oldsoundguy on 2008-02-17
You do NOT have to have the hot new gaming machine specification to run Linux or even WinDOZ.  You are putting that cart before the horse.  Decide on WHAT you want to do with the machine and go from there.  Debating .7 difference in processor speed is a moot point .. you, as a human being will never be able to tell the difference.  Only reason for the faster processor is bragging rights at your next gaming lan party.

---

### Post by PsychedelicWonders on 2008-02-17
I was fine with the processor I had picked out, but someone mentioned that it will not run blu-ray.

But now the second processor I just posted a couple up, someone who bought it off newegg left a review that they bought it to run blu-ray.

So I just want to make sure that processor can run blu-ray.

---

### Post by jbman on 2008-02-18
don't worry about the CPU for the HD playback, be more concerned about the GPU on the video card. Look into something that has HDMI and will play HD content on linux well.

---

### Post by PsychedelicWonders on 2008-02-18
How do I determine if the video card will play HD well?  And especially in Linux?

---

### Post by PsychedelicWonders on 2008-02-18
Regarding the DVD/CD player/burner

Do I want it to be IDE or SATA? What is the pros and cons of either or?

I think I read some where that someone couldnt play regular cd's because it was a SATA drive, does that make sense?

These are the two ive come to conclusion with..

Depending on which way is better either the IDE (PATA) or the SATA, it's between the following two ASUS..

[http://www.newegg.com/Product/Produc...82E16827135148](http://www.newegg.com/Product/Produc...82E16827135148)

[http://www.newegg.com/Product/Produc...82E16827135156](http://www.newegg.com/Product/Produc...82E16827135156)

Or the following samsung...

[http://www.newegg.com/product/produc...82E16827151154](http://www.newegg.com/product/produc...82E16827151154)

What do you guys think and why?

---

### Post by dark_phantom on 2008-02-18
> **PsychedelicWonders said:**
> How do I determine if the video card will play HD well?  And especially in Linux?

Just look for a card that's HDCP enabled or complaint.  I also heard that you need a 2.6 GHz or better processor to decode HD content, but I'm not an expert on this.  You don't need a RAID card if your mobo can do RAID.  

I'm trying to put one together myself, but for now I'm just reading on it.  Probably I'll convert my 8400 into an HTPC.

> **PsychedelicWonders said:**
> Regarding the DVD/CD player/burner

Do I want it to be IDE or SATA? What is the pros and cons of either or?

I think I read some where that someone couldnt play regular cd's because it was a SATA drive, does that make sense?



It's a matter of whether your mobo has an interface for it.  If it's a new mobo go with SATA, which is the new technology, PATA is old.  No, SATA or PATA shouldn't be a problem for reading a cd.  It was probably something else.

---

### Post by dark_phantom on 2008-02-18
A few links regarding HD with Nvidia cards.

[http://www.nvidia.com/page/purevideo_hd.html](http://www.nvidia.com/page/purevideo_hd.html)
[http://www.nvidia.com/object/pvhd_system_requirements.html](http://www.nvidia.com/object/pvhd_system_requirements.html)

---

### Post by PsychedelicWonders on 2008-06-27
Here is the mother board I am getting... will it be able to RAID/mirror my 2 hard drives for me?


[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121315](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121315)

Or will i need a card?

---

