---
title: "Adaptec RAID Horror Story"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by JettCRX on 2005-06-15
This isn't necessarily a request for help ... more of a warning to others.  :)

My setup:

[list]
[*]Adaptec ATA RAID 1200A Controller (which I now know is NOT supported out of the box by Ubuntu)
[*]Windows 2000 Professional installed on Primary 160GB RAID-0 (2x80GB ... Primary Master, Secondary Master)
[*]2 20GB drives that used to be my primary RAID array (now Primary Slave, Secondary Slave), but I upgraded and so I was planning to use these to play around with other OSes.  Have played some in the past, but not much.
[/list]

So tonight, I fire up the Ubuntu installer and tell it to install to the 20gb Primary Slave drive.  Go with automated everything ... defaults all the way through ... tells me I need to reboot to complete ... no problem... system reboots, POSTs, RAID controller fires up... and BAM!  "A drive in your RAID array has failed."   DOH!   ](*,) 

To make a long story short, what actually happened, as best as I can tell:

Ubuntu Installer loaded GRUB ... but since Ubuntu doesn't support the RAID controller, it was treated as a simple IDE controller ... the Primary Master was marked as the bootable drive, so GRUB installed there, nuking all of the RAID configuration info.  Upon reboot, the RAID controller failed to find this information and choked.  I had fully intended to disconnect the RAID-0 drives so that this couldn't happen ... and simply forgot.

I googled my problem to see if I could find a solution ... didn't find anyone with my exact problem, but after piecing together ideas from various places, this is what I ended up doing:

1. Ran the RAID utility and DELETED the RAID configuration from the 1 drive that still thought it belonged in a RAID array.  "Are you sure?  ALL DATA WILL BE LOST!"  *gulp*  Yes.

2. CREATED a new RAID array using the 2 80gb drives.  "Are you sure?  ALL DATA WILL BE LOST!"  *gulp*  Yes.

3. Searched the web and discovered the most excellent Ultimate Boot CD ... ([http://ubcd.sourceforge.net](http://ubcd.sourceforge.net)) ... I've been out of doing hardware for a living for a while ... so I didn't have any appropriate utilities...  But this CD looked like just the thing.  Burned the ISO with my wife's laptop...

4. Used TestDisk to search the newly created RAID array for deleted partitions.  Low and behold, there it was!  Restored it perfectly and booted without any problems.  Yippeeeee!

5. Backed up ALL of the data that I was dreadfully afraid I had lost.  

6. Happy dance!   [IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG] 


So what have I learned (or more accurately, been REMINDED of, because I knew all of this already ...)?  

[list=1]
[*]CHECK TO MAKE SURE YOUR HARDWARE IS COMPATIBLE BEFORE YOU INSTALL ANY OS!
[*]BACK UP DATA REGULARLY!
[*]MAKE SURE YOU KNOW WHAT AN INSTALLER IS DOING BEFORE YOU SAY "Yeah, run auto with defaults" !!!
[*]DISCONNECT DRIVES YOU DON'T WANT TO SCREW UP WHEN INSTALLING A NEW OS... Worry about bootloader setups LATER.
[/list]

Oy!  What a stressful past couple of hours.   :razz:

---

### Post by angrykeyboarder on 2005-06-16
[QUOTE=JettCRX]This isn't necessarily a request for help ... more of a warning to others.  :)

My setup:


[list]
[*]Adaptec ATA RAID 1200A Controller (which I now know is NOT supported out of the box by Ubuntu)
[*]Windows 2000 Professional installed on Primary 160GB RAID-0 (2x80GB ... Primary Master, Secondary Master)
[*]2 20GB drives that used to be my primary RAID array (now Primary Slave, Secondary Slave), but I upgraded and so I was planning to use these to play around with other OSes. Have played some in the past, but not much.
[/list]
So tonight, I fire up the Ubuntu installer and tell it to install to the 20gb Primary Slave drive. Go with automated everything ... defaults all the way through ... tells me I need to reboot to complete ... no problem... system reboots, POSTs, RAID controller fires up... and BAM! "A drive in your RAID array has failed." DOH! ](*,) 

To make a long story short, what actually happened, as best as I can tell:

Ubuntu Installer loaded GRUB ... but since Ubuntu doesn't support the RAID controller, it was treated as a simple IDE controller ... the Primary Master was marked as the bootable drive, so GRUB installed there, nuking all of the RAID configuration info. Upon reboot, the RAID controller failed to find this information and choked. I had fully intended to disconnect the RAID-0 drives so that this couldn't happen ... and simply forgot.

I googled my problem to see if I could find a solution ... didn't find anyone with my exact problem, but after piecing together ideas from various places, this is what I ended up doing:

1. Ran the RAID utility and DELETED the RAID configuration from the 1 drive that still thought it belonged in a RAID array. "Are you sure? ALL DATA WILL BE LOST!" *gulp* Yes.

2. CREATED a new RAID array using the 2 80gb drives.  "Are you sure?  ALL DATA WILL BE LOST!"  *gulp*  Yes.

3. Searched the web and discovered the most excellent Ultimate Boot CD ... ([http://ubcd.sourceforge.net]("http://ubcd.sourceforge.net")) ... I've been out of doing hardware for a living for a while ... so I didn't have any appropriate utilities... But this CD looked like just the thing. Burned the ISO with my wife's laptop...

4. Used TestDisk to search the newly created RAID array for deleted partitions. Low and behold, there it was! Restored it perfectly and booted without any problems. Yippeeeee!

5. Backed up ALL of the data that I was dreadfully afraid I had lost.  

6. Happy dance!   \\:D/ 


So what have I learned (or more accurately, been REMINDED of, because I knew all of this already ...)?  

[list=1]
[*]CHECK TO MAKE SURE YOUR HARDWARE IS COMPATIBLE BEFORE YOU INSTALL ANY OS!
[*]BACK UP DATA REGULARLY!
[*]MAKE SURE YOU KNOW WHAT AN INSTALLER IS DOING BEFORE YOU SAY "Yeah, run auto with defaults" !!!
[*]DISCONNECT DRIVES YOU DON'T WANT TO SCREW UP WHEN INSTALLING A NEW OS... Worry about bootloader setups LATER.
[/list]
Oy!  What a stressful past couple of hours.   :razz:[/QUOTE]

 
So uhh.. no Ubuntu in th end?

---

### Post by fastluck on 2005-06-16
I've been through the stress a couple of times--looks like you got lucky (like I usually was). I'm glad to hear that. Hey...thanks for posting the UBCD url.  I'm going to get it right now.

**...and I'm back.** Finally, someone with the balls to put NTFS/write on a bootable CD.  I think I'm going to like this.... 

Cheers,

Fastluck

---

### Post by JettCRX on 2005-06-17
I do have Ubuntu running... on a 20gb drive attached to my onboard IDE... I've been having a blast the past few days configuring my system ... learning a lot as I go...

Ideally, I'd like to put Ubuntu on the 160gb RAID and put Windows on a 20GB drive... with one 20GB drive for shared data.  On my lunch break today, I decided to Google some more... there are a TON of people trying to get this card to work with Linux ... but lots of dead ends ... 

I realized that I had better luck with network card setup when I googled the CHIPSET rather than the CARD ... so on a whim, I looked into what chipset the Adaptec ATA 1200A card has ... turns out it's a HPT370.  Soooo... I searched for "HPT370 Linux."  Low and behold...

Turns out Highpoint Technology released a linux driver a long time ago for this card... however, at the time, they didn't release the source... just a couple of binaries for specific distros and kernels.  Not too terribly helpful.  I found several old mailing-list posts to this effect... At some point since then however, they open sourced their driver code ... now we're getting somewhere!

So I guess my next step is to try to build the sources ... and go from there.  If I can use the resulting driver to access my current Windows partition, then I'll go about backing up all of my windows data, wiping the 160gb partition, moving Windows to the other 20gb drive... and trying to load Ubuntu on the 160gb RAID.  

It won't be this weekend however, going to visit the inlaws for Father's Day.  Will report back some time next week.

---

