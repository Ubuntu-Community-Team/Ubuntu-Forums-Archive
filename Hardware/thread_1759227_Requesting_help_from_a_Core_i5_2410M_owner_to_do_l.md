---
title: "Requesting help from a Core i5 2410M owner to do luks benchmark on 2.6.38 kernel"
date: 2011-05-15
forum: Hardware
---

### Post by User4519 on 2011-05-15
Hi :)

I have a request for anyone out there who may be fortunate enough to sit on a Sandy Bridge Core i5 2410M-based laptop and running Natty - or any other OS for that matter, so long as it's based on Linux 2.6.38 (because that's when LUKS became SMP aware).

I'm looking to but a new laptop soon and I'm torn between an ASUS U36SD and a Lenovo T420s. Specs-wise the Lenovo is a sure winner, but in terms of looks (and price) the ASUS comes out on top.

The main problem with the ASUS one, though, is the i5 2410M processor, which happens to be the **only** 2nd gen i5 that is missing both virtualization extensions, and most importantly the AES-NI extension which provides an extreme boost in AES based encryption and decryption. Which comes in very handy, as I **always** encrypt the hard drive on my laptops. Hardware is hardware, and sad to loose, but if there's one thing my insurance can't compensate me for, it's identity theft and the loss of my own and my customers' private data.

So - still being quite hot on the U36SD I decided to Google for someone having done benchmarks of LUKS on the 2410M processor. I couldn't find that specifically, but I did find this more generic post,

[http://blog.wpkg.org/2009/04/23/cipher-benchmark-for-dm-crypt-luks/](http://blog.wpkg.org/2009/04/23/cipher-benchmark-for-dm-crypt-luks/)

In which is a link to this benchmarking script, which I just ran on my puny Core 2 ULV processor (not as bad as I expected, really):

[http://www.holtznet.de/luks/cryptobench.sh](http://www.holtznet.de/luks/cryptobench.sh)

My hope is that someone with an i5 2410M will run this script (if possible with AC power and on batteries), and paste the resulting output here? I'm wondering if the 2410M without AES-NI is still powerful enough to support full throughput from my Vertex 2 SSD even while encrypted.

With hopes and thanks in advance,
Daniel :)

---

### Post by User4519 on 2011-05-16
Sorry to resort to this, but... Bumpetybump? :)

---

### Post by User4519 on 2011-06-03
Yeah, sorry, bumping it once more... The laptop is soon to be released...

---

### Post by oldmankit on 2011-06-10
I'm the midst of doing my first researches into buying a laptop especially for linux, and discussions like these are really helpful.

---

### Post by User4519 on 2011-06-14
> **oldmankit said:**
> I'm the midst of doing my first researches into buying a laptop especially for linux, and discussions like these are really helpful.

Well, in case oldmankit isn't just being sarcastic, I feel obliged to give this one final BUMP, and then I'll leave the thread to die if no-one replies.

Thanks in advance for any help, and apologies for the constant bumping.

---

### Post by e-Tiggy on 2011-06-20
> **DanielBuus said:**
> Well, in case oldmankit isn't just being sarcastic, I feel obliged to give this one final BUMP, and then I'll leave the thread to die if no-one replies.

Thanks in advance for any help, and apologies for the constant bumping.

well i'm running windows so can't run your script, but i have a 2410m and currently ecrypting my drive with truecrypt. the simulation run showed 240-250MB/sec mean speed, maybe that will help you to decide.

---

### Post by e-Tiggy on 2011-06-21
> **e-Tiggy said:**
> well i'm running windows so can't run your script, but i have a 2410m and currently ecrypting my drive with truecrypt. the simulation run showed 240-250MB/sec mean speed, maybe that will help you to decide.

and thats at 100%, all cores turbo boosted.

---

### Post by rjs1064 on 2011-06-22
i have an i5 sandy bridge laptop, bought a couple of weeks ago. But 3d graphics don't work so no games. Most other things work although it has crashed a few times. Hopefully it will be fixed eventually.

---

### Post by User4519 on 2011-06-23
> **e-Tiggy said:**
> and thats at 100%, all cores turbo boosted.

Hi e-Tiggy!

Thanks for that! Even though that's not Linux, it's definitely useful info. ~250 MB/s is full throttle on my SSD, and I don't see how it could possible be slower in Linux.

Thank you for the info! :)

Daniel

---

### Post by gururise on 2011-10-24
I did a BIOS update on my Fujitsu LH531 with Core i5-2410M processor, and suddenly, I have AES-NI instructions enabled!!

---

### Post by User4519 on 2011-10-25
> **gururise said:**
> I did a BIOS update on my Fujitsu LH531 with Core i5-2410M processor, and suddenly, I have AES-NI instructions enabled!!

That must be a bug, then, misreporting something... It's clearly not [supported in hardware]("http://ark.intel.com/products/52224").

---

### Post by Trevayne10 on 2011-11-14
> **DanielBuus said:**
> That must be a bug, then, misreporting something... It's clearly not [supported in hardware]("http://ark.intel.com/products/52224").

DanielBuus,


Read the fine print, last sentence, all the way at the bottom of the webpage:

[http://ark.intel.com/products/52224](http://ark.intel.com/products/52224)

"Some products can support AES New Instructions with a Processor Configuration update, in particular, i7-2630QM/i7-2635QM, i7-2670QM/i7-2675QM, i5-2430M/i5-2435M, i5-2410M/i5-2415M. Please contact OEM for the BIOS that includes the latest Processor configuration update."

i5-2410M is listed, so it has AES-NI hardware capability built in.  It just needs the laptop OEM to supply a BIOS that will allow the user to enable it.

I have a Toshiba Satellite L755-S5258 laptop with the same CPU, and I'm hoping and waiting for Toshiba to release an updated BIOS that will allow AES-NI activation (I know, "don't hold your breath").

---

### Post by User4519 on 2011-11-15
> **Trevayne10 said:**
> DanielBuus,


Read the fine print, last sentence, all the way at the bottom of the webpage:

[http://ark.intel.com/products/52224](http://ark.intel.com/products/52224)

"Some products can support AES New Instructions with a Processor Configuration update, in particular, i7-2630QM/i7-2635QM, i7-2670QM/i7-2675QM, i5-2430M/i5-2435M, i5-2410M/i5-2415M. Please contact OEM for the BIOS that includes the latest Processor configuration update."

i5-2410M is listed, so it has AES-NI hardware capability built in.  It just needs the laptop OEM to supply a BIOS that will allow the user to enable it.

I have a Toshiba Satellite L755-S5258 laptop with the same CPU, and I'm hoping and waiting for Toshiba to release an updated BIOS that will allow AES-NI activation (I know, "don't hold your breath").

That's fantastic! Great spotting! I vaguely recall reading about something like this recently, I think while I was looking to see if SSH could utilize AES-NI (would make sshfs a pretty awesome alternative to smbfs).

Myself, I'm now on an i7 as I opted for the MacBook Air in the end, but this is great to know for anyone else shopping! :)

Cheerio :)

---

