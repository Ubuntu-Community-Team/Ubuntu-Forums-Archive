---
title: "Can I partition my External USB Hard Drive??"
date: 2011-10-04
forum: Hardware
---

### Post by mrjoeyman on 2011-10-04
Its a really big drive. Can you tell me how I can make it into 2 partitions? I would like to have just one small partition to work with..and leave the rest unallocated? Is that possible with a drive like this?

---

### Post by mikewhatever on 2011-10-04
Yes, you can use Gparted from the Ubuntu repositories.

May I ask why you don't want to use all the available space.

---

### Post by mrjoeyman on 2011-10-04
Why yes mrjoeyman you can. I will relate my experience and maybe someone can benefit, maybe not. I use an external usb hard drive for storing data. The way I broke it up into 2 partitions (it was all one) is by using Gparted, a nice program that comes with linux for noobs like myself and advanced users as well. First I copied all of my files to another drive so that they would not be on the usb drive during the shrink (which was the first step, you will see....) Then with the drive being empty, I opened up Gparted and navigated to the disk in question by using the little arrow button on the top right side of the window. Then I right clicked on the existing single partition, which was 298 gigs large and clicked on "resize". After that I got messages that told me "that the world might come to an end if I did that and was I sure that I wanted to do that?" So I figured what the heck.... Ok, so I used my mouse and clicked on and grabbed the right end of the rectangle graphic above that represented my partition, and slid it to the left about 20 gigs worth. This "shrunk" the existing graphic of that partition, and left a little "unallocated" gray space at the end (on the left, an unallocated 20 gigs worth). I clicked on "apply actions",then it read me the riot act again and I clicked "ok". Well it took about 1 minute and it was done. Now I had a smaller (gray) partion on the right and the now smaller shrunken partition on the left. Now I then click on the gray unallocated space on the right of the graphic and clicked on "new" for "new" partition. It asked me what kind of partition I wanted and I didnt know. I googled it and found that you only need a primary partition if an operating system is going to be installed, so I didnt need that. It gave me a choice between extended, and logical, so I googled that too. Turns out and extended partition is a "container" where you can create other "logical" partitions in it. So I chose a label (a name) and the "extended" option, and kept the file system that was already showing, which was ext4. I then clicked "ok" and it made me a cute little extended partition there on the end. Ok 20 gigs is a lot but compared to the remaining 278 gigs, it just looked kinda cute sittin there waiting for someone to bring it to life. Well when it was done I rebooted (I figured you gotta reboot right?) and when it came up I checked for my new partition......and....it ain't there? Well being the noob I am, I had previously checked around some programs and had seen one called "disk utility" and opened that up. In there I could see the 278 gig partition, and the 20 gig, but the twenty gig said "extended" and was white and not the color of the other one (purple in my case). Well I clicked on it and tried to mount it with a button that said "mount" and it didn't. Then I remembered that an extended partition is a container for logical partitions so I right clicked on it again and noticed a little button down below, become un-grayed out, and it said "create partition". Well you know me....I clicked on it. Low and behold a window popped up and let me name it and I hit "ok", and all at once I had brought to life that little white bastid, with the "extended" sign on it! It was all purple and it had its own name! It was even the one I had GIVEN it! I clicked the "mount" button again and linux mounted that sucker like a bullrider ridin the meanest bull in the rodeo! (Im sorry, I need a kleenex......)......................................................................
Ok, Im back. To make a long story, short, (too late!) I rebooted and went to my "computer" icon and there she was all awaitin on me, beggin me to put some data on her! 

Thanks to anyone who gave me the tidbits I used to finally tie all of this together, and I hope it can help some other noobasaurus like me!

---

### Post by mrjoeyman on 2011-10-04
> **mikewhatever said:**
> Yes, you can use Gparted from the Ubuntu repositories.

May I ask why you don't want to use all the available space.

Hey Mike I was answering my own question so it would be available to others in case they were wondering the same thing. I figured it out finally. As to why I didnt want to use all of it, I had a problem once already and the troubleshooting and maintenance involved in all 298 gigs was very, very time consuming. Now if I have another problem, I can muss it up quickly. Also if I have a problem on the main partition, my backups (which are now on the 20 gig part) will be protected. And as I need more space I can just shrink down more and make more partitions if needed.All is working very well! Thanks.:guitar:

---

