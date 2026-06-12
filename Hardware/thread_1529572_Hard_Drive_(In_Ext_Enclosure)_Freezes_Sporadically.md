---
title: "Hard Drive (In Ext Enclosure) Freezes Sporadically"
date: 2010-07-12
forum: Hardware
---

### Post by luger on 2010-07-12
I have a 1.5 TB drive put into an external hard drive enclosure which is plugged into an Ubuntu nettop via USB.  The Ubuntu nettop is a home theater computer used for watching videos and listening to music while hooked up to my HDTV.  I store the media on the 1.5 TB hard drive and download directly to that hard drive.  
 
Sometimes in the middle of watching a video, the video will freeze up and I'll notice the hard drive within the enclosure stopped spinning.  I'll shut everything down and start back up again and everything is fine.  This happens sporadically and sometimes won't happen for many days.  More common than that is that I'll start some downloads onto the hard drive before I go to bed but wake up and find that the hard drive froze in the middle of the night and the downloads stopped.  The hard drive in the enclosure doesn't have an OS on it and is only being used for storage.
 
I'm not sure if the hard drive is at fault or the enclosure it is in.  Basically, I'm not sure where to start in order to fix this problem.

I contacted the support team for the manufacturer's of the enclosure and their response was: "This is a bug under linux.  Try as full update or contact linux support."  I've tried to ask for clarification from them but am wondering if anybody is familiar with anything like this.

If it helps,
The Coolmax enclosure is found here: [http://bit.ly/c49bBI](http://bit.ly/c49bBI)
And, the Seagate hard drive is here: [http://bit.ly/9N61Ys](http://bit.ly/9N61Ys)

Thanks everyone.

---

### Post by Grenage on 2010-07-12
That sounds more like a hardware fault, than a software fault.  I would be curious what their response would be if you said that you were using Windows - but that would involve 'fibbing'.

---

### Post by luger on 2010-07-12
My thoughts exactly.  He claims it's a Linux bug but gives no details on what the bug or how it would be resolved other than "updating" Linux (my Ubuntu is up to date).

I think I'll probably just buy a better enclosure and hope that's the source of the problem as opposed to the hard drive.

---

### Post by Grenage on 2010-07-12
I'm sure you've thought of it, but can you connect the drive directly to the computer for a few days?

---

### Post by luger on 2010-07-12
Yeah, I definitely would if I could.  But, it's a tiny nettop computer ([http://bit.ly/b2rSMp](http://bit.ly/b2rSMp)) so I can't fit this hard drive in it to test that out.

---

### Post by Grenage on 2010-07-12
Ah I see.  Well if you can't plug it into a Windows box as a test (read:humour), I'd personally send it back and tell them it's duff.

---

### Post by luger on 2010-07-12
Ah, yes, good point.  I didn't think of that!  I'll try mimicking the situation on a Windows PC and see what that does.

---

### Post by cascade9 on 2010-07-12
> **luger said:**
> Yeah, I definitely would if I could.  But, it's a tiny nettop computer ([http://bit.ly/b2rSMp](http://bit.ly/b2rSMp)) so I can't fit this hard drive in it to test that out.

You dont have to use an internal HDD internally...you can just pop it on the desk, hook up the SATA and power cables, and off you go!  ;)

---

### Post by luger on 2010-07-12
> **cascade9 said:**
> You dont have to use an internal HDD internally...you can just pop it on the desk, hook up the SATA and power cables, and off you go!  ;)

Yeah, I am currently using the HD in an external enclosure hooked into the Ubuntu machine.  I'm pretty sure the enclosure is the device that is causing the problems.  I've been continuing to e-mail their support staff but am getting really suspicious e-mails in return that just say "contact linux support" or "update linux" as they claim it is something wrong with Linux and not their hardware.  This seems like a really shady company... Definitely not buying any more of their products.

---

### Post by bkann on 2010-07-12
On the off chance that it is your Linux installation, and to rule that out as a potential culprit, could you boot with a live disc, mount the external disk, and then put it through the wringer for a few days?

If it doesn't fail that way, it might be worth taking another look at your installation.  If it does fail during that time, you'll at least have confirmed that it's not your installation.

Just a thought.

---

### Post by cascade9 on 2010-07-13
> **luger said:**
> Yeah, I am currently using the HD in an external enclosure hooked into the Ubuntu machine.  I'm pretty sure the enclosure is the device that is causing the problems.  I've been continuing to e-mail their support staff but am getting really suspicious e-mails in return that just say "contact linux support" or "update linux" as they claim it is something wrong with Linux and not their hardware.  This seems like a really shady company... Definitely not buying any more of their products.

I agree, from the look of the site they have I think that its probably the enclosure. Or to be more accurate, probably the UWM-> SATA chip ;) 

"Contact Linux Support" = bugger off, dont bother us, your problem. :| Well, thats a lost customer...make that 2, I will remember that name,

---

### Post by luger on 2010-07-13
bkann: Yeah, I might give that a try just to test it out.

cascade9: I'm still trying to get more answers out of their tech support.  They claimed there have been no problems with these enclosures so I copied a long list of complaints I found in reviews of the product, haha.  I just want him to give more information on this mysterious "bug in linux" that he apparently knows about.

---

