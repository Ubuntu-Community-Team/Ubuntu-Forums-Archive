---
title: "[SOLVED] Hard Drive Failure?"
date: 2008-06-27
forum: Hardware
---

### Post by seuzy13 on 2008-06-27
This is not particularly an ubuntu problem (it is related to hardware in general), but I have found this a helpful community, so I am going to seek advice here.

My church's laptop (XP Professional) which we use to store sermons and project song lyrics onto our screen, has recently taken a turn for the worst. The computer is getting a PXE error on start up. I have found various articles about this on the internet (see bottom of post) and they all seem to point to one thing. A hard drive problem. It is possible that the hard drive is just busted, but I have a lot of people depending on me, and I would like to restore it if at all possible. My hopeful thoughts are that it is simply a bad hard drive connection that I can remedy by snapping or plugging something back in. This is probably not the case, but if it is, I would like some experienced advice for checking that the hard drive is connected properly and fixing the connection if need be.

The computer makes crazy buzzing noises when I turn it upside down while it is running, and it makes unusual noises when attempting to boot as well.

Thank you!

Links:
[http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/06/pxe-e61-failure-error-when-booting/](http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/06/pxe-e61-failure-error-when-booting/)
[http://www.computerhope.com/issues/ch000706.htm](http://www.computerhope.com/issues/ch000706.htm)
[http://www.computerhope.com/issues/ch000229.htm](http://www.computerhope.com/issues/ch000229.htm)

EDIT--By the way, I *am* able to boot from a CD. I have booted it up with my 8.04 live CD, and gparted does not detect the hard drive, so that leads me to believe that is the cause for the problem.

EDIT2--Actually, now, after the live CD was irresponsive and I had to force shut down. The computer boot message is 
"A disk read error ocurred
Press Ctrl+Alt+Del to Restart"
It now even refuses to boot from a CD.

---

### Post by russlar on 2008-06-27
This sounds like a hard drive on the way out. My advice would be to get a replacement ASAP, and get a tool like Norton Ghost to move the existing system on the failing hdd to the new one.

---

### Post by thideras on 2008-06-27
If the drive is somewhat functional, you should be able to remove it and install it into a known working desktop.  You won't boot from it, but instead just load from the main drive and pull all the data off.

If it is a SATA based drive, you need no tools, it plugs in just like its 3.5" brother.

If it is an IDE based drive, you will need a tool like this to convert it:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812203012](http://www.newegg.com/Product/Product.aspx?Item=N82E16812203012)



Basically if the drive itself works, data recovery is simple.  If the drive is toast, there is going to be little you can do.  If it is mechanical failure (bearings, etc), the only way is to send it in to a data recovery center which is very expensive.  If it is electronic failure, you can swap the logistics with a same make and model drive.

---

### Post by seuzy13 on 2008-06-27
Any particular advice on how to do this? We never backed-up the data (I wasn't really aware of our backing-up system, 'cause I wasn't particularly in charge of this computer). So, essentially we've lost a few years of sermons, though I think many of them our on CDs and minidiscs scattered all over the place. A new hard drive may or may not be in our budget. We do not have an XP install CD or a copy of Norton Ghost either. This could total a few hundred dollars before its all said and done easily. The pastor REALLY does not want to go back to using an overhead even for a short time, so...

I also have absolutely no experience with installing a new hard drive. *shrugs* 

As to the second post:
I do not know whether it is SATA or IDE. Way to check for this?
Also, since gparted could not detect it from the live CD, it may seem as though it is toast, correct?

Thanks

---

### Post by seuzy13 on 2008-06-27
I booted up using a WinXP recovery disc. When I go into the recovery console, it is able to detect the hard drive, because as it is starting up it displays on the bottom that it is examining the drive and displays the correct size for it as well. Hopefully, this is a good sign?

---

### Post by russlar on 2008-06-27
> **seuzy13 said:**
> I booted up using a WinXP recovery disc. When I go into the recovery console, it is able to detect the hard drive, because as it is starting up it displays on the bottom that it is examining the drive and displays the correct size for it as well. Hopefully, this is a good sign?

It is a good sign, but if the hardware fails it's game over.

---

### Post by seuzy13 on 2008-06-27
Well, I'm pretty sure the hard drive is IDE...which means if I were to hook it up to a desktop to get the files out, I would need an adapter. I know they don't cost much, but I don't want to purchase something without being sure it will work...

Thoughts? Ideas?

---

### Post by mykrob on 2008-06-27
if you dont want to spend anything, your best bet is to take the hard drive out and "slave" it into another working machine. Provided the other machine can read the hard drive, you can copy the data onto the good hard drive.

---

### Post by seuzy13 on 2008-06-27
Do you have a link or something explaining how to do this? (It's not that I don't want to spend anything. I just don't want to spend money needlessly.)

Thanks!

---

### Post by thideras on 2008-06-28
> **mykrob said:**
> if you dont want to spend anything, your best bet is to take the hard drive out and "slave" it into another working machine. Provided the other machine can read the hard drive, you can copy the data onto the good hard drive.The only issue is if it is an IDE based drive.  They use a more dense pin configuration, which means you need a converter to plug into a conventional IDE cable.

OP:  I would suggest checking some local computer shops, there are probably some that either have the part you are looking for or would be willing to help you.  I know around here they are extremely helpful :).  About the only way to salvage the data if a live CD can't read it is to put it into a desktop.  If you do not have experience, I'm sure there is someone around you willing to help you out.

---

### Post by seuzy13 on 2008-06-28
All right, I'll see what I can do with that. Thank you. I'll post if I have any updates or further questions, but in the mean time, I think I have enough to go on.

---

### Post by seuzy13 on 2008-06-28
I talked with Pastor who had taken it to geek squad earlier, and I neglected to ask the details of his findings there. It appears that they too said the hard drive was zonked and took it to a back room and hooked it up to another computer. This computer did not recognize it. Of course, they said they had ways to get the data off (ranging from $500 to $1500--which is not worth it, obviously). I'm not sure exactly how they went about hooking it up to another computer, but it seems that it's basically toast and there's not much to do for it. 

However, it would still be nice to restore it to working order by buying a new hard drive instead of getting rid of it all, because it's still a very much working system otherwise. I found the same hard drive model and make on ebay for under $50, but I'm wondering if I should spring for a better one, and if it would work with the computer. I'm also not certain how to install it, configure BIOS, etc.

I've been searching the net for answers, but haven't had much luck.

---

### Post by thideras on 2008-06-30
Honestly, I wouldn't put much faith behind Geek Squad.  They are salesmen, not techs.  I'm sure you can find someone that knows what they are doing to help you ;)

---

### Post by seuzy13 on 2008-06-30
Yep, I've never been a fan of people that fix computers for their profession, because they over charge and never seem to do it right. I'd rather do it myself and gain the experience. But, you know, I was the one of the last to get into the project of fixing it.

Anyway, I think he is just going to get a new computer and leave me to do what I want with this one. So, I'm not so much worried about the data any more (though all the songs will have to be reprogrammed into the new computer...probably by me).

If I replace the hard drive with the same model, it will only be 40GB. Wondering if I can go for a better one? Say 80GB? If so, what sort of specs should I follow. The one in their now is an IDE 2.5" 5400 RPM, etc., etc.

Once more, thanks for the help you are providing!

---

### Post by Tomatz on 2008-06-30
> **seuzy13 said:**
> This is not particularly an ubuntu problem (it is related to hardware in general), but I have found this a helpful community, so I am going to seek advice here.

My church's laptop (XP Professional) which we use to store sermons and project song lyrics onto our screen, has recently taken a turn for the worst. The computer is getting a PXE error on start up. I have found various articles about this on the internet (see bottom of post) and they all seem to point to one thing. A hard drive problem. It is possible that the hard drive is just busted, but I have a lot of people depending on me, and I would like to restore it if at all possible. My hopeful thoughts are that it is simply a bad hard drive connection that I can remedy by snapping or plugging something back in. This is probably not the case, but if it is, I would like some experienced advice for checking that the hard drive is connected properly and fixing the connection if need be.

The computer makes crazy buzzing noises when I turn it upside down while it is running, and it makes unusual noises when attempting to boot as well.

Thank you!

Links:
[http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/06/pxe-e61-failure-error-when-booting/](http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/06/pxe-e61-failure-error-when-booting/)
[http://www.computerhope.com/issues/ch000706.htm](http://www.computerhope.com/issues/ch000706.htm)
[http://www.computerhope.com/issues/ch000229.htm](http://www.computerhope.com/issues/ch000229.htm)

EDIT--By the way, I *am* able to boot from a CD. I have booted it up with my 8.04 live CD, and gparted does not detect the hard drive, so that leads me to believe that is the cause for the problem.

EDIT2--Actually, now, after the live CD was irresponsive and I had to force shut down. The computer boot message is 
"A disk read error ocurred
Press Ctrl+Alt+Del to Restart"
It now even refuses to boot from a CD.


I will pray for it....

Seriously though does it make clicking noises like a solenoid switch?

---

### Post by thideras on 2008-06-30
> **seuzy13 said:**
> Yep, I've never been a fan of people that fix computers for their profession, because they over charge and never seem to do it right. I'd rather do it myself and gain the experience. But, you know, I was the one of the last to get into the project of fixing it.

Anyway, I think he is just going to get a new computer and leave me to do what I want with this one. So, I'm not so much worried about the data any more (though all the songs will have to be reprogrammed into the new computer...probably by me).

If I replace the hard drive with the same model, it will only be 40GB. Wondering if I can go for a better one? Say 80GB? If so, what sort of specs should I follow. The one in their now is an IDE 2.5" 5400 RPM, etc., etc.

Once more, thanks for the help you are providing!If you want to replace it, any 2.5" laptop hard drive that is IDE *should* work.  I would suggest removing the drive to see what type of configuration it is.  Go to a website like Newegg that has detailed pictures of the drive and do a search for 2.5" drives, 5400rpm and the price range you want.  Find one that fits what you want and that has the same interface.

Depending on the laptop, it might have a custom interface where you can only replace it with an OEM supplied drive.

---

### Post by seuzy13 on 2008-06-30
*should*?

How can I determine if it has a custom interface that can only replaced by an OEM supplied drive? I've opened it up and looked at the hard drive. Aside from the fact that it's in this special case (which I could just slip the new one into), it *looks* like anything of the same size would fit.

---

### Post by thideras on 2008-06-30
> **seuzy13 said:**
> *should*?

How can I determine if it has a custom interface that can only replaced by an OEM supplied drive? I've opened it up and looked at the hard drive. Aside from the fact that it's in this special case (which I could just slip the new one into), it *looks* like anything of the same size would fit.Yup, *should*. :)

The only way to tell if it is a "normal" drive is to take it out of its special case and compare it with ones off of Newegg (or other sites).

---

### Post by seuzy13 on 2008-06-30
I uploaded some photos of the hard drive:
[http://s3.supload.com/free/P6300011.JPG/view/](http://s3.supload.com/free/P6300011.JPG/view/)
[http://s3.supload.com/free/P6300012.JPG/view/](http://s3.supload.com/free/P6300012.JPG/view/)
[http://s3.supload.com/free/P6300013.JPG/view/](http://s3.supload.com/free/P6300013.JPG/view/)

Either I'm not looking from the right angle (I removed too much/too little) or it looks nothing like the pics on newegg. However, it does look like [this pic](http://img.auctiva.com/imgdata/4/8/9/6/0/6/webimg/145575777_tp.jpg) from ebay with some slight differences.

Also, there's this tidbit of info on the sticker, "This drive is manufactured by Seagate for OEM distribution. For product information or technicall suport, please contact your system OEM."

Is this not good?

---

### Post by thideras on 2008-06-30
Our internet is slow here, it will take a few minutes to check it and find one that will work.  Not to mention that that we have people in queue here >.<

Can you take a picture of the pins headon?  Hard to tell from the pictures what it looks like.

---

### Post by toolzen on 2008-06-30
> **seuzy13 said:**
> I uploaded some photos of the hard drive:
[http://s3.supload.com/free/P6300011.JPG/view/](http://s3.supload.com/free/P6300011.JPG/view/)
[http://s3.supload.com/free/P6300012.JPG/view/](http://s3.supload.com/free/P6300012.JPG/view/)
[http://s3.supload.com/free/P6300013.JPG/view/](http://s3.supload.com/free/P6300013.JPG/view/)

Either I'm not looking from the right angle (I removed too much/too little) or it looks nothing like the pics on newegg. However, it does look like [this pic](http://img.auctiva.com/imgdata/4/8/9/6/0/6/webimg/145575777_tp.jpg) from ebay with some slight differences.

Also, there's this tidbit of info on the sticker, "This drive is manufactured by Seagate for OEM distribution. For product information or technicall suport, please contact your system OEM."

Is this not good?

This looks like a standard 44-pin IDE connector. Any 44-pin ATA/IDE device should fit in the laptop. Also, if you want to buy a part that converts 44 pin to the normal 40 pin found on most not-so-new desktop computers, I would use an external hard drive enclosure rather than a converter. That way you can plug the drive in to the USB port, rather than cracking the case open on a computer - also some converters are really cheaply made, and can fry your drive.

If you logic board on your drive is fried, you can do as previously suggested and buy another drive of the same make/model and switch the logic boards (you'll need a special tool - I believe a hex-head? screwdriver). If you do that, your logic board will probably need the same version of firmware - be sure that you get one with the same version (you may have to call customer support, if that's easier for you).

---

### Post by seuzy13 on 2008-06-30
I did the best I could. My camera's not very good and wouldn't focus well that close up. This one was the best I got.

[http://s3.supload.com/free/P6300019.JPG/view/](http://s3.supload.com/free/P6300019.JPG/view/)


EDIT:

> This looks like a standard 44-pin IDE connector. Any 44-pin ATA/IDE device should fit in the laptop. Also, if you want to buy a part that converts 44 pin to the normal 40 pin found on most not-so-new desktop computers, I would use an external hard drive enclosure rather than a converter. That way you can plug the drive in to the USB port, rather than cracking the case open on a computer - also some converters are really cheaply made, and can fry your drive.

If you logic board on your drive is fried, you can do as previously suggested and buy another drive of the same make/model and switch the logic boards (you'll need a special tool - I believe a hex-head? screwdriver). If you do that, your logic board will probably need the same version of firmware - be sure that you get one with the same version (you may have to call customer support, if that's easier for you).

Ah, thank you. Didn't see your post on the next page.

So, would something such as [this](http://cgi.ebay.com/SEAGATE-100GB-LAPTOP-HARD-DRIVE-ST9100822A_W0QQitemZ120277536067QQihZ002QQcategoryZ158852QQssPageNameZWDVWQQrdZ1QQcmdZViewItem) work? I looked it up on seagate.com and it is a 44-pin connector, but it doesn't look exactly like mine. It has two extra pins off to the side, while mine has four little pins arranged in a square off to the side. These four don't appear to plug into any thing when I connect the hard drive.

I looked up my hard drive model too (don't know why I didn't think about it before). It's a ST94011A, and it's listed as having 44 pins as well. But I'm still wondering about the differences in placement, etc.

One more thing, I've been looking at the place where the hard drive plugs in, and it is built with screws or metal blockings of some sort around the place where the pins are inserted, so that if the pins don't stick out from the hard drive, they won't be able to plug in, because the sides of the hard drive would hit the screws/blockings. Not sure how to describe it, but that doesn't look very promising considering how the various hard drives I've been looking at are shaped. For example, [this](http://i2.ebayimg.com/03/i/000/fa/c7/d65e_1.JPG) one would not fit because either side around the pins would hit the screws and you wouldn't be able to get the pins in.

---

### Post by toolzen on 2008-07-01
> **seuzy13 said:**
> I did the best I could. My camera's not very good and wouldn't focus well that close up. This one was the best I got.

[http://s3.supload.com/free/P6300019.JPG/view/](http://s3.supload.com/free/P6300019.JPG/view/)


EDIT:



Ah, thank you. Didn't see your post on the next page.

So, would something such as [this](http://cgi.ebay.com/SEAGATE-100GB-LAPTOP-HARD-DRIVE-ST9100822A_W0QQitemZ120277536067QQihZ002QQcategoryZ158852QQssPageNameZWDVWQQrdZ1QQcmdZViewItem) work?

Yes, and in my humble opinion Seagate makes the best drives - most have a 5 year warranty.

>  I looked it up on seagate.com and it is a 44-pin connector, but it doesn't look exactly like mine. It has two extra pins off to the side, while mine has four little pins arranged in a square off to the side. These four don't appear to plug into any thing when I connect the hard drive.

These are the pin jumpers - most likely there is another device that is attached to the same cable (probably the CD rom). The pin jumpers tell the BIOS what the device is on the cable. So if one end of the cable is plugged into the main board, and the other end is connected to the hard drive, and there is a device also connected to the middle connector in the cable, then the hard drive would be the "master" or device 0 or something like that, and the cd rom would be the slave or device 1. If you look on your hard drive there is probably a little guide printed that shows what way to put the pin jumper on to set the drive to a certain mode - either master, slave, or cable-select. Look at that guide to determine which one your drive was set to, and use the guide on the new drive to set it to the same mode. I'm guessing from your post that your drive probably is missing the pin jumper - it just has the little wires but not a tiny plastic thing that you slide onto two of the pins - what two pins you slide this jumper on is what sets the master/slave/cable select setting. Sometimes taking the pin completely off is also a setting (like on mine you take the pin off to set it to master). Look on your guide on your old drive to see what it means if there is no pin jumper - it's probably master - and be sure to set your new drive to that same setting (also probably by just removing the jumper, but it is different with every drive).

> I looked up my hard drive model too (don't know why I didn't think about it before). It's a ST94011A, and it's listed as having 44 pins as well. But I'm still wondering about the differences in placement, etc.

One more thing, I've been looking at the place where the hard drive plugs in, and it is built with screws or metal blockings of some sort around the place where the pins are inserted, so that if the pins don't stick out from the hard drive, they won't be able to plug in, because the sides of the hard drive would hit the screws/blockings. Not sure how to describe it, but that doesn't look very promising considering how the various hard drives I've been looking at are shaped. For example, [this](http://i2.ebayimg.com/03/i/000/fa/c7/d65e_1.JPG) one would not fit because either side around the pins would hit the screws and you wouldn't be able to get the pins in.

I suppose that you could buy a replacement drive from the manufacturer to make sure, but I would try hard to find a good Seagate drive that would fit. ;)

---

### Post by seuzy13 on 2008-07-01
So, you're saying that the two "extra" long pins on a new hard drive could be removed? If so, what do I do about the sides surrounding the pins? For example, [this](http://www.auctiva.com/hostedimages/showimage.aspx?gid=489606&image=145575777&images=145575777&formats=0&format=0) hard drive is the same model as mine, but it looks slightly different, having the pin sort of enclosed on either side. The pins on mine all stick out from the hard drive (you can see on the pictures I posted).

I left a post on the forum of my computer's manufacturer, but it could be days before they get back to me... :-(

---

### Post by toolzen on 2008-07-01
> **seuzy13 said:**
> So, you're saying that the two "extra" long pins on a new hard drive could be removed? If so, what do I do about the sides surrounding the pins? For example, [_this_](http://www.auctiva.com/hostedimages/showimage.aspx?gid=489606&image=145575777&images=145575777&formats=0&format=0) hard drive is the same model as mine, but it looks slightly different, having the pin sort of enclosed on either side. The pins on mine all stick out from the hard drive (you can see on the pictures I posted).

I left a post on the forum of my computer's manufacturer, but it could be days before they get back to me... :-(

The pins themselves cannot be removed - the little plastic part (which can be seen in this [_link_](http://www.pcguide.com/intro/fun/jump-c.html) and if you look closely in the link you just posted) is moved into different positions on those "extra" pins to reflect one of the positions listed on the chart printed on the front of your drive.

Also, there are different versions of most drive models. So even if it is a Seagate Barracuda for example a drive from one year/version may look a little different from another exact same drive model from a different year.

---

### Post by seuzy13 on 2008-07-01
If you mean the gray part in the picture I posted, I'm not talking about that, because mine has one of those too. I'm talking about how it would be physically impossible to insert one of these drives, because the place where it plugs into the motherboard is built *inward*, so that if there is any thing on either side of the pins *as a whole* it will hit the place where the screws to the hard drive cover go in, and the pins won't be able to go any farther and won't be able to plug in as a result.

Now, my drive does have a guide on the front. The master is listed with six pins without jumpers. Four are arranged in a square and two are off to the side a little in their own column. Thing is, my hard drive has one row of pins and then four little pins in a square. Two of them have a sort of half-jumper on them that only covers them half way. The part that doesn't make any sense is that there is no place for these four to plug in for aforementioned reasons, so anything you do to them won't be detected *anyway*. =/ Really confusing.

---

### Post by seuzy13 on 2008-07-02
I got a reply from the support forum of my computer's manufacturer. Apparently, my drive has an "intermediate connector" attached to it, which is allowing it to plug into the laptop. Attaching the same connector to any hard drive would fix the problem I've been describing. The connector is damaged, and I'm still waiting on word as to what kind of connector to replace it with.

In the meantime, I think this thread should be marked solved, but if you know anything about intermediate connectors and want to post with advice, by all means do so.

---

