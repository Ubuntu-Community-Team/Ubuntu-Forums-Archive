---
title: "Cannot load Ubuntu installation interface"
date: 2015-05-10
forum: Hardware
---

### Post by addison6 on 2015-05-10
I would like to switch all our desktops from Windows XP to Ubuntu Desktop. 35 desktops with the same configuration:

Motherboard: Foxconn P4M8907MA-RS2H (775 socket, 1 x PCIex16, 2 x PCI, 1 x PCIex1)
Processor: P4 3.40 GHz
Memory: 2 x 1G Corsair 533 MHz
Video: MSI Radeon 5450 VRAM 1G
Storage: SATA1 150 GB

In my opinion even for our days this configuration can perform pretty well for office activities like Internet navigation, Email, Office documents.

I extracted one desktop from the network for testing before replacing OS in all. I created a DVD with the latest Ubuntu Desktop 14.04.2 i386 image. I can boot the CD, but it cannot load the installation user interface. I get the dark pink background over the whole screen and those two white icons on the bottom (keyboard - round circle with a man inside). And it is blocked from now on. I extracted a second desktop from the network, same situation.

If I cannot deal with this I have to remain on Windows XP or to replace the whole network in time with a huge cost just to access a modern OS! I never find a linux version which cannot be installed on good desktop configuration. I suspect there are some limitations coming from BIOS. I tried to disable ACPI, to load optimized version for BIOS, I extracted memory, I pull out SATA cable from motherboard, nothing worked! It is clear that this motherboard not allow booting Linux CD's, like a firewall.

It must be a way to skip this motherboard limitation. With this motherboard I can load an Ubuntu HDD 80 GB till I get a message related to reconfigure the graphics, then I have the Terminal. Maybe CD is blocked by motherboard to load Linux versions? Please I need an advice.

Thank you.

---

### Post by ian-weisser on 2015-05-10
> **addison6 said:**
> With this motherboard I can load an Ubuntu HDD 80 GB till I get a message related to reconfigure the graphics,
The entire, exact wording of that message would be very helpful.
Feel free to take a (clear) photo of it.

---

### Post by addison6 on 2015-05-10
Let me describe in detail. Booting installation from CD fails. I remove SATA drive cable and came back with an old HDD which has Ubuntu 13 Desktop on it. I could boot from this device, except making working related to graphics. I had to go in Terminal to try fixing. I gave up because important was to check if the hardware can boot. 

Conclusion. HDD is booting an installation of Ubuntu, but I cannot start an installation from DVD. This is the main reason I said it could be limitation to BIOS for Linux installation.

---

### Post by addison6 on 2015-05-11
This is a problem related to the motherboard. A known issue 7 years ago in this Forum. This manufacturer Foxconn has a problem with Linux. They don't provide correct ACPI programming for Linux in BIOS. But they love Windows! I was very frustrated to see I can boot my DVD but getting no installation interface. I created several disks with different Ubuntu versions, but the result was the same. When I came with an HDD which had Ubuntu installed, it worked but it freezes, unstable. I removed all PCI cards, replaced memory, the same result.

I contacted Foxconn. They said as follows:

"**is out of our project plan to support Linux OS when we design. so we don't test to install Linux**"

And that's it! We are doomed to stay with Windows XP which ended in support last year! Just 35 desktops!

That statement from Foxconn was very important for the consumer. As a company Foxconn hidden an important issue from customer in order to take the right decision when he bought that product. This is a breaking of law. On the other side, they pushed their customers to Microsoft instead of having a "free will" to install what OS they need. Just imagine a medium computer user seeing it cannot install Ubuntu. Or having an unstable version. He will start hating Linux. Why I am forced to buy only Microsoft OS? Just having viruses, keyloggers and a lot of crap stuff?

As I know when you pretend it is an ACPI compliant, this should work no matter what OS are you using. This is another breaking of law, this is a defective product. It is like you manufacture bread but you don't tell your customers you use milk, peanuts, and people could die.

I spent a full weekend to manage installing Ubuntu. I can't do that thanks to Foxconn. What a crap.

Hope finally Foxconn will admit their fault and provide a fix. I am pretty sure I am not the only customer with this problem.

---

