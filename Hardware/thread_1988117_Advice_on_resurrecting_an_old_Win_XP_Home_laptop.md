---
title: "Advice on resurrecting an old Win XP Home laptop"
date: 2012-05-26
forum: Hardware
---

### Post by Face-Ache on 2012-05-26
I have also asked this question in The Community Cafe ( [http://ubuntuforums.org/showpost.php?p=11972184&postcount=22](http://ubuntuforums.org/showpost.php?p=11972184&postcount=22) ), but thought i might get some more responses and ideas from here.

Mods/Admins, feel free to delete this thread if you see it as a duplicate :)

I'm trying to resurrect an older Windows XP Home machine. It's got a 1.8Ghz processor, and 512mb of RAM, and there appears to be a few bad sectors on the HDD.

Any suggestions or advice on how i should go about bringing it back from the dead?
Are the bad sectors a sign of more problems in the future?
What distro's would you guys recommend?

Many thanks

---

### Post by ahallubuntu on 2012-05-26
I don't know what you mean by "bad sectors," but if you mean "pending sector errors" according to S.M.A.R.T., you should assume the drive is failing and expect to replace it.  SOMETIMES you can write zeros over your whole hard drive and clear pending sectors - try a program like DBAN ([www.dban.org](www.dban.org)) for that.

If you mean "reallocated sectors," those aren't fatal but they indicate that the drive's firmware has already dectected some bad sectors and replaced them.  A few reallocated sectors on an old drive isn't catastrophic, but if the number keeps increasing, the drive its way to failure.

You can probably find a used IDE/PATA hard drive (if that's what this old laptop takes) for about $30 USD for a 30GB on eBay in the US - not sure what you'd pay in NZ.

Try the Parted Magic CD (nice Linux distro full of utilities) to check S.M.A.R.T. status (SmartControl) and run tests, etc.

---

### Post by 23dornot23d on 2012-05-26
> 
Are the bad sectors a sign of more problems in the future?


Usually a sign of more serious things to come ...... not really worth messing with that drive ..... IMHO ..... pull it out and put another in its place and you are ready to go .... knowing that you are not going to be wasting your time and loosing data later .....

Drives are reasonably cheap ...... or do as I did ..... set it to boot from a USB hard drive .....  ( I actually took the internal out .... never replaced it ) just run from a [[COLOR=Blue]_**external USB hard drive**_[/COLOR]]("http://www.shopping.com/verbatim-verbatim-store-n-go-superspeed-500-gb-usb-3-0-external-hard-drive-97656-pink/info?sb=1") ..... you can get cheaper ones that are not solid state but these are quiet and light and need no other power supply.

You would need to check they are compatible and will boot ok from your laptop though.

---

### Post by Face-Ache on 2012-05-27
> **ahallubuntu said:**
> I don't know what you mean by "bad sectors," but if you mean "pending sector errors" according to S.M.A.R.T., you should assume the drive is failing and expect to replace it.

When i go to Disk Utility, under Overall Assessment, it says "Disk has a few bad sectors". When i dig a bit deeper, it says "Current Pending Sector Count", and lists 11 Sectors - so it does look those 'pending sector errors' you speak of.

I think i saw an option in the Disk Utility to write zeros over the whole drive, so i might give that a try once the data-recovery is complete. Nothing to lose really!

Heh, the data-recovery started out at 1.5mb per second, with an estimated time of 2.5 hours, now at 735kb per second, saying 6 hours. 4.4Gb out of 22.9 copied. Doesn't sound too good does it?

Thanks for the replies too.

---

### Post by Face-Ache on 2012-05-28
The data-recover completed fine, but the screen has some issues, so i'm going to swap it out with a new screen.

The existing screen has a maximum resolution of 1280 x 800 - will it be an issue if i swap in a new screen that has a resolution of 1680x1050?

Would appreciate some advice on that please  :)

The laptop is a Toshiba Satellite M40X.

---

### Post by wilee-nilee on 2012-05-28
I would not use any OS I did not install and had been used by somebody else, especially a windows setup, no matter how well I knew them being part of this.

You have the computer now and can extract the activation key, I would do that, check the laws on passed along ownership and reinstall that OS, if legal to do so.

You probably are the owner of the license now, I just suggest this as a heads up is all.

---

### Post by Face-Ache on 2012-05-28
I don't think that's an issue; i've recovered their personal data, have formatted the drive completely, and will install Lubuntu 12.04 on it once i get the screen replaced. I certainly won't be putting Windows back on it :)

---

### Post by cortman on 2012-05-28
I wouldn't mess with the bad HDD if I were you; you can get a new drive for pretty cheap if you're shrewd. For some info/inspiration on getting the old PC up and running check out [K.Mandla's blog.]("http://kmandla.wordpress.com/")

---

### Post by Blackbird_13 on 2012-05-28
I agree you shouldn't rely on a pc with bad sectors. Having said that I had an old windows xp pc which I wanted to dual boot with Ubuntu. However, because of  bad sectors Ubuntu wouldn't install. I followed the advice in the following link to resolve the bad sectors issue.
[HTML]http://ubuntuforums.org/showthread.php?t=1244058[/HTML] I was then able to install Ubuntu. I now use the pc for testing - it doesn't get used heavily, but hasn't failed in over two years.

---

### Post by ahallubuntu on 2012-05-28
> **Face-Ache said:**
> The data-recover completed fine,

You had 11 pending (bad) sectors before.  Did you check S.M.A.R.T. again to see if you still have any of them?  If you do, it's time to junk the drive.  If they are ALL gone, you can cautiously re-use the drive in my experience.  As always, it's important to make regular backups of important data (for ANY hard drive actually).  Drives can fail unpredictably.

> **Face-Ache said:**
>  but the screen has some issues, so i'm going to swap it out with a new screen.

The existing screen has a maximum resolution of 1280 x 800 - will it be an issue if i swap in a new screen that has a resolution of 1680x1050?

Most likely that won't work.  The laptop video card will likely support only a 1280x800 screen.  It's possible you could also swap video cards and install one for the laptop that supports 1680x1050, *IF* the laptop was originally sold with that option.  You would need to install a specific video card that was designed to work with this laptop; if there was no such video card, don't bother and stick with a 1280x800 screen.

You have to be really careful with screen replacement.  You don't have to get an exact replacement, but you must get a compatible replacement.  Not all 1280x800 screens are compatible, even if you can physically plug in the same cables.  Unfortunately, laptop screens are not completely standard.  If you have say a Dell Inspiron E1505, you need to get a screen that is compatible with that, not a Gateway screen that is exactly the same size.  eBay is my usual source for such screens.

---

### Post by Face-Ache on 2012-05-29
I checked SMART again, and sadly, the bad sectors were still showing. I did just do a straight format of the drive - do you think the writing 1's or 0's technique might have a better chance of 'resetting' the bad sectors?

Even if the drive is able to have a Lubuntu install on it, i certainly won't be keeping anything important on it. Will likely replace it shortly. I have to admit, on a drive with essentially millions of sectors, i'm struggling with tossing it out because 11 are bad - you know what i mean?!! :)

The original screen had some lines running down it, and in my attempts to fix these lines, i cracked it. Yep, hard to admit that, TBH; lesson learned!

So i've got a new screen coming from a different seller on that TradeMe website i mentioned earlier. They're a retailer, so i do have *some* recourse if it doesn't work, specifically as i have asked if it was compatible. It's native 1280x800, and costs a bit more than the one i was originally considering;
[http://www.trademe.co.nz/Browse/Listing.aspx?id=478107905](http://www.trademe.co.nz/Browse/Listing.aspx?id=478107905)

This was only ever really going to be a 'weekend project', one of those things to try and get usable again, just because i can. So far i'm out NZD$124.50. Another replacement HDD will likely be at the very least NZD$50+ .... *sigh* turning out to be an expensive little project!

---

### Post by ahallubuntu on 2012-05-29
A "straight format" writes almost nothing except a new partition table, so I wouldn't have expected that to change much in terms of failing sectors.  A "low level format" (takes a while) may or may not be the same as writing zeros.  I'd just use a DBAN ([www.dban.org](www.dban.org) ) CD and let it zero the drive overnight or whatever it takes.  You can speed it up by doing just one pass not the three passes DBAN defaults to.

If the drive's firmware can mark the pending sectors as "bad" it can assign spares to replace them ("reallocated sectors").  This could happen if you DBAN/zero the drive.  Or they may all just clear.  Or none of them may clear.  But if there are still pending sectors showing, even just one sector, you run the risk that the OS will try to use that sector and that could cause some issue as bad as causing a blue screen in Windows.  (I have seen a single pending sector do that.)

You COULD just take a chance and install an OS anyway, if it's not an important laptop.  Just try it and see what happens and if it seems to work, just keep an eye on it and hope none of the bad sectors gets used.

---

### Post by Face-Ache on 2012-05-29
I've burnt dban to a disc, and as soon as i get the new screen working, i'll run it and see how it goes. Fingers crossed!

Thanks for all the advice :)

---

### Post by Face-Ache on 2012-05-29
Decided i might as well get dban running now, so i've plugged in an external monitor, and am doing a single-pass write of the HDD. It's a 60GB hard-drive, and started off saying it would take 53 minutes.

It's now at just over 50% done, and saying there's another 17 hours to go!

Is it normal for a single-pass write write on a 60GB drive to take so long? Or has it just started hitting those bad sectors?

---

### Post by ahallubuntu on 2012-05-29
Yes, I think it started hitting those bad sectors.  53 minutes sounds about typical.  Time to put that drive to rest I fear.

---

### Post by Face-Ache on 2012-05-29
I saw your post, but thought i'd leave it for a while longer - nothing to lose but a bit of electricity  :)

And now it's sped up again! At around 65% with an hour or so to go. Will be interesting to see what the SMART stuff says when i boot into Ubuntu once it's done.

---

### Post by ahallubuntu on 2012-05-30
Please do post the updated S.M.A.R.T. info after it's done - now I'm curious.

---

### Post by Face-Ache on 2012-05-30
dban finished and said it wiped the HDD with no problems - said 'pass' somewhere on the final screen.

After my last post, dban spent the next while speeding up and slowing down a few times. From when i started the single-pass dban wipe, it has taken approximately 20 hours to complete on a 60gb drive.

I'm probably not going to fire it up again until the replacement screen has arrived and been installed, but i'll post the SMART results as soon as i have them to hand.

---

### Post by Face-Ache on 2012-05-31
Okay, new screen is installed, and working fine.

I've booted to my Ubuntu 11.10 USB install, and SMART says the disk is fine - see attached. So i'm pleasantly surprised.

My next step is to proceed with a Lubuntu 12.10 install to this HDD, and take it from there.

---

### Post by ahallubuntu on 2012-05-31
That's great news.  Personally, I would recommend also running the extended S.M.A.R.T. test on the drive before you install anything - then check S.M.A.R.T. status one last time.  If still no issues, go for it!

---

### Post by Face-Ache on 2012-06-01
Ran the extended SMART stuff, all good, so proceeded with the install, and again, all good! I'm currently posting this from my new Lubuntu 12.04 install  :)

I'm not going to be keeping anything important on this HDD, and the machine will likely be my experimental PC/Laptop to break and then try and fix. Will be interesting to see how long the HDD lasts.

At the moment, i'm pretty happy with how it's panned out.

---

