---
title: "System Design (Hardware Selection)"
date: 2010-12-29
forum: Hardware
---

### Post by earnshae on 2010-12-29
Hello,

I am currently designing a new PC and trying to select hardware and I was hoping to leverage some community experience so that I have the minimal amount of problems when assembling the final system.

Is this the right place to post these kinds of questions? The description of the forum, says it is for people having problems with hardware after install... Where I don't have problems yet... I am trying to make sure that any hardware I purchase will work well, and meet my design goals. If it is not can you please suggest a forum where these types of questions should be posted?

Thank you, for your time.

---

### Post by IcarusR on 2010-12-29
We need a bit more info. What is this system to be used for, gaming, surfing net, word processing or as a server ??

---

### Post by cascade9 on 2010-12-30
> **IcarusR said:**
> We need a bit more info. What is this system to be used for, gaming, surfing net, word processing or as a server ??

Budget and location would be good ideas as well. ;)

---

### Post by VonSpyder on 2010-12-30
since you said PC i am assuming you are looking at building ajack of all tradesmachine:something that is okay at everything but not great at any one thing. in such an event heres some suggestions:

Hard drives: have two of them. one for linux and one for whatever else.

Vid card: Nvidia or ATI. Im partial to ATI but Nvid support is a touch better. do not use on board video. ever. its evil.

Soundcard: Soundblaster. Nuff said.

Power supply: nothing less than 400watts.

that is all.

---

### Post by earnshae on 2010-12-30
Okay here are a few details
Budget 3k (CAN)

Purpose
Research(Number Curnching)
Development(Write/Compile Code)
Virtualiation(Multiple OS Virtual Machines running concurrently require windows/os x for specific apps)
Design(CAD)

Gaming
Low requirements-Done through virtualization

Want
Three monitor support. (3x6" @ 1920x1200)
Space for nVidia Tesla Card (Future)
High degree of paralism.

CPU i7 970/980 (probably 970)
RAM 12GB to 24GB
HD Shopping around
Video... Looking for recomendations to meet the want list.
Motherboard... Looking for recomendations.
Cooling... not sure if I need an advanced cooling system yet...

Anything I am missing?

---

### Post by gordintoronto on 2010-12-30
If you need OS X, you need an Apple.

Your applications don't appear to require a high-end video card.

Do you really, really need a third monitor? I hear an undue number of complaints from people trying to set up a third monitor.

The CPU you selected comes with a cooler. Unless you plan to overclock, the standard cooler is fine -- and keeps the warranty in force. Pay attention to airflow in the case, not specifically for the CPU.

You can afford to have an SSD for program loading, and WD "black" hard drives for data. Unless the research involves huge files, I suggest 640 GB hard drives, which have better reliability than huge drives.

PCMech has forums where people could give you better help than you will find here -- especially about current motherboards.

Finally, wait until after CES....

---

### Post by cascade9 on 2010-12-31
3k with monitors, or without? 

You could get a i970 system going for 3k without monitors (not that I would), but with monitors...Near enough to $1K on just he CPU , its going to be very tight. 

> **VonSpyder said:**
> Soundcard: Soundblaster. Nuff said.

Noess! Not creative. 

Asus makes some great sound cards and there is always m-audio as well. 

> **gordintoronto said:**
> If you need OS X, you need an Apple.

Do you really, really need a third monitor? I hear an undue number of complaints from people trying to set up a third monitor.

The CPU you selected comes with a cooler. Unless you plan to overclock, the standard cooler is fine -- and keeps the warranty in force. Pay attention to airflow in the case, not specifically for the CPU.

You can afford to have an SSD for program loading, and WD "black" hard drives for data. Unless the research involves huge files, I suggest 640 GB hard drives, which have better reliability than huge drives.

PCMech has forums where people could give you better help than you will find here -- especially about current motherboards.

Finally, wait until after CES....

You dont 'need' an apple for OSX. It might be against the EULA to install OSX on 'non-apple branded hardware' but it does work. 

+1 on the 3rd monitor. 

Running a aftermarket CPU cooler might technically break warranty on CPUs, but I've never had a problem RMAing CPUs that used an aftermarket heatsink/fan. Agreed though, you dont 'need' a aftermarket heatsink/fan. 

OK, 640GB HDDs are more reliable? Source, please, this sounds interesting.

---

### Post by earnshae on 2010-12-31
For some reason it didn't post my original reply.

Budget is Without monitors.

Definitely running the three monitors I wish I could do more . Combined with the multi desktop from Ubuntu productivity gets sick. Especially give the type of work I am currently doing.

Basically the way I set it up is lhs, shell 2-4 sessions for task at hand. mid IDE/text editor usually split into 2 views for easy cross refencing code,  web browser (task at hand reference) + constant apps I like to float my chat sessions and email across all desktops. I then assign desktops specific. Ie for one of my clients I need a windows box, so I keep it on desktop 4 with similar materials, so if I need to work for that client bang desktop four and go.

Thinking of using an ATI Eyefinity as the video card, the comments here seem mixed, anybody have any experience for this card in 10.10?

---

### Post by gordintoronto on 2011-01-01
> **cascade9 said:**
> OK, 640GB HDDs are more reliable? Source, please, this sounds interesting.

This is based entirely on the ratings on Newegg. I know, many of the people who enter ratings are biased, but I think that probably applies to all the products.

For hard drives, the bulk of the poor ratings are a result of DOA or "dead within three months."

An example of two drives which rank fairly high within their respective segments:
WD Black 640: 87% 4 or 5 eggs, 9% 1 or 2 eggs. (More eggs is better, 5 is the maximum.)
Samsung 1.5 TB "eco green": 74% 4 or 5 eggs, 19% 1 or 2 eggs. The Samsung was ranked 7th out of 42 drives larger than 800 GB, so there are a lot of drives which got worse ratings.

Once again, I understand that Newegg ratings are imperfect, but they do provide some basis for comparison. In this case, the anecdotal evidence I have read is consistent with the Newegg ratings.

In the summer of 2009 I built a new computer, the first time I've ever started with an empty box. I made heavy use of the Newegg ratings to select components, plus comments I read on the PCMech web site. The system worked the first time I turned it on, and has been completely reliable since then.

---

### Post by 0004tom on 2011-01-01
> **earnshae said:**
> Thinking of using an ATI Eyefinity as the video card, the comments here seem mixed, anybody have any experience for this card in 10.10?

Eyefinity isn't a card it's a feature in the HD5/6xxx series cards.

All off the HD6xxx series cards to date are eyefinity compatible, only a select few in the HD5xxx series are. If your looking into a HD5xxx series card you need to a card with a Display Port output.

You don't need an monitor with Displayport input tho, as you can get DP > DVI/VGA adaptors that work a treat.

Also i've used eyefinity on a number of cards, with ubuntu/arch linux, HD5450/5750 and currently on a HD6850

Even tho the HD6xxx are not yet supported in linux, they will use the HD5xxx driver, you will just get a watermark in the bottom right hand corner of each screen. which can be removed however.

Oh, can I also add, that FGLRX isn't the only option now for triple head support, the open source Radeon Driver supports 3 outputs in the same way as eyefinity. You do however lose quite a bit of performable as it's still in heavy development.

---

### Post by cascade9 on 2011-01-02
> **gordintoronto said:**
> This is based entirely on the ratings on Newegg. I know, many of the people who enter ratings are biased, but I think that probably applies to all the products.

For hard drives, the bulk of the poor ratings are a result of DOA or "dead within three months."

An example of two drives which rank fairly high within their respective segments:
WD Black 640: 87% 4 or 5 eggs, 9% 1 or 2 eggs. (More eggs is better, 5 is the maximum.)
Samsung 1.5 TB "eco green": 74% 4 or 5 eggs, 19% 1 or 2 eggs. The Samsung was ranked 7th out of 42 drives larger than 800 GB, so there are a lot of drives which got worse ratings.

Once again, I understand that Newegg ratings are imperfect, but they do provide some basis for comparison. In this case, the anecdotal evidence I have read is consistent with the Newegg ratings.

In the summer of 2009 I built a new computer, the first time I've ever started with an empty box. I made heavy use of the Newegg ratings to select components, plus comments I read on the PCMech web site. The system worked the first time I turned it on, and has been completely reliable since then.

Interesting. I dont think its reliable, but still interesting.

---

