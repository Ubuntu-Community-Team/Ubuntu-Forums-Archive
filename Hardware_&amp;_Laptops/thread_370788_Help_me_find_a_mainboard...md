---
title: "Help me find a mainboard.."
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by Betelgeuse on 2007-02-26
Hi,

I'm planning to have a new desktop PC and I build all my PC's myself, so I'll build this one too.
Selecting the components for linux is a new thing for me. I'm new to Linux and using Kubuntu for only 2 months. So, installing drivers is a hard thing for me. My current PC is running fine and every hardware I have is working. The only problem was video driver (NVIDIA) and I installed NVIDIA driver with Automatix and now it works fine now... (I could not make the computer to suspend to disk but it's not a big problem for now)

So, I need to select a mainboard to use with intel core2 duo CPU. The ASUS distributor here has an excellent technical support so I'm thinking of buying an Asus mainboard. But they do not know anything about linux so I do not know if I'll have any problems with drivers for the onboard hardware (USB, ethernet, chipset, audio etc.) So I may buy another brand which support linux better. (I think we have to support brands that support linux)

What mainboard should I buy? Which brand deserves our support ? I do not want to give my money to a company that support only Windows and I do not want to have trouble installing linux drivers. So, give me a brand and a model of a mainboard so I can build a good PC.

The PC will be used by my employe at the office. He's a software developer and he deserves a new PC too. I'm planning to switch my company from windows to Linux and a new PC will be a good motivation for the employees to switch to Linux. So, help me select good hardware for linux. 

I'll ask about which video card later. :))

---

### Post by Daveth on 2007-02-26
I have had no problems at all with my ASUS A8N-SLI Premium board, though this running an Athlon X2 chip rather than Intel. Chipset, ethernet and SATA etc all run fine. Using an Audigy 2 PCI card for sound rather than the onboard. USB mouse support a bit flaky sometimes- a Logitech problem possibly. Use the k7 kernel and both cores are recognised. I built mine and shopped for as many A-list components as I could get/ afford. Not sure about the newer nforce chipsets- always best to be on the trailing,rather than the cutting, edge with kit.

---

### Post by eeried on 2007-03-21
USB mouse a bit flaky? ouch -- which Logitech mouse have you got?

At least I see ther's a PS/2 mouse port.

I'm glad to hear there are no problem with AN8-SLI-Premium as it looks like a very good MB that's on sale on Ebay in France at least. Though I don't have any use for SLI I may be tempted.

@ Betelgeuse
Threre are several pages when you can find compatible MB but there are not updated (wiki-ubuntu to begin with). 

Looking for MBs compatible with Linux is a hassle! But you may have seen the new AM2 socket Gigabyte  MB that has a free BIOS -- however AMD2 socket CPU are more expensive than 939 CPU.

I toot am looking for some new components to replace my  rather slow PII computer.

---

### Post by robenroute on 2007-03-21
Have a look at phoronix.com they regularly test motherboards and rate them for Linux compatibility.

I think (off the top of my head) that the ASUS P5B series isn't too shabby....

---

### Post by Betelgeuse on 2007-03-21
I've finally decided which components I should buy for my new PC. 
Mainboard : Intel G965WM 
This mainboard has onboard intel GMA x3000 video so I'll not need to buy another video car. 
My main problem was video cards, I do not want propriatry software runnning on my computer and I want to buy hardware that supports free software. ATI and NVIDIA do not give a damn about free software drivers so I want intel onboard video, intel opens their specs to developers to write free software drivers and actively supports linux, so, for video cards, we have only 3 choices, ATI, NVIDIA and Intel. I chose intel becouse of their supports on video drivers. I do not play games so I do not need powerfull 3d graphics, I think this intel gma x3000 video chip is more than enough for me.

---

### Post by eeried on 2007-03-22
I understand your point about Intel, Betelgeuse. The question is though are their free drivers for Linux *good*? Ati free drivers aren't very good apparently. I would shun ATI anyway.

If your motherboard works with Linux don't forget to add it to Ubuntu-Wiki and to [http://doc.gwos.org/index.php/](http://doc.gwos.org/index.php/)

Thanks for the link to Phoronix, robenroute.

---

### Post by Betelgeuse on 2007-03-22
> **eeried said:**
> I understand your point about Intel, Betelgeuse. The question is though are their free drivers for Linux *good*? Ati free drivers aren't very good apparently. I would shun ATI anyway.

If your motherboard works with Linux don't forget to add it to Ubuntu-Wiki and to [http://doc.gwos.org/index.php/](http://doc.gwos.org/index.php/)

Thanks for the link to Phoronix, robenroute.

For my choice of Intel mainboard for intel graphics was based on opensource drivers. And I've found a web site [http://www.intellinuxgraphics.org](http://www.intellinuxgraphics.org) and it seems we'll see "good" open source graphics drivers from intel. I hope they will make graphics card too, now we have only onboard intel graphics. I think there are too many people with ATI graphics cards and they are not using them with linux so most of them will buy intel graphics cards if there is good drivers for them. One of my friend installed kubuntu because of my advice and now having trouble with his ATI card and he dumped that card to garbage and bought an NVIDIA card. 

And I've send an e-mail to Richard Stallman (The head of Free Software Foundation and GNU) and confirmed intel's free software intentions. I was not expecting a reply from him but he sen me a very friendly reply. Now I'm thinking about joining FSF.

---

### Post by eeried on 2007-03-22
This is great news, Betelgeuse. I remember now reading something about intel and the "free world", and it must have been on the FSF website.

---

### Post by Betelgeuse on 2007-03-22
> **eeried said:**
> This is great news, Betelgeuse. I remember now reading something about intel and the "free world", and it must have been on the FSF website.

That's why I'll buy an intel mainboard. we have to supprort from companies who makes hardware with free software drivers and we should NOT buy hardware from companies who do not give a damn about free software. Now, people are buying hardware without goo open source drivers (like ATI) and they come to this forums and complain about their video card is not working with linux. Linux community do not have to reverse engineer some hardware to make it work with linux. it's the hardware companies that should cooperate.

---

### Post by eeried on 2007-03-22
Hello again,

maybe you ought to read this page before you buy your mobo: [https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28deluxe%29]("https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28deluxe%29")

---

