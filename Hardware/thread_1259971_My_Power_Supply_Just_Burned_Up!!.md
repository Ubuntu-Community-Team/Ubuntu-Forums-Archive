---
title: "My Power Supply Just Burned Up!!"
date: 2009-09-07
forum: Hardware
---

### Post by dodle on 2009-09-07
My computer (not a laptop) was working fine and had been for a long time.  Tonight I decided to install two more hard drives for extra space, one IDE and an SATA.  Afterwards, I connected the power supply to the wall outlet, the machine immediately turned on without hitting the power button.  I heard a high pitched screeching noise and smelled something burning.  Immediately I shut down the machine.  I disconnected all of the hard drives and tried powering up again.  The result was the same exact scenario.  I then removed the power supply from the machine and tried plugging it into the wall by itself, same thing.  

My power supply is an Antec PS-500.  I went to Antec's sight to see how long their warranties last, 3 years.  I've had it for 4 years now, and it's got quite some mileage on it.  Now I have taken it apart am looking for parts that look burnt out.  I just learned how to solder, so I hope that this is something that I can replace.  

Any advice on what the problem could be?  Similar experiences?  What to look for?  

Could this have happened because of something that I did, or does it sound like the power supply could just be getting old?

---

### Post by Whiffle on 2009-09-07
Screeching noise sounds like fan.  But if you smelled something burning, it may be hard to track down (burnt insulation maybe), and could be problematic in the future if not fixed properly.  I've been soldering for a while now, and I'm not certain i'd be comfortable making repairs to a power supply unless it were something blindingly obvious.  I'd probably just be happy it didn't take my motherboard with it, and go buy a new one.

And 4 years sounds about right.  Sometimes they live forever, but that is about how long my last Antec lasted.

---

### Post by dodle on 2009-09-07
Thanks for your quick reply.  After looking around inside I found 2 components that look like they may be the problem.  I'm not sure what they are called but "capacitor" comes to mind, so that's what I'll call them.  They are tubular, and the silver ends of them are slightly puffed out.  I've heard that when the ends are puffed out that they are bad.  But I expected the "puffing" to be more extreme.  

I really don't want to pay for a new power supply.  Does it sound like it's worth a try to replace these "capacitors"?

---

### Post by Whiffle on 2009-09-07
Sounds like capacitors, and it does sound like they're toast.  And now that I think about it, the screeching noise might have been them.  If you can identify what capacitance they are (they should be labeled), and find suitable replacements, they shouldn't be difficult to replace.  And if it works, then good deal.

---

### Post by dodle on 2009-09-07
Thanks a bunch.  I'm going to try and find replacements tomorrow.  My brother has more experience soldering than I do, so I'm going to seek his help.  I'll post whether it works or not.

---

### Post by dodle on 2009-09-08
We successfully replaced the capacitors, but it didn't fix the problem.  The "screeching" continues.

---

### Post by RabidWeezle on 2009-09-08
There's some things that should just be replaced, power supplies being one of them, don't risk frying your motherboard and componants over a 50 dollar power supply. Also, faulty power supplies are known to cause electrical fires.

---

### Post by Whiffle on 2009-09-08
Yeah I'd give it a toss.  If it were just the capacitors I wouldn't be worried, but it sounds like there is more to it than that.  I was hoping it was just a couple of those bad capacitors that have been floating around the last few years.

---

### Post by GoldenSun on 2009-09-08
You can get a nice psu on newegg for $50 that is better than that antec.  I would look at Corsair for decent psu's.  If you catch them on sale, you can get a godly deal.  

You should keep you old psu and continue to figure out what's wrong with it.  If you ever get it in some kind of working condition, you could test fans or other hardware before putting it in your case.

---

### Post by dodle on 2009-09-08
I put in a power supply that is < 200watts to try and make sure everything was okay.  I switched out my video card with an old one that the power supply could handle.  Apparently, my hard disks got fried.  The mobo isn't recognizing either of them.  

These drives have invaluable stuff on them that I hadn't got backed up yet.  Is there any way to get the data off of them?  Can I send them into the manufacturers to get fixed?

---

### Post by Whiffle on 2009-09-08
> **dodle said:**
> I put in a power supply that is < 200watts to try and make sure everything was okay.  I switched out my video card with an old one that the power supply could handle.  Apparently, my hard disks got fried.  The mobo isn't recognizing either of them.  

These drives have invaluable stuff on them that I hadn't got backed up yet.  Is there any way to get the data off of them?  Can I send them into the manufacturers to get fixed?

Or is the motherboard fried?  I would think that more likely than the hard disks.  Try the hard disks in another computer to be sure.

---

### Post by GoldenSun on 2009-09-08
you can run a program called photorec on them to recover lost files.

---

### Post by dodle on 2009-09-08
The mobo seems to be fine.  I can run a live Ubuntu disk.  Both IDE ports appear to be working fine.  I did try one of the drives in an older computer.  It didn't work.  

One is formatted Ext3 and the other is NTFS.  

@ GoldenSun:
The drives aren't recognized, I don't think Photorec will work.

---

### Post by Whiffle on 2009-09-08
If you can find a newer computer, I would try that, despite the connectors being the same, there can be other compatability issues, but it doesn't sound good so far.

If you can find a drive of the exact same kind, and I do mean exact, sometimes you can switch the circuit boards on the bottom, since that is usually what gets damaged, and then access the data on the drives.  Otherwise you're pretty much stuck sending them off to some data recovery business.

And this is why I never ever cheap out on a power supply, they tend to take other things with them.

---

### Post by dodle on 2009-09-08
I agree, I probably won't ever buy Antec again.  I thought they were pretty reliable.

I'll try to find a newer computer to test these on.

Thanks for your help everyone.

---

### Post by dodle on 2009-09-09
I went to my brother's house and tested the hard drives on his computer which still doesn't recognize the drives.  Tomorrow I am going to contact Maxtor and Western Digital to see if I can get the drives repaired.  On the Maxtor I can see a physical burn on one of the chips.

---

### Post by dodle on 2009-09-09
I just found a matching logic board for one of my hard drives on Ebay.  It has the same model number: WD800JB-00JJC0.  But the DCM number is different.  I'm not sure what DCM is.  Will it still work?  I really need to get this drive working.

---

### Post by Whiffle on 2009-09-09
[quote=webpage]
DCM: CVJAA 
This is very important when replacing the internal read write heads of a drive. The last 5 digits of the DCM number will need to match the original drive for compatible heads, But most importantly I have found that you can match this DCM number across several models e.g. WD200BB and WD200JB will Work... this is also the same between the silver top WD and  Black top WD will still be compatible. I have also had the odd drive that is larger than the drive I needed with the same DCM and more heads than what I need but I found the extra heads where deactivated and still worked.[/quote]

[http://www.harddrive-repair.com/hard-drive-parts.html](http://www.harddrive-repair.com/hard-drive-parts.html)

sounds like you're good so long as you're not trying to match heads.

---

### Post by dodle on 2009-09-10
I hope this all works out.  I ordered a board for my Maxtor drive first.  I found one that was identical to the board in my drive.  If it works, I'll go ahead and get one for the Western Digital.  Thanks again.

---

### Post by dodle on 2009-09-13
I received the circuit (logic) board for my Maxtor hard drive.  It works perfectly now.  Thanks for the advise on changing boards Whiffle.  I'll be backing up my data right away.

> **Whiffle said:**
> [quote=webpage] Originally Posted by webpage
DCM: CVJAA
This is very important when replacing the internal read write heads of a drive. The last 5 digits of the DCM number will need to match the original drive for compatible heads, But most importantly I have found that you can match this DCM number across several models e.g. WD200BB and WD200JB will Work... this is also the same between the silver top WD and Black top WD will still be compatible. I have also had the odd drive that is larger than the drive I needed with the same DCM and more heads than what I need but I found the extra heads where deactivated and still worked.[http://www.harddrive-repair.com/hard-drive-parts.html](http://www.harddrive-repair.com/hard-drive-parts.html)

sounds like you're good so long as you're not trying to match heads.[/QUOTE]

Thanks again, this will be very helpful in finding a compatible board for my WD.

---

### Post by Whiffle on 2009-09-13
Awesome. :)

---

