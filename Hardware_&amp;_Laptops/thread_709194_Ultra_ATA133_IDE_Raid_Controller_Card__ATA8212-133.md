---
title: "Ultra ATA/133 IDE Raid Controller Card  ATA8212-133R not detected"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by labinnsw on 2008-02-27
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/25648](https://answers.launchpad.net/ubuntu/+question/25648) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I requested support for this issue on launchpad and recieved no response. Hoping for better luck here.

I have spent the last three weeks trying to install this card in Ubuntu Gutsy Gibbon to no avail. In a separate partition on the same drive I have also installed Gutsy while the card was in place in the hope that it would be recognized and installed. That was also unsuccessful. I have attempted so many solutions from so many posts that I don't know where to start with what information to give. I know additional information is needed before any assistance can be given, but instead of me giving an endless string of what I have tried and the results, I think it would be best if I am asked for specific information which I will then supply and we can proceed from there.

I should also add that I am not an advanced user so, if you are giving instructions, please make them detailed and step by step. (e.g. "http://ubuntuforums.org/showthread.php?t=642015" is a perfect how to at my level) Plus instructions set out this way can be used by users at any level.

lspci output is at: [http://paste.ubuntu-nl.org/57449/](http://paste.ubuntu-nl.org/57449/)
dmesg output is at: [http://paste.ubuntu-nl.org/57450/](http://paste.ubuntu-nl.org/57450/)

Cd Rom connected to "Ultra ATA/133 IDE Raid Controller Card ATA8212-133R" has not been detected.

Any help will be appreciated.

---

### Post by mrsteveman1 on 2008-02-27
If those logs were posted with the card in the machine, I'm not sure what the problem is so far but the kernel isn't loading a driver for the card, and its not appearing on the PCI bus for some reason.

At the least it should show up as an unknown device but should at least list its pci address.

Since this is a softraid card, it should be loading some bios code at boot right after the normal bios screen. Does that show anything?

---

### Post by labinnsw on 2008-02-28
Thanks for replying mrsteveman1

The card was in place when the logs were posted

I have recorded the boot process and posted it on You tube; [http://www.youtube.com/watch?v=WdKE9gxkajc](http://www.youtube.com/watch?v=WdKE9gxkajc), but I could not (bearing in mind that I am a novice and am not too sure what I am looking for) see anything loading pertinent to the card.

Hope this helps

---

### Post by mrsteveman1 on 2008-02-28
So are the lite-on dvdrw and the 250gb seagate drive connected to the motherboard or the add-in card?

I see it loading some bios code for a marvell chip but i was under the impression your add-in card uses the ITE chipset. Does this card work in other machines?

---

### Post by labinnsw on 2008-02-28
The lite-on dvdrw and the 250gb seagate drive are connected to the motherboard, I will try the card in another computer when I get home this evening. I am having a problem with the other computer, NTLDR is missing. I will advise further as soon as possible.

Update

I cannot get the other computer to load any OS, not even the one I am currently using. I am contemplating getting another PCI to IDE card and trying to see if it will be detected on the system I am now running.

---

### Post by labinnsw on 2008-03-16
I acquired a High Point Rocket Raid 454 PCI card and did a fresh installing, which was quick, easy and painless. I had no loss of information. See my last post at [http://ubuntuforums.org/showthread.php?t=719240](http://ubuntuforums.org/showthread.php?t=719240).

Thanks to mrsteveman1 for walking me through the trouble shooting phase.

---

