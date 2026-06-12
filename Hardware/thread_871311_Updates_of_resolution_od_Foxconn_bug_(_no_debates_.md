---
title: "Updates of resolution od Foxconn bug ( no debates please just updates)"
date: 2008-07-26
forum: Hardware
---

### Post by KiwiNZ on 2008-07-26
This relates to this thread 
 
[http://ubuntuforums.org/showthread.php?t=869249](http://ubuntuforums.org/showthread.php?t=869249)
 
This thread is to allow updates on progress to resolve this issue with Foxconn. 
 
The subject has been fully debated so we dont need further an the subject as to fault blame or intent.That will only serve to bury resolution.
 
Thank you in advance

---

### Post by jimv on 2008-07-26
This is kind of related.  Thanks to the OP of the Foxconn thread, my brightness keys now work.  I decompiled my DHDT and noticed that it referenced two tables based on OS: Vista and not-Vista.  So I deleted the reference for not-Vista, and replaced the words "Windows 2006" with "Linux", and then recompiled and installed the fixed DHDT.

Now my laptop is running Ubuntu 100% problem free!  Thanks to the person who posted about this originally.

---

### Post by TheAlmightyCthulhu on 2008-07-26
Foxconn has said they will post an official response on Monday, they sent me a DSDT table to patch the kernel with this morning, but it ended up giving me every error the original BIOS does, plus a message that the kernel can't find the "rio grande table" and is "bailing!".

It will be extremely interesting to see where this ends up, my idea is (without speculating as to the cause of the problem), that someone's boss(es) are aware of the situation that has brewed, and that they're being ridden to provide a BIOS that works well with Linux.

As for their reasoning, I don't care, I just want them to take accountability and fix it, they owe their customers an ACPI compliant board, as advertised, even if they don't go out of their way to advertise that it works with Linux.

**I want everyone to know that regardless what happens to this thread or my account since KiwiNZ is censoring it and pushing to have me banned, you can keep up with the situation at** <spam snipped>

**staff: No, you're in trouble for creating multiple accounts. There is no plan to delete this thread or the information about the faulty dsdt tables. Please make your case rather than spreading falsehoods. **

---

### Post by TheAlmightyCthulhu on 2008-07-26
Response to Matthew Garrett's assumption that the bad BIOS is "not a bug":

[http://izanbardprince.wordpress.com/2008/07/27/with-all-respect-to-matthew-garrett/](http://izanbardprince.wordpress.com/2008/07/27/with-all-respect-to-matthew-garrett/)

---

### Post by mjg59 on 2008-07-26
> **jimv said:**
> This is kind of related.  Thanks to the OP of the Foxconn thread, my brightness keys now work.  I decompiled my DHDT and noticed that it referenced two tables based on OS: Vista and not-Vista.  So I deleted the reference for not-Vista, and replaced the words "Windows 2006" with "Linux", and then recompiled and installed the fixed DHDT.

Now my laptop is running Ubuntu 100% problem free!  Thanks to the person who posted about this originally.

That's an entirely separate issue. Your system is designed to use the new Intel IGD OpRegion specification. This isn't supported in versions of Windows before Vista, so with your change to the DSDT it's falling back to the old-fashioned code. I've added support for this to Linux, which should be shipping in 2.6.27.

---

### Post by jimv on 2008-07-27
> **mjg59 said:**
> That's an entirely separate issue. Your system is designed to use the new Intel IGD OpRegion specification. This isn't supported in versions of Windows before Vista, so with your change to the DSDT it's falling back to the old-fashioned code. I've added support for this to Linux, which should be shipping in 2.6.27.

Ah, cool.  I still thank him because the brightness key issue had been bugging me since I first started using Ubuntu in Feisty, and I wouldn't have thought to check for different tables until his post.

---

### Post by jimv on 2008-07-27
> **TheAlmightyCthulhu said:**
> Response to Matthew Garrett's assumption that the bad BIOS is "not a bug":

[http://izanbardprince.wordpress.com/2008/07/27/with-all-respect-to-matthew-garrett/](http://izanbardprince.wordpress.com/2008/07/27/with-all-respect-to-matthew-garrett/)

Do you have the link to Matt's original post?

---

### Post by TheAlmightyCthulhu on 2008-07-27
> **jimv said:**
> Do you have the link to Matt's original post?

He went to Red Hat's Bugzilla and marked it "Closed: Not a bug", apparently this was a mistake on his part as he later comments in the page, I snapped on the concern that he was closing bugs without even a vague idea of what my BIOS was doing, or how Linux responded to it.

---

### Post by Runamok on 2008-07-27
Please be smart about the situation, and we can all garner the best result for the Linux community.  

Almighty. you already have the community's attention.  Be the bigger OS, and live up to it's heritage.  This will be resolved.  PLEASE, Please, please.... there is  no reason to sensationalize this. But be vigilant.  Whether intentional, or not.... For Foxconn's credit, on short notice, they have sent CBrunning to this thread to help us.  Give Foxconn some time, we all know that they are "trying" to fix the problem.  Their effort will reveal their intentions.

However, if the solution is half-hearted or unacceptable, then take more action.  I don't want this to be placated, but for now, have patience.  I think Foxconn recognizes that shoddy programming and support is unacceptable. The 150k+ views should tell them that. TheAlmightyCthulhu seems knowledgeable, and he is in the unique position of a mediator for this process.  Live up to your potential.  I for one, am deeply intrigued as to how a leading manufacturer will handle this situation, as it impacts the entire market.

And If CBrunning is not getting the upper level support he needs, perhaps he should ask his superiors if Foxconn is serious about upholding the marketing departments claim of Linux ACPI support.  If marketing is not, then Foxconn should realize that they are cutting themselves out of an emerging market.

Here's to hoping it gets resolved amicably. ):P

- Runamok

---

### Post by Dark Angel on 2008-07-27
What, might I ask, has been done to TheAlmightyCthulhu's avatar and user title?  This is a guy who has gone out of his way to help the community and it looks like he's being derided by someone with too much power on their hands.

Edit:  Just saw MY new user title.  Very cute, mate.  Very cute.

---

### Post by jimv on 2008-07-27
> **Runamok said:**
> TheAlmightyCthulhu seems knowledgeable


Well...he is a [Great Old One]("http://en.wikipedia.org/wiki/Cthulhu").

---

### Post by rberger123 on 2008-07-27
> **Runamok said:**
> Please be smart about the situation, and we can all garner the best result for the Linux community.

I was about to say the same. Even if things go a little over the top any attention and focus brought to these issues can just be beneficial, thanks to a kind of fortunate mingling of two separate topics, i.e. ACPI standard compliance and the claim of maybe intentionally breaking Linux. Regardless the latter, this obviously is a good time to seek and urge for advances on the former.

I'd expect especially Linux developers to be pleased, as they have been complaining often enough about the sad state of affairs, needing them to reimplement Windows behavior "bug for bug". If I were one, I'd think I could expect my voice of concern being heard sooner in the future.

---

### Post by thetango on 2008-07-27
[http://mjg59.livejournal.com/94905.html](http://mjg59.livejournal.com/94905.html)

and

[http://mjg59.livejournal.com/94998.html](http://mjg59.livejournal.com/94998.html)

Quote from mjg, a well known Linux kernel engineer currently at Red Hat:

"Are there ACPI issues with Ryan's system? It sounds like it. The "Error attaching device data" complaints indicate some kind of failure on the part of the kernel to work out how the devices correspond to the ACPI namespace, but I strongly suspect that this is a Linux bug. Failure to reboot after suspend? Could be anything (I'd need direct access to the hardware to figure it out properly), but again it's almost certainly a Linux bug. The standard way Linux reboots systems is to bang the keyboard controller, and it's conceivable that something we're doing on resume is leaving the keyboard controller in a slightly confused state. We're clearly doing something wrong there, given that my Dell comes up without a keyboard about one resume in twenty - I just haven't had time to look into it yet.

The only remaining thing is the mutex handwaving. I've got no clue what's going on there. Ryan's suggested change (from Acquire (MUTE, 0x03E8) to Acquire (MUTE, 0xFFFF)) simply means that the OS will wait forever until it acquires the mutex - in the past it would only wait a second. The reason the compiler generates a warning here is that the firmware never checks whether it acquired the mutex or not! Bumping the timeout to infinity obviously fixes this warning (there's no need to check the return code if you're happy to wait forever rather than failing), but the original code is merely stupid as opposed to a spec violation.

Take home messages? There's no evidence whatsoever that the BIOS is deliberately targeting Linux. There's also no obvious spec violations, but some further investigation would be required to determine for sure whether the runtime errors are due to a Linux bug or a firmware bug. Ryan's modifications should result in precisely no reasonable functional change to the firmware (if it's ever hitting the mutex timeout, something has already gone horribly wrong), and if they do then it's because Linux isn't working as it's intended to. I can't find any way in which the code Foxconn are shipping is worse than any other typical vendor. This entire controversy is entirely unjustified."

and 

"Accusing companies of conspiring against us when the most likely explanation is simply that they don't care is a ******* ridiculous thing to do and does nothing to get rid of the impression that Linux users are a bunch of whining childish hatemongers. Next time, try talking to someone who actually understands this stuff first?"

---

### Post by Dark Angel on 2008-07-27
Pretty impressive that the guy can diagnose a code fault without ever seeing a line of code.

---

### Post by rberger123 on 2008-07-27
> **thetango said:**
> when the most likely explanation

Sorry, I can't quite see how anything "most likely" is an actual update. Are you really sure you don't want to stir another debate here?

---

### Post by thetango on 2008-07-27
> **Dark Angel said:**
> Pretty impressive that the guy can diagnose a code fault without ever seeing a line of code.

:confused:

Uh ... the second link starts with "Ryan kindly sent me a copy of the ACPI tables for his motherboard, so I've had the opportunity to look at them in a little more detail. There's nothing especially surprising."

... and mjg is one the "bigwigs" of Linux ACPI.

// just sayin'

---

### Post by thetango on 2008-07-27
> **rberger123 said:**
> Sorry, I can't quite see how anything "most likely" is an actual update. Are you really sure you don't want to stir another debate here?

No, I really don't.  

I think what mjg is trying to say is that while Ryan's "fix" does something, it's not really a fix.

mjg is pointing out that Linux has a bug in it somewhere -- "most likely" in the ACPI code (but he can't be 100% sure without more detailed analysis of the code).  The "fix" that Ryan offers is using that broken code and the code is misbehaving to return a positive result.

ie) Linux is still broken.  And it just happens to work correctly but no one has identified precisely what is wrong yet.

OTOH what Ryan has does look like it works around the problem, and for that he deserves credit.

---

### Post by rberger123 on 2008-07-27
Right, thanks for the clarification, albeit much of this still being too speculative for my taste also on mjg's side. It's appreciated anyway.

While giving credit to Ryan, I'd too like to give him some for just not letting himself being brushed off by bad customer support, like many of us do just so often, but rather ringing a bell. I'm aware that this might have interfered with some people's weekend plans and am sorry for them. On the good side, it's hopefully one more step towards making vendors aware it could make sense to provide reasonable support, to all OSes users alike.

---

### Post by mjg59 on 2008-07-27
> **Dark Angel said:**
> Pretty impressive that the guy can diagnose a code fault without ever seeing a line of code.

The code in question appears in numerous other BIOSes as well, and the small chunk that Ryan posted was enough to let me know that the suggested changes would have no effect. Having the original tables let me verify that even if Linux were behaving incorrectly, the BIOS did nothing with the knowledge that the system was Linux.

---

### Post by kingtaurus on 2008-07-27
> **mjg59 said:**
> The code in question appears in numerous other BIOSes as well, and the small chunk that Ryan posted was enough to let me know that the suggested changes would have no effect. Having the original tables let me verify that even if Linux were behaving incorrectly, the BIOS did nothing with the knowledge that the system was Linux.

The exact code appears in my ASUS P5K-E BIOS (my guess is that this is standard code from AMI).

---

### Post by JPorter on 2008-07-27
If nothing else positive comes from this whole debacle, at least it has focused a large number of minds on one of the great Linux stumbling blocks... grossly inconsistent ACPI behavior from system to system.  If the end result is better, more consistent and ultimately more functional power behavior under Linux, *for everyone*, then the ol' Ryan will have done some good.

---

### Post by NeoTaoistTechnoPagan on 2008-07-27
> **JPorter said:**
> ...grossly inconsistent ACPI behavior from system to system...

Wasn't that one of his points in his initial post?

The fact that Foxconn said that there was nothing wrong with the board, he just wasn't using some *other* OS ...AND the FACT that one of the companies that 'standardizes' ACPI is Microsoft, *is it possible* that they have shown how far they are willing to go to make free software in all iterations seem unstable enough as to not be an option?

While this does seem to sound very conspiratorial a la X-Files-ish, there could be more to this, or it could be nothing.

Deus ex machina?

NTTP

---

### Post by Arvi Pingus on 2008-07-28
I reacted to Foxconn about their non-Linux friendly approach and see what I answer I got```
Dear Sir,
Thank you very much for your attention with Foxconn.
With regard to this issue posted on Ubuntu forum, we are trying to resolve it and we would like to state here that Foxconn will never reject Linux.
If you meet similar problems, please try to provide your detailed configuration, (including cpu, memory, hdd, Linux version and its kernel, etc.) and the symptom so that we could test in our bed and analyse to resolve this.
It is really a pleasure to be of service to you, Sir.
Thanks and best regards,
Foxconn Technical Support
```So there is still hope for a 'bug'fix?

Anxious to see how quick they will solve the issue (they even test in their bed? :))

---

### Post by patrickgood on 2008-07-28
In the past I farmed the gold by myself to level up . I think it is enjoyable. But now i am too busy to farm the gold. and now I am really wondering to get some gold from some site although I know maybe it is not a good thing.  you know one site[SIZE="4"]:KS[COLOR="Red"] a-g-a-m-e g-o-l-d c-o-m  or  w-w-w w-o-w. 4-s.n-e-t .[/COLOR][/SIZE] them always spam me in the game . sometimes I was really ticked off . did you ever try buying gold just for :popcorn:the spamers ? and they said I can contact them by email for phone or go ot their livesupports at any time . it is relilable? Safe?  :lolflag:
Thanks guys :guitar:

---

### Post by patrickgood on 2008-07-28
hey guys , :lolflag:
I  enjoy the game and relax myself after the working and studying . but I found that more and more people just level up their characters by buying gold or powerleveling . you know what , we made the two accounts at the same time , and he would :KSbe lvl 35 and mine is just 15 .  that is so unfair . so it is really not good thing  for me to play with him . why more and :)more people are willing to spend money on game . and why are they so crazy about [COLOR="DarkOrange"][SIZE="4"]a-g-a-m-e  g-o-l-d.  c-o-m  ;   w-w-w  w-o-w 4-s. c-o-m??? [/SIZE][/COLOR] it it so excellent for gameplayers?  :guitar:

---

### Post by Dark Angel on 2008-07-28
Bug fix or no, their customer support seems to have improved.

edit:  I noticed the change in my user title again.  Thank you.

---

### Post by Neckbeard on 2008-07-28
> **Dark Angel said:**
> Bug fix or no, their customer support seems to have improved.

edit:  I noticed the change in my user title again.  Thank you.

No kidding, I saw how they were behaving before, there is no excuse for this.

---

### Post by MountainX on 2008-07-28
I saw the TheAlmightyCthulh's update about Foxconn (below) and I decided to send a thanks to Foxconn. I wanted to share their reply here. See below.

(I'm not sure why the prior thread was closed. See [http://ubuntuforums.org/showthread.php?t=869249](http://ubuntuforums.org/showthread.php?t=869249))

> **TheAlmightyCthulhu said:**
> 
Update: I just got off the phone with Foxconn, they called me from China (1 AM in Indiana, heh) and were asking if I would test an improved version of their BIOS based partially on the modifications I've made to mine, hopefully this all blows over, and regardless of who's fault it is or isn't, we can just go back to using our computers with full functionality.

Thanks to the community for helping me get the message to Foxconn.

Edit: Please tell Foxconn what you think of their behavior:

[http://www.foxconnchannel.com/support/online.aspx](http://www.foxconnchannel.com/support/online.aspx)

[B][U]
I said:[/U][/B]
"Thank you for working on the Linux support in your BIOS. I have been following the discussion at [http://ubuntuforums.org/showthread.php?t=869249](http://ubuntuforums.org/showthread.php?t=869249). I am very glad to hear that you will work to resolve this. Thank you!"

**_Foxconn replied:_**
Dear Sir,
Thank you very much for your attention with Foxconn.
With regard to this issue posted on Ubuntu forum, we are trying to resolve it and we would like to state here that Foxconn will never reject Linux.
If you meet similar problems, please try to provide your detailed configuration, (including cpu, memory, hdd, Linux version and its kernel, etc.) and the symptom so that we could test in our bed and analyse to resolve this.
It is really a pleasure to be of service to you, Sir.
Thanks and best regards,
Foxconn Technical Support

---

### Post by MountainX on 2008-07-28
I just found this thread.

Here is my post about Foxconn's reply to me on this issue:

[http://ubuntuforums.org/showthread.php?p=5474291#post5474291](http://ubuntuforums.org/showthread.php?p=5474291#post5474291)

---

### Post by linuser on 2008-07-28
Hello I have an asrock (asrock dual sata II) with this table dstd  acpi for bios AMIBIOS

> 
 Name (OSVR, Ones)
    Method (OSFL, 0, NotSerialized)
    {
        If (LNotEqual (OSVR, Ones))
        {
            Return (OSVR)
        }

        If (LEqual (PICM, 0x00))
        {
            Store (0xAC, DBG8)
        }

        Store (0x01, OSVR)
        If (CondRefOf (\_OSI, Local1))
        {
            If (\_OSI ("Windows 2001"))
            {
                Store (0x00, OSVR)
            }
        }
        Else
        {
            If (MCTH (\_OS, "Microsoft Windows NT"))
            {
                Store (0x04, OSVR)
            }
            Else
            {
                If (MCTH (\_OS, "Microsoft WindowsME: Millennium Edition"))
                {
                    Store (0x02, OSVR)
                }

                If (MCTH (\_OS, "Linux"))
                {
                    Store (0x03, OSVR)
                }
            }
        }

        Return (OSVR)
    }







I have the same problem that the foxconn?

 the suspended way and the hibernation does not work

---

### Post by knutschr on 2008-07-28
I admit I am in very deep water now, but I still have some, may be very silly questions, I have been thinking about today:

Is there a such ting as "Linux" when it comes to how a BIOS should respond?
Different Linux kernels have support for different things, like Windows kernels have.
So, Windows is divided into different flavors (2000, XP, Vista aso) in BIOS responds.
"Linux" will have different kernels being able to do things corresponding to different flavours of Windows.
There would have been much extra work to ask for what kernel is used.
Therefor Linux kernels present themselves as the Windows version having the same implements.

I think that when BIOS asks specifically if it is Linux, BIOS is set to correspond with very old kernels, and that the problem would have been omitted if the BIOS never asked.

Please correct me if I am wrong.

---

### Post by Daelyn on 2008-07-28
I must say I was delighted when I saw the first thread about this last week. That the Linux community finally found something out we've all been waiting for. But, then the joy faded quickly when realizing 90% the hardware I support and maintain contain Foxconn mobo's and thereby could be affected.


I've now, today, read through every link within every link to find out as much as possible, and am now not so sure about it anymore.

*So, please, everyone who decides to continue their "hate" or "blame" towards Foxconn, read everything through (from both parties) before deciding where you stand. *

According to Matthew over @ [http://mjg59.livejournal.com/](http://mjg59.livejournal.com/) 
>  **All Linux kernels since 2.6.24. will claim to support all the "_OSI" interfaces ** which means the return value of "OS check" will be the same as any of the newer windows versions. or in worst case scenario
>  **Linux has responded to _OS with "Microsoft Windows NT" since 2.6.9. ** which just made this whole thing **invalid** according to me. 


There is a bug somewhere but it is almost, to be sure I think, **not caused by** ```
                If (MCTH (_OS, "Linux"))
                {
                    Store (0x03, OSVR)
                }

``` **as originally believed.**

Of course, Foxconn and others are still claiming full ACPI compliance and they most likley would fail a unbiased test. But, how would they know in the end it wasn't working out all right? 


I've now stepped one more step on the O/S understanding ladder, which is endlessly high. Linux is trying to keep up with the Microsoft Windoze's DSDT's, which is quite a reverse engineering effort done by the kernel developers (Thank you, btw!). 

Albeit I think it is the wrong way to approach the growing problem of Microsofts strong hold the majority of systems, I would also find it the only way to deal with it until Linux gains higher ground and can put more demands or "criterias" for the manufacturers to meet.

**Until then, we'll have to ride the wave of Microsoft, I suppose.**

Call me a traitor, or whatever, it doesn't remove the facts that Microsoft is still the TopDog here.

**EDIT2: Forgot to mention, this "bug" or "problem" is present on other motherboards from other manufacturers also. Apparently it does affect AMI BIOS'es only, that we know of. Solution to this is to come soon, according to manufacturer officials.**

---

### Post by rberger123 on 2008-07-28
> **MountainX said:**
> I saw the TheAlmightyCthulh's update about Foxconn

Well, you could have given a direct link anyway. As some of you might have noticed by now, TheAlmighty is currently banned from these forums due to not complying with some of them rules.

In case you want to keep up to date with his views and proceedings, here's his blog
[http://izanbardprince.wordpress.com/](http://izanbardprince.wordpress.com/)

---

### Post by Neckbeard on 2008-07-29
> **linuser said:**
> Hello I have an asrock (asrock dual sata II) with this table dstd  acpi for bios AMIBIOS



I have the same problem that the foxconn?

 the suspended way and the hibernation does not work

Contact whoever made the board, tell them that Foxconn has acknowledged the problem, and that they are developing a patch with AMI.

This is all very frustrating, I had been wondering why Ubuntu was behaving like it is on my machine.

---

### Post by Neckbeard on 2008-07-29
> **rberger123 said:**
> Well, you could have given a direct link anyway. As some of you might have noticed by now, TheAlmighty is currently banned from these forums due to not complying with some of them rules.

In case you want to keep up to date with his views and proceedings, here's his blog
[http://izanbardprince.wordpress.com/](http://izanbardprince.wordpress.com/)

Thank you, I had just noticed this when you had said something about it, all of the Google results are hogged by the original "sabotage theory", it does look like Microsoft had a major part in this and is trying to stay out of the spotlight by letting AMI do dirty work for them, it looks like ASUS and MSI boards are also affected.

Ouch, this is a mess now matter how it came about!

---

### Post by jkrise on 2008-07-29
I buy Intel boards because they support Linux. Yesterday, I got a new Intel DG33FB motherboard for a PACS server at my hospital. I tried Ubunutu64 and various other distros, but got similar problems, as reported in the original thread.

The board however loads Windows XP just fine. The BIOS version says DPP3510J and I'm not sure if it's AMI or not. The vendor says he will replace it with an Intel DQ35MP instead.

Meanwhile I find many users [have similar problems]("http://www.linuxquestions.org/questions/linux-enterprise-47/unable-to-install-linux-on-intel-dg33fb-motherboard-587147/page2.html") with the DG33FB board. Should I wait for a BIOS update from Intel or go in for the more expensive DQ35MP instead?

---

### Post by Neckbeard on 2008-07-29
> **jkrise said:**
> I buy Intel boards because they support Linux. Yesterday, I got a new Intel DG33FB motherboard for a PACS server at my hospital. I tried Ubunutu64 and various other distros, but got similar problems, as reported in the original thread.

The board however loads Windows XP just fine. The BIOS version says DPP3510J and I'm not sure if it's AMI or not. The vendor says he will replace it with an Intel DQ35MP instead.

Meanwhile I find many users [have similar problems]("http://www.linuxquestions.org/questions/linux-enterprise-47/unable-to-install-linux-on-intel-dg33fb-motherboard-587147/page2.html") with the DG33FB board. Should I wait for a BIOS update from Intel or go in for the more expensive DQ35MP instead?

Looks like Foxconn makes a lot of the Intel boards? Call Intel?

---

### Post by jkrise on 2008-07-29
> **Neckbeard said:**
> Looks like Foxconn makes a lot of the Intel boards? Call Intel?

I called Intel and got a similar reply to what Foxconn gave.... "The board is only meant for Windows operating systems, not Linux. To buy a certified Linux motherboard, get a DQ35MP instead."

I tried the parameter "pci=nommconf" as suggested; it went a bit further ahead on the installation, but crashed. Sounds very fishy.. why would Intel motherboards not work with Linux? I'm very disappointed to note that the Linux kernel is patched to report as Windows to the BIOS. Why? Should the BIOS care what OS is running?

This is very similar to the "Report as IE" trick, on Opera and Firefox - many sites are still broken inspite of this kludge.

---

### Post by linuser on 2008-07-29
I have sent  mail to asrock and this is what they have answered me:)

> 

Dear ASRock Customer,

 

Sorry, this motherboard does not support linux. (we did not test it under Linux system)

Please kindly use Windows 2000/XP with this motherboard.

 

Thanks for contacting ASRock.

Yours truly,

ASRock

 


:lolflag:

---

### Post by Dark Angel on 2008-07-29
> **jkrise said:**
> This is very similar to the "Report as IE" trick, on Opera and Firefox - many sites are still broken inspite of this kludge.

SHOULD it care?  No.  At least I don't believe so.

DOES it care?  With at least one BIOS manufacturer doing, at best shoddy work or at worst deliberately engineering the issue, it would seem that "care" it does.

---

### Post by rberger123 on 2008-07-29
All you guys getting a "this motherboard does not support linux" answer from your support, just do what TheAllmighty did:

look if the board is advertised to be ACPI standard compliant. If it is, tell them you are **_not_** asking for Linux support, you are asking for standard compliance as advertised.

---

### Post by linuser on 2008-07-29
Have answered them with this message to asrock



> 

Thank you for answering
I am not asking that soporteis linux Only I want to know if it fulfils  ACPI standard compliant For a possible bug of the bios AMI That affects to linux
A lot of graces by everything




Have than answer

---

### Post by mjg59 on 2008-07-29
> **rberger123 said:**
> All you guys getting a "this motherboard does not support linux" answer from your support, just do what TheAllmighty did:

look if the board is advertised to be ACPI standard compliant. If it is, tell them you are **_not_** asking for Linux support, you are asking for standard compliance as advertised.

If you're going to do that, please ensure that you point out precisely which section of the ACPI specification is being broken. The AMI BIOS code appears to be compliant with the ACPI specification.

---

### Post by Neckbeard on 2008-07-29
> **mjg59 said:**
> If you're going to do that, please ensure that you point out precisely which section of the ACPI specification is being broken. The AMI BIOS code appears to be compliant with the ACPI specification.

[http://izanbardprince.wordpress.com/2008/07/29/latest-mail-from-foxconn-continuing-to-promise-a-fix-as-highest-priority-and-my-reply/](http://izanbardprince.wordpress.com/2008/07/29/latest-mail-from-foxconn-continuing-to-promise-a-fix-as-highest-priority-and-my-reply/)

I guess not.

Has anyone seen this yet?

Looks like a lot of motherboards with a bug ridden AMI BIOS

I have one of their boards and I'm going to be mad as hell if this doesn't get fixed.

This is unfolding very, very strangely I think.

---

### Post by mjg59 on 2008-07-29
> **Neckbeard said:**
> [http://izanbardprince.wordpress.com/2008/07/29/latest-mail-from-foxconn-continuing-to-promise-a-fix-as-highest-priority-and-my-reply/](http://izanbardprince.wordpress.com/2008/07/29/latest-mail-from-foxconn-continuing-to-promise-a-fix-as-highest-priority-and-my-reply/)

I guess not.

No. There's a difference between not being standards compliant and having a bug (though I remain unconvinced that there's a bug in anything other than Linux here). The AMI tables compile cleanly with the Intel reference compiler with the exception of some warnings that have nothing whatsoever to do with standards compliance. As I said, if you're going to complain to a board manufacturer about their standards compliance then make sure you can tell them which part of the standard they're violating. If you can't, then don't make the claim.

---

### Post by Neckbeard on 2008-07-29
> **mjg59 said:**
> No. There's a difference between not being standards compliant and having a bug (though I remain unconvinced that there's a bug in anything other than Linux here). The AMI tables compile cleanly with the Intel reference compiler with the exception of some warnings that have nothing whatsoever to do with standards compliance. As I said, if you're going to complain to a board manufacturer about their standards compliance then make sure you can tell them which part of the standard they're violating. If you can't, then don't make the claim.

[http://izanbardprince.wordpress.com/2008/07/29/my-official-statement-on-the-matthew-garrett-kerfluffle/](http://izanbardprince.wordpress.com/2008/07/29/my-official-statement-on-the-matthew-garrett-kerfluffle/)

I don't think he likes you very much. :lolflag:

---

### Post by VMC on 2008-07-29
I have a broken DSDT table but as yet I'm unable to fix it. I don't think I have a Foxconn motherboard. I have a Dell Optiplex system. I did dump the dmicode but nothing points to Foxconn.

I followed this link and found the point of my failure but can't find a fix:
[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

Surprisingly my fan comes on and off with a defective DSDT table. Someone mentioned that it's built into the BIOS.

---

### Post by Neckbeard on 2008-07-29
> **VMC said:**
> I have a broken DSDT table but as yet I'm unable to fix it. I don't think I have a Foxconn motherboard. I have a Dell Optiplex system. I did dump the dmicode but nothing points to Foxconn.

I followed this link and found the point of my failure but can't find a fix:
[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

Surprisingly my fan comes on and off with a defective DSDT table. Someone mentioned that it's built into the BIOS.

Looks like Foxconn makes some of those, but won't stand behind them, you have to go to Dell for that.

(good luck)

---

### Post by rberger123 on 2008-07-29
> **mjg59 said:**
> If you're going to do that, please ensure that you point out precisely which section of the ACPI specification is being broken.

Most certainly, Sir.

We're all gonna try as hard as we can to find the point precisely. Albeit it might be much easier for the manufacturer, who has full access to all BIOS source code.

I mean, with the industry being so forthcoming, open and precise to us why would we want to serve them otherwise.

Thanks a lot for the reminder!

Best regards, Raimund

---

### Post by mjg59 on 2008-07-29
> **rberger123 said:**
> Most certainly, Sir.

We're all gonna try as hard as we can to find the point precisely. Albeit it might be much easier for the manufacturer, who has full access to all BIOS source code.


One of the nice things about ACPI is that it's trivial to decompile, which means that anyone who has one of these boards has everything needed to test whether it complies with the ACPI spec or not. I can't find anything in the Foxconn tables that fails to conform (there's a checksum error in a table that's not part of the specification, so that's entirely irrelevant), but that's obviously not a guarantee. There's plenty of people claiming that there's a spec violation going on, so I'd love it if they could actually point out which bit of the spec is being violated and by which code.

---

### Post by XeroxGUI on 2008-07-29
[http://service.foxconnchannel.com/econtact/online/onlineFeedback.init.do?selectCaseId=6C80F3630A86825C00E6529C200B2C72](http://service.foxconnchannel.com/econtact/online/onlineFeedback.init.do?selectCaseId=6C80F3630A86825C00E6529C200B2C72)

there's the response to my nasty complaint.:guitar:

---

### Post by knutschr on 2008-07-29
> **mjg59 said:**
> One of the nice things about ACPI is that it's trivial to decompile, which means that anyone who has one of these boards has everything needed to test whether it complies with the ACPI spec or not. I can't find anything in the Foxconn tables that fails to conform (there's a checksum error in a table that's not part of the specification, so that's entirely irrelevant), but that's obviously not a guarantee. There's plenty of people claiming that there's a spec violation going on, so I'd love it if they could actually point out which bit of the spec is being violated and by which code.
I read of much interest your postings, as I understand you are very cunning in this matter.
None has answered my former questions, so I ask you to do it:
-Why has the BIOS a reference to "Linux" when there is no equal use of kernels in linux, and the kernels present themselves as the corresponding Windows version?
-Is this required?

---

### Post by mjg59 on 2008-07-29
> **knutschr said:**
> 
-Why has the BIOS a reference to "Linux" when there is no equal use of kernels in linux, and the kernels present themselves as the corresponding Windows version?

Because it's old code that's present in multiple BIOSes from several vendors, which makes me suspect that it's originally part of some Intel sample code. When a new motherboard gets released, the ACPI tables aren't written from scratch - they're usually just modified from the previous motherboard. This code wasn't breaking anything, so nobody ever got around to removing it.
> 
-Is this nessesary?

No.

---

### Post by Fitzcarraldo on 2008-07-29
> **mjg59 said:**
> No. There's a difference between not being standards compliant and having a bug (though I remain unconvinced that there's a bug in anything other than Linux here).

As a neophyte I'm trying to understand the source of the problem, and have a few genuine questions:

Apparently Foxconn, and now AMI, are working on a change to the BIOS of various mobos. If there is no bug in the BIOS, what are they changing, and why? Presumably, if they thought the fault lay with Linux, they would say so?

This issue seems to be a hot topic on many Linux-related forums and blogs at the moment. However, as far as resolution of the problem is concerned, all I have read so far relates to the BIOS supplier working to implement a change to the BIOS. If you believe there is only a bug in Linux itself, is anything happening on the Linux side? If this is a possible bug in the kernel, is anyone from the Linux kernel team investigating the problem and trying to come up with a fix for the kernel?

---

### Post by mjg59 on 2008-07-29
> **Fitzcarraldo said:**
> 
Apparently Foxconn, and now AMI, are working on a change to the BIOS of various mobos. If there is no bug in the BIOS, what are they changing, and why? Presumably, if they thought the fault lay with Linux, they would say so?

Given the press, how would Foxconn announcing that the bug is in Linux be received? Right now it'd still be perceived as them trying to pass the buck. Linux bugs can often be worked around in the BIOS, so that would be one approach - alternatively, they're just showing willing in trying to diagnose the real problem.

> This issue seems to be a hot topic on many Linux-related forums and blogs at the moment. However, as far as resolution of the problem is concerned, all I have read so far relates to the BIOS supplier working to implement a change to the BIOS. If you believe there is only a bug in Linux itself, is anything happening on the Linux side? If this is a possible bug in the kernel, is anyone from the Linux kernel team investigating the problem and trying to come up with a fix for the kernel?

I'm travelling at the moment, but I've arranged to get hold of the motherboard in question once I'm back home (mid next week). I ought to be able to track down the source of the problem then.

---

### Post by Neckbeard on 2008-07-29
> **knutschr said:**
> I read of much interest your postings, as I understand you are very cunning in this matter.
None has answered my former questions, so I ask you to do it:
-Why has the BIOS a reference to "Linux" when there is no equal use of kernels in linux, and the kernels present themselves as the corresponding Windows version?
-Is this required?

I think this explains it:

[http://en.wikipedia.org/wiki/Cargo_cult_programming]("http://en.wikipedia.org/wiki/Cargo_cult_programming")

---

### Post by Neckbeard on 2008-07-29
> **mjg59 said:**
> Given the press, how would Foxconn announcing that the bug is in Linux be received? Right now it'd still be perceived as them trying to pass the buck. Linux bugs can often be worked around in the BIOS, so that would be one approach - alternatively, they're just showing willing in trying to diagnose the real problem.



I'm travelling at the moment, but I've arranged to get hold of the motherboard in question once I'm back home (mid next week). I ought to be able to track down the source of the problem then.

Foxconn has admitted that this is no problem on same chipset with Award BIOS.

If a Linux bug, then why does everything get fixed on identical hardware with the Award BIOS?

I'm believing at the moment it's a bad BIOS and not Linux, or that if it is Linux, this BIOS is triggering the problem at any rate while most other BIOSes don't?

The latter sounds very unlikely (that it's a Linux bug) just for that.

---

### Post by Neckbeard on 2008-07-29
I was just reading some more, he also mentions FreeBSD is similarly afflicted with the reboot after suspend error?

---

### Post by vanessaezekowitz on 2008-07-30
In response to the original thread, I sent Foxconn an email letting them know how I felt.  I don't have a foxconn system, but I'm always watching for good deals on hardware, so I felt this might affect me some day.  Call me a fangirl if you want, I'm very passionate about Linux. :-)  

Here's what I originally wrote:

> I recently read of an attempt by your company to explicitly manufacture boards that use a damaged BIOS, which results in improper, non-compliant ACPI configuration data being returned when a Linux-based operating system is being run.  According to the report, your PR department has explicitly and clearly stated that you will not support Linux.  Why then, does your BIOS data include deliberately broken entries for Linux?   If you had simply stuck with code/data that is fully compliant to the ACPI specification, this issue would not crop up.  No doubt you've heard plenty of complaints by now due to the news being covered on Slashdot.  If your management is smart, they will find and fire the person(s) responsible for this outrage, and fix it post-haste.  Slashdot can, as you are no doubt also aware, severely damage large companies' reputations when those companies get out of line.  I am disgusted by this practice, I find it outright reprehensible, and will NEVER buy any hardware made by your company.

...Needless to say, I was just plain ticked off.  They responded with a link pointing to some kind of issue tracking system.  Therein was this reply:

> Dear Vanessa Ezekowitz
Thank you very much for your attention with Foxconn.
With regard to this issue posted on the websites, we are trying to resolve it and we would like to state here that Foxconn will never reject Linux.
If you meet similar problems, please try to provide your detailed configuration, (including cpu, memory, hdd, Linux version and its kernel, etc.) and the symptom so that we could test in our bed and analyse to resolve this.
It is really a pleasure to be of service to you, [ma'am].
Thanks and best regards,
Foxconn Technical Support

(corrected a pronoun error in their reply).

Figured their reply would be interesting to others here.

---

### Post by saaya on 2008-07-30
Hi all,
I work for Foxconn QuantumForce, the highend desktop parts, different department but Ill try to help out :)

First of all thanks to KiwiNZ and the admin and moderator team on the forums here for trying to keep things calm and solution focussed :)

Second of all thanks to mjg59 for shedding some light on the actual problem and answering peoples questions around here :)
If there is anything i can do to help you or somebody you know who can fix this problem and improve the compatibility in future people let me know. 

> **TheAlmightyCthulhu said:**
> 
It will be extremely interesting to see where this ends up, my idea is (without speculating as to  the cause of the problem), that someone's boss(es) are aware of the situation that has brewed, and that they're being ridden to provide a BIOS that works well with Linux.

As for their reasoning, I don't care, I just want them to take accountability and fix it, they owe their customers an ACPI compliant board, as advertised, even if they don't go out of their way to advertise that it works with Linux.The tech support guys you talked to didnt do anything wrong in my opinion and they told you the same thing ANY mainboard vendor will tell you. And sorry to dissapoint you, but no, nobody here is in trouble or gets poked by their bosses because of what you said or did.

all your whining and blaming foxconn for deliberatly cripping linux has achieved is people here at foxconn taking the open source community less serious, which is very dissapointing imo.
unfortunately there are still quite some people who believe in the myth of the louder you complain the better you will be treated...

> **Runamok said:**
> I think Foxconn recognizes that shoddy programming and support is unacceptable. The 150k+ views should tell them that.about the programming i cant comment, but as far as i know the troublesome code isnt written by us but by AMI and is used by every mainboard vendor who uses AMI BIOS kernels. about the support, could you please tell me what exactly is so shoddy about it? he told him the same thing any tech support will tell you, its not supported... and he event went ahead and offered to try and fix it but was only threattened and harassed by almighty. For the record, our tech support guys started to check on this and are looking for a fix ever since almighty first contacted them, not after almighty spammed the net with negative propaganda about foxconn!

> **Runamok said:**
> And If CBrunning is not getting the upper level support he needs, perhaps he should ask his superiors if Foxconn is serious about upholding the marketing departments claim of Linux ACPI support.correct me if im wrong, i work for a different department, but as fas as i know foxconn never claimed linux support to begin with... and a part of the community stoning foxconn before we even started working with the community isnt really helping in creating a good and efficient relationship, now is it? 

> **rberger123 said:**
> I was about to say the same. Even if things go a little over the top any attention and focus brought to these issues can just be beneficial, thanks to a kind of fortunate mingling of two separate topics, i.e. ACPI standard compliance and the claim of maybe intentionally breaking Linux. Regardless the latter, this obviously is a good time to seek and urge for advances on the former.

I'd expect especially Linux developers to be pleased, as they have been complaining often enough about the sad state of affairs, needing them to reimplement Windows behavior "bug for bug". If I were one, I'd think I could expect my voice of concern being heard sooner in the future.on the contrary, all that is achieved if some people who dont even get their facts straight create the manufacturers a big headache, is that the REAL open source community who is trying to get someting done and improve things, is taken less serious or might even be ignored.

would you want to work with somebody who might visit opra and other tv shows one day trying to discredit you, just cause he got upset over some bug that isnt even your fault?

"Accusing companies of conspiring against us when the most likely explanation is simply that they don't care is a ******* ridiculous thing to do and does nothing to get rid of the impression that Linux users are a bunch of whining childish hatemongers. Next time, try talking to someone who actually understands this stuff first?"

exactly... 

> **JPorter said:**
> If the end result is better, more consistent and ultimately more functional power behavior under Linux, *for everyone*, then the ol' Ryan will have done some good.if the end result is anything good it will be because smart, dedicated hard working people from the open source community and foxconn will work on this and find a solution and NOT because almighty created a pr nightmare for foxconn. 

> **Dark Angel said:**
> Bug fix or no, their customer support seems to have improved.i dont see any change in tech support at all... but if your happy with the support now, good :)

> **Neckbeard said:**
> No kidding, I saw how they were behaving before, there is no excuse for this.then tell me, how were "they" behaving? they were polite throughout the whole time from what ive seen, even when almighty pressured them and provoked them. and even after all the headaches he caused them they were actually working on a fix and still are.. so what exactly did they do wrong?

> **Neckbeard said:**
> Thank you, I had just noticed this when you had said something about it, all of the Google results are hogged by the original "sabotage theory", it does look like Microsoft had a major part in this and is trying to stay out of the spotlight by letting AMI do dirty work for them, it looks like ASUS and MSI boards are also affected.

Ouch, this is a mess now matter how it came about!
its possible that microsoft provided this code to AMI, but the fact that the code seems to be outdated is not microsofts fault and surely not a sabotage attempt...

> **rberger123 said:**
> All you guys getting a "this motherboard does not support linux" answer from your support, just do what TheAllmighty didsure, if you want to kill off manufacturer support for linux all together, go ahead. if you actually want to do something to improve the situation you might want to try and work WITH the manufacturers and not against them.

just like somebody posted in this thread, the problem of the open source community is that there isnt ONE organisation that certifies standards like MS or Intel or AMD etc do. So imagine you want to sell a product that complies with Linux... how would you ensure it works well with all the main distributions out there? for MS Intel AMd etc its easy, you submit your product and they will evaluate it and help you to get it compliant. with linux its not that easy...

I really like the idea of open source and want to support it, but its really not easy... its not even about the money it costs or the work it takes, there is just no unified concept to certify compatibility... at least as far as im aware of...

> **mjg59 said:**
> Given the press, how would Foxconn announcing that the bug is in Linux be received? Right now it'd still be perceived as them trying to pass the buck. Linux bugs can often be worked around in the BIOS, so that would be one approach - alternatively, they're just showing willing in trying to diagnose the real problem.

I'm travelling at the moment, but I've arranged to get hold of the motherboard in question once I'm back home (mid next week). I ought to be able to track down the source of the problem then.At the moment nobody KNOWS what the issue is, so of course our engineers are working on it and are trying to solve it. And regardless of where the problem lies, im pretty sure the problem can be fixed on both sides...

I really dont like how many people are focussed on who is to blame... ami, microsoft, foxconn, linux... does it matter?
we should all focus on getting the problem fixed and making it work! maybe its a problem of the BIOS but its easier or more reasonable to fix it in linux somehow to prevent somthing like this or something similar to happen again? after all foxconn boards arent the only ones using this ami code, so if it can be fixed in linux without too much hassle, that would be the best thing as it would fix the problem overall for ALL boards, wouldnt it?

if you have any questions or want to help in improving foxconns linux compatibility or foxconns relations to the open source community please let me know! I might be able to hook some penguin veterans up with our engineers which should help a bunch to imrove future support :)
i wish i could have a chat with linus or the round table of the elders, but i have no idea how we could approach them... if anyboy can hook us up, let me know!

and to almighty etc: i heard about this before the PR mess and negative propaganda was spread on the net, and all it caused was me and others reconsidering if we should even try to get involved or just ignore it... but after seeing that at least a part of the community here is actually interested in improving things and working on this, me, carl and others have decided to try and support them. Dont think this only happened cause of your whining and complaining, on the contrary... i recommend you some anger management training and hope you will think about what your trying to achieve and how you can achieve it first next time.
next time if you cant open a door you might want to try ring the bell or try another door instead of using explosives to blow the doors and windows open and cause a mess for everybody on the entire block.

all you achieved is discrediting yourself and unfortunately a part of the open source community to foxconn, the press and even the FTC! congratulations! thats quite an achievement in only one or two weeks...
you know what? microsoft should hire you and more people like you to do just what you did here, if they really want to sabotage the open source community.

---

### Post by mjg59 on 2008-07-30
> **Neckbeard said:**
> Foxconn has admitted that this is no problem on same chipset with Award BIOS.

If a Linux bug, then why does everything get fixed on identical hardware with the Award BIOS?

Ok, so there are two issues here. The first is that ACPI is a complex specification (over 600 pages) and it's very easy to write two different implementations of the same code that will trigger entirely different paths in the OS. The second is that ACPI defines only a small subset of the hardware behaviour. The legacy BIOS code (x86 assembler, not ACPI bytecode) is responsible for much of the initial hardware setup and suspend and resume handling. Different implementations may program the hardware differently, and Linux may work fine with one setup and not the other.

> 
I'm believing at the moment it's a bad BIOS and not Linux, or that if it is Linux, this BIOS is triggering the problem at any rate while most other BIOSes don't?

The latter sounds very unlikely (that it's a Linux bug) just for that.

It's really not very unlikely. I've done a lot of work with BIOS code in the past.

---

### Post by Neckbeard on 2008-07-30
> **saaya said:**
> Hi all,
I work for Foxconn QuantumForce, the highend desktop parts, different department but Ill try to help out :)

First of all thanks to KiwiNZ and the admin and moderator team on the forums here for trying to keep things calm and solution focussed :)

Second of all thanks to mjg59 for shedding some light on the actual problem and answering peoples questions around here :)
If there is anything i can do to help you or somebody you know who can fix this problem and improve the compatibility in future people let me know. 

The tech support guys you talked to didnt do anything wrong in my opinion and they told you the same thing ANY mainboard vendor will tell you. And sorry to dissapoint you, but no, nobody here is in trouble or gets poked by their bosses because of what you said or did.

all your whining and blaming foxconn for deliberatly cripping linux has achieved is people here at foxconn taking the open source community less serious, which is very dissapointing imo.
unfortunately there are still quite some people who believe in the myth of the louder you complain the better you will be treated...

about the programming i cant comment, but as far as i know the troublesome code isnt written by us but by AMI and is used by every mainboard vendor who uses AMI BIOS kernels. about the support, could you please tell me what exactly is so shoddy about it? he told him the same thing any tech support will tell you, its not supported... and he event went ahead and offered to try and fix it but was only threattened and harassed by almighty. For the record, our tech support guys started to check on this and are looking for a fix ever since almighty first contacted them, not after almighty spammed the net with negative propaganda about foxconn!

correct me if im wrong, i work for a different department, but as fas as i know foxconn never claimed linux support to begin with... and a part of the community stoning foxconn before we even started working with the community isnt really helping in creating a good and efficient relationship, now is it? 

on the contrary, all that is achieved if some people who dont even get their facts straight create the manufacturers a big headache, is that the REAL open source community who is trying to get someting done and improve things, is taken less serious or might even be ignored.

would you want to work with somebody who might visit opra and other tv shows one day trying to discredit you, just cause he got upset over some bug that isnt even your fault?

"Accusing companies of conspiring against us when the most likely explanation is simply that they don't care is a ******* ridiculous thing to do and does nothing to get rid of the impression that Linux users are a bunch of whining childish hatemongers. Next time, try talking to someone who actually understands this stuff first?"

exactly... 

if the end result is anything good it will be because smart, dedicated hard working people from the open source community and foxconn will work on this and find a solution and NOT because almighty created a pr nightmare for foxconn. 

i dont see any change in tech support at all... but if your happy with the support now, good :)

then tell me, how were "they" behaving? they were polite throughout the whole time from what ive seen, even when almighty pressured them and provoked them. and even after all the headaches he caused them they were actually working on a fix and still are.. so what exactly did they do wrong?


its possible that microsoft provided this code to AMI, but the fact that the code seems to be outdated is not microsofts fault and surely not a sabotage attempt...

sure, if you want to kill off manufacturer support for linux all together, go ahead. if you actually want to do something to improve the situation you might want to try and work WITH the manufacturers and not against them.

just like somebody posted in this thread, the problem of the open source community is that there isnt ONE organisation that certifies standards like MS or Intel or AMD etc do. So imagine you want to sell a product that complies with Linux... how would you ensure it works well with all the main distributions out there? for MS Intel AMd etc its easy, you submit your product and they will evaluate it and help you to get it compliant. with linux its not that easy...

I really like the idea of open source and want to support it, but its really not easy... its not even about the money it costs or the work it takes, there is just no unified concept to certify compatibility... at least as far as im aware of...

At the moment nobody KNOWS what the issue is, so of course our engineers are working on it and are trying to solve it. And regardless of where the problem lies, im pretty sure the problem can be fixed on both sides...

I really dont like how many people are focussed on who is to blame... ami, microsoft, foxconn, linux... does it matter?
we should all focus on getting the problem fixed and making it work! maybe its a problem of the BIOS but its easier or more reasonable to fix it in linux somehow to prevent somthing like this or something similar to happen again? after all foxconn boards arent the only ones using this ami code, so if it can be fixed in linux without too much hassle, that would be the best thing as it would fix the problem overall for ALL boards, wouldnt it?

if you have any questions or want to help in improving foxconns linux compatibility or foxconns relations to the open source community please let me know! I might be able to hook some penguin veterans up with our engineers which should help a bunch to imrove future support :)

and to almighty etc: i heard about this before the PR mess and negative propaganda was spread on the net, and all it caused was me and others reconsidering if we should even try to get involved or just ignore it... but after seeing that at least a part of the community here is actually interested in improving things and working on this, me, carl and others have decided to try and support them. Dont think this only happened cause of your whining and complaining, on the contrary... i recommend you some anger management training and hope you will think about what your trying to achieve and how you can achieve it first next time.
next time if you cant open a door you might want to try ring the bell or try another door instead of using explosives to blow the doors and windows open and cause a mess for everybody on the entire block.

And the spin cycle begins.....:lolflag:

You guys have no excuse to treat people like that, it was obvious you never planned on fixing the problem, that is provided you really work for Foxconn.

I sent an email about you to this Heart Zhang and Carl Brunning, referencing this post, we'll find out shortly I suspect.

I suspect more likely you're from the Linux Hater's blog here to spread FUD.

---

### Post by jimv on 2008-07-30
I think this all just comes down to two things:

Not all code is checked as thoroughly as it should be

and

some people like being outraged for even the silliest reasons.

---

### Post by Neckbeard on 2008-07-30
Well, he's very inflammatory against Ryan, and he's probably the (or one of the) caustic persons responsible for letting this blow up like it has.

Reading Ryan's blog, I think he had no choice but to use a battering ram (in the analogy), they were obviously stonewalling.

---

### Post by mjg59 on 2008-07-30
> **Neckbeard said:**
> And the spin cycle begins.....:lolflag:

You guys have no excuse to treat people like that, it was obvious you never planned on fixing the problem, that is provided you really work for Foxconn.

I sent an email about you to this Heart Zhang and Carl Brunning, referencing this post, we'll find out shortly I suspect.

I suspect more likely you're from the Linux Hater's blog here to spread FUD.

This is not in the slightest bit appropriate. Bear in mind the code of conduct, and be respectful to people who have offered opinions - even if you disagree with them.

---

### Post by saaya on 2008-07-30
> **Neckbeard said:**
> And the spin cycle begins.....:lolflag:what do you mean?

> **Neckbeard said:**
> You guys have no excuse to treat people like thatlike what? i still dont get what exactly the problem was with the reply our tech support gave...

> **Neckbeard said:**
> it was obvious you never planned on fixing the problemwhat makes you think so? 0_o

> **Neckbeard said:**
> that is provided you really work for Foxconn.then why would i claim to work for foxconn?
ask the admin team of this forum, i registered here with my foxconn email address.
and if you want to check it quickly by yourself, i happen to be a moderator on the official Foxconn QuantumForce tech support Forum on XtremeSystems:
[http://www.xtremesystems.org/forums/forumdisplay.php?f=281](http://www.xtremesystems.org/forums/forumdisplay.php?f=281)

> **Neckbeard said:**
> I sent an email about you to this Heart Zhang and Carl Brunning, referencing this post, we'll find out shortly I suspect.im in yantai china right now visiting the tech support department and motherboard factory, so i might even be able to post a picture of me and heart zhang later if you want :D

> **Neckbeard said:**
> I suspect more likely you're from the Linux Hater's blog here to spread FUD.linux haters blog? who is that, and if i was a linux hater then why would i pretend to be a foxconn employee and offer to work with ubuntu and other linux distributions?

tinfoil hats sure seem to be popular around here :P

---

### Post by saaya on 2008-07-30
> **jimv said:**
> I think this all just comes down to two things:

Not all code is checked as thoroughly as it should be

and

some people like being outraged for even the silliest reasons.yeah, thats my understanding as well. i dont know too much about BIOS coding and acpi and linux etc, but it seems AMI either followed Microsofts recommendation to provide seperate ACPI tables for each OS, or they did it by themselves, cause some OSes might need special ACPI tables? maybe some OSes dont support some features and thats why they need a different ACPI table?

and then since we and others dont have enough resources and there is no unified testing procedure for linux ACPI tables the tables were not updated anymore at some point, but only the vista and maybe windows xp tables. 

what i dont get is why linux cant just use the vista table if it works ok... and i already asked our bios engineering team if we cant just copy the vista table and use the same infos in our linux acpi table in bios as well... no reply so far...

> **Neckbeard said:**
> Well, he's very inflammatory against Ryan, and he's probably the (or one of the) caustic persons responsible for letting this blow up like it has.

Reading Ryan's blog, I think he had no choice but to use a battering ram (in the analogy), they were obviously stonewalling.who was stonewalling? our tech support? where? and even IF one single tech support agent would have stone walled, you guys have to realize that there are other ways to contact foxconn. Ive worked in quite some big companies like amd and dhl, the german telekom etc, and the customer support is never easy to get past if you have a question or request they cant take care of. ive worked in customer support myself and i know that all they can do is forward the request but it most likely ends up nowhere... if you really want something changed you need to talk to the right people, product management, engineers, public reations etc...

or do you think wallmart will offer a new flavour of java if you ask the senior citizen in the entrance welcomming you and telling you where you can find vegetables and where you can find books?

---

### Post by Neckbeard on 2008-07-30
> **saaya said:**
> yeah, thats my understanding as well. i dont know too much about BIOS coding and acpi and linux etc, but it seems AMI either followed Microsofts recommendation to provide seperate ACPI tables for each OS, or they did it by themselves, cause some OSes might need special ACPI tables? maybe some OSes dont support some features and thats why they need a different ACPI table?

and then since we and others dont have enough resources and there is no unified testing procedure for linux ACPI tables the tables were not updated anymore at some point, but only the vista and maybe windows xp tables. 

what i dont get is why linux cant just use the vista table if it works ok... and i already asked our bios engineering team if we cant just copy the vista table and use the same infos in our linux acpi table in bios as well... no reply so far...

who was stonewalling? our tech support? where? and even IF one single tech support agent would have stone walled, you guys have to realize that there are other ways to contact foxconn. Ive worked in quite some big companies like amd and dhl, the german telekom etc, and the customer support is never easy to get past if you have a question or request they cant take care of. ive worked in customer support myself and i know that all they can do is forward the request but it most likely ends up nowhere... if you really want something changed you need to talk to the right people, product management, engineers, public reations etc...

or do you think wallmart will offer a new flavour of java if you ask the senior citizen in the entrance welcomming you and telling you where you can find vegetables and where you can find books?

Well, one bad employee can besmirch the entire company's image, if I were to guess, I'd say you should have trained those employees with "If you don't know, find out, don't take the attitude with the customer".

Even if he's wrong about everything else, that incompetent support representative would have even had my temper going, in this case, he was the powder keg, and your employee lit the match. Yes?

---

### Post by mjg59 on 2008-07-30
> **saaya said:**
> yeah, thats my understanding as well. i dont know too much about BIOS coding and acpi and linux etc, but it seems AMI either followed Microsofts recommendation to provide seperate ACPI tables for each OS, or they did it by themselves, cause some OSes might need special ACPI tables? maybe some OSes dont support some features and thats why they need a different ACPI table?

As a couple of concrete examples of this: when you eject a hotswap drive in a laptop, ACPI generates a message to the OS asking it to recheck the device. Windows 98 expects this message to be delivered to the parent bus, whereas later versions of Windows expect this to be delivered to the child device. The ACPI specification is unclear on which behaviour is correct. As a result, for correct behaviour an ACPI table needs to check which version of Windows it's running on.

Another example is the high precision event timer (HPET). Older versions of Windows don't support it, but as it's defined in ACPI it will show up as a device. Users complain when they open device manager and see a device that doesn't have a driver. The easiest workaround is to modify the ACPI tables so that the HPET is only enabled on newer versions of Windows. This obviously means that they need to check the version of Windows used.

So, why does Linux claim to be Windows? Because of things like the HPET example above. Vendors don't test on Linux, so only tend to make sure that hardware is whitelisted on newer versions of Windows. If Linux didn't claim to be Vista, then that hardware wouldn't be enabled. Bug? Arguably. Misfeature? Certainly. Violation of the ACPI specification? Not in the slightest.

It's an economic reality that the Linux market isn't big enough for most motherboard vendors to show any sign of caring as yet. To be honest, that's a good thing - vendors that test against Linux are likely to try to put workarounds in their BIOS to deal with Linux bugs, and those workarounds will then break when we fix Linux (and yes, we have seen cases where exactly this has happened - a vendor checked if the system was Linux, and then worked around a Linux bug. We fixed that bug, and the system broke because the workaround was now incorrect). I'm happy tweaking Linux's ACPI implementation until it behaves identically to the Microsoft one, and bugs like this make it easier to do so.

Those who claim that any system-specific checks are inherently violations of the ACPI specification should consider what should be done when the specification can be interpreted in two different ways. If Linux interprets it one way and Windows interprets it the other, which interpretation do you think vendors are going to choose? If different versions of Windows interpret it in different ways, how do you support both?

---

### Post by Neckbeard on 2008-07-30
> **saaya said:**
> what do you mean?
tinfoil hats sure seem to be popular around here :P

[http://people.csail.mit.edu/rahimi/helmet/](http://people.csail.mit.edu/rahimi/helmet/)

They actually would amplify Foxconn's use of the dark side of the Force. :lolflag:

"This is not the BIOS you're looking for, move along, move along....."

---

### Post by Rocket2DMn on 2008-07-30
Please, let's keep this thread on topic.  Specifically, this is only supposed to be about updates on the resolution(s) to the original problem - debate/discussion about who did what correctly/wrong/rudely/kindly/etc needs to cease.  That includes stopping Foxconn/AMI/Microsoft bashing and related talk about treatment of customers and employees by each other.
Thank you.

---

### Post by jkrise on 2008-07-30
The plot thickens... there are still many unanswered questions, which probably mjg59 should respond to:

1. "It's an economic reality that the Linux market isn't big enough for most motherboard vendors to show any sign of caring as yet. "
In which case:
1a. Why is the BIOS checking for Linux at all?
1b. Having detected Linux, why is it redirecting it to a different table to one that's sent to any Windows version?

2. "So, why does Linux claim to be Windows? Because of things like the HPET example above."
2a. This means the Linux kernel developers have not understood the lessons from the browser wars. Merely having access to a specification and claiming to be Windows is insufficient - do the kernel developers have access to the code in Vista which handles ACPI? As mjg59 himself says: "what should be done when the specification can be interpreted in two different ways"? Without access to the manner in which Vista interprets AND responds; why was the decision taken to declare Linux as 'Vista'???
2b. If the user wants only normal features from the BIOS and not the advanced features of ACPI, why can't he load Linux on the same hardware by turning off the ACPI flag in the kernel? I have a problem with the Intel DG33FB motherboard, as I described earlier; and even after specifying pci=nommconf and acpi=off ; it still refuses to load Linux - any flavour. 

3. mjg59 still gives the impression that somehow Linux is buggy and faulty here: If so
3a. How was Ryan able to get the system working by making just a few small changes to the AMI BIOS?
3b. Why is it that the same board with a different BIOS does not behave with these problems?
3c. Why is it that even non-Foxconn boards such as ASUS show up the same same problems with an AMI BIOS?

The Linux kernel developers must realise that playing the Microsoft game will only make Linux more needlessly unstable and negatively impact mindshare and marketshare. Also since Microsoft is a monopoly and does not (thankfully) do any hardware; it should not be allowed to get away with subverting the h/w mfrs to make faulty systems, and handle it with Vista's undocumented WHEA; thereby messing up with Linux. There should be no reason a kernel released in 2000 should not be able to boot in a motherboard made in 2008; backward compatibility in hardware and graceful failure in case of non-standard features must be the acceptable behaviour. It indeed appears that h/w mfrs have specifically taken pains to make sure their boards crash on old kernels, and rely on bugs in new Linux kernels, despite the intentions of the developers like mjg59.

---

### Post by Neckbeard on 2008-07-30
Turning ACPI off is a horrible thing to have to do, you can kiss SMP and many other nice things good bye.

---

### Post by Neckbeard on 2008-07-30
> **jkrise said:**
> The plot thickens... there are still many unanswered questions, which probably mjg59 should respond to:

1. "It's an economic reality that the Linux market isn't big enough for most motherboard vendors to show any sign of caring as yet. "
In which case:
1a. Why is the BIOS checking for Linux at all?
1b. Having detected Linux, why is it redirecting it to a different table to one that's sent to any Windows version?

2. "So, why does Linux claim to be Windows? Because of things like the HPET example above."
2a. This means the Linux kernel developers have not understood the lessons from the browser wars. Merely having access to a specification and claiming to be Windows is insufficient - do the kernel developers have access to the code in Vista which handles ACPI? As mjg59 himself says: "what should be done when the specification can be interpreted in two different ways"? Without access to the manner in which Vista interprets AND responds; why was the decision taken to declare Linux as 'Vista'???
2b. If the user wants only normal features from the BIOS and not the advanced features of ACPI, why can't he load Linux on the same hardware by turning off the ACPI flag in the kernel? I have a problem with the Intel DG33FB motherboard, as I described earlier; and even after specifying pci=nommconf and acpi=off ; it still refuses to load Linux - any flavour. 

3. mjg59 still gives the impression that somehow Linux is buggy and faulty here: If so
3a. How was Ryan able to get the system working by making just a few small changes to the AMI BIOS?
3b. Why is it that the same board with a different BIOS does not behave with these problems?
3c. Why is it that even non-Foxconn boards such as ASUS show up the same same problems with an AMI BIOS?

The Linux kernel developers must realise that playing the Microsoft game will only make Linux more needlessly unstable and negatively impact mindshare and marketshare. Also since Microsoft is a monopoly and does not (thankfully) do any hardware; it should not be allowed to get away with subverting the h/w mfrs to make faulty systems, and handle it with Vista's undocumented WHEA; thereby messing up with Linux. There should be no reason a kernel released in 2000 should not be able to boot in a motherboard made in 2008; backward compatibility in hardware and graceful failure in case of non-standard features must be the acceptable behaviour. It indeed appears that h/w mfrs have specifically taken pains to make sure their boards crash on old kernels, and rely on bugs in new Linux kernels, despite the intentions of the developers like mjg59.

I've seen Garrett dodging that question, about why the BIOS tweak works, honestly I doubt he even knows, and it's bothering him.

I've used this on my board and it does make the system much more agreeable, Garrett keeps stating it won't have an effect, he's wrong, I'm sorry.

---

### Post by deepspring on 2008-07-30
Nice find.

Decided to checkout my Laptop (Toshiba Satellite A100 (PSAARA)), which has a few minor ACPI related quirks:

```

            Store (0x07D0, OSYS)
            If (CondRefOf (_OSI, Local0))
            {
                If (_OSI ("Linux"))
                {
                    Store (One, LINX)
                }

                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }

                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
            }

            If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
            {
                TRAP (0x3D)
            }

            TRAP (0x32)
        }

```

Time to play.... muahahahahahahaha

---

### Post by Neckbeard on 2008-07-30
> **deepspring said:**
> Nice find.

Decided to checkout my Laptop (Toshiba Satellite A100 (PSAARA)), which has a few minor ACPI related quirks:

```

            Store (0x07D0, OSYS)
            If (CondRefOf (_OSI, Local0))
            {
                If (_OSI ("Linux"))
                {
                    Store (One, LINX)
                }

                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }

                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
            }

            If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
            {
                TRAP (0x3D)
            }

            TRAP (0x32)
        }

```

Time to play.... muahahahahahahaha

Definitely something Garrett can't explain, so why does it work for hundreds of people but he says nuh uh?

---

### Post by Daelyn on 2008-07-30
> **jkrise said:**
> 3. mjg59 still gives the impression that somehow Linux is buggy and faulty here: If so

3a. How was Ryan able to get the system working by making just a few small changes to the AMI BIOS?
3b. Why is it that the same board with a different BIOS does not behave with these problems?
3c. Why is it that even non-Foxconn boards such as ASUS show up the same same problems with an AMI BIOS?

3a: Ryan changed the DSDT table with the purpose of having the "Linux" string beeing as a "_OSI" identifier. This on the other hand should already be happening because the newer Linux kernels responds to those "_OSI" saying "Hi! I'm supporting it. Take me!" and hence the "else" function to search for Linux/WinNT/9X/ME should never come in place. 

This change, together with a changed wait time to "forever" caused some of the errors to be supressed. I wonder in the end how much was fixed of the problems. maybe it did help in some way, but, not all the way. Guess it caused other dodgy problems instead. 

3b: mjg59 has already explained this in a previous post. Different behaviour of BIOS here: [http://ubuntuforums.org/showpost.php?p=5486617&postcount=59](http://ubuntuforums.org/showpost.php?p=5486617&postcount=59) > **mjg59 said:**
> Ok, so there are two issues here. The first is that ACPI is a complex specification (over 600 pages) and it's very easy to write two different implementations of the same code that will trigger entirely different paths in the OS. The second is that ACPI defines only a small subset of the hardware behaviour. The legacy BIOS code (x86 assembler, not ACPI bytecode) is responsible for much of the initial hardware setup and suspend and resume handling. Different implementations may program the hardware differently, and Linux may work fine with one setup and not the other.

3c: Old code? I don't think they have bothered about changing it really. It has worked fine with Windoze and been certified by their tools. All fine, til someone now found out it might not be the best of ideas.

---

### Post by Sef on 2008-07-30
Locked.  This thread has gotten too inflammatory.

---

### Post by Rocket2DMn on 2008-07-30
This thread will remain closed, but I wanted to post this for those interested.

I received a message about contacting Ubuntu devs from somebody at Foxconn (shall remain anonymous):

> Could you tell me how I can contact one or some ubuntu developers to hook them up with our engineers and maybe indirectly with AMI?

Our engineers do play with linux every now and then and i believe ubuntu is one of the flavours, but they are far from experts.

My response:

> For end users, there is a system called Launchpad which has a bug report feature. The bug that was created for this issue is at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338)
Kernel bugs are put under the "linux" package and are generally assigned to ubuntu-kernel-team after they are confirmed. In this instance, I have assigned the bug to ubuntu-kernel-acpi as explained at [https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

I don't have contact information for the linux kernel developers, but you can get ahold of the Ubuntu kernel team by visiting their wiki page at [https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam)
You may consider registering on their mailing list and contacting them that way. You can also use IRC if you prefer, though the mailing list may be a little more effective since more people will see it. They may refer you upstream to the linux kernel developers.

---

### Post by Rocket2DMn on 2008-08-01
Another update for those interested.

I spoke further with the person in the message above, and it turns out that the kernel team was already in contact with the Foxconn rep below.  I received this message this afternoon which confirms the latest update on the bug report as well.

> Hi just want to say we have now got the bug in the ami bios fixed

and the person called TheAlmightyCthukhu has now had a debug bios from us and has fixed the problem

i will inform you again when we release the production bios on are web

am sorry this all causes a headache all round and hope every one is happy after this

anyway i will mail you again when release

thanks

Carl Brunning

Foxconn UK
Technical Manager

The relevant post from the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338"):
> BIOS fix for Foxconn motherboards very soon, I am beta testing a new BIOS that resolves all the party poopers as long as you're using kernel 2.6.26

MSI and ASUS appear to want to have nothing to do with this, thats my hunch anyway, kindly pester them if you're their customer would be my suggestion, but we all know that would make me a hypocrite. :P

---

