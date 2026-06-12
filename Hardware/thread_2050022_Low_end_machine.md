---
title: "Low end machine?"
date: 2012-08-29
forum: Hardware
---

### Post by rmcellig on 2012-08-29
I read a lot about distros for low end machines. Is my computer considered a low end machine?

It's a Dell Dimension 3000 circa 2002. It has 2GB of Ram and a celeron 2.66ghz processor. I'm trying to figure out what distros would match up well with my computer.

---

### Post by ahallubuntu on 2012-08-29
With 2GB of RAM, any distro of Ubuntu will work fine on it.  Lubuntu may work a little better than plain Ubuntu, but Lubuntu is a little less friendly and "pretty."  Try both.

Unfortunately, you are stuck with integrated video - this Dell has no AGP or PCI-E slot to add a better video card.

I would personally upgrade the Celeron CPU to a Pentium 4 (which is the CPU class in that machine).  That could help video performance a little.  I have worked on many Dells of that vintage.  You can probably get a faster CPU for as cheap as $5 on eBay, if you find out which ones are compatible.

Upgrading the CPU on one of these Dimensions is pretty easy - you can do it without a screwdriver.  Here is a link to the service manual with exact instructions and diagrams:

[http://support.dell.com/support/edocs/systems/dim3000/en/SM/index.htm](http://support.dell.com/support/edocs/systems/dim3000/en/SM/index.htm)

Looks like you can get a hyperthreaded P4 with an 800MHZ Front-Side Bus.  That should give you a really nice speed boost.  (Hyperthreading may add 10% to 20% to the performance vs. a CPU without it.)

[http://support.dell.com/support/edocs/systems/dim3000/en/SM/specs.htm#wp1075776](http://support.dell.com/support/edocs/systems/dim3000/en/SM/specs.htm#wp1075776)

Here's a list of Pentium 4 CPUs.  You can use this reference to find CPUs that are compatible (Northwood Socket 478 should work, up to 3.2GHZ, FSB of 800MHZ or 533MHZ).

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#Northwood_.28130_nm.29](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#Northwood_.28130_nm.29)

Search the CPU eSpec you find in the Wikipedia listing on eBay.  For example, the 3GHZ P4 HT has two CPU numbers (eSpec): SL6WK and SL78Z.  Search for those on eBay, see what they are selling for.  If they cost too much, look for other ones.  Even a regular P4 Northwood Socket 478 without Hyperthreading would be a step up from that Celeron.

---

### Post by Petro Dawg on 2012-08-29
I installed Xubuntu on an old Dell Dimension 3000 that I saved from the trash at work.  Xubuntu ran flawlessly on it.  If I were you, I would try live sessions of ubuntu, kubuntu, and xubuntu and select the one you like best.  They are all good.

You might also look at Fedora-17 (although the ubuntu only crowd will hate me for mentioning it).  Try many and pick what fits you best.  Personally, I find it fun to test drive different linux flavors.

---

### Post by rmcellig on 2012-08-30
Thanks for all the feedback! I am using the Dell for one thing only and that is recording my radio shows. I have puppy Linux installed on it and it runs great!! I just want to install an alternate distro. I think I will take a look at Xubuntu 12.04 and see how it goes. Regarding cpu's I will check that as well.

---

### Post by rmcellig on 2012-08-30
So if I try this one at the top processor speed it should work in my dell dimension 3000?

I got this info from the service manual link you posted above. I don't have to change the fan or power supply? That would be great of all I need to buy is the CPU and replace what I currently have.

Intel® Pentium® 4 processor that runs at 2.8 GHz , 3.0 GHz, and 3.2 GHZ internally and 800 MHz externally with Hyper-Threading Technology

---

### Post by ahallubuntu on 2012-08-30
I have upgraded a couple of similar Dells and never needed to upgrade anything else.  The fan and heat sink should be fine, as long as you are choosing a CPU listed in the Dell spec.  Power supply: MAYBE.  If you have a lot of other loads on the power supply (several drives and add-in cards) already, perhaps you should upgrade the power supply too.  If not, just a single hard drive and no add-in cards, it should be fine.

A power supply upgrade might be advisable anyway on this old Dell if you've never upgraded it.  I've replaced a lot of them due to failure.  (power light turns yellow, unit won't power on.)  Plus, newer 80+ rated power supplies can use about 10 watts less just sitting there idle.  I see them on sale in the US sometimes for $20 USD after rebate.  Sometimes you can't quite fit the back connector and switch of a generic power supply through the back of a Dell case.  I recently had to cut (physically) some of the metal off the back of a Dell case to access the power connector.  It wasn't a 3000.  They're all a little different.
 
You might want to get some thermal paste to put on the new CPU (clean off any old/burnt thermal paste or pad from old heat sink if need be before replacing the CPU).  I just upgraded one from a 2.4GHZ to 2.8GHZ and there was no residue at all (or paste) on the old heat sink, so I didn't do anything, just swapped CPUs.

One thing: if you still have Windows(?) by chance, I would look at upgrading the BIOS to latest available from Dell, if possible, for the 3000.  If you can't do this, most likely the new CPU will work anyway, but sometimes BIOS upgrades add support for newer CPUs.

---

### Post by rmcellig on 2012-08-30
Great advice! Thanks!!

---

### Post by rmcellig on 2012-08-31
[QUOTE=Petro Dawg;12205351]I installed Xubuntu on an old Dell Dimension 3000 that I saved from the trash at work.  Xubuntu ran flawlessly on it.  If I were you, I would try live sessions of ubuntu, kubuntu, and xubuntu and select the one you like best.  They are all good.

I installed Xubuntu 12.04 on my Dell 3000 and love it. What a fantastic OS. Sure is different than what I remember it to be. Is it wise to update to 4.10 from 4.8 xfce or should I wait untill the next major xubuntu update in October? If it's safe to update, how would I go about doing this?

---

### Post by mörgæs on 2012-08-31
L/Xubuntu are great, but you should consider a little tweak here and there:

[http://ubuntuforums.org/showpost.php?p=12207789&postcount=6](http://ubuntuforums.org/showpost.php?p=12207789&postcount=6)

---

