---
title: "Red face  Laptops with locked Bios (this means no changing the wireless card)"
date: 2008-07-19
forum: Hardware
---

### Post by mimagabooks on 2008-07-19
**[CENTER]I have started this post to begin the reporting of systems that do not allow a person to change their wireless cards.[/CENTER]**

**[CENTER]Please report any systems that don't take replacement parts[/CENTER]**

Why does this matter? It matters if you want a better card or even if your old card brakes and you need to replace it. Just buying a card with the same chip set will not be enough. Its id must be one that the manufacturer has set in its BIOS; translation you pay lots more.


The term for this practice is "locked Bios system"


Laptops that have this problem that I have found today.

**HP**

Pavilion models

dv5000 CTO
(amd64 with bcm4318) Most likely all models of the 5000 series have locked bios.

**Compaq**

Compaq nc6000 (all others in this series would be a safe bet)

There are dozens of other reports on hps forums check for your model and then please report it here.

It is a safe bet that all HP Compaq products have locked Bios in them. The exception might be their impossibly high end business laptops and gaming laptops.


**Sony**

I would lay money on it being so, I have recently worked on a system that seemed to require vista be on it's hard drive. In others words no vista no laptop, you couldn't even reinstall their vista backup after a clean wipe of the hard drive. This would be an example of a OS Depended bios lock. (Would like to hear from others to confirm this type of lock)

So my money is on Sony having a wireless card bios lock as well.


**Dell**

Several of my friends have changed out their bcm43xx series for Gigabyte GN-WI01HT MINI PCI units.

So we need more reports on this brand but so far it seems promising.

**Toshiba**

?

**Acer**

?


[CENTER][B]Please Report Systems and manufacturers that allow you to change.

Educate the buyer to influence the market![/B][/CENTER]

---

### Post by mimagabooks on 2008-07-19
Just a Quick quote from hp forums.

The cards are physically identical and only differ by firmware IDs. The first excuse was blamed on FCC rules re: interactions between card and different antenna (since these are passive, this sounds bogus). SO.. why do non-American HP customers have to suffer these US-only "FCC restrictions?" Why not supply a BIOS option to turn the lock off for non-Americans - not every country agrees with the FCC - or even cares. The whole point of a laptop is to travel and not be restricted to one country - why this US-centric restriction?

The later second excuse (since we we're unconvinced of the first one) was the stupid HP LED/button - so what if it's flakey, give us the option, we're grown-ups!!! It states on your website that the i2200 & nc6000 are compatible - of course they are, they are Intel-approved Centrino components!

The REAL excuse: because HP prefer to charge a huge markup on generic cards. Now, look what's happened to Microsoft in the courts over anti-competitive practices.. wise-up before it's too late HP. Either supply an unlocked BIOS or we demand you compensate us with a 1-for-1 trade-in for our official Intel 2200's for your corporate-hacked ones.

---

### Post by mimagabooks on 2008-07-19
Quote 1:

bios hack for hp dv1000 series laptops with unsupported wireless cards

[Log in to get rid of this advertisement]
ok, dont know if you have heard about this, but appearently hp has been ordered by the fcc ( or so they say) to only allow usage of certain wireless cards in the new bios updates. (so dont update your bios if you have a bios that is older than june of 2004). It is a full on bios lockout and halt. the problem is this. i bought a bad *** 400mW atheros chipset wireless minipci card and put it in and got "104 unsupported wireless network device detected. remove the device and restart. system halted." something like that, i dont remember the exact, but if you have seen it you know. so here is my question. my bios is a Phoenix NoteBIOS 4.0 Release 6.0, and on the Phoenix site [http://www.phoenix.com/en/Products/C....0/default.htm](http://www.phoenix.com/en/Products/C....0/default.htm) there is release 6.1 out. so if i use thier flash utility and flash it, will i screw up bad, or will it write the original un-hp-tainted bios to the eeprom and boot just fine allowing me to use my wireless card that is linux compliant? the original card is a broadcom, and sucks, and i hate ndiswrapper. the card is usable with the system... dont let the "unsupported" crap fool you. i can boot up without the card inserted, and hurry and put it in between the bios boot and the lilo prompt (probably not good for the card huh?) and linux sees it and i even built the drivers and had it working, but on reboot, i have to take it out power on, put it back in at the precise moment, and dont reboot for as long as possible. i mean seriously, what are they trying to pull here. if i wanted a mac, i wouldve bought one, and probably shouldve. does anyone know the answer to what i ask, or have a better solution?


Quote 2:

ok, just for anyone that wants to know... i used this guys instructions to edit the eeprom on my atheros SR2, and low and behold, it works beautifully. the site is here, cause i dont see the reason for me to recap what he did.

[http://www.dagarlas.org/stuff/computing/article0001.php](http://www.dagarlas.org/stuff/computing/article0001.php)

i used his binary instead of compiling my own, but the code is easy enough to edit for your needs. his binary will work on all atheros cards that i know of, or at least all of them with the 5211, 5212, or 5213 chipset.

now, next i am going to use ethtool to edit the eeprom on my 200mW saneo minipci card, and if it works i will put up an amazing howto like he did. i will do this cause the saneo cards are way cheaper than the atheros ones, for a powerful card. and they have 2 ufl antenna connectors, just like the original card... but the SR2 only has one ufl... i will then be purchasing a saneo b/g model, and i will do the same to it, and post a howto for it. the saneo b/gs are very strong cards... and also have the 2 connectors on them.. i will then work on other cards.. but most wireless cards will be base on either the prism (saneo) chipset, or the atheros chipset.. other cards that you want me to see if i can get around the bios lockout.. let me know... and if i can afford the card, i will give it a shot.

this is actually better than trying to hack the bios, cuase you will not mess up the system like this.

---

### Post by iTrickU on 2010-06-01
Be VERY careful when updating the bios of a dv9000, i've had 2 and both updates screwed up the numlock function, when numlock is on letters on the keyboard turned to numbers, made it impossible to type with numlock on.

The motherboard will have to be re-tattooed and only hp can do it.

---

