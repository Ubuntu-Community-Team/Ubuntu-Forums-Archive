---
title: "A possible bug in Foxconn boards BIOS affects Linux ACPI"
date: 2008-07-24
forum: Hardware
---

### Post by TheAlmightyCthulhu on 2008-07-24
[B]Update: I just got off the phone with Foxconn, they called me from China (1 AM in Indiana, heh) and were asking if I would test an improved version of their BIOS based partially on the modifications I've made to mine, hopefully this all blows over, and regardless of who's fault it is or isn't, we can just go back to using our computers with full functionality.
[/B]
**Thanks to the community for helping me get the message to Foxconn.**

**Edit: Please tell Foxconn what you think of their behavior:**

[http://www.foxconnchannel.com/support/online.aspx](http://www.foxconnchannel.com/support/online.aspx)

You need to put in an email, and then it will bring up a form, choose Complain/Suggest.

FOXCONN PHONE NUMBERS and LOCATIONS OF US-Based facilities

[http://maps.google.com/maps?q=foxconn]("http://maps.google.com/maps?q=foxconn")

**Edit: Welcome Digg, Reddit, and Slashdot.**

[http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux](http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux)
[http://www.reddit.com/comments/6tcv8/foxconn_deliberately_sabotaging_their_bios_to/](http://www.reddit.com/comments/6tcv8/foxconn_deliberately_sabotaging_their_bios_to/)
[http://linux.slashdot.org/article.pl?sid=08/07/25/1150218](http://linux.slashdot.org/article.pl?sid=08/07/25/1150218)

**Who is Foxconn and why must we get the message to them?**

I've heard a lot of people ask, "Who the hell is Foxconn", if you use a PC, there's a good chance you have one of their boards, even if it's branded as MSI or some other brand, if you use a Nintendo Wii, XBOX 360, or Playstation 3, Foxconn made that motherboard, this isn't some little dodgy hardware maker with no name that we can afford to be quiet about.
------------
I have disassembled my BIOS to have a look around, and while I won't post all the results here, I'll tell you what I did find.

They have several different tables, a group for Windws XP and Vista, a group for 2000, a group for NT, Me, 95, 98, etc. that just errors out, and one for LINUX.

The one for Linux points to a badly written table that does not correspond to the board's ACPI implementation, causing weird kernel errors, strange system freezing, no suspend or hibernate, and other problems, using my modifications below, I've gotten it down to just crashing on the next reboot after having suspended, the horrible thing about disassembling any program is that you have no commenting, so it's hard to tell which does what, but I'll be damned if I'm going to buy a copy of Vista just to get the crashing caused by Foxconn's BIOS to stop, I am not going to be terrorized.

-----
**How to fix:**

**Get Intel's BIOS ACPI source compiler:**

sudo apt-get install iasl

**Dump your DSDT table:**

sudo cat /sys/firmware/acpi/tables/DSDT > dsdt.dat

**Disassemble it:**

iasl -d dsdt.dat

**Open it in Gedit:**

gedit dsdt.dsl

**Fix Foxconn sabotage:**

Find, the section that starts out with

```
            If (_OSI ("Windows 2000"))
            {
                Store (0x04, OSVR)
            }
```Go down til you get to the first

```
        }
        Else
        {
```Past that you should see Linux alongside Windows NT, which is above another Else that leads to Windows Me.

Should look like:

```
            If (MCTH (_OS, "Linux"))

            {
                Store (0x3, OSVR)
            }
```Change it to:
```

            If (_OSI ("Linux"))
            {
                Store (Zero, OSVR)
            }
```
Copy the section, and remove it and the other characters (CAREFULLY PRESERVING SYNTAX!!!!)

Then move the Linux section to right underneath Windows 2006 section.

It will look about like this now:

       ```
Name (OSVR, Ones)
    Method (OSFL, 0, NotSerialized)
    {
        If (LNotEqual (OSVR, Ones))
        {
            Return (OSVR)
        }

        If (LEqual (PICM, Zero))
        {
            Store (0xAC, DBG8)
        }

        Store (One, OSVR)
        If (CondRefOf (_OSI, Local1))
        {
            If (_OSI ("Windows 2000"))
            {
                Store (0x04, OSVR)
            }

            If (_OSI ("Windows 2001"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001 SP1"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001 SP2"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001.1"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001.1 SP1"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2006"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Linux"))
            {
                Store (Zero, OSVR)
            }
        }
        Else
        {
            If (MCTH (_OS, "Microsoft Windows NT"))
            {
                Store (0x04, OSVR)
            }
            Else
            {
                If (MCTH (_OS, "Microsoft WindowsME: Millennium Edition"))
                {
                    Store (0x02, OSVR)
                }
            }
        }

        Return (OSVR)
    }

```**Don't recompile it yet, or this will happen:**

```


dsdt.dsl  6379:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6393:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6408:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6423:             Acquire (MUTE, 0x0FFF)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6437:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6452:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6467:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

Compilation complete. 0 Errors, 7 Warnings, 0 Remarks, 77 Optimizations
```These are bogus mutes that are harmless to Windows (it ignores them), but crash Linux sporadically, soooo....

Find and replace all seven occurences of Acquire (MUTE, 0x03E8) and replace with Acquire (MUTE, 0xFFFF), it appears they're trying to crash the kernel by locking a region of memory that shouldn't be locked, but without access to their source code comments, I can only speculate, this tells it to lock a memory address that is always reserved instead. ;)

**Now compile it**

iasl -tc dsdt.dsl

(You shouldn't get any warnings,there are any warnings or ERRORS, go find out what you did wrong!)

**And install it and configure the kernel to use it:**

sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml

sudo update-initramfs -c -k all

All future kernels should automatically find it there and build it.

**REBOOT**
--------------

This doesn't seem to help get rid of the suspend/resume and then reboot issue, but it appears to fix the rest, their BIOS is damned sloppy it's hard to really even tell what you're doing in there.

Use this advice at your own risk.

**So there you have it!**

[B]Edit: Complained to the Federal Trade Commission

[http://www.ftc.gov](http://www.ftc.gov)[/B]

[B]Foxconn
458 E. Lambert Road Fullerton
Fullerton, CA
92835

FOXCONN PHONE NUMBER: 714-871-9968

Company sold me a computer motherboard, model G33M-S, claiming that it was compliant with ACPI versions 1.0, 2.0, and 3.0.

Linux and FreeBSD do not work with this motherboard due to it's ACPI configuration, using a disassembler program, I have found that it detects Linux specifically and points it to bad DSDT tables, thereby corrupting it's hardware support, changing this and setting the system to override the BIOS ACPI DSDT tables with a customized version that passes the Windows versions to Linux gives Linux ACPI support stated on the box, I am complaining because I feel this violates an anti-trust provision in the Microsoft settlement, I further believe that Microsoft is giving Foxconn incentives to cripple their motherboards if you try to boot to a non-Windows OS.[/B]

[B]We have received your complaint.  

Thank you for contacting the FTC. Your complaint has been entered into Consumer Sentinel, a secure online database available to thousands of civil and criminal law enforcement agencies worldwide. Your reference number is:
19642372[/B]

**Edit: Full correspondence with Foxconn**

Me:

[B]ACPI issues, cannot reboot after having used suspend

Jul 22 08:37:53 ryan-pc kernel: ACPI: FACS 7FFBE000, 0040
Jul 22 08:37:53 ryan-pc kernel: ACPI: FACS 7FFBE000, 0040
Jul 22 08:37:53 ryan-pc kernel: ACPI: FACS 7FFBE000, 0040
Jul 22 08:37:53 ryan-pc kernel: ACPI: FACS 7FFBE000, 0040
Jul 22 08:37:53 ryan-pc kernel: ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  70, should be 69 [20070126]

I get these messages in my system log at boot, I also fail to reboot after having used suspend in a session, it hangs and plays a continued beep on the PC speaker.
[/B]

Foxconn:

[B]Dear Ryan:

Do you get the same beep codes if you were to remove all RAM out and then turn the system ON again?[/B]

Me:

[B]No, because then I wouldn't be able to boot into Linux, suspend to RAM, to get the ACPI failure, have syslogd pollute my /var/log/messages file with it, or read about it in my system log.

In particular, the number of quirks that the kernel has to use, and this invalid checksum are what has me nervous.

If you need me to attach the full contents of /var/log/messages, I can do so.[/B]

Foxconn:

[B]Dear Ryan:

This board was never certified for Linux. It is only certified for Vista. See URL below. So please test under Vista. Does this issue also occured under Vista or Winxp?

[http://www.foxconnchannel.com/product/Motherboards/certification.aspx](http://www.foxconnchannel.com/product/Motherboards/certification.aspx)[/B]

Me:

Well, this is a replacement for a dead Intel board (a 945g that fully supported ACPI), Vista was never really up for consideration, and I'm not about to go buy a copy to find out.

[B]The ACPI specs are there for a reason, and broken BIOS's like what is in this motherboard are the reason standard ACPI does not work, I've taken the liberty of filing the report in kernel.org, Red Hat, and Canonical's Ubuntu bug tracking systems, and posting the contents of my kernel error log on my blog, which is in the first several results if you Google search "Foxconn G33M" or "Foxconn G33M-s", "Foxconn Linux", etc, as well as prominently in other search formats, so hopefully this will save other people from a bad purchase, and hopefully kernel.org can work around your broken BIOS in 2.6.26, as I understand that kernel is more forgiving of poorly written BIOSes built for Windows.

I've already gotten several dozen hits on those pages, so you guys are only hurting yourselves in the long run, by using bad BIOS ROMs, as people like me are quite vocal when dealing with a bad product.
[/B]

Foxconn: 

[B]Dear Ryan,

Making idle treats is not going to solve anything.

As already stated this model has not been certified under Linux nor supported.

As you are unhappy with the product- using a non-support operating system nor certified, please contact your reseller for a refund.[/B]

Me:

[B]Yeah, well, I allege that you guys thoroughly suck.

Learn how to write a BIOS before you go selling hardware with falsified specs.[/B]

Me:

[B]I've been debugging your AMI BIOS, and the ACPI support on it is far from within compliance with the standards, I've dumped out the debugging data into  Canonical's Launchpad bug tracking system so that we may be able to support some sort of a workaround for the bad ACPI tables in your BIOS, I would hope that you will be part of the solution instead of the problem, alienating customers and telling them to go buy a copy of Windows Vista is not service, your product claims to be ACPI compliant and is not, therefore you are falsely advertising it with features it isn't capable of.

I would ask that you issue an update that doesn't make it dependent upon Windows Hardware Error Architecture, but that decision is up to you.

Please find all relevant data here:

Bug #251338 in Ubuntu: &#8220;Bad ACPI support on Foxconn G33M/G33M-S motherboards with AMI BIOS&#8221;
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338)

I appreciate your consideration in this matter.

-Ryan[/B]

Foxconn:

[B]Dear Ryan,

You are incorrect in that the motherboard is not ACPI complaint. If it were not, then it would not have received Microsoft Certification for WHQL.

Refer to:
[http://winqual.microsoft.com/HCL/ProductDetails.aspx?m=v&g=s&cid=105&sv=&f=&pn=G33M-S&oid=3179](http://winqual.microsoft.com/HCL/ProductDetails.aspx?m=v&g=s&cid=105&sv=&f=&pn=G33M-S&oid=3179)

As already stated, this model has not been certified under Linux nor supported.

It has been marketed as a Microsoft Certified Motherboard for their operating systems.[/B]

Me:

[B]I've found separate DSDT tables that the BIOS hands to Linux specifically, changing it to point to the DSDT tables Vista gets fixes all Linux issues with this board.

So while I accept that you've gotten some kind of Microsoft Certification (doesn't surprise me), that does not make your board ACPI capable, just that Windows is better at coping with glitches custom tailored to it, for this purpose.[/B]

Foxconn: 

[B]Dear Ryan,

Stop sending us these!!![/B]

Me: 

[B]Your BIOS is actually pretty shoddy, I've taken the liberty of posting everything that's wrong with the DSDT lookup tables and how to fix some of it so the community that has already purchased your filth can make do with it, also, it's now pretty much impossible to google Foxconn and Linux in the same sentence without getting hit by the truth, that your boards aren't good enough to handle it.

Have a very nice day.[/B]

Foxconn:

[B]Dear Ryan,

Surely this is the way to ask for us to attempt to fix something that is not supported in the first place.[/B]

Me:

[B]Would it be so difficult? I mean really? I suppose you've never heard of building a happy customer base vs. just angering everyone that deals with your products to the point they make sure others don't make the mistake of buying them.

You know, I have several computers, and they all support any OS I want to put there, as well they should, if you can't fix the damaged BIOS you put there intentionally, can you at least put a big thing on the site that says no LInux support so people won't make the mistake of buying your stuff?

Your DSDT table looks like it was written by a first year computer science student, it is scary, I will not just shut up and go away until I feel like I've been done right, this can end up on Digg, Slashdot, filed with the FTC that you are passing bad ACPI data on to Linux specifically.

I saw you targeting Linux with an intentionally broken ACPI table, you also have one for NT and ME, a separate one for newer NT variants like 2000, XP, Vista, and 2003/2008 Server, I'm sure that if you actually wrote to Intel ACPI specs instead of whatever quirks you can get away with for 8 versions of Windows and then go to the trouble of giving a botched table to Linux (How much *is* Microsoft paying you?) it would end up working a lot better, but I have this idea you don't want it to.[/B]

---

### Post by quinnten83 on 2008-07-24
And now in English....?

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **quinnten83 said:**
> And now in English....?

They detect Linux, give it a bad DSDT table, one that looks ok at a glance, but broken in subtle ways so that some of it works, but not correctly.

You call them to ask why their board won't run Linux.

They tell you to buy Vista.

They're basically rubbing Microsoft's back. (To keep this G rated)

---

### Post by gunashekar on 2008-07-24
Is it possible to correct the problem and publish it? What legal issues will be there?

---

### Post by bruce89 on 2008-07-24
Trustworthy Computing anyone?

---

### Post by klange on 2008-07-24
That is quite dubious...

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **gunashekar said:**
> Is it possible to correct the problem and publish it? What legal issues will be there?

Probably distributing proprietary source code.

Uhhhm, I wouldn't want to patch the hardware for this (too much that could go wrong), but I'm pretty sure I could fix it up to run as a custom DSDT loaded by the kernel on boot, basically that will override the table the BIOS has given it.

I'm reverting back to Hardy Heron as the kernel patch that allows custom DSDT's is not in Intrepid quite yet, there I'll test it and see what happens.

it's a simple one-line change to redirect to the same tables that Windows XP and Vista get, so I'm thinking I could cook something up pretty quick.

Distributing? No, but I might be able to post how to do it in general enough terms.

---

### Post by Polygon on 2008-07-24
posting before this gets dugg and the vast power of the internet makes foxconn crap their pants

anyway, that is very nasty. Maybe this should be posted on the kernel bug list as well, since they seem to be the ones who can actually write code to get around it

---

### Post by TheAlmightyCthulhu on 2008-07-24
Edit I posted this in OP instead

---

### Post by TheAlmightyCthulhu on 2008-07-24
This silences all the warnings from Hardy's kernel and lets mmconfig work as well.

What it won't do, yet, is let you suspend or hibernate, but I'm pretty sure that with all the ACPI work being done in 2.6.26, that Intrepid will support bad Windows ACPI tables through Windows Hardware Error Architecture support.

(sigh)

But at least this fixes a few things now, and more to come.

---

### Post by gunashekar on 2008-07-24
Great job!.. I agree that this must be brought to the attention of Kernel developers.

---

### Post by poofyhairguy on 2008-07-24
Well, no more Foxconn for me. That is disappointing as they were one of my favorite brands to recommend. Gigabyte or bust from now on I guess...

---

### Post by gletob on 2008-07-24
should we digg it ?

---

### Post by Polygon on 2008-07-24
i say do it.

---

### Post by Lord Xeb on 2008-07-24
Yes, agreee. That would be a good idea. Also, the more that the community is aware of it, the more pressure there would be to fix, and this the more people that are trying to get it done because everyone else is taking too long.

---

### Post by TheAlmightyCthulhu on 2008-07-24
Edit added to OP

---

### Post by the yawner on 2008-07-24
Interesting. I wonder if this is an isolated issue.

---

### Post by cardinals_fan on 2008-07-24
Somebody should put this on Slashdot.

---

### Post by tiachopvutru on 2008-07-24
> **the yawner said:**
> Interesting. I wonder if this is an isolated issue.

If there are a lot of these cases, we can blame Linux hardware incompatibility and instability on hardware makers who "perform shady acts under the scene in the best interest of Microsoft." :lolflag:

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **tiachopvutru said:**
> If there are a lot of these cases, we can blame Linux hardware incompatibility and instability on hardware makers who "perform shady acts under the scene in the best interest of Microsoft." :lolflag:

Was that ever in doubt?

Last Intel board I will ever own.

ONLY Foxconn board I will ever own.

Unfortunately, Foxconn is the one that provides a lot of Tier2 OEM's their main board, so it can be hard to pin it down to them, I really hope this doesn't become more widespread.

The biggest insult was them telling me their crap was ACPI compliant because MICROSOFT said it was.

---

### Post by stinger30au on 2008-07-24
nothing like publicity to get action.

slashdot it and digg it as well i say

---

### Post by tamoneya on 2008-07-24
is this a specific to foxconn issue or is it more related to the bios manufacturer(pheonix, ami...).  If it is specific to the bios manufacturer it may very well affect other brands of motherboards as well.  I have never had a foxconn board and dont plan on getting one so i dont know what they run for their bios.  It would be good if we could check other boards with similar bioses for this issue.

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **tamoneya said:**
> is this a specific to foxconn issue or is it more related to the bios manufacturer(pheonix, ami...).  If it is specific to the bios manufacturer it may very well affect other brands of motherboards as well.  I have never had a foxconn board and dont plan on getting one so i dont know what they run for their bios.  It would be good if we could check other boards with similar bioses for this issue.

It uses a customized AMI BIOS.

---

### Post by TheAlmightyCthulhu on 2008-07-24
Edit: added to OP

---

### Post by mrgnash on 2008-07-24
Disgusting behavior on their part :( Oh well, I'll know to give their products a wide berth in the future.

---

### Post by tamoneya on 2008-07-24
> **TheAlmightyCthulhu said:**
> It uses a customized AMI BIOS.

It still could be an upstream problem though even with a modified bios.  I dont have any recent boards with AMI so I cant check myself.  Does anyone else want to give it a try?

EDIT:  I just did some more research and it appears I had a misunderstanding about DSDT(DSDT is placed in the BIOS by the hardware manufacturer) and I now agree that the fault lies with foxconn.

---

### Post by Yes on 2008-07-24
Digg it: [http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux](http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux).

---

### Post by musicalmike235 on 2008-07-24
I know someone at work who is going to want to see this. 

Come tomorrow I am going to start harassing the phone operator at foxcomm until they explain themselves.

---

### Post by tamoneya on 2008-07-24
> **Yes said:**
> Digg it: [http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux](http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux).

dugg

reddit:[http://www.reddit.com/comments/6tcv8/foxconn_deliberately_sabotaging_their_bios_to/](http://www.reddit.com/comments/6tcv8/foxconn_deliberately_sabotaging_their_bios_to/)

---

### Post by cprofitt on 2008-07-24
> **TheAlmightyCthulhu said:**
> Was that ever in doubt?

Last Intel board I will ever own.



Um... why blame Intel?

---

### Post by Megaton on 2008-07-24
I have submitted this to Slashdot, hopefully we can get a real answer and some accountability from Foxconn.

---

### Post by Spr0k3t on 2008-07-24
I'm sending in my complaint to Foxconn... pitty too, I've got many Foxconn systems/equipment that will be replaced with something more Linux friendly.

---

### Post by aktiwers on 2008-07-24
Disgusting..   I look forward to read more replys from them..

---

### Post by Yes on 2008-07-25
Just wondering, what problems are caused by this?

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **Yes said:**
> Just wondering, what problems are caused by this?

Lots of weird errors in system log, no fan control, no thermal zone, quirky hardware support, no suspend, no hibernate, when I apply my custom DSDT table, I can suspend and resume alright, but when I go to reboot, the system freezes

---

### Post by SuperMike on 2008-07-25
> **TheAlmightyCthulhu said:**
> Linux and FreeBSD do not work with this motherboard due to it's ACPI configuration, using a disassembler program, I have found that it detects Linux specifically and points it to bad DSDT tables, thereby corrupting it's hardware support, changing this and setting the system to override the BIOS ACPI DSDT tables with a customized version that passes the Windows versions to Linux gives Linux ACPI support stated on the box, I am complaining because I feel this violates an anti-trust provision in the Microsoft settlement, I further believe that Microsoft is giving Foxconn incentives to cripple their motherboards if you try to boot to a non-Windows OS.

You seem very smart. I'm having ACPI issues with my Acer Extensa 4420 laptop. It has a Phoenix BIOS. How can I detect if I'm being messed with, as well?

And do you realize that if you can find a trail of emails between Microsoft and this provider, you've found another set of Halloween docs? Would be great if we could find the link here!

---

### Post by frup on 2008-07-25
I hope everyone diggs this and actively does everything they can to make people aware of this absolutely disgusting policy.

I can not see how this kind of behaviour does not violate anti-trust's

1) Actively making separate and flawed behaviour for Linux as a competing OS 

2) making older versions of Windows flawed too to force upgrades and sales.

I can't wait to see how this could be justified.

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **PrivateVoid said:**
> Um... why blame Intel?

AMD doesn't really seem to deal with vendors that don't support Linux lately.

Great Linux support on all my AMD boxes, I've been nothing but mad with this motherboard, the one it replaced, etc.

---

### Post by frup on 2008-07-25
4chan is up, maybe an /i/ on the digg post could be done. A personal army is tempting haha.

---

### Post by TheAlmightyCthulhu on 2008-07-25
I posted my full correspondence with Foxconn thus far.

I am so angry it's not funny,

---

### Post by frup on 2008-07-25
The slashdot submission has reached green on firehose ([http://slashdot.org/firehose.pl](http://slashdot.org/firehose.pl)) (linux -story) I gave it a plus

The digg post ([http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux](http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux)) has only 26 diggs currently.

---

### Post by quanumphaze on 2008-07-25
I've dugg it too, currently 26

It's pretty sad that anyone will go out of their way to break things for us.

> **TheAlmightyCthulhu said:**
> Lots of weird errors in system log, no fan control, no thermal zone, quirky hardware support, no suspend, no hibernate, when I apply my custom DSDT table, I can suspend and resume alright, but when I go to reboot, the system freezes

Oddly enough the exact same thing happens on an old P3 IBM desktop I have from around 2001. After suspend/resume when I shut it down it freezes at the point when it shuts down X. It's not related to this Foxconn problem though. If there is a fix for this computer (I never really bothered checking) it may work for the dodgy Foxconn board.

---

### Post by Polygon on 2008-07-25
im dig #28, i dont have a slashdot account so i cant +1 it, i dont even see the article on slashdot anyway.

---

### Post by Canis familiaris on 2008-07-25
Umm... I will now never recommend Foxconn to anyone.

---

### Post by quanumphaze on 2008-07-25
For anyone else who cant figure out Slashdot firehose you have to type "linux" into the tag box. The list box above it put's in "linux -story" which only gives out front page stories. We need to see all the submissions.

It's status is Green at the moment.

---

### Post by frup on 2008-07-25
> **quanumphaze said:**
> For anyone else who cant figure out Slashdot firehose you have to type "linux" into the tag box. The list box above it put's in "linux -story" which only gives out front page stories. We need to see all the submissions.

It's status is Green at the moment.

weird for me -story gives unpublished stories and plain story give front page articles

---

### Post by Polygon on 2008-07-25
i created a slashdot account just to +1 that one up, and now it appears to be orange. I take it that is good.

i did 'linux -story" to see the article

---

### Post by TheAlmightyCthulhu on 2008-07-25
Or you could just go to:

[http://slashdot.org/firehose.pl?op=view&id=790917](http://slashdot.org/firehose.pl?op=view&id=790917)

(Link subject to change later)

---

### Post by thunderdannc on 2008-07-25
I know we all want to jump on the bandwagon here, but this week I had a similar issue with ACPI, a Foxconn 661MXPlus, and Windows XP. During the install XP wouldn't detect the board as ACPI complaint and installed the Standard PC driver instead of the ACPI driver which caused all types of havoc with suspend and shutting down. I had to manually set ACPI using F5 during the install to get it working. Just filling you in that this may be a larger issue than just on the linux end. 

Could you post your board version and BIOS version? I'll try and post mine after work tomorrow. We sell these boards so it'll be interesting to see if this is a common thing.

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **thunderdannc said:**
> I know we all want to jump on the bandwagon here, but this week I had a similar issue with ACPI, a Foxconn 661MXPlus, and Windows XP. During the install XP wouldn't detect the board as ACPI complaint and installed the Standard PC driver instead of the ACPI driver which caused all types of havoc with suspend and shutting down. I had to manually set ACPI using F5 during the install to get it working. Just filling you in that this may be a larger issue than just on the linux end. 

Could you post your board version and BIOS version? I'll try and post mine after work tomorrow. We sell these boards so it'll be interesting to see if this is a common thing.

**DMI Decode dump:**

[http://launchpadlibrarian.net/16287094/dmidecode.txt](http://launchpadlibrarian.net/16287094/dmidecode.txt)

**Kernel Messages:**

[http://launchpadlibrarian.net/16287097/messages](http://launchpadlibrarian.net/16287097/messages)

The most obvious one would be:

Jul 24 02:25:48 ryan-desktop klogd: [    0.320385] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 70, should be 69 [20080321]

**Uname -a**

Linux ryan-desktop 2.6.26-4-generic #1 SMP Mon Jul 14 18:39:36 UTC 2008 x86_64 GNU/Linux

(Does the same things on .24, .25, .26 on EVERY Linux kernel I've tried)

---

### Post by wolfen69 on 2008-07-25
wow. we in linux land think that because suspend/resume is the biggest issue, that linux sux? i could name MANY faults with windows. use it if you want, but i wont be a part of it. community means alot to me. why do people spend so much time and money on windows, only to spend more money fixing it? (i should know, they pay me to fix it) and i laugh at them, silently.

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **wolfen69 said:**
> wow. we in linux land think that because suspend/resume is the biggest issue, that linux sux? i could name MANY faults with windows. use it if you want, but i wont be a part of it. community means alot to me. why do people spend so much time and money on windows, only to spend more money fixing it? (i should know, they pay me to fix it)

I said FOXCONN sucks, there's no reason for all these errors, if it was just suspend, I wouldn't be all that pissed.

---

### Post by Canis familiaris on 2008-07-25
> **wolfen69 said:**
> wow. we in linux land think that because suspend/resume is the biggest issue, that linux sux? i could name MANY faults with windows. use it if you want, but i wont be a part of it. community means alot to me. why do people spend so much time and money on windows, only to spend more money fixing it? (i should know, they pay me to fix it) and i laugh at them, silently.

You have misunderstood this thread.

---

### Post by collinp on 2008-07-25
Sounds like they are doing things in support of Microsoft. Does anyone have a clue about how they certified this motherboard?

---

### Post by Polygon on 2008-07-25
they most likely just check to make sure it works and it doesnt do anything bad to the operating system, im sure they dont inspect the source code to see that they are doing anything bad like this

and it seems that the slashdot thing is red, so should we see this on the front page tommrow? :D

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **Polygon said:**
> they most likely just check to make sure it works and it doesnt do anything bad to the operating system, im sure they dont inspect the source code to see that they are doing anything bad like this

and it seems that the slashdot thing is red, so should we see this on the front page tommrow? :D

That doesn't explain the bogus mute's that were there just to crash the kernel, or why the checksum was invalid.

---

### Post by collinp on 2008-07-25
if they certified it like that, then they would have caught it when they tested linux.

---

### Post by Mercury_Alpha on 2008-07-25
While intent is difficult to establish here, it's obvious to me that they messed up a pretty straightforward set of instructions.

BTW, the Reddit submission shot like a rocket to its front page. Should be some interesting discussion there.

---

### Post by wolfen69 on 2008-07-25
> **Anurag_panda said:**
> You have misunderstood this thread.

would not be the first time. sorry.

---

### Post by Trail on 2008-07-25
Horrible. 

(Yeah, this is why I have stopped upgrading my hardware and just upgrade my software nowadays :P)

---

### Post by last1 on 2008-07-25
Mental note: Don't buy Foxconn. Or apparently Dell because they buy Foxconn stuff

---

### Post by TheAlmightyCthulhu on 2008-07-25
I just filed a complaint with the Better Business Bureau, over false advertising, bad customer service, and misleading business practices.

[http://www.labbb.org/BBBWeb/Forms/Business/CompanyReportPage_Expository.aspx?CompanyID=13160422](http://www.labbb.org/BBBWeb/Forms/Business/CompanyReportPage_Expository.aspx?CompanyID=13160422)

BBB gives Foxconn an F:

"We strongly question the company’s reliability for reasons such as that they have failed to respond to complaints, their advertising is grossly misleading, they are not in compliance with the law’s licensing or registration requirements, their complaints contain especially serious allegations, or the company’s industry is known for its fraudulent business practices. "

---

### Post by jimv on 2008-07-25
Wow, I just read the OP, and I must say that he's dramatizing the whole situation a bit much.  I mean, seriously, the idea that Foxconn is trying to "destroy Linux ACPI" is ridiculous.

---

### Post by jimv on 2008-07-25
> **TheAlmightyCthulhu said:**
> I just filed a complaint with the Better Business Bureau, over false advertising, bad customer service, and misleading business practices.

[http://www.labbb.org/BBBWeb/Forms/Business/CompanyReportPage_Expository.aspx?CompanyID=13160422](http://www.labbb.org/BBBWeb/Forms/Business/CompanyReportPage_Expository.aspx?CompanyID=13160422)

BBB gives Foxconn an F:

"We strongly question the company&#8217;s reliability for reasons such as that they have failed to respond to complaints, their advertising is grossly misleading, they are not in compliance with the law&#8217;s licensing or registration requirements, their complaints contain especially serious allegations, or the company&#8217;s industry is known for its fraudulent business practices. "

Yeah, with a whopping 2 complaints that were just added tonight.  My God, they're villians!

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **jimv said:**
> Yeah, with a whopping 2 complaints.

Make that three. :P

---

### Post by KiwiNZ on 2008-07-25
please remember this thread is about an allegation not  a proven situation.

People should use caution when posting

---

### Post by d-_-b.za on 2008-07-25
Thanks for the heads up, one of my distributors only sell Foxconn boards, but luckily I haven't bought one yet and now I know to stay away from them.

But this brings another question to my mind: Do we have a central database/place to see which hardware is GNU/Linux compatible and which are not?

If anybody knows of such a database please post it, or otherwise one might need to start a database like this.

Regards,

Ps. I'm a Xubuntu newbie so if their is a obvious database like this please still post it here, or just pm me.

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **KiwiNZ said:**
> please remember this thread is about an allegation not  a proven situation.

People should use caution when posting

You can't argue that it at least would appear that they've gone well out of their way to run roughshod over Linux.

1. First they use a very invasive method to try and detect Linux, since Linux ACPI reports itself as Windows through the documented _OSI method, so we KNOW they were actively looking for Linux.

2. Introduce Mutes that Windows conveniently ignores, but lock up and crash Linux.

**Looks like a Search and Destroy mission to me!** ;)

---

### Post by KiwiNZ on 2008-07-25
> **TheAlmightyCthulhu said:**
> You can't argue that it at least would appear that they've gone well out of their way to run roughshod over Linux.

1. First they use a very invasive method to try and detect Linux, since Linux ACPI reports itself as Windows through the documented _OSI method, so we KNOW they were actively looking for Linux.

2. Introduce Mutes that Windows conveniently ignores, but lock up and crash Linux.

**Looks like a Search and Destroy mission to me!** ;)

To be honest I find it hard to believe that they have a campaign against Linux. There would be nothing to gain and would have a zero fiscal gain.

I think it is a bug you have found

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **KiwiNZ said:**
> To be honest I find it hard to believe that they have a campaign against Linux. There would be nothing to gain and would have a zero fiscal gain.

I think it is a bug you have found

After looking through the disassembled BIOS for the last several hours, rebooting it, and tweaking it more, I'd say this is very intentional, I've found redundant checks to make sure it's really running on Windows, regardless what the OS tells it it is, and then of course fatal errors that will kernel panic FreeBSD or Linux, scattered all over the place, even in the table path for Windows 9x, NT, 2000, XP, and Vista, and had to correct them (Well, at least divert them off into a segment of RAM I hope to god I'm sure about)

No, this looks extremely calculated, it's like they knew someone would probably go tearing it apart eventually and so tried to scatter landmines out so as to where you'd probably hit one eventually.

So if it is a mistake, or incompetence, then it's the most meticulous, targeted, and dare I say, anal retentive incompetence I've seen. :popcorn:

---

### Post by conb123 on 2008-07-25
I knew it, i currently have a 945g7ma-8ks2h Foxconn mobo and i have to add boot option noapic nolapic acpi=off otherwise it just freezes as soon as i log in. Also i have sound issues whereas if i enable compiz my audio will just loop one note do you think this will fix that problem. Thanks alot though ive needed a thread like this for a long time wish i had never bought Foxconn.

_Conb123_

---

### Post by shadowber on 2008-07-25
> **KiwiNZ said:**
> To be honest I find it hard to believe that they have a campaign against Linux. There would be nothing to gain and would have a zero fiscal gain.

I think it is a bug you have found

How far fetched is it to you that MS is paying them to do this? I am not saying that this is the fact, but we have all seen the way MS behaves, and I just won't put it past them in this case, so theres your "fiscal gain" right there... 
Why would MS do this? How many times do you see in these very forums, how someone complains that they tried out Ubuntu, and hibernation, or any number of things didn't work, and they are going back to MS? 
The very fact that they get "certification" from MS lights a big red warning light in my head, so no I don't find it that hard to believe...

---

### Post by iMerlin on 2008-07-25
It's one thing to ignore operating systems that you don't want to support but it's totally unacceptable that they deliberately sabotage Linux support this way.

I hope the FTC will take a look at your claim of false advertising. Until then, someone should organize a boycott of Foxconn products.

I'm still curious how they are able to fulfill Windows standards and get a certification without being ACPI compliant. Especially because I'd think it would be easier from a engineering point of view to implement a certified standard than to make a hack for a specific operating system without getting the specs from someone.

Does Microsoft distribute some Windows specific information to motherboard makers?

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **iMerlin said:**
> It's one thing to ignore operating systems that you don't want to support but it's totally unacceptable that they deliberately sabotage Linux support this way.

I hope the FTC will take a look at your claim of false advertising. Until then, someone should organize a boycott of Foxconn products.

I'm still curious how they are able to fulfill Windows standards and get a certification without being ACPI compliant. Especially because I'd think it would be easier from a engineering point of view to implement a certified standard than to make a hack for a specific operating system without getting the specs from someone.

Does Microsoft distribute some Windows specific information to motherboard makers?

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=3fa347770a8a9cb3568600380ce4b5c041b3ac0b](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=3fa347770a8a9cb3568600380ce4b5c041b3ac0b)

ACPICA: Disassembler support for new ACPI tables

Implemented full disassembler support for the following new ACPI
tables: BERT, EINJ, and ERST. Partial disassembler support for
the complicated HEST table. These tables support the [B]Windows
Hardware Error Architecture (WHEA).[/B]

So yes, Microsoft can deviate enough to have proprietary BIOSes that only work with Windows, and if anything comes up, "We're jsut supporting implementation errors".

;)

This also means that Linux has to emulate WHEA as much as it can, and Intrepid Ibex using kernel 2.6.26 is a lot better than Hardy, even with my fix, it only has one serious ACPI bug left with my fix, and that is it hangs on the next reboot after I have used suspend in that session.

My guess is that this BIOS is using HEST with a liberal dose of "errors" that Windows conveniently fixes.

It doesn't really conform to ACPI, but it *does* work with Vista.

---

### Post by KiwiNZ on 2008-07-25
I am closing this thread in the interim to allow staff to review and gain advice

---

### Post by matthew on 2008-07-25
I have reviewed the thread. The information for how to fix the issue has been posted. The rest of the discussion is speculative and is better left for [other venues]("http://linux.slashdot.org/article.pl?sid=08/07/25/1150218&") like [these]("http://digg.com/linux_unix/Foxconn_deliberately_sabotaging_their_BIOS_to_destroy_Linux") and [more]("http://www.reddit.com/comments/6tcv8/foxconn_deliberately_sabotaging_their_bios_to/").

EDIT: 
I have had a few PMs and emails about the thread closure. I understand the issue. I would like to see a free and open discussion of this. However, my fears in doing so are several. We have a code of conduct in place in these forums. In my experience, these sorts of conversations are extremely difficult to maintain within those parameters as they generally become quite heated and emotional. That would require extra staff time to respond to reported posts and cause us to deal with issues that really are not well suited to a forum dedicated to tech-support, not politics or social action. A problem was discovered and posted about. A solution was found and also posted. That is why we exist.

While I understand the issue at hand, and while I am content to allow the original post to remain in place, completely uncensored, I am very nervous about the tenor of the conversation. Some have recommended that I post a warning to all to stay within the bounds of the Forums CoC while discussing the issue, but on something like this I would expect several pages of comments (mine included), and any comment I make to this effect would be buried quickly in the deluge.

Finally, we all need to remember that the company being complained about, Foxconn, has not had an opportunity to respond publically to the accusation, and that the quotes being attributed to them have not been substantiated. We do not wish to be a part of a possible character assassination. I'm not saying that is what is happening, but only one side has been offered, and all quotes are being given by that side. While it is entirely possible that a major wrong has been done that needs to be exposed, it is also possible that we are looking at a bug, simple incompetence or error, or something far less sinister.

So, if you feel the need to rant, to blow off some steam, or to make claims that the world hates us, hates our operating system, or you just want to post in support of the other side, please do so in the locations where that conversation is taking place.

---

### Post by matthew on 2008-07-25
Here is a quick followup from the [Phoronix forums]("http://www.phoronix.com/scan.php?page=news_item&px=NjYyMA"). 

> Receiving publicity on SlashDot today is word that [Foxconn refuses to support Linux]("http://linux.slashdot.org/article.pl?sid=08/07/25/1150218&from=rss"). Foxconn is a large OEM motherboard manufacturer, but according to a [thread on the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=869249"), they refuse to support Linux. There is a bug in one of their DSDT tables for their BIOS that's causing installation issues with Linux. The DSDT for Windows is correct, but Foxconn isn't interested in issuing a (simple) update to fix the Linux support. However, this isn't surprising to us. We've known that Foxconn does not wish to support Linux at all. Going back to 2006, Foxconn has told us at Phoronix that they aren't interested in Linux on their motherboards and they have no desire to support it. For more on motherboards under Linux, check out our [motherboard reviews]("http://www.phoronix.com/scan.php?page=category&item=Motherboards").

So, it appears we have third party confirmation of the issue, and of Foxconn's desire to NOT support Linux, at least confirmation enough for me to feel comfortable opening the thread again.

I would like to politely remind everyone to please keep comments within the Forum CoC...and with that, welcome back. Thank you to everyone for your understanding while the thread was closed.

---

### Post by Rocket2DMn on 2008-07-25
I have already finished the triage on the bug report posted at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338) since the OP provided the required information and confirmations were available elsewhere.  Thank you for the extra info, matthew.

---

### Post by flintmecha on 2008-07-25
Paranoia much?

So a no-name motherboard manufacturer screws up the code to make their BIOS compatible with Linux.. okay. They suck at making things compatible. 

Where's the proof that it was intentional? There is none. 

I sincerely believe some people just LOOK for ways to blame people for being "pro-micro$oft" or "anti-linux" so they can pitch a fit. 

Also, I buried this on Digg.

---

### Post by tamoneya on 2008-07-25
> **flintmecha said:**
> Paranoia much?

So a no-name motherboard manufacturer screws up the code to make their BIOS compatible with Linux.. okay. They suck at making things compatible. 

Where's the proof that it was intentional? There is none. 

I sincerely believe some people just LOOK for ways to blame people for being "pro-micro$oft" or "anti-linux" so they can pitch a fit. 

Also, I buried this on Digg.

Foxconn is not a no name manufacturer.  They make the motherboard for many major PC vendors (dell, hp ...) as well as the intel branded motherboards.  Also it isnt about being intentional or not.  It is about claiming to support ACPI.  ACPI is not OS dependent yet they load separate code for linux than for windows.

---

### Post by matthew on 2008-07-25
> **flintmecha said:**
> Paranoia much?

So a no-name motherboard manufacturer screws up the code to make their BIOS compatible with Linux.. okay. They suck at making things compatible. 

Where's the proof that it was intentional? There is none. 

I sincerely believe some people just LOOK for ways to blame people for being "pro-micro$oft" or "anti-linux" so they can pitch a fit. 
I agree, for the most part. I do think that this is evidence of an unwillingness to cater to the needs/desires of the Linux community, and therefore should be made public. However, there is no evidence that I have seen of direct action to exclude, only of intentional inaction not to include. However subtle, there is a difference. One reeks of malice, the other of apathy. 

Either way, I'll spend my money buying things from a company who is interested in supporting and complying with accepted standards, and will do so even more happily with a vendor who is actively interested in supporting Linux.

:)

---

### Post by damis648 on 2008-07-25
This makes me EXTREMELY angry. This is clearly intentional.

---

### Post by wolfemi1 on 2008-07-25
Very interesting issue.  I would like to extend my personal thanks for the terrific efforts of TheAlmightyCthulhu, since I'm about to build a system and I likely would not have been able to figure out this problem myself had I bought a Foxconn motherboard.  I also sincerely appreciate the bad publicity Foxconn is receiving from this, and I hope that it inspires them to change their practices, and hopefully scares off other manufacturers as well.  Could this (and similar actions) possibly be the source of the Linux ACPI woes of a few years ago?:confused:

---

### Post by motang on 2008-07-25
I say we boycott Foxconn!

---

### Post by tamoneya on 2008-07-25
Im curious to know what dell does about this.  They typically use OEM motherboards from foxconn yet they still support linux.  Could someone with a dell PC that was preinstalled with ubuntu run a check as shown in the OP?  Dell may have put in their own DSDT tables in order to clear out what foxconn did.  Would that be acknowledging foxconn's faulty claim of ACPI support?

---

### Post by damis648 on 2008-07-25
> **tamoneya said:**
> Im curious to know what dell does about this.  They typically use OEM motherboards from foxconn yet they still support linux.  Could someone with a dell PC that was preinstalled with ubuntu run a check as shown in the OP?  Dell may have put in their own DSDT tables in order to clear out what foxconn did.  Would that be acknowledging foxconn's faulty claim of ACPI support?

Mine was not preinstalled, but I will run a check just the same.

EDIT: and that was because Dell has not created their own driver for the graphics card, otherwise it would be and will be.

---

### Post by damis648 on 2008-07-25
Unfortunately there are no such if statements in my DSDT table source. If anyone would like to have a look at it and see if you can make any sense of it, please feel free. It is attached below. Please note my BIOS ARE NOT up-to-date. I am using A07, not the new A08. The A08 causes my trackpad to malfunction. When I apply a fix, it becomes unconfigurable. I am sticking with A07 right not because it works.

---

### Post by jgsack on 2008-07-25
I wonder if it might do some good to follow up your ftc complaint with a reference to this:

[http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf)

Regards,
..jim

---

### Post by kingtaurus on 2008-07-25
I did a quick decompilation of my AMI BIOS (on my ASUS P5K-E). It has the exact same snippet of code as the OP. I'm not having the same problems as the original poster. But I have experienced another BIOS related issue (the MTRR tables given to Linux by the BIOS are improperly configured :confused: when memory remapping is enabled).

My assumption is that the code section below is provided by AMI to both ASUS and Foxconn. My guess is that with both the ASUS and Foxconn decompiled BIOS section (assuming we have similar hardware, we might be able to figure out what they are doing).

```
  
        Store (One, OSVR)
        If (CondRefOf (_OSI, Local1))
        {
            If (_OSI ("Windows 2000"))
            {
                Store (0x04, OSVR)
            }

            If (_OSI ("Windows 2001"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001 SP1"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001 SP2"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001.1"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2001.1 SP1"))
            {
                Store (Zero, OSVR)
            }

            If (_OSI ("Windows 2006"))
            {
                Store (Zero, OSVR)
            }
        }
        Else
        {
            If (MCTH (_OS, "Microsoft Windows NT"))
            {
                Store (0x04, OSVR)
            }
            Else
            {
                If (MCTH (_OS, "Microsoft WindowsME: Millennium Edition"))
                {
                    Store (0x02, OSVR)
                }

                If (MCTH (_OS, "Linux"))
                {
                    Store (0x03, OSVR)
                }
            }
        }

```

---

### Post by snowpine on 2008-07-25
Interesting thread (though a lot of it was over my head). Maybe this is a stupid question, but how can I find out if any of my computers (Dell and Gateway) have a Foxconn mobo? Is there a physical logo or sticker, or do I need to boot up the computer and run some kind of command?

---

### Post by kingtaurus on 2008-07-25
I just tested Suspend and Resume (it worked properly and the logs appear clean).

---

### Post by CrazyGuy123 on 2008-07-25
**IF** this was done intentionally, it may not have been to directly "attack" desktop Linux.  It could be that since the motherboard was designed for desktop PC's, the manufacturers of the PC/board/BIOS decided to limit it's potential use for server systems (which are often Linux), since they prefer to sell server class motherboards for that.

The above idea, if true, gives financial motivation.

---

### Post by viper2007 on 2008-07-25
That is just retarded, i messaged foxconn about this and i hope everyone else that reads this contacts them to tell them how retarded they are.

---

### Post by pante on 2008-07-25
[I]ACPI (Advanced Configuration and Power Interface) is an open industry specification co-developed by Hewlett-Packard, Intel, **Microsoft**, Phoenix, and Toshiba. 

ACPI establishes industry-standard interfaces enabling OS-directed configuration, power management, and thermal management of mobile, desktop, and server platforms.[/I]

[http://www.acpi.info/](http://www.acpi.info/)

[email]info@acpi.info[/email]

---

### Post by Taxman415a on 2008-07-25
> **viper2007 said:**
> That is just retarded, i messaged foxconn about this and i hope everyone else that reads this contacts them to tell them how retarded they are.

Please do so, but also please do so with tact. There is little worse for the Linux community than overzealousness. That just gives people reasons not to bother.

Not wanting to support Linux is a perfectly acceptable business decision, even if we'd prefer differently. Foxconn's actions do look pretty suspicious though, since it seems they had to go out of their way to make the motherboard not work with Linux instead of just not supporting Linux. 

So tell them how you feel, but please do so politely.

---

### Post by azadpanchi on 2008-07-25
I recently bought a mother board, I am glad it wasn't a foxconn although I was considering it; needless to say I am glad.

Whats up with all the Linux hate in this world, what did Linux ever do to foxconn.

---

### Post by cbrunning on 2008-07-25
HI 

just to say as am from Foxconn, No we dont deliberately sabotage the bios
Plus the person who replyed to the email did not understand Linux

but we will have the bios fix sometime next week and at the same time a relook at how we are testing are boards with linux.

since this board should have been tested.

please dont flame me :)

heAlmightyCthulhu am sending a message hope you will reply

thanks


UK Technical Manager

---

### Post by phidia on 2008-07-25
> **snowpine said:**
> Interesting thread (though a lot of it was over my head). Maybe this is a stupid question, but how can I find out if any of my computers (Dell and Gateway) have a Foxconn mobo? Is there a physical logo or sticker, or do I need to boot up the computer and run some kind of command?

Open a terminal enter "lshw" that should give you the motherboard type & manufacturer plus lots of other output.

---

### Post by damis648 on 2008-07-25
> **cbrunning said:**
> HI 

just to say as am from Foxconn, No we dont deliberately sabotage the bios
Plus the person who replyed to the email did not understand Linux

but we will have the bios fix sometime next week and at the same time a relook at how we are testing are boards with linux.

since this board should have been tested.

please dont flame me :)

heAlmightyCthulhu am sending a message hope you will reply

thanks


UK Technical Manager

Sorry if you are from Foxconn, but this is quite unconvincing. Perhaps you should use proper English.

---

### Post by orclev on 2008-07-25
See, enough press gets results. Not supporting Linux I can understand and that's acceptable, but when you're made aware of a problem with a product it should be fixed (in this case Linux was irrelevant, there was a bug in the boards ACPI implementation, that fact that it only showed up in Linux doesn't make it any less of a bug). I'm not convinced Foxconn did or didn't deliberately try to prevent Linux from working with their motherboard either.

@TheAlmightyCthulhu
If they do follow through with this, make sure to update the BBB report you filed to show that they eventually did respond and fix the problem, even if it was only after a lot of pressure was exerted on them (more so than should have been necessary).

---

### Post by cbrunning on 2008-07-25
before you start on my English am dyslexic

so some of my typing english is bad

am here to help

---

### Post by SirYes on 2008-07-25
> **cbrunning said:**
> HI 

just to say as am from Foxconn, No we dont deliberately sabotage the bios
Plus the person who replyed to the email did not understand Linux

but we will have the bios fix sometime next week and at the same time a relook at how we are testing are boards with linux.

since this board should have been tested.

please dont flame me :)

heAlmightyCthulhu am sending a message hope you will reply

thanks


UK Technical Manager

Nice to hear from you with such positive statements. Thanks!

At least this is much quicker and more concrete response than recent Creative dumb posting to Daniel_K, who was releasing modified sound drivers for older Creative Sound Blaster cards... See the Knight_Rider's comment which contains an original post from Phil O'Shaughnessy (VP Corporate Communications, Creative Labs Inc.):

[http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&thread.id=116332&view=by_date_ascending&page=1](http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&thread.id=116332&view=by_date_ascending&page=1)

---

### Post by damis648 on 2008-07-25
> **cbrunning said:**
> before you start on my English am dyslexic

so some of my typing english is bad

am here to help

Ah, Sorry. Sometimes I do not think and am sincerely sorry. Back on topic, can you tell us why your BIOS specifically change most things ACPI when it finds that Linux is the Operating System? (Not a flame, just wondering)

---

### Post by cbrunning on 2008-07-25
thats am unable to answer yet
but i think the board in the early stages had problem with acpi for vista and was fixed.
but so i think your seeing the remain of the tested code, which should have be removed.

not the first time i've had to have acpi fixed on are boards
and will not be the last:)

---

### Post by damis648 on 2008-07-25
> **cbrunning said:**
> thats am unable to answer yet
but i think the board in the early stages had problem with acpi for vista and was fixed.
but so i think your seeing the remain of the tested code, which should have be removed.

not the first time i've had to have acpi fixed on are boards
and will not be the last:)

Thanks for your replies. When these bugs are fixed, we hope to hear back from you.

---

### Post by cbrunning on 2008-07-25
not a problem 

you will hear more, i say before the end of next week
as my report goes in on monday about this 
am going to enjoy this fight with china :) hehehe

---

### Post by Rocket2DMn on 2008-07-25
> **cbrunning said:**
> not a problem 

you will hear more, i say before the end of next week
as my report goes in on monday about this 
am going to enjoy this fight with china :) hehehe

I will continue to follow this thread, but if you could make a post on the Launchpad bug report when a fix is released, it would be much appreciated - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338)
At that time, an official link to the newer BIOS version and/or article that outlines the changes would also be appropriate.
Thank you.

---

### Post by Runamok on 2008-07-25
Hope this gets resolved soon!  The ball is in your court Foxconn!

---

### Post by | MM | on 2008-07-25
> **TheAlmightyCthulhu said:**
> After looking through the disassembled BIOS for the last several hours, rebooting it, and tweaking it more, I'd say this is very intentional...

While i agree this is a concerning situation.  I would think it a bit premature to make the accusations that are being made until it was found it failed on many versions of the linux kernel.  (I am no expert) Perhaps they tested on a RHEL (for example) kernel and the latest kernels change their behaviour such that they now fail with this BIOS implementation.

I am with Kiwi, it seems a reach that they would intentionally target Linux for failure.

---

### Post by feest on 2008-07-25
I don't know much about the lower end stuff on computers like biosses and acpi tables and i'm not askint to explain. but if there is a standard to provide any os that can deal with this standard a working platform. it should not be build to devide different os'es that can deal with the same standard. if it does. this cannot be good. Either poor coding or taking down linux. (i think the first)

---

### Post by another_sam on 2008-07-25
[http://www.foxconn.com/](http://www.foxconn.com/)

Look at the background. 
- Speed: OK.
- Quality: OK.
- Flexibility: Cropped.

And they are clearly proud about it. What else could you expect?

---

### Post by kencoe on 2008-07-25
Here is reply as a representative of the company I work at, and as the person in charge of component selection. I would suggest more responses the same. Response below was entered as an information request...

Please respond. I have read the article listed here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249)

If the accusations in this thread are true (I will be checking into it this weekend) It is bad marketing for your company to make false claims of compliance, or to handle complaints in such an unprofessional manner. The alleged conduct of the technician in the thread alone is grossly unprofessional. False compliance claims are immoral, unprofessional, and may even be illegal in this country. If this is indeed the contents of your conversation and/or your products are incorrectly labeled as compliant, , I will be removing all foxconn products from our listed product line. I will be looking into this accusation, and I expect a quick response from you if I am to continue to market and sell your products..

---

### Post by MighMoS on 2008-07-25
> **feest said:**
> I don't know much about the lower end stuff on computers like biosses and acpi tables and i'm not askint to explain. but if there is a standard to provide any os that can deal with this standard a working platform. it should not be build to devide different os'es that can deal with the same standard. if it does. this cannot be good. Either poor coding or taking down linux. (i think the first)

Actually, the second wouldn't be too far off. There is a public memo from Mr. Gates talking about possible ways to prevent Linux from reaping the benefits of ACPI (one of which was adding: surprise: Microsoft Windows-only extensions).

---

### Post by darrelljon on 2008-07-25
> **MighMoS said:**
> Actually, the second wouldn't be too far off. There is a public memo from Mr. Gates talking about possible ways to prevent Linux from reaping the benefits of ACPI (one of which was adding: surprise: Microsoft Windows-only extensions).

[Here]("http://hehe2.net/thedarkside/microsoft/even-more-incriminating-evidence-in-the-foxconn-debacle/")

---

### Post by T1Oracle on 2008-07-25
We need this on YouTube.  If we can get a popular video on YouTube about this issue then it will get more visibility.

---

### Post by Midwest-Linux on 2008-07-25
I posted a link of this thread to The Linux Link Net, the forum for the The Linux Link Tech Show.

[http://thelinuxlink.net/forum/viewforum.php?f=2](http://thelinuxlink.net/forum/viewforum.php?f=2)

---

### Post by Midwest-Linux on 2008-07-25
Also posted at the Linux section of the Vista Forums.

[http://thevistaforums.com/index.php?showforum=103](http://thevistaforums.com/index.php?showforum=103)

Also submitted to Castellini On Computers.

---

### Post by KiwiNZ on 2008-07-25
I am going to change the title of this thread to be more accurate.
 
Foxconn representatives have stated that it is a bug.
 
The title should reflect that it is a possible bug.
 
There has been no proof of deliberate action that part is an allegation

---

### Post by Vadi on 2008-07-25
It's a confirmed bug, I'm not sure why did you call it "possible". One might also note that it negatively, not positively affects Linux. 

"**A bug in Foxconn boards BIOS negatively affects Linux ACPI**"

---

### Post by TheAlmightyCthulhu on 2008-07-25
> **KiwiNZ said:**
> I am going to change the title of this thread to be more accurate.
 
Foxconn representatives have stated that it is a bug.
 
The title should reflect that it is a possible bug.
 
There has been no proof of deliberate action that part is an allegation

I still say it's a SET of very HORRIBLE, yet awfully CONVENIENT "bugs", and a big company like Microsoft may have baked a few million pies filled with $100 bills for these "bugs". :popcorn:

What do you want as proof?

```
            If (MCTH (_OS, "l1nux"))

            {
                Then (8Uy v1574, 5creW joOr5elF)
            }
```

---

### Post by sargek on 2008-07-25
This is an excellent thread and I am glad you brought this to light. As another poster mentioned, this harkens of "treacherous computing", and I wouldn't be surprised if the Sopranos, oops, I mean Microsoft, were behind this in some way.

The good thing about this is how it was discovered: by an intelligent individual who knows how to hack. This is what Open Source is all about - power in the hands of the users. This is why Microsoft will never be a threat to GNU/Linux and Open Source: we make them nervous because we operate in a way they cannot possibly fathom, and with ideals that are not governed by money, but by what is right for the community as a whole.

Excellent...

---

### Post by Lantesh on 2008-07-25
I recently put together a new system, and I did consider a Foxconn board.  Ultimately I went with an Asus board, because I've been using them for years, and they've always treated me well.  I am now seeing just how wise a move that was.  I can only imagine how terribly angry I'd have been had I wasted my money on a Foxconn board.  Thanks for the heads up.  I will certainly avoid their products in the future.

---

### Post by Niva on 2008-07-25
Thanks for the info posted here guys, I've been questioning ACPI errors on bootup in Fedora for months and never bothered researching into it.  I have an Asus motherboard and Gutsy 64 bit never installed successfully on it which forced me over to Fedora 8 which was capable of coping with a lot of the errors Gutsy complained about.  Definitely food for thought, I wonder if Foxconn is the only guilty company.

---

### Post by another_sam on 2008-07-25
> **sargek said:**
> This is an excellent thread and I am glad you brought this to light. As another poster mentioned, this harkens of "treacherous computing", and I wouldn't be surprised if the Sopranos, oops, I mean Microsoft, were behind this in some way.

The good thing about this is how it was discovered: by an intelligent individual who knows how to hack. This is what Open Source is all about - power in the hands of the users. This is why Microsoft will never be a threat to GNU/Linux and Open Source: we make them nervous because we operate in a way they cannot possibly fathom, and with ideals that are not governed by money, but by what is right for the community as a whole.

Excellent...

I loved that

---

### Post by DarKnyht on 2008-07-25
Here is a suggestion.  Instead of just flooding a company that doesn't care with complaints, those of us that have purchased a Foxconn board with this issue should file a complaint with the [Better Business Bureau]("http://www.bbb.org").  This is false advertising if the company claims that their boards is complaint when it is in fact not and furthermore sabotages your machine.

This is the sort of thing that should not be tolerated and we should get the big dogs after them.

---

### Post by ShiningHolden on 2008-07-26
I applaud you for compiling all of this.

Please teach me how I can inspect my BIOS. :P

---

### Post by Cresho on 2008-07-26
I spit on foxconn or what ever you spell it too!  I read the slashdot reffering to this thread and was like, WOW!

---

### Post by ilago on 2008-07-26
This is **not** a possible bug. It is a **real**, and now documented, bug.

I appreciate that a representative from Foxconn has posted here and advised that the bug will be rectified. Until that fix is provided and published, it remains a bug, **not** a possible bug.

ACPI is a documented standard, last updated in around 2006. Even if hardware manufacturers need to add functions, complying with published standards should be a requirement.

[http://www.acpi.info/spec.htm]("http://www.acpi.info/spec.htm")

---

### Post by Cresho on 2008-07-26
in light of this situation, I take back my spit quote.

Thanks foxconn!

---

### Post by Amaranth on 2008-07-26
That's funny, I thought the kernel now claimed to be "Windows" instead of "Linux" for this exact reason. It's easier to pretend to be Windows and be bug-for-bug compatible with them instead of trying to work around all of the old, broken, untested "Linux" paths in various ACPI implementations.

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **Amaranth said:**
> That's funny, I thought the kernel now claimed to be "Windows" instead of "Linux" for this exact reason. It's easier to pretend to be Windows and be bug-for-bug compatible with them instead of trying to work around all of the old, broken, untested "Linux" paths in various ACPI implementations.

It responds to OSI requests as every version of Windows there is (bites his hand).

It responds to their MCTH OS request as Linux, therefore the BIOS figures out Linux is Linux no matter what a properly formatted request would have given it.

So I had to get rid of their request and replace it with a standard OSI request, I probably could have just left it blank, but that would be adding even more sloppiness in there, so it's better off telling it "Even if it says it's Linux, give it table Zero anyway", then the BIOS really has no other way to countermand that.

B-)

---

### Post by billgoldberg on 2008-07-26
Why people are thanking the OP is beyond me.

*<mumbles something quietly>*

It's ridiculous.

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **billgoldberg said:**
> Why people are thanking the OP is beyond me.

*<mumbles something quietly>*

It's ridiculous.

Probably seeing as how Foxconn makes 8 out of every 10 PC motherboards, just relabels them as MSI and others, so you could have a Doomsday situation out there where 80% of computers could not boot and run Linux.

I suspect they were dipping their toe in the water with this one model series, to see what would happen.

---

### Post by billgoldberg on 2008-07-26
> **TheAlmightyCthulhu said:**
> Probably seeing as how Foxconn makes 8 out of every 10 PC motherboards, just relabels them as MSI and others, so you could have a Doomsday situation out there where 80% of computers could not boot and run Linux.

I suspect they were dipping their toe in the water with this one model series, to see what would happen.

I doubt very much they make 80% of all the motherboard.

You're right to speak out, I just find the number of thanks to be ridiculous.

---

### Post by Rocket2DMn on 2008-07-26
The story was dugg, hit reddit, and slashdot -> 150,000+ hits.  That pretty much explains it.

---

### Post by hogwartsnigel on 2008-07-26
Guys, I have had the same support advice from Asus with regard a minor issue on their P5K pro board...."we suggest you install vista or XP" Bah

Nigel

---

### Post by Canis familiaris on 2008-07-26
> **billgoldberg said:**
> I doubt very much they make 80% of all the motherboard.

You're right to speak out, I just find the number of thanks to be ridiculous.

Why not. A single person with the help of a community brings a company to its knees.
He deserves the thanks.

---

### Post by Canis familiaris on 2008-07-26
> **hogwartsnigel said:**
> Guys, I have had the same support advice from Asus with regard a minor issue on their P5K pro board...."we suggest you install vista or XP" Bah

Nigel
It is not exactly fault of the companies what their employees at call centers suggest,
I find the responders at call centers of almost all companies to be unfriendly and useless.
When they cant argue they just slam the phone.

---

### Post by Schotty on 2008-07-26
> **Midwest-Linux said:**
> I posted a link of this thread to The Linux Link Net, the forum for the The Linux Link Tech Show.

[http://thelinuxlink.net/forum/viewforum.php?f=2](http://thelinuxlink.net/forum/viewforum.php?f=2)

This is one of the better podcasts out there, much less for Linux topics.  Thanks for the plug; Dann, Link, Alan, and Pat appreciate it I am sure.

BTW, are you heading over to Ohio Linuxfest?  If so, I'll see you there and suck down a few beers with ya :D

Later!

---

### Post by Yellow Pasque on 2008-07-26
> You are incorrect in that the motherboard is not ACPI complaint. If it were not, then it would not have received Microsoft Certification for WHQL.

This is the best part. LOL.

---

### Post by Schotty on 2008-07-26
> **Lantesh said:**
> I recently put together a new system, and I did consider a Foxconn board.  Ultimately I went with an Asus board, because I've been using them for years, and they've always treated me well.  I am now seeing just how wise a move that was.  I can only imagine how terribly angry I'd have been had I wasted my money on a Foxconn board.  Thanks for the heads up.  I will certainly avoid their products in the future.

Actually I run a computer business on the side and FoxConn is not a bad choice for boards.  I have at least a dozen systems out there with linux still on it without issue.

I think this is an isolated case with a small number of models.  Please realize that I have had hell with about every vendor out there.  But generally it had to do with laptops, rather than desktops.

Personally, I only want to use boards that adhere to standards. This makes it easier to support via the chosen OS the customer wants.  Intel has been very friendly over the last few years, but again, that is essentially FoxConn.

I am speculating here, but I do think that the big boys (Sun, IBM, Dell, HP, etc) get the source for the BIOS so they can tweak it or have a dev kit, because I have seen vastly different BIOSes coming from what seems to be the same boards when you get down to it, just a different vendor.

Perhaps the chap from FC-UK can chime in here on that one.  Because in that case, we can sit with some reassurance that the vendors that have been very Linux friendly lately (Dell, Intel, HP, ASUS) have more control than some here believe.

Thanks!
Later!

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **Temüjin said:**
> This is the best part. LOL.


It's INDUSTRY compliant, cause Microsoft said it works with Vista, and maybe XP too!

That was the part where I said "Oh snap" and went right to work making "idle treats", I wonder if Foxconn would like some chocolate chips in their idle treats. :lolflag:

---

### Post by mech7 on 2008-07-26
:confused:why the hell would they do that

---

### Post by TheAlmightyCthulhu on 2008-07-26
[http://izanbardprince.wordpress.com/2008/07/26/my-reply-to-criticism-from-some-people-in-regards-to-the-foxconn-issue/](http://izanbardprince.wordpress.com/2008/07/26/my-reply-to-criticism-from-some-people-in-regards-to-the-foxconn-issue/)

Before you read this: I have been in contact with Foxconn and they’ve told me they are rewriting several sections of their BIOS code to be friendly to Linux, when this is the case, I will make a post stating what they have done, what it has fixed, and what, if any, problems are left.

This post is mainly to deal with people accusing me of how I approached Foxconn in the first place.

———————————

I’ve been going down the comments of several blogs and news sites that link to my post on Ubuntu Forums regarding Foxconn’s (I believe) willfull and intentional sabotage of Linux:

We’ll start with me contacting the company after experiencing a problem with every Linux kernel and distribution I have tried, some may say that I should have approached them better, I would say I’ve been more than generous, my initial contact with them was around the 18th I believe, or over a week ago.

After several rounds of e-mail exchanges, with an incompetent technician that the company later admitted didn’t know Linux from next Tuesday, who thought that my problem was relating to some kind of BIOS error that was preventing my computer from starting, even though I gave him a list of the loggings from /var/log/messages detailing the kernel errors and the invalid checksum of the DSDT table their BIOS passes to Linux.

I might add that their support ticket system lists many different varieties of LINUX, and I noted that I was using Linux, their support system lets you create Linux incidents, why am I to think that they don’t support Linux? Sure they have **** plastered up everywhere that says “Certified for Vista”, what hardware maker doesn’t?

And they shouldn’t have to support any particular OS, the BIOS’s job is to bootstrap the PC, hand the OS various information that is supposed to be operating system agnostic, then kindly buggar off.

So why am I angry with Foxconn?

As I have stated repeatedly, I do not feel that there is any way that this was not intentional, they went to great lengths to sniff for Linux, and hand it it’s very own DSDT table, which was not only inappropriate for the hardware on the board, but also failed a checksum test, had multiple compiler warnings, and so on.

Passing it the DSDT table Vista gets is far from perfect solution, but still works better, so why did they write a table for Linux, write it poorly, and then break it intentionally in several spots, the compiler toolkit by Microsoft or Intel even gives you tools to alert you if the compiled BIOS failed a checksum test, it’s not something you’re going to overlook.

*IF* Linux got the Vista/XP table and broke, I would assume Foxconn was just another stupid motherboard maker over in the Windows world masturbating itself instead of following the ACPI specification.

But it is quite obvious to me that Foxconn went very much out of it’s way to give Linux multiple problems, and generally make Linux look like a total pile of crap, there is no other explanation.

Occam’s Razor states that the simplest answer is often the correct one.

Would the “broken BIOS from stupidity/negligence” answer pass this test given what I have stated?

Absolutely not!

How about:

Item 1. Foxconn makes a lot of motherboards, with good hardware specs (sans BIOS), and sells them pretty cheaply, this comprises the bulk of the PC market.

Item 2. Linux is a free operating system, you can download it and use it without paying for anything but the CD to burn it to.

Therefore Foxconn boards and Linux seem to be a very good combination, economically speaking, based on advertised specs of Foxconn’s board.

So:

User (like me): Purchases Foxconn board to use with Linux, most users don’t know what the BIOS is I’ll bet, in the past Linux was a lot more difficult to figure out, now Ubuntu and other distributions are easy as pie.

Microsoft takes notice, and has already had a history of trying to subvert Linux, and Bill Gates said in a set of e-mails with other Microsoft guys that they’d love to make the ACPI spec break with any other OS besides Windows.

So Microsoft comes over and dumps truckload of money/kickbacks/incentives/crate of Cuban cigars signed by Fidel freaking Castro on Foxconn.

Foxconn then breaks their BIOS so that Windows will load and work fine, but Linux is ******.

New users, likely booting up Ubuntu will see how “unstable” it is, just assume that Linux is crap, and run back to Windows over this problem that Microsoft and Foxconn have in fact, concocted.

I’m not so angry with their non support of Linux, as them (1) Going out of their way to break it, (2) Selling their motherboard as ACPI compliant when it is NOT, (3) Having Linux support tickets just to tell the user that has ALREADY GONE THROUGH THE TROUBLE of having the damned thing paid for, shipped, and put into his/her computer to “go get Vista”, or “Ship the thing back”

DAMN IT! I will _NOT_ just “ship it back” or “buy Vista”

Foxconn lied about the ACPI specification support (it relies on Windows error handling because it’s not ACPI compliant), they go out of their way to break Linux, they admit that they have people writing their BIOS code that are basically intern-level and don’t really know what they’re doing, and they have also admitted to leaving debugging code in the final product that doesn’t actually do anything, except sit there and maybe cause even more errors because they forget to remove a reference to it here or there.

I will _ALSO_ not shut up until it is fixed, because I think many other Linux users might buy this product and face similar problems.

It also became obvious that I was getting nowhere with their representatives, and that I may have to resort to other methods, to bring this to their superior’s attention.

Their behavior towards me, as a customer, as a customer having difficulties with features that they proudly proclaimed “industry” level compliance with, that Linux would have no trouble with if they really were implemented to spec, is totally unacceptable, and I defend my attitude towards Foxconn on that.

Who knows? Maybe even Windows users will get a better BIOS out of this?

---

### Post by Captain Goatse on 2008-07-26
> **TheAlmightyCthulhu said:**
> It responds to OSI requests as every version of Windows there is (bites his hand).

It responds to their MCTH OS request as Linux, therefore the BIOS figures out Linux is Linux no matter what a properly formatted request would have given it.

As far as I can tell, _OS is equal to "Microsoft Windows NT" in Linux.  Unless ACPI specifies a way for the BIOS to change this, _OS will remain as "Microsoft Windows NT."

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **Captain Goatse said:**
> As far as I can tell, _OS is equal to "Microsoft Windows NT" in Linux.  Unless ACPI specifies a way for the BIOS to change this, _OS will remain as "Microsoft Windows NT."

That would be even worse.

It hands Linux 0x03

It hands Windows NT 0x02

---

### Post by Hasefroch on 2008-07-26
> **TheAlmightyCthulhu said:**
> 
New users, likely booting up Ubuntu will see how “unstable” it is, just assume that Linux is crap, and run back to Windows over this problem that Microsoft and Foxconn have in fact, concocted.


Couldn't be more agree with this.

:popcorn:


Nvidia, ATI, Creative, Foxconn :lolflag: do they think we are idiots?

thanks man for reporting this "BUG"

---

### Post by newbie2 on 2008-07-26
tracyanne wrote :
> Don't buy anything from FoxConn. But brings up another point, I set up a Lenovo laptop for a lady, but there is obviously a BIOS issue. One of two things happen, either it ignores the CD/DVD hardware or It won't suspend resume.

The two are mutually exculsive. I can enable ACPI, and I get suspend resume, but the OS in unable to see the CD/DVD harware, it's as if it doesn't exist. Or I can turn ACPI off, I get no suspend resume, and in fact I get no auto poweroff either, but the OS can see the CD /DVD hardware, and it mounts a CD or DVD fine. This has got to Faulty BIOS. The question this article raises for me is "is this deliberate?"
[http://lxer.com/module/forums/t/27579/](http://lxer.com/module/forums/t/27579/)
:rolleyes:

---

### Post by nitePhyyre on 2008-07-26
BBB gives Foxconn an F:

"We strongly question the company’s reliability for reasons such as that they have failed to respond to complaints, their advertising is grossly misleading, they are not in compliance with the law’s licensing or registration requirements, their complaints contain especially serious allegations, or the company’s industry is known for its fraudulent business practices. "
i think i want a foxconn board now... class action anyone? ;)


"I can not see how this kind of behaviour does not violate anti-trust's"

did anyone read that link that talked about the ms specs? can any one make a connection? can any ms developers in here comment? ;)


"So if it is a mistake, or incompetence, then it's the most meticulous, targeted, and dare I say, anal retentive incompetence I've seen."
that makes it sound like an accident.. truth is stranger...


"How far fetched is it to you that MS is paying them to do this?"
stop guessing and asking rhetorical questions, and go find out.

Now I hate to hijack this tread, but:

My laptop has problems also.  As soon as GRUB starts Ubuntu, there is a message saying somthing like: "Pc bios error #81[bunch of numbers]."  It does some funky things during the hibernate cylce, suspend doesnt work, and the battery only lasts about 1/2 hour. Is there a way to fix this?

sort of makes me wonder how many other computers have a bad bios?

---

### Post by Hasefroch on 2008-07-26
> **nitePhyyre said:**
> Now I hate to hijack this tread, but:

My laptop has problems also.  As soon as GRUB starts Ubuntu, there is a message saying somthing like: "Pc bios error #81[bunch of numbers]."  It does some funky things during the hibernate cylce, suspend doesnt work, and the battery only lasts about 1/2 hour. Is there a way to fix this?



Installing Window$ Vi$ta is the solution i guess.

---

### Post by themacmeister on 2008-07-26
I am sure that Dell have done the same thing with some of their Optiplex computers. My computer has NEVER worked with ACPI suspend/hibernate from any distro I have installed, and I have installed quite a few recently.

"hold them to their box-specs"

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **damis648 said:**
> Unfortunately there are no such if statements in my DSDT table source. If anyone would like to have a look at it and see if you can make any sense of it, please feel free. It is attached below. Please note my BIOS ARE NOT up-to-date. I am using A07, not the new A08. The A08 causes my trackpad to malfunction. When I apply a fix, it becomes unconfigurable. I am sticking with A07 right not because it works.

I PM'd you, suddenly I don't feel so bad anymore.

I've fixed your BIOS, it had 8 warnings, and one error (causing it to not compile at all) caused by a typo, I left the warnings alone for now, I really don't like messing with variables any more than I have to, I'll email you the compiled result.

Here's what I did:

Remove all reference to Windows 98, NT, Me

Define _OS response "Linux" as "Windows 2006" (Vista!), point it to Store 20

Define _OSI response "Windows 2006" as synonymous with Linux, point it to Store 20

Create new _OSI response "Linux", and give it Store 20

Replaced: Name (_HID, "*pnp0c14") with Name (_HID, "pnp0c14")

In otherwords, like it or not, it's booting Linux.

Before removing typo that MS compiler ignores:

"Compilation complete. 1 Errors, 8 Warnings, 0 Remarks, 576 Optimizations"

(It says complete, but it won't compile if there are errors)

After:

"Compilation complete. 0 Errors, 8 Warnings, 0 Remarks, 576 Optimizations"

God I love Microsoft's compiler, leaving all those errors, warnings, and not optimizing ANYTHING. B-)

If anyone is interested, this is some kind of Dell BIOS I believe?

If you need me to fix your DSDT, dump it and PM me with your email address, we will do things THERE.

I _DO NOT_ want you to attach any source code or intellectual property of anyone's to this thread, but I will help you as a courtesy, just not here!

---

### Post by Vadi on 2008-07-26
The fact is that Foxconn isn't the only company that does this, as pointed out by some others and mj59 in this post: [http://mjg59.livejournal.com/85923.html](http://mjg59.livejournal.com/85923.html)

Except he failed to get as much attention. 

His message? "Message to vendors: If we're not behaving in the same way as Windows does, let us know. We'll fix it. This has the benefit of fixing not only your latest and greatest platform, but also all the older ones that expected the same behaviour. Please don't try to work around our bugs in your BIOS - it just means that we need to special case you forever, and in the long run your hardware won't work as well as it would if we just fixed things properly."

---

### Post by vineh on 2008-07-26
i find it quite surprising that there are administrators on these forums, a Linux forum, which is inherently reasonably technical, who presumably lack the technical understanding to comprehend what is being said here by our freind cthulu.

just to paraphrase, the bios is not just *defective* for linux.

you see in this instance linux actually impersonates windows for compatibility purposes.

so the bios wouldnt realy even NEED to have ANY reference to linux  in it. 

the fact that they have specifically put code that LOOKS FOR linux, and then sends an alternate response to a linux OS, to say it is not intentional, or that it could be a bug,  well lets just say the term *heads in the sand* comes to mind. perhaps sand from the *lalala i cant hear you* dept... =P

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **Vadi said:**
> The fact is that Foxconn isn't the only company that does this, as pointed out by some others and mj59 in this post: [http://mjg59.livejournal.com/85923.html](http://mjg59.livejournal.com/85923.html)

Except he failed to get as much attention. 

His message? "Message to vendors: If we're not behaving in the same way as Windows does, let us know. We'll fix it. This has the benefit of fixing not only your latest and greatest platform, but also all the older ones that expected the same behaviour. Please don't try to work around our bugs in your BIOS - it just means that we need to special case you forever, and in the long run your hardware won't work as well as it would if we just fixed things properly."

In his position, he has to be professional, in my position, as a customer, I have a right to go in, bang my fist on the desk, and ask "Why the hell is this not working?"

I've been in contact with Foxconn and this has lit a fire under their ***, and I believe they are now committed to helping.

They have sent me a DSDT table that I intend to try out in a few minutes, cross your fingers.

Edit: STill doesn't work right, it fixes some of the more obvious errors though, I will apply my modifications to theirs and see if it helps.

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **vineh said:**
> i find it quite surprising that there are administrators on these forums, a Linux forum, which is inherently reasonably technical, who presumably lack the technical understanding to comprehend what is being said here by our freind cthulu.

just to paraphrase, the bios is not just *defective* for linux.

you see in this instance linux actually impersonates windows for compatibility purposes.

so the bios wouldnt realy even NEED to have ANY reference to linux  in it. 

the fact that they have specifically put code that LOOKS FOR linux, and then sends an alternate response to a linux OS, to say it is not intentional, or that it could be a bug,  well lets just say the term *heads in the sand* comes to mind. perhaps sand from the *lalala i cant hear you* dept... =P

Occom's Razor Time:

Theory: They were negligent wankers that didn't care and/or just a bug

Theory assumes many unlikely circumstances.

1. Foxconn accidentally put an entire DSDT table and a reference to it just for Linux, but thats a bug, they just didn't notice it before the BIOS shipped, oops.

2. Foxconn broke this table so that not even Windows could use it, much less anything else, but this is just a bug, they overlooked it before it shipped.

3. Foxconn claims not to support Linux, but has an entire table just for it, that is obviously broken and doesn't even pass a checksum test, but this is a bug you see, they didn't notice it.

4. Foxconn makes no mention of Linux on their site, but lets you create support tickets for it, to which they reply "Get Vista" or "Ship it back", this is a bug you see, the invisible man put FEDORA and GENTOO, and others in their support database.

5. (This is a joke, I have no proof this part happened) A large sum of money gets wired from Redmond to Shenzen, China, this was undoubtedly the work of Chinese h4x0r5 making Microsoft look bad, bad h4x0r5!

6. Being called out, publicly, Foxconn craps themselves and starts fixing the BIOS that they "accidentally" shipped with a "bug", being an entirely broken BIOS that won't even boot anything unless extreme hacks are used, especially for Linux.

Just a bug, my rear end, this was indeed deliberate, I have enough proof to satisfy any reasonable person.

**As long as Foxconn fixes it, and does not introduce any more intentionally faulty products, I will be happy and go away.**

---

### Post by TheAlmightyCthulhu on 2008-07-26
Carl,

I used the website, and I did not appreciate any of that at all, actually I was quite horrified that a motherboard manufacturer as large as Foxconn is has just totally torpedoed Linux and then blows off customers that are angry about it.

I will be more than happy, and in fact I am looking forward to writing a thorough and detailed review of your repaired BIOS, if it works reasonably well with operating systems that are not Windows, I will give it a glowing review, everywhere I have been thus far.

Furthermore, I think it shows a complete lack of professionalism, to treat millions of users, and potential customers (who may or may not be now) in this way, I know that if this issue is not resolved, I will not be the only one going to great lengths to avoid purchasing your company's products, Phoronix, Slashdot, and Digg, are probably the three places you guys really don't want to be, because people that buy products such as yours (including your line of Nvidia video cards, very popular with Linux users) read things like this and associate that with your brand.

So just telling 8% of the market, who does not use Windows to go kindly screw themselves is probably not the best thing you guys can do.

Now, I know you guys probably realize everything I've just said, I was throwing it ou there to make an example and for you to actually think about that when your boss is asking you why in the hell this justifies an expenditure, I centainly don't mean to be disrespectful, rude, or hostile, had I received any help without taking it to this level, I would have gone about my business.

As for ACPI, lots of luck with that, even just looking at the assembler, bluntly, makes me want to vomit, you should really be standardizing on the Intel reference specification and using Intel compiler tools, it would save you from having to fish for several versions of Windows, singling out Linux as an OS that supports ACPI features circa 10 years old (and broken), and totally ignoring everything else.

If you insist on basing it on this weird fishing behavior, I would suggest removing all references to Linux and removing the table it uses, removing all references to Windows NT and Me (This board wouldn't even boot them, it's kludge), and keeping the _OSI and tables for Windows Vista and XP, Linux will respond to an _OSI telling the BIOS it is Windows, so doing what I have said should cut the amount of crap code in the BIOS by half, or more.

Then, you can concentrate your efforts on fixing the crashing on reboot after having suspended, which seems either in the DSDT table, elsewhere in the BIOS, god only knows where, chances are this is a bug in any ACPI compliant OS, but XP and Vista simply ignore it, it's most likely a few lines of code somewhere that just needs tweaking, but for the love of God please get rid of all the legacy crap, it hurts my brain just looking at it.

When you post the fixed BIOS, please assemble the whole thing with Intel's tools, they work surprisingly well on pretty much any modern OS, even the piece of crap, Vista.

I know, it seems like a lot of work, it will pay off, you won't have to hack on bad, outdated code to support version X of operating system Y in the future, your code now is spaghetti code, scratch that.......Chef Boyardee Spaghetti code.

Anyhow, I appreciate Foxconn's new found willingness to help, I really really do. (I mean that!)

-Ryan

[B]On Sat, Jul 26, 2008 at 6:57 AM, Carl Brunning <carl.brunning AT foxconn.com> wrote:

Hi Ryan
     
Thank you for all the information so far...

When you reported to foxconn did you email or use the website, sorry working out who give the bad answer to you and stop stuff like this from happening again.
     
On Monday, I will be sending a email to the bios team about this and having it fixed as well.
     
Time for me to read the acpi spec again last time I looked was over 4 years ago :-(
    
Ouch going to be fun again lol
     
    
Anyway thanks again,
     
     
    Kind Regards
    Carl Brunning

    Technical Manager for UK and Ireland 
    Foxconn CSDEU B.V (UK)
    Tel +44 1908 276610
    Tel +44 1908 276621(Direct)
    Mobile 07870 622 398
    VOIP : 528 2611  when it works

    WEB [http://www.foxconnchannel.com](http://www.foxconnchannel.com)[/B]

---

### Post by silkstone on 2008-07-26
The BIOS coding is beyond me, but I understand the gist of this thread. I hope it now gets fixed and that what you've done here may deter people from making such 'mistakes' in future.

As a general comment, headlines such as 'XYZ tries to kill Linux' may be true, but may also leave 99% of people unimpressed as it doesn't apply to them. If I'm right in thinking that true acpi compliance will allow Linux to run, whether or not the board is officially 'approved for Linux', then perhaps the lack of compliance with acpi standards should be the main headline. Just a thought. ;)

---

### Post by phill0 on 2008-07-26
For those of you who are skeptic about Microsoft's involvement, I would like to post an email from Bill Gates to his staff:

> 
From: Bill Gates
Sent: Sunday, January 24, 1999 8:41 AM
To: Jeff Westerinen; Ben Fathi
CC: Carl Stork (Exchange); Nathan Myhrvold; Eric Rudder
Subject: ACPI extensions

One thing I find myself wondering about is whether we shouldn’t try and make the "ACPI" extensions somehow Windows specific.

It seems unfortunate if we do this work and get our partners to do the work and the result is that Linux works great without having to do the work.

Maybe there is no way to avoid this problem but it does bother me.

Maybe we could define the APIs so that they work well with NT and not the others even if they are open.

Or maybe we could patent something related to this.


Source: [http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf)
(The pdf was OCRed so I'm not certain that the names in "To" and "CC" headers are right.)

So judge for yourself. At the very least you have to agree that considering strong cooperation between Foxconn and Microsoft this looks fishy.

---

### Post by autocrosser on 2008-07-26
My note to FoxxConn website support:


I have considered FoxConn motherboards for myself & my customers in the past. I will consider them IF you will straighten up your Linux support. I would not be your largest customer (building only 8/10 computers per year), but I promise to not recommend FoxConn motherboards to my customers until I get a positive result from the Linux community.

Your management should look at this posting: [http://ubuntuforums.org/showthread.php?t=869249](http://ubuntuforums.org/showthread.php?t=869249)   

One unhappy linux customer will snowball into the community becoming very vocal & I might add that Ubuntu Linux has currently over 10 million users--with a fair amount for us being very tech-savy.

I don't expect a response from this, but if I do---I would like feedback from higher management.

Dean Loros
Performance by Design Ltd.

---

### Post by aczid on 2008-07-26
Registered here just to say you are my hero, and give you thanks.
Great job!

---

### Post by Perpetual on 2008-07-26
Maybe I am missing something but I can not find where Foxconn ever states that the board is certified for Linux.

---

### Post by zekica on 2008-07-26
For a hundredth time, they state ACPI compliance on their site, but one of their DSDT tables even has a wrong checksum (a table that is passed only to Linux).

---

### Post by phill0 on 2008-07-26
> **Perpetual said:**
> Maybe I am missing something but I can not find where Foxconn ever states that the board is certified for Linux.

It doesn't have to be certified for Linux. There are standards, and if the manufacturer says that the board complies with them then software that supports the standard will run correctly. Standard is an interface in this case, connecting two systems software and hardware. If we would need certification for every software hardware combination then we would be just creating many separate lines of standards, and therefore defy the idea of standardization.

---

### Post by TheAlmightyCthulhu on 2008-07-26
> Real standards, wrote Schilling, are for physical objects like steel beams: they let designers order a part and incorporate it into their design with foreknowledge of how it will perform under real-world conditions. 

“If a beam fails in service, then the builder’s lawyers call the beam maker’s lawyers to discuss things like compensatory and punitive damages.” 

Apparently, the threat of liability keeps most companies honest; those who aren’t honest presumably get shut down soon enough. This notion of standards breaks down when applied to software systems.

There is so much wiggle room in these standards as to make the idea that a company might have liability for not following them ludicrous to ponder. Indeed, everybody follows these self-designed standards, yet none of the products are compatible.

-UNIX Hater's Handbook, 1994

---

### Post by Perpetual on 2008-07-26
> **zekica said:**
> For a hundredth time, they state ACPI compliance on their site, but one of their DSDT tables even has a wrong checksum (a table that is passed only to Linux).

Hmm, ok.  I stand corrected.

---

### Post by rberger123 on 2008-07-26
Also wanna say thanks for your very informative posting. Owning an MSI P965 Platinum, I wasn't even aware yet that MSI is basically Foxconn. Still indeed, I found the very issues you described when disassembling my DSDT. Also, I have that very reboot after suspend problem you mention, and your changes don't fix that here as well, as you say.

One additional favor I'd like to ask though: in case you find out further stuff, and I'm especially thinking of the reboot problem, could you please keep us posted on your first article on the front page? It would make it much easier to stay up to date with your findings.

Again, thanks a lot,
Raimund

---

### Post by TheAlmightyCthulhu on 2008-07-26
> **rberger123 said:**
> Also wanna say thanks for your very informative posting. Owning an MSI P965 Platinum, I wasn't even aware yet that MSI is basically Foxconn. Still indeed, I found the very issues you described when disassembling my DSDT. Also, I have that very reboot after suspend problem you mention, and your changes don't fix that here as well, as you say.

One additional favor I'd like to ask though: in case you find out further stuff, and I'm especially thinking of the reboot problem, could you please keep us posted on your first article on the front page? It would make it much easier to stay up to date with your findings.

Again, thanks a lot,
Raimund

Yes, I'll keep you posted.

---

### Post by OmegaBLK on 2008-07-26
Just wanted to give support to you **TheAlmightyCthulhu**.  Great job bringing the spotlight on to this issue.  Even though it appears Foxconn is attemtping to fix it we all need to keep up the pressure on not just them, but all companies that break or do not adhere to open standards properly and push these inferior wares out onto the public. These type of problems are not acceptable whether it is due to malicious intentions or pure laziness.  Thanks to you **TheAlmightyCthulhu**, your work is appreaciated.

---

### Post by autocrosser on 2008-07-26
I just pulled the dsdt.dat from my Gigabyte P35 (rev2) motherboard. To my eye, it looks like a well set-up one. I'm posting the results here for others to read--no exceptions for Linux--looks like clean, professional code. 

Edit--looks like it uses a default set for Linux--**TheAlmightyCthulhu**, you might take a look to see if it can help you & of course--comment on any problems you see.......

Further info--the only reference I find to the "sniffing" area in the P35 dsdt file is here:  [http://www.ussg.iu.edu/hypermail/linux/kernel/0612.0/0389.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0612.0/0389.html)

And the P35 file conforms to the info there.....comments?

---

### Post by brokenLockpick on 2008-07-26
I just checked the OP suggested luckily I saw no explicit reference to Linux in mine. Perhaps this only effects certain models, my particular board is a Foxconn-Winfast 6150K8MA-8EKRS.

---

### Post by cbrunning on 2008-07-26
Just to say to a lot of people
Foxconn may make a lot of other people stuff but we do not make there bios

and yes we have a few bios teams so some will make the bios correctly and some of the other teams are new people who are still learning how to make bios 

so bugs like this can happen
so please do not assume all boards have the same bugs

i've been using and doing linux for now 10 years, so when i find a bug in are boards i get them fixed, just not tested teh G33m with linux my self so i missed this board

thanks 

to every one foxconn may be the largest Manufacture but on the motherboard makking under are own name is not that old, compary to the other we still learning and making  mistake that others  likes asus and gigabyte have learned and dont make
but we are getting there :) 

we will get this fixed and am sure we will ensure not to have this type of bug again 

thanks

---

### Post by MadOp on 2008-07-26
I  just joined the forum to be able to thank TheAlmightyCthulhu for putting this in the spotlight and for going to such efforts to do it. Commendable indeed!

I've also found cbrunning posts and if the company is able to reckon a mistake and fix it quickly, I'm sure that would be appreciated by the whole FLOSS community.

I think it's about time the copmanies realize that FLOSS users, while might not be too many in numbers, are very vocal and more importantly, are too many times the ones others seek to for recommendation and advice, end users and companies as well. 

Hope something positive comes aout from this.
Cheers!

---

### Post by aktiwers on 2008-07-26
So fare I actually think that Foxconn has handled this situation very well. Looking past the bad support yesterday, it seams like they are ready to get this fixed asap and are spending the necessary resources to do so.  I'm really looking forward to see how well there updated BIOS works.

Maybe they learned from Creatives mistakes? 

Please keep us updated (in post #1) how the testing is going. And thanks for your effort ! :)

---

### Post by jb1 on 2008-07-26
"Never attribute to malice that which is adequately explained by stupidity."

A whole thread full of angsty neckbeards blaming Foxconn for sabotage without an evidence at all.  Wow.

---

### Post by t2000kw on 2008-07-26
I don't believe anything deliberate happened, but someone at the company forgot what the word prototyping means. It requires thorough testing before running something down the production line. Doing it right first time costs less than fixing things later. Successful manufactures always thoroughly test prototypes and don't rush to market with one that isn't fully tested for all likely scenarios to be encountered.

If one of the previous posts is correct, it looks like there will be a flash update for this fix. I'm not sure how you would apply it without a booting OS, but I would guess could go to a friend's place, download the fix, and put it on a floppy or flash drive. 

I went to the manufacturer's web site yesterday and left my thoughts with them, mentioning that it was a poor business decision on the part of the support person who basically said "we don't care--we only support Windows operating systems" and that this would come back to haunt them very soon. 

If the above person is correct, this may be limited to one particular motherboard. 

Donald

---

### Post by snick525 on 2008-07-26
> **jb1 said:**
> "Never attribute to malice that which is adequately explained by stupidity."

A whole thread full of angsty neckbeards blaming Foxconn for sabotage without an evidence at all.  Wow.

Did you even read the OP?  There are, seemingly, blatantly shoddy DSDT tables for Linux OS's.

That seems like sabotage to me.

---

### Post by jb1 on 2008-07-26
> **snick525 said:**
> Did you even read the OP?  There are, seemingly, blatantly shoddy DSDT tables for Linux OS's.

That seems like sabotage to me.Do you even know anything about LInux ACPI, or do you just jump on nerdrage bandwagons?   [http://mjg59.livejournal.com/85923.html](http://mjg59.livejournal.com/85923.html)

Also, people should 1) not buy the absolute worst hardware on the market, 2) pay attention to which OSes are supported 3) not act like socially inept neckbeards when dealing with a company's support drones.  Seeing as Foxconn boards cost, at most $30-$50, I hardly feel this is worthy of an 11 page nerdrage thread and FTC complaints.

---

### Post by eduren on 2008-07-26
I have a system assembled by Compaq and have seen a few foxconn logos on my mobo, could this be affecting me? 

I dont understand what problems other people are getting but i have trouble with hibernating and other issues with graphics.

running hardy ubuntu

---

### Post by knutschr on 2008-07-26
> **jb1 said:**
> Do you even know anything about LInux ACPI, or do you just jump on nerdrage bandwagons?   [http://mjg59.livejournal.com/85923.html](http://mjg59.livejournal.com/85923.html)

Also, people should 1) not buy the absolute worst hardware on the market, 2) pay attention to which OSes are supported 3) not act like socially inept neckbeards when dealing with a company's support drones.  Seeing as Foxconn boards cost, at most $30-$50, I hardly feel this is worthy of an 11 page nerdrage thread and FTC complaints.

1) Foxconn produce good and cheap hardware. Else they would not be used by so many vendors.
2) Today we have standards. As usual, MS try to implement their own and push their non-standard APIs to others so that other OSes, following standards, won't work properly. There really should be no need of, when buying a machine, to ask for if the motherboard supports Linux, MAC  or other!
3)I think this sabotage is paid from MS.
It is very worthy to tell MS they can't continue to pay vendors for this sabotage, and to show vendors they will loose very much money doing this, as I think Foxconn has done already in the time to come unless they do something.
I think, like 70 mill. other Linux users, and 10th of millions users of old MS, that it will be very long time until I will buy a board from them.

---

### Post by KiwiNZ on 2008-07-26
Ok 
 
This thread has served it purpose . Its jusy going in circles now and people are snipping at each other.
 
I am closing for now and will re evaluate should things change.
 
 
For updates re this issue please see this thread 
 
[http://ubuntuforums.org/showthread.php?t=871311](http://ubuntuforums.org/showthread.php?t=871311)

---

