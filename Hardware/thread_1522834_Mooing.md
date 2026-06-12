---
title: "Mooing"
date: 2010-07-02
forum: Hardware
---

### Post by Total Noob on 2010-07-02
My computer is pretty old, and it seems to heave like a mooing cow, one at death's doorstep, laboring to breathe.

Is it done? Is it the hard drive giving out?

Thanks.

---

### Post by howefield on 2010-07-02
Without a doubt, bovine mooing in your machine is terminal.

May it rest in peace !!


PS.
On second thoughts, you're not playing some weird mp3, are you ?

---

### Post by SoFl W on 2010-07-02
That or you are just running the original Citadel BBS software.  M)oo!

Of course ubuntu will moo for you too... if you know how.

---

### Post by paulisdead on 2010-07-02
I assume you mean it's making some odd noises?  It could be the drive, but there's the possibility it's a fan as well.  They can collect dust, and become unbalanced, which will create odd noises well.  Sometimes cables get pressed into fans or drives and the vibration can make odd noises, too.  Probably not a bad idea to pop the side off and power it on, carefully, and try to track down exactly what is making that noise.  If you're really worried about the drive, grab the drive manufacturer's testing tools from their site, and run them.  Is the mooing at any specific time or when you do something specific?

---

### Post by Total Noob on 2010-07-06
> **paulisdead said:**
> I assume you mean it's making some odd noises?  It could be the drive, but there's the possibility it's a fan as well.  They can collect dust, and become unbalanced, which will create odd noises well.  Sometimes cables get pressed into fans or drives and the vibration can make odd noises, too.  Probably not a bad idea to pop the side off and power it on, carefully, and try to track down exactly what is making that noise.  If you're really worried about the drive, grab the drive manufacturer's testing tools from their site, and run them.  Is the mooing at any specific time or when you do something specific?

All good ideas. Thanks. The unit gives a groan perhaps once every 30-45 seconds all the time, regular but not exactly Old Faithful exact.

---

### Post by djinnkeeper on 2010-07-06
Is there vibration?  Are the fans operational?  Do you hear any squealing accompanying the "mooing" ..?  Too bad you can't make a recording for us to hear! :popcorn:
..and please.. unless you know what you're looking for, don't go "popping off" the side panel while it's running.  If you do, for God's sake don't go poking around in there.. and close it up quickly because the side panel is making the airflow work (the average desktop-tower will overheat if you leave the side panel off while it's running..)

---

### Post by pricetech on 2010-07-06
If I understand your definition of "mooing", it's probably a cooling fan.  Start by cleaning it thoroughly with compressed air.  If that doesn't work, replace it.

It it's the one inside the power supply, it is not recommended you open the power supply to service it.  Whether or not you actually do is up to you depending on how comfortable you are with electronic gadgets and how careful you are when working around potentially dangerous, perhaps deadly, voltages / currents.

---

### Post by cascade9 on 2010-07-06
30-45 seconds between noises, its *probably* not a fan IMO. 

I'd check 'htop' and see if the nosies conincide with data being written to swap.

---

### Post by Total Noob on 2010-07-07
Overnight, I replaced the hard drive and the cd player, blew it out with compressed air, and installed two versions of Linux. The mooing continues, but at a lower volume.

It may be the power supply fan, so I'm going to reopen the case and clean it again with compressed air.

Should I lubricate the fan with some WD-40 spray or 3 in 1 oil?

Thanks.

---

### Post by endotherm on 2010-07-07
usually if I am trying to figure out which fan is misbehaving, I just touch each of them in the center to slow them down. if the noise ceases at the same time, then I know I have found the culprit. 

based on your description (btw mooing computer => hilarity) I would be inclined to blame a hdd, but not entirely certian what you are hearing. 

No I would not recommend any fluid lubricant on the fans, but some graphite power would work nicely. usually once a fan is making bad noises though, the bearings or the sleave are damaged. since they are cheap parts made to be replaced, I'd just get a few new ones.

---

### Post by rivenathos on 2010-07-07
"Mooing" is a pretty good description of the sound, to be sure.  ;-)  

I can share to having heard a similar sound in relation to IBM/Hitachi Deskstar hard drives.  These were drives whose model numbers matched up with the infamous "Deathstar" drive fiasco of a few years back.  These drives still functioned just fine, but made a "mooing" sound every so often.  One of the users described the drive as "sounding like the ice maker in his refrigerator getting ready to dump cubes."  Different drives had different levels of the sound.

While this may not be the exact problem of the original poster, it may be something to consider checking out - especially if the secondary hard drive used for testing was of the same make/model.

---

### Post by recluce on 2010-07-08
Try to install smartmontools and run a couple of tests:

sudo smartctl --test=short /dev/sda

sudo smartctl --test=conveyance /dev/sda

Obtain the results with sudo smartctl -a /dev/sda

"sda" stands in for whatever drive you want to test. While the tests cannot provide assurance that your drive is OK (in case the tests find nothing), they can alert you if they do find a problem.

Also, the tests work the mechanics quite hard, so it might provoke the "mooing", if the drive is to blame.

---

### Post by Total Noob on 2010-07-08
Thanks. I'll give that stuff a whirl.

---

