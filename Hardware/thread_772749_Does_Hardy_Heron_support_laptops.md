---
title: "Does Hardy Heron support laptops?"
date: 2008-04-28
forum: Hardware
---

### Post by geercom on 2008-04-28
Does Hardy Heron support laptops? If not, what is the best variant that does? I have an IBM Thinkpad R40.

---

### Post by Yellow Pasque on 2008-04-28
Yes. It should support your laptop nicely except for maybe the wireless. Do you know what kind of card you have?
[http://www.thinkwiki.org/wiki/Category:R40](http://www.thinkwiki.org/wiki/Category:R40)

---

### Post by Alldan on 2008-04-28
On my Acer 5101 ANWLMi Hardy Heron works  perfectly. Power management, Fn key, widescreen, battery, restrictred drivers, card reader, etc. I tried  older Ubuntu versions and many other Linux flavors and in my opinion Hardy is the best option.

---

### Post by geercom on 2008-04-28
> **Temüjin said:**
> Yes. It should support your laptop nicely except for maybe the wireless. Do you know what kind of card you have?
[http://www.thinkwiki.org/wiki/Category:R40](http://www.thinkwiki.org/wiki/Category:R40)

I don't use wireless, but I use a D-Link card for Ethernet because the internal Ethernet connection is broken. Should that work OK?

---

### Post by geercom on 2008-04-28
> **Alldan said:**
> On my Acer 5101 ANWLMi Hardy Heron works  perfectly. Power management, Fn key, widescreen, battery, restrictred drivers, card reader, etc. I tried  older Ubuntu versions and many other Linux flavors and in my opinion Hardy is the best option.

Do I need any special installation instructions? If so, where are they located?

---

### Post by howlingmadhowie on 2008-04-28
the best thing would probably be to try out the live cd and see what works. at least that much will work once you have it installed.

but be warned with the live cd, cd drives are a lot slower than hard drives, so the system may be quite unresponsive.

---

### Post by sheilnaik on 2008-04-28
Hardy Heron runs fine on my Dell 700m (I'm posting from it right now while I'm watching a DVD for class).  Download the Live CD and give it a shot.  As long as the display and wireless work fine on the Live CD, you should be ok.

As for my specific laptop, suspend didn't work out of the box for me so I had to use [this trick]("http://ubuntuforums.org/showthread.php?t=471855") to get it working.  My Fn buttons also don't work and I had to set the graphical effects to none (since my onboard graphics card is terrible), but everything else seems to be in order.

I don't use this laptop for anything other than word processing, web browsing, and IM, so Ubuntu is perfect for me.

---

### Post by jespdj on 2008-04-29
Ofcourse it supports laptops. It runs really well on my Dell XPS M1530. See the link in my signature below.

---

### Post by FredB on 2008-04-29
Running Hardy 64 bits on my Acer 5520g (sold to me with Vista Home Basic). And I have nearly all the compiz effects enabled...

---

### Post by nwdz on 2008-04-29
i think Hardy is good for laptops too...provided you dont have Intel 3945ABG wireless card...other than that...everything works fine..

---

### Post by Bartender on 2008-04-29
Notebooks can be trickier than desktops, but with each revision of Ubuntu the gap seems to close.
Some general rules of thumb - ATI graphics and Broadcom wireless chipsets can be a real pain.  From what I've read on the forums lots of folks run IBM notebooks with ATI, and Broadcom can often be made to run too, so the problem is not insurmountable.  At least with some models.
AFAICT my Acer 5920 is running Hardy better than Feisty.  There were some weird glitches with Feisty - such as a text message whenever it started saying it was unable to allocate something or another - that have gone away.
Search the forum for threads regarding your model, and google it too.  Sometimes random google searches will bring up valuable info that doesn't show up in a forum search.
At some point you'll probably just have to give it a go.  Unless you contact someone who has the exact same model and has installed Hardy there's almost always some level of uncertainty.  As mentioned, Live CD's are handy for taking a test drive but the results aren't always 100% accurate.

---

### Post by FergyTech on 2008-05-23
I have a Thinkpad R40 and I can't seem to get past the boot screen for the CD.  I had the same issue with the last version and I just tried this on 8.04 with the same result.  The checksum matches and I was able to install OpenSUSE 10 - so I know the CD drive is OK.

When the CD boots and I get the screen, which asks if I want to run the LiveCD or check the disk, etc... when I press the ENTER key to do anything, it freezes.  I tried the alternate disk aswell on the last version and it was unsuccessful too.

---

### Post by JC Cheloven on 2008-05-23
> **FergyTech said:**
> I have a Thinkpad R40 and I can't seem to get past the boot screen for the CD.  I had the same issue with the last version and I just tried this on 8.04 with the same result.  The checksum matches and I was able to install OpenSUSE 10 - so I know the CD drive is OK.

When the CD boots and I get the screen, which asks if I want to run the LiveCD or check the disk, etc... when I press the ENTER key to do anything, it freezes.  I tried the alternate disk aswell on the last version and it was unsuccessful too.

Perhaps you should start another thread asking for help with this. Anyway, did you try  ```
noapic nolapic
``` as boot options? This often helps with hardware locks, as might be your case

---

