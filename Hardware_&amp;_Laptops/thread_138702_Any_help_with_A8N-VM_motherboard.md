---
title: "Any help with A8N-VM motherboard?"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by dpicker on 2006-03-02
Hi,

Ive been using ubuntu ever since warty warthog and I love it.

Everything has always worked straight out the box and Ive never had too many problems.

However, I just bought a new computer last month and I didnt know at the time but i had chosen a computer that has had some problems with running linux.
I have the dreaded Asus A8N-VM (non csm) with nforce 410 chipset and integrated geforce 6100.

So far with 5.10 I have over come a lot of hurdles through reading forums etc. 
I use the 'noapic nolapic' boot prompt to prevent the computer from freezing, and change xorg.conf to use vesa (installing nvidia drivers later).
I dont use onboard LAN as I use a wireless usb adapter and ndiswrapper.

So I was fairly pleased with how far I had come from not having anything to work, to this and it has actually been a good learning experience.

But I am stuck when it comes to sound and leaves ubuntu useless as I always like to listen to music etc. I came across this: [http://www.nvnews.net/vbulletin/showpost.php?p=824408&postcount=343](http://www.nvnews.net/vbulletin/showpost.php?p=824408&postcount=343)

Which gave me a lot of hope but I dont want to compile a whole new kernel and patch it etc as I find this too much work and too risky despite having a nice tutorial.

If I have no choice I am willing to wait until 6.04 with no sound.
In case you are wondering, I have ran 6.04 Alpha 4 and have seen some improvements:

My usb wireless adapter was recognised and works fine (despite no light appearing on it and signal apparently at 0%)

Some form of sound device is recognised.. In volume control i can see HDA Nvidia (alsa mixer) and Analog Devices AD1986A (oss mixer) however there is still no sound. Not even a high pitched screeching noise or poor sound lol.

I also came across this: [http://www.nvnews.net/vbulletin/showpost.php?p=795184&postcount=227](http://www.nvnews.net/vbulletin/showpost.php?p=795184&postcount=227) 

Does this mean I need to tell ubuntu to use intel_hda? And if so, How do I go about doing this?

I was also wondering, by using the 'noapic nolapic' boot prompt, am i sacrificing anything at all?

Any help (or sound) would be fantastic!

Cheers,
David.

---

### Post by wetland on 2006-03-02
According to this [Link]("http://quaggaspace.org/a8nvm/").
It looks like only kernels 2.6.15 or higher support the Intel HDA Audio / "Azalia" sound card?

---

### Post by dpicker on 2006-03-03
Yes, which is why i tried (and still running) ubuntu dapper drake.

Is there more detailed instructions on how to patch the kernel for Azelia sound? And will i need to recompile alsa?

---

