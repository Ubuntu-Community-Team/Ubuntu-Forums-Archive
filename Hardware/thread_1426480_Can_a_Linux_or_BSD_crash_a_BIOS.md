---
title: "Can a Linux or BSD crash a BIOS?"
date: 2010-03-10
forum: Hardware
---

### Post by TBABill on 2010-03-10
Just a strange question. I distro hop with one partition on my laptop and decided to try PC-BSD 8. I ran md5sum and burned the DVD at the slowest speed possible. The installer began but only got less than 30 seconds into the install and the screen froze with the same group of text tiled across the screen about 20 times. I can't recall what it said, but wasn't a clue to anything.
 
Anyway, the whole machine froze and could not be unlocked without a hard reset. Then the machine will not even boot to the BIOS screen. It's an ACER Aspire 5520 and cycles power on and off every 2 seconds. According to Google searches this is an indicator of a failed component of the motherboard, corrupt BIOS, defective video (in my case it's on the motherboard of my laptop) or another pretty much fatal failure.
 
Is it possible for the OS to communicate with the BIOS in a way that could harm it during installation? I did do all the basic troubleshooting, such as rebooting and running on AC with battery removed, holding power button 1 minute with AC and DC power removed (and turning back on while still holding power button down), removing RAM and rebooting, removing HD and rebooting, etc. No changes every time. 
 
I've decided to trash the laptop and replace it, but I want to know if this could happen again on another machine or just coincidental that it happened in the beginning stages of an installation?

---

### Post by TBABill on 2010-03-11
Bump...
 
And as an addition, I am not assuming the OS caused the damage, but wondering if it were corrupted during the burn process is there a possibility of something erroneously damaging a computer's BIOS.

---

### Post by cascade9 on 2010-03-11
It is possible for an OS to communicate with the BIOS- this is how you can update the BIOS from the OS. As far as I know, you can only do that with windows. Linux should be able to do it, somehow, but its not something I've ever seen. 

I doubt that any linux distro would do corrupt you BIOS. 

You could try clearingthe CMOS. Probably you would need to take the back off the laptop and manually remove the battery for a while. Or you could try this fix-

> I had the same thing occur with my Acer 5520 Notebook. The green charge light was on but when I pushed the power switch nothing happened. I did some research on the internet and this is what I did that solved the problem: 

I removed the battery and unplugged the power supply. I then held down the power button for 45 seconds. I then reinstalled the battery and the power supply and pushed the power button and voila it worked. I did have to try it a couple of times before it woorked but all is well now.From here-

[http://en.kioskea.net/forum/affich-40158-asus-laptop-does-not-power-up#p62903](http://en.kioskea.net/forum/affich-40158-asus-laptop-does-not-power-up#p62903)

The problem that fixed is not exactly what happening in your case, but near enough its worth a try. 

Good luck ;)

---

### Post by ssulaco on 2010-03-11
> **TBABill said:**
> 
I've decided to trash the laptop and replace it
I wouldnt do that yet...I cant imagine Linux corrupting the bios,
Have you tried pulling your CMOS battery and waiting 5 minutes....and/or depending on the age of the computer I would just replace the battery....
Ive had some boot issues in the past that were caused by a weak cmos battery

---

### Post by srs5694 on 2010-03-11
In addition to clearing the CMOS (if you can find documentation on doing this), try disconnecting the hard disk and see if you can boot a CD/DVD. I've recently become aware of some [obscure and rare problems](http://www.rodsbooks.com/gdisk/bios.html) that can cause symptoms like those you describe, related to disk contents. (That's my own page to which I just linked. If you have more information, I'd love to hear about it!)

---

### Post by as123 on 2010-12-22
Hi,
I've been researching the same phenomenon:
it seems BSD related though (so another forum maybe ?)

I had same problem with an HP G72 130 notebook, which I managed two times to completely disable - the computer wouldn't even boot up the BIOS.

I have a strong feeling that the BIOS was interfering with modifications to the MBR:

the BIOS, as it is known, contains on most of todays notebooks, code which automatically connects to servers of the company "absolute corp" in america. This is often, if not always done without the user being able to disable it. That is, the BIOS contains a rootkit from this company, ("computrace" technology) which  cannot be disabled and ! is able to install further software on a (win, at least officially) partition, and in the MBR.
The technology is well documented on their webpage. Computer manufacturers disguise it, or use it, as 'theft protection'.
See also here:
[http://corelabs.coresecurity.com/index.php?module=Wiki&action=view&type=publication&name=Deactivate_the_Rootkit](http://corelabs.coresecurity.com/index.php?module=Wiki&action=view&type=publication&name=Deactivate_the_Rootkit)
[www.absolute.com](www.absolute.com)
[http://www.absolute.com/en/products/bios-compatibility.aspx](http://www.absolute.com/en/products/bios-compatibility.aspx)
[http://www.absolute.com/en/lojackforlaptops/technology.aspx](http://www.absolute.com/en/lojackforlaptops/technology.aspx)
(when reading it pls keep in mind that as long as no option to switch it on/off in the BIOS menu is available, the BIOS behavviour cannot be changed other than flushing which is not done by software unless the sw is presented as flushing the BIOS.................. (that means the root kit has to be there already and connecting without user interfering)). See also their patents !

Moreover, I have just disabled a clevo x7200 installing FreeBSD. The symptomps are the same as yours. In this case, I suspect also ACPI or whatever.

There is not much written about it, also not about the BIOS rootkit, so that's why I'm posting here.

Additionally I note that in principle it is possible, also with linux or bsd or whatever, to flush the BIOS, reprogramme it, and this holds for every firmware in the computer I reckon, as holds for the rootkits in firmware.

If someone as similar experience, pls post.

---

