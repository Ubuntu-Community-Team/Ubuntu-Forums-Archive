---
title: "Low cost data server"
date: 2008-07-08
forum: Hardware
---

### Post by Skillachi on 2008-07-08
Ok so heres what I want to do. I have some old pc parts lieing around the place. Enough to make a pretty old but still functioning PC. So what I was thinking is that, since i have alot of data (that I would really hate to lose), and i need to do backups. I would spend some money (hopefully no more than $250 and setup a server at my house that would do nothing more than hold data. I am hoping to setup things in RAID 5 and the only hardware I would need are: the Hard drives, and the raid controller to do so. I did my research on some websites and found some cheap 500gb hdds (coming up to about $180) and now i have the following questions:

1) Which Raid controller do you recommend - It needs to be a good well supported raid controller that hopefully supports raid 5. If it doesnt support raid 5, thats ok as long as its good, its just a preferential choice not a necessary one.

2) Which flavour of linux (or preferably ubuntu since i'm used to it) should I run? - I was thinking xubuntu since it requires the least resources and would do its work, however all other suggestions are welcome.

3) Which software would I need to run this? - What am I going to need next to probably the drivers that come with the raid controller to have good operation. And in case the raid controller software doesnt come with any kind of notification in case of hdd failure, is there anything that would auto-notify me or something?

4) What would the setup be like... After I've done all the hardware installation and setup xubuntu (or watever) what do I do?

5) Do you think im wasting money going hardware RAID, or should I go software RAID?

Thanks for all your help in advance

---

### Post by Skillachi on 2008-07-10
ok.... guess no help in this then

---

### Post by tamoneya on 2008-07-10
i dont have any controllers to recommend as I just use a software RAID.  I have a quad core processor though so it really isnt a big deal for me.  If however the only thing that the computer is doing is managing the RAID and running a server it may not matter.  

As for RAID 5 I would actually recommend RAID 1 for you.  I am assuming that you have 2x500GB since 500GB drives go for about $80-$90 currently.  If you have two drives there is no sense it going RAID 5.  It will work but you waste resources calculating the parity bits and since it is just the parity of one bit it is always just the opposite.  Instead just copy over the bit itself for redundancy.  This would make it a RAID 1 system

---

### Post by Fire_Chief on 2008-07-10
Regarding the RAID controller (should you choose to get one), it does depend entirely on the type of drives you are using (IDE, SCSI, SATA). 
However, I agree with tamoneya's assessment that RAID 1 is a better solution. It is much easier to recover from should a drive fail and is overall less complicated. In this case, you do not really need a RAID controller for the system as the overhead is minimal.

Cheers!

---

### Post by Skillachi on 2008-07-10
Well Unfortunately I wont be running quad core... I'll be lucky if im even running a pentium 4. I havent yet done stock on what old parts are available to me. But Its gonna be a low tech system.

I was gonna purchase 3x500GB (found for $70 on newegg) so that I could run raid 5 and get 1TB of storage space fully backed up in case of failure, which is why I preferred raid 5... however if all else fails i'll dig deep and buy 4 500gb hd's and then still get the 1tb of storage that i wanted.

---

### Post by tamoneya on 2008-07-10
okay well since I assumed 2 drives and it is actually 3 that changes things a bit.  Honestly since it sounds you are trying to stay cheap I would still go with the software RAID as long as you wont be using this computer for anything besides a fileserver. Who cares if there is overhead on the CPU.  Also have you considered 2x750GB.  It should be the same price as 3x500GB.  having two drives means less points of failure and then you could do RAID 1 and keep it simpler.

---

### Post by Skillachi on 2008-07-10
The 2x750gb would work out to be basically the same 1TB so yeh i guess that makes alot of sense... Raid 1 should be a cheaper equivalent becuz its so damn hard to find an affordable raid controller card with more than 2 ports...

So basically I would just need to setup software raid and freenas and im good to go then?

edit: I just thought about it and whichever way i take it, i would probably still need the raid controller card... why? Because since i know the mobo is gonna be an old mobo, it probably wont be able to work with more than about 500gb worth of storage (or would it?) so I would end up needing the card to do that part for me right?

---

### Post by Fire_Chief on 2008-07-10
What type of drives are you getting?

---

### Post by Skillachi on 2008-07-10
Preferably SATA (cheaper), because of its transfer speed advantages etc

---

### Post by tamoneya on 2008-07-10
the mobo should be able to handle the 500 or 750 GB drives regardless of age.  If it has a SATA port it will handle any sata drive.  Thats the idea.  Chances are that old means IDE though.

---

### Post by Skillachi on 2008-07-10
Yea thats the thing... if the mobo can handle sata then i know theres no problem. However im thinking, if the mobo cant handle sata then i could go with the controller card and let it do the sata work for me?

---

### Post by snowpine on 2008-07-10
We need to know your system specs to recommend a "flavour" of linux for you. Xubuntu is indeed the lightest of the official "buntus" however it is far from the lightest linux, if you catch my meaning. Pentium 3 with 256mb ram will run xubuntu very well, however, if you do a minimal type of server install, it can get even lighter.

I will defer to others' expertise on the raid questions.

---

### Post by Skillachi on 2008-07-10
Overstood, as soon as i can i'll do a proper setup and then see where i can go from there.

---

### Post by Fire_Chief on 2008-07-10
If you need to get a card for the SATA and don't need really high throughput, then just get a regular SATA PCI adapter instead of forking out for a full blown SATA RAID controller.

---

