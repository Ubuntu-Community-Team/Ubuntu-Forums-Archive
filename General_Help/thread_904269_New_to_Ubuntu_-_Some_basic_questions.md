---
title: "New to Ubuntu - Some basic questions"
date: 2008-08-29
forum: General Help
---

### Post by corkyo4 on 2008-08-29
Hi,

i have just discovered ubuntu and am keen to use it as it seems like a better alternative to xp.

i have a few questions though. 

Firstly im running an acer 5612WLMI laptop - 4gb of DDR2 ram, 1.66GHz dual core intel @ 667MHz, 120Gb HDD and ATI Mobility Radeon X1300 512Mb

My first question is,

Does Ubuntu typically run faster than XP??

Does it have support for most windows based applications, i.e. Itunes, Call of Duty 4, Norton Antivirus, Etc??

When i install it, will it overwrite my version of XP or does it install along side??

How Secure is the operating system??

Finally, i have 4Gb of memory in my machine, however XP only see's 2 i think. Will Ubuntu recognise i have 4Gb of memory or is it the same as XP in that respect??

Many Thanks For Your Help


Tom

---

### Post by Crafty Kisses on 2008-08-29
Yes in some cases Ubuntu runs faster than XP, yes.

---

### Post by corkyo4 on 2008-08-29
Hi,

i have just discovered ubuntu and am keen to use it as it seems like a better alternative to xp.

i have a few questions though.

Firstly im running an acer 5612WLMI laptop - 4gb of DDR2 ram, 1.66GHz dual core intel @ 667MHz, 120Gb HDD and ATI Mobility Radeon X1300 512Mb

My first question is,

Does Ubuntu typically run faster than XP??

Does it have support for most windows based applications, i.e. Itunes, Call of Duty 4, Norton Antivirus, Etc??

When i install it, will it overwrite my version of XP or does it install along side??

How Secure is the operating system??

Finally, i have 4Gb of memory in my machine, however XP only see's 2 i think. Will Ubuntu recognise i have 4Gb of memory or is it the same as XP in that respect??

Many Thanks For Your Help


Tom

---

### Post by amac777 on 2008-08-29
> **corkyo4 said:**
> Does Ubuntu typically run faster than XP??

No. In my experience they are about the same.

> Does it have support for most windows based applications, i.e. Itunes, Call of Duty 4, Norton Antivirus, Etc??

No. In my experience you will have to investigate alternatives for many of the programs that you're used to running on XP.

> When i install it, will it overwrite my version of XP or does it install along side??

You can install it along side XP and then have a menu when you boot the computer of which you want to use.

> How Secure is the operating system??

Pretty secure even in it's default configuration. I don't run any anti-virus programs or even setup the firewall and I've not had any problems. 

> Finally, i have 4Gb of memory in my machine, however XP only see's 2 i think. Will Ubuntu recognise i have 4Gb of memory or is it the same as XP in that respect??

Assuming your memory problem in XP is not a hardware problem, I think Ubuntu would recognize all the memory. I have 1 GB though so not sure if there is anything special about 4 GB and your particular hardware config.

---

### Post by justleen on 2008-08-29
> **corkyo4 said:**
> 
Does Ubuntu typically run faster than XP??

Not neccisarily, that depens on what you install, and what starts at boot time. In my expierence, a clean linux  install boots slightly faster then a clean XP. In general you can assume they run the same (not trying to start a flame war here, just stating my experience)
> **corkyo4 said:**
> 
Does it have support for most windows based applications, i.e. Itunes, Call of Duty 4, Norton Antivirus, Etc??
 No. Linux is fundamentelly different then windows so you cannot run windows applications (you can, but not natively) THats said, almost any application you can imagine has a linux alternative.
> **corkyo4 said:**
> 
When i install it, will it overwrite my version of XP or does it install along side?? 
During install you will be given several options where to install ubuntu. If you have free space (as in: unpartitioned space or a partition on which ubuntu can install) it will give the option to install there. Check out the install faq on the wiki page for details.[/qoute]

> **corkyo4 said:**
> 
How Secure is the operating system??
 In what context? As in virus/malware protection? quite good.. 
As in "unhackable"? quite good..
as in "data protection"? quite good..

this is an age old question, and I dont think i can answer that easily.
Linux and unix a renowed for their security and stabilty, so...

> **corkyo4 said:**
> 
Finally, i have 4Gb of memory in my machine, however XP only see's 2 i think. Will Ubuntu recognise i have 4Gb of memory or is it the same as XP in that respect??

probably not.. xp can address 4GB without problems, so if XP is not seeing it, I would probably start with shuffling the modules around in diffent slots.. is you BIOS able to see the whole 4GB at all??

---

### Post by coffeecat on 2008-08-29
> **corkyo4 said:**
> Does it have support for most windows based applications, i.e. Itunes, Call of Duty 4, Norton Antivirus, Etc??

Windows applications don't run in Linux. You can get many of them to run in WINE, which itself runs in Linux, but that's a different matter. It's best to find the Linux/Ubuntu equivalent for your favourite Windows applications. Same story if you used a Mac - native Windows applications don't run on a Mac and vice versa.

And you don't need an alternative for Norton Antivirus. :wink:

> **corkyo4 said:**
> When i install it, will it overwrite my version of XP or does it install along side??

You have a choice:

1. Set it up as a dual-boot with Windows. You will probably have to resize your Windows partition.

2. Erase Windows and install Ubuntu so that it is the only OS on your machine.

3. Install it in the Windows partition using Wubi.

> **corkyo4 said:**
> How Secure is the operating system??

How long is a piece of string? No OS is 100% secure, but Linux is inherently more secure than Windows.

> **corkyo4 said:**
> Finally, i have 4Gb of memory in my machine, however XP only see's 2 i think. Will Ubuntu recognise i have 4Gb of memory or is it the same as XP in that respect??

It depends whether you install the 32-bit or 64-bit version of Ubuntu.* No 32-bit OS can see all of your 4GB - see [this link]("http://www.dansdata.com/askdan00015.htm") for an explanation. Actually, that's not quite true. If you use a kernel with PAE support, you can use more than 4GB with even a 32-bit OS, but that's not something most people use. And as far as Windows only seeing 2GB, I don't know. It should be showing you about 3.2 GB.

* Is that a core duo or core 2 duo Intel? You'll only be able to run a 64-bit OS on the core 2 duo.

---

### Post by cszikszoy on 2008-08-29
> **coffeecat said:**
> * Is that a core duo or core 2 duo Intel? You'll only be able to run a 64-bit OS on the core 2 duo.

Not true.  I'm running Hardy 32bit on my core2duo.

---

### Post by gusst250 on 2008-08-29
> **cszikszoy said:**
> Not true.  I'm running Hardy 32bit on my core2duo.

Ok wrong again, I'll explain. you can run a 32- and 64-bit OS with a core 2 dou. But only 32-bit with a core duo.

---

### Post by coffeecat on 2008-08-29
> **cszikszoy said:**
> Not true.  

I presume your first language is not English. I did not say "you can run only 64-bit OSs on a core 2 duo". I said that one would only be **able** to run a 64-bit OS on the core 2 duo - implication being that one would not be able to run a 64-bit OS on the core duo.

> **cszikszoy said:**
> I'm running Hardy 32bit on my core2duo.

I'm very glad to hear it. :p And I'm running Hardy 32bit on my 64 bit AMD X2. :wink:


**gusst250** is saying what I was trying to say.

---

### Post by mixmaster on 2008-08-29
> **coffeecat said:**
> I presume your first language is not English. I did not say "you can run only 64-bit OSs on a core 2 duo". I said that one would only be **able** to run a 64-bit OS on the core 2 duo - implication being that one would not be able to run a 64-bit OS on the core duo.
Actually, it doesn't matter what his first language is.  The statement as phrased is completely ambiguous.  The funny thing is that because I knew what you were trying to say I didn't perceive the ambiguity until someone else misread it.

English is a wonderful language for such constructs.

---

### Post by coffeecat on 2008-08-29
> **mixmaster said:**
> The statement as phrased is completely ambiguous.  The funny thing is that because I knew what you were trying to say I didn't perceive the ambiguity until someone else misread it.

You're quite right. When I replied to **cszikszoy**, I thought my original sentence was only slightly ambiguous. I was wrong. Not about the core2duo :wink:. I was wrong about it being only slightly ambiguous. It's **very** ambiguous. And my 'clarification' was even worse. :oops:

> **mixmaster said:**
> English is a wonderful language for such constructs.

Only too true. It reminds me of the (possibly apocryphal) job reference: "When this person joined our company, he set the standard to which he would work, and he has consistently achieved that standard ever since."

---

